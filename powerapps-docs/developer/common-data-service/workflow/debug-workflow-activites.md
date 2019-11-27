---
title: Debugging von Workflowaktivitäten (Common Data Service) | Microsoft Docs
description: Beschreibt, wie Sie Workflow-Aktivitäten mit dem Plug-In-Registrierungstool debuggen können.
ms.custom: ''
ms.date: 06/21/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 578b38161e887aeaafe098692ec67ecf4e1412ce
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748498"
---
# <a name="debug-workflow-activities"></a>Workflowaktivitäten debuggen

Da benutzerdefinierte Workflow-Erweiterungen .NET Framework-Assemblys sind, können Sie sie mit Methoden debuggen, die der Art und Weise, wie Sie Plug-Ins debuggen, sehr ähnlich sind. 

## <a name="use-the-plug-in-registration-tool"></a>Verwenden Sie das Plug-in-Registrierungstool.

Das Plugin Registration Tool (PRT) ist eines der Tools, die Sie bei NuGet herunterladen können. Weitere Informationen: [Tools von NuGet herunterladen](../download-tools-nuget.md).

Nachdem Sie das FHM heruntergeladen haben, klicken Sie auf den `PluginRegistration.exe`, um es auszuführen.

## <a name="install-profiler"></a>Profiler installieren

Vom PRT aus können Sie die Plug-in-Profilerlösung installieren, indem Sie auf die Schaltfläche **Profiler installieren** klicken.

![Die Schaltfläche Profiler installieren im Plug-In-Registrierungstool.](../media/tutorial-debug-plug-in-install-profiler.md.png)

Diese Lösung bietet die Möglichkeit, den Kontext zu erfassen, der an Ihre Workflowaktivität übergeben wird und ermöglicht die Wiedergabe, mit der Sie die Logik in Ihrem Code lokal mit Visual Studio debuggen können.

Wenn der **Plug-In-Profiler** für Ihre Common Data Service-Instanz installiert ist, sehen Sie ihn im PRT am unteren Rand der Liste **Registrierte Plug-Ins & benutzerdefinierte Workflowaktivitäten**.

![Plug-In-Profiler im Plug-in-Registrierungstool](media/Plug-in-Profiler.png)

## <a name="profile-a-workflow-activity"></a>Profilierung einer Workflow-Aktivität

Um eine Workflow-Aktivität zu profilieren, klicken Sie mit der rechten Maustaste auf den **Plug-In-Profiler** und wählen Sie **Workflowprofilierung starten**.

![Workflowprofilierung starten](media/Start-profiling-workflow.png)

Dadurch wird das Dialogfeld **Profiler-Einstellungen** geöffnet, das die folgenden Optionen bietet:

![Profiler-Einstellungsdialog](media/profiler-settings.png)

|Feld|Beschreibung|
|--|--|
|**Workflow**|Wählen Sie die Workflow- oder benutzerdefinierte Aktion aus, die die Workflowaktivität enthält, die Sie debuggen möchten.|
|**Schritte**|Wählen Sie die spezifischen Schritte innerhalb dieses Workflows oder dieser benutzerdefinierten Aktion aus, die Sie debuggen möchten.|
|**Profilspeicher angeben**|Wir empfehlen Ihnen, **In Entität speichern** zu wählen.|
|**Profilereinstellung festlegen**|Wenn Sie mit einem System arbeiten, in dem der Workflow häufig ausgeführt wird, können Sie die Auswirkungen auf die Leistung reduzieren, indem Sie die Anzahl der erfassten Profile begrenzen.|
|**Sichere Konfiguration einbeziehen**|Dies bietet die Möglichkeit, potenziell sensible Daten, die als sichere Konfiguration übergeben werden könnten, nicht zu sehen.|

Klicken Sie auf **OK**, um Ihre Einstellungen zu speichern.

> [!NOTE]
> Zum Zeitpunkt dieses Schreibens können Sie den folgenden Fehler sehen:
> 
> ![Fehler beim Festlegen der Workflowaktivitätsprofiler-Einstellungen](media/error-setting-profiler-settings-workflow-activity.png)
> 
> Die Details dieses Fehlers beinhalten die Meldung: `Automatic workflow cannot be published if no activation parameters have been specified.`
> 
> Die Profileinstellungen wurden erfolgreich gespeichert. Dieser Fehler tritt auf, weil der Prozess der Profilerstellung einer benutzerdefinierten Workflow-Aktivität eine Kopie des Workflows erstellt und sowohl den ursprünglichen Workflow als auch die Kopie deaktiviert. Sie müssen die Profilkopie neu konfigurieren und aktivieren, um ein Profil zu erfassen.  Weitere Informationen finden Sie in den folgenden Schritten:

## <a name="capture-a-profile"></a>Erfassen eines Profils

Wenn ein Profil für den Workflow konfiguriert wird, das eine benutzerdefinierte Workflow-Aktivität enthält, wird eine Kopie des ursprünglichen Workflows erstellt und der Text `(Profiled)` an den Namen angehängt. Sowohl das Original als auch die Kopie der Workflows sind deaktiviert.

> [!NOTE]
> Wenn Sie nicht in der **Standard** lösung des Systems arbeiten, sehen Sie möglicherweise den kopierten Workflow nicht, da er zu dieser Lösung hinzugefügt wird. Um den kopierten Workflow der Lösung anzuzeigen, die Sie verwenden, müssen Sie auf **Vorhandenes Element hinzufügen** klicken und anschließend diese Kopie Ihrer Lösung hinzuzufügen.

Die deaktivierten Workflows sollten wie folgt aussehen:

![Kopierter Workflow im Projektmappen-Explorer](media/copied-workflow-solution-explorer.png)

Beim Kopieren des Workflows geht ein Teil der Konfiguration verloren. Wenn Sie versuchen, den kopierten Workflow zu aktivieren, erhalten Sie folgende Fehlermeldung: `An automatic process cannot be activated if no activation parameters have been specified. Add activation parameters, and then activate. ...`

Das bedeutet, dass Sie die Eigenschaften **Starten bei** des Workflows neu konfigurieren müssen. In diesem Fall möchten wir den Workflow festlegen, dass er beginnt, wenn sich das Feld **Kontoname** ändert:

![Start bei Feld Einstellungsänderungen](media/start-when-field-changes.png)

Klicken Sie auf die Schaltfläche **Auswählen**, um das Feld **Kontoname** auszuwählen.

![Starten bei Feld Änderungseinstellung Feld Dialog auswählen](media/start-when-field-change-field-select-dialog.png)

Der kopierte Profilworkflow wird ebenfalls in einen Hintergrund-(asynchronen) Workflow umgewandelt. Es ist einfacher, einen Echtzeit-(synchronen) Workflow zu testen, deshalb klicken Sie in der Menüleiste auf **In einen Echtzeitworkflow konvertieren**.

Speichern Sie den kopierten Profilworkflow und aktivieren Sie ihn.

Aktualisieren Sie in einer App, die mit Ihrer Common Data Service-Instanz verbunden ist oder durch die Verwendung der Webservices den Wert **Kontoname** einer Firmenentität. Dadurch wird eine Instanz des Kontexts erfasst, die an Ihre benutzerdefinierte Workflowaktivität übergeben wird, und sie wird als Profildatensatz im System gespeichert.

> [!TIP]
> Wenn Ihr Workflow asynchron ist, stellen Sie sicher, dass er abgeschlossen ist, bevor Sie mit dem nächsten Schritt fortfahren. Gehen Sie zu Einstellungen > Systemaufträge und überprüfen Sie, ob der Workflow erfolgreich war.

## <a name="stop-profiling"></a>Stoppen Sie die Profilerstellung

Nachdem Sie das zu debuggende Profil erfasst haben, sollten Sie die Profilerstellung des Plug-Ins beenden.  

Um die Profilerstellung zu beenden, heben Sie die Registrierung des Workflows mit dem PRT auf.

![Workflowprofilierung stoppen](media/stop-profiling.png)

Dadurch wird die Kopie des erstellten Workflows gelöscht.

> [!IMPORTANT]
> Der kopierte Workflow wird weiterhin deaktiviert. Sie müssen ihn manuell reaktivieren, wenn Sie möchten, dass er angewendet wird.

## <a name="debug-your-assembly"></a>Debuggen Ihres Assemblys

1. Klicken Sie im PRT auf **Plug-In-Ausführung wiederholen**.
1. Klicken Sie im **Plug-In-Ausführung wiederholen Dialog** auf der Registerkarte **Setup** auf die Schaltfläche Herunterladen, um ein **Profil** auszuwählen.

    ![Plug-In-Ausführung wiederholen-Dialog](media/replay-plugin-execution-dialog.png)

    > [!NOTE]
    > Die Registerkarten **Unsichere Konfiguration**, **Sichere Konfiguration** und **Einstellungen** werden nicht für das Debuggen von Workflowaktivitäten verwendet. Sie werden nur verwendet für Plug-Ins.

1. Wählen Sie im Dialogfeld **Profil aus CRM auswählen** das aktuellste Profil aus, das dasjenige darstellt, das Sie gerade generiert haben.

    ![Wählen Sie das Profil aus, die Sie soeben generiert haben](media/select-profile-from-crm-dialog.png)

    > [!NOTE]
    > Sie können die erfassten Profile in der **benutzerdefinierten Dynamics 365**-Webanwendung verwalten, indem Sie zu **Einstellungen** > **Erweiterungen** > **Plug-In-Profile** navigieren.

1. Klicken Sie auf **Auswählen**, um den Dialog zu schließen.
1. Klicken Sie im Feld **Assembly-Speicherort** auf die Schaltfläche Auslassungspunkte (**...**), um den Speicherort der Assemblys hinzufügen, die die Workflowaktivität enthalten, die Sie debuggen.
1. Öffnen Sie Ihr Workflowaktivitätsprojekt in Visual Studio.
1. Fügen Sie einen Haltepunkt zu einer Zeile innerhalb der `Execute`-Methode Ihrer Workflowaktivität hinzu.

    ![Festlegen eines Haltepunktes](media/set-breakpoint-in-workflow-activity.png)

1. Wählen Sie im **Debuggen**-Menü **An den Prozess anhängen...**.
1. Suchen Sie nach dem Prozess für `PluginRegistration.exe`.

    > [!TIP]
    > Der Suchfilter hilft Ihnen, diesen schneller zu finden. Die dem Prozess zugeordnete Prozess-ID (PID) wird für jede Sitzung unterschiedlich sein. Die PID wird im Dialogfeld **Plug-In-Ausführung wiederholen** unter **Plug-In Verfolgung** angezeigt.

    ![Visual Studio – Dialog "Zum Verarbeiten anfügen"](media/visual-studio-attach-to-process-dialog.png)

1. Klicken Sie auf **Anfügen**, um Ihren Visual Studio-Debugger an die PRT-Anwendung anzuhängen, die die Prozesswiedergabe ausführen soll.
1. Klicken Sie im Dialogfeld **Plug-In-Ausführung wiederholen** im PRT auf die Schaltfläche **Ausführung beginnen**.

Sie sollten nun in der Lage sein, durch Ihren Code zu navigieren und Ihre Workflowaktivität mit Visual Studio zu debuggen.



### <a name="more-information"></a>Weitere Informationen

[Debuggen von Plug-Ins](../debug-plug-in.md)<br />
[Lernprogramm: Debuggen eines Plug-Ins](../tutorial-debug-plug-in.md)

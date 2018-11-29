---
title: 'Lernprogramm: Debuggen eines Plug-In (Common Data Service für Apps) | MicrosoftDocs'
description: 'Dieses Lernprogramm ist das zweite in der Serie, in der Ihnen gezeigt wird, wie Sie mit Plug-Ins arbeiten. '
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="tutorial-debug-a-plug-in"></a>Lernprogramm: Debuggen eines Plug-Ins

Dieses Lernprogramm ist das zweite in der Serie, in der Ihnen gezeigt wird, wie Sie mit Plug-Ins arbeiten. 

- [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)
- Lernprogramm: Debuggen eines Plug-Ins (Dieses Lernprogramm)
- [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)

Eine detaillierte Erläuterung der unterstützenden Konzepte und technischen Details finden Sie unter:

- [Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](plug-ins.md)
- [Schreiben eines Plug-Ins](write-plug-in.md)
- [Registrieren eines Plug-Ins](register-plug-in.md)
- [Debuggen von Plug-Ins](debug-plug-in.md)


## <a name="goal"></a>Ziel

Da ein Plug-In auf einen Remoteserver ausgeführt wird, können Sie keinen Debugger an den Prozess anhängen. Der Plug-In-Profiler erfasst ein Profil eines ausführenden Plug-Ins und ermöglicht Ihnen die lokale Ausführung des Plug-Ins mit Visual Studio erneut wiederzugeben.



## <a name="prerequisites"></a>Voraussetzungen

- Alle Voraussetzungen für [Lernprogramm: Schreiben und Registrieren eines Plug-Ins](tutorial-write-plug-in.md) gelten. Informationen unter [Voraussetzungen:](tutorial-write-plug-in.md#prerequisites).
- Wenn Sie das vorherige Lernprogramm nicht abgeschlossen haben, können Sie die folgenden allgemeinen Schritte mit einem anderen registrierten Plug-In verwenden.

## <a name="install-plug-in-profiler"></a>Plug-In-Profiler installieren

1. Wenn das Plug-In-Registrierungstool nicht bereits installiert und geöffnet ist, führen Sie die Schritte in [Lernprogramm: Schreiben und Registrieren eines Plug-Ins](tutorial-write-plug-in.md) aus, um es zu öffnen. Schließen Sie den Abschnitt [Herstellen einer Verbindung mit dem Plug-In-Registrierungstool](tutorial-write-plug-in.md#connect-using-the-plug-in-registration-tool) ab.
1. Klicken Sie im Plug-In-Registrierungstool auf **Profiler installieren**.

    ![Profiler installieren](media/tutorial-debug-plug-in-install-profiler.md.png)

1. Dies installiert eine neue verwaltete Lösung namens Plug-in Profiler in Ihrer CDS for App-Umgebung. Es dauert eine Minute oder zwei, den Vorgang abzuschließen.

## <a name="start-profiling"></a>Profilierung starten

1. Wählen Sie im Plug-In-Registrierungstool den Schritt **(Schritt) BasicPlugin.FollowupPlugin: Erstellen einer Firma** aus, den Sie zuvor registriert haben, und klicken Sie auf **Profilerstellung starten**.

    ![Profilierung starten](media/tutorial-debug-plug-in-start-profiling.png)

1. Nehmen Sie im Dialog **Profiler-Einstellungen** die Standardeinstellungen an und klicken Sie auf **OK**, um den Dialog zu schließen.

    ![foo](media/tutorial-debug-plug-in-profiler-settings.png)

## <a name="capture-a-profile"></a>Erfassen eines Profils

1. Erstellen Sie in Ihrer modellgesteuerten App eine neue Firma, um das Plug-In auszulösen. Dadurch wird eine Instanz des ausgeführten Plug-Ins erfasst und als Profildatensatz im System gespeichert.
1. Im Plug-In-Registrierungstool klicken Sie auf **Debuggen**

    ![Auf "Debuggen" klicken](media/tutorial-debug-plug-in-capture-profile-debug.png)

1. Im Dialogfeld **Plug-In-Ausführung wiederholen** auf der Registerkarte **Setup** klicken Sie auf das Symbol ![Auswählen des Profilbefehls](media/tutorial-debug-plug-in-select-profile-command.png), um das Dialogfeld **Profil von CRM auswählen** zu öffnen.
1. Wählen Sie im Dialogfeld **Profil von CRM auswählen** das Profil aus, in dem **Typname** **BasicPlugin.FollowupPlugin** entspricht und das aufgezeichnete Profil darstellt wird, als Sie das Plug-In zuletzt starteten.

    ![Profil aus dem CRM-Dialog auswählen](media/tutorial-debug-plug-in-select-profile-dialog.png)

## <a name="debug-your-plug-in"></a>Ihr Plug-In-debuggen

1. Im Dialogfeld **Plug-In-Ausführung wiederholen** auf der Registerkarte **Setup** im Abschnitt **Assembly angeben** klicken Sie auf die Schaltfläche mit den Auslassungspunkten (**…**) und wählen den Speicherort Ihrer `BasicPlugin.dll`aus.

    ![Wiederholung der Plug-in-Ausführung](media/tutorial-debug-plug-in-replay-plug-in-execution.png)

1. In Ihrem Visual Studio-Projekt legen Sie einen Haltepunkt in Ihrer Plug-In-Klasse fest.

    ![Festlegen eines Haltepunktes](media/tutorial-debug-plug-in-set-break-point.png)

1. In Ihrem Visual Studio-Projekt wählen Sie **Debuggen** > **Zum Verarbeiten anfügen...** aus.

    ![Befehl "Zum Verarbeiten anfügen"](media/tutorial-debug-plug-in-attach-to-process.png)

1. Wählen Sie den Prozess **PluginRegistration.exe** aus, und klicken Sie auf **Anfügen**.

    ![Dialog "Zum Verarbeiten anfügen"](media/tutorial-debug-plug-in-attach-to-process-dialog.png)

    > [!NOTE]
    > Sie sollten sehen, dass das Plug-In-Registrierungstool jetzt im Debugmodus ausgeführt wird.

1. Klicken Sie im Dialogfeld **Plug-In-Ausführung wiederholen** auf **Ausführung beginnen**.

    ![Ausführung beginnen](media/tutorial-debug-plug-in-replay-plug-in-execution-debug.png)

1. In Ihrem Visual Studio-Projekt sollten Sie sehen, dass der Code am zuvor festgelegten Haltepunkt angehalten wird. 

    ![Haltepunkttreffer](media/tutorial-debug-plug-in-breakpoint-hit.png)

1. Sie können den Code nun schrittweise durchlaufen, um ihn zu debuggen.


## <a name="repeat"></a>Wiederholen

Zur Wiederholung: Wählen Sie in Ihrem Visual Studio-Projekt **Debuggen** > **Wieder anfügen** zur Verarbeitung aus, und klicken Sie im Dialogfeld **Plug-In-Ausführung wiederholen** klicken Sie erneut auf **Ausführen starten**.

## <a name="stop-profiling"></a>Stoppen Sie die Profilerstellung

1. Schließen Sie den Dialog **Plug-In-Ausführung wiederholen**
1. Im Plug-In-Registrierungstool klicken Sie auf **Profilierung beenden**

    ![Stoppen Sie die Profilerstellung](media/tutorial-debug-plug-in-stop-profiling.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu allgemeinen Optionen bei Plug-Ins finden Sie unter [Lernprogramm: Ein Plug-In aktualisieren](tutorial-update-plug-in.md)

Wenn Sie nicht beim nächsten Lernprogramm fortsetzen, sollten Sie die Registrierung der BasicPlugin-Assembly, die Sie in diesem Schritt erstellt haben, aufheben. Anweisungen finden Sie unter [Registrierung der Assembly, des Plug-Ins und des Schritts aufheben](tutorial-update-plug-in.md#unregister-assembly-plug-in-and-step).


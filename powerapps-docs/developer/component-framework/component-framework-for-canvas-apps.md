---
title: Codekomponenten für Canvas-Apps | Microsoft-Dokumentation
description: Erstellen von Codekomponenten für Canvas-Apps
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 11/26/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: e10a7c01e40e65e0a65f82713ba920500b8ee5bf
ms.sourcegitcommit: 13d4042c7bd73580cc8c595e137de7e7fec22875
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "3170226"
---
# <a name="code-components-for-canvas-apps"></a>Codekomponenten für Canvas-Apps

Das Power Apps component framework ermöglicht es App-Entwicklern, Codekomponenten für die Verwendung in einer App oder über Apps zu erstellen. Weitere Informationen: [Übersicht über das Power Apps Komponenten Framework](overview.md) 

In dieser öffentlichen Vorschau ermöglicht das Power Apps component framework den Herstellern von Anwendungen, Codekomponenten zu erstellen, zu debuggen, zu importieren und mit dem Power Apps-CLI-Werkzeug zu Canvas-Anwendungen hinzuzufügen. In dieser öffentlichen Vorschau werden nur bestimmte APIs unterstützt. Wir empfehlen Ihnen, jede API zu prüfen, um festzustellen, ob sie Canvas-Anwendungen unterstützt. 

> [!WARNING]
> Codekomponenten enthalten Code, der möglicherweise nicht von Microsoft generiert werden kann und ggf. auf Sicherheitstoken und Daten zugreifen kann. Wenn Sie Codekomponenten zu einer App hinzufügen, sollten Sie sicherstellen, dass die Codekomponentenlösungen von einer vertrauenswürdigen Quelle stammen.

## <a name="prerequisites"></a>Voraussetzungen

1. Eine Power Apps-Lizenz ist erforderlich. Weitere Informationen: [Power Apps component framework Lizenz](overview.md#licensing)
2. Es sind Systemadministratorrechte erforderlich, um die Power Apps-Komponentenfunktion in der Umgebung zu aktivieren.

## <a name="enable-power-apps-component-framework-feature"></a>Aktivieren der Funktion des Power Apps component framework

Um Codekomponenten zu einer App hinzuzufügen, müssen Sie die Funktion des Power Apps component framework in jeder Umgebung aktivieren, in der Sie sie verwenden möchten. So aktivieren Sie eine Umgebung für die Verwendung von Codekomponenten in ihren Apps:

1. Melden Sie sich bei [Power Apps](https://powerapps.microsoft.com/) an.

2. Klicken Sie auf das Symbol **Einstellungen** und wählen dann **Admin Center** aus.
    
    ![Einstellungen und Admin Center](media/select-admin-center-from-settings.png "Einstellungen und Admin Center") 

3. Wählen Sie die Registerkarte **Umgebungen** im linken Bereich und wählen Sie die Umgebung aus, in der Sie diese Funktion aktivieren möchten. Wählen Sie die Auslassungspunkte (**...**) und wählen Sie dann **Einstellungen**.

4. Wählen Sie auf der Registerkarte **Produkte** die Option **Funktionen** aus.

   ![Aktivieren von Power Apps Component Framework](media/enable-pcf-feature.png "Aktivieren des Power Apps Component Framework")

5. Stellen Sie den Schalter in der Liste der verfügbaren Funktionen auf **Ein** unter **Power Apps component framework für Canvas-Apps** und klicken Sie auf **speichern**.

6. Öffnen Sie nun die App, in der Sie die Codekomponente hinzufügen möchten, und navigieren Sie zu **Datei** > **Einstellungen** und wählen Sie **Erweiterte Einstellungen**.

   ![Aktivieren Sie Komponenten für das Power Apps Component Framework](media/enable-components-for-pcf.png "Aktivieren Sie Komponenten für Power Apps Component Framework")
   
7. Setzen Sie den **Komponenten**-Schalter auf **Ein** unter dem Abschnitt **Experimentelle Funktion**.

## <a name="implementing-code-components"></a>Implementieren von Codekomponenten

Nachdem Sie das Feature des Power Apps component framework in Ihrer Umgebung aktiviert haben, können Sie mit der Implementierung der Logik für Codekomponenten beginnen.

 Das Thema [Erstellen Ihrer ersten Codekomponente](implementing-controls-using-typescript.md) demonstriert den schrittweisen Prozess zum Erstellen von Codekomponenten.

## <a name="add-components-to-a-canvas-app"></a>Hinzufügen von Komponenten zu einer Canvas-App

So fügen Sie Codekomponenten zu einer Canvas-App hinzu:

1. Navigieren zu Power Apps Studio.
2. Erstellen einer neuen Canvas-App oder Bearbeiten einer vorhandenen App, der Sie die Codekomponente hinzufügen möchten.

   > [!IMPORTANT]
   > Stellen Sie sicher, dass die Lösungs-ZIP-Datei bereits nach Common Data Service [importiert](https://docs.microsoft.com/powerapps/maker/common-data-service/import-update-export-solutions) wurde, bevor Sie mit dem nächsten Schritt fortfahren.

3. Gehen Sie zu **Einfügen** > **Benutzerdefiniert** > **Komponente importieren**. 
 
    ![Komponenten einfügen](media/insert-components-import.png "Komponenten einfügen")

4. Wähle Sie die Registerkarte **Code**, fügen Sie eine Komponente aus der Liste hinzu, und wählen Sie dann **Importieren**. 

    ![Beispielkomponente importieren](media/import-component-add-sample-component.png "Beispielkomponente importieren")

5. Klicken Sie auf das Symbol **+** im linken Bereich und erweitern Sie die Registerkarte Codekomponenten, um die Beispielkomponente hinzuzufügen.

   ![Beispielkomponente hinzufügen](media/add-sample-component-from-list.png "Beispielkomponente hinzufügen")

## <a name="delete-a-code-component"></a>Löschen einer Codekomponente 

Wenn Sie eine Codekomponente aus einer Canvas-App löschen möchten, wählen Sie die Codekomponente, die Sie löschen möchten und dann die Schaltfläche **Löschen** aus dem Menü aus. Wenn die Codekomponente aus der App gelöscht wird, werden alle Codekomponentenelemente aus der App und dem App-Paket gelöscht.

## <a name="update-existing-code-components"></a>Aktualisieren vorhandener Codekomponenten

Immer wenn Sie die Codekomponenten aktualisieren und die Änderungen in der Laufzeit sehen möchten, müssen Sie das `version`-Attribut in der Manifestdatei anstoßen. Es wird empfohlen, die Version der Komponente immer anzustoßen, wenn Sie Änderungen vornehmen.

> [!NOTE]
> Vorhandene Codekomponenten werden nur aktualisiert, sofern die App geschlossen oder in Power Apps Studio erneut geöffnet wird. Wenn Sie die App erneut öffnen, werden sie aufgefordert, die Codekomponenten zu aktualisieren. Wenn Sie die Codekomponenten einfach löschen oder sie wieder in die App hinzufügen, werden die Komponenten nicht aktualisiert.

## <a name="see-also"></a>Siehe auch

[Power Apps component framework Übersicht](overview.md)<br/>
[Erstellen Sie Ihre erste Codekomponente](implementing-controls-using-typescript.md)<br/>
[Erlernen des Power Apps component framework](https://docs.microsoft.com/learn/paths/use-power-apps-component-framework)

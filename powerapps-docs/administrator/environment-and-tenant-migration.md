---
title: Migrieren von Apps zwischen Umgebungen und Mandanten | Microsoft-Dokumentation
description: Exemplarische Vorgehensweise zum Migrieren von PowerApps-Apps zwischen Umgebungen und Mandanten
author: jamesol-msft
manager: kfile
ms-topic: conceptual
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.author: jamesol
ms.openlocfilehash: 3a064bdb3f75bf45047e3ae0ff465fde1d2b66fa
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
---
# <a name="environment-and-tenant-app-migration-through-packaging"></a>Migration der Umgebungs- und Mandanten-App durch Paketerstellung
Erfahren Sie, wie Sie Ressourcen mithilfe von Paketerstellung von einer Umgebung zu einer anderen migrieren. Diese Umgebungen können innerhalb des gleichen Mandanten oder mandantenübergreifend sein.

## <a name="the-scenario"></a>Das Szenario
Ein gängiges Szenario: Bei Test- oder Entwicklungsumgebungen und bei einer Produktionsumgebung möchten Sie möglicherweise Ressourcen migrieren. Entwickler und Tester haben weitreichenden Zugriff auf die Apps in ihrer Umgebung. Aber bei der Migration einer neuen App bis hin zur Produktion hat diese Umgebung eine strenge Kontrolle über Berechtigungen zum Aktualisieren und Ändern der App.

In einem weiteren Szenario verfügt jeder Kunde über seine eigene Umgebung und seine eigenen Daten. Wenn ein neuer Kunde hinzugefügt wird, wird eine neue Umgebung für ihn erstellt, und Sie würden Apps in seine Umgebung migrieren.

## <a name="which-resources-can-i-migrate-through-packaging"></a>Welche Ressourcen können mithilfe von Paketerstellung migriert werden?
Beim Exportieren einer App werden ihre abhängigen Ressourcen ebenfalls im Paket exportiert.  Zunächst wird, wie in der Tabelle unten erläutert, nur eine Teilmenge aller möglichen Ressourcentypen unterstützt.

| Ressourcentyp | Unterstützt | Importoptionen |
| --- | --- | --- |
| App |Ja |Es gibt zwei Möglichkeiten, eine App in eine Umgebung zu importieren: <ol><li><b>Neu erstellen</b>: Die App wird als neue App in der Umgebung erstellt, in die das Paket importiert wird.</li> <li><b>Aktualisieren</b>: Die App ist in der Umgebung bereits vorhanden und wird beim Importieren des Pakets aktualisiert.</li></ol> |
| Flow |Ja |Es gibt zwei Möglichkeiten, einen Flow in eine Umgebung zu importieren: <ol><li><b>Neu erstellen</b>: Der Flow wird als neuer Flow in der Umgebung erstellt, in die das Paket importiert wird.</li> <li><b>Aktualisieren</b>: Der Flow ist in der Umgebung bereits vorhanden und wird beim Importieren des Pakets aktualisiert.</li></ol> <b>Hinweis:</b> Alle Ressourcen, von denen der Flow abhängt, werden ebenfalls in das exportierte App-Paket eingeschlossen und müssen mit dem importierten Paket konfiguriert werden. |
| Benutzerdefinierte Connectors |Nein |Wenn eine App von einem benutzerdefinierten Connector abhängt, wird das Exportieren des Connectors als Teil des Pakets derzeit <b>nicht unterstützt</b>. <p></p> Wenn Sie über eine App verfügen, die sich auf einen benutzerdefinierten Connector stützt, haben Sie derzeit lediglich die Möglichkeit, den Connector beim Importieren des Pakets in der Zielumgebung manuell neu zu erstellen oder zu aktualisieren. |
| Verbindungen |Nein |Wenn eine App von einer Verbindung abhängt (z.B. einer SQL-Verbindung mit Anmeldeinformationen), wird das Exportieren der Verbindung oder der Anmeldeinformationen als Teil des Pakets derzeit nicht unterstützt. <p></p> Wenn Sie über eine App verfügen, die sich auf eine freigegebene Verbindung (wie SQL) stützt, haben Sie derzeit lediglich die Möglichkeit, diese Verbindung mit den entsprechenden Anmeldeinformationen in der Zielumgebung neu zu erstellen und die Verbindung auszuwählen, wenn Sie das Paket importieren. |
| CDS-Anpassungen |Nein |Das Exportieren von CDS-Anpassungen ist nicht mehr in den Packprozess integriert. Sie müssen sie jetzt, wie nachfolgenden beschrieben, exportieren und die Standardumgebungslösung importieren. |
| Gateways |Nein |Gateways werden nur in Standardumgebungen (und {Mandantenname}-Umgebungen (von der Vorschau)) unterstützt, sodass Export/Migration nicht unterstützt werden. |

## <a name="how-do-i-get-access-to-packaging-for-my-app"></a>Wie erhalte ich Zugriff auf Pakete für meine App?
Die Möglichkeit zum Exportieren von Apps ist für alle Benutzer mit der Berechtigung „Kann bearbeiten“ für die App verfügbar.

Die Möglichkeit zum Importieren ist für alle Benutzer mit der Berechtigung „Umgebungsersteller“ in der Zielumgebung verfügbar.

Benutzer benötigen einen PowerApps-Plan 2 oder eine PowerApps-Plan 2-Testlizenz, um eine App exportieren oder importieren zu können.

> [!NOTE]
> Während der Vorschauphase für die Paketerstellung kann jeder Benutzer mit einer gültigen PowerApps-Lizenz Pakete für seine Apps und Umgebungen testen.

## <a name="exporting-an-app"></a>Exportieren einer App
1. Klicken oder tippen Sie unter http://web.powerapps.com erst auf **Apps**, dann auf die Auslassungspunkte für die zu migrierende App, und klicken oder tippen Sie anschließend auf **Export (preview)** (Exportieren (Vorschau)).

    ![Auswählen von „Exportieren“](./media/environment-and-tenant-migration/select-export.png)
2. Wenn die Seite zum Exportieren von Paketen geöffnet wird, geben Sie einen Namen und eine Beschreibung für das Paket ein.

    ![Überprüfen der Paketdetails](./media/environment-and-tenant-migration/package-details.png)
3. Im Abschnitt „Paketinhalt überprüfen“ können Sie optional Anmerkungen oder Notizen hinzufügen oder die Einstellung dafür ändern, wie die einzelnen Ressourcen während des Paketimports in die Zielumgebung importiert werden.

    ![Konfigurieren des Paketinhalts](./media/environment-and-tenant-migration/export-package-content.png)

4. Wählen Sie nach Abschluss des Vorgangs **Exportieren** aus, und der Download der Paketdatei beginnt innerhalb weniger Sekunden.

## <a name="importing-an-app"></a>Importieren einer App
1. Klicken oder tippen Sie unter http://web.powerapps.com erst auf **Apps** und anschließend auf **Paket importieren (Vorschau)**.

    ![Auswählen von „Importieren“](./media/environment-and-tenant-migration/select-import.png)
2. Wählen Sie **Hochladen** aus, und wählen Sie die App-Paketdatei aus, die importiert werden soll.

    ![Auswählen der Paketdatei](./media/environment-and-tenant-migration/select-file.png)
3. Wenn das Paket hochgeladen wurde, müssen Sie den Paketinhalt überprüfen und weitere Eingaben für alle mit einem roten Symbol gekennzeichneten Elemente vornehmen; hierzu wählen Sie das Schraubenschlüsselsymbol für das betreffende Element aus und geben die erforderlichen Informationen ein.

    ![Überprüfen des Paketinhalts](./media/environment-and-tenant-migration/import-package-content.png)
4. Sobald Sie alle erforderlichen Informationen eingegeben haben, wählen Sie **Importieren** aus.

    ![Aktualisierter gepackter Inhalt](./media/environment-and-tenant-migration/import-package-content-dirty.png)
5. Bei Abschluss des Importvorgangs werden Sie automatisch zu einer Seite umgeleitet (die der unten stehenden ähnelt), auf der mitgeteilt wird, ob der Importvorgang erfolgreich war oder fehlgeschlagen ist.

    ![Überprüfen der Importergebnisse](./media/environment-and-tenant-migration/import-results.png)

> [!NOTE]
>  Wenn Sie eine App importieren und sich entscheiden, eine vorhandene App zu **aktualisieren**, werden die neuen Änderungen als Entwurf der Anwendungen gespeichert.  Sie müssen diese Änderungen [veröffentlichen](http://powerapps.microsoft.com/tutorials/save-publish-app/#publish-an-app), damit sie für alle anderen Benutzer der Anwendungen verfügbar sind.
>
>

## <a name="exporting-cds-customizations-and-model-driven-apps"></a>Exportieren von CDS-Anpassungen und modellgesteuerten Apps
Sie können sämtliche Anpassungen von Entitäten oder Optionen und alle modellgesteuerten Apps exportieren, die Sie unter https://web.powerapps.com erstellt haben, indem Sie die Standardumgebungslösung wie folgt exportieren:
> [!NOTE]
>  Mehr Informationen über Lösungen in PowerApps erhalten Sie unter [Einführung in Lösungen](../developer/common-data-service/introduction-solutions.md).
>
>

1. Wählen Sie unter http://web.powerapps.com den Designmodus **Model-driven (preview)** (Modellgesteuert (Vorschau)) in Ihrer Umgebung aus.

    ![Auswählen des Designmodus „Modellgesteuert“](./media/environment-and-tenant-migration/select-model-driven.png)

2. Klicken Sie im Navigationsbereich links auf **Erweitert**, um den Projektmappen-Explorer für die Standardlösung dieser Umgebung zu starten.

    ![„Erweitert“ auswählen](./media/environment-and-tenant-migration/select-advanced.png)

3. Klicken Sie auf **Projektmappe exportieren**, und schließen Sie den erforderlichen Schritt ab.  Innerhalb von wenigen Sekunden startet der Download der Lösungspaketdatei.

    ![Auswählen von „Exportieren“](./media/environment-and-tenant-migration/select-export-solution.png)

## <a name="importing-cds-customization-and-model-driven-apps"></a>Importieren von CDS-Anpassungen und modellgesteuerten Apps
Sie können CDS-Lösungspakete derzeit leider nur manuell importieren. Es wird an einer Verbesserung dieses Vorgangs gearbeitet.

1. Wählen Sie unter http://web.powerapps.com den Designmodus **Model-driven (preview)** (Modellgesteuert (Vorschau)) in Ihrer Umgebung aus.

    ![Auswählen des Designmodus „Modellgesteuert“](./media/environment-and-tenant-migration/select-model-driven.png)

2. Klicken Sie im Navigationsbereich links auf **Erweitert**, um den Projektmappen-Explorer für die Standardlösung dieser Umgebung zu starten.

    ![„Erweitert“ auswählen](./media/environment-and-tenant-migration/select-advanced.png)

3. Kopieren Sie die URL aus Ihrem Browser, nehmen Sie die folgenden Änderungen vor, und navigieren Sie dann zu der neuen URL in Ihrem Browser:

    * Aktuelle URL-Struktur: https://{orguniquename}.crm.dynamics.com/tools/solution/edit.aspx?id={solutionname}

        ![URL bearbeiten](./media/environment-and-tenant-migration/edit-url.png)

    * Neue URL-Struktur: https://{orguniquename}.crm.dynamics.com/tools/solution/SolutionImportWizard.aspx

        ![Paket auswählen](./media/environment-and-tenant-migration/select-package.png)

4. Wählen Sie die CDS-Lösungspaketdatei aus, die Sie importieren möchten, und beenden Sie den Assistenten.

5. Wenn der Import erfolgreich durchgeführt wurde, wird zur Bestätigung der folgende Dialog angezeigt. Damit die Änderungen für andere Benutzer verfügbar sind, die ebenfalls in der Umgebung Anpassungen vornehmen, klicken Sie auf **Publish All Customizations** (Alle Anpassungen veröffentlichen).

    ![Import erfolgreich](./media/environment-and-tenant-migration/successful-import.png)

---
title: Portal Konfiguration migrieren | MicrosoftDocs
description: Erfahren Sie, wie Sie die Portal Konfiguration migrieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0aa057594b500c7019a4d645c70cafcfff183608
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543053"
---
# <a name="migrate-portal-configuration"></a>Migrieren der Portalkonfiguration

Die Portal Entwicklung umfasst mehrere Konfigurationen und Anpassungen, um eine gewünschte Benutzerfunktion für die Endbenutzer des Portals zu erzielen.

Nachdem Sie die Entwicklung oder Konfiguration Ihrer Portal Instanz abgeschlossen haben, möchten Sie möglicherweise Ihre neueste Portal Konfiguration von der Entwicklung zu Test-oder Produktionsumgebungen migrieren. Bei der Migration wird die vorhandene Konfiguration aus der Quell Common Data Service Umgebung exportiert und anschließend in die Ziel Common Data Service Umgebung importiert.

Zum Exportieren von Konfigurationsdaten müssen Sie das Konfigurations Migrationstool und eine Portal spezifische Konfigurations Schema Datei verwenden. Weitere Informationen zu diesem Tool finden Sie unter [Verwalten von Konfigurationsdaten](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data).

> [!NOTE]
> - Es wird empfohlen, die neueste Version des Konfigurations Migrationstools zu verwenden. Das Konfigurations Migrationstool kann von nuget heruntergeladen werden. Weitere Informationen zum Herunterladen des Tools finden [Sie unter Herunterladen von Tools von nuget](https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget).
> - Die minimale Lösungs Version von Portalen, die von Schema Dateien für die Konfigurations Migration unterstützt wird, ist 8.4.0.275. Es wird jedoch empfohlen, dass Sie die neueste Projektmappenversion verwenden.

Schema Dateien sind für die folgenden Portal Typen verfügbar:
- [Communityportal](https://go.microsoft.com/fwlink/p/?linkid=2019704)
- [Self-Service-Portal für Kunden](https://go.microsoft.com/fwlink/p/?linkid=2019705)
- [Partner Portal](https://go.microsoft.com/fwlink/p/?linkid=2019803)
- [Personal Self-Service-Portal](https://go.microsoft.com/fwlink/p/?linkid=2019802)
- [Benutzerdefiniertes Portal](https://go.microsoft.com/fwlink/p/?linkid=2019804)

Die Standardschema Dateien enthalten Informationen zu Portal Entitäten, Beziehungen und Eindeutigkeits Definitionen für jede Entität. Weitere Informationen: [Exportieren von Portal-Konfigurationsdaten](#export-portal-configuration-data)

Nachdem Sie die Konfigurationsdaten exportiert haben, müssen Sie Sie in die Zielumgebung importieren. Weitere Informationen: [Importieren von Portal Konfigurationsdaten](#import-portal-configuration-data)

> [!NOTE]
> Die Schema Dateien werden bereitgestellt, um den erforderlichen Aufwand für die Erstellung eines Schemas zu verringern. Das Schema kann mithilfe der vom Tool bereitgestellten Standardmethoden auf Ihre Implementierung zugeschnitten werden. Schema Dateien können im Konfigurations Migrationstool geladen und so geändert werden, dass Entitäten, Attribute usw. hinzugefügt, entfernt und geändert werden.

## <a name="export-portal-configuration-data"></a>Portal Konfigurationsdaten exportieren

Sie können Portal Konfigurationsdaten mithilfe von Portal spezifischen Konfigurations Schema Dateien aus einem Quellsystem exportieren.

1.  Laden Sie das Konfigurations Migrationstool herunter, und extrahieren Sie es in den gewünschten Ordner.

2.  Laden Sie eine Portal Konfigurationsschema-Datei mithilfe der oben angegebenen Links für Ihren Porttyp herunter.

3.  Doppelklicken Sie auf die Datei **datamigrationutility. exe** im Ordner `<your_folder>\Tools\ConfigurationMigration`, um das Konfigurations Migrationstool auszuführen, wählen Sie im Hauptbildschirm **Daten exportieren** aus, und klicken Sie dann auf **weiter**.
    
    > [!div class=mx-imgBorder]
    > ![Exportieren von Konfigurationsdaten](../media/export-config-data.png "Exportieren von Konfigurationsdaten")

4.  Geben Sie auf dem **Anmelde** Bildschirm Authentifizierungs Details an, um eine Verbindung mit ihrer Common Data Service Umgebung herzustellen, über die Sie Daten exportieren möchten. Wenn Sie in der Common Data Service Umgebung mehrere Organisationen haben, aus denen die Daten exportiert werden sollen, aktivieren Sie das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen** , und wählen Sie dann **Anmeldung**aus.

    > [!div class=mx-imgBorder]
    > ![Geben Sie Authentifizierungs Details an, um eine Verbindung mit ihrer Common Data Service Umgebung herzustellen, über die Sie Daten exportieren möchten.](../media/export-config-login.png "Geben Sie Authentifizierungs Details an, um eine Verbindung mit ihrer Common Data Service Umgebung herzustellen, über die Sie Daten exportieren möchten.")

5.  Wenn Sie mehrere Organisationen haben und im vorherigen Schritt das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen** ausgewählt haben, können Sie auf dem nächsten Bildschirm die Organisation auswählen, mit der Sie eine Verbindung herstellen möchten. Wählen Sie eine Common Data Service Umgebung für die Verbindung aus. 

    > [!NOTE]
    > Wenn Sie nicht über mehrere Organisationen verfügen, wird dieser Bildschirm nicht angezeigt.

6.  Navigieren Sie in der **Schema Datei**zu der Portal spezifischen Konfigurations Schema Datei, die für den Datenexport verwendet werden soll.

7.  Geben **Sie unter in Datendatei speichern**den Namen und den Speicherort der zu exportierenden Datendatei an.

    > [!div class=mx-imgBorder]
    > ![Angeben von Schema-und Zieldateien](../media/export-config-file-name.png "Angeben von Schema-und Zieldateien")

8.  Wählen Sie **Daten exportieren**aus. Der Bildschirm zeigt den Status des Export Fortschritts und den Speicherort der exportierten Datei unten auf dem Bildschirm an, nachdem der Export abgeschlossen ist.

    > [!div class=mx-imgBorder]
    > ![Fortschritt des Konfigurationsdaten Exports](../media/export-config-status.png "Fortschritt des Konfigurationsdaten Exports")

    > [!IMPORTANT]
    > Das Konfigurations Migrationstool unterstützt nicht das Filtern von Datensätzen in einer Entität. Standardmäßig werden alle Datensätze in der ausgewählten Entität exportiert. Wenn Sie mehr als einen Website Daten Satz erstellt haben, werden daher alle Website Datensätze exportiert.

9.  Wählen Sie **Beenden** , um das Tool zu schließen.

## <a name="import-portal-configuration-data"></a>Importieren von Portal-Konfigurationsdaten

1.  Führen Sie das Konfigurations Migrationstool aus, und wählen Sie im Hauptbildschirm **Daten importieren** aus, und klicken Sie dann auf **weiter**.

    > [!div class=mx-imgBorder]
    > ![Importieren von Konfigurationsdaten](../media/import-config-data.png "Importieren von Konfigurationsdaten")

2.  Geben Sie auf dem **Anmelde** Bildschirm Authentifizierungs Details an, um eine Verbindung mit ihrer Common Data Service Umgebung herzustellen, über die Sie Daten exportieren möchten. Wenn Sie in der Common Data Service Umgebung mehrere Organisationen haben, aus denen die Daten exportiert werden sollen, aktivieren Sie das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen** , und wählen Sie dann **Anmeldung**aus.

3.  Wenn Sie mehrere Organisationen haben und im vorherigen Schritt das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen** ausgewählt haben, können Sie auf dem nächsten Bildschirm die Organisation auswählen, mit der Sie eine Verbindung herstellen möchten. Wählen Sie eine Common Data Service Umgebung für die Verbindung aus. 

    > [!NOTE]
    > - Wenn Sie nicht über mehrere Organisationen verfügen, wird dieser Bildschirm nicht angezeigt.
    > - Stellen Sie sicher, dass die Portallösung bereits für die Organisation installiert ist, in der Sie die Konfigurationen importieren möchten.

4.  Im nächsten Bildschirm werden Sie aufgefordert, die Datendatei (ZIP-Datei) anzugeben, die importiert werden soll. Navigieren Sie zu der Datendatei, wählen Sie Sie aus, und klicken Sie dann auf **Daten importieren**. 

    > [!div class=mx-imgBorder]
    > ![Fortschritt des Konfigurationsdaten Imports](../media/import-config-status.png "Fortschritt des Konfigurationsdaten Imports")

5.  Der nächste Bildschirm zeigt den Import Status Ihrer Datensätze an. Der Datenimport erfolgt in mehreren Durchläufen, um zuerst die Foundation-Daten zu importieren, während die abhängigen Daten in die Warteschlange eingereiht werden. Anschließend werden die abhängigen Daten in den nachfolgenden Durchläufen importiert, um beliebige Daten Abhängigkeiten oder Verknüpfungen zu verarbeiten. Dies stellt einen sauberen und konsistenten Datenimport sicher. 

6.  Wählen Sie **Beenden** , um das Tool zu schließen. 

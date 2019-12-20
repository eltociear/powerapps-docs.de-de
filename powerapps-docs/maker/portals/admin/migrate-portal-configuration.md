---
title: Migrieren der Portalkonfiguration | MicrosoftDocs
description: Informationen zum Migrieren der Portalkonfiguration.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 80f9cc89b0da2eec5d134f282507e68658e42a96
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "2816381"
---
# <a name="migrate-portal-configuration"></a>Portalkonfiguration migrieren

Die Portalentwicklung umfasst mehrere Konfigurationen und Anpassungen, um eine gewünschte Erfahrung für Portalendbenutzer zu erreichen.

Nachdem Sie die Entwicklung oder Konfiguration Ihrer Portal-Instanz abgeschlossen haben, möchten Sie möglicherweise die aktuelle Portal-Konfiguration aus der Entwicklungs- zur Testumgebung oder zu Produktionsumgebungen migrieren. Das Migrieren Ihrer Daten beinhaltet den Export der vorhandenen Konfigurationsdaten von der Quell-Common Data Service-Umgebung und den anschließenden Import in die Ziel-Common Data Service-Umgebung.

Zum Exportieren der Konfigurationsdaten müssten Sie das Tool für die Konfigurationsmigration und eine portalspezifische Konfigurationsschemadatei verwenden. Weitere Informationen zu diesem Tool finden Sie unter [Konfigurationsdaten verwalten](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data).

> [!NOTE]
> - Wir empfehlen Ihnen, die neueste Version des Tools für die Konfigurationsmigration zu verwenden. Das Tool für die Konfigurationsmigration kann von NuGet heruntergeladen werden. Weitere Informationen zum Herunterladen des Tools: [Tools von NuGet herunterladen](https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget).
> - Die mindestens erforderliche Lösungsversion von Portalen, die von Schemadateien für die Konfigurationsmigration unterstützt wird, ist 8.4.0.275. Es ist jedoch empfehlenswert, die aktuelle Lösungsversion zu verwenden.

Schemadateien sind für die folgenden Portaltypen verfügbar:

- **In einer Umgebung mit Common Data Service erstellte Portale**
    - [Benutzerdefiniertes Portal (leeres Portal)](https://go.microsoft.com/fwlink/p/?linkid=2110477)

- **Portale, die in einer Umgebung mit modellgesteuerten Apps in Dynamics 365 erstellt wurden**
    - [Benutzerdefiniertes Portal (leeres Portal)](https://go.microsoft.com/fwlink/p/?linkid=2019804)
    - [Community-Portal](https://go.microsoft.com/fwlink/p/?linkid=2019704)
    - [Kunden-Self-Service-Portal](https://go.microsoft.com/fwlink/p/?linkid=2019705)
    - [Partnerportal](https://go.microsoft.com/fwlink/p/?linkid=2019803)
    - [Mitarbeiter-Self-Service-Portal](https://go.microsoft.com/fwlink/p/?linkid=2019802)

Die standardmäßigen Schemadateien enthalten Informationen zu Portalentitäten, Beziehungen und Eindeutigkeitsdefinitionen für jede Entität. Weitere Informationen: [Portalkonfigurationsdaten exportieren](#export-portal-configuration-data)

Nach dem Export der Konfigurationsdaten müssen Sie sie in die Zielumgebung importieren. Weitere Informationen: [Portalkonfigurationsdaten importieren](#import-portal-configuration-data)

> [!NOTE]
> Die Schemadateien werden bereitgestellt, um den erforderlichen Aufwand für die völlig neue Erstellung eines Schemas zu verringern. Schemas können für Ihre Implementierung mithilfe der Standardmethoden angepasst werden, die von dem Tool bereitgestellt werden. Schemadateien können im Tool für die Konfigurationsmigration geladen und geändert werden, um Entitäten, Attribute usw. hinzuzufügen, zu entfernen und zu ändern.

## <a name="export-portal-configuration-data"></a>Exportieren von Portalkonfigurationsdaten

Sie können Portalkonfigurationsdaten aus einem Quellsystem exportieren, indem Sie portalspezifische Konfigurationsdatenschemadateien verwenden.

1.  Laden Sie das Tool für die Konfigurationsmigration herunter und extrahieren Sie es in den gewünschten Ordner.

2.  Laden Sie eine Portalkonfigurations-Schemadatei für Ihren Portaltyp mithilfe der oben angegebenen Links herunter.

3.  Doppelklicken Sie auf die Datei **DataMigrationUtility.exe** im Ordner `<your_folder>\Tools\ConfigurationMigration`, um das Tool für die Konfigurationsmigration auszuführen, wählen Sie auf dem Hauptbildschirm **Daten exportieren** aus und wählen Sie dann **Weiter** aus.
    
    > [!div class=mx-imgBorder]
    > ![Konfigurationsdaten exportieren](../media/export-config-data.png "Konfigurationsdaten exportieren")

4.  Geben Sie auf dem Bildschirm **Anmeldung** Authentifizierungsdetails an, um die Verbindung zu Ihrer Common Data Service-Umgebung herzustellen, von der Sie Daten exportieren möchten. Wenn Sie mehrere Organisationen in der Common Data Service-Umgebung haben, von der Sie die Daten exportieren möchten, aktivieren Sie das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen**, und wählen Sie dann **Anmelden** aus.

    > [!div class=mx-imgBorder]
    > ![Stellen Sie Authentifizierungsdetails bereit, um sich mit Ihrer Common Data Service-Umgebung zu verbinden, von der Sie Daten exportieren möchten](../media/export-config-login.png "Stellen Sie Authentifizierungsdetails bereit, um sich mit Ihrer Common Data Service-Umgebung zu verbinden, von der Sie Daten exportieren möchten")

5.  Wenn Sie mehrere Organisationen haben und im vorherigen Schritt das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen** ausgewählt haben, können Sie auf dem nächsten Bildschirm die Organisation auswählen, mit der Sie eine Verbindung herstellen möchten. Wählen Sie eine Common Data Service-Umgebung für die Verbindung aus. 

    > [!NOTE]
    > Wenn Sie nicht mehrere Organisationen haben, wird der Bildschirm nicht angezeigt.

6.  Suchen Sie in der **Schemadatei** und wählen Sie die portalspezifische Konfigurationsschemadatei aus, die für den Datenexport verwendet werden soll.

7.  Geben Sie unter **In Datendatei speichern** den Namen und den Ort der zu exportierenden Datendatei an.

    > [!div class=mx-imgBorder]
    > ![Schema- und Zieldateien angeben](../media/export-config-file-name.png "Schema- und Zieldateien angeben")

8.  Wählen Sie **Daten exportieren** aus. Der Bildschirm zeigt den Exportfortschritt und den Speicherort der exportierten Datei unten auf dem Bildschirmrand an, sobald der Import abgeschlossen ist.

    > [!div class=mx-imgBorder]
    > ![Exportfortschritt der Konfigurationsdaten](../media/export-config-status.png "Exportfortschritt der Konfigurationsdaten")

    > [!IMPORTANT]
    > Das Configuration Migration Tool unterstützt nicht das Filtern von Datensätzen in einer Entität. Standardmäßig werden alle Datensätze in der ausgewählten Entität exportiert. Wenn Sie also mehr als einen Website-Datensatz erstellt haben, werden alle Websitedatensätzen exportiert.

9.  Wählen Sie **Schließen**, um das Tool zu schließen.

## <a name="import-portal-configuration-data"></a>Importieren von Portalkonfigurationsdaten

1.  Führen Sie das Tool für die Konfigurationsmigration aus und wählen Sie auf dem Hauptbildschirm **Daten importieren** aus, und wählen Sie dann **Weiter** aus.

    > [!div class=mx-imgBorder]
    > ![Konfigurationsdaten importieren](../media/import-config-data.png "Konfigurationsdaten importieren")

2.  Geben Sie auf dem Bildschirm **Anmeldung** Authentifizierungsdetails an, um die Verbindung zu Ihrer Common Data Service-Umgebung herzustellen, von der Sie Daten exportieren möchten. Wenn Sie mehrere Organisationen in der Common Data Service-Umgebung haben, von der Sie die Daten exportieren möchten, aktivieren Sie das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen**, und wählen Sie dann **Anmelden** aus.

3.  Wenn Sie mehrere Organisationen haben und im vorherigen Schritt das Kontrollkästchen **Liste der verfügbaren Organisationen anzeigen** ausgewählt haben, können Sie auf dem nächsten Bildschirm die Organisation auswählen, mit der Sie eine Verbindung herstellen möchten. Wählen Sie eine Common Data Service-Umgebung für die Verbindung aus. 

    > [!NOTE]
    > - Wenn Sie nicht mehrere Organisationen haben, wird der Bildschirm nicht angezeigt.
    > - Stellen Sie sicher, dass die Portallösung bereits für die Organisation installiert ist, bei der Sie die Konfigurationen importieren möchten.

4.  Der folgende Bildschirm fordert Sie auf, die zu importierende Datendatei (.zip) anzugeben. Navigieren Sie zu der Datendatei, wählen Sie sie aus, und wählen Sie dann **Daten importieren** aus. 

    > [!div class=mx-imgBorder]
    > ![Importfortschritt der Konfigurationsdaten](../media/import-config-status.png "Importfortschritt der Konfigurationsdaten")

5.  Der nächste Bildschirm zeigt den Importstatus Ihrer Datensätze an. Der Datenimport geschieht in mehreren Durchläufen; zunächst werden die Grundlagendaten importiert, während die abhängigen Daten zusammengestellt werden. Dann werden die abhängigen Daten in den folgenden Durchläufen importiert, um alle Datenabhängigkeiten und Verknüpfungen zu berücksichtigen. Dadurch wird ein sauberer und konsistenter Datenimport sichergestellt. 

6.  Wählen Sie **Schließen**, um das Tool zu schließen. 

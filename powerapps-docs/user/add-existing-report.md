---
title: Hinzufügen eines Berichts von außerhalb von Power Apps| Microsoft-Dokumentation
description: Hinzufügen eines Berichts von außerhalb von Power Apps
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e730d498a4d82518d0f908645e26a541c1e8c6af
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302953"
---
# <a name="add-a-report-from-outside-power-apps"></a>Hinzufügen eines Berichts von außerhalb von Power Apps

Wenn Sie einen benutzerdefinierten Bericht außerhalb des Systems erstellt haben, können Sie sie ihn leicht zu Power Apps hinzufügen.

Informationen zum Erstellen eines benutzerdefinierten Berichts finden Sie unter [Übersicht über Berichte](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/get-started-writing-reports).

1. Wählen Sie im linken Navigationsbereich den Bereich „Berichte“ aus. 
2. Wählen Sie auf der Befehlsleiste **Neu** aus.
  
   **Hinzufügen einer in einer anderen Anwendung erstellten Datei**  
  
   1. Wählen Sie im Bereich **Quelle** im Feld **Berichtstyp** die Option **Vorhandene Datei** aus.  
   
     > [!div class="mx-imgBorder"]
     > ![Hinzufügen eines vorhandenen Berichts](media/add_existing_report.png "Hinzufügen eines vorhandenen Berichts")
  
   2. Geben Sie im Feld **Dateispeicherort** den Pfad und Dateinamen der hinzuzufügenden Datei ein, oder wählen Sie **Durchsuchen**, um die Datei zu suchen. 
   
      Sie können auch viele andere Dateitypen hochladen (beispielsweise eine Excel-Datei). Wenn die Datei aber wie ein SQL Server Reporting Services-Bericht oder wie ein durch den Berichts-Assistenten erstellter Bericht funktionieren soll, muss es sich um eine RDL-Datei handeln. Weitere Informationen finden Sie unter [Berichtverfassungsumgebung mit SQL Server Data Tools](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools).
  
      ODER:  
  
   **Hinzufügen eines Links zu einer Webseite**  
  
   1.  Wählen Sie im Bereich **Quelle** im Feld **Berichtstyp** die Option **Link zu Webseite** aus.  
  
   2.  Geben Sie im Feld **Webseiten-URL** die URL der Webseite ein.  
  
3. Geben Sie die Eigenschaften für den Bericht an.
  
   1.  Im Abschnitt **Details** geben Sie einen aussagekräftigen Namen und eine Beschreibung für den Bericht an.  
  
   2.  Das Textfeld **Übergeordneter Bericht** zeigt den übergeordneten Bericht des aktuellen Berichts an, falls vorhanden.  
  
   3. **Kategorien**. Wählen Sie die Schaltfläche ![Auslassungspunkte](media/ellipsis-button.png "Schaltfläche mit Auslassungspunkten") aus, um die Werte für dieses Feld auszuwählen oder zu ändern, und geben Sie anschließend die Kategorien ein, die in diesen Bericht einbezogen werden sollen.****  
  
   4. **Verknüpfte Datensatztypen**. Wählen Sie die Schaltfläche ![Auslassungspunkte](media/ellipsis-button.png "Schaltfläche mit Auslassungspunkten") aus, um die Werte für dieses Feld auszuwählen oder zu ändern, und wählen Sie anschließend die gewünschten Datensatztypen aus, damit der Bericht in der Berichtsliste einer Seite für bestimmte Datensatztypen angezeigt wird.****  
  
   5. **Anzeigen in**. Wählen Sie die Schaltfläche ![Auslassungspunkte](media/ellipsis-button.png "Schaltfläche mit Auslassungspunkten") aus, um die Werte für dieses Feld auszuwählen oder zu ändern, und wählen Sie anschließend eine oder mehrere der Optionen aus, um anzugeben, wo der Bericht angezeigt werden soll.****  
  
        Wenn Sie nichts auswählen, wird der Bericht den Endbenutzern nicht angezeigt.  
  
4. Klicken Sie auf **Speichern** oder auf **Speichern und schließen**.  




### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Bearbeiten des Standardfilters eines Berichts](edit-report-filter.md)

[Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten](troubleshoot-reports.md)

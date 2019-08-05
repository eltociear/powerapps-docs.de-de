---
title: Hinzufügen eines Berichts von außerhalb von powerapps | Microsoft-Dokumentation
description: Hinzufügen eines Berichts von außerhalb von powerapps
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
ms.openlocfilehash: 24faa77b454cf3324e4b7277c94c6cd364aec9a9
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420166"
---
# <a name="add-a-report-from-outside-powerapps"></a>Hinzufügen eines Berichts von außerhalb von powerapps

Wenn Sie einen benutzerdefinierten Bericht außerhalb des Systems erstellt haben, können Sie ihn problemlos zu powerapps hinzufügen.

Informationen zum Erstellen eines benutzerdefinierten Berichts finden Sie im [Handbuch zur Berichterstattung und Analyse](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/analytics/get-started-writing-reports).

1. Wählen Sie im linken Navigationsbereich den Bereich Berichte aus. 
2. Klicken Sie in der Befehlsleiste auf **neu**.
  
   **Hinzufügen einer Datei, die in einer anderen Anwendung erstellt wurde**  
  
   1. Wählen Sie im Abschnitt **Quelle** im Feld **Berichtstyp** die Option **vorhandene Datei**aus.  
   
     > [!div class="mx-imgBorder"]
     > ![Vorhandenen Bericht hinzufügen](media/add_existing_report.png "Vorhandenen Bericht hinzufügen")
  
   2. Geben Sie im Feld **Datei Speicherort** den Pfad und den Dateinamen der hinzu zufügenden Datei ein, oder wählen Sie **Durchsuchen** aus, um die Datei zu suchen. 
   
      Sie können viele andere Dateitypen, z. b. eine Excel-Datei, hochladen, damit diese z. b. wie ein SQL Server Reporting Services Bericht oder Berichts-Assistent erstellt werden kann. RDL-Datei. Weitere Informationen finden Sie unter [Report Writing Environment Using SQL Server Data Tools](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools).
  
      ODER  
  
   **Hinzufügen eines Links zu einer Webseite**  
  
   1.  Wählen Sie im Abschnitt **Quelle** im Feld **Berichtstyp** die Option **mit Webseite verknüpfen**aus.  
  
   2.  Geben Sie im Feld **Webseiten-URL** die URL der Webseite ein.  
  
3. Geben Sie die Eigenschaften für den Bericht an.
  
   1.  Geben Sie im **Detail** Abschnitt einen aussagekräftigen Namen und eine Beschreibung für den Bericht an.  
  
   2.  Das Textfeld über **geordneter Bericht** zeigt den übergeordneten Bericht des aktuellen Berichts an, sofern vorhanden.  
  
   3. **Kategorien**. Wählen Sie die Schaltfläche mit den Auslassungs Punkten der Schaltfläche mit **den Auslassungs Punkten für dieses Feld auswählen oder ändern aus** ![](media/ellipsis-button.png "") , und geben Sie dann die Kategorien an, die in diesen Bericht aufgenommen  
  
   4. **Zugehörige Daten Satz Typen**. Damit der Bericht in der Liste Berichte auf einer Seite für bestimmte Daten Satz Typen angezeigt wird, klicken Sie auf die Schaltfläche mit den Auslassungs Punkten auf der Schaltfläche mit **den Auslassungs Punkten für dieses Feld auswählen oder ändern** ![](media/ellipsis-button.png "") , und wählen Sie dann Daten Satz Typen aus.  
  
   5. **Anzeigen in**. Um anzugeben, wo Berichte sichtbar sein sollen, wählen Sie die Schaltfläche mit den Auslassungs Punkten der Schaltfläche mit **den Auslassungs Punkten für dieses Feld auswählen oder ändern aus** ![Ellipsis button](media/ellipsis-button.png "Ellipsis button") , und wählen Sie dann eine oder mehrere der Optionen aus.  
  
        Wenn keine Werte ausgewählt sind, ist der Bericht für Endbenutzer nicht sichtbar.  
  
4. Wählen Sie **Speichern** oder **Speichern und schließen**aus.  




### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Berichts Filter bearbeiten](edit-report-filter.md)

[Problembehandlung bei Daten, die nicht in einem Bericht angezeigt werden](troubleshoot-reports.md)

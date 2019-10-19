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
ms.openlocfilehash: 9f775c5607720adcf233524522accb926d955289
ms.sourcegitcommit: c4328e83f5caa58eab83757180b56ced480af220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71982653"
---
# <a name="add-a-report-from-outside-powerapps"></a>Hinzufügen eines Berichts von außerhalb von powerapps

Wenn Sie einen benutzerdefinierten Bericht außerhalb des Systems erstellt haben, können Sie ihn problemlos zu powerapps hinzufügen.

Informationen zum Erstellen eines benutzerdefinierten Berichts finden Sie im [Handbuch zur Berichterstattung und Analyse](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/get-started-writing-reports).

1. Wählen Sie im linken Navigationsbereich den Bereich Berichte aus. 
2. Klicken Sie in der Befehlsleiste auf **neu**.
  
   **Hinzufügen einer Datei, die in einer anderen Anwendung erstellt wurde**  
  
   1. Wählen Sie im Abschnitt **Quelle** im Feld **Berichtstyp** die Option **vorhandene Datei**aus.  
   
     > [!div class="mx-imgBorder"]
     > ![Hinzufügen eines]vorhandenen Berichts(media/add_existing_report.png "Hinzufügen eines vorhandenen Berichts")
  
   2. Geben Sie im Feld **Datei Speicherort** den Pfad und den Dateinamen der hinzu zufügenden Datei ein, oder wählen Sie **Durchsuchen** aus, um die Datei zu suchen. 
   
      Sie können viele andere Dateitypen, z. b. eine Excel-Datei, hochladen, damit diese z. b. wie ein SQL Server Reporting Services Bericht oder Berichts-Assistent erstellt werden kann. RDL-Datei. Weitere Informationen finden Sie unter [Report Writing Environment Using SQL Server Data Tools](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools).
  
      Oder  
  
   **Hinzufügen eines Links zu einer Webseite**  
  
   1.  Wählen Sie im Abschnitt **Quelle** im Feld **Berichtstyp** die Option **mit Webseite verknüpfen**aus.  
  
   2.  Geben Sie im Feld **Webseiten-URL** die URL der Webseite ein.  
  
3. Geben Sie die Eigenschaften für den Bericht an.
  
   1.  Geben Sie im **Detail** Abschnitt einen aussagekräftigen Namen und eine Beschreibung für den Bericht an.  
  
   2.  Das Textfeld über **geordneter Bericht** zeigt den übergeordneten Bericht des aktuellen Berichts an, sofern vorhanden.  
  
   3. **Kategorien**. Wählen Sie(media/ellipsis-button.png "die Schaltfläche") mit den Auslassungs Punkten der ![Schaltfläche]mit **den Auslassungs Punkten für dieses Feld auswählen oder ändern aus** , und geben Sie dann die Kategorien an, die in diesen Bericht aufgenommen  
  
   4. **Zugehörige Daten Satz Typen**. Damit der Bericht in der Liste Berichte auf einer Seite für bestimmte Daten Satz Typen angezeigt wird, klicken Sie auf(media/ellipsis-button.png "die Schaltfläche") mit **den Auslassungs Punkten auf der Schaltfläche mit den Auslassungs Punkten für dieses Feld auswählen oder ändern** ![], und wählen Sie dann Daten Satz Typen aus.  
  
   5. **Anzeigen in**. Um anzugeben, wo Berichte sichtbar sein sollen, wählen Sie(media/ellipsis-button.png "die Schaltfläche") mit den Auslassungs Punkten der ![Schaltfläche]mit **den Auslassungs Punkten für dieses Feld auswählen oder ändern aus** , und wählen Sie dann eine oder mehrere der Optionen aus.  
  
        Wenn keine Werte ausgewählt sind, ist der Bericht für Endbenutzer nicht sichtbar.  
  
4. Wählen Sie **Speichern** oder **Speichern und schließen**aus.  




### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Berichts Filter bearbeiten](edit-report-filter.md)

[Problembehandlung bei Daten, die nicht in einem Bericht angezeigt werden](troubleshoot-reports.md)

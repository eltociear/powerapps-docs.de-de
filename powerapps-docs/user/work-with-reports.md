---
title: Arbeiten mit Berichten | Microsoft-Dokumentation
description: Arbeiten mit Berichten in Power Apps
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
ms.openlocfilehash: c16a589ddcd1e7beb0be1ce28bc9f6df6a8c8b83
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79239957"
---
# <a name="work-with-reports"></a>Arbeiten mit Berichten

Mithilfe von Berichten können Sie Ihre Fortschritte im Hinblick auf Ihre Geschäftsziele überwachen. Darüber hinaus können Sie Trends nachverfolgen, was Ihnen ggf. einen Wettbewerbsvorteil verschafft.  

Weitere Informationen zur Strukturierung und Erstellung von Berichten finden Sie hier: [Hinzufügen von Berichtsfeatures zur modellgesteuerten App](https://docs.microsoft.com/powerapps/maker/model-driven-apps/add-reporting-to-app).
  
## <a name="run-a-report"></a>Ausführen eines Berichts  
  
1. Wählen Sie im linken Navigationsbereich den Bereich „Berichte“ aus. 
2. Wählen Sie den gewünschten Bericht und anschließend **Bericht ausführen** aus.  
  
   > [!NOTE]
   >  Im Dialogfeld **Berichts-Viewer** können Sie die Suchkriterien unverändert lassen oder nach Bedarf ändern.  
   
   > [!div class="mx-imgBorder"]
   > ![Ausführen eines Berichts](media/report-run.png "Ausführen eines Berichts")
 
  
## <a name="share-a-report-with-other-users-or-teams"></a>Freigeben eines Berichts für andere Benutzer oder Teams    

1. Wählen Sie im linken Navigationsbereich den Bereich „Berichte“ aus.  
2. Wählen Sie in der Liste mit den Berichten den Bericht aus, den Sie freigeben möchten.  
3. Wählen Sie auf der Befehlsleiste **Freigeben** aus.

   > [!div class="mx-imgBorder"]
   > ![Freigeben eines Berichts](media/report-share.png "Freigeben eines Berichts")
  
4. Wählen Sie im Dialogfeld **Bericht freigeben** die Option **Benutzer/Team hinzufügen** aus.    
5. Suchen Sie im Dialogfeld **Datensätze nachschlagen** nach dem Benutzer- oder Teamdatensatz, für den Sie den Bericht freigeben möchten, und aktivieren Sie das Kontrollkästchen neben dem Datensatz.

   > [!div class="mx-imgBorder"]
   > ![Auswählen eines Benutzers für die Berichtsfreigabe](media/report-share1.png "Auswählen eines Benutzers für die Berichtsfreigabe")

6. Wählen Sie **Auswählen** aus, um den Benutzer- oder Teamdatensatz dem Feld **Ausgewählte Datensätze** hinzuzufügen, und wählen Sie anschließend **Hinzufügen** aus.

   > [!div class="mx-imgBorder"]
   > ![Hinzufügen eines Benutzers für die Berichtsfreigabe](media/report-share2.png "Hinzufügen eines Benutzers für die Berichtsfreigabe")
  
7. Wählen Sie im Dialogfeld **Bericht freigeben** den gewünschten Zugriffstyp aus. Folgende Berechtigungen stehen zur Verfügung: „Lesen“, „Schreiben“, „Löschen“, „Anfügen“, „Zuweisen“ und „Freigeben“. Dadurch wird der Benutzer- oder Teamdatensatz dem Feld **Ausgewählte Datensätze** hinzugefügt.

   > [!div class="mx-imgBorder"]
   > ![Auswählen des Freigabezugriffs](media/report-share3.png "Auswählen des Freigabezugriffs")
  

## <a name="share-a-report-with-your-organization-for-admins"></a>Freigeben eines Berichts für Ihre Organisation (für Administratoren)
 Berichte, die für alle Benutzer hilfreich sind, können für die Organisation verfügbar gemacht werden.  

1. Wählen Sie im linken Navigationsbereich den Bereich „Berichte“ aus.  
2. Wählen Sie in der Liste mit den Berichten den Bericht aus, den Sie freigeben möchten.  
3. Wählen Sie auf der Befehlsleiste **Bearbeiten** aus.  
4. Wählen Sie im Menü **Aktionen** die Option **Bericht der Organisation zur Verfügung stellen**.  
  
   > [!div class="mx-imgBorder"]
   > ![Freigeben eines Berichts für die Organisation](media/report-share4.png "Freigeben eines Berichts für die Organisation")

## <a name="download-a-report"></a>Herunterladen eines Berichts

1. Wählen Sie im linken Navigationsbereich den Bereich „Berichte“ aus. 
2. Wählen Sie in der Liste mit den Berichten den Bericht aus, den Sie freigeben möchten.  
3. Wählen Sie auf der Befehlsleiste **Bearbeiten** aus.  
4. Wählen Sie im Menü **Aktionen** die Option **Bericht herunterladen** aus.  
Die RDL-Datei enthält die FetchXML-Abfrage, auf der der Bericht basiert.
5. Öffnen Sie den Bericht nach Abschluss des Downloadvorgangs.





### <a name="see-also"></a>Siehe auch

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Hinzufügen eines vorhandenen Berichts](add-existing-report.md)

[Bearbeiten des Standardfilters eines Berichts](edit-report-filter.md)

[Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten](troubleshoot-reports.md)



---
title: Bearbeiten des Standardfilters eines Berichts | Microsoft-Dokumentation
description: Bearbeiten des Standardfilters eines Berichts
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
ms.openlocfilehash: 53e4f2fc61bb72b4c3fc6fed188b513641c2034d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "3302493"
---
# <a name="edit-the-default-filter-of-a-report"></a>Bearbeiten des Standardfilters eines Berichts

Wenn es sich bei einem Bericht um einen SQL Server Reporting Services-Bericht handelt, der für die Vorfilterung aktiviert ist und über einen Standardfilter verfügt, können Sie den Standardfilter ändern, um die Daten anzuzeigen, die Sie im Bericht anzeigen möchten. Dieser Filter wird jedes Mal verwendet, wenn ein Benutzer den Bericht ausführt.

1. Wählen Sie im linken Navigationsbereich den Bereich „Berichte“ aus.
2. Wählen Sie einen Bericht aus, und wählen Sie auf der Befehlsleiste **Standardfilter bearbeiten** aus.

     > [!div class="mx-imgBorder"]
     > ![Standardberichtsfilter bearbeiten](media/edit_filter.png "Standardberichtsfilter bearbeiten")
  
3. Ändern Sie die Filterkriterien.  
  
   Die Kriterien sind nach den im Filter zu verwendenden Datensatztypen wie **Firmen** oder **Kontakte** gruppiert.  
  
   ### <a name="to-edit-an-existing-row"></a>So bearbeiten Sie eine vorhandene Zeile
   1. Wählen Sie den relationalen Abfrageoperator aus, und wählen Sie einen Operator aus. Alternativ können Sie den unterstrichenen Wert auswählen und einen neuen Wert eingeben.  
  
   2. Wählen Sie den relationalen Abfrageoperator aus, und wählen Sie einen Operator aus.  
  
   So fügen Sie eine Kriterienzeile hinzu  

   1.  Wählen Sie **Auswählen**, und geben Sie das Feld an, nach dem gefiltert werden soll.  

   2.  Wählen Sie den relationalen Abfrageoperator aus, und wählen Sie einen Operator aus.  

   3.  Klicken Sie auf **Wert eingeben**, und geben Sie einen Wert ein, nach dem gefiltert werden soll. Für einige Werte können Sie auf die Schaltfläche **Auswählen oder Ändern der Werte für das Feld, klicken Sie auf die Schaltfläche mit den ![Auslassungspunkten](media/ellipsis-button.png "Schaltfläche mit Auslassungspunkten")**, um das Dialogfeld **Werte auswählen** zu öffnen und den gewünschten Wert auszuwählen.  

   ### <a name="to-group-criteria"></a>Gruppieren von Kriterien
   Sie müssen mindestens zwei Zeilen für denselben Datensatztyp auswählen. Allerdings können Zeilen mit Feldwerten aus unterschiedlichen Datensatztypen wie z. B. **Konto** und **Kontakt** nicht gruppiert werden.  

   1.  Wählen Sie für jede Zeile, die Sie gruppieren möchten, im detaillierten Modus die Schaltfläche **Menüoptionen** für diese Zeile und anschließend **Zeile auswählen** aus.  

   2.  Wählen Sie auf der Filtersymbolleiste die Option **Gruppieren UND** oder **Gruppieren ODER** aus.  

   3.  Wenn Sie eine Zeile aus einer Gruppe entfernen möchten, wählen Sie die Schaltfläche **Menüoptionen** für diese Zeile und anschließend **Löschen** aus.  

   4.  Wenn Sie eine Gruppe auswählen möchten, wählen Sie die Schaltfläche **Menüoptionen** für diese Gruppe und anschließend **Gruppe auswählen** aus.  

   5.  Wenn Sie eine Kriterienklausel zu einer Gruppe hinzufügen möchten, wählen Sie die Schaltfläche **Menüoptionen** für diese Gruppe und anschließend **Klausel hinzufügen** aus. Wählen Sie danach das Feld, den relationalen Abfrageoperator und den Wert aus.  

   6.  Wenn Sie die Auswahl einer zuvor ausgewählten Gruppe aufheben möchten, wählen Sie die Schaltfläche **Menüoptionen** für diese Gruppe und anschließend **Gruppenauswahl aufheben** aus.  

   7.  Wenn Sie eine Gruppierung aufheben möchten, wählen Sie die Schaltfläche **Menüoptionen** für diese Gruppe und anschließend **Gruppierung aufheben** aus.  

   8.  Wenn Sie eine **Gruppe UND**-Gruppe in eine **Gruppe ODER**-Gruppe oder eine **Gruppe ODER**- in eine **Gruppe UND**-Gruppe ändern möchten, wählen Sie die Schaltfläche **Menüoptionen** für diese Gruppe aus, und wählen Sie dann **In ODER ändern** oder **In UND ändern** aus.  

   > [!TIP]
   > - Wenn Sie alle Kriterien löschen und neu beginnen möchten, klicken Sie auf der Filtersymbolleiste auf **Löschen**, und klicken Sie dann auf **Bestätigen**.  
   > - Wenn Sie eine Zeile löschen möchten, wählen Sie die Schaltfläche **Menüoptionen** für diese Zeile und anschließend **Löschen** aus.  
  
4. Wählen Sie **Standardfilter speichern** aus, wenn der Vorgang abgeschlossen ist.



### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Hinzufügen eines vorhandenen Berichts](add-existing-report.md)

[Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten](troubleshoot-reports.md)


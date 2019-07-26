---
title: Bearbeiten des Standard Filters eines Berichts | Microsoft-Dokumentation
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
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420212"
---
# <a name="edit-the-default-filter-of-a-report"></a>Bearbeiten des Standardfilters eines Berichts

Wenn es sich bei einem Bericht um einen SQL Server Reporting Services Bericht handelt, der für die Vorfilterung aktiviert ist und über einen Standardfilter verfügt, können Sie den Standardfilter ändern, um die Daten anzuzeigen, die Sie im Bericht erwarten. Dieser Filter wird jedes Mal verwendet, wenn ein Benutzer den Bericht ausführt.

1. Wählen Sie im linken Navigationsbereich den Bereich Berichte aus.
2. Wählen Sie einen Bericht aus, und wählen Sie auf der Leiste der Zeilen Leiste die Option **Standard Filter bearbeiten**aus.

     > [!div class="mx-imgBorder"]
     > ![Standard Berichts Filter bearbeiten](media/edit_filter.png "Standard Berichts Filter bearbeiten")
  
3. Ändern Sie die Filterkriterien.  
  
   Die Kriterien sind nach Daten Satz Typen gruppiert, die Sie im Filter verwenden können, z. b. **Konten** oder **Kontakte**.  
  
   ### <a name="to-edit-an-existing-row"></a>So bearbeiten Sie eine vorhandene Zeile
   1. Wählen Sie den relationalen Abfrage Operator aus, und wählen Sie einen Operator aus. Alternativ können Sie den unterstrichenen Wert auswählen und einen neuen  
  
   2. Wählen Sie den relationalen Abfrage Operator aus, und wählen Sie einen Operator aus.  
  
   So fügen Sie eine Kriterienzeile hinzu:  

   1.  Wählen Sie **auswählen**aus, und geben Sie das zu filternde Feld an.  

   2.  Wählen Sie den relationalen Abfrage Operator aus, und wählen Sie einen Operator aus.  

   3.  Wählen Sie **Wert eingeben**, und geben Sie einen Wert ein, nach dem gefiltert werden soll. Für einige Werte können Sie die Schalt ![](media/ellipsis-button.png "Fläche mit den") Auslassungs Punkten der Schaltfläche mit den Auslassungs Punkten **für dieses Feld auswählen oder ändern** auswählen, um das Dialogfeld **Werte auswählen** zu öffnen und den gewünschten Wert auszuwählen.  

   ### <a name="to-group-criteria"></a>So gruppieren Sie Kriterien
   Sie müssen mindestens zwei Zeilen für denselben Daten Satz Typen auswählen. Allerdings können Zeilen mit Feldwerten aus unterschiedlichen Daten Satz Typen, z. b. **Konto** -und **Kontakt** Daten Satz Typen, nicht gruppiert werden.  

   1.  Wählen Sie für jede Zeile, die Sie gruppieren möchten, im detaillierten Modus die Menü Schaltfläche **Optionen** für diese Zeile aus, und klicken Sie dann auf **Zeile auswählen**.  

   2.  Wählen Sie auf der Filter Symbolleiste die Option **Gruppieren und** oder **Gruppe oder**aus.  

   3.  Um eine Zeile aus einer Gruppe zu entfernen, wählen Sie die Menü Schaltfläche **Optionen** für diese Zeile aus, und wählen Sie dann **Löschen**aus.  

   4.  Um eine Gruppe auszuwählen, wählen Sie die Menü Schaltfläche **Optionen** für diese Gruppe aus, und wählen Sie dann **Gruppe auswählen**aus.  

   5.  Um einer Gruppe eine kriterienklausel hinzuzufügen, wählen Sie die Menü Schaltfläche **Optionen** für diese Gruppe und dann **Klausel hinzufügen**aus, und wählen Sie dann das Feld, den relationalen Abfrage Operator und den Wert aus.  

   6.  Um die Auswahl einer zuvor ausgewählten Gruppe zu deaktivieren, wählen Sie die **Menü** Schaltfläche Optionen für diese Gruppe aus, und wählen Sie dann **Gruppe deaktivieren**aus.  

   7.  Um die Gruppierung einer Gruppe zu deaktivieren, wählen Sie die Menü Schaltfläche **Optionen** für diese Gruppe aus, und wählen Sie dann Gruppierung **Deaktivieren**aus.  

   8.  Wenn Sie eine **Gruppe und** Gruppe in eine Gruppe **oder** Gruppe oder eine Gruppe **oder** Gruppe in eine **Gruppe und** Gruppe ändern möchten, wählen Sie die Menü Schaltfläche **Optionen** für diese Gruppe aus, und wählen Sie dann **in oder** ändern **aus.**  

   > [!TIP]
   > - Um alle Kriterien zu löschen und zu beginnen, wählen Sie auf der Filter Symbolleiste die Option **Löschen**aus, und wählen Sie dann **bestätigen**aus.  
   > - Um eine Zeile zu löschen, wählen Sie die Menü Schaltfläche **Optionen** für diese Zeile aus, und wählen Sie dann **Löschen**aus.  
  
4. Wenn Sie dies abgeschlossen haben, wählen Sie **Standard Filter speichern**aus.



### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Erstellen eines Berichts mithilfe des Berichts-Assistenten](create-report-with-wizard.md)

[Vorhandenen Bericht hinzufügen](add-existing-report.md)

[Problembehandlung bei Daten, die nicht in einem Bericht angezeigt werden](troubleshoot-reports.md)


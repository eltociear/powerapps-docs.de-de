---
title: Erstellen eines Berichts mithilfe des Berichts-Assistenten | Microsoft-Dokumentation
description: Erstellen eines Berichts mithilfe des Berichts-Assistenten in Power apps
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
ms.openlocfilehash: 8c7bde8d3aa5406a7ddcc5ecb2df4c2c7db7051e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733272"
---
# <a name="create-a-report-using-the-report-wizard"></a>Erstellen eines Berichts mithilfe des Berichts-Assistenten


Verwenden Sie den Berichts-Assistenten, um Berichte mit Diagrammen und Tabellen zu erstellen, mit denen Sie Ihre Daten problemlos analysieren können. 

Alle Berichte, die mit dem Berichts-Assistenten erstellt werden, sind Abruf basierte Berichte. Beachten Sie, dass alle mit dem Berichts-Assistenten generierten Berichte im Querformat gedruckt werden.

## <a name="create-a-new-report"></a>Neuen Bericht erstellen

1. Wählen Sie im linken Navigationsbereich den Bereich Berichte aus.  
2. Klicken Sie in der Befehlsleiste auf **neu**.

    > [!div class="mx-imgBorder"]
    > ![Erstellen eines neuen Berichts](media/newreport.png "Neuen Bericht erstellen")
  
3. Ein **Bericht:** der Bildschirm neuer Bericht wird angezeigt. Überlassen Sie für **Berichtstyp** die Standardauswahl, **melden** Sie den Bericht, und wählen Sie die Schaltfläche **Berichts-Assistent** aus. 

    > [!div class="mx-imgBorder"]
    > ![Berichts-Assistent](media/report_wizard.png "Berichts-Assistent")
  
4. Überprüfen Sie auf dem nächsten Bildschirm die Standardauswahl, und klicken Sie dann auf **weiter**.
 
    > [!div class="mx-imgBorder"]
    > ![Berichts-Assistent](media/report_wizard_1.png "Berichts-Assistent")
   
4. Geben Sie auf dem Bildschirm **Berichts Eigenschaften** einen Namen für den Bericht ein, und wählen Sie dann den Datensatz aus, der in den Bericht eingeschlossen werden soll. Klicken Sie anschließend auf **weiter**
 
    > [!div class="mx-imgBorder"]
    > ![Berichts Eigenschaften-Bildschirm](media/report_wizard_2.png "Berichts Eigenschaften-Bildschirm")
  
5.  Wählen Sie auf der Seite **Datensätze auswählen, die im Bericht** eingeschlossen werden sollen die Filter aus, um zu bestimmen, welche Datensätze in den Bericht eingeschlossen werden. Wenn Sie z. b. nur Ergebnisse für Datensätze anzeigen möchten, die in den letzten 60 Tagen geändert wurden, können Sie diesen Filter in diesem Bildschirm festlegen. Wenn Sie nicht möchten, dass die Daten gefiltert werden, wählen Sie **Löschen**aus.

    > [!div class="mx-imgBorder"]
    > ![Datensätze auswählen, die in den Bericht eingeschlossen werden sollen *](media/report_wizard_3.png "Datensätze auswählen, die in den Bericht aufgenommen werden sollen")
  
6. Wählen Sie auf dem Bildschirm Layout- **out-Felder** das Layout des Berichts aus. Wählen Sie **hier klicken, um eine Gruppierung hinzuzufügen,** und wählen Sie aus, wie die Daten gruppiert werden sollen.

    > [!div class="mx-imgBorder"]
    > ![Layout für Felder](media/report_wizard_4.png "Layout für Felder")

7. Wählen Sie den Daten **Banktyp** und die **Spalte** für die Daten aus, die im Bericht gruppiert werden sollen. Wenn Sie Ihre Auswahl getroffen haben, wählen Sie **OK**aus.

    > [!div class="mx-imgBorder"]
    > ![DD-Gruppierungs Bildschirm](media/report_wizard_5.png "Gruppierungs Bildschirm hinzufügen")
  
8. Wählen Sie **Klicken Sie hier, um eine Spalte** zu Datenspalten hinzuzufügen, die sich auf den im vorherigen Schritt ausgewählten Datensatz-Typ beziehen.  

    > [!div class="mx-imgBorder"]
    > ![Gruppierungs Bildschirm hinzufügen](media/report_wizard_6.png "Gruppierungs Bildschirm hinzufügen")

9. Wählen Sie auf dem Bildschirm **Spalte hinzufügen** die Daten aus, die für die Spalte angezeigt werden sollen, und klicken Sie dann auf **OK**. 

    > [!div class="mx-imgBorder"]
    > ![Spalten Bildschirm hinzufügen](media/report_wizard_7.png "Spalten Bildschirm hinzufügen")
  
10. Wiederholen Sie den vorherigen Schritt für alle zusätzlichen Spalten, die Sie hinzufügen möchten. Wenn Sie den Vorgang abgeschlossen haben, können Sie auf dem Bildschirm zum Anordnen **von Feldern** **auf weiter gehen.**
 
    > [!div class="mx-imgBorder"]
    > ![weiteren Spalten Bildschirm hinzufügen](media/report_wizard_8.png "Weiteren Spalten Bildschirm hinzufügen")
  
11. Wählen Sie auf dem Bildschirm **Format Bericht formatieren** Sie den Bericht aus, und klicken Sie dann auf **weiter**.
 
    > [!div class="mx-imgBorder"]
    > ![Formatieren von Berichten](media/report_wizard_9.png "Berichts Bildschirm formatieren")

12. Überprüfen Sie die Zusammenfassung des Berichts, und klicken Sie auf **weiter** und dann auf **Fertig**stellen. Dieser Bericht kann nun in der Liste der Berichte im System angezeigt werden.

    > [!div class="mx-imgBorder"]
    > ![Bericht anzeigen](media/report_wizard_10.png "Anzeigen des Berichts")

### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Vorhandenen Bericht hinzufügen](add-existing-report.md)

[Berichts Filter bearbeiten](edit-report-filter.md)

[Problembehandlung bei Daten, die nicht in einem Bericht angezeigt werden](troubleshoot-reports.md)



---
title: Erstellen eines Berichts mithilfe des Berichts-Assistenten | Microsoft-Dokumentation
description: Erstellen eines Berichts mithilfe des Berichts-Assistenten in Power Apps
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "3302930"
---
# <a name="create-a-report-using-the-report-wizard"></a>Erstellen eines Berichts mithilfe des Berichts-Assistenten


Verwenden Sie den Berichts-Assistenten, um Berichte mit Diagrammen und Tabellen zu erstellen, mit denen Sie Ihre Daten problemlos analysieren können. 

Alle mit dem Berichts-Assistenten erstellten Berichte basieren auf der Fetch-Funktion. Beachten Sie, dass alle mit dem Berichts-Assistenten generierten Berichte im Querformat gedruckt werden.

## <a name="create-a-new-report"></a>Erstellen eines neuen Berichts

1. Wählen Sie im linken Navigationsbereich den Bereich „Berichte“ aus.  
2. Wählen Sie auf der Befehlsleiste **Neu** aus.

    > [!div class="mx-imgBorder"]
    > ![Erstellen eines neuen Berichts](media/newreport.png "Erstellen eines neuen Berichts")
  
3. Der Bildschirm **Bericht: Neuer Bericht** wird angezeigt. Behalten Sie für **Berichtstyp** die Standardauswahl **Bericht des Berichts-Assistenten** bei, und wählen Sie die Schaltfläche **Berichts-Assistenten** aus. 

    > [!div class="mx-imgBorder"]
    > ![Berichts-Assistent](media/report_wizard.png "Bildschirm „Berichts-Assistent“")
  
4. Behalten Sie im nächsten Bildschirm die Standardauswahl bei, und wählen Sie dann **Weiter** aus.
 
    > [!div class="mx-imgBorder"]
    > ![Berichts-Assistent](media/report_wizard_1.png "Bildschirm „Berichts-Assistent“")
   
4. Geben Sie im Bildschirm **Berichtseigenschaften** einen Namen für den Bericht ein, und wählen Sie dann den Datensatz aus, der in den Bericht eingeschlossen werden soll. Klicken Sie dann auf **Weiter**.
 
    > [!div class="mx-imgBorder"]
    > ![Bildschirm „Berichtseigenschaften“](media/report_wizard_2.png "Bildschirm „Berichtseigenschaften“")
  
5.  Wählen Sie im Bildschirm **Wählen Sie die Datensätze aus, die im Bericht enthalten sein sollen.** die Filter aus, um zu bestimmen, welche Datensätze in den Bericht eingeschlossen werden. Wenn Sie z. B. nur Ergebnisse für Datensätze anzeigen möchten, die in den letzten 60 Tagen geändert wurden, können Sie diesen Filter in diesem Bildschirm festlegen. Wenn Sie nicht möchten, dass die Daten gefiltert werden, wählen Sie **Löschen** aus.

    > [!div class="mx-imgBorder"]
    > ![Wählen Sie die Datensätze aus, die im Bericht enthalten sein sollen.*](media/report_wizard_3.png "Wählen Sie die Datensätze aus, die im Bericht enthalten sein sollen.")
  
6. Wählen Sie im Bildschirm **Layout für Felder** das Layout des Berichts aus. Wählen Sie **Klicken Sie hier, um eine Gruppierung hinzuzufügen.** aus, und wählen Sie aus, wie die Daten gruppiert werden sollen.

    > [!div class="mx-imgBorder"]
    > ![Layout für Felder](media/report_wizard_4.png "Layout für Felder")

7. Wählen Sie den **Datensatztyp** und die **Spalte** für die Daten aus, die im Bericht gruppiert werden sollen. Wenn Sie Ihre Auswahl getroffen haben, wählen Sie **OK** aus.

    > [!div class="mx-imgBorder"]
    > ![Bildschirm „Gruppierung hinzufügen“](media/report_wizard_5.png "Bildschirm „Gruppierung hinzufügen“")
  
8. Wählen Sie **Hier klicken, um eine Spalte hinzuzufügen.** für Spalten mit Daten aus, die sich auf den im vorherigen Schritt ausgewählten Datensatztyp beziehen.  

    > [!div class="mx-imgBorder"]
    > ![Bildschirm „Gruppierung hinzufügen“](media/report_wizard_6.png "Bildschirm „Gruppierung hinzufügen“")

9. Wählen Sie im Bildschirm **Spalte hinzufügen** die Daten aus, die für die Spalte angezeigt werden sollen, und wählen Sie dann **OK** aus. 

    > [!div class="mx-imgBorder"]
    > ![Bildschirm „Spalte hinzufügen“](media/report_wizard_7.png "Bildschirm „Spalte hinzufügen“")
  
10. Wiederholen Sie den vorherigen Schritt für alle zusätzlichen Spalten, die Sie hinzufügen möchten. Wenn Sie den Vorgang abgeschlossen haben, wählen Sie im Bildschirm **Layout für Felder** die Option **Weiter** aus.
 
    > [!div class="mx-imgBorder"]
    > ![Bildschirm „Weitere Spalte hinzufügen“](media/report_wizard_8.png "Bildschirm „Weitere Spalte hinzufügen“")
  
11. Wählen Sie im Bildschirm **Bericht formatieren** aus, wie der Bericht formatiert werden soll, und wählen Sie dann **Weiter** aus.
 
    > [!div class="mx-imgBorder"]
    > ![Bericht formatieren](media/report_wizard_9.png "Bildschirm „Bericht formatieren“")

12. Überprüfen Sie die Zusammenfassung des Berichts, und wählen Sie **Weiter** und dann **Fertigstellen** aus. Dieser Bericht wird nun in der Berichtsliste im System angezeigt.

    > [!div class="mx-imgBorder"]
    > ![Bericht anzeigen](media/report_wizard_10.png "Anzeigen des Berichts")

### <a name="see-also"></a>Siehe auch
[Arbeiten mit Berichten](work-with-reports.md) 

[Hinzufügen eines vorhandenen Berichts](add-existing-report.md)

[Bearbeiten des Standardfilters eines Berichts](edit-report-filter.md)

[Behandeln von Problemen im Zusammenhang mit nicht angezeigten Berichtsdaten](troubleshoot-reports.md)



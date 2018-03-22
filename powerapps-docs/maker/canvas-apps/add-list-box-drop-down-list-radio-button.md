---
title: Hinzufügen von Listenfeldern, Dropdownlisten und Optionsfeldern | Microsoft-Dokumentation
description: Erstellen oder Konfigurieren von Mehrfachauswahl-Optionen in PowerApps
services: ''
suite: powerapps
documentationcenter: ''
author: lonu
manager: anneta
editor: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/23/2016
ms.author: lonu
ms.openlocfilehash: 8eacac89f7578a83757299b8e627cf757fb1c6d7
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons"></a>Hinzufügen von Listenfeldern, Dropdownlisten oder Optionsfeldern
PowerApps bietet Mehrfachauswahl- und Einfachauswahl-Optionen; hierzu zählen ein Listenfeld, eine Dropdownliste und Optionsfelder. In diesem Thema werden diese Steuerelemente hinzugefügt, und mithilfe einer **Tabellen**-Formel werden die Listen erstellt. Wenn ein Element in der Liste ausgewählt wird, werden andere Steuerelemente aktualisiert.

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="add-a-list-box"></a>Hinzufügen eines Listenfelds
1. Wählen Sie auf der Registerkarte **Einfügen** die Option **Steuerelemente** und anschließend **Listenfeld** aus:  

    ![][2]  

2. Benennen Sie das **Listenfeld**-Steuerelement in **MyListBox** um:  

    ![][3]

3. Legen Sie seine **[Items](controls/properties-core.md)**-Eigenschaft auf den folgenden Ausdruck fest:  
   ```["circle","triangle","rectangle"]```  <br/>

    Der Designer sieht nun etwa wie folgt aus:

    ![][4]

4. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole** aus, wählen Sie den Kreis aus, und verschieben Sie ihn unter das **Listenfeld**-Steuerelement:

    ![][5]  

5. Fügen Sie ein Dreieck und ein Rechteck aus, und ordnen Sie die Formen unter dem **Listenfeld**-Steuerelement in einer Reihe an:

    ![][6]  

6. Legen Sie die **[Visible](controls/properties-core.md)**-Eigenschaft der folgenden Formen auf die genannten Funktionen fest:  

   | Form | Wert für Visible-Funktion |
   | --- | --- |
   | circle |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | triangle |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | rectangle |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. Rufen Sie eine Vorschau der Ergebnisse auf (![][1]). Wählen Sie die verschiedenen Formen im **Listenfeld**-Steuerelement aus. Nur die ausgewählte Form bzw. die ausgewählten Formen werden angezeigt. Drücken Sie ESC, oder wählen Sie das **X** aus, um zum Bildschirm zurückzukehren.

In diesen Schritten haben Sie mithilfe eines Ausdrucks eine Liste von Elementen in einem **Listenfeld**-Steuerelement erstellt. Je nach Auswahl im **Listenfeld**-Steuerelement werden andere Formen angezeigt. Sie können diese Vorgehensweise auf andere Elemente im Unternehmen anwenden. Sie können mit einem **Listenfeld**-Steuerelement beispielsweise Produktabbildungen, Produktbeschreibungen usw. anzeigen.

## <a name="add-radio-buttons"></a>Hinzufügen von Optionsfeldern
1. Wählen Sie auf der Registerkarte **Start** die Option **Neuer Bildschirm** aus.

2. Wählen Sie auf der Registerkarte **Einfügen** die Option **Steuerelemente** und anschließend **Radio** aus.

    ![][10]  

3. Benennen Sie das **Radio**-Steuerelement in **Choices** um, und legen Sie seine **[Items](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    Ändern Sie ggf. die Größe des Steuerelements, um alle Optionen anzuzeigen.

4. Wählen Sie auf der Registerkarte **Einfügen** die Option **Symbole** aus, und wählen Sie anschließend den Kreis aus.

5. Legen Sie die **[Fill](controls/properties-color-border.md)**-Eigenschaft des Kreises auf die folgende Funktion fest:  
   ```If(Choices.Selected.Value = "red", RGBA(192, 0, 0, 1), Choices.Selected.Value = "green", RGBA(0, 176, 80, 1), Choices.Selected.Value = "blue", RGBA(0, 32, 96, 1))```  

    In dieser Formel ändert der Kreis je nach ausgewähltem Optionsfeld seine Farbe.

6. Verschieben Sie den Kreis wie im folgenden Beispiel veranschaulicht unter das **Radio**-Steuerelement:

    ![][14]  

7. Rufen Sie eine Vorschau der Ergebnisse auf (![][1]). Wählen Sie ein anderes Optionsfeld aus, um die Farbe des Kreises ändern. Drücken Sie ESC, oder wählen Sie das **X** aus, um zum Bildschirm zurückzukehren.

## <a name="add-a-drop-down-list"></a>Hinzufügen einer Dropdownliste
1. Fügen Sie einen Bildschirm hinzu, und fügen Sie anschließend ein **Dropdown**-Steuerelement hinzu.

    ![][15]  

2. Benennen Sie das Steuerelement in **DDChoices** um, und legen Sie seine **[Items](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>
   **["red","green","blue"]**

3. Fügen Sie einen Kreis hinzu, verschieben Sie ihn unter das **Dropdown**-Steuerelement, und legen Sie die **[Fill](controls/properties-color-border.md)**-Eigenschaft des Kreises auf diese Formel fest:  
   ```If(DDChoices.Selected.Value = "red", RGBA(192, 0, 0, 1), DDChoices.Selected.Value = "green", RGBA(0, 176, 80, 1), DDChoices.Selected.Value = "blue", RGBA(0, 32, 96, 1))```

4. Rufen Sie eine Vorschau der Ergebnisse auf (![][1]). Wählen Sie die anderen Optionen zum Ändern der Farbe des Kreises aus.

[1]: ./media/add-list-box-drop-down-list-radio-button/preview.png
[2]: ./media/add-list-box-drop-down-list-radio-button/listbox.png
[3]: ./media/add-list-box-drop-down-list-radio-button/renamelistbox.png
[4]: ./media/add-list-box-drop-down-list-radio-button/itemslistbox.png
[5]: ./media/add-list-box-drop-down-list-radio-button/circle.png
[6]: ./media/add-list-box-drop-down-list-radio-button/allshapes.png
[10]: ./media/add-list-box-drop-down-list-radio-button/radiobutton.png
[12]: ./media/add-list-box-drop-down-list-radio-button/itemsradio.png
[14]: ./media/add-list-box-drop-down-list-radio-button/radiocircle.png
[15]: ./media/add-list-box-drop-down-list-radio-button/dropdown.png

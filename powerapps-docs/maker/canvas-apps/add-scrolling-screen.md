---
title: Hinzufügen eines Scrollbildschirms | Microsoft-Dokumentation
description: Erstellen Sie einen Bildschirm, durch den Benutzer scrollen können, um mehr Inhaltstypen anzuzeigen, als mit einem Mal auf dem Bildschirm angezeigt werden können.
documentationcenter: na
author: lonu
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 10/25/2016
ms.author: lonu
ms.openlocfilehash: fd7b418de7a78220dfc1019c923749fb8e6ddf5c
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="add-a-scrolling-screen-in-powerapps"></a>Hinzufügen eines Scrollbildschirms in PowerApps
Erstellen Sie einen Bildschirm, durch den Benutzer scrollen können, um andere Elemente anzuzeigen. Sie können beispielsweise eine App erstellen, in der Daten in einem Säulendiagramm und einem Liniendiagramm dargestellt werden. Durch Hinzufügen eines Scrollbildschirms können Sie mehrere Steuerelemente hinzufügen, die Benutzer beim Scrollen anzeigen können.

Wenn Sie in einem Abschnitt mehrere Steuerelemente hinzufügen, bleibt die relative Position der Steuerelemente im Abschnitt erhalten, wobei es keine Rolle spielt, ob es sich um eine Smartphone-App oder eine Tablet-App handelt. Beachten Sie, dass sich Bildschirmgröße und -ausrichtung auf die Anordnung der Abschnitte auswirken können.  

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-scrolling-screen"></a>Erstellen eines Scrollbildschirms
1. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Neuer Bildschirm**:
   
    ![Option zum Hinzufügen eines Bildschirms zu einer App][1]
2. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Layouts**, und klicken oder tippen Sie anschließend auf die Option zum Erstellen eines unendlichen Scrolling-Zeichenbereichs:  
   
    ![Option zum Hinzufügen eines unendlichen Scrolling-Zeichenbereichs][2]
   
    Dem Zeichenbereich wird Folgendes hinzugefügt:  
   
    ![Ein Bildschirm mit einem unendlichen Scrolling-Zeichenbereich in seiner Standarddarstellung][3]

## <a name="add-elements"></a>Hinzufügen von Elementen
Fügen wir dem Zeichenbereich nun einige Steuerelemente hinzu, um die Funktionsweise des Scrollbildschirms zu veranschaulichen.

1. Klicken oder tippen Sie im hinzugefügten Zeichenbereich auf **Ein Element von der Registerkarte „Einfügen“ hinzufügen**.
   
    ![][4]
2. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Diagramme**, und klicken oder tippen Sie anschließend auf **Säulendiagramm**.
   
    ![Option zum Hinzufügen eines Säulendiagramms][5]
   
    Ein Säulendiagramm wird in der ersten Karte auf dem Bildschirm angezeigt:  
   
    ![Standardmäßiges Säulendiagramm][7]
3. Klicken oder tippen Sie auf der Registerkarte **Einfügen** auf **Text**, und klicken oder tippen Sie anschließend auf **Stifteingabe**:  
   
    ![Option zum Hinzufügen eines Stift-Steuerelements][8]
4. Verschieben Sie das Stift-Steuerelement unter das Diagramm, und ändern Sie die Größe des Steuerelements so, dass es den unteren Rand der Karte bedeckt:  
   
    ![Stift-Steuerelement verschieben und dessen Größe ändern][9]

## <a name="add-a-section"></a>Hinzufügen eines Abschnitts
Nun fügen wir eine weitere Karte mit einem weiteren Steuerelement hinzu.

1. Klicken oder tippen Sie am unteren Rand des Bildschirms auf **Abschnitt hinzufügen**:  
   
    ![Option zum Hinzufügen eines Abschnitts][10]
   
    Dem Bildschirm wird eine neue Karte hinzugefügt:  
   
    ![Neue Karte unter dem Standardabschnitt][11]
2. Wechseln Sie bei ausgewählter Karte zur Registerkarte **Einfügen**, klicken oder tippen Sie auf **Diagramme**, und klicken oder tippen Sie anschließend auf **Liniendiagramm**.
   
    Das neue Diagramm ist zu groß, um gemeinsam mit den anderen Steuerelementen auf dem Bildschirm angezeigt zu werden:  
   
    ![Am unteren Rand der neuen Karte hinzugefügtes Liniendiagramm][12]
3. Öffnen Sie den Vorschaumodus durch Drücken von F5 (oder durch Klicken oder Tippen des Wiedergabe-Symbols in der Nähe der oberen rechten Ecke).
   
    ![Öffnen des Vorschaumodus](./media/add-scrolling-screen/open-preview.png)
4. Scrollen Sie nach unten, um das neue Liniendiagramm anzuzeigen.  
   
    ![Vorschau des Liniendiagramms][13]

[1]: ./media/add-scrolling-screen/add-screen.png
[2]: ./media/add-scrolling-screen/add-canvas.png
[3]: ./media/add-scrolling-screen/default-canvas.png
[4]: ./media/add-scrolling-screen/insert-visual.png
[5]: ./media/add-scrolling-screen/add-chart.png
[7]: ./media/add-scrolling-screen/default-chart.png
[8]: ./media/add-scrolling-screen/add-pen.png
[9]: ./media/add-scrolling-screen/move-resize-pen.png
[10]: ./media/add-scrolling-screen/add-section.png
[11]: ./media/add-scrolling-screen/new-card.png
[12]: ./media/add-scrolling-screen/add-line-chart.png
[13]: ./media/add-scrolling-screen/line-chart-preview.png

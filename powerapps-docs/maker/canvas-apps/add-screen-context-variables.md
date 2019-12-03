---
title: Hinzufügen eines Bildschirms in eine Canvas-App und Wechseln zwischen Bildschirmen | Microsoft-Dokumentation
description: Hinzufügen eines Bildschirms zu einer Canvas-APP und Verwenden von vorwärts-und rückwärts Pfeilen zum Wechseln zwischen Bildschirmen in Power apps
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cbe6173c94f001874b126a5b8ecb1bdf9ad21b70
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724421"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>Hinzufügen eines Bildschirms in eine Canvas-App und Wechseln zwischen Bildschirmen

Erstellen Sie eine Canvas-App mit mehreren Bildschirmen, und bieten Sie Benutzern Möglichkeiten, zwischen diesen Bildschirmen zu wechseln.

## <a name="add-and-rename-a-screen"></a>Hinzufügen und Umbenennen eines Bildschirms

1. Wählen Sie auf der Registerkarte **Startseite** die Option **neuer Bildschirm**aus, und wählen Sie dann den Typ des hinzu zufügenden Bildschirms aus.

    ![Option zum Hinzufügen von Bildschirmen auf der Registerkarte „Start“](./media/add-screen-context-variables/add-screen.png)

2. Wählen Sie im rechten Bereich den Namen des Bildschirms (direkt oberhalb der Registerkarte **Eigenschaften** ) aus, und geben Sie dann **Source**ein.

    ![Umbenennen des Standardbildschirms](./media/add-screen-context-variables/name-source-screen.png)

3. Fügen Sie einem weiteren Bildschirm hinzu, und benennen Sie diesen **Target**.

    ![Zwei Bildschirme auf der linken Navigationsleiste](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>Bildschirme neu anordnen

Zeigen Sie in der linken Navigationsleiste auf einen Bildschirm, den Sie nach oben oder unten verschieben möchten, wählen Sie die Schaltfläche mit den Auslassungs Zeichen aus, und klicken Sie dann **auf nach oben** oder **nach unten**.

![Bildschirm neu anordnen](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> Wenn die APP geöffnet wird, wird der Bildschirm am oberen Rand der hierarchischen Liste der Steuerelemente in der Regel zuerst angezeigt. Sie können jedoch einen anderen Bildschirm angeben, indem Sie die **[OnStart](controls/control-screen.md)** -Eigenschaft auf eine Formel festlegen, die die **[Navigate](functions/function-navigate.md)** -Funktion enthält.

## <a name="add-navigation"></a>Navigation hinzufügen

1. Öffnen Sie bei ausgewähltem **Quell** Bildschirm die Registerkarte **Einfügen** , wählen Sie **Symbole**aus, und klicken Sie dann auf **weiter**.  

    ![Option „Formen“ auf der Registerkarte „Einfügen“](./media/add-screen-context-variables/add-next-arrow.png)

2. (optional) Verschieben Sie den Pfeil, sodass er sich in der unteren rechten Ecke des Bildschirms befindet.

3. Wählen Sie bei ausgewähltem Pfeil die Registerkarte **Aktion** aus, und klicken Sie dann auf **Navigieren**.

    Die **[OnSelect](controls/properties-core.md)** -Eigenschaft für den Pfeil wird automatisch auf eine **Navigate**-Funktion festgelegt.

    ![Auf Navigate-Funktion festgelegte OnSelect-Eigenschaft](./media/add-screen-context-variables/onselect-default.png)

    Wenn ein Benutzer den Pfeil auswählt, wird der **Ziel** Bildschirm ausgeblendet.

4. Fügen Sie im Bildschirm **Target** einen **Pfeil „Zurück“** hinzu, und legen Sie dessen **[OnSelect](controls/properties-core.md)** -Eigenschaft auf die folgende Formel fest:

    `Navigate(Source, ScreenTransition.Fade)`

5. Wenn Sie die Alt-Taste gedrückt halten, wechseln Sie zwischen den Bildschirmen, indem Sie den Pfeil auf jedem Bildschirm auswählen.

## <a name="more-information"></a>Weitere Informationen

[Bildschirm Steuerungs Referenz](controls/control-screen.md)
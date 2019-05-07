---
title: Hinzufügen eines Bildschirms in eine Canvas-App und Wechseln zwischen Bildschirmen | Microsoft-Dokumentation
description: Fügen Sie einer Canvas-App einen Bildschirm hinzu, und nutzen Sie die Weiter- und Zurück-Pfeile, um in PowerApps zwischen Bildschirmen zu wechseln
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
ms.openlocfilehash: b6f83d21b2964dac7c4925d45efdf11a3a1e6b02
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63321383"
ms.PowerAppsDecimalTransform: true
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>Hinzufügen eines Bildschirms in eine Canvas-App und Wechseln zwischen Bildschirmen

Erstellen Sie eine Canvas-App mit mehreren Bildschirmen, und bieten Sie Benutzern Möglichkeiten, zwischen diesen Bildschirmen zu wechseln.

## <a name="add-and-rename-a-screen"></a>Hinzufügen und Umbenennen eines Bildschirms

1. Auf der **Startseite** Registerkarte **neuer Bildschirm**, und wählen Sie dann auf die Art des Bildschirms, die Sie hinzufügen möchten.

    ![Option zum Hinzufügen von Bildschirmen auf der Registerkarte „Start“](./media/add-screen-context-variables/add-screen.png)

2. Wählen Sie im rechten Bereich, den Namen des Bildschirms (direkt über die **Eigenschaften** Registerkarte), und geben Sie dann **Quelle**.

    ![Umbenennen des Standardbildschirms](./media/add-screen-context-variables/name-source-screen.png)

3. Fügen Sie einem weiteren Bildschirm hinzu, und benennen Sie diesen **Target**.

    ![Zwei Bildschirme auf der linken Navigationsleiste](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>Bildschirme neu anordnen

Zeigen Sie in der linken Navigationsleiste auf einen Bildschirm, den Sie verwenden möchten, nach oben oder unten, wählen Sie die Schaltfläche mit den Auslassungspunkten, das angezeigt wird, und wählen Sie dann **nach oben verschieben** oder **nach unten verschieben**.

![Neuanordnen von Bildschirm](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> Wenn die app geöffnet wird, wird der Bildschirm am oberen Rand der hierarchischen Liste der Steuerelemente in der Regel zuerst angezeigt. Aber Sie können einen anderen Bildschirm angeben, durch Festlegen der **[OnStart](controls/control-screen.md)** Eigenschaft, um eine Formel mit den **[Navigate](functions/function-navigate.md)** Funktion.

## <a name="add-navigation"></a>Navigation hinzufügen

1. Mit der **Quelle** Bildschirm ausgewählt haben, öffnen Sie die **einfügen** Registerkarte **Symbole**, und wählen Sie dann **Pfeil "Weiter"**.  

    ![Option „Formen“ auf der Registerkarte „Einfügen“](./media/add-screen-context-variables/add-next-arrow.png)

2. (optional) Verschieben Sie den Pfeil, sodass er sich in der unteren rechten Ecke des Bildschirms befindet.

3. Wählen Sie bei ausgewähltem Pfeil, der **Aktion** Registerkarte, und wählen Sie dann **Navigate**.

    Die **[OnSelect](controls/properties-core.md)**-Eigenschaft für den Pfeil wird automatisch auf eine **Navigate**-Funktion festgelegt.

    ![Auf Navigate-Funktion festgelegte OnSelect-Eigenschaft](./media/add-screen-context-variables/onselect-default.png)

    Wenn ein Benutzer auf den Pfeil klickt der **Ziel** Bildschirm eingeblendet.

4. Fügen Sie im Bildschirm **Target** einen **Pfeil „Zurück“** hinzu, und legen Sie dessen **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:

    `Navigate(Source; ScreenTransition.Fade)`

5. Während Sie die Alt-Taste gedrückt halten, wechseln Sie zwischen den Bildschirmen, indem Sie den Pfeil auf den einzelnen Bildschirmen auswählen.

## <a name="more-information"></a>Weitere Informationen

[Bildschirm-Steuerelement: Referenz](controls/control-screen.md)
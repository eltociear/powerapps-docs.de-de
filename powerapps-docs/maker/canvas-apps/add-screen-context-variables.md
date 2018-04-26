---
title: Hinzufügen eines Bildschirms und Wechseln zwischen Bildschirmen | Microsoft-Dokumentation
description: Fügen Sie einer App einen Bildschirm hinzu, und nutzen Sie die Weiter- und Zurück-Pfeile, um in PowerApps zwischen Bildschirmen zu wechseln
documentationcenter: na
author: aftowen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 07/10/2017
ms.author: anneta
ms.openlocfilehash: 19c06fa9bfc7098227e5f30a1c913522d9e6e7a3
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="add-a-screen-and-navigate-between-screens"></a>Hinzufügen eines Bildschirms und Wechseln zwischen Bildschirmen
Erstellen Sie eine App mit mehreren Bildschirmen, und bieten Sie Benutzern Möglichkeiten, zwischen diesen Bildschirmen zu wechseln.

## <a name="prerequisites"></a>Voraussetzungen
* Erfahren Sie, wie Sie ein [Steuerelement konfigurieren](add-configure-controls.md).
* Erstellen oder öffnen Sie eine App.

## <a name="add-and-rename-a-screen"></a>Hinzufügen und Umbenennen eines Bildschirms
1. Klicken oder tippen Sie auf der Registerkarte **Start** auf **Neuer Bildschirm**.

    ![Option zum Hinzufügen von Bildschirmen auf der Registerkarte „Start“](./media/add-screen-context-variables/add-screen.png)

2. Klicken oder tippen Sie im rechten Bereich auf den Namen des Bildschirms (direkt über der Registerkarte **Eigenschaften**), und geben Sie anschließend den neuen Namen **Source** (Quelle) ein.

    ![Umbenennen des Standardbildschirms](./media/add-screen-context-variables/name-source-screen.png)

3. Fügen Sie einem weiteren Bildschirm hinzu, und benennen Sie diesen **Target**.

    ![Zwei Bildschirme auf der linken Navigationsleiste](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="add-navigation"></a>Navigation hinzufügen
1. Öffnen Sie bei ausgewähltem Bildschirm **Source** die Registerkarte **Einfügen**, klicken oder tippen Sie auf **Symbole** und anschließend auf den **Pfeil „Weiter“**.  

    ![Option „Formen“ auf der Registerkarte „Einfügen“](./media/add-screen-context-variables/add-next-arrow.png)

2. (optional) Verschieben Sie den Pfeil, sodass er sich in der unteren rechten Ecke des Bildschirms befindet.

3. Klicken oder tippen Sie bei ausgewähltem Pfeil auf die Registerkarte **Aktion** und anschließend auf **Navigieren**.

    Die **[OnSelect](controls/properties-core.md)**-Eigenschaft für den Pfeil wird automatisch auf eine **Navigate**-Funktion festgelegt.  

    ![Auf Navigate-Funktion festgelegte OnSelect-Eigenschaft](./media/add-screen-context-variables/onselect-default.png)

    Wenn ein Benutzer auf den Pfeil klickt oder tippt, wird der Bildschirm **Target** eingeblendet.

4. Fügen Sie im Bildschirm **Target** einen **Pfeil „Zurück“** hinzu, und legen Sie dessen **[OnSelect](controls/properties-core.md)**-Eigenschaft auf die folgende Formel fest:
   <br>**Navigate(Source, ScreenTransition.Fade)**

5. Öffnen Sie den Vorschaumodus (![](./media/add-screen-context-variables/preview.png) oder drücken Sie F5), und wechseln Sie dann zwischen den Bildschirmen, indem Sie auf die hinzugefügten Pfeile klicken oder tippen.

6. Drücken Sie **ESC**, um zum Standardarbeitsbereich zurückzukehren.

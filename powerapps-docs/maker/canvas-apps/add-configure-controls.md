---
title: Hinzufügen und Konfigurieren eines Canvas-App-Steuerelements | Microsoft-Dokumentation
description: Hier erhalten Sie schrittweise Anweisungen, anhand derer Sie Canvas-App-Steuerelemente direkt, über die Symbolleiste, auf der Registerkarte „Eigenschaften“ oder in der Bearbeitungsleiste hinzufügen und konfigurieren können.
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/25/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 798a355e1c8728b41f3e92f183d4a4e2831b7cc2
ms.sourcegitcommit: 90245baddce9d92c3ce85b0537c1ac1cf26bf55a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "57799454"
---
# <a name="add-and-configure-a-canvas-app-control-in-powerapps"></a>Hinzufügen und Konfigurieren eines Canvas-App-Steuerelements in PowerApps

Fügen Sie Ihrer Canvas-App vielfältige Benutzeroberflächenelemente hinzu, und konfigurieren Sie Aspekte ihrer Darstellung und ihres Verhaltens direkt, über die Symbolleiste, auf der Registerkarte **Eigenschaften** oder in der Bearbeitungsleiste. Diese Elemente der Benutzeroberfläche werden als Steuerelemente bezeichnet, während die von Ihnen konfigurierten Aspekte als Eigenschaften bezeichnet werden.

## <a name="prerequisites"></a>Voraussetzungen

1. Wenn Sie noch nicht über eine PowerApps-Lizenz verfügen [registrieren](../signup-for-powerapps.md), und klicken Sie dann [Anmeldung](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc).
1. Klicken Sie unter **eigene App**, zeigen Sie auf **Canvas-app mit leerer App**, und wählen Sie dann **diese App**.
1. Wenn Sie aufgefordert werden, die Einführung anzuschauen, wählen Sie **Weiter** mit wichtigen Bereichen der PowerApps Schnittstelle vertraut machen (oder wählen Sie **überspringen**).

    Sie können die Tour immer später erstellen, indem Sie auf das Fragezeichen-Symbol in der Nähe der oberen rechten Ecke des Bildschirms, und wählen Sie dann **Einführungstour**.

## <a name="add-and-select-a-control"></a>Fügen Sie hinzu, und wählen Sie ein Steuerelement

Auf der **einfügen** Registerkarte, führen Sie einen der folgenden Schritte aus:

- Wählen Sie **Bezeichnung** oder **Schaltfläche** einen dieser Typen von Steuerelementen hinzufügen.
- Wählen Sie eine Kategorie von Steuerelementen, und wählen Sie dann auf den Typ des Steuerelements, die Sie hinzufügen möchten.

Wählen Sie z. B. **neuer Bildschirm**, und wählen Sie dann **leere** auf einen leeren Bildschirm Ihrer app hinzufügen. (Die Bildschirme sind eine Art von Steuerelement, das weitere Typen von Steuerelementen enthalten kann.)

![Bildschirm "hinzufügen"](./media/add-configure-controls/add-screen.png)

Den Namen des neuen Bildschirms **Screen2** und wird im linken Navigationsbereich angezeigt. Diesem Bereich werden eine hierarchische Liste der Steuerelemente in Ihrer app, sodass Sie problemlos ermitteln können, und wählen Sie jedes Steuerelement.

![Screen2 in Liste](./media/add-configure-controls/list-screen2.png)

Wählen Sie zur Veranschaulichung der Funktionsweise dieser Liste, **Bezeichnung** auf die **einfügen** Registerkarte. Das neue Steuerelement wird unter **Screen2** in der hierarchischen Liste.

![Screen2 in Liste](./media/add-configure-controls/add-label.png)

Auf dem Bildschirm umschließt ein Feld mit sechs Handles die Bezeichnung in der Standardeinstellung an. Diese Art von Feld umgeben ist, welches Steuerelement ausgewählt ist. Wenn Sie den Bildschirm durch Klicken oder tippen es (jedoch außerhalb der Bezeichnung) auswählen, wird das Feld aus der Bezeichnung ausgeblendet. Bezeichnung auszuwählen erneut, Sie können klicken oder tippen Sie auf diese oder können Sie klicken oder tippen Sie auf **Label2** in der hierarchischen Liste der Steuerelemente.

> [!IMPORTANT]
> Sie müssen immer ein Steuerelement auswählen, bevor Sie sie konfigurieren können.

## <a name="rename-a-control"></a>Umbenennen eines Steuerelements

Wählen Sie in der hierarchischen Liste der Steuerelemente, zeigen Sie auf das Steuerelement, das Sie umbenennen möchten, die angezeigt wird, und wählen Sie dann Schaltfläche mit den Auslassungspunkten **umbenennen**. Sie können dann einen eindeutigen, einprägsamen Namen auf, die Erstellung Ihrer app leichter eingeben.

![Umbenennen des Steuerelements](./media/add-configure-controls/rename-control.png)

## <a name="delete-a-control"></a>Löschen eines Steuerelements

Wählen Sie in der hierarchischen Liste der Steuerelemente, die das Steuerelement, das Sie löschen möchten, zeigen Sie auf die Schaltfläche, die angezeigt wird, und wählen Sie dann **löschen**. Um ein Steuerelement zu löschen, die nicht von einem Bildschirm ist, können Sie auch das Steuerelement auf der Canvas auswählen, und drücken Sie dann die ENTF-Taste.

![Steuerelement löschen](./media/add-configure-controls/delete-control.png)

## <a name="reorder-screens"></a>Bildschirme neu anordnen

Zeigen Sie in der hierarchischen Liste von Steuerelementen, die einen Bildschirm, den Sie verwenden möchten, nach oben oder unten, wählen Sie die Schaltfläche mit den Auslassungspunkten, das angezeigt wird, und wählen Sie dann **nach oben verschieben** oder **nach unten verschieben**.

![Neuanordnen von Bildschirm](./media/add-configure-controls/reorder-screen.png)

> [!NOTE]
> Wenn die app geöffnet wird, wird der Bildschirm am oberen Rand der hierarchischen Liste der Steuerelemente in der Regel zuerst angezeigt. Aber Sie können einen anderen Bildschirm angeben, durch Festlegen der **[OnStart](controls/control-screen.md)** Eigenschaft, um eine Formel mit den **[Navigate](functions/function-navigate.md)** Funktion.

## <a name="move-and-resize-a-control"></a>Verschieben und die Größe eines Steuerelements

Um ein Steuerelement verschieben möchten, wählen Sie aus, zeigen Sie auf seinen Mittelpunkt, damit der Pfeil mit vier Spitzen wird angezeigt, und ziehen Sie das Steuerelement dann an einen anderen Speicherort.

![Steuerelement verschieben](./media/add-configure-controls/move-control.png)

Klicken Sie zum Ändern der Größe eines Steuerelements wählen Sie aus, zeigen Sie auf beliebiges Handle, das im Auswahlfeld, damit der Pfeil mit zwei Spitzen angezeigt wird, und ziehen Sie dann auf das Handle.

![Steuerelement verschieben](./media/add-configure-controls/resize-control.png)

> [!NOTE]
> Wie weiter unten in diesem Thema wird beschrieben, Sie können auch verschieben und die Größe eines Steuerelements durch eine beliebige Kombination von Ändern seiner  **[X](controls/properties-size-location.md)**,  **[Y](controls/properties-size-location.md)**,  **[Höhe](controls/properties-size-location.md)**, und **[Breite](controls/properties-size-location.md)** Eigenschaften in der Bearbeitungsleiste angezeigt.

## <a name="change-the-text-of-a-label-or-a-button"></a>Ändern des Texts einer Bezeichnung oder eine Schaltfläche

Wählen Sie eine Bezeichnung oder eine Schaltfläche, doppelklicken Sie auf den Text, der im Steuerelement angezeigt wird, und geben Sie dann den gewünschten Text.

![Ändern Sie text](./media/add-configure-controls/change-text.png)

> [!NOTE]
> Wie weiter unten in diesem Thema wird beschrieben, können Sie diesen Text auch ändern, indem Sie ändern die **[Text](controls/properties-core.md)** -Eigenschaft in der Bearbeitungsleiste angezeigt.

## <a name="configure-a-control-from-the-toolbar"></a>Konfigurieren eines Steuerelements über die Symbolleiste

Durch Konfigurieren eines Steuerelements über die Symbolleiste können Sie eine größere Anzahl von Optionen als beim direkten Konfigurieren eines Steuerelements angeben.

Sie können z. B. eine Bezeichnung auswählen, wählen Sie die **Startseite** Registerkarte, und ändern Sie die Schriftart des Texts in der Bezeichnung.

![Schriftart ändern](./media/add-configure-controls/change-font.png)

## <a name="configure-a-control-from-the-properties-tab"></a>Konfigurieren eines Steuerelements auf der Registerkarte „Eigenschaften“

Mithilfe der **Eigenschaften** Registerkarte können Sie eine größere Anzahl von Optionen als durch Konfigurieren eines Steuerelements auf der Symbolleiste Sie können angeben.

Z. B. Sie können ein Steuerelement auswählen und dann ein- oder ausblenden, indem Sie ändern die **Visible** Eigenschaft.

![Sichtbarkeit einstellen](./media/add-configure-controls/set-visibility.png)

## <a name="configure-a-control-in-the-formula-bar"></a>Konfigurieren eines Steuerelements in der Bearbeitungsleiste

Anstatt ein Steuerelement zu konfigurieren, direkt, über die Symbolleiste oder in der **Eigenschaften** Registerkarte können Sie ein Steuerelement konfigurieren, indem Sie eine Eigenschaft in der Eigenschaftenliste auswählen und anschließend einen Wert in der Bearbeitungsleiste angeben. Mit dieser Vorgehensweise können Sie Eigenschaften nach ihrer alphabetischen Reihenfolge durchsuchen, und Sie können mehr Werttypen angeben.

Sie können z. B. eine Bezeichnung auswählen und konfigurieren sie Sie anschließend auf folgende Weise:

- Verschieben Sie ihn dazu **X** oder **Y** in der Liste der Eigenschaften und anschließend eine andere Anzahl in der Bearbeitungsleiste angeben.

    ![Legen Sie X-Eigenschaft](./media/add-configure-controls/x-property.png)

- Ändern Sie die Größe durch Auswahl **Höhe** oder **Breite** in der Liste der Eigenschaften und anschließend eine andere Anzahl in der Bearbeitungsleiste angeben.

    ![Legen Sie die Height-Eigenschaft](./media/add-configure-controls/height-property.png)

- Ändern Sie den Text durch auswählen **Text** in der Liste der Eigenschaften und anschließend eine beliebige Kombination von eine Literalzeichenfolge, einen Ausdruck oder eine Formel in der Bearbeitungsleiste angeben.

    - Ein Zeichenfolgenliteral in Anführungszeichen eingeschlossen ist, und es wird angezeigt, genau, wie Sie es eingeben. **"Hello, World"** ist eine Literalzeichenfolge.

        ![Legen Sie die Text-Eigenschaft auf ein Zeichenfolgenliteral](./media/add-configure-controls/literal-string.png)

    - Ein Ausdruck keine enthält eine Funktion und basiert häufig auf eine Eigenschaft eines anderen Steuerelements. **Screen1.Height** ist ein Ausdruck, der die Höhe des zeigt **Screen1**.

        ![Text-Eigenschaft auf einen Ausdruck festgelegt.](./media/add-configure-controls/expression.png)

    - Eine Formel enthält eine oder mehrere Funktionen. Die **jetzt** Funktion gibt das aktuelle Datum und die Uhrzeit zurück, in der lokalen Zeitzone und die **Text** Funktion die Werte wie z. B. Datumsangaben, Uhrzeiten und Währungen formatiert.

        ![Text-Eigenschaft auf eine Formel festgelegt.](./media/add-configure-controls/formula.png)

        Formeln sind in der Regel wesentlich komplexer als in diesem Beispiel, sodass sie Daten aktualisieren, Sortieren Sie sie, Filtern und andere Vorgänge ausführen. Weitere Informationen finden Sie unter den [Formelreferenz](formula-reference.md).

## <a name="next-steps"></a>Nächste Schritte

- Finden Sie schrittweise Anleitungen zum Konfigurieren von allgemeinen Steuerelementen wie z. B. [Bildschirme](add-screen-context-variables.md), [listet](add-list-box-drop-down-list-radio-button.md), [Galerien](add-gallery.md), [Forms](add-form.md), und [Diagramme](use-line-pie-bar-chart.md).
- Finden Sie Referenzinformationen zu allen Typen von Steuerelementen in der [steuern Verweis](reference-properties.md).

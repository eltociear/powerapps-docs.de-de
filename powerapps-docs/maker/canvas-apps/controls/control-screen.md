---
title: 'Bildschirm-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Bildschirm-Steuerelement
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/14/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dceb9eee8eb5a0ed11a4b44fb2df6d63ba5e9cae
ms.sourcegitcommit: 5899d37e38ed7111d5a9d9f3561449782702a5e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71038255"
ms.PowerAppsDecimalTransform: true
---
# <a name="screen-control-in-powerapps"></a>Bildschirm-Steuerelement in PowerApps

Ein Benutzeroberflächenelement, das in einer App ein oder mehrere Steuerelemente enthält

## <a name="description"></a>Beschreibung

Die meisten Apps verfügen über mehrere **Bildschirm**-Steuerelemente, die **[Bezeichnung](control-text-box.md)** -Steuerelemente, **[Schaltflächen-](control-button.md)** und andere Steuerelemente enthalten und Daten anzeigen sowie die Navigation unterstützen. Informationen dazu, wie Sie einen Bildschirm hinzufügen, Bildschirme neu anordnen und die Navigation konfigurieren, finden [Sie unter Hinzufügen eines Bildschirms](../add-screen-context-variables.md).

## <a name="key-properties"></a>Haupteigenschaften

**[BackgroundImage](properties-visual.md)** : der Name einer Bilddatei, die im Hintergrund eines Bildschirms angezeigt wird

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**Height** : die Höhe des Bildschirms. Wenn die APP reaktionsfähig ist (die[**Skalierung**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) ist **deaktiviert) und**das Gerät, auf dem die app ausgeführt wird, kürzer als diese Eigenschaft ist, kann der Bildschirm vertikal scrollen.

**[ImagePosition](properties-visual.md)** : Die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Bilds auf einem Bildschirm oder in einem Steuerelement, wenn die Größe nicht mit der Bildgröße identisch ist.

**Name** : der Name des Bildschirms.

**OnHidden**: Das Verhalten einer App, wenn der Benutzer zu einer anderen Bildschirmansicht wechselt.

**OnVisible**: Das Verhalten einer App, wenn der Benutzer zu einem Bildschirm navigiert.  Verwenden Sie diese Eigenschaft zum Einrichten von Variablen und zum vorab Laden von Daten, die vom Bildschirm verwendet werden.  Verwenden Sie die [**app. OnStart**](../functions/object-app.md#onstart-property) -Eigenschaft für das einmalige einrichten, wenn die APP gestartet wird.

**Orientation** : die Ausrichtung des Bildschirms. Wenn seine **Breite** größer als seine **Höhe**ist, ist die Ausrichtung **Layout. horizontal**; Andernfalls wird " **Layout. Vertical**" verwendet.

**Size** : eine positive ganze Zahl, die die Größe des Bildschirms klassifiziert. Die Klassifizierung wird bestimmt, indem die **Width** -Eigenschaft des Bildschirms mit den Werten in der [**app. sizebreakpoints**](../functions/signals.md) -Eigenschaft verglichen wird. Der **ScreenSize** -Typ besteht aus vier Werten ("**Small**", " **Medium**", " **Large**" und " **extralarge**"), die den ganzen Zahlen 1 bis 4 entsprechen.

**Width** : die Breite des Bildschirms. Wenn die APP reaktionsfähig ist (die[**Skalierung**](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) ist **deaktiviert) und**das Gerät, auf dem die app ausgeführt wird, schmaler ist als diese Eigenschaft, kann der Bildschirm horizontal scrollen.

## <a name="related-functions"></a>Verwandte Funktionen

[**Distinct**( *DataSource*; *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Beispiel

1. Fügen Sie ein **[Optionsfeld](control-radio.md)** -Steuerelement hinzu, nennen Sie es **ScreenFills**, und legen Sie seine **[Items](properties-core.md)** -Eigenschaft auf folgenden Wert fest:

    `["Red"; "Green"]`

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?

1. Nennen Sie die das **Bildschirm**-Standardsteuerelement **Source**, fügen Sie ein weiteres **Bildschirm**-Steuerelement hinzu, und nennen Sie es **Target**.

1. Fügen Sie in **Source**ein **[Shape](control-shapes-icons.md)** -Steuerelement hinzu (z. b. einen Pfeil), und legen Sie dessen **[onselect](properties-core.md)** -Eigenschaft auf diese Formel fest:

    `Navigate(Target; ScreenTransition.Fade)`

    Benötigen Sie weitere Informationen zur **[Navigate](../functions/function-navigate.md)** -Funktion oder [anderen Funktionen](../formula-reference.md)?

1. Fügen Sie in **Target** ein **[Shape](control-shapes-icons.md)** -Steuerelement hinzu (z.B. einen Pfeil), und legen Sie seine **[OnSelect](properties-core.md)** -Eigenschaft auf diese Formel fest:

    `Navigate(Source; ScreenTransition.Fade)`

1. Legen Sie die **[Fill](properties-color-border.md)** -Eigenschaft von **Target** auf diese Formel fest:

    `If("Red" in ScreenFills.Selected.Value; RGBA(255; 0; 0; 1); RGBA(54; 176; 75; 1))`

1. Wählen Sie den **Quell** Bildschirm aus, und wählen Sie dann bei gedrückter Alt-Taste eine **[der beiden](control-radio.md)** Optionen im Optionsfeld aus, und wählen Sie dann das **[Shape](control-shapes-icons.md)** -Steuerelement aus.

    Das **Ziel** wird in der von Ihnen ausgewählten Farbe angezeigt.

1. Wählen Sie unter **Ziel**das **[Shape](control-shapes-icons.md)** -Steuerelement aus, das zur **Quelle**zurückzukehren ist.

1. optionale Wählen Sie im options **[Feld die andere](control-radio.md)** Option aus, und wählen Sie dann das **[Shape](control-shapes-icons.md)** -Steuerelement aus, um zu bestätigen, dass das **Ziel** in der anderen Farbe angezeigt wird

1. optionale Ordnen Sie die Bildschirme neu an, indem Sie in der linken Navigationsleiste auf das **Ziel** zeigen, die Auslassungs Punkte auswählen und nach **oben**klicken.

    Das **Ziel** wird zuerst angezeigt, wenn der Benutzer die APP öffnet.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="color-contrast"></a>Farbkontrast

Wenn die **Anzeige** als Hintergrund für Text gilt, muss zwischen den folgenden Eigenschaften ein angemessener Farbkontrast bestehen:

- **[Fill](properties-color-border.md)** und Text
- (Ggf.) **[BackgroundImage](properties-visual.md)** und Text

Wenn beispielsweise eine **Anzeige** eine **[Bezeichnung](control-text-box.md)** enthält und die Füllung der Bezeichnung durchsichtig ist, wird diese **[Füllung](properties-color-border.md)** als Hintergrundfarbe für die Bezeichnung verwendet.

Sie sollten nicht nur den Text überprüfen, sondern auch den Farbkontrast mit grundlegenden graphischen Objekten wie Bildern mit Sternen in einem **[Bewertungs](control-rating.md)** -Steuerelement.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe

- Jeder **Ansicht** muss ein eindeutiger Name zugewiesen sein. Der Anzeigename kann auf dieselbe Weise wie andere Steuerelemente angezeigt und bearbeitet werden, also entweder in der Strukturansicht des Bereichs „Steuerelemente“ oder im Header im Bereich „Eigenschaften“.

    > [!NOTE]
  > Wenn eine neue **Anzeige** geladen wird, nennt die Sprachausgabe deren Namen.

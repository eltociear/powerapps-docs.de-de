---
title: 'Bildschirm-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Bildschirm-Steuerelement
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6fedff6d6ffc34fe390ec6978672d699480a7cb9
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61548729"
ms.PowerAppsDecimalTransform: true
---
# <a name="screen-control-in-powerapps"></a>Bildschirm-Steuerelement in PowerApps

Ein Benutzeroberflächenelement, das in einer App ein oder mehrere Steuerelemente enthält

## <a name="description"></a>Beschreibung

Die meisten Apps verfügen über mehrere **Bildschirm**-Steuerelemente, die **[Bezeichnung](control-text-box.md)**-Steuerelemente, **[Schaltflächen-](control-button.md)** und andere Steuerelemente enthalten und Daten anzeigen sowie die Navigation unterstützen. Informationen dazu, wie Sie einen Bildschirm hinzufügen, Bildschirme neu anordnen und Konfigurieren der Navigation finden Sie in [fügen Sie einen Bildschirm](../add-screen-context-variables.md).

## <a name="key-properties"></a>Haupteigenschaften

**[BackgroundImage](properties-visual.md)** : der Name einer Bilddatei, die im Hintergrund eines Bildschirms angezeigt wird

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**Höhe** – die Höhe des Bildschirms. Wenn die app reaktionsfähig ist ([**an anpassen** ](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) ist **aus**) und das Gerät, auf denen die app ausgeführt wird, ist kürzer als diese Eigenschaft, vertikal scrollen können.

**[ImagePosition](properties-visual.md)**: Die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Bilds auf einem Bildschirm oder in einem Steuerelement, wenn die Größe nicht mit der Bildgröße identisch ist.

**Namen** -der Name des Bildschirms.

**OnHidden**: Das Verhalten einer App, wenn der Benutzer zu einer anderen Bildschirmansicht wechselt.

**OnStart**: Das Verhalten einer App, wenn sie vom Benutzer geöffnet wird.

- Die Formel, auf die diese Eigenschaft festgelegt ist, wird vor dem Anzeigen des ersten Bildschirms der App ausgeführt. Rufen Sie die [**Navigate**](../functions/function-navigate.md)-Funktion zum Ändern des Bildschirms auf, der beim Start der App zuerst angezeigt wird.
- Sie können mit der [**UpdateContext**](../functions/function-updatecontext.md)-Funktion keine [Kontextvariablen](../working-with-variables.md) festlegen, da noch kein Bildschirm angezeigt wurde. Sie können Kontextvariablen allerdings an die **Navigate**-Funktion übergeben und eine [Sammlung](../working-with-variables.md) mithilfe der [**Collect**](../functions/function-clear-collect-clearcollect.md)-Funktion erstellen und auffüllen.
- Wenn Sie eine App aktualisieren, wird die Formel, auf die diese Eigenschaft festgelegt ist, beim Laden der App in PowerApps Studio ausgeführt. Um die Auswirkungen einer Änderung dieser Eigenschaft anzuzeigen, müssen Sie Ihre App speichern, schließen und neu laden.
- Die **OnStart**-Eigenschaft ist tatsächlich eine Eigenschaft der App und nicht des Bildschirms. Zur Vereinfachung der Bearbeitung wird sie als Eigenschaft auf dem ersten Bildschirm Ihrer App angezeigt und geändert. Wenn Sie den ersten Bildschirm entfernen oder Bildschirme neu anordnen, kann diese Eigenschaft schwer zu finden sein. In diesem Fall sollten Sie Ihre App speichern, schließen und neu laden, woraufhin die Eigenschaft wieder als Eigenschaft auf dem ersten Bildschirm angezeigt wird.

**OnVisible**: Das Verhalten einer App, wenn der Benutzer zu einem Bildschirm navigiert.

**Ausrichtung** -die Ausrichtung des Bildschirms. Wenn die **Breite** ist größer als die **Höhe**, der die Ausrichtung werden **Layout.Horizontal**ist, andernfalls wird **Layout.Vertical** .

**Größe** -eine positive ganze Zahl, die die Größe des Bildschirms klassifiziert. Die Klassifizierung wird bestimmt durch Vergleich des Bildschirms **Breite** Eigenschaft, um die Werte in der [ **App.SizeBreakpoints** ](../functions/signals.md) Eigenschaft. Die **ScreenSize** Typ besteht aus vier Werten (**kleine**, **Mittel**, **groß**, und **ExtraLarge** ), die die ganzen Zahlen 1 bis 4 entsprechen.

**Breite** -die Breite des Bildschirms. Wenn die app reaktionsfähig ist ([**an anpassen** ](../set-aspect-ratio-portrait-landscape.md#change-screen-size-and-orientation) ist **aus**) und das Gerät, auf denen die app ausgeführt wird, ist enger gefasst als diese Eigenschaft, horizontal scrollen können.

## <a name="related-functions"></a>Verwandte Funktionen

[**Distinct**( *DataSource*; *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Beispiel

1. Fügen Sie ein **[Optionsfeld](control-radio.md)**-Steuerelement hinzu, nennen Sie es **ScreenFills**, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf folgenden Wert fest:

    `["Red"; "Green"]`

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?

1. Nennen Sie die das **Bildschirm**-Standardsteuerelement **Source**, fügen Sie ein weiteres **Bildschirm**-Steuerelement hinzu, und nennen Sie es **Target**.

1. In **Quelle**, Hinzufügen einer **[Form](control-shapes-icons.md)** steuern (z.B. einen Pfeil), und legen dessen **[OnSelect](properties-core.md)** Eigenschaft Diese Formel:

    `Navigate(Target; ScreenTransition.Fade)`

    Benötigen Sie weitere Informationen zur **[Navigate](../functions/function-navigate.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?

1. Fügen Sie in **Target** ein **[Shape](control-shapes-icons.md)**-Steuerelement hinzu (z.B. einen Pfeil), und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:

    `Navigate(Source; ScreenTransition.Fade)`

1. Legen Sie die **[Fill](properties-color-border.md)**-Eigenschaft von **Target** auf diese Formel fest:

    `If("Red" in ScreenFills.Selected.Value; RGBA(255; 0; 0; 1); RGBA(54; 176; 75; 1))`

1. Wählen Sie die **Quelle** und klicken Sie dann, während Sie die Alt-Taste gedrückt halten, wählen Sie eine der Optionen im der **[Radio](control-radio.md)** steuern, und wählen Sie dann die **[Form](control-shapes-icons.md)** Steuerelement.

    **Ziel** angezeigt, die in der Farbe, die Sie ausgewählt wird.

1. In **Ziel**, wählen die **[Form](control-shapes-icons.md)** Rückgabe an **Quelle**.

1. (optional) Wählen Sie die andere Option in der **[Radio](control-radio.md)** steuern, und wählen Sie dann die **[Form](control-shapes-icons.md)** Steuerelement, um zu bestätigen, dass **Ziel**  in einer anderen Farbe angezeigt wird.

1. (optional) Die Bildschirme neu anordnen, indem Sie mit dem Mauszeiger auf **Ziel** in der linken Navigationsleiste klicken Sie auf die Auslassungspunkte, die angezeigt wird, und wählen Sie dann **nach oben verschieben**.

    **Ziel** zuerst angezeigt werden, wenn der Benutzer die app wird geöffnet.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="color-contrast"></a>Farbkontrast

Wenn die **Anzeige** als Hintergrund für Text gilt, muss zwischen den folgenden Eigenschaften ein angemessener Farbkontrast bestehen:

- **[Fill](properties-color-border.md)** und Text
- (Ggf.) **[BackgroundImage](properties-visual.md)** und Text

Wenn beispielsweise eine **Anzeige** eine **[Bezeichnung](control-text-box.md)** enthält und die Füllung der Bezeichnung durchsichtig ist, wird diese **[Füllung](properties-color-border.md)** als Hintergrundfarbe für die Bezeichnung verwendet.

Sie sollten nicht nur den Text überprüfen, sondern auch den Farbkontrast mit grundlegenden graphischen Objekten wie Bildern mit Sternen in einem **[Bewertungs](control-rating.md)**-Steuerelement.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe

- Jeder **Ansicht** muss ein eindeutiger Name zugewiesen sein. Der Anzeigename kann auf dieselbe Weise wie andere Steuerelemente angezeigt und bearbeitet werden, also entweder in der Strukturansicht des Bereichs „Steuerelemente“ oder im Header im Bereich „Eigenschaften“.

    > [!NOTE]
  > Wenn eine neue **Anzeige** geladen wird, nennt die Sprachausgabe deren Namen.

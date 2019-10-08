---
title: 'Shape-Steuerelemente und Symbole für Steuerelemente: Referenz | Microsoft-Dokumentation'
description: Informationen einschließlich Eigenschaften und Beispielen für Shape-Steuerelemente und Symbole für Steuerelemente
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 46f1974b5ff32cf21d1e9f24c15362c24b44fbe3
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986335"
ms.PowerAppsDecimalTransform: true
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Shape-Steuerelemente und Symbole für Steuerelemente in PowerApps
Grafiken, deren Eigenschaften wie Aussehen und Verhalten Sie konfigurieren können

## <a name="description"></a>Beschreibung
Diese Steuerelemente umfassen Pfeile, geometrische Formen, Aktionssymbole und Symbole, deren Eigenschaften wie Füllung, Größe und Position sich konfigurieren lassen. Sie können auch die **[onselect](properties-core.md)** -Eigenschaft so konfigurieren, dass die APP reagiert, wenn der Benutzer das Steuerelement auswählt.

## <a name="key-properties-icons-and-shapes"></a>Schlüsseleigenschaften (Symbole und Formen)
**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Onselect](properties-core.md)** – gibt an, wie die APP reagiert, wenn der Benutzer ein Steuerelement auswählt.

## <a name="key-properties-icons-only"></a>Schlüsseleigenschaften (nur Symbole)

**Icon** : der Typ des anzuzeigenden Symbols (z. b. **ArrowDown** oder **ShoppingCart**). 

**Rotation** : die Anzahl der Grad, um die das Symbol gedreht wird. 

**Color** : die Farbe des Symbols nach Name oder RGBA-Werten.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)** : Bezeichnung für Sprachausgaben

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[FocusedBorderColor](properties-color-border.md)** : die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)** : die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Pressedbordercolor](properties-color-border.md)** – die Farbe des Rahmens eines Steuer Elements, wenn der Benutzer dieses Steuerelement auswählt.

**[Pressedfill](properties-color-border.md)** – die Hintergrundfarbe eines Steuer Elements, wenn der Benutzer dieses Steuerelement auswählt.

**[TabIndex](properties-accessibility.md)** : Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen

[**Navigate**( *ScreenName*; *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>Beispiel

1. Nennen Sie das **[Bildschirm](control-screen.md)** -Standardsteuerelement **Target**, fügen Sie ein **[Label](control-text-box.md)** -Steuerelement (Bezeichnung) hinzu, und legen Sie anschließend die  **[Text](properties-core.md)** -Eigenschaft so fest, dass **Target** angezeigt wird.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

1. Fügen Sie ein **[Bildschirm](control-screen.md)** -Steuerelement hinzu, und nennen Sie es **Source**.

1. Fügen Sie in **Source** ein **Shape**-Steuerelement hinzu, und legen Sie seine **[OnSelect](properties-core.md)** -Eigenschaft auf diese Formel fest:

  `Navigate(Target; ScreenTransition.Fade)`
  
1. Drücken Sie F5, und wählen Sie dann das **Shape** -Steuerelement aus.

    Der Bildschirm **Target** wird angezeigt.

1. (optional) Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren, fügen Sie ein **Shape**-Steuerelement zu **Target** hinzu, und legen Sie die **[OnSelect](properties-core.md)** -Eigenschaft des **Shape**-Steuerelements auf diese Formel fest:

  `Navigate(Source; ScreenTransition.Fade)`

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="color-contrast"></a>Farbkontrast

Folgendes gilt nur für Grafiken, die als Schaltflächen oder nicht allein zu Darstellungszwecken verwendet werden.

Für Symbole:
- **[Color](properties-color-border.md)** und **[Fill](properties-color-border.md)**
- Es gelten die [Standardanforderungen für Farbkontraste](../accessible-apps-color.md), wenn das Steuerelement als Schaltfläche verwendet wird.

Für Formen mit Rahmen:
- **[BorderColor](properties-color-border.md)** und die Farbe außerhalb des Steuerelements
- **[FocusedBorderColor](properties-color-border.md)** und die Farbe außerhalb des Steuerelements, wenn dieses als Schaltfläche verwendet wird

Für Formen ohne Rahmen:
- **[Fill](properties-color-border.md)** und die Farbe außerhalb des Steuerelements
- **[PressedFill](properties-color-border.md)** und die Farbe außerhalb des Steuerelements, wenn dieses als Schaltfläche verwendet wird
- **[HoverFill](properties-color-border.md)** und die Farbe außerhalb des Steuerelements, wenn dieses als Schaltfläche verwendet wird

### <a name="screen-reader-support"></a>Sprachausgabeunterstützung
- **[Accessiblelabel](properties-accessibility.md)** muss auf eine nicht leere Zeichenfolge festgelegt werden, wenn die Grafik als Schaltfläche verwendet wird, oder andernfalls nicht nur für die Dekoration.

- **[Accessiblelabel](properties-accessibility.md)** muss leer sein oder die leere Zeichenfolge **""** lauten, wenn die Grafik redundante Informationen bereitstellt oder ausschließlich für die Dekoration vorgesehen ist. Dieser Wert bewirkt, dass Bildschirm Sprachausgaben die Grafik ignorieren.

Beispielsweise können Sie die **[accessiblelabel](properties-accessibility.md)** -Eigenschaft eines **Einstellungs** Symbols auf **Settings**festlegen. Dieses Symbol wird nicht als Schaltfläche verwendet. Sie befindet sich neben einer **[Bezeichnung](control-text-box.md)** , die ebenfalls **Einstellungen**besagt. Die Sprachausgabe liest das Symbol und die Bezeichnung als **Einstellungen**, was unnötig ausführlich ist. In diesem Fall benötigt das Symbol kein **[accessiblelabel](properties-accessibility.md)** .

> [!IMPORTANT]
> Sprachausgaben lesen ein Symbol oder eine Form als **Schaltfläche** , wenn das **[accessiblelabel](properties-accessibility.md)** -Element auf eine leere Zeichenfolge festgelegt ist und dessen **[TabIndex](properties-accessibility.md)** auf 0 (null) oder größer festgelegt ist. Solche Symbole oder Formen werden als Schaltflächen gerendert. 

### <a name="keyboard-support"></a>Tastaturunterstützung
- **[TabIndex](properties-accessibility.md)** muss 0 (null) oder größer sein, wenn die Grafik als Schaltfläche verwendet wird. Wenn Sie diesen Wert für ein Symbol oder eine Form festlegen, können Tastatur Benutzer dorthin navigieren.

- Fokus Indikatoren müssen klar sichtbar sein, wenn die Grafik als Schaltfläche verwendet wird. Verwenden Sie **[focusedbordercolor](properties-color-border.md)** und **[focusedborderdicke](properties-color-border.md)** , um dieses Ergebnis zu erzielen.

    > [!NOTE]
    > Wenn **[TabIndex](properties-accessibility.md)** gleich 0 (null) oder größer ist, werden das Symbol oder die Form als Schaltfläche gerendert. Seine Darstellung ändert sich nicht, aber Bildschirm Sprachausgaben identifizieren das Bild ordnungsgemäß als Schaltfläche. Ist **[TabIndex](properties-accessibility.md)** kleiner als 0 (null), wird das Symbol oder die Form als Bild erkannt.

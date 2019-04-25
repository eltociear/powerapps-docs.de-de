---
title: 'Shape-Steuerelemente und Symbole für Steuerelemente: Referenz | Microsoft-Dokumentation'
description: Informationen einschließlich Eigenschaften und Beispielen für Shape-Steuerelemente und Symbole für Steuerelemente
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 88e0a74d2c25d1d2f5f571f4d1850417d1aab9ca
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63318435"
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Shape-Steuerelemente und Symbole für Steuerelemente in PowerApps
Grafiken, deren Eigenschaften wie Aussehen und Verhalten Sie konfigurieren können

## <a name="description"></a>Beschreibung
Diese Steuerelemente umfassen Pfeile, geometrische Formen, Aktionssymbole und Symbole, deren Eigenschaften wie Füllung, Größe und Position sich konfigurieren lassen. Sie können auch konfigurieren, deren **[OnSelect](properties-core.md)** Eigenschaft, damit die app reagiert, wenn der Benutzer das Steuerelement auswählt.

## <a name="key-properties-icons-and-shapes"></a>Schlüsseleigenschaften (Symbole und Formen)
**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[OnSelect](properties-core.md)**  – wie die app reagiert, wenn der Benutzer ein Steuerelement auswählt.

## <a name="key-properties-icons-only"></a>Schlüsseleigenschaften (nur für Symbole)

**Symbol "** -den Typ des Symbols angezeigt (z. B. **ArrowDown** oder **ShoppingCart**). 

**Drehung** -Anzahl Grad zu drehen Sie das Symbol. 

**Farbe** – die Farbe des Symbols, das anhand des Namens oder RGBA-Werte.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[FocusedBorderColor](properties-color-border.md)**: die Rahmenfarbe eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[FocusedBorderThickness](properties-color-border.md)**: die Rahmendicke eines Steuerelements, wenn das Steuerelement der Fokus ist.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[PressedBorderColor](properties-color-border.md)**  – die Farbe des Rahmens eines Steuerelements, wenn der Benutzer dieses Steuerelement auswählt.

**[PressedFill](properties-color-border.md)**  – die Hintergrundfarbe eines Steuerelements, wenn der Benutzer dieses Steuerelement auswählt.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen

[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>Beispiel

1. Nennen Sie das **[Bildschirm](control-screen.md)**-Standardsteuerelement **Target**, fügen Sie ein **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie anschließend die  **[Text](properties-core.md)**-Eigenschaft so fest, dass **Target** angezeigt wird.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

1. Fügen Sie ein **[Bildschirm](control-screen.md)**-Steuerelement hinzu, und nennen Sie es **Source**.

1. Fügen Sie in **Source** ein **Shape**-Steuerelement hinzu, und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:

  `Navigate(Target, ScreenTransition.Fade)`
  
1. Drücken Sie F5, und wählen Sie dann die **Form** Steuerelement.

    Der Bildschirm **Target** wird angezeigt.

1. (optional) Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren, fügen Sie ein **Shape**-Steuerelement zu **Target** hinzu, und legen Sie die **[OnSelect](properties-core.md)**-Eigenschaft des **Shape**-Steuerelements auf diese Formel fest:

  `Navigate(Source, ScreenTransition.Fade)`

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
- **[AccessibleLabel](properties-accessibility.md)**  muss auf eine nicht leere Zeichenfolge festgelegt werden, wenn die Grafik als Schaltfläche verwendet wird, oder befindet sich nicht allein zu Darstellungszwecken andernfalls.

- **[AccessibleLabel](properties-accessibility.md)**  muss leer sein oder die leere Zeichenfolge **""** , wenn die Grafik redundanten Informationen enthält oder ausschließlich Dekoration ist. Dieser Wert führt dazu, dass Sprachausgaben die Grafik ignoriert werden sollen.

Legen Sie z. B. möglicherweise die **[AccessibleLabel](properties-accessibility.md)** Eigenschaft eine **Einstellungen** Symbol **Einstellungen**. Dieses Symbol wird nicht als Schaltfläche verwendet. Es befindet sich neben einer **[Bezeichnung](control-text-box.md)** , die ebenfalls den Namen **Einstellungen**. Sprachausgaben lesen sowohl Symbol-als auch die Bezeichnung als **Einstellungen**, d.h. unnötig ausführlich. In diesem Fall auf das Symbol muss kein  **[AccessibleLabel](properties-accessibility.md)**.

> [!IMPORTANT]
> Sprachausgaben lesen erst gelesen wird, ein Symbol oder eine Form als **Schaltfläche** wenn seine **[AccessibleLabel](properties-accessibility.md)** auf eine leere Zeichenfolge festgelegt ist und die zugehörige **[TabIndex ](properties-accessibility.md)** auf 0 (null) oder höher festgelegt ist. Diese Symbole oder Formen werden als Schaltflächen gerendert. 

### <a name="keyboard-support"></a>Tastaturunterstützung
- **[TabIndex](properties-accessibility.md)**  muss 0 (null) oder höher, wenn die Grafik als Schaltfläche verwendet wird. Wenn Sie diesen Wert für ein Symbol oder eine Form festlegen, können Benutzer über die Tastatur dorthin navigieren.

- Fokusindikatoren müssen übersichtlich angezeigt werden, wenn die Grafik als Schaltfläche verwendet, wird sein. Verwendung **[FocusedBorderColor](properties-color-border.md)** und **[FocusedBorderThickness](properties-color-border.md)** um dieses Ergebnis zu erzielen.

    > [!NOTE]
    > Wenn **[TabIndex](properties-accessibility.md)** gleich 0 (null) oder größer ist, werden das Symbol oder die Form als Schaltfläche gerendert. Seine Darstellung nicht geändert, aber die Sprachausgabe erkennt das Bild als Schaltfläche richtig. Ist **[TabIndex](properties-accessibility.md)** kleiner als 0 (null), wird das Symbol oder die Form als Bild erkannt.

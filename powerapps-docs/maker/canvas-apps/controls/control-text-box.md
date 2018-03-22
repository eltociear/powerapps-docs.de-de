---
title: 'Label-Steuerelement (Bezeichnung): Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Label-Steuerelement
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: f0547963060d31f86b32cc2aaff38b116d35036b
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="label-control-in-powerapps"></a>Label-Steuerelement (Bezeichnung) in PowerApps
Ein Feld, das Daten wie Text, Zahlen, Datumsangaben oder Währung anzeigt.

## <a name="description"></a>Beschreibung
Eine Bezeichnung zeigt Daten an, die Sie als Textzeichenfolgenliteral angeben, das genauso angezeigt wird, wie Sie es eingeben, oder als Formel, die zu einer Textzeichenfolge ausgewertet wird. Bezeichnungen werden häufig außerhalb anderer Steuerelemente (z.B. als Banner, das einen Bildschirm identifiziert), als Bezeichnung für die Identifizierung eines anderen Steuerelements (z.B. ein Bewertungs- oder Audiosteuerelement) oder in einer Galerie angezeigt, um einen bestimmten Typ von Information zu einem Element anzuzeigen.

## <a name="key-properties"></a>Haupteigenschaften
**[AutoHeight](properties-core.md)**: Durch Festlegen auf TRUE kann die Größe der Bezeichnung automatisch erhöht werden, um den gesamten konfigurierten Text anzuzeigen. Durch Festlegen auf FALSE wird der Text auf die zugewiesene Größe abgeschnitten.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[Text](properties-core.md)** – Text, der in einem Steuerelement angezeigt wird oder von einem Benutzer in ein Steuerelement eingegeben wird.

**[DelayOutput](properties-core.md)**: Durch Festlegen auf TRUE wird eine Aktion während der Texteingabe verzögert.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**AutoHeight**: Gibt an, ob die **[Height](properties-size-location.md)**-Eigenschaft einer Bezeichnung automatisch erhöht wird, wenn ihre **[Text](properties-core.md)**-Eigenschaft mehr Zeichen enthält, als das Steuerelement gleichzeitig anzeigen kann.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[LineHeight](properties-text.md)**: Der Abstand zwischen Elementen, z.B. Textzeilen oder Elementen in einer Liste.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**Overflow**: Gibt an, ob eine Bildlaufleiste in einer Bezeichnung angezeigt wird, wenn die **Wrap**-Eigenschaft auf **TRUE** festgelegt ist und der Wert der **[Text](properties-core.md)**-Eigenschaft des Steuerelements mehr Zeichen enthält, als das Steuerelement gleichzeitig anzeigen kann.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[VerticalAlign](properties-text.md)** – Die Position des Texts in einem Steuerelement in Relation zur vertikalen Mitte des Steuerelements.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**Wrap**: Gibt an, ob Text, der zu lang für eine Bezeichnung ist, in die nächste Zeile umbrochen wird.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Text**( *Zahl*, "*CodesFormatieren*" )](../functions/function-text.md)

## <a name="examples"></a>Beispiele
### <a name="show-a-literal-string"></a>Anzeigen eines Zeichenfolgenliterals
* Fügen Sie eine Bezeichnung hinzu, und legen Sie deren **[Text](properties-core.md)**-Eigenschaft auf **"Hello, world"** fest (einschließlich der doppelten Anführungszeichen).
  
    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

### <a name="show-the-result-of-a-formula"></a>Anzeigen des Ergebnisses einer Formel
* Fügen Sie eine Bezeichnung hinzu, und legen Sie deren **[Text](properties-core.md)**-Eigenschaft auf eine Formel wie diese fest:<br>
  **Today()**
  
    > [!NOTE]
> Verwenden Sie beim Angeben einer Formel nur Anführungszeichen, wenn ein Argument der Formel ein Zeichenfolgenliteral ist. Umschließen Sie in diesem Fall das Argument und nicht die Formel mit doppelten Anführungszeichen.
  
    Benötigen Sie weitere Informationen zur **[Today](../functions/function-now-today-istoday.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?

### <a name="show-data-in-a-gallery"></a>Anzeigen von Daten in einem Katalog
In diesem Verfahren erstellen Sie eine Sammlung mit dem Namen **CityPopulations**, die Daten über die Bevölkerung verschiedener Städte in Europa enthält. Als Nächstes zeigen Sie diese Daten in einem Katalog an, der drei Bezeichnungen enthält, und geben den Datentyp an, der in jeder Bezeichnung angezeigt wird.

1. Fügen Sie eine Schaltfläche hinzu, und legen Sie ihre Eigenschaft **[OnSelect](properties-core.md)** auf diese Formel fest:<br>
   **ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
2. Drücken Sie F5, wählen Sie die Schaltfläche aus, und drücken Sie dann die ESC-TASTE.
3. Fügen Sie einen Textkatalog hinzu, und legen Sie dessen **[Items](properties-core.md)**-Eigenschaft auf **CityPopulations** fest.
   
    Wenn der Katalog ausgewählt ist, werden im rechten Bereich Optionen für diesen Katalog angezeigt.
4. Legen Sie im Bereich **Gallery1** die obere Liste auf **Population**, die mittlere Liste auf **City** und die untere Liste auf **Country** fest.


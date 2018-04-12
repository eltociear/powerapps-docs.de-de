---
title: 'Radio-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Radio-Steuerelement
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
ms.openlocfilehash: 9cf051ba94e9d43b4c263d627c25affa66e6b843
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="radio-control-in-powerapps"></a>Radio-Steuerelement in PowerApps
Eine Liste, die alle Optionen anzeigt, aber der Benutzer kann nur jeweils eine auswählen.

## <a name="description"></a>Beschreibung
Ein **Radio**-Steuerelement, mit denen Benutzer jahrzehntelange Erfahrung haben, wird am besten mit nur wenigen Optionen verwendet, die sich gegenseitig ausschließen.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)** – Der Anfangswert eines Steuerelements, bevor es vom Benutzer geändert wird.

**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

[!INCLUDE [long-items](../../../includes/long-items.md)]

**[Value](properties-core.md)**: Gibt den Wert eines Eingabesteuerelements an.

## <a name="all-properties"></a>Alle Eigenschaften
**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[FocusedBorderThickness](properties-color-border.md)** – Die Rahmenstärke eines Steuerelements, wenn es den Tastaturfokus besitzt.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[LineHeight](properties-text.md)**: Der Abstand zwischen Elementen, z.B. Textzeilen oder Elementen in einer Liste.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**RadioBackgroundFill**: Die Farbe des Hintergrunds der Kreise in einem Steuerelement der Radioschaltfläche.

**RadioBorderColor**: Die Farbe des Kreises für jede Option in einem Steuerelement der Radioschaltfläche.

**RadioSelectionFill**: Die Farbe, die innerhalb des Kreises, der ausgewählten Option in einem Steuerelement der Radioschaltfläche angezeigt wird.

**RadioSize**: Der Durchmesser der Kreise in einem Steuerelement der Radioschaltfläche.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)** – Passt die Aktivierreihenfolge von Steuerelementen zur Laufzeit an, wenn sie auf einen Wert ungleich 0 festgelegt wird.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>Beispiel
1. Fügen Sie das **Radio**-Steuerelement hinzu, nennen Sie es **Pricing**, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf die folgende Formel fest:
   <br>**["Standard", "Premium"]**
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein Steuerelement **[Label](control-text-box.md)** (Bezeichnung) hinzu, verschieben Sie es unter das **Radio**-Steuerelement (Optionsfeld) und legen Sie die Eigenschaft **[Text](properties-core.md)** des Steuerelements **[Label](control-text-box.md)** auf diese Formel fest:
   <br>**If("Premium" in Pricing.Selected.Value, "$200 pro Tag", "$150 pro Tag")**
   
    Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
3. Drücken Sie F5, und wählen Sie anschließend eine der beiden Optionen im Steuerelement **Radio**.
   
    Das Steuerelement **[Label](control-text-box.md)** (Bezeichnung) zeigt den entsprechenden Text Ihrer Wahl.
4. (optional) Wählen Sie im Steuerelement **Radio** die andere Option für die Bestätigung, dass der entsprechende Text angezeigt wird.
5. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.

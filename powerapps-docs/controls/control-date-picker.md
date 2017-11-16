---
title: 'Datumsauswahl-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, über das Datumsauswahl-Steuerelement"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: f2605680c7b6e8f7102fd3459230344863a93f55
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="date-picker-control-in-powerapps"></a>Datumsauswahl-Steuerelement in PowerApps
Ein Steuerelement, mit dem Benutzer durch Klicken oder Tippen ein Datum angeben können.

## <a name="description"></a>Beschreibung
Wenn Sie ein **Datumsauswahl**-Steuerelement anstatt eines **[Texteingabe](control-text-input.md)**-Steuerelements verwenden, geben Benutzer das Datum in jedem Fall im richtigen Format an.

## <a name="key-properties"></a>Haupteigenschaften
**DefaultDate** – Der Anfangswert eines Datum-Steuerelements, es sei denn, der Benutzer ändert ihn.

**SelectedDate** – Das Datum, das in einem Datum-Steuerelement ausgewählt ist.

**Format** – Das Textformat, in dem das Steuerelement das Datum zeigt und der Benutzer das Datum angibt. Sie können diese Eigenschaft auf **ShortDate** (Standard) oder **LongDate** festlegen, um Datumsangaben basierend auf der **Language**-Eigenschaft dieses Steuerelements zu formatieren. Sie können diese Eigenschaft auf einen Ausdruck festlegen, z. B. **TT.MM.JJJJ**, wenn Sie dasselbe Format ungeachtet der Sprache wünschen. Beispiel:

* Das Steuerelement zeigt **12/31/2017**, wenn der Benutzer auf den letzten Tag von 2017 klickt oder tippt. Die **Format**-Eigenschaft ist auf **ShortDate**, die **Language**-Eigenschaft auf **en-us** festgelegt.
* Das Steuerelement zeigt **dimanche 31 decembre 2017**, wenn der Benutzer auf den letzten Tag von 2017 klickt oder tippt. Die **Format**-Eigenschaft ist auf **LongDate**, die **Language**-Eigenschaft auf **fr-fr** festgelegt.

**Sprache** – Bestimmt die Sprache, die zum Formatieren von Datumsangaben, einschließlich der Namen von Monaten, verwendet wird. Wenn diese Eigenschaft nicht angegeben ist, wird die Sprache von der Geräteeinstellung des Benutzers bestimmt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[FocusedBorderThickness](properties-color-border.md)**: Die Rahmenstärke eines Steuerelements, wenn es den Tastaturfokus besitzt.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt („Edit“, Bearbeiten), ob nur Daten angezeigt werden („View“, Anzeigen) oder ob das Steuerelement deaktiviert ist („Disabled“, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**EndYear** – Das letzte Jahr, auf das Benutzer den Wert eines Steuerelements für die Datumsauswahl festlegen können.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)** – Der Abstand zwischen dem Text in einem Steuerelement und dem oberen Rand des Steuerelements.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**StartYear** – Das früheste Jahr, auf das Benutzer den Wert eines Steuerelements für die Datumsauswahl festlegen können.

**[TabIndex](properties-accessibility.md)** – Passt die Aktivierreihenfolge von Steuerelementen zur Laufzeit an, wenn sie auf einen Wert ungleich 0 festgelegt wird.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
**[Year](../functions/function-datetime-parts.md)**( *DateTimeValue* )

## <a name="example"></a>Beispiel
1. Fügen Sie ein **Datumsauswahl**-Steuerelement hinzu, und benennen Sie es **Deadline**.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie dessen **[Text](properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**DateDiff(Today(), Deadline.SelectedDate) & " days to go!"**
   
    Benötigen Sie weitere Informationen zur **[DateDiff](../functions/function-dateadd-datediff.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
3. Drücken Sie F5, legen Sie für **Deadline** ein Datum fest, und klicken oder tippen Sie dann auf **OK**.
   
    Im **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) wird angezeigt, wie viele Tage zwischen dem aktuellen und dem gewählten Datum verbleiben.
4. Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren.


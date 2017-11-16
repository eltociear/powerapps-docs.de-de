---
title: 'Dropdown-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen über das Dropdown-Steuerelement, einschließlich Eigenschaften und Beispielen"
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
ms.openlocfilehash: 30b36217b0871b85b3868cd305992d7e4f364557
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="drop-down-control-in-powerapps"></a>Dropdown-Steuerelement in PowerApps
Eine Liste, die nur das erste Element anzeigt, bis der Benutzer sie öffnet.

## <a name="description"></a>Beschreibung
Ein **Dropdown**-Steuerelement ist platzsparend und eignet sich besonders für umfangreiche Listen. Das Steuerelement beansprucht nur eine Zeile, bis der Benutzer den Abwärtspfeil auswählt, um weitere Optionen einzublenden.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)**: Der Anfangswert eines Steuerelements, bevor er vom Benutzer geändert wird.

**[Items](properties-core.md)** – Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

[!INCLUDE [long-items](../../includes/long-items.md)]

**Selected** – Das ausgewählte Element.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[FocusedBorderThickness](properties-color-border.md)** – Die Rahmenstärke eines Steuerelements, wenn es den Tastaturfokus besitzt.

**ChevronBackground** – Die Farbe im Hintergrund des Abwärtspfeils einer Dropdownliste.

**ChevronFill** – Die Farbe des Abwärtspfeils in einer Dropdownliste.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Reset](properties-core.md)**: Gibt an, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**[SelectionColor](properties-color-border.md)**: Die Textfarbe des ausgewählten Elements oder der Elemente in einer Liste oder die Farbe des Auswahltools in einem Stift-Steuerelement.

**[SelectionFill](properties-color-border.md)** – Die Hintergrundfarbe des ausgewählten Elements oder der Elemente in einer Liste oder eines ausgewählten Bereichs eines Stift-Steuerelements.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[TabIndex](properties-accessibility.md)**: Passt die Aktivierreihenfolge von Steuerelementen zur Laufzeit an, wenn sie auf einen Wert ungleich 0 festgelegt wird.

**[QuickInfo](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="example"></a>Beispiel
1. Fügen Sie ein **[Schaltflächen](control-button.md)**-Steuerelement hinzu, und konfigurieren Sie seine **[Text](properties-core.md)**-Eigenschaft für das Anzeigen von **Collect**.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Legen Sie die **[OnSelect](properties-core.md)**-Eigenschaft des **[Schaltflächen](control-button.md)**-Steuerelements auf die folgende Formel fest:
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    Benötigen Sie weitere Informationen zur **[ClearCollect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
3. Drücken Sie F5, klicken oder tippen Sie auf das **[Button](control-button.md)**-Steuerelement (Schaltfläche), und drücken Sie dann ESC.
4. Fügen Sie ein **Dropdown**-Steuerelement hinzu, weisen Sie ihm den Namen **Countries** hinzu, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**Distinct(CityPopulations, Country)**
5. Fügen Sie ein **Textkatalog**-Steuerelement in vertikaler/Hochformat-Ausrichtung ein, und legen Sie dessen **[Items](properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**Filter(CityPopulations, Countries.Selected.Value in Country)**
6. Geben Sie im ersten Element des **Textkatalog**-Steuerelements für die **[Text](properties-core.md)**-Eigenschaft im oberen **[Label](control-text-box.md)**-Steuerelement den Wert **ThisItem.City** an. Löschen Sie anschließend das untere **[Label](control-text-box.md)**-Steuerelement.
7. Geben Sie für die **[TemplateSize](control-gallery.md)**-Eigenschaft des **Textkatalog**-Steuerelements den Wert **80** an.
8. Drücken Sie F5 und klicken oder tippen Sie auf den Abwärtspfeil in der Liste **Countries**. Wählen Sie dann eine Option aus der Liste aus.
   
    Im **Textkatalog**-Steuerelement werden nur Städte angezeigt, die sich im ausgewählten Land befinden.


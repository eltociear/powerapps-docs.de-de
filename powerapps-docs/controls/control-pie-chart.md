---
title: 'Kreisdiagramm-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, zum Kreisdiagramm-Steuerelement"
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
ms.openlocfilehash: 1388eac45e5086f677cb83c8db9593fe01a9819f
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="pie-chart-control-in-powerapps"></a>Kreisdiagramm-Steuerelement in PowerApps
Ein Steuerelement, das einen Vergleich relativer Werte anzeigt

## <a name="description"></a>Beschreibung
Fügen Sie ein **Kreisdiagramm**-Steuerelement hinzu, wenn Sie relative Daten aus einer Tabelle anzeigen möchten, die in der äußersten linken Spalte Bezeichnungen und in der zweiten Spalte von links Werte enthält.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**ShowLabels**: gibt an, ob ein Kreisdiagramm einen Wert darstellt, der mit jedem seiner Segmente verknüpft ist.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**Explode**: gibt den Abstand zwischen den Segmenten in einem Kreisdiagramm an.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**ItemBorderColor**: gibt die Farbe des Rahmens um jedes Segment in einem Kreisdiagramm an.

**ItemBorderThickness**: gibt die Stärke des Rahmens um jedes Segment in einem Kreisdiagramm an.

**ItemColorSet**: gibt die Farbe der einzelnen Datenpunkte in einem Diagramm an.

**LabelPosition**: gibt die Position von Bezeichnungen in einem Kreisdiagramm relativ zu seinen Segmenten an.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein **[Button](control-button.md)**-Steuerelement (Schaltfläche) hinzu, und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **Collect(Revenue2015, {Product:"Europa", Revenue:27000}, {Product:"Ganymede", Revenue:26300}, {Product:"Callisto", Revenue:29200})**
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
2. Drücken F5, klicken oder tippen Sie auf das Steuerelement des Typs **[Schaltfläche](control-button.md)** , und drücken Sie anschließend die ESC-Taste, um in den Standardarbeitsbereich zurückzukehren.
3. Fügen Sie ein Steuerelements des Typs **Kreisdiagramm** hinzu, und legen Sie seine  **[Items](properties-core.md)**-Eigenschaft auf **Revenue2015** fest.
   
    Das **Kreisdiagramm**-Steuerelement zeigt die Umsatzdaten für jedes Produkt in Bezug auf die anderen Produkte.


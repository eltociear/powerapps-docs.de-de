---
title: 'Säulendiagramm-Steuerelement und Liniendiagramm-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Säulendiagramm-Steuerelement und das Liniendiagramm-Steuerelement
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
ms.openlocfilehash: 039b267394ef6be5e3038fa0b07149f69fee6a51
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="column-chart-and-line-chart-controls-in-powerapps"></a>Steuerelemente für Säulendiagramme und Liniendiagramme in PowerApps
Steuerelemente, die Daten in Form eines Diagramms mit X- und Y-Achse darstellen.

## <a name="description"></a>Beschreibung
Standardmäßig bestehen das **Säulendiagramm**-Steuerelement und das **Liniendiagramm**-Steuerelement aus mehreren gruppierten Steuerelementen. In diesen Steuerelementen werden ein Titel, Daten sowie eine Legende angezeigt.

## <a name="key-properties"></a>Haupteigenschaften
**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**NumberOfSeries** – Gibt an, wie viele Datenspalten in einem Säulen- oder Liniendiagramm widergespiegelt werden.

## <a name="all-properties"></a>Alle Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**GridStyle** – Gibt an, ob für ein Säulen- oder Liniendiagramm die x-Achse, die y-Achse, beide Achsen oder keine Achse angezeigt wird.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**ItemColorSet** – Die Farbe jedes Datenpunkts eines Diagramms.

**ItemsGap** – Der Abstand zwischen Spalten in einem Säulendiagramm.

* Die **ItemsGap**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**Markers** – Gibt an, ob in einem Säulen- oder Liniendiagramm der Wert der einzelnen Datenpunkte angezeigt wird.

**MarkerSuffix** – Text, der nach den einzelnen Werten in einem Säulendiagramm angezeigt wird, für das die **Markers**-Eigenschaft auf **true** festgelegt ist.

* Die **MarkerSuffix**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**MinimumBarWidth** – Die geringstmögliche Breite von Säulen in einem Säulendiagramm.

* Die **MinimumBarWidth**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**SeriesAxisMax** – Der höchste Wert für die y-Achse eines Säulen- oder Liniendiagramms.

* Die **SeriesAxisMax**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**SeriesAxisMin** – Eine Zahl, mit der der niedrigste Wert der y-Achse eines Säulendiagramms angegeben wird.

* Die **SeriesAxisMin**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**XLabelAngle** – Der Winkel der Beschriftungen unterhalb der x-Achse eines Säulen- oder Liniendiagramms.

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**YAxisMax** – Der höchste Wert der y-Achse eines Liniendiagramms.

* Die **YAxisMax**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**YAxisMin** – Der niedrigste Wert der y-Achse eines Liniendiagramms.

* Die **YAxisMin**-Eigenschaft ist nur beim **Säulendiagramm**-Steuerelement verfügbar, beim **Liniendiagramm**-Steuerelement kann sie nicht verwendet werden.

**YLabelAngle** – Der Winkel der Beschriftungen neben der y-Achse eines Linien- oder Säulendiagramms.

## <a name="related-functions"></a>Verwandte Funktionen
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein **[Button](control-button.md)**-Steuerelement (Schaltfläche) hinzu, und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:<br>
   **Collect(Revenue, {Year:"2013", Europa:24000, Ganymede:22300, Callisto:21200}, {Year:"2014", Europa:26500, Ganymede:25700, Callisto:24700},{Year:"2014", Europa:27900, Ganymede:28300, Callisto:25600})**
   
    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
2. Drücken Sie F5, klicken oder tippen Sie auf das **[Schaltflächen](control-button.md)**-Steuerelement, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.
3. Fügen Sie ein **Säulendiagramm**-Steuerelement oder ein **Liniendiagramm**-Steuerelement hinzu, und legen Sie für die **[Items](properties-core.md)**-Eigenschaft den Wert **Revenue** sowie für die **NumberOfSeries**-Eigenschaft den Wert **3** fest.
   
    Das Steuerelement zeigt die Umsatzdaten jedes Produkts aus drei Jahren an.


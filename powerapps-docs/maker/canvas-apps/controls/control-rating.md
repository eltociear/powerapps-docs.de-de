---
title: 'Steuerelement für Bewertungen: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Steuerelement für Bewertungen
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
ms.openlocfilehash: 4dd23b8c94ee4760e40b4513e7a88667f85c3a4b
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="rating-control-in-powerapps"></a>Steuerelement für Bewertungen in PowerApps
Ein Steuerelement, mit dem Benutzer einen Wert zwischen 1 und einer maximalen Anzahl, die Sie festlegen, angeben können.

## <a name="description"></a>Beschreibung
Mit diesem Steuerelement kann der Benutzer z.B. angeben, wie gut ihm etwas gefallen hat, indem er eine bestimmte Anzahl von Sternen auswählt.

## <a name="key-properties"></a>Haupteigenschaften
**[Default](properties-core.md)**: Der Anfangswert eines Steuerelements, bevor er vom Benutzer geändert wird.

**Max**: Der maximale Wert, auf den der Benutzer einen Schieberegler oder eine Bewertung festlegen kann.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[FocusedBorderThickness](properties-color-border.md)** – Die Rahmenstärke eines Steuerelements, wenn es den Tastaturfokus besitzt.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**RatingFill**: Die Farbe der Sterne in einem Steuerelement für Bewertungen.

**ReadOnly**: Gibt an, ob ein Benutzer den Wert eines Schiebereglers oder eines Bewertung-Steuerelements ändern kann.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**ShowValue**: Gibt an, ob ein Wert des Schiebereglers oder der Bewertung angezeigt wird, wenn der Benutzer diesen Wert ändert oder auf das Steuerelement zeigt.

**[TabIndex](properties-accessibility.md)**: Passt die Aktivierreihenfolge von Steuerelementen zur Laufzeit an, wenn sie auf einen Wert ungleich 0 festgelegt wird.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Average**( *Value1*, *Value2,* ... )](../functions/function-aggregates.md)

## <a name="example"></a>Beispiel
1. Fügen Sie ein Steuerelement **Rating** hinzu, und nennen Sie es **Quantitative**.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein Steuerelement **[Text input](control-text-input.md)** hinzu, nennen Sie es **Qualitative**, und verschieben Sie es unter das Steuerelement **Rating**.
3. Legen Sie die Eigenschaft **[Default](properties-core.md)** des Steuerelements **[Text input](control-text-input.md)** auf **""** fest, und legen Sie sein **HintText** auf diese Formel fest:
   <br>**If(Quantitative.Value > 3, „Was hat Ihnen besonders gefallen?“, „Wie können wir es besser machen?“)**
   
    Benötigen Sie weitere Informationen zur **[If](../functions/function-if.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
4. Drücken Sie F5, und klicken oder tippen Sie anschließend auf entweder vier oder fünf Sterne im Steuerelement **Rating** (Bewertung).
   
    Der Hinweistext im Steuerelement **[Text input](control-text-input.md)** wird geändert, um die hohe Bewertung zu reflektieren.
5. Klicken oder tippen Sie in **Quantitative** auf weniger als vier Sterne.
   
    Der Hinweistext im Steuerelement **[Text input](control-text-input.md)** wird geändert, um die niedrige Bewertung zu reflektieren.
6. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren.


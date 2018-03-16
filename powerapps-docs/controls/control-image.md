---
title: 'Image-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, zum Image-Steuerelement"
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
ms.openlocfilehash: 0ab25713976e9f89fa74b5f7664b13dca447841e
ms.sourcegitcommit: 87327f99636c68c62c755c4eb48861249a5a3add
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2018
---
# <a name="image-control-in-powerapps"></a>Image-Steuerelement in PowerApps
Ein Steuerelement, das ein Image aus einer lokalen Datei oder einer Datenquelle anzeigt

## <a name="description"></a>Beschreibung
Wenn Sie ein oder mehrere **Image**-Steuerelemente in Ihrer App hinzufügen, können Sie einzelne Images, die nicht Teil eines Datensatzes sind, anzeigen oder Images von Datensätzen in Datenquellen integrieren.

## <a name="key-properties"></a>Haupteigenschaften
**[Image](properties-visual.md)** : der Name des Images, das in einem Image-, Audio- oder Mikrofon-Steuerelement angezeigt wird

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**ApplyEXIFOrientation**: Gibt an, ob Ausrichtung, die in den im Bild eingebetteten EXIF-Daten angegeben ist, automatisch angewendet wird.

**AutoDisableOnSelect**: Deaktiviert das Steuerelement automatisch, während das OnSelect-Verhalten ausgeführt wird.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[FocusedBorderThickness](properties-color-border.md)** – Die Rahmenstärke eines Steuerelements, wenn es den Tastaturfokus besitzt.

**CalculateOriginalDimensions**: aktiviert die **OriginalHeight** und **OriginalWidth**-Eigenschaften.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**FlipHorizontal**: Gibt an, ob das Bild vor der Anzeige horizontal gekippt werden soll.

**FlipVertical**: Gibt an, ob das Bild vor der Anzeige vertikal gekippt werden soll.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[ImagePosition](properties-visual.md)**: Die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Bilds auf einem Bildschirm oder in einem Steuerelement, wenn die Größe nicht mit der Bildgröße identisch ist.

**ImageRotation**: Gibt an, wie das Bild vor der Anzeige gedreht werden soll.  Zulässige Werte sind „none“, „clockwise (CW) 90 degrees“, „counter-clockwise (CCW) 90 degrees“ und „clockwise 180 degrees“.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OriginalHeight**: gibt die ursprüngliche Höhe eines Images an, wobei die **CalculateOriginalDimensions**-Eigenschaft aktiviert ist.

**OriginalWidth**: gibt die ursprüngliche Breite eines Images an, wobei die **CalculateOriginalDimensions**-Eigenschaft aktiviert ist.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[RadiusBottomLeft](properties-size-location.md)** – Der Grad der Rundung der linken unteren Ecke eines Steuerelements.

**[RadiusBottomRight](properties-size-location.md)** – Der Grad der Rundung der rechten unteren Ecke eines Steuerelements.

**[RadiusTopLeft](properties-size-location.md)** – Der Grad der Rundung der linken oberen Ecke eines Steuerelements.

**[RadiusTopRight](properties-size-location.md)** – Der Grad der Rundung der rechten oberen Ecke eines Steuerelements.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**Transparency**: gibt an, inwieweit Steuerelemente hinter einem Bild sichtbar bleiben.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Remove**( *DataSource*, ThisItem)](../functions/function-remove-removeif.md)

## <a name="examples"></a>Beispiele
### <a name="show-an-image-from-a-local-file"></a>Anzeigen eines Images aus einer lokalen Datei
1. Klicken oder tippen Sie im Menü **File** (Datei) auf die Option **Media** (Medien), und klicken oder tippen Sie anschließend auf **Browse** (Durchsuchen).
2. Klicken oder tippen Sie auf die Image-Datei, die Sie hinzufügen möchten, und klicken oder tippen Sie auf **Open** (Öffnen). Drücken Sie anschließend ESC, um in den Standardarbeitsbereich zurückzukehren.
3. Fügen Sie ein **Image**-Steuerelement hinzu, und legen Sie dessen **Image**-Eigenschaft auf den Namen der Datei fest, die Sie hinzugefügt haben.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

    Das **Image**-Steuerelement zeigt das von Ihnen angegebene Image an.

### <a name="show-a-set-of-images-from-a-data-source"></a>Anzeigen eines Satzes von Images aus einer Datenquelle
1. Laden Sie diese [Excel-Datei](https://pwrappssamples.blob.core.windows.net/samples/FlooringEstimates.xlsx) herunter, und speichern Sie sie auf Ihrem lokalen Gerät.
2. Erstellen oder öffnen Sie in PowerApps Studio eine App, und klicken oder tippen Sie dann im rechten Bereich auf **Datenquelle hinzufügen**.

    Wenn im rechten Bereich **Datenquelle hinzufügen** nicht angezeigt wird, klicken oder tippen Sie auf der linken Navigationsleiste auf einen beliebigen Bildschirm.
3. Klicken oder tippen Sie auf **Add static data to your app** (Statische Daten zu Ihrer App hinzufügen), klicken oder tippen Sie auf die Excel-Datei, die Sie heruntergeladen haben, und klicken oder tippen Sie anschließend auf **Open** (Öffnen).
4. Aktivieren Sie das Kontrollkästchen **Flooring Estimates** (Kostenschätzungen für Bodenbeläge), und klicken oder tippen Sie auf **Connect** (Verbinden).
5. Fügen Sie ein **Katalog**-Steuerelement mit Bildern hinzu, und legen Sie seine **[Items](properties-core.md)**-Eigenschaft auf **FlooringEstimates** (Kostenschätzungen für Bodenbeläge) fest.

    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?

    Das **Katalog**-Steuerelement zeigt Bilder von Teppich-, Parkett- und Fliesenprodukten auf Basis von Links in der von Ihnen heruntergeladenen Excel-Datei.

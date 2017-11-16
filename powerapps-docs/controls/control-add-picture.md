---
title: "Steuerelement „Bild hinzufügen“: Referenz | Microsoft-Dokumentation"
description: "Informationen, einschließlich Eigenschaften und Beispiele, über das Steuerelement „Bild hinzufügen“"
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
ms.openlocfilehash: 6a7c60755f5623803d20bec4ec9881108b1116c6
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="add-picture-control-in-powerapps"></a>Steuerelement „Bild hinzufügen“ in PowerApps
Nimmt ein Foto auf oder lädt Bilder vom lokalen Gerät.

## <a name="description"></a>Beschreibung
Mit diesem Steuerelement können die Benutzer Fotos aufnehmen oder Bilddateien von ihrem Gerät laden und die Datenquelle mit diesem Inhalt aktualisieren. Auf einem mobilen Gerät wird für den Benutzer das Auswahldialogfeld des Geräts angezeigt, in dem zwischen dem Aufnehmen eines Fotos und dem Auswählen eines bereits verfügbaren Fotos gewählt werden kann.

Dieses Steuerelement besteht aus zwei Steuerelementen.  Klicken oder tippen Sie einmal, um das äußere Steuerelement auszuwählen, das das geladene Bild enthält.  Klicken oder tippen Sie erneut, um das innere Label-Steuerelement auszuwählen.

## <a name="outer-control-properties"></a>Eigenschaften des äußeren Steuerelements
Diese Eigenschaften beziehen sich auf das äußere Steuerelement.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**Error** – Falls beim Hochladen eines Bilds ein Problem auftritt, enthält diese Eigenschaft eine entsprechende Fehlerzeichenfolge.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**Media** – Ein Bezeichner für den Clip, der von einem Audio- oder Video-Steuerelement wiedergegeben wird.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="inner-text-properties"></a>Eigenschaften des inneren Textfelds
Diese Eigenschaften beziehen sich auf das innere Label-Steuerelement, das in der Standardeinstellung den Text „Tippen oder klicken, um ein Bild hinzuzufügen“ enthält.  Klicken oder tippen Sie zum Auswählen dieses inneren Steuerelements einmal auf das Steuerelement **Bild hinzufügen**, und klicken oder tippen Sie dann noch einmal.

**[Align](properties-text.md)** – Die Position von Text in Relation zur horizontalen Mitte des Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Font](properties-text.md)** – Der Name der Schriftfamilie des angezeigten Texts.

**[FontWeight](properties-text.md)** – Die Schriftbreite des Texts in einem Steuerelement: **Bold** (Fett), **Semibold** (Halbfett), **Normal** oder **Lighter** (Heller).

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[Italic](properties-text.md)** – Legt fest, ob der Text in einem Steuerelement kursiv formatiert ist.

**[OnChange](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

**[Padding](properties-size-location.md)** – Der Abstand zwischen dem Text auf einer Import- oder Exportschaltfläche und den Rändern der Schaltfläche.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[Strikethrough](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text durchgestrichen ist.

**[Text](properties-core.md)** – Text, der in einem Steuerelement angezeigt wird oder von einem Benutzer in ein Steuerelement eingegeben wird.

**[Underline](properties-text.md)** – Legt fest, ob der in einem Steuerelement angezeigte Text unterstrichen ist.

**[VerticalAlign](properties-text.md)** – Die Position des Texts in einem Steuerelement in Relation zur vertikalen Mitte des Steuerelements.

## <a name="related-functions"></a>Verwandte Funktionen
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Beispiel
### <a name="add-images-to-an-image-gallery-control"></a>Hinzufügen von Bildern zu einem Bildkatalog-Steuerelement
1. Fügen Sie ein **Bild hinzufügen**-Steuerelement hinzu, und klicken Sie dann dreimal darauf.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Klicken oder tippen Sie im Dialogfeld **Öffnen** auf eine Bilddatei, und klicken oder tippen Sie dann auf **Öffnen**.
3. Fügen Sie ein **[Schaltfläche](control-button.md)**-Steuerelement hinzu, verschieben Sie es unter das Steuerelement **Bild hinzufügen**, und legen Sie die **[OnSelect](properties-core.md)**-Eigenschaft für das **[Schaltfläche](control-button.md)**-Steuerelement auf die folgende Formel fest:<br>
   **Collect(MyPix, AddMediaButton1.Media)**
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder zu [anderen Funktionen](../formula-reference.md)?
4. Fügen Sie ein **Bildkatalog**-Steuerelement hinzu, und legen Sie dessen **[Items](properties-core.md)**-Eigenschaft auf **MyPix** fest.
5. Drücken Sie F5, und klicken oder tippen Sie auf das **[Schaltfläche](control-button.md)**-Steuerelement.
   
    Das Bild aus dem **Bild hinzufügen**-Steuerelement wird im Steuerelement **Bildkatalog** angezeigt. Wenn das Bild nicht das gleiche Seitenverhältnis wie das **[Bild](control-image.md)**-Steuerelement im **Bildkatalog**-Steuerelement aufweist, legen Sie die **[ImagePosition](properties-visual.md)**-Eigenschaft des **[Bild](control-image.md)**-Steuerelements auf **Fit** fest.
6. Klicken oder tippen Sie auf das **Bild hinzufügen**-Steuerelement, auf eine andere Bilddatei, auf **Öffnen** und dann auf das hinzugefügte **[Schaltfläche](control-button.md)**-Steuerelement.
   
    Das zweite Bild wird im **Bildkatalog**-Steuerelement angezeigt.
7. (optional) Wiederholen Sie den vorherigen Schritt beliebig oft, und kehren Sie dann zurück zum Standardarbeitsbereich, indem Sie ESC drücken.

Verwenden Sie die **[SaveData](../functions/function-savedata-loaddata.md)**-Funktion, um die Bilder lokal zu speichern, oder die **[Patch](../functions/function-patch.md)**-Funktion, um eine Datenquelle zu aktualisieren.


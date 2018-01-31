---
title: 'Audio- und Video-Steuerelemente: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, über Audio- und Video-Steuerelemente"
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
ms.openlocfilehash: 7aa3c2e2e6b0e6baaaec9666fc7b4e56c9568317
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="audio-and-video-controls-in-powerapps"></a>Audio- und Video-Steuerelemente in PowerApps
Ein Steuerelement, das eine Audiodatei, eine Videodatei oder Videos auf YouTube abspielt.

## <a name="description"></a>Beschreibung
In einem **Audio**-Steuerelement kann ein Audioclip aus einer Datei, eine Aufzeichnung aus einem **[Mikrofon](control-microphone.md)**-Steuerelement oder die Audiospur aus einer Videodatei abgespielt werden. In einem **Video**-Steuerelement werden Videoclips aus einer Datei oder von YouTube abgespielt, wenn Sie eine URL angeben.

## <a name="key-properties"></a>Haupteigenschaften
**Loop** – Gibt an, ob ein Audio- oder Videoclip am Ende der Wiedergabe automatisch neu gestartet wird.

**Media**: Ein Bezeichner für den Clip, der von einem Audio- oder Video-Steuerelement wiedergegeben wird.

**ShowControls** – Gibt an, ob ein Audio- oder Videoplayer, z.B. eine Schaltfläche für Wiedergabe und ein Lautstärkeregler, und ein Stift-Steuerelement angezeigt wird, z.B. Symbole zum Zeichnen oder Löschen.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**AutoPause** – Gibt an, ob ein Audio- oder Videoclip automatisch angehalten wird, wenn der Benutzer zu einem anderen Bildschirm navigiert.

**AutoStart** – Gibt an, ob ein Steuerelement Audio oder Video automatisch einen Clip wiedergibt, wenn der Benutzer zu dem Bildschirm navigiert, der das Steuerelement enthält.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[Image](properties-visual.md)** – Der Name des Bilds, das in einem Bild-, Audio- oder Mikrofon-Steuerelement angezeigt wird.

**[ImagePosition](properties-visual.md)** – Die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Bilds auf einem Bildschirm oder in einem Steuerelement, wenn die Größe nicht mit der Bildgröße identisch ist.

**OnEnd** – Gibt an, wie eine App reagiert, wenn die Wiedergabe eines Audio- oder Videoclips beendet ist.

**OnPause** – Gibt an, wie eine App reagiert, wenn der Benutzer den Clip anhält, der von einem Audio- oder Video-Steuerelement wiedergegeben wird.

**OnStart** – Gibt an, wie die App reagiert, wenn der Benutzer die Aufnahme per Mikrofon-Steuerelement startet.

**Paused** – Ist *true*, wenn ein Steuerelement zum Wiedergeben von Medien angehalten wurde, andernfalls *false*.

**[Reset](properties-core.md)** – Legt fest, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**Start** – Gibt an, ob ein Audio- oder Videoclip wiedergegeben wird.

**StartTime** – Der Zeitpunkt nach dem Start eines Audio- oder Videoclips, zu dem die Wiedergabe des Clips beginnt.

**Time** – Die aktuelle Position eines Mediensteuerelements.

**[Tooltip](properties-core.md)** – Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**First**( *TableName* )](../functions/function-first-last.md)

## <a name="examples"></a>Beispiele
### <a name="play-an-audio-or-video-file"></a>Wiedergeben einer Audio- oder Videodatei
1. Klicken oder tippen Sie im Menü **Datei** auf **Medien**, klicken oder tippen Sie auf **Videos** oder **Audio**, und klicken oder tippen Sie dann auf **Durchsuchen**.
2. Navigieren Sie zu der Datei, die Sie verwenden möchten, klicken oder tippen Sie darauf und dann auf **Öffnen**.
3. Drücken Sie ESC, um zum Standardarbeitsbereich zurückzukehren, fügen Sie ein **Audio**- oder **Video**-Steuerelement hinzu, und legen Sie die **Media**-Eigenschaft auf die hinzugefügte Datei fest.
   
    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?
4. Drücken Sie F5, und spielen Sie den Clip durch Klicken oder Tippen auf die Wiedergabeschaltfläche des Steuerelements ab, das Sie hinzugefügt haben.
   
    > [!TIP]
> Die Wiedergabeschaltfläche für das **Video**-Steuerelement wird angezeigt, wenn Sie auf das Steuerelement zeigen.
5. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.

### <a name="play-a-youtube-video"></a>Abspielen eines YouTube-Videos
1. Fügen Sie ein **Video**-Steuerelement hinzu, und legen Sie die **Media**-Eigenschaft auf die URL (in doppelten Anführungszeichen) eines YouTube-Videos fest.
2. Drücken Sie F5, und spielen Sie den Clip durch Klicken oder Tippen auf die Wiedergabeschaltfläche des **Video**-Steuerelements ab.
3. Drücken Sie die ESC-Taste, um zum Standardarbeitsbereich zurückzukehren.


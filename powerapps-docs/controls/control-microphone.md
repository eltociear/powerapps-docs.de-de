---
title: 'Mikrofon-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, zum Mikrofon-Steuerelement"
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
ms.openlocfilehash: 3ffede0018a371b3c3a4cf4a3a1f9fc8115140de
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="microphone-control-in-powerapps"></a>Mikrofon-Steuerelement in PowerApps
Ein Steuerelement, mit dem der Benutzer Töne aufzeichnen kann

## <a name="description"></a>Beschreibung
Wenn Sie dieses Steuerelement hinzufügen, kann der Benutzer eine Datenquelle mit einem oder mehreren Tönen aktualisieren, unabhängig davon, wo die App ausgeführt wird.

## <a name="key-properties"></a>Haupteigenschaften
**Mic**: gibt auf einem Gerät mit mehr als einem Mikrofon die numerische ID des Mikrofons an, das die App verwendet.

**OnStop**: gibt an, wie die App reagiert, wenn der Benutzer die Aufzeichnung mit einem Mikrofon-Steuerelement beendet.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[Color](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledColor](properties-color-border.md)**: Die Farbe des Texts in einem Steuerelement, wenn seine **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[DisabledFill](properties-color-border.md)**: Die Hintergrundfarbe eines Steuerelements, wenn dessen **[DisplayMode](properties-core.md)**-Eigenschaft auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[HoverColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer den Mauszeiger über ihm hält.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[Image](properties-visual.md)** : der Name des Images, das in einem Image-, Audio- oder Mikrofon-Steuerelement angezeigt wird

**[ImagePosition](properties-visual.md)** : gibt die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Images in einem Bildschirm oder in einem Steuerelement an, wenn es nicht die gleiche Größe wie das Image hat.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnStart**: gibt an, wie die App reagiert, wenn der Benutzer eine Aufzeichnung mit einem Steuerelement-Mikrofon beginnt.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedColor](properties-color-border.md)** – Die Farbe des Texts in einem Steuerelement, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[PressedFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[Reset](properties-core.md)**: Gibt an, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

**[QuickInfo](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Beispiel
### <a name="add-sounds-to-a-custom-gallery-control"></a>Hinzufügen von Tönen zu einem benutzerdefinierten Katalog-Steuerelement
1. Fügen Sie ein **Mikrofon** hinzu, nennen Sie es **MyMic**, und legen Sie seine **OnStop**-Eigenschaft auf folgende Formel fest:<br>
   **Collect(MySounds, MyMic.Audio)**
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
2. Fügen Sie ein Steuerelement des Typs **benutzerdefinierter Katalog** hinzu, verschieben Sie es unter **MyMic**, und legen Sie die **[Items](properties-core.md)**-Eigenschaft für das Steuerelement des Typs **benutzerdefinierter Katalog** auf **MySounds** fest.
3. Fügen Sie in der Vorlage für das Steuerelement des Typs **benutzerdefinierter Katalog** ein **[Audio](control-audio-video.md)**-Steuerelement hinzu, und legen Sie seine **Media**-Eigenschaft auf **ThisItem.Url** fest.
4. Drücken Sie F5, klicken oder tippen Sie auf **MyMic**, um mit der Aufzeichnung zu beginnen, und klicken oder tippen Sie anschließend erneut, um die Aufzeichnung zu beenden.
5. Klicken oder tippen Sie im Steuerelement des Typs **benutzerdefinierter Katalog** auf die Schaltfläche zur Wiedergabe im **[Audio](control-audio-video.md)**-Steuerelement, um Ihre Aufzeichnung wiederzugeben.
6. Fügen Sie eine beliebig große Anzahl von Aufzeichnungen ein, und kehren Sie anschließend durch Drücken von ESC in den Standardarbeitsbereich zurück.
7. (optional) Fügen Sie in der Vorlage für das Steuerelement des Typs **benutzerdefinierter Katalog** ein **[Schaltflächen](control-button.md)**-Steuerelement ein, und legen Sie seine  **[OnSelect](properties-core.md)**-Eigenschaft auf **Remove(MySounds, ThisItem)** fest. Drücken Sie anschließend F5, und entfernen Sie eine Aufzeichnung durch Klicken oder Tippen auf das entsprechende **Schaltflächen**-Steuerelement.

Verwenden Sie die  **[SaveData](../functions/function-savedata-loaddata.md)**-Funktion, um die Aufzeichnungen lokal zu speichern, oder die  **[Patch](../functions/function-patch.md)**-Funktion, um eine Datenquelle zu aktualisieren.


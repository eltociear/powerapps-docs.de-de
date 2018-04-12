---
title: 'Stifteingabe-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Stifteingabe-Steuerelement
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
ms.openlocfilehash: 7e5be9b68b501279329c23f9afe5d451487fa8d1
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="pen-input-control-in-powerapps"></a>Stifteingabe-Steuerelement in PowerApps
Ein Steuerelement, mit dem der Benutzer Bereiche eines Bildes zeichnen, löschen oder markieren kann.

## <a name="description"></a>Beschreibung
Benutzer können dieses Steuerelement wie ein Whiteboard verwenden. Sie können Diagramme zeichnen und Wörter schreiben, die in eingegebenen Text konvertiert werden können.

## <a name="key-properties"></a>Haupteigenschaften
**[Color](properties-color-border.md)**  – Die Farbe der Eingabestriche.

**Mode** – Das Steuerelement ist im Modus **Draw** oder **Erase**.  Der Modus „Select“ ist veraltet.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**Input**: Eingabe

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**[SelectionColor](properties-color-border.md)**: Die Textfarbe des ausgewählten Elements oder der Elemente in einer Liste oder die Farbe des Auswahltools in einem Stift-Steuerelement.

**SelectionThickness**: Die Stärke des Auswahltools für ein Stifteingabe-Steuerelement.

**ShowControls**: Gibt beispielsweise an, ob für einen Audio- oder Videoplayer eine Schaltfläche für die Wiedergabe und ein Lautstärkeregler und für ein Stift-Steuerelement Symbole zum Zeichnen oder Löschen angezeigt werden.

**[Size](properties-text.md)** – Der Schriftgrad des Texts, der in einem Steuerelement angezeigt wird.

**[QuickInfo](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Collect**( *CollectionName*, *DatatoCollect* )](../functions/function-clear-collect-clearcollect.md)

## <a name="example"></a>Beispiel
### <a name="create-a-set-of-images"></a>Erstellen Sie einen Satz von Bildern
1. Fügen Sie ein **Pen input**-Steuerelement hinzu, benennen Sie es **MyDoodles** und legen Sie seine Eigenschaft **ShowControls** auf **TRUE** fest.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein Steuerelement **[Button](control-button.md)** hinzu, verschieben Sie es unter **MyDoodles**, und legen Sie die Eigenschaft **[Text](properties-core.md)** des Steuerelements **[Button](control-button.md)** so fest, dass **Add** angezeigt wird.
3. Legen Sie die Eigenschaft **[OnSelect](properties-core.md)** des Steuerelements **[Button](control-button.md)** auf die folgende Formel fest:<br>
   **Collect(Doodles, {Sketch:MyDoodles.Image})**
4. Fügen Sie ein Steuerelement **Image gallery** hinzu, verschieben Sie es unter das Steuerelement **[Button](control-button.md)**, und verkleinern Sie die Breite des **Image gallery**, bis drei Elemente angezeigt werden.
5. Legen Sie die Eigenschaft **[Items](properties-core.md)** des Steuerelements **Image gallery** auf **Doodles** fest, und drücken Sie anschließend F5.
6. Zeichnen Sie ein Bild in **MyDoodles**, und klicken oder tippen Sie anschließend auf das Steuerelement **[Button](control-button.md)**.
   
    Das Bild, das Sie gezeichnet haben, wird im Steuerelement **Image gallery** angezeigt.
7. (optional) Klicken oder tippen Sie im Steuerelement **Pen input** auf das Symbol, um das gezeichnete Bild zu löschen, zeichnen Sie ein anderes Bild, und klicken oder tippen Sie auf das Steuerelement **[Button](control-button.md)**.
8. Legen Sie im Steuerelement **Image gallery** die Eigenschaft **[OnSelect](properties-core.md)** des Steuerelements **[Image](control-image.md)** auf diese Formel fest:<br>
   **Remove(Doodles, ThisItem)**
9. Entfernen Sie eine Zeichnung, indem Sie auf das Steuerelement **Image gallery** klicken oder tippen.

Verwenden Sie die **[SaveData](../functions/function-savedata-loaddata.md)**-Funktion, um Ihre Zeichnungen lokal zu speichern, oder die **[Patch](../functions/function-patch.md)**-Funktion zur Speicherung in einer Datenquelle.

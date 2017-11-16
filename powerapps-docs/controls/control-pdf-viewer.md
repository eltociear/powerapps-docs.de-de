---
title: 'PDF-Viewer-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, zum PDF-Viewer-Steuerelement"
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
ms.openlocfilehash: 51b0045bd8b5e83f754c4d68e1dfe63566371ae1
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="pdf-viewer-control-in-powerapps"></a>PDF-Viewer-Steuerelement in PowerApps
Ein Steuerelement, das den Inhalt einer PDF-Datei anzeigt

## <a name="description"></a>Beschreibung
Zeigen Sie Text, Grafiken und anderen Inhalt in einer PDF-Datei an, indem Sie diese Art von Steuerelement hinzufügen und seine **Document**-Eigenschaft auf die URL der Datei festlegen, die Sie anzeigen möchten. Verwenden Sie dabei doppelte Anführungszeichen.

## <a name="key-properties"></a>Haupteigenschaften
**Document**: gibt die, in doppelten Anführungszeichen gesetzte, URL der PDF-Datei an.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**ActualZoom**: gibt den tatsächlichen Vergrößerungsfaktor des Steuerelements an. Dieser kann sich von dem Faktor unterscheiden, der mit der **Zoom**-Eigenschaft angefordert wurde.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**CurrentFindText**: gibt den aktuellen Suchbegriff an, der verwendet wird.

**CurrentPage**: gibt die Anzahl der Seiten in einer PDF-Datei an, die tatsächlich angezeigt wird.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[DisabledBorderColor](properties-color-border.md)**: Die Farbe des Steuerelementrahmens, wenn die **[DisplayMode](properties-core.md)**-Eigenschaft des Steuerelements auf **Disabled** (Deaktiviert) festgelegt ist.

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**FindNext**: sucht nach der nächsten Instanz von **FindText** im Dokument.

**FindPrevious**: sucht nach der vorherigen Instanz von **FindText** im Dokument.

**FindText**: gibt den Suchbegriff an, der im Dokument gesucht.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über das Steuerelement hält.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnStateChange**: gibt an, wie eine App reagiert, wenn sich der Zustand des Steuerelements ändert.

**[PaddingBottom](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem unteren Rand des Steuerelements.

**[PaddingLeft](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem linken Rand des Steuerelements.

**[PaddingRight](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem rechten Rand des Steuerelements.

**[PaddingTop](properties-size-location.md)**: Der Abstand zwischen dem Text eines Steuerelements und dem oberen Rand des Steuerelements.

**Page**: gibt die Nummer der Seite an, die Sie anzeigen möchten.

**PageCount**: gibt die Anzahl der Seiten in einem Dokument an.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**ShowControls**: Gibt beispielsweise an, ob für einen Audio- oder Videoplayer eine Schaltfläche für die Wiedergabe und ein Lautstärkeregler und für ein Stift-Steuerelement Symbole zum Zeichnen oder Löschen angezeigt werden.

**[QuickInfo](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**Zoom**: gibt den Prozentsatz an, mit dem ein Bild einer Kamera vergrößert wird (oder die Ansicht einer Datei in einem PDF-Viewer).

## <a name="example"></a>Beispiel
* Fügen Sie ein Steuerelement des Typs **PDF-Viewer** hinzu, und legen Sie seine **Document**-Eigenschaft (in doppelten Anführungszeichen) auf die URL einer PDF-Datei fest, wie im folgenden Beispiel gezeigt:<br>
  **"http://www.who.int/gho/publications/world_health_statistics/EN_WHS2015_TOC.pdf?ua=1"**
  
    Das Steuerelement zeigt die PDF-Datei.
  
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?


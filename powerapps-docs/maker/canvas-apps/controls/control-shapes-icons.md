---
title: 'Shape-Steuerelemente und Symbole für Steuerelemente: Referenz | Microsoft-Dokumentation'
description: Informationen einschließlich Eigenschaften und Beispielen für Shape-Steuerelemente und Symbole für Steuerelemente
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
ms.openlocfilehash: 7a71695460453816dd5c63dad8477cb7ccc703d7
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>Shape-Steuerelemente und Symbole für Steuerelemente in PowerApps
Grafiken, deren Eigenschaften wie Aussehen und Verhalten Sie konfigurieren können

## <a name="description"></a>Beschreibung
Diese Steuerelemente umfassen Pfeile, geometrische Formen, Aktionssymbole und Symbole, deren Eigenschaften wie Füllung, Größe und Position sich konfigurieren lassen. Sie können auch die Eigenschaft **[OnSelect](properties-core.md)** konfigurieren, damit die App reagiert, wenn der Benutzer auf das Steuerelement klickt oder tippt.

## <a name="key-properties"></a>Haupteigenschaften
**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[HoverFill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger über ihm hält.

**[PressedBorderColor](properties-color-border.md)** – Die Rahmenfarbe eines Steuerelements, wenn der Benutzer auf das Steuerelement tippt oder klickt.

**[FocusedBorderThickness](properties-color-border.md)** – Die Rahmenstärke eines Steuerelements, wenn es den Tastaturfokus besitzt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen
[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>Beispiel
1. Nennen Sie das **[Bildschirm](control-screen.md)**-Standardsteuerelement **Target**, fügen Sie ein **[Label](control-text-box.md)**-Steuerelement (Bezeichnung) hinzu, und legen Sie anschließend die  **[Text](properties-core.md)**-Eigenschaft so fest, dass **Target** angezeigt wird.
   
    Möchten Sie wissen, wie Sie ein [Steuerelement hinzufügen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein **[Bildschirm](control-screen.md)**-Steuerelement hinzu, und nennen Sie es **Source**.
3. Fügen Sie in **Source** ein **Shape**-Steuerelement hinzu, und legen Sie seine **[OnSelect](properties-core.md)**-Eigenschaft auf diese Formel fest:
   <br>**Navigate(Target, ScreenTransition.Fade)**
4. Drücken Sie F5, und klicken oder tippen Sie anschließend auf das **Shape**-Steuerelement.
   
    Der Bildschirm **Target** wird angezeigt.
5. (optional) Drücken Sie die ESC-TASTE, um zum Standardarbeitsbereich zurückzukehren, fügen Sie ein **Shape**-Steuerelement zu **Target** hinzu, und legen Sie die **[OnSelect](properties-core.md)**-Eigenschaft des **Shape**-Steuerelements auf diese Formel fest:
   <br>**Navigate(Source, ScreenTransition.Fade)**


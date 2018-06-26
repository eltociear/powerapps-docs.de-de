---
title: Referenz zum Rich-Text-Editor-Steuerelement | Microsoft-Dokumentation
description: Informationen über das Rich-Text-Editor-Textsteuerelement, einschließlich Eigenschaften und Beispielen
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
ms.date: 05/24/2018
ms.author: fikaradz
ms.openlocfilehash: 36fa317a4611c72ab4d2f6ce09e176b14b688a55
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34585087"
---
# <a name="rich-text-editor-control-experimental-in-powerapps"></a>Rich-Text-Editor-Steuerelement in PowerApps (experimentell)
Ein experimentelles Steuerelement, über das Benutzer Text innerhalb eines WYSIWYG-Bearbeitungsbereichs formatieren können.  Die Ausgabe erfolgt im HTML-Format.

## <a name="description"></a>Beschreibung
Das **Rich-Text-Editor**-Steuerelement stellt für den App-Benutzer einen WYSIWYG-Bearbeitungsbereich zum Formatieren von Text bereit.  Die Eingaben und Ausgaben des Steuerelements erfolgen im HTML-Format.

Sie können (z.B. aus einem Webbrowser oder aus Word) kopierten Rich-Text in das Steuerelement einfügen.  

Das Steuerelement soll zum Formatieren von Text verwendet werden. Es wird nicht garantiert, dass die Integrität der HTML-Eingabe erhalten bleibt.  Sämtliche Skript-, Stil- und Objektmarkierungen sowie andere Markierungen, die Probleme hervorrufen könnten, werden vom Editor entfernt.  D.h., wenn Rich-Text außerhalb von PowerApps erstellt wurde, sieht er möglicherweise nicht so aus wie in dem Produkt, in dem er erstellt wurde.

Derzeit werden die folgenden Features unterstützt:
- Fett, kursiv, unterstrichen
- Textfarbe, Hervorhebungsfarbe
- Textgröße
- Nummerierte Listen, Aufzählungen
- Hyperlinks
- Formatierung löschen

Wenn Sie das Steuerelement innerhalb eines Formulars verwenden möchten, klicken Sie auf die Karte „Mehrzeiligen Text bearbeiten“, und passen Sie dieses an, indem Sie das RTE-Steuerelement einfügen.

## <a name="limitations"></a>Beschränkungen
Die aktuelle Version des Steuerelements befindet sich aufgrund der folgenden temporären Einschränkungen noch in der Experimentierphase:
- Das Steuerelement weist eingeschränkte Features zum Formatieren von Text auf.  

- Das Steuerelement ist hauptsächlich für die Verwendung in Browsern auf großen Bildschirmen vorgesehen.  Die Verwendung des Steuerelements auf einem Smartphone kann daher sehr frustrierend sein.

- Bekannte Probleme bei der Erstellung, wenn Windows Studio oder der Edge-Browser verwendet werden.  Derzeit wird empfohlen, Web Studio in Chrome zu verwenden.


## <a name="key-properties"></a>Haupteigenschaften
**[Standard:](properties-core.md)** Eingabeeigenschaft für den ersten Textwert, der im Editor angezeigt wird.

**HtmlText:** Ausgabeeigenschaft für den entstandenen Rich-Text im HTML-Format.



## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[AccessibleLabel](properties-accessibility.md)**: Bezeichnung für Sprachausgaben Sollte den Zweck dieser Anlagen beschreiben.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement das Hinzufügen und Löschen von Dateien zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[TabIndex](properties-accessibility.md)**: Navigationsreihenfolge der Tastatur in Bezug auf andere Steuerelemente.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (oder des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

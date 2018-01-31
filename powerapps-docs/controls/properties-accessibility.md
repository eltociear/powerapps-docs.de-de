---
title: Eigenschaften von Bedienungshilfen | Microsoft-Dokumentation
description: "Enthält Referenzinformationen zu Eigenschaften, z.B. TabIndex, QuickInfo."
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
ms.date: 01/26/2017
ms.author: fikaradz
ms.openlocfilehash: d35b4bc7a6e479ce47ad0a0b841a6ed9ccfd1a52
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="accessibility-properties-in-powerapps"></a>Eigenschaften von Bedienungshilfen in PowerApps
Hier geht es um die Konfiguration von Eigenschaften, die für Benutzer mit Sehschwäche als Hilfe für alternative Interaktionsmöglichkeiten mit Steuerelementen dienen.

### <a name="properties"></a>Eigenschaften
**AccessiblityLabel**: Beschreibung des Steuerelements, das von Bildschirmsprachausgaben gelesen werden soll.   Durch einen leeren Wert für Bild-, Symbol- und Formsteuerelemente werden diese für die Bildschirmsprachausgabe unsichtbar und als Dekoration behandelt.

* Gilt für Steuerelemente des folgenden Typs: **[Audio](control-audio-video.md)**, **[Schaltfläche](control-button.md)**, **[Kamera](control-camera.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Dropdown](control-drop-down.md)**, **[HTML-Text](control-html-text.md)**, **[Bild](control-image.md)**, **[Bezeichnung](control-text-box.md)**, **[Listenfeld](control-list-box.md)**, **[Mikrofon](control-microphone.md)**, **[PDF-Viewer](control-pdf-viewer.md)**, **[Stifteingabe](control-pen-input.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)**, **[Timer](control-timer.md)**, **[Umschalten](control-toggle.md)** und **[Video](control-audio-video.md)**.

**TabIndex**: Passt die Aktivierreihenfolge von Steuerelementen zur Laufzeit an.

Mit dem Standardwert 0 wird die Standardaktivierreihenfolge basierend auf der XY-Koordinate des Steuerelements angegeben.  Wenn Sie einen höheren Wert als 0 wählen, wird die Aktivierreihenfolge für alle Steuerelemente mit den Standardwerten entsprechend verschoben.  Ein Steuerelement mit einem TabIndex-Wert von 2 hat in der Aktivierreihenfolge Vorrang vor einem Steuerelement mit dem TabIndex-Wert 3 oder höher.

Beachten Sie, dass bei Containern, z.B. Formular- und Katalog-Steuerelementen, immer erst alle Elemente des Containers durchlaufen werden, bevor die Steuerelemente außerhalb des Containers an die Reihe kommen.  Die Aktivierreihenfolge des Containers entspricht der Reihenfolge des niedrigsten TabIndex-Werts eines untergeordneten Steuerelements.

Durch Festlegen von TabIndex auf den Wert -1 wird der Registerkartenzugriff auf das Steuerelement deaktiviert; im Fall von Bildern, Symbolen und Formen werden diese zu nicht interaktiven Elementen.

* Gilt für Steuerelemente des folgenden Typs: **[Schaltfläche](control-button.md)**, **[Datumsauswahl](control-date-picker.md)**, **[Dropdown](control-drop-down.md)**, **[Bild](control-image.md)**, **[Import](control-export-import.md)**, **[Listenfeld](control-list-box.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)** und **[Umschalten](control-toggle.md)**.

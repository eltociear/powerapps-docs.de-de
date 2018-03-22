---
title: Kerneigenschaften | Microsoft-Dokumentation
description: Enthält Referenzinformationen zu den Eigenschaften „Disabled“, „Visible“ und „ReadOnly“.
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: cad53141d6896ad71caaca77b7bf07fee2ac0600
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="core-properties-in-powerapps"></a>Kerneigenschaften in PowerApps
Konfigurieren Sie, ob der Benutzer ein Steuerelement sehen und damit interagieren kann.

### <a name="properties"></a>Eigenschaften
**Default**: Anfangswert eines Steuerelements, bevor es vom Benutzer geändert wird.

* Gilt für Steuerelemente des folgenden Typs: **[Karte](control-card.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Dropdown](control-drop-down.md)**, **[Katalog](control-gallery.md)**, **[Listenfeld](control-list-box.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)**und **[Umschalten](control-toggle.md)**.

**DelayOutput**: Wird auf „true“ festgelegt, um eine Aktion während der Texteingabe zu verzögern.

* Gilt für Steuerelemente des folgenden Typs: **[Texteingabe](control-text-input.md)** und **[Karte](control-card.md)**.

**DisplayMode**: Mögliche Werte sind **Edit, View** und **Disabled** (Bearbeiten, Anzeigen und Deaktiviert). Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).  Im Modus **View** (Anzeigen) zeigen Eingabesteuerelemente wie **[Texteingabe](control-text-input.md)**, **[Dropdown](control-drop-down.md)**, **[Datumsauswahl](control-date-picker.md)** lediglich den Textwert an, und es werden keine interaktiven Elemente oder Dekorationen gerendert.  Dadurch sind sie für die Anzeige in Formularen oder als lesbare Ausgabe geeignet.

* Gilt für Steuerelemente des folgenden Typs: **[Bild hinzufügen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Schaltfläche](control-button.md)**, **[Kamera](control-camera.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Säulendiagramm](control-column-line-chart.md)**, **[Datumsauswahl](control-date-picker.md)**, **[Dropdown](control-drop-down.md)**, **[Export](control-export-import.md)**, **[Katalog](control-gallery.md)**, **[HTML-Text](control-html-text.md)**, **[Symbol](control-shapes-icons.md)**, **[Bild](control-image.md)**, **[Import](control-export-import.md)**, **[Bezeichnung](control-text-box.md)**, **[Liniendiagramm](control-column-line-chart.md)**, **[Listenfeld](control-list-box.md)**, **[Mikrofon](control-microphone.md)**, **[PDF-Viewer](control-pdf-viewer.md)**, **[Stifteingabe](control-pen-input.md)**, **[Kreisdiagramm](control-pie-chart.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Form](control-shapes-icons.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)**, **[Timer](control-timer.md)**, **[Umschalten](control-toggle.md)** und **[Video](control-audio-video.md)**.

**Items**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

* Gilt für Steuerelemente des folgenden Typs: **[Säulendiagramm](control-column-line-chart.md)**, **[Dropdown](control-drop-down.md)**, **[Katalog](control-gallery.md)**, **[Liniendiagramm](control-column-line-chart.md)**, **[Listenfeld](control-list-box.md)**, **[Kreisdiagramm](control-pie-chart.md)** und **[Optionsfeld](control-radio.md)**.

**OnChange**: Gibt an, wie die App reagiert, wenn der Benutzer den Wert eines Steuerelements ändert (z.B. per Schieberegler).

* Gilt für Steuerelemente des folgenden Typs: **[Bild hinzufügen](control-add-picture.md)**, **[Dropdown](control-drop-down.md)**, **[Listenfeld](control-list-box.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)** und **[Umschalten](control-toggle.md)**.

**OnSelect**: Gibt an, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

* Gilt für Steuerelemente des folgenden Typs: **[Bild hinzufügen](control-add-picture.md)**, **[Schaltfläche](control-button.md)**, **[Kamera](control-camera.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Säulendiagramm](control-column-line-chart.md)**, **[Datumsauswahl](control-date-picker.md)**, **[Dropdown](control-drop-down.md)**, **[Export](control-export-import.md)**, **[HTML-Text](control-html-text.md)**, **[Symbol](control-shapes-icons.md)**, **[Bild](control-image.md)**, **[Import](control-export-import.md)**, **[Bezeichnung](control-text-box.md)**, **[Liniendiagramm](control-column-line-chart.md)**, **[Listenfeld](control-list-box.md)**, **[Mikrofon](control-microphone.md)**, **[PDF-Viewer](control-pdf-viewer.md)**, **[Stifteingabe](control-pen-input.md)**, **[Kreisdiagramm](control-pie-chart.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Form](control-shapes-icons.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)** ,**[Timer](control-timer.md)**  und **[Umschalten](control-toggle.md)**.

**Reset**: Gibt an, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.  Siehe auch die **[Reset](../functions/function-reset.md)**-Funktion.

* Gilt für Steuerelemente des folgenden Typs: **[Audio](control-audio-video.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Dropdown](control-drop-down.md)**, **[Listenfeld](control-list-box.md)**, **[Mikrofon](control-microphone.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)**, **[Timer](control-timer.md)**, **[Umschalten](control-toggle.md)** und **[Video](control-audio-video.md)**.

**Text**: Text, der in einem Steuerelement angezeigt wird oder von einem Benutzer in ein Steuerelement eingegeben wird.

* Gilt für Steuerelemente des folgenden Typs: **[Bild hinzufügen](control-add-picture.md)**, **[Schaltfläche](control-button.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Export](control-export-import.md)**, **[Import](control-export-import.md)**, **[Bezeichnung](control-text-box.md)**, **[Texteingabe](control-text-input.md)** und **[Timer](control-timer.md)**.

**QuickInfo**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

* Gilt für Steuerelemente des folgenden Typs: **[Audio](control-audio-video.md)**, **[Schaltfläche](control-button.md)**, **[Kamera](control-camera.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Dropdown](control-drop-down.md)**, **[HTML-Text](control-html-text.md)**, **[Bild](control-image.md)**, **[Bezeichnung](control-text-box.md)**, **[Listenfeld](control-list-box.md)**, **[Mikrofon](control-microphone.md)**, **[PDF-Viewer](control-pdf-viewer.md)**, **[Stifteingabe](control-pen-input.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)**, **[Timer](control-timer.md)**, **[Umschalten](control-toggle.md)** und **[Video](control-audio-video.md)**.

**Value**: Gibt den Wert des Eingabesteuerelements an.

* Gilt für Steuerelemente des folgenden Typs: **[Kontrollkästchen](control-check-box.md)**, **[Optionsfeld](control-radio.md)**, **[Schieberegler](control-slider.md)** und **[Umschalten](control-toggle.md)**.

**Visible**: Gibt an, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

* Gilt für Steuerelemente des folgenden Typs: **[Bild hinzufügen](control-add-picture.md)**, **[Audio](control-audio-video.md)**, **[Schaltfläche](control-button.md)**, **[Kamera](control-camera.md)**, **[Karte](control-card.md)**, **[Kontrollkästchen](control-check-box.md)**, **[Säulendiagramm](control-column-line-chart.md)**, **[Datumsauswahl](control-date-picker.md)**, **[Formular anzeigen](control-form-detail.md)**, **[Dropdown](control-drop-down.md)**, **[Formular bearbeiten](control-form-detail.md)**, **[Export](control-export-import.md)**, **[Katalog](control-gallery.md)**, **[HTML-Text](control-html-text.md)**, **[Symbol](control-shapes-icons.md)**, **[Bild](control-image.md)**, **[Import](control-export-import.md)**, **[Bezeichnung](control-text-box.md)**, **[Liniendiagramm](control-column-line-chart.md)**, **[Listenfeld](control-list-box.md)**, **[Mikrofon](control-microphone.md)**, **[PDF-Viewer](control-pdf-viewer.md)**, **[Stifteingabe](control-pen-input.md)**, **[Kreisdiagramm](control-pie-chart.md)**, **[Optionsfeld](control-radio.md)**, **[Bewertung](control-rating.md)**, **[Form](control-shapes-icons.md)**, **[Schieberegler](control-slider.md)**, **[Texteingabe](control-text-input.md)**, **[Timer](control-timer.md)**, **[Umschalten](control-toggle.md)** und **[Video](control-audio-video.md)**.


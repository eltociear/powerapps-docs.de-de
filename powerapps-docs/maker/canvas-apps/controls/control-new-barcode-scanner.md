---
title: 'Barcode-Scanner-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Barcode Scanner-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 56d8ca116b4b683d7096ef08f550dfa11c32d3c6
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986449"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>Barcode-Scanner-Steuerelement für Canvas-apps

Scannt Barcodes, QR-Codes und datenmatrixcodes auf einem Android-oder IOS-Gerät. Wird in einem Webbrowser nicht unterstützt.

## <a name="description"></a>Beschreibung

Das-Steuerelement öffnet einen nativen Scanner auf einem Android-oder IOS-Gerät. Der Scanner erkennt automatisch einen Barcode, einen QR-Code oder einen Datenmatrix Code, wenn er in der Ansicht angezeigt wird. Das-Steuerelement unterstützt das Scannen in einem Webbrowser nicht.

Das-Steuerelement unterstützt QR-Codes, datenmatrixcodes und diese Arten von Barcodes:

- UPC A
- UPC E
- EAN 8
- EAN 13
- CODE 39
- CODE 128
- ITF
- PDF 417

## <a name="key-properties"></a>Haupteigenschaften

**Value** – Output-Eigenschaft, die den Textwert des zuletzt überprüften Codes enthält.

**TextText** , der auf der Schaltfläche angezeigt wird, mit der der Scanner aktiviert wird.

**Onscan** – gibt an, wie eine APP reagiert, wenn ein Barcode erfolgreich gescannt wird.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**Flash lightenabled** : gibt an, ob die Taschenlampe beim Öffnen des Scanners automatisch aktiviert wird.

**[Height](properties-size-location.md)** – die Höhe der Schaltfläche, mit der der Scanner aktiviert wird.

**Preferfrontcamera** : gibt an, ob die Frontkamera, sofern verfügbar, für die Überprüfung verwendet wird.

**[Tooltip](properties-core.md)** : Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**Type** : der Typ des Codes, der in der zuletzt erfolgreichen Überprüfung erkannt wurde.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – die Breite der Schaltfläche, mit der der Scanner aktiviert wird.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
Die gleichen Richtlinien für das **[Schalt](control-button.md)** Flächen-Steuerelement gelten für das **Barcode Scanner** -Steuerelement, da es sich um eine Schaltfläche handelt, die den Scan

### <a name="visual-alternatives"></a>Visuelle Alternativen
* Der Barcode Scanner ist eine Schaltfläche, die das Scanergebnis nicht anzeigt. Es wird empfohlen, das Scanergebnis mit einem **[Label](control-text-box.md)** -Steuerelement anzuzeigen. Legen Sie die **[Text](properties-core.md)** -Eigenschaft der Bezeichnung auf die **value** -Eigenschaft des Barcode Scanners fest. Legen Sie die **[Live](properties-accessibility.md)** -Eigenschaft der Bezeichnung auf " **höflich** " fest, damit Benutzer mit Bildschirm Lesevorgängen über Änderungen benachrichtigt werden. Diese Änderung bewirkt, dass der überprüfte Wert unabhängig von der visuellen Funktion für alle zugänglich ist.

* Benutzer mit visuellen und Motor Behinderungen bevorzugen die Kamera möglicherweise nicht auf einen Barcode. Fügen Sie ggf. eine weitere Form der Eingabe hinzu, z. b. ein **[Text Eingabe](control-text-input.md)** -Steuerelement, damit Benutzer Barcodes eingeben können

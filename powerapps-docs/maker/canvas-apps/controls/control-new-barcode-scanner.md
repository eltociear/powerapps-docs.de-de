---
title: 'Barcodescanner Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Barcodescanner Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1e41ec8d228e62c22354d77777a8390bfd442f8c
ms.sourcegitcommit: 212d397284c431f5989dc7b39549e2fc170d447e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58491574"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>Barcodescanner Steuerelement für Canvas-apps

Scans-Barcodes, QR-Codes und Datenmatrix Codes auf einem Android- oder iOS-Gerät. In einem Webbrowser unterstützt nicht.

## <a name="description"></a>Beschreibung

Das Steuerelement wird geöffnet, einen native Scanner auf einem Android- oder iOS-Gerät. Der Scanner erkennt automatisch, einen Barcode, einen QR-Code oder eine Datenmatrix Code in der Ansicht. Das Steuerelement unterstützt nicht die Überprüfung in einem Webbrowser.

Das Steuerelement unterstützt QR-Codes Datenmatrix Codes und diese Arten von Barcodes:

- UPC A
- UPC E
- EAN 8
- EAN 13
- CODE 39
- CODE 128
- ITF
- PDF 417

## <a name="key-properties"></a>Haupteigenschaften

**Wert** – Ausgabe der Eigenschaft, die den Textwert des Codes enthält, die zuletzt überprüft wurde.

**Text** -Text, auf die Schaltfläche angezeigt wird, die die Überprüfung aktiviert.

**OnScan** : wie eine app reagiert, wenn Sie ein Barcode erfolgreich überprüft wird.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**FlashlightEnabled** –, ob die Taschenlampe automatisch aktiviert ist, wenn die Überprüfung geöffnet wird.

**[Höhe](properties-size-location.md)**  – die Höhe der Schaltfläche, die die Überprüfung aktiviert.

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**Typ** – der Typ des Codes, der bei der Überprüfung gefunden wurden, die zuletzt erfolgreich ausgeführt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Breite](properties-size-location.md)**  – die Breite der Schaltfläche, die die Überprüfung aktiviert.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit
Dieselben Richtlinien wie für die **[Schaltfläche](control-button.md)** Steuerelement gelten für die **Barcode-Scanner** steuern, da es sich um eine Schaltfläche handelt, die die Überprüfung wird gestartet.

### <a name="visual-alternatives"></a>Visuellen alternativen
* Der Barcodescanner ist eine Schaltfläche, die das Überprüfungsergebnis nicht angezeigt wird. Sollten Sie erwägen, die das Überprüfungsergebnis mit einem **[Bezeichnung](control-text-box.md)** Steuerelement. Legen Sie die Bezeichnung des **[Text](properties-core.md)** Eigenschaft des Barcodescanners **Wert** Eigenschaft. Legen Sie die Bezeichnung des **[Live](properties-accessibility.md)** Eigenschaft **Polite** , damit Benutzer der Sprachausgabe über Änderungen benachrichtigt werden. Diese Änderung wird den gescannten Wert für jedermann, unabhängig von visual Möglichkeit zugänglich.

* Benutzer, die mit visual und motor behinderungen möglicherweise nicht auf die Kamera zeigen Sie auf einen Barcode bevorzugen. Erwägen Sie eine andere Form der Eingabe, z. B. eine **[Texteingabe](control-text-input.md)** -Steuerelement, für den Benutzer zur Eingabe von Barcodes.

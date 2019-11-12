---
title: 'Steuerelement für das Barcode-Scanner: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispielen, über das Barcode Scanner-Steuerelement
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e80f34917bba942f85e141c382cf3b1caa5e6d44
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650749"
ms.PowerAppsDecimalTransform: true
---
# <a name="web-barcode-scanner-control-experimental-in-powerapps"></a>Steuerelement "Barcode-Scanner" (experimentell) in powerapps

Das ältere Barcode-Scan-Steuerelement, das veraltet ist, aber möglicherweise für das Scannen von Codes in einem Webbrowser nützlich ist.

## <a name="description"></a>Beschreibung

Das Steuerelement zeigt den Kamera Feed in der APP an, sodass Benutzer Barcodes auf allen Geräten überprüfen können. Das Steuerelement ist aufgrund schlechter Leistung veraltet, und das Steuerelement für die Steuerung mobiler **[Barcode](control-new-barcode-scanner.md)** ersetzt dieses Steuerelement.

## <a name="key-properties"></a>Haupteigenschaften

**barcode scanner** – Auf einem Gerät mit mehreren Barcodescannern die numerische ID des von der App verwendeten Barcodescanners.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**[AccessibleLabel](properties-accessibility.md)** : Bezeichnung für Sprachausgaben

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**ShowLiveBarcodeDetection**: legt fest, ob visuelle Anhaltpunkte dargestellt werden, um den Status der Barcodeerkennung zu ermitteln. Gelbe Rechtecke stellen die Bereiche dar, die untersucht werden. Eine grüne Linie, die durch das Rechteck geht, zeigt an, dass die Barcodeerkennung erfolgreich war.

**Stream** – Das automatisch entsprechend der **StreamRate**-Eigenschaft aktualisierte Bild.

**StreamRate** – Gibt an, wie oft das Bild in der **Stream**-Eigenschaft aktualisiert wird (in Millisekunden).  Dieser Wert kann zwischen 100 (einer Zehntelsekunde) und 3.600.000 (eine Stunde) liegen.

**Text**: Barcodewert, der vom Scanner zuletzt erkannt wurde.

**[QuickInfo](properties-core.md)** : Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen

[**Patch**( *DataSource*; *BaseRecord*; *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Beispiel

### <a name="add-photos-to-an-image-gallery-control"></a>Hinzufügen von Fotos zu einem Bildkatalog-Steuerelement

1. Fügen Sie ein **Barcodescanner**-Steuerelement hinzu, und benennen Sie es **Mybarcode scanner**.

    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?

1. Fügen Sie ein **Label** -Steuerelement hinzu, und legen Sie dessen Ausgabe auf die **Text** -Eigenschaft des Barcode Scanners fest.

1. Scannen Sie einen Barcode des unter " **Barcodetype** "-Eigenschaft festgelegten Typs.

    In der Bezeichnung wird der gescannte Barcode angezeigt.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="video-alternatives"></a>Videoalternativen

* Sie sollten eine **[Bezeichnung](control-text-box.md)** hinzufügen, deren **[Text](properties-core.md)** auf den **Text** des Barcodescanners festgelegt ist. Da der Barcodescanner nicht den ermittelten Barcodewert anzeigt, kann jeder Benutzer den Scanner verwenden und nicht nur Benutzer mit Sehbehinderung.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe

* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

    > [!NOTE]
  > Bildschirm Sprachausgaben werden ankündigen, wenn ein neuer Barcode gefunden wurde. Der Wert wird nicht angekündigt. Solange der Barcode in der Ansicht angezeigt wird, erinnern die Sprachausgabe den Benutzer alle fünf Sekunden darauf, dass derselbe Barcode immer noch identifiziert wird.

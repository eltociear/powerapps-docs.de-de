---
title: 'Barcodescanner-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, über das Barcodescanner-Steuerelement"
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
ms.openlocfilehash: c27a2319d74db9a50acff84e40ea7df83dc1c126
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="barcode-scanner-control-in-powerapps"></a>Barcodescanner-Steuerelement in PowerApps
Ein Steuerelement, mit dem der Benutzer mithilfe des Barcodescanners des Geräts Fotos aufnehmen kann.

## <a name="description"></a>Beschreibung
Wenn Sie dieses Steuerelement hinzufügen, kann der Benutzer eine Datenquelle mit einem oder mehreren Fotos vom aktuellen Ort, an dem die App ausgeführt wird, aktualisieren.

## <a name="key-properties"></a>Haupteigenschaften
**barcode scanner** – Auf einem Gerät mit mehreren Barcodescannern die numerische ID des von der App verwendeten Barcodescanners.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften
**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**Brightness** – Bestimmt die Helligkeit, die von einem Benutzer voraussichtlich im Bild wahrgenommen wird.

**Contrast** – Gibt an, wie leicht ähnliche Farben in einem Bild für den Benutzer voneinander zu unterscheiden sind.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**[OnSelect](properties-core.md)** – Legt fest, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

**OnStream** – Legt fest, wie die App reagiert, wenn die **Stream**-Eigenschaft aktualisiert wird.

**Photo** – Das Bild, das aufgenommen wird, wenn der Benutzer ein Foto macht.

**Stream** – Das automatisch entsprechend der **StreamRate**-Eigenschaft aktualisierte Bild.

**StreamRate** – Gibt an, wie oft das Bild in der **Stream**-Eigenschaft aktualisiert wird (in Millisekunden).  Dieser Wert kann zwischen 100 (einer Zehntelsekunde) und 3.600.000 (eine Stunde) liegen.

**[Tooltip](properties-core.md)** – Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**Zoom** – Der Prozentsatz, mit dem das Bild von einem Barcodescanner oder die Ansicht einer Datei in einem PDF-Viewer vergrößert wird.

## <a name="related-functions"></a>Verwandte Funktionen
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Beispiel
### <a name="add-photos-to-an-image-gallery-control"></a>Hinzufügen von Fotos zu einem Bildkatalog-Steuerelement
1. Fügen Sie ein **Barcodescanner**-Steuerelement hinzu, und benennen Sie es **Mybarcode scanner**.
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
2. Fügen Sie ein **Bezeichnung**-Steuerelement hinzu, und legen Sie dessen Ausgabe auf den Barcodewert fest.  
3. Scannen Sie einen Barcode des in der BarcodeType-Eigenschaft festgelegten Typs.
4. In der Bezeichnung wird der gescannte Barcode angezeigt.


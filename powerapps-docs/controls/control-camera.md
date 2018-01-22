---
title: 'Kamera-Steuerelement: Referenz | Microsoft-Dokumentation'
description: "Informationen, einschließlich Eigenschaften und Beispiele, über das Kamera-Steuerelement"
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
ms.openlocfilehash: a3a724ad42082962ec8aea4e616f1d75aa7299ec
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="camera-control-in-powerapps"></a>Kamera-Steuerelement in PowerApps
Ein Steuerelement, mit dem der Benutzer mithilfe der Kamera des Geräts Fotos aufnehmen kann.

## <a name="description"></a>Beschreibung
Wenn Sie dieses Steuerelement hinzufügen, kann der Benutzer eine Datenquelle mit einem oder mehreren Fotos vom aktuellen Ort, an dem die App ausgeführt wird, aktualisieren.

## <a name="key-properties"></a>Haupteigenschaften
**Camera** – Auf einem Gerät mit mehreren Kameras ist dies die ID der von der App verwendeten Kamera.

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

**[Tooltip](properties-core.md)**: Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**Zoom**: Der Prozentsatz, mit dem ein Bild einer Kamera vergrößert wird (oder die Ansicht einer Datei in einem PDF-Viewer).

## <a name="related-functions"></a>Verwandte Funktionen
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>Beispiel
### <a name="add-photos-to-an-image-gallery-control"></a>Hinzufügen von Fotos zu einem Bildkatalog-Steuerelement
1. Fügen Sie ein **Kamera**-Steuerelement hinzu, benennen Sie es **MyCamera**, und legen Sie dessen **[OnSelect](properties-core.md)**-Eigenschaft auf die folgende Formel fest:<br>
   **Collect(MyPix, MyCamera.Photo)**
   
    Möchten Sie wissen, wie Sie [ein Steuerelement hinzufügen, benennen und konfigurieren](../add-configure-controls.md)?
   
    Benötigen Sie weitere Informationen zur **[Collect](../functions/function-clear-collect-clearcollect.md)**-Funktion oder [anderen Funktionen](../formula-reference.md)?
2. Drücken Sie F5, und nehmen Sie dann ein Foto auf, indem Sie auf **MyCamera** klicken oder tippen.
3. Fügen Sie ein **[Bildkatalog](control-gallery.md)**-Steuerelement hinzu, und passen Sie dann die Größe des zugehörigen **[Bild](control-image.md)**-Steuerelements, seiner Vorlage und des **Bildkatalog**-Steuerelements so an, dass sie den Bildschirm ausfüllen.
4. Legen Sie die **[Items](properties-core.md)**-Eigenschaft des **Bildkatalog**-Steuerelements auf den folgenden Ausdruck fest:<br>**MyPix.Url**.
5. Legen Sie die **[Image](properties-visual.md)**-Eigenschaft des **Bild**-Steuerelements im Katalog auf den folgenden Ausdruck fest:<br>
   **ThisItem.Url**
   
    Das aufgenommene Foto wird im **Bildkatalog**-Steuerelement angezeigt.
6. Machen Sie beliebig viele Fotos, und drücken Sie dann ESC, um zum Standardarbeitsbereich zurückzukehren.
7. (optional) Legen Sie die **OnSelect**-Eigenschaft des **Bild**-Steuerelements im **Bildkatalog**-Steuerelement auf **Remove(MyPix, ThisItem)** fest, drücken Sie F5, und klicken oder tippen Sie dann auf ein Foto, um dieses zu entfernen.

Verwenden Sie die **[SaveData](../functions/function-savedata-loaddata.md)**-Funktion, um die Fotos lokal zu speichern, oder die **[Patch](../functions/function-patch.md)**-Funktion, um eine Datenquelle zu aktualisieren.


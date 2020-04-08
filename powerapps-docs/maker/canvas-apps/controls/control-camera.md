---
title: 'Kamera-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Kamera-Steuerelement
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/07/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 59c0f85dd71c9dc512e348d6d8ee9686d6945fa1
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871118"
---
# <a name="camera-control-in-power-apps"></a>Kamerasteuerelement in Power Apps

Ein Steuerelement, mit dem Benutzer mit der Kamera auf einem Gerät Bilder aufnehmen können.

## <a name="description"></a>Beschreibung

Verwenden Sie das **Kamera** Steuerelement, um Bilder mit der Kamera eines Geräts zu erfassen.  Das Gerät muss über eine Kamera verfügen, und der Benutzer muss die APP für die Verwendung der Kamera autorisieren. Das Kamera Steuerelement wird unterstützt, wenn es in einem Webbrowser ausgeführt wird.

Das zuletzt erfasste Bild steht über die **Photo** -Eigenschaft zur Verfügung. Mit dieser Eigenschaft können die Images wie folgt lauten:

- **Angezeigt mit dem Image-Steuerelement.** Verwenden Sie das [Image](control-image.md) -Steuerelement, um das erfasste Bild anzuzeigen. Weitere Informationen finden Sie in den [Beispielen](#examples).  
- **Temporär in eine Variable oder eine Auflistung einfügen.**  Verwenden Sie die Funktion " [Set](../functions/function-set.md) " oder " [Collect](../functions/function-clear-collect-clearcollect.md) " zum Speichern von Bildern in einer Variablen oder einer Sammlung.  Gehen Sie vorsichtig vor, wenn Sie mehrere Abbilder in einer Sammlung gleichzeitig mit eingeschränktem Arbeitsspeicher des Geräts verwenden. Verwenden Sie die Funktionen [SaveData](../functions/function-savedata-loaddata.md) und [LoadData](../functions/function-savedata-loaddata.md) , um Bilder in den lokalen Speicher auf dem Gerät und in [Offline Szenarien](../offline-apps.md)zu verschieben.
- **In einer Datenbank gespeichert.**  Verwenden Sie die [Patch](../functions/function-patch.md) -Funktion, um Bilder in einer Datenbank zu speichern.
- **Als Base64-codierte Text Zeichenfolge übertragen.**  Verwenden Sie die [JSON](../functions/function-json.md) -Funktion zum Base64-Codieren von Bildern.

Verwenden Sie die Eigenschaften " **Stream**", " **streamrate**" und " **OnStream** ", um Bilder automatisch auf einem Timer zu erfassen, z. b. das anpacken eines Bilds an eine Zeitverlaufs Sequenz.

Auf erfasste Medien wird durch einen Textzeichen folgen-URI verwiesen. Weitere Informationen finden Sie in der [Dokumentation zum Datentyp](../functions/data-types.md#uris-for-images-and-other-media).

Bilder, die vom Kamera Steuerelement generiert werden, sind in der Regel nicht vollständig in der Kamera. Wenn Sie Bilder mit vollständiger Auflösung benötigen, verwenden Sie das Steuerelement [Bild hinzufügen](control-add-picture.md) .

## <a name="key-properties"></a>Haupteigenschaften

**Availabledevices** – Tabelle der verfügbaren Kameras auf dem Gerät.

Die Tabelle enthält zwei Spalten: 
- *ID* -Nummer, die mit der **Kamera** -Eigenschaft verwendet werden soll 
- Der *Name* , der vom Gerät zur Identifizierung der Kamera bereitgestellt wird. Einige Plattformen können *vor* und *nach dem* Auffinden der Kamera enthalten.

*Hinweis*: nicht alle Geräte in der Tabelle sind möglicherweise in Ihrer APP verwendbar.  Dabei kann es sich um spezielle Treiber oder Anwendungen handeln, die für bestimmte Zwecke vorgesehen sind.  

**Kamera** – die numerische ID der zu verwendenden Kamera.  Hilfreich auf Geräten mit mehr als einer Kamera.  

**OnStream** – Legt fest, wie die App reagiert, wenn die **Stream**-Eigenschaft aktualisiert wird.

**Photo** – das Bild, das aufgezeichnet wird, wenn der Benutzer ein Bild annimmt. 

**Stream** – Das automatisch entsprechend der **StreamRate**-Eigenschaft aktualisierte Bild.

**StreamRate** – Gibt an, wie oft das Bild in der **Stream**-Eigenschaft aktualisiert wird (in Millisekunden). Dieser Wert kann zwischen 100 (einer Zehntelsekunde) und 3.600.000 (eine Stunde) liegen.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

[AccessibleLabel](properties-accessibility.md): Bezeichnung für Sprachausgaben. Sollte beschreiben, warum ein Bild aufgenommen werden soll.

[BorderColor](properties-color-border.md): Die Farbe des Rahmens eines Steuerelements.

[BorderStyle](properties-color-border.md): Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

[BorderThickness](properties-color-border.md): Die Linienstärke des Rahmens eines Steuerelements.

**Brightness** – Bestimmt die Helligkeit, die von einem Benutzer voraussichtlich im Bild wahrgenommen wird.

**Contrast** – Gibt an, wie leicht ähnliche Farben in einem Bild für den Benutzer voneinander zu unterscheiden sind.

[Display Mode](properties-core.md) – gibt an, ob das Steuerelement Benutzereingaben zulässt (**Edit**), nur Daten (**Ansicht**) anzeigt oder deaktiviert (**deaktiviert**) ist.

[Focusedbordercolor](properties-color-border.md) – die Farbe des Rahmens eines Steuer Elements, wenn sich das Steuerelement im Fokus befindet.

[Focusedborderdicke](properties-color-border.md) – die Stärke des Rahmens eines Steuer Elements, wenn sich das Steuerelement im Fokus befindet.

[Height](properties-size-location.md): Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

[OnSelect](properties-core.md): Gibt an, wie die App reagiert, wenn der Benutzer auf ein Steuerelement tippt oder klickt.

[TabIndex](properties-accessibility.md) – Reihenfolge der Tastaturnavigation im Vergleich zu anderen Steuerelementen.

[QuickInfo](properties-core.md): Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

[Visible](properties-core.md): Gibt an, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

[Width](properties-size-location.md): Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

[X](properties-size-location.md) – der Abstand zwischen dem linken Rand eines Steuer Elements und dem linken Rand des übergeordneten Containers oder Bildschirms.

[Y](properties-size-location.md) – der Abstand zwischen dem oberen Rand eines Steuer Elements und dem oberen Rand des übergeordneten Containers oder Bildschirms.

## <a name="examples"></a>Beispiele

Für diese Beispiele benötigen Sie ein Gerät mit einer Kamera. Verwenden Sie zum Testen Ihrer APP eine Web-Cam, auf die Sie über Ihren Browser zugreifen können. Oder indem Sie Ihre APP speichern und in ein IOS-oder Android-Gerät mit einer Kamera laden.

### <a name="simple-display-of-a-captured-picture"></a>Einfache Anzeige eines aufgezeichneten Bilds

1. [Fügen Sie](../add-configure-controls.md) ein **Kamera** Steuerelement hinzu.

1. Autorisieren Sie die APP für die Verwendung der Gerätekamera.

1. Fügen Sie ein [**Bild**](../controls/control-image.md) Steuerelement hinzu.

1. Legen Sie die **Image** -Eigenschaft des **Image** -Steuer Elements auf die folgende Formel fest:

    ```powerapps-dot
    Camera1.Photo
    ```

    > [!NOTE]
    > Ersetzen Sie den Kamera-Steuerelement Namen *Camera1* nach Bedarf.

1. Drücken Sie F5, um die app in der Vorschau anzuzeigen.

1. Wählen Sie das Kamera Steuerelement aus, oder tippen Sie auf das Steuerelement. Das Ergebnis sollte im Image-Steuerelement angezeigt werden.

### <a name="add-pictures-to-an-image-gallery-control"></a>Hinzufügen von Bildern zu einem Bildkatalog-Steuerelement

1. Fügen Sie ein **Kamera** Steuerelement hinzu, benennen Sie es **MyCamera**, und legen Sie dessen [onselect](properties-core.md) -Eigenschaft auf diese Formel fest:

    ```powerapps-dot
    Collect( MyPix, MyCamera.Photo )
    ```

    Weitere Informationen:

    - [Vorgehensweise beim Hinzufügen, benennen und Konfigurieren eines Steuer Elements](../add-configure-controls.md)
    - Erfahren Sie mehr über die [Collect](../functions/function-clear-collect-clearcollect.md) -Funktion oder [andere Funktionen](../formula-reference.md).

1. Drücken Sie F5, und wählen Sie dann ein Bild aus, indem Sie auf **MyCamera**klicken oder tippen.

1. Hinzufügen eines [vertikalen](control-gallery.md) Katalog-Steuer Elements. Und ändern Sie dann die Größe des [Image](control-image.md) -Steuer Elements, seiner Vorlage und des **Bild** Katalog-Steuer Elements, sodass es in den Bildschirm passt.

1. Legen Sie die [Items](properties-core.md) -Eigenschaft des **Bild** Katalog-Steuer Elements auf diese Formel fest:
 
    ```powerapps-dot
    MyPix
    ```

1. Legen Sie die [Image](properties-visual.md) -Eigenschaft des **Bild** -Steuer Elements im Katalog auf diese Formel fest:

    ```powerapps-dot   
    ThisItem.Url
    ```

    Das Bild, das Sie aufgerufen haben, wird im **Bild** Katalog-Steuerelement angezeigt.

1. Nehmen Sie beliebig viele Bilder an, und kehren Sie dann zum Standard Arbeitsbereich zurück, indem Sie ESC drücken.

1. optionale Legen **Sie die onselect** -Eigenschaft des **Bild** -Steuer Elements im **Bild** Katalog-Steuerelement auf die folgende Formel fest:

    ```powerapps-dot
    Remove( MyPix, ThisItem )
    ```

1. Drücken Sie F5, und wählen Sie dann ein Bild aus, um es zu entfernen.

Verwenden Sie die [SaveData](../functions/function-savedata-loaddata.md) -Funktion, um die Bilder lokal zu speichern, oder die [Patch](../functions/function-patch.md) -Funktion, um eine Datenquelle zu aktualisieren.

### <a name="change-the-active-camera-from-a-drop-down"></a>Ändern der aktiven Kamera aus einer Dropdown-Dropdown-

1. [Fügen Sie](../add-configure-controls.md) ein **Kamera** Steuerelement hinzu.

1. Autorisieren Sie die APP für die Verwendung der Gerätekamera.
    
1. [Fügen Sie](../add-configure-controls.md) ein [Dropdown](control-drop-down.md) -Steuerelement hinzu.

1. Legen Sie die **Elemente** der Dropdown Liste auf Folgendes fest:

    ```powerapps-dot
    Camera1.AvailableDevices
    ```

    > [!NOTE]
      > Ersetzen Sie den Kamera-Steuerelement Namen *Camera1* nach Bedarf.
    
1. Legen Sie die **Kamera** -Eigenschaft der Kamera auf fest: 

    ```powerapps-dot
    Dropdown1.Selected.Id
    ```

    > [!NOTE]
      > Ersetzen Sie den Namen des Dropdown-Steuer Elements *Dropdown1* nach Bedarf.

1. Drücken Sie F5, und wählen Sie dann ein Element aus der Dropdown Liste aus, um die Kamera zu ändern.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

Das Kamera Steuerelement zeigt den Kamera-Feed an und fungiert auch als Schaltfläche, die ein Bild annimmt. Daher gibt es ähnliche Barrierefreiheits Überlegungen wie bei Schaltflächen.

### <a name="video-alternatives"></a>Videoalternativen

Sie sollten eine alternative Eingabemöglichkeit für Benutzer hinzufügen, die eine Sehbehinderung haben. Fügen Sie z. b. [Bild hinzu](control-add-picture.md) , damit Benutzer ein Bild von Ihrem Gerät hochladen können.

### <a name="color-contrast"></a>Farbkontrast

Es muss ein angemessener Farbkontrast zwischen [focusedbordercolor](properties-color-border.md) und der äußeren Farbe bestehen.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe

[Accessiblelabel](properties-accessibility.md) muss vorhanden sein.

### <a name="keyboard-support"></a>Tastaturunterstützung

- [TabIndex](properties-accessibility.md) muss 0 (null) oder größer sein, damit Tastatur Benutzer dorthin navigieren können.

- Fokusindikatoren müssen deutlich sichtbar sein. Verwenden Sie [focusedbordercolor](properties-color-border.md) und [focusedborderdicke](properties-color-border.md) , um die Sichtbarkeit von Fokus Indikatoren zu aktualisieren.

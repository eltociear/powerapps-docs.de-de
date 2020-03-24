---
title: 'Mikrofon-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, zum Mikrofon-Steuerelement
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 353485baf6726314f6009c57838b3aa68d145fa0
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436753"
ms.PowerAppsDecimalTransform: true
---
# <a name="microphone-control-in-power-apps"></a>Mikrofon-Steuerelement in powerapps

Ein Steuerelement, mit dem App-Benutzer Sounds von Ihrem Gerät aufzeichnen können.

## <a name="description"></a>Beschreibung

Verwenden Sie das **Mikrofon** -Steuerelement, um Audiodaten mit dem Mikrofon eines Geräts zu erfassen.  Das Gerät muss über ein Mikrofon verfügen, und der Benutzer muss die APP für die Verwendung des Mikrofons autorisieren.  Das Mikrofon-Steuerelement wird unterstützt, wenn es in einem Webbrowser ausgeführt wird.  

Der zuletzt aufgezeichnete Audioclip ist über die **Audioeigenschaft** verfügbar. Mit dieser Eigenschaft kann aufgezeichnete Audiodaten wie folgt lauten:

- **Wiedergegeben mit dem Audiosteuerelement.**  Verwenden Sie das [Audiosteuerelement](control-audio-video.md) , um die Aufzeichnung zu lauschen. Weitere Informationen finden Sie in den [Beispielen](#examples).
- **Temporär in eine Variable oder eine Auflistung einfügen.**  Verwenden Sie die [Set](../functions/function-set.md) -oder [Collect](../functions/function-clear-collect-clearcollect.md) -Funktion, um Audioclips in einer Variablen oder einer Auflistung zu speichern.  Verwenden Sie mit eingeschränktem Arbeitsspeicher für Geräte gleichzeitig Vorsicht bei mehreren Audioclips in einer Sammlung.  Verwenden Sie die Funktionen [SaveData](../functions/function-savedata-loaddata.md) und [LoadData](../functions/function-savedata-loaddata.md) , um Audioclips in den lokalen Speicher auf dem Gerät und in [Offline Szenarien](../offline-apps.md)zu verschieben.
- **In einer Datenbank gespeichert.**  Verwenden Sie die [Patch](../functions/function-patch.md) -Funktion, um Audioclips in einer Datenbank zu speichern.
- **Als Base64-codierte Text Zeichenfolge übertragen.**  Verwenden Sie die [JSON](../functions/function-json.md) -Funktion, um Audioclips per Base64 zu codieren.

Format des aufgezeichneten Audioformats:

- *3GP-* Format für *Android*.
- *AAC* -Format für *IOS*.
- *OGG* -Format für *Webbrowser*.

Auf erfasste Medien wird durch einen Textzeichen folgen-URI verwiesen. Weitere Informationen finden Sie in der [Dokumentation zum Datentyp](../functions/data-types.md#uris-for-images-and-other-media).

## <a name="key-properties"></a>Haupteigenschaften

**Audioclip** – der Audioclip, der aufgezeichnet wird, wenn der Benutzer das Gerät des Geräts aufzeichnet. 

**MIC** – numerische ID des Mikrofons auf einem Gerät mit mehr als einem Mikrofon.

**OnStop**: gibt an, wie die App reagiert, wenn der Benutzer die Aufzeichnung mit einem Mikrofon-Steuerelement beendet.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

[AccessibleLabel](properties-accessibility.md): Bezeichnung für Sprachausgaben. Sollte den Zweck dieses Mikrofons beschreiben.

[BorderColor](properties-color-border.md): Die Farbe des Rahmens eines Steuerelements.

[BorderStyle](properties-color-border.md): Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

[BorderThickness](properties-color-border.md): Die Linienstärke des Rahmens eines Steuerelements.

[Color](properties-color-border.md): Die Farbe des Texts in einem Steuerelement.

[Display Mode](properties-core.md) – gibt an, ob das Steuerelement Benutzereingaben zulässt (**Edit**), nur Daten (**Ansicht**) anzeigt oder deaktiviert (**deaktiviert**) ist.

[Disabledbordercolor](properties-color-border.md) – die Farbe des Rahmens eines Steuer Elements, wenn die [Display Mode](properties-core.md) -Eigenschaft des Steuer Elements auf " **deaktiviert**" festgelegt ist.

[Disabledcolor](properties-color-border.md) – die Farbe des Texts in einem Steuerelement, wenn seine [Display Mode](properties-core.md) -Eigenschaft auf " **deaktiviert**" festgelegt ist.

[Disabledfill](properties-color-border.md) – die Hintergrundfarbe eines Steuer Elements, wenn dessen [Display Mode](properties-core.md) -Eigenschaft auf " **deaktiviert**" festgelegt ist.

[Fill](properties-color-border.md): Die Hintergrundfarbe eines Steuerelements.

[Focusedbordercolor](properties-color-border.md) – die Farbe des Rahmens eines Steuer Elements, wenn sich das Steuerelement im Fokus befindet.

[Focusedborderdicke](properties-color-border.md) – die Stärke des Rahmens eines Steuer Elements, wenn sich das Steuerelement im Fokus befindet.

[Height](properties-size-location.md): Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

[HoverBorderColor](properties-color-border.md): Die Rahmenfarbe eines Steuerelements, wenn der Benutzer den Mauszeiger auf das Steuerelement bewegt.

[HoverColor](properties-color-border.md): Die Farbe des Texts in einem Steuerelement, wenn der Benutzer mit der Maus darauf zeigt.

[HoverFill](properties-color-border.md): Die Hintergrundfarbe eines Steuerelements, wenn der Benutzer mit der Maus darauf zeigt.

[Image](properties-visual.md): Der Name des Bilds, das in einem Bild-, Audio- oder Mikrofon-Steuerelement angezeigt wird.

[ImagePosition](properties-visual.md): Die Position (**Fill**, **Fit**, **Stretch**, **Tile** oder **Center**) eines Bilds auf einem Bildschirm oder in einem Steuerelement, wenn die Größe nicht mit der Bildgröße identisch ist.

[Onselect](properties-core.md) – gibt an, wie die APP reagiert, wenn der Benutzer ein Steuerelement auswählt.

**OnStart**: gibt an, wie die App reagiert, wenn der Benutzer eine Aufzeichnung mit einem Steuerelement-Mikrofon beginnt.

[Pressedbordercolor](properties-color-border.md) – die Farbe des Rahmens eines Steuer Elements, wenn der Benutzer dieses Steuerelement auswählt.

[Pressedcolor](properties-color-border.md) – die Textfarbe in einem Steuerelement, wenn der Benutzer dieses Steuerelement auswählt.

[Pressedfill](properties-color-border.md) – die Hintergrundfarbe eines Steuer Elements, wenn der Benutzer dieses Steuerelement auswählt.

[Reset](properties-core.md): Gibt an, ob ein Steuerelement auf seinen Standardwert zurückgesetzt wird.

[TabIndex](properties-accessibility.md) – Reihenfolge der Tastaturnavigation im Vergleich zu anderen Steuerelementen.

[QuickInfo](properties-core.md): Erklärender Text, der angezeigt wird, wenn der Benutzer auf ein Steuerelement zeigt.

[Visible](properties-core.md): Gibt an, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

[Width](properties-size-location.md): Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

[X](properties-size-location.md) – der Abstand zwischen dem linken Rand eines Steuer Elements und dem linken Rand des übergeordneten Containers oder Bildschirms.

[Y](properties-size-location.md) – der Abstand zwischen dem oberen Rand eines Steuer Elements und dem oberen Rand des übergeordneten Containers oder Bildschirms.

## <a name="examples"></a>Beispiele

### <a name="simple-direct-playback"></a>Einfache direkte Wiedergabe

In diesem Beispiel verbinden wir direkt ein **Mikrofon** -Steuerelement mit einem **Audiosteuerelement** für die sofortige Wiedergabe:

1. [Fügen](../add-configure-controls.md) Sie Ihrer APP ein **Mikrofon** -Steuerelement hinzu.
1. Autorisieren Sie die APP zur Verwendung des Geräts, wenn Sie dazu aufgefordert werden.
1. Fügen Sie der APP ein **Audiosteuerelement** hinzu.
1. Legen Sie die **Media** -Eigenschaft des **audiosteuerelements** auf die folgende Formel fest:

    ```powerapps-comma
    Microphone1.Audio
    ```

    > [!NOTE]
    > Ersetzen Sie den Mikrofon-Steuerelement Namen *Microphone1* nach Bedarf.

1. Vorschau der App anzeigen.
1. Wählen Sie das **Mikrofon** -Steuerelement aus, um die Aufzeichnung
1. Sprechen Sie, um Audiodaten aufzuzeichnen.
1. Wählen Sie das **Mikrofon** Steuerelement erneut aus, um die Aufzeichnung zu beenden.
1. Wählen Sie das **Audiosteuerelement** aus, um die Aufzeichnung zu hören.  

### <a name="add-sounds-to-a-gallery-control"></a>Hinzufügen von Sounds zu einem Katalog-Steuerelement

In diesem Beispiel erstellen wir einen Katalog mit Audioclips, die in einer Sammlung gespeichert sind und einzeln für die Wiedergabe ausgewählt werden können:

1. [Fügen Sie](../add-configure-controls.md) ein **Mikrofon** Steuerelement hinzu.

1. Legen Sie mit der [Collect](../functions/function-clear-collect-clearcollect.md) -Funktion die **onstopeigenschaft** auf diese Formel fest:

    ```powerapps-comma
    Collect( MySounds; MyMic.Audio )
    ```

1. Fügen Sie **ein Katalog** -Steuerelement hinzu, verschieben Sie es unter **mymic**.

1. Legen Sie die [Items](properties-core.md) -Eigenschaft für den Katalog auf diese Formel fest:

    ```powerapps-comma
    MySounds
    ```

1. Fügen Sie in der Vorlage für das **benutzerdefinierte** Katalog Steuerelement ein [Audiosteuerelement](control-audio-video.md) hinzu.

1. Legen Sie die **Media** -Eigenschaft des audiosteuerelements auf diese Formel fest:

    ```powerapps-comma
    ThisItem.Url
    ```

1. Drücken Sie F5, um die app in der Vorschau anzuzeigen.

1. Wählen Sie **mymic** aus, um die Aufzeichnung zu starten, und klicken Sie dann erneut, um die Aufzeichnung zu starten

1. Wählen Sie im Katalog- **Steuerelement die Wiedergabe** Schaltfläche im **Audiosteuerelement** aus, um die Aufzeichnung wiederzugeben.

1. Fügen Sie beliebig viele Aufzeichnungen hinzu, und kehren Sie dann zum Standard Arbeitsbereich zurück, indem Sie die ESC-Taste drücken.

1. optionale Fügen Sie in der Vorlage **für das Katalog** -Steuerelement ein [Schalt](control-button.md) Flächen-Steuerelement hinzu.

1. Legen [Sie die onselect](properties-core.md) -Eigenschaft auf die folgende Formel fest:

    ```powerapps-comma
    Remove( MySounds; ThisItem )
    ```

1. Drücken Sie F5, und entfernen Sie dann eine Aufzeichnung, indem Sie das entsprechende **Schalt** Flächen-Steuerelement auswählen.

Verwenden Sie die [SaveData](../functions/function-savedata-loaddata.md) -Funktion, um die Aufzeichnungen lokal zu speichern, oder die [Patch](../functions/function-patch.md) -Funktion, um eine Datenquelle zu aktualisieren.

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

Die gleichen Richtlinien gelten für [Schalt](control-button.md) Flächen, da **Mikrofon** nur eine spezialisierte Schaltfläche ist. Beachten Sie auch Folgendes:

### <a name="audio-alternatives"></a>Audioalternativen

Sie sollten eine alternative Eingabemöglichkeit für Benutzer hinzufügen, die eine Sprachbehinderung haben oder nicht über ein Mikrofon verfügen. Beispielsweise [Texteingabe](control-text-input.md) , damit Benutzer Text eingeben können.

### <a name="color-contrast"></a>Farbkontrast

- Lesen Sie die [Standardanforderungen für Farbkontraste](../accessible-apps-color.md).
- Stellen Sie sicher, dass der Farbkontrast zwischen [Bild](properties-visual.md) und Text und Symbol der Schaltfläche (falls zutreffend) angemessen ist.

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe

- [Accessiblelabel](properties-accessibility.md) muss vorhanden sein.

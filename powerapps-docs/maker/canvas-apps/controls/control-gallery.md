---
title: 'Bildkatalog-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Bildkatalog-Steuerelement
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/25/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba5df28f03ec5e7c9a3d8146aecb0427d8145b13
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61544244"
---
# <a name="gallery-control-in-canvas-apps"></a>Bildkatalog-Steuerelement in Canvas-apps

Ein Steuerelement, das andere Steuerelemente enthält und einen Datensatz anzeigt.

## <a name="description"></a>Beschreibung

Ein **Bildkatalog**-Steuerelement kann mehrere Datensätze aus einer Datenquelle darstellen. Jeder Datensatz kann mehrere Datentypen enthalten. Ein **Bildkatalog**-Steuerelement kann beispielsweise mehrere Kontakte darstellen, wobei jedes Element Kontaktdaten wie den Namen, eine Adresse und eine Telefonnummer umfasst. Jedes Datenfeld wird in einem eigenen Steuerelement innerhalb des **Bildkatalog**-Steuerelements angezeigt. Sie können diese Steuerelemente mithilfe dieser Vorlage konfigurieren. Die Vorlage wird im Bildkatalog als erstes Element angezeigt. Sie finden sie am linken Rand des **Bildkatalog**-Steuerelements (Querformat bzw. horizontale Ausrichtung) bzw. an der Oberseite des **Bildkatalog**-Steuerelements (Hochformat bzw. vertikale Ausrichtung). Änderungen an der Vorlage beziehen sich auf das **Bildkatalog**-Steuerelement insgesamt.

Vordefinierte Vorlagen für angezeigt, dass die Bilder und Texte in einem Katalog verfügbar sind, sowie einen Katalog für Elemente mit variabler Höhe.

## <a name="limitations"></a>Einschränkungen

Wenn ein Benutzer blättert die **Flexible Höhe** Katalog-Steuerelements, bevor alle Elemente geladen sind, wird das Element, die derzeit in Ansicht möglicherweise der Ansicht nach unten und außen verschoben, wenn der Datenladevorgang abgeschlossen ist. Um dieses Problem zu vermeiden, verwenden Sie einen Standard **Katalog** -Steuerelement statt der **Flexible Höhe** Variant-Wert.

## <a name="key-properties"></a>Haupteigenschaften

**[Default:](properties-core.md)** Das Element oder der Datensatz aus der Datenquelle, das bzw. der beim Starten der App im Katalog ausgewählt werden soll.

**[Items](properties-core.md)**: Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**Selected** – Das ausgewählte Element.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**[AccessibleLabel](properties-accessibility.md) ** – Bezeichnung des Katalogs (nicht den darin enthaltenen Elementen) für Sprachausgaben. Sollte die Elementliste beschreiben.

**AllItems** – Alle Elemente eines Katalogs, einschließlich zusätzlicher Steuerelementwerte, die Teil der Vorlage des Katalogs sind.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)**: Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**ItemAccessibleLabel** – Bezeichnung jedes Katalogelement für Sprachausgaben. Sollte beschreiben, was jedes Element ist.

**NavigationStep** – Gibt an, wie weit in einem Katalog gescrollt werden kann, wenn die **ShowNavigation**-Eigenschaft auf **true** festgelegt ist und der Benutzer am Ende des Katalogs jeweils einen Navigationspfeil verwendet.

**Auswählbare** : Legt fest, ob Katalogelemente ausgewählt werden können. Bei Festlegung auf **"true"**, Sprachausgabe Identifizieren der-Galerie als eine Liste auswählbarer und wählen Sie ein Element durch Klicken oder tippen. Bei Festlegung auf **"false"**, Sprachausgabe Identifizieren der-Galerie als eine normale Liste und klicken oder tippen auf ein Element nicht wählen Sie ihn.

**ShowNavigation** – Gibt an, ob in einem Katalog an beiden Enden ein Pfeil angezeigt wird, damit Benutzer durch die Elemente scrollen können, indem Sie auf einen Pfeil klicken oder tippen.

**ShowScrollbar** – Gibt an, ob eine Bildlaufleiste angezeigt wird, wenn Benutzer auf einen Katalog zeigen.

**Snap** – Gibt an, ob in einem Katalog ein automatischer Sprung zum nächsten vollständigen Element durchgeführt wird, wenn Benutzer durch den Katalog scrollen.

**TemplateFill** – Die Hintergrundfarbe eines Katalogs.

**TemplatePadding** – Der Abstand zwischen den Elementen eines Katalogs.

**TemplateSize** – Die Höhe der Vorlage für einen Katalog im Hochformat (vertikal) bzw. die Breite der Vorlage für einen Katalog im Querformat (horizontal).

**Transition** – Der visuelle Effekt (**Pop**, **Push** oder **None**), wenn Benutzer im Katalog auf ein Element zeigen.

**[Visible](properties-core.md)** – Legt fest, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

**[Width](properties-size-location.md)** – Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**WrapCount** – Die Anzahl der in einer Zeile oder Spalte angezeigten Elemente (je nachdem, ob ein horizontales oder vertikales Layout verwendet wird).

**[X](properties-size-location.md)** – Der Abstand zwischen dem linken Rand eines Steuerelements und dem linken Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

**[Y](properties-size-location.md)** – Der Abstand zwischen dem oberen Rand eines Steuerelements und dem oberen Rand des übergeordneten Containers (bzw. des Bildschirms, wenn kein übergeordneter Container vorhanden ist).

## <a name="related-functions"></a>Verwandte Funktionen

[**Filter**( *DataSource*, *Formula* )](../functions/function-filter-lookup.md)

## <a name="examples"></a>Beispiele

### <a name="show-and-filter-data"></a>Anzeigen und Filtern von Daten

* [Anzeigen von Text](control-text-box.md#show-data-in-a-gallery)
* [Anzeigen von Bildern](control-image.md#show-a-set-of-images-from-a-data-source)
* [Filtern von Daten mithilfe einer Listenoption](control-drop-down.md#example)
* [Filtern von Daten mithilfe eines Schiebereglers](control-slider.md#example)

### <a name="get-data-from-the-user"></a>Abrufen von Daten eines Benutzers

* [Abrufen von Text](control-text-input.md#collect-data)
* [Abrufen von Bildern](control-add-picture.md#add-images-to-an-image-gallery-control)
* [Abrufen von Fotos](control-camera.md#example)
* [Abrufen von Tönen](control-microphone.md#example)
* [Abrufen von Zeichnungen](control-pen-input.md#create-a-set-of-images)

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="color-contrast"></a>Farbkontrast

Wenn ein Katalogelement aktiviert wird, indem man auf eine beliebige Stelle klickt, muss zwischen den folgenden Elementen ein angemessener Farbkontrast vorhanden sein:

* Zwischen **[BorderColor](properties-color-border.md)** und der Farbe außerhalb des Katalogs, wenn es einen Rahmen gibt
* Zwischen **[Fill](properties-color-border.md)** und der Farbe außerhalb des Katalogs, wenn es keinen Rahmen gibt

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe

* **[AccessibleLabel](properties-accessibility.md)** muss vorhanden sein.

    > [!NOTE]
    > Die Sprachausgabe wird bei der Elemente im Katalog ändern. **AccessibleLabel** wird ebenfalls erwähnt. Dadurch wird die Meldung in einen Kontext gesetzt und hat eine noch wichtigere Funktion, wenn mehrere Kataloge gleichzeitig angezeigt werden.

* Wenn ein Katalogelement mehrere Steuerelemente enthält, verwenden Sie **ItemAccessibleLabel** um das Galerieelement Inhalt zusammenzufassen.

* Legen Sie den Wert der **Selectable** zu **"true"** sollen Benutzer ein Katalogelement auswählen. Andernfalls legen Sie diesen Wert auf **"false"**.

* Wenn ein Katalogelement mehrere Steuerelemente enthält, verwenden Sie **ItemAccessibleLabel** eine Zusammenfassung des Katalogs Inhalt des Elements angeben.

* **Auswählbare** sollte entsprechend festgelegt werden, je nachdem, ob Benutzer gedacht sind, um ein Katalogelement auszuwählen.

### <a name="keyboard-support"></a>Tastaturunterstützung

* Sie sollten **ShowScrollbar** auf **TRUE** festlegen. Auf den meisten Geräten mit Touchscreen wird die Scrollleiste erst angezeigt, wenn der Benutzer mit dem Scrollen beginnt.
* Wenn ein Katalogelement aktiviert wird, indem man auf eine beliebige Stelle klickt, muss es auch eine Möglichkeit für Tastaturbenutzer geben, dieses Katalogelement auszuwählen. Sie können z.B. eine **[Schaltfläche](control-button.md)** hinzufügen, für die die **OnSelect**-Eigenschaft auf **Select(Parent)** festgelegt ist.

    > [!NOTE]
  > Steuerelemente, die sich außerhalb des Katalogs befinden, werden nicht in der Reihenfolge der Tastaturnavigation innerhalb des Katalogs abgefragt. Die **[TabIndex](properties-accessibility.md)**-Eigenschaft von Steuerelementen innerhalb eines Katalogs ist eingeschränkt. Weitere Informationen finden Sie unter [Eigenschaften von Bedienungshilfen in PowerApps](properties-accessibility.md).

---
title: 'Bildkatalog-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Bildkatalog-Steuerelement
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/25/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a532af505e579e66d3dfa0dce22a1c3ac6a4a6cc
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650521"
---
# <a name="gallery-control-in-canvas-apps"></a>Katalog-Steuerelement in Canvas-apps

Ein Steuerelement, das andere Steuerelemente enthält und einen Datensatz anzeigt.

## <a name="description"></a>Beschreibung

Ein **Bildkatalog**-Steuerelement kann mehrere Datensätze aus einer Datenquelle darstellen. Jeder Datensatz kann mehrere Datentypen enthalten. Ein **Bildkatalog**-Steuerelement kann beispielsweise mehrere Kontakte darstellen, wobei jedes Element Kontaktdaten wie den Namen, eine Adresse und eine Telefonnummer umfasst. Jedes Datenfeld wird in einem eigenen Steuerelement innerhalb des **Bildkatalog**-Steuerelements angezeigt. Sie können diese Steuerelemente mithilfe dieser Vorlage konfigurieren. Die Vorlage wird im Bildkatalog als erstes Element angezeigt. Sie finden sie am linken Rand des **Bildkatalog**-Steuerelements (Querformat bzw. horizontale Ausrichtung) bzw. an der Oberseite des **Bildkatalog**-Steuerelements (Hochformat bzw. vertikale Ausrichtung). Änderungen an der Vorlage beziehen sich auf das **Bildkatalog**-Steuerelement insgesamt.

Es stehen vordefinierte Vorlagen zum Darstellen von Bildern und Text in einem Katalog zur Verfügung, sowie ein Katalog für Elemente mit variabler Höhe.

## <a name="limitations"></a>Einschränken

Wenn ein Benutzer einen Bildlauf zum **flexiblen Height** Gallery-Steuerelement durchführt, bevor alle Elemente geladen wurden, wird das aktuell in der Ansicht enthaltene Element möglicherweise nach unten und aus der Ansicht verschoben, wenn das Laden der Daten abgeschlossen ist. Um dieses Problem zu vermeiden, verwenden Sie ein Standard **Galerie** -Steuerelement anstelle der **flexiblen Höhen** Variante.

## <a name="key-properties"></a>Haupteigenschaften

**[Default:](properties-core.md)** Das Element oder der Datensatz aus der Datenquelle, das bzw. der beim Starten der App im Katalog ausgewählt werden soll.

**[Items](properties-core.md)** – Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**Selected**: Das ausgewählte Element.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

**[Accessiblelabel](properties-accessibility.md)** – Bezeichnung des Katalogs (nicht der darin enthaltenen Elemente) für Sprachausgaben. Sollte die Elementliste beschreiben.

**AllItems** – Alle Elemente eines Katalogs, einschließlich zusätzlicher Steuerelementwerte, die Teil der Vorlage des Katalogs sind.

**[BorderColor](properties-color-border.md)** – Die Farbe des Rahmens eines Steuerelements.

**[BorderStyle](properties-color-border.md)** – Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

**[BorderThickness](properties-color-border.md)** – Die Stärke des Rahmens eines Steuerelements.

**[DisplayMode](properties-core.md)** : Legt fest, ob das Steuerelement Benutzereingaben zulässt (**Edit**, Bearbeiten), ob nur Daten angezeigt werden (**View**, Anzeigen) oder ob das Steuerelement deaktiviert ist (**Disabled**, Deaktiviert).

**[Fill](properties-color-border.md)** – Die Hintergrundfarbe eines Steuerelements.

**[Height](properties-size-location.md)** – Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**Itemaccessiblelabel** – Bezeichnung der einzelnen Galerie Elemente für Bildschirm Sprachausgaben. Sollte die einzelnen Elemente beschreiben.

**NavigationStep** – Gibt an, wie weit in einem Katalog gescrollt werden kann, wenn die **ShowNavigation**-Eigenschaft auf **true** festgelegt ist und der Benutzer am Ende des Katalogs jeweils einen Navigationspfeil verwendet.

**Auswählbar** – gibt an, ob Galerie Elemente ausgewählt werden können. Wenn diese Option auf " **true**" festgelegt ist, wird der Katalog als auswählbare Liste identifiziert, und Sie können ein Element auswählen, indem Sie darauf klicken oder tippen. Wenn diese Option auf **false**festgelegt ist, wird der Katalog von den Sprachausgaben als reguläre Liste identifiziert, und durch Klicken oder tippen auf ein Element wird es nicht ausgewählt.

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
    > Bildschirm Sprachausgaben werden ankündigen, wenn sich Elemente im Katalog ändern. **AccessibleLabel** wird ebenfalls erwähnt. Dadurch wird die Meldung in einen Kontext gesetzt und hat eine noch wichtigere Funktion, wenn mehrere Kataloge gleichzeitig angezeigt werden.

* Wenn ein Galerie Element mehrere Steuerelemente enthält, verwenden Sie **itemaccessiblelabel** , um den Inhalt des Galerie Elements zusammenzufassen.

* Legen Sie den Wert **wählbar** auf **true** fest, wenn Sie möchten, dass Benutzer ein Galerie Element auswählen. Andernfalls legen Sie diesen Wert auf **false**fest.

* Wenn ein Galerie Element mehrere Steuerelemente enthält, verwenden Sie **itemaccessiblelabel** , um eine Zusammenfassung der Inhalte des Galerie Elements bereitzustellen.

* **Auswählbar** sollte entsprechend festgelegt werden, abhängig davon, ob Benutzer ein Galerie Element auswählen sollen.

### <a name="keyboard-support"></a>Tastaturunterstützung

* Sie sollten **ShowScrollbar** auf **TRUE** festlegen. Auf den meisten Geräten mit Touchscreen wird die Scrollleiste erst angezeigt, wenn der Benutzer mit dem Scrollen beginnt.
* Wenn ein Katalogelement aktiviert wird, indem man auf eine beliebige Stelle klickt, muss es auch eine Möglichkeit für Tastaturbenutzer geben, dieses Katalogelement auszuwählen. Sie können z.B. eine **[Schaltfläche](control-button.md)** hinzufügen, für die die **OnSelect**-Eigenschaft auf **Select(Parent)** festgelegt ist.

    > [!NOTE]
  > Steuerelemente, die sich außerhalb des Katalogs befinden, werden nicht in der Reihenfolge der Tastaturnavigation innerhalb des Katalogs abgefragt. Die **[TabIndex](properties-accessibility.md)** -Eigenschaft von Steuerelementen innerhalb eines Katalogs ist eingeschränkt. Weitere Informationen finden Sie unter [Eigenschaften von Bedienungshilfen in PowerApps](properties-accessibility.md).

---
title: 'Bildkatalog-Steuerelement: Referenz | Microsoft-Dokumentation'
description: Informationen, einschließlich Eigenschaften und Beispiele, über das Bildkatalog-Steuerelement
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
ms.openlocfilehash: ca48ccaf4aca72301d3a8b7f2eb79885d7c7cdf5
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80871325"
---
# <a name="gallery-control-in-canvas-apps"></a>Katalog-Steuerelement in Canvas-apps

Ein Steuerelement, das andere Steuerelemente enthält und einen Datensatz anzeigt.

## <a name="description"></a>Beschreibung

Ein **Bildkatalog**-Steuerelement kann mehrere Datensätze aus einer Datenquelle darstellen. Jeder Datensatz kann mehrere Datentypen enthalten. Verwenden Sie z. b **. ein Katalog** -Steuerelement, um mehrere Kontakte anzuzeigen, wobei jedes Element Kontaktinformationen anzeigt, die einen Namen, eine Adresse und eine Telefonnummer für jeden Kontakt enthalten.

Jedes Datenfeld wird in einem **separaten Steuerelement innerhalb des Katalog** -Steuer Elements angezeigt. Und Sie können diese Steuerelemente in der Vorlage konfigurieren. Die Vorlage wird als erstes Element in der Galerie angezeigt:

- Am linken **Rand eines Katalog-Steuer Elements** im horizontalen/Querformat.
- Und oben **in einem Katalog** -Steuerelement in vertikaler/Hochformat-Ausrichtung. 

Änderungen an der Vorlage beziehen sich auf das **Bildkatalog**-Steuerelement insgesamt.

Es stehen vordefinierte Vorlagen zum Darstellen von Bildern und Text in einem Katalog zur Verfügung, und es ist ein Katalog für Elemente mit variabler Höhe verfügbar.

## <a name="limitations"></a>Einschränkungen

Wenn ein Benutzer einen Bildlauf zum **flexiblen Height** Gallery-Steuerelement durchführt, bevor alle Elemente geladen wurden, wird das aktuell in der Ansicht enthaltene Element möglicherweise nach unten und aus der Ansicht verschoben, wenn das Laden der Daten abgeschlossen ist. Um dieses Problem zu vermeiden, verwenden Sie ein Standard **Galerie** -Steuerelement anstelle der **flexiblen Höhen** Variante.

## <a name="key-properties"></a>Haupteigenschaften

[Standard](properties-core.md) – das Element oder der Datensatz aus der Datenquelle, das beim Starten der APP im Katalog ausgewählt werden soll.

[Items](properties-core.md): Die Quelle der Daten, die in einem Steuerelement angezeigt werden, z.B. ein Katalog, eine Liste oder ein Diagramm.

**Selected**: Das ausgewählte Element.

## <a name="additional-properties"></a>Zusätzliche Eigenschaften

[Accessiblelabel](properties-accessibility.md) – Bezeichnung des Katalogs (nicht der darin enthaltenen Elemente) für Sprachausgaben. Sollte die Elementliste beschreiben.

**AllItems** – Alle Elemente eines Katalogs, einschließlich zusätzlicher Steuerelementwerte, die Teil der Vorlage des Katalogs sind.

[BorderColor](properties-color-border.md): Die Farbe des Rahmens eines Steuerelements.

[BorderStyle](properties-color-border.md): Legt fest, ob der Rahmen eines Steuerelements **Solid** (Durchgehend), **Dashed** (Gestrichelt), **Dotted** (Gepunktet) oder **None** (Keiner) ist.

[BorderThickness](properties-color-border.md): Die Linienstärke des Rahmens eines Steuerelements.

**Delta laden** : verzögert das Laden von Elementen (Zeilen), bis der Bildschirm zuerst geladen wird.

[Display Mode](properties-core.md) – gibt an, ob das Steuerelement Benutzereingaben zulässt (**Edit**), nur Daten (**Ansicht**) anzeigt oder deaktiviert (**deaktiviert**) ist.

[Fill](properties-color-border.md): Die Hintergrundfarbe eines Steuerelements.

[Height](properties-size-location.md): Die Entfernung zwischen dem oberen und unteren Rand eines Steuerelements.

**Itemaccessiblelabel** – Bezeichnung der einzelnen Galerie Elemente für Bildschirm Sprachausgaben. Sollte die einzelnen Elemente beschreiben.

**Loadingspinner** (**keine**, Steuer **Elemente** oder **Daten**)-Wenn kein Wert angezeigt wird, wird Spinner nicht angezeigt. Wenn Steuerelemente | Daten, Spinner werden angezeigt, wenn ein renderdurchlauf auftritt, der zu sichtbaren leeren Zeilen führt.

**Loadingspinnercolor** : die Füllfarbe des Lade Spinners.  Default ist auf BorderColor festgelegt.

**NavigationStep** – Gibt an, wie weit in einem Katalog gescrollt werden kann, wenn die **ShowNavigation**-Eigenschaft auf **true** festgelegt ist und der Benutzer am Ende des Katalogs jeweils einen Navigationspfeil verwendet.

**Auswählbar** – gibt an, ob Galerie Elemente ausgewählt werden können. Wenn diese Einstellung auf " **true**" festgelegt ist, bezeichnen die Sprachausgabe den Katalog als auswählbare Liste Und wählen Sie ein Element aus, indem Sie es auswählen. Wenn diese Option auf " **false**" festgelegt ist, wird der Katalog von den Sprachausgaben als reguläre Liste identifiziert, und die Auswahl eines Elements wird nicht ausgewählt.

**Shownavigation** – gibt an, ob ein Pfeil an jedem Ende eines Katalogs angezeigt wird, damit Benutzer durch die Elemente im Katalog scrollen können, indem Sie einen Pfeil auswählen.

**ShowScrollbar** – Gibt an, ob eine Bildlaufleiste angezeigt wird, wenn Benutzer auf einen Katalog zeigen.

**Snap** – Gibt an, ob in einem Katalog ein automatischer Sprung zum nächsten vollständigen Element durchgeführt wird, wenn Benutzer durch den Katalog scrollen.

**TemplateFill** – Die Hintergrundfarbe eines Katalogs.

**TemplatePadding** – Der Abstand zwischen den Elementen eines Katalogs.

**Templatesize** – die Höhe der Vorlage für einen Katalog in vertikaler/Hochformat-Ausrichtung. Oder die Breite der Vorlage für einen Katalog im horizontalen/Querformat.

**Transition** – Der visuelle Effekt (**Pop**, **Push** oder **None**), wenn Benutzer im Katalog auf ein Element zeigen.

[Visible](properties-core.md): Gibt an, ob ein Steuerelement angezeigt wird oder ausgeblendet ist.

[Width](properties-size-location.md): Der Abstand zwischen dem linken und rechten Rand eines Steuerelements.

**WrapCount** – Die Anzahl der in einer Zeile oder Spalte angezeigten Elemente (je nachdem, ob ein horizontales oder vertikales Layout verwendet wird).

[X](properties-size-location.md) – der Abstand zwischen dem linken Rand eines Steuer Elements und dem linken Rand des übergeordneten Containers oder Bildschirms.

[Y](properties-size-location.md) – der Abstand zwischen dem oberen Rand eines Steuer Elements und dem oberen Rand des übergeordneten Containers oder Bildschirms.

## <a name="related-functions"></a>Ähnliche Funktionen

[Filter ( *DataSource*, *Formel* )](../functions/function-filter-lookup.md)

[Reset ( *Control* )](../functions/function-reset.md) : setzt Ihren Katalog auf den ursprünglichen Zustand zurück. Der Anfangszustand schließt den Bildlauf zum ersten Element ein und wählt das erste Element oder den Standardwert aus, falls vorhanden. 

  > [!NOTE]
  > Das Steuerelement **Zurücksetzen** setzt nicht alle untergeordneten Elemente des Katalogs rekursiv zurück.

## <a name="examples"></a>Beispiele

### <a name="show-and-filter-data"></a>Anzeigen und Filtern von Daten

- [Anzeigen von Text](control-text-box.md#show-data-in-a-gallery)
- [Anzeigen von Bildern](control-image.md#show-a-set-of-images-from-a-data-source)
- [Filtern von Daten mithilfe einer Listenoption](control-drop-down.md#example)
- [Filtern von Daten mithilfe eines Schiebereglers](control-slider.md#example)

### <a name="get-data-from-the-user"></a>Abrufen von Daten eines Benutzers

- [Abrufen von Text](control-text-input.md#collect-data)
- [Abrufen von Bildern](control-add-picture.md#add-images-to-an-image-gallery-control)
- [Abrufen von Fotos](control-camera.md#examples)
- [Abrufen von Tönen](control-microphone.md#examples)
- [Abrufen von Zeichnungen](control-pen-input.md#create-a-set-of-images)

## <a name="accessibility-guidelines"></a>Richtlinien für Barrierefreiheit

### <a name="color-contrast"></a>Farbkontrast

Wenn ein Katalogelement aktiviert wird, indem man auf eine beliebige Stelle klickt, muss zwischen den folgenden Elementen ein angemessener Farbkontrast vorhanden sein:

- [BorderColor](properties-color-border.md) und die Farbe außerhalb des Katalogs (wenn es einen Rahmen gibt).
- [Fill](properties-color-border.md) und die Farbe außerhalb des Katalogs (wenn es keinen Rahmen gibt).

### <a name="screen-reader-support"></a>Unterstützung der Sprachausgabe

- [Accessiblelabel](properties-accessibility.md) muss vorhanden sein.

    > [!NOTE]
    > Bildschirm Sprachausgaben werden ankündigen, wenn sich Elemente im Katalog ändern. **AccessibleLabel** wird ebenfalls erwähnt. Dadurch wird die Meldung in einen Kontext gesetzt und hat eine noch wichtigere Funktion, wenn mehrere Kataloge gleichzeitig angezeigt werden.

- Wenn ein Galerie Element mehrere Steuerelemente enthält, verwenden Sie **itemaccessiblelabel** , um den Inhalt der Galerie Elemente anzuzeigen.

- Legen Sie den Wert **wählbar** auf **true** fest, wenn Sie möchten, dass Benutzer ein Galerie Element auswählen. Andernfalls legen Sie diesen Wert auf **false**fest.

- Wenn ein Galerie Element mehrere Steuerelemente enthält, verwenden Sie **itemaccessiblelabel** , um eine Zusammenfassung der Inhalte des Galerie Elements bereitzustellen.

- **Auswählbar** sollte entsprechend festgelegt werden, abhängig davon, ob Benutzer ein Galerie Element auswählen sollen.

### <a name="keyboard-support"></a>Tastaturunterstützung

- Sie sollten **ShowScrollbar** auf **TRUE** festlegen. Auf den meisten Touchscreen-Geräten wird die Scrollleiste erst angezeigt, wenn der Bildlauf beginnt.
- Wenn ein Katalogelement aktiviert wird, indem man auf eine beliebige Stelle klickt, muss es auch eine Möglichkeit für Tastaturbenutzer geben, dieses Katalogelement auszuwählen. Beispielsweise können Sie eine [Schaltfläche](control-button.md) hinzufügen, deren **onselect** -Eigenschaft auf **Select (Parent)** festgelegt ist.

    > [!NOTE]
  > Steuerelemente, die sich außerhalb des Katalogs befinden, werden nicht in der Reihenfolge der Tastaturnavigation innerhalb des Katalogs abgefragt. [TabIndex](properties-accessibility.md) -Steuerelemente innerhalb eines Katalogs sind im Gültigkeitsbereich. Weitere Informationen finden Sie unter [Eigenschaften von Bedienungshilfen in PowerApps](properties-accessibility.md).

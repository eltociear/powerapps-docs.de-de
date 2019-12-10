---
title: Grundlegendes zu Tabellen in Canvas-Apps | Microsoft-Dokumentation
description: Referenzinformationen zum Arbeiten mit Canvas-App-Tabellen, Spalten und Datensätzen in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 777dd5452af8662569e2e51452142a1bbce3f619
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732850"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-canvas-app-tables-and-records-in-power-apps"></a>Grundlegendes zu Canvas-App-Tabellen und Datensätzen in powerapps

In powerapps können Sie eine Canvas-app erstellen, die auf Informationen in Microsoft Excel, SharePoint, SQL Server und mehreren anderen Quellen zugreift, die Daten in Datensätzen und Tabellen speichern. Um möglichst effizient mit diesen Daten umzugehen, machen Sie sich mit den Konzepten vertraut, die diesen Strukturen zugrunde liegen.

* Ein Datensatz enthält mindestens eine Kategorie von Informationen zu einer Person, einem Ort oder einem Gegenstand. Ein Datensatz kann z.B. den Namen, die E-Mail-Adresse und die Telefonnummer eines einzelnen Kunden enthalten. Andere Tools beziehen sich auf einen Datensatz als „Zeile“ oder „Element“.
* Eine Tabelle enthält mindestens einen Datensatz, der dieselben Informationskategorien enthält. Eine Tabelle kann z.B. die Namen, die E-Mail-Adressen und die Telefonnummern von 50 Kunden enthalten.

In der App verwenden Sie [Formeln](working-with-formulas.md) zum Erstellen, Aktualisieren und Bearbeiten von Datensätzen und Tabellen. Daten werden wahrscheinlich in eine externe [Datenquelle](working-with-data-sources.md) gelesen und geschrieben, und zwar in eine erweiterte Tabelle. Darüber hinaus können Sie eine oder mehrere interne Tabellen erstellen, die [Sammlungen](working-with-data-sources.md#collections) genannt werden.

Sie können eine Vielzahl von Formeln erstellen, die den Namen einer Tabelle als Argument annehmen, so wie eine Formel in Excel eine oder mehrere Zellbezüge als Argumente akzeptiert. Einige Formeln in Power Apps geben eine Tabelle zurück, die die anderen von Ihnen angegebenen Argumente widerspiegelt. Sie können beispielsweise eine Formel erstellen:

* einen Datensatz in einer Tabelle zu aktualisieren, indem Sie diese Tabelle als eines von mehreren Argumente für die **[Patch](functions/function-patch.md)** -Funktion angeben.
* Spalten in einer Tabelle hinzufügen, entfernen und umbenennen, indem Sie diese Tabelle als Argument für die Funktionen **[AddColumns](functions/function-table-shaping.md)** , **[DropColumns](functions/function-table-shaping.md)** oder **[RenameColumns](functions/function-table-shaping.md)** angeben. Keine dieser Funktionen verändert die ursprüngliche Tabelle. Stattdessen gibt die Funktion eine andere Tabelle auf Grundlage der anderen, von Ihnen angegebenen Argumente zurück.

## <a name="elements-of-a-table"></a>Elemente einer Tabelle
![](media/working-with-tables/elements-of-a-table.png)

### <a name="records"></a>Datensätze
Jeder Datensatz enthält mindestens eine Kategorie von Informationen zu einer Person, einem Ort oder einem Gegenstand. Im obigen Beispiel für jedes Produkt ein Datensatz (**Chocolate** (Schokolade), **Bread** (Brot) und **Water** (Wasser)) und eine Spalte für jede Informationskategorie vorhanden (**Price** (Preis), **Quantity on Hand** (Lagerbestand) und **Quantity on Order** (bestellte Menge)).

In einer Formel können Sie mit geschweiften Klammern auf einen Datensatz selbst, außerhalb eines Tabellenkontexts verweisen. Angenommen, der Datensatz **{ Name: "Strawberries"; Price: 7,99 }** (Name: "Erdbeeren", Preis: 7.99) ist nicht mit einer Tabelle verknüpft. Beachten Sie, dass die Feldnamen in diesem Beispiel, **Name** und **Price**, nicht in doppelte Anführungszeichen eingeschlossen sind.

### <a name="fields"></a>Felder
Ein Feld ist eine einzelne Information in einem Datensatz. Sie können diese Art von Feld als Wert in einer Spalte eines bestimmten Datensatzes visuell darstellen.

Wie mit einem Steuerelement verweisen Sie auf ein Feld, indem Sie den **.** - [Operator](functions/operators.md) auf einen Datensatz anwenden.  **First(Products).Name** gibt beispielsweise das Feld **Name** für den ersten Datensatz in der Tabelle **Products** (Produkte) zurück.

Ein Feld kann einen anderen Datensatz oder eine andere Tabelle enthalten, wie im Beispiel zur **[GroupBy](functions/function-groupby.md)** -Funktion dargestellt. Sie können beliebig viele Ebenen von Datensätzen und Tabellen verschachteln.

### <a name="columns"></a>Spalten
Eine Spalte bezieht sich auf das gleiche Feld für einen oder mehrere Datensätze in einer Tabelle. Im obigen Beispiel verfügt jedes Produkt über eine Preisfeld, und der Preis befindet sich für alle Produkte in der gleichen Spalte.  Die zuvor genannte Tabelle weist vier Spalten auf, deren Namen horizontal ganz oben dargestellt sind:

* **Name**
* **Price** (Preis)
* **Quantity on Hand** (Lagerbestand)
* **Quantity on Order** (Bestellte Menge)

Der Spaltenname spiegelt die Felder in dieser Spalte wider.

Alle Werte innerhalb einer Spalte gehören dem gleichen Datentyp an. Im obigen Beispiel enthält die Spalte „Quantity on Hand“ immer enthält eine Zahl wie „12 Einheiten“, niemals eine Zeichenfolge, für einen Datensatz.  Der Wert eines Felds kann auch *leer* sein.  

In anderen Tools können Spalten „Felder“ genannt werden.

> [!NOTE]
> Für SharePoint-und Excel-Datenquellen, die Spaltennamen mit Leerzeichen enthalten, ersetzt powerapps die Leerzeichen durch **"\_x0020\_"** . Beispielsweise wird **"Spalten Name"** in SharePoint oder Excel in powerapps als **"Column_x0020_Name"** angezeigt, wenn Sie im Datenlayout angezeigt oder in einer Formel verwendet werden.

### <a name="table"></a>Tabelle
Eine Tabelle umfasst mindestens einen Datensatz, jeder mit mehreren Feldern, die datensatzübergreifend konsistente Namen aufweisen.

Alle Tabellen, die in einer Datenquelle oder eine Sammlung gespeichert sind, haben einen Namen, den Sie dazu verwenden können, um auf die Tabelle zu verweisen und sie an Funktionen zu übergeben, die Tabellen als Argumente akzeptieren.  Tabellen können auch das Ergebnis einer Funktion oder eine Formel sein.

Sie können wie im folgenden Beispiel eine Tabelle in einer Formel ausdrücken, indem Sie die **[Table](functions/function-table.md)** -Funktion mit einer Reihe von Datensätzen verwenden, die Sie in geschweiften Klammern ausdrücken:

`Table( { Value: "Strawberry" }; { Value: "Vanilla" } )`

Sie können auch eine einspaltige Tabelle mit eckigen Klammern definieren.  Alternativ können Sie den obigen Ausdruck wie folgt schreiben:

`[ "Strawberry"; "Vanilla" ]`

## <a name="table-formulas"></a>Tabellenformeln
In Excel und powerapps verwenden Sie Formeln, um Zahlen und Text Zeichenfolgen auf ähnliche Weise zu bearbeiten:

* Geben Sie in Excel in Zelle **A1** einen Wert ein, z.B. **42**, und geben Sie dann in eine andere eine Formel, z.B. **A1+2**, ein, um den Wert **44** anzuzeigen.
* Legen Sie in powerapps die **[default](controls/properties-core.md)** -Eigenschaft von **Slider1** auf **42**fest, und legen Sie die **[Text](controls/properties-core.md)** -Eigenschaft einer Bezeichnung auf **Slider1. Value + 2** fest, um den Wert **44**anzuzeigen.

In beiden Fällen ändert sich der berechnete Wert automatisch, wenn die Werte der Argumente geändert werden (z.B. die Zahl in Zelle **A1** oder der Wert von **Slider1**).

Sie können Formeln auf ähnliche Weise verwenden, um auf Daten in Tabellen und Datensätzen zuzugreifen und diese zu bearbeiten. In einigen Formeln können Sie Tabellennamen wie **Min(Catalog; Price)** als Argumente verwenden, um den niedrigsten Wert in der Spalte **Price** der **Catalog**-Tabelle anzuzeigen. Andere Formeln stellen ganze Tabellen als Rückgabewerte bereit, wie z.B. **RenameColumns(Catalog; "Price"; "Cost")** , womit alle Datensätze aus der **Catalog**-Tabelle zurückgegeben werden, jedoch der Name der Spalte **Price** in **Cost** (Kosten) geändert wird.

Ebenso wie Zahlen, werden Formeln, die Tabellen und Datensätze enthalten, automatisch neu berechnet, wenn die zugrunde liegenden Tabelle oder der zugrunde liegende Datensatz geändert wird. Wenn die Kosten eines Produkts in die **Catalog**-Tabelle unter den vorherigen Mindestwert sinken, wird der Rückgabewert der **[Min](functions/function-aggregates.md)** -Formel automatisch geändert und angepasst.

Lassen Sie einige einfache Beispiele ansehen.

1. Erstellen Sie eine leere App für ein Smartphone, und fügen Sie ein vertikales **[Katalog](controls/control-gallery.md)** -Steuerelement hinzu, das andere Steuerelemente enthält.

    Es wird Platzhaltertext aus einer Tabelle namens **CustomGallerySample** angezeigt. Die **[Items](controls/properties-core.md)** -Eigenschaft des **[Katalog](controls/control-gallery.md)** -Steuerelements der Anzeige wird automatisch auf die Tabelle festgelegt.

    ![](media/working-with-tables/gallery-items.png)

    > [!NOTE]
    > Einige Steuerelemente wurden neu angeordnet und zur Veranschaulichung vergrößert.

2. Statt die **[Items](controls/properties-core.md)** -Eigenschaft auf den Namen einer Tabelle festzulegen, legen Sie sie auf eine Formel fest, die den Namen der Tabelle als Argument enthält, wie in diesem Beispiel:

    `Sort(CustomGallerySample; SampleHeading; Descending)`

    Diese Formel beinhaltet die **[Sort](functions/function-sort.md)** -Funktion, die den Namen einer Tabelle als erstes Argument und der Name einer Spalte in dieser Tabelle als zweites Argument akzeptiert. Die Funktion unterstützt auch ein optionales drittes Argument, das vorschreibt, dass die Daten in absteigender Reihenfolge sortiert werden sollen.

    ![](media/working-with-tables/gallery-items-sort.png)

3. Legen Sie die **[Items](controls/properties-core.md)** -Eigenschaft auf eine Formel fest, die die Formel aus dem vorherigen Schritt als Argument akzeptiert und eine Tabelle zurückgibt, wie im folgenden Beispiel:

    `FirstN(Sort(CustomGallerySample; SampleHeading; Descending); 2)`

    In dieser Formel verwenden Sie die Funktion **[FirstN](functions/function-first-last.md)** , um eine bestimmte Anzahl von Datensätzen in einer Tabelle anzuzeigen. Verwenden Sie die **[Sort](functions/function-sort.md)** -Funktion als erstes Argument für **[FirstN](functions/function-first-last.md)** und eine Zahl (in diesem Fall **2**) als das zweite Argument, das angibt, wie viele Datensätze angezeigt werden sollen.

    Die gesamte Formel gibt eine Tabelle zurück, die die ersten beiden Datensätze der **CustomGallerySample**-Tabelle enthält, sortiert nach der Spalte **SampleHeading** in absteigender Reihenfolge.

    ![](media/working-with-tables/gallery-items-sort-firstn.png)

## <a name="table-functions-and-control-properties"></a>Tabellenfunktionen und Steuerelementeigenschaften

Beachten Sie die **niedrigere** Funktion. Wenn die " **Welcome** "-Variable die Text Zeichenfolge **"Hello, World"** enthält, gibt die Formel " **Lower" (Willkommen)** **"Hello, World"** zurück.  Diese Funktion ändert in keiner Weise den Wert in der Variablen. **Lower** ist eine reine Funktion, da Sie nur Eingaben verarbeitet und die Ausgabe erzeugt. Das ist alles. Sie hat keine Nebenwirkungen. Alle Funktionen in Excel und die meisten Funktionen in Power apps sind reine Funktionen, die es ermöglichen, dass die Arbeitsmappe oder die APP automatisch neu berechnet wird.

Powerapps bietet eine Reihe von Funktionen, die auf Tabellen auf die gleiche Weise ausgeführt werden. Diese Funktionen nehmen Tabellen als Eingabe und Filtern, sortieren, transformieren, reduzieren und fassen ganze Datentabellen zusammen. In der Tat können **niedrigere** und viele andere Funktionen, die in der Regel einen einzelnen Wert verwenden, auch eine einspaltige Tabelle als Eingabe verwenden.

* **[Sort](functions/function-sort.md)** , **[Filter](functions/function-filter-lookup.md)** : sortieren und filtern Datensätze
* **[FirstN](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)** : geben die ersten N oder letzten N Datensätze einer Tabelle zurück
* **[Abs](functions/function-numericals.md)** , **[Sqrt](functions/function-numericals.md)** , **[Round](functions/function-round.md)** , **[RoundUp](functions/function-round.md)** , **[RoundDown](functions/function-round.md)** : arithmetische Vorgänge auf jeden Datensatz einer einspaltigen Tabelle mit einer einspaltigen Ergebnistabelle
* **[Left](functions/function-left-mid-right.md)** , **[Mid](functions/function-left-mid-right.md)** , **[Right](functions/function-left-mid-right.md)** , **[Replace](functions/function-replace-substitute.md)** , **[Substitute](functions/function-replace-substitute.md)** , **[Trim](functions/function-trim.md)** , **[Lower](functions/function-lower-upper-proper.md)** , **[Upper](functions/function-lower-upper-proper.md)** , **[Proper](functions/function-lower-upper-proper.md)** : Bearbeitung von Zeichenfolgen in jedem Datensatz einer einspaltigen Tabelle mit einer einspaltigen Ergebnistabelle aus Zeichenfolgen
* **[Len](functions/function-len.md)** : gibt für eine Spalte von Zeichenfolgen eine einspaltige Tabelle zurück, die die Länge einer jeden Zeichenfolge enthält.
* **[Concatenate](functions/function-concatenate.md)** : verkettet mehrere Zeichenfolgenspalten und ergibt eine einspaltige Tabelle mit Zeichenfolgen
* **[AddColumns](functions/function-table-shaping.md)** , **[DropColumns](functions/function-table-shaping.md)** , **[RenameColumns](functions/function-table-shaping.md)** , **[ShowColumns](functions/function-table-shaping.md)** : bearbeiten Spalten der Tabelle und ergeben eine neue Tabelle mit unterschiedlichen Spalten
* **[Distinct](functions/function-distinct.md)** : entfernt doppelte Datensätze
* **[Shuffle](functions/function-shuffle.md)** : mischt die Reihenfolge von Datensätze zufällig
* **[HashTags](functions/function-hashtags.md)** : sucht in einer Zeichenfolge nach Hashtags
* **[Error](functions/function-errors.md)** : stellt bei der Arbeit mit einer Datenquelle Fehlerinformationen bereit

Viele dieser Funktionen übernehmen eine einspaltige Tabelle als Eingabe. Wenn eine ganze Tabelle nur eine Spalte enthält, können Sie Sie anhand des Namens angeben. Wenn eine Tabelle über mehrere Spalten verfügt, können Sie eine dieser Spalten angeben, indem Sie die *Table. Column* -Syntax verwenden. **Products.Name** gibt beispielsweise die einspaltige Tabelle mit den **namens** Werten aus der **Products** -Tabelle zurück.

Sie können eine Tabelle mit der Funktion **[AddColumns](functions/function-table-shaping.md)** , **[renamecolumns](functions/function-table-shaping.md)** , **[showcolumns](functions/function-table-shaping.md)** oder **[dropcolumns](functions/function-table-shaping.md)** vollständig neu strukturieren. Diese Funktionen ändern nur Ihre Ausgabe, nicht Ihre Quelle.

Eigenschaften von Steuerelementen können auch Tabellen sein:

* **Items** : gilt für Galerien, Listenfelder und Kombinations Felder. Diese Eigenschaft definiert die Tabelle, die im Katalog oder in der Liste angezeigt wird.
* **SelectedItems** : gilt für Listenfelder und Kombinations Felder. Diese Eigenschaft definiert die Tabelle der Elemente, die der Benutzer ausgewählt hat, wenn **selectmultiple** aktiviert ist.

## <a name="behavioral-formulas"></a>Verhaltens Formeln

Andere Funktionen sind speziell zum Ändern von Daten und zum Auftreten von Nebeneffekten konzipiert. Da diese Funktionen nicht rein sind, müssen Sie Sie sorgfältig erstellen, und Sie können nicht an der automatischen Neuberechnung von Werten in der APP teilnehmen. Diese Funktionen können nur in [Verhaltens Formeln](working-with-formulas-in-depth.md)verwendet werden.

* **[Erfassen](functions/function-clear-collect-clearcollect.md)** , **[Löschen](functions/function-clear-collect-clearcollect.md)** und **[clearcollect](functions/function-clear-collect-clearcollect.md)** : erstellt Auflistungen, löscht sie und fügt ihnen Daten hinzu.
* **[Patch](functions/function-patch.md)** : ändert ein oder mehrere Felder in einem Datensatz.
* **[Update](functions/function-update-updateif.md)** , **[UpdateIf](functions/function-update-updateif.md)** : aktualisiert Datensätze, die mindestens einem von Ihnen angegebenen Kriterium entsprechen
* **[Remove](functions/function-remove-removeif.md)** , **[RemoveIf](functions/function-remove-removeif.md)** : löscht Datensätze, die mindestens einem von Ihnen angegebenen Kriterium entsprechen

## <a name="record-formulas"></a>Datensatzformeln

Sie können auch eine Formel erstellen, die Daten für einen einzelnen Datensatz berechnet, einen einzelnen Datensatz als Argument akzeptiert und einen einzelnen Datensatz als Rückgabewert bereitstellt. Lassen Sie uns zum Katalogbeispiel zurückkehren und die **Gallery1.Selected**-Eigenschaft zum Anzeigen von Informationen aus einem beliebigen Datensatz verwenden, den der Benutzer aus dem Katalog ausgewählt hat.

1. Fügen Sie eine [**Schaltfläche**](controls/control-button.md)hinzu, und legen Sie die **[onselect](controls/properties-core.md)** -Eigenschaft auf diese Formel fest:<br>
    **Collect( SelectedRecord; Gallery1.Selected )**

2. Halten Sie die ALT-TASTE gedrückt, und wählen Sie die Schaltfläche aus.

3. Klicken Sie im Menü **Datei** auf **Sammlungen**.

    ![](media/working-with-tables/selected-collection.png)

Diese Formel gibt einen Datensatz zurück, der nicht nur die Daten aus dem Datensatz enthält, die derzeit im Katalog ausgewählt ist, sondern auch jedes Steuerelement in diesem Katalog. Der Datensatz enthält z.B. sowohl eine **SampleText**-Spalte, die der **SampleText**-Spalte in der ursprünglichen Tabelle entspricht, als auch eine **Subtitle1**-Spalte, die die Bezeichnung darstellt, die die Daten aus dieser Spalte enthält. Wählen Sie das Tabellensymbol in der **Subtitle1**-Spalte aus, um diese Daten detaillierter zu analysieren.

> [!NOTE]
> Die Spalte **Subtitle1** kann z.B. **Subtitle2** genannt werden, wenn Sie andere Elemente als die in diesem Thema verwendeten hinzugefügt haben.

Da Sie nun über den ausgewählten Datensatz verfügen, können Sie mit dem **.** -Operator Operator

1. Fügen Sie ein **[Bezeichnung](controls/control-text-box.md)** -Steuerelement hinzu, und verschieben Sie es unter den Katalog und die Schaltfläche.

1. Legen Sie die **[Text](controls/properties-core.md)** -Eigenschaft auf den folgenden Ausdruck fest:<br>
    **"Selected: " & Gallery1.Selected.SampleHeading**

    ![](media/working-with-tables/gallery-selected.png)

Sie haben aus der **Selected**-Eigenschaft, die einen Datensatz darstellt, die **SampleHeading**-Eigenschaft extrahiert.

Sie können einen Datensatz auch als einen Allzweckcontainer für verwandte benannte Werte verwenden.

* Wenn Sie eine Formel um die Funktionen **[UpdateContext](functions/function-updatecontext.md)** und **[Navigate](functions/function-navigate.md)** erstellen, verwenden Sie einen Datensatz, um die [Kontextvariablen](working-with-variables.md#use-a-context-variable) zu erfassen, die Sie aktualisieren möchten.
* Wenden Sie die **[Updates](controls/control-form-detail.md)** -Eigenschaft auf ein **[Formular bearbeiten](controls/control-form-detail.md)** -Steuerelement an, um die Änderungen zu erfassen, die vom Benutzer in einem Formular vorgenommen wurden.
* Verwenden Sie die **[Patch](functions/function-patch.md)** -Funktion, um eine Datenquelle zu aktualisieren und um Datensätze zusammenführen.

In diesen Fällen war der Datensatz niemals Teil einer Tabelle.

## <a name="record-functions-and-control-properties"></a>Datensatzfunktionen und Steuerelementeigenschaften
Funktionen, die Datensätze zurückgeben:

* **[FirstN](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)** : geben den ersten oder letzten Datensatz oder Datensätze der Tabelle zurück
* **[Lookup](functions/function-filter-lookup.md)** : gibt den ersten Datensatz aus einer Tabelle zurück, die mindestens einem Kriterium entspricht
* **[Patch](functions/function-patch.md)** : aktualisiert eine Datenquelle oder führt Datensätze zusammen
* **[Defaults](functions/function-defaults.md)** : gibt die Standardwerte für eine Datenquelle zurück

Eigenschaften, die Datensätze zurückgeben:

* **Selected**: gilt für Kataloge und Listenfelder. Gibt den aktuell ausgewählten Datensatz zurück
* **Updates**: gilt für Kataloge.  Zieht allen Änderungen, die ein Benutzer in einem Dateneingabeformular vornimmt
* **[Update](functions/function-update-updateif.md)** : gilt für Eingabesteuerelemente wie Texteingabe-Steuerelemente und Schieberegler. Richtet einzelne, zusammenzustellende Eigenschaften für den Katalog ein

## <a name="record-scope"></a>Datensatzebene

Einige Funktionen werten eine Formel in allen Datensätzen einer Tabelle einzeln aus. Das Ergebnis der Formel wird auf verschiedene Weise verwendet:

* **AddColumns**: Die Formel stellt den Wert des hinzugefügten Felds bereit.
* **Average**, **Max**, **Min**, **Sum**, **StdevP**, **VarP**: Die Formeln stellen den zu aggregierenden Wert bereit.
* **Filter**, **Lookup**: Die Formel bestimmt, ob der Datensatz in die Ausgabe aufgenommen werden soll.
* **Concat**: Die Formel bestimmt die zu verkettenden Zeichenfolgen.
* **Distinct**: Die Formel gibt einen Wert zurück, mit dem doppelte Datensätze ermittelt werden können.
* **ForAll** : die Formel kann einen beliebigen Wert zurückgeben, möglicherweise mit Nebeneffekten.
* **Sort**: Die Formel stellt den Wert bereit, nach dem die Datensätze sortiert werden sollen.
* **With** -Formula kann einen beliebigen Wert zurückgeben, potenziell mit Nebeneffekten.

Innerhalb dieser Formeln können Sie auf die Felder des aktuell verarbeiteten Datensatzes verweisen. Jede dieser Funktionen erstellt eine „Datensatzebene“, in dem die Formel ausgewertet wird und in dem die Felder des Datensatzes als Bezeichner der obersten Ebene verfügbar sind. Sie können aus der gesamten App auch auf Steuerelementeigenschaften und andere Werte verweisen.

Nehmen Sie z.B. die Tabelle **Products**:

![](media/working-with-tables/requested.png)

Um diese Beispiel Tabelle in Ihrer APP zu erstellen, fügen Sie eine Schaltfläche ein, legen Sie die **onselect** -Eigenschaft auf diese Formel fest, und wählen Sie dann die Schaltfläche aus (Klicken Sie, während Sie die Alt-Taste in Power apps Studio gedrückt halten):

```powerapps-comma
Set( Products;
    Table(
        { Product: "Widget";    'Quantity Requested': 6;  'Quantity Available': 3 };
        { Product: "Gadget";    'Quantity Requested': 10; 'Quantity Available': 20 };
        { Product: "Gizmo";     'Quantity Requested': 4;  'Quantity Available': 11 };
        { Product: "Apparatus"; 'Quantity Requested': 7;  'Quantity Available': 6 }
    )
)
```

So bestimmen Sie, ob eines dieser Produkte mehr angefordert hat, als verfügbar ist:

`Filter( Products; 'Quantity Requested' > 'Quantity Available' )`

Das erste Argument für **Filter** ist die Tabelle von Datensätzen, die verarbeitet wird, und das zweite Argument ist eine Formel.  **Filter** erstellt eine Datensatzebene für die Auswertung dieser Formel, in dem die Felder jedes Datensatzes verfügbar sind, in diesem Fall **Product**, **Quantity Requested** (Nachgefragte Menge) und **Quantity Available** (verfügbare Menge).  Das Ergebnis des Vergleichs bestimmt, ob jeder Datensatz in das Ergebnis der Funktion aufgenommen werden soll:

![](media/working-with-tables/needed.png)

Außerdem können wir berechnen, wie viel von jedem Produkt bestellt werden soll:

```powerapps-comma
AddColumns( 
    Filter( Products; 'Quantity Requested' > 'Quantity Available' ); 
    "Quantity To Order"; 'Quantity Requested' - 'Quantity Available'
)
```

Hier wird dem Ergebnis eine berechnete Spalte hinzugefügt. **AddColumns** verfügt über eine eigene Datensatzebene, die zum Berechnen des Unterschiedes zwischen dem Angeforderten und dem Verfügbaren verwendet wird.

![](media/working-with-tables/toorder.png)

Schließlich können wir die Ergebnistabelle auf nur die gewünschten Spalten reduzieren:

```powerapps-comma
ShowColumns(
    AddColumns(
        Filter( Products; 'Quantity Requested' > 'Quantity Available' );
        "Quantity To Order"; 'Quantity Requested' - 'Quantity Available'
    );
    "Product";
    "Quantity To Order"
)
```

![](media/working-with-tables/toorderonly.png)

Beachten Sie, dass wir oben an einigen Stellen doppelte Anführungszeichen (") und an anderen einfache Anführungszeichen (') verwendet haben.  Einfache Anführungszeichen sind beim Verweisen auf den Wert eines Objekts wie ein Feld oder eine Tabelle erforderlich, wenn der Name des Objekts ein Leerzeichen enthält.  Doppelte Anführungszeichen werden verwendet, wenn nicht auf den Wert eines Objekts verweisen wird, sondern darüber gesprochen. Dies kommt vor allem dann vor, wenn das Objekt noch nicht vorhanden ist, wie bei **AddColumns**.

## <a name="disambiguation"></a>Mehrdeutigkeitsvermeidung

Feldnamen, die mit dem Datensatzbereich hinzugefügt werden, setzen die gleichen Namen von anderen Orten der App außer Kraft.  In diesem Fall können Sie weiterhin von außerhalb der Datensatzebene mithilfe des [ **@** -Operators zur Mehrdeutigkeitsvermeidung](functions/operators.md) auf Werte zugreifen:

* Verwenden Sie zum Zugreifen auf Werte aus geschachtelten Datensatzbereichen den **@** -Operator mit dem Namen der jeweiligen Tabelle, indem Sie das folgende Muster nutzen:<br>_Tabelle_ **[@** _Feldname_ **]**
* Verwenden Sie zum Zugreifen auf globale Werte, z.B. Datenquellen, Sammlungen und Kontextvariablen, das Muster **[@** _Objektname_ **]** (ohne Tabellenbezeichnung).

Wenn es sich bei der gerade verarbeiteten Tabelle um einen Ausdruck wie **Filter(** _Tabelle_ **,** ... **)** handelt, kann der Operator zur Mehrdeutigkeitsvermeidung nicht verwendet werden.  Nur die innerste Datensatzebene kann auf Felder aus diesem Tabellenausdruck zugreifen, indem der Operator zur Mehrdeutigkeitsvermeidung nicht verwendet wird.

Angenommen, Sie haben eine Sammlung **X**:

![](media/working-with-tables/X.png)

Sie können diese Sammlung mit **ClearCollect( Y; \["A"; "B"\] )** erstellen.

Und eine weitere Sammlung **Y**:

![](media/working-with-tables/Y.png)

Sie können diese Sammlung mit **ClearCollect( Y; ["A"; "B"] )** erstellen.

Definieren Sie darüber hinaus eine Kontextvariable namens **Value** mit dieser Formel: **UpdateContext( {Value: "!"} )** .

Lassen Sie uns alle Puzzleteile zusammensetzen. In diesem Kontext ergibt die folgende Formel:

```powerapps-comma
Ungroup(
    ForAll( X;
        ForAll( Y;
            Y[@Value] & Text( X[@Value] ) & [@Value]
        )
    );
    "Value"
)
```

die folgende Tabelle:

![](media/working-with-tables/XY.png)

Was ist hier passiert?  Die äußerste **ForAll**-Funktion definiert eine Datensatzebene für **X** und erlaubt den Zugriff auf das **Value**-Feld jedes Datensatzes während der Verarbeitung.  Der Zugriff erfolgt einfach mithilfe des Wortes **Value** oder mithilfe von **X[@Value]** .

Die innerste **ForAll** -Funktion definiert einen anderen Daten Satz Bereich für **Y**.  Da in dieser Tabelle auch ein **Wertfeld** definiert ist, verweist die Verwendung des **Werts** hier auf das Feld im Datensatz von **Y**und nicht mehr auf den Wert von **X**.  Für den Zugriff auf das **Wertfeld** von **X**müssen wir die längere Version mit dem Operator "disambiguations" verwenden.

Da **Y** die innerste Datensatzebene darstellt, ist beim Zugriff auf Felder dieser Tabelle keine Mehrdeutigkeitsvermeidung erforderlich. Die Verwendung dieser Formel erzielt daher dasselbe Ergebnis:

```powerapps-comma
Ungroup(
    ForAll( X;
        ForAll( Y;
            Value & Text( X[@Value] ) & [@Value]
        )
    );
    "Value"
)
```

Alle Datensatzebenen von **ForAll** sind dem globalen Bereich übergeordnet. Die von uns definierte **Wert** Kontext Variable ist ohne den mehrdeutigkeits Operator nicht nach Namen verfügbar. Verwenden Sie **[@Value]** , um auf diesen Wert zuzugreifen.

Gruppierung aufgruppierung vereinfacht das Ergebnis, da die gehosteten **ForAll** -Funktionen zu einer Tabelle mit einem Tabellen Ergebnis führen.

## <a name="single-column-tables"></a>Einspaltige Tabellen

Um mit einer einzelnen Spalte aus einer Tabelle zu arbeiten, verwenden Sie die Funktion **showcolumns** wie in diesem Beispiel:

```powerapps-comma
ShowColumns( Products; "Product" )
```

Diese Formel erzeugt eine einspaltige Tabelle:

![](media/working-with-tables/single-column.png)

Um eine kürzere Alternative zu erhalten, geben Sie *Table. Column*an, die die einspaltige Tabelle einer *Spalte* aus der *Tabelle*extrahiert. Diese Formel erzeugt beispielsweise genau das gleiche Ergebnis wie die Verwendung von **showcolumns**.

```powerapps-comma
Products.Product
```

## <a name="inline-records"></a>Inline Datensätze

Datensätze werden mit geschweiften Klammern ausgedrückt, die die Namen von Feldwerten enthalten.  Sie können den ersten Datensatz in der Tabelle am Anfang dieses Themas z.B. mit dieser Formel ausdrücken:

`{ Name: "Chocolate"; Price: 3,95; 'Quantity on Hand': 12; 'Quantity on Order': 10 }`

Sie können Formeln auch in andere Formeln einbetten, wie in diesem Beispiel gezeigt:

`{ Name: First(Products).Name; Price: First(Products).Price * 1,095 }`

Datensätze lassen sich auch schachteln, indem geschweifte Klammern geschachtelt werden, wie in diesem Beispiel gezeigt:

`{ 'Quantity': { 'OnHand': ThisItem.QuantOnHand; 'OnOrder': ThisItem.QuantOnOrder } }`

Schließen Sie jeden Spaltenname, die ein Sonderzeichen wie ein Leerzeichen oder einen Doppelpunkt enthält, in einfache Anführungszeichen ein.  Um ein einfaches Anführungszeichen in einem Spaltennamen zu verwenden, verdoppeln Sie es.

Beachten Sie, dass der Wert in der **Price**-Spalte kein Währungssymbol wie ein Dollarzeichen enthält. Die Formatierung wird angewendet, wenn der Wert angezeigt wird.  

## <a name="inline-tables"></a>Inline Tabellen
Mithilfe mit der **[Table](functions/function-table.md)** -Funktion und einem Satz von Datensätzen können Sie eine Tabelle erstellen. Die Tabelle zu Beginn dieses Themas lässt sich mit dieser Formel ausdrücken:

```powerapps-comma
Table( 
    { Name: "Chocolate"; Price: 3,95; 'Quantity on Hand': 12; 'Quantity on Order': 10 };
    { Name: "Bread"; Price: 4,95; 'Quantity on Hand': 34; 'Quantity on Order': 0 };
    { Name: "Water"; Price: 4,95; 'Quantity on Hand': 10; 'Quantity on Order': 0 } 
)
```

Sie können Tabellen auch schachteln:

```powerapps-comma
Table( 
    { Name: "Chocolate"; 
      'Quantity History': Table( { Quarter: "Q1"; OnHand: 10; OnOrder: 10 };
                                 { Quarter: "Q2"; OnHand: 18; OnOrder: 0 } ) 
    }
)
```

## <a name="inline-value-tables"></a>Inline Wert Tabellen
Sie können einspaltige Tabellen erstellen, indem Sie Werte in eckigen Klammern angeben. Die daraus resultierende Tabelle enthält eine einzelne Spalte namens **Value**.

`[ 1; 2; 3; 4 ]` entspricht z. b. `Table( { Value: 1 }; { Value: 2 }; { Value: 3 }; { Value: 4 } )` und gibt folgende Tabelle zurück:

![](media/working-with-tables/inline-table.png)


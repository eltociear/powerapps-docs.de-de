---
title: Funktionen „AddColumns“, „DropColumns“, „RenameColumns“ und „ShowColumns“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "AddColumns", "dropcolumns", "renamecolumns" und "showcolumns" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c60017202c398d7a7e73ea9ff3ccee2bd8835b42
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730043"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-power-apps"></a>Funktionen "AddColumns", "dropcolumns", "renamecolumns" und "showcolumns" in powerapps
Formen eine [Tabelle](../working-with-tables.md) durch Hinzufügen, Verwerfen, Umbenennen und Auswählen der [Spalten](../working-with-tables.md#columns)

## <a name="overview"></a>Übersicht
Diese Funktionen formen eine Tabelle, indem sie deren Spalten anpassen:

* Verringern Sie mehreren Spalten in einer Tabelle auf eine einige Spalte, um sie mit Funktionen wie **[Lower](function-lower-upper-proper.md)** oder **[Abs](function-numericals.md)** zu verwenden, die sich nur auf einzelne Spalten beziehen.  
* Fügen Sie einer Tabelle eine berechnete Spalte hinzu (z.B. die Spalte **Gesamtpreis**, die das Ergebnis der Multiplikation von **Quantität** und **Stückpreis** anzeigt).
* Geben Sie einer Spalte für die Benutzer oder die Verwendung in Formeln einen aussagekräftigeren Namen.

Eine Tabelle ist ein Wert in Power apps, wie z. b. eine Zeichenfolge oder eine Zahl.  Sie können eine Tabelle als Argument in einer Formel angeben, und Formeln können eine Tabelle als Ergebnis zurückgeben.

> [!NOTE]
> In den Funktionen, die in diesem Thema beschrieben werden, wird die ursprüngliche Tabelle nicht geändert. Stattdessen nehmen Sie diese Tabelle als Argument und geben eine neue Tabelle mit angewendeter Transformation zurück. Weitere Details erfahren Sie unter [Arbeiten mit Tabellen](../working-with-tables.md).  

Die Spalten einer [Datenquelle](../working-with-data-sources.md) können durch diese Funktionen nicht geändert werden. Daten müssen an ihrer Quelle geändert werden. Sie können einer [Sammlung](../working-with-data-sources.md#collections) mit der **[Collect](function-clear-collect-clearcollect.md)** -Funktion Spalten hinzufügen. Weitere Informationen finden Sie unter [Arbeiten mit Datenquellen](../working-with-data-sources.md).  

## <a name="description"></a>Beschreibung
Die Funktion **AddColumns** fügt einer Tabelle eine Spalte hinzu, und eine Formel definiert die Werte in dieser Spalte. Vorhandene Spalten bleiben unverändert.

Die Formel wird für jeden Datensatz der Tabelle ausgewertet.
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Die Funktion **DropColumns** schließt Spalten aus einer Tabelle aus.  Alle anderen Spalten bleiben unverändert. **DropColumns** schließt Spalten aus, und **ShowColumns** schließt Spalten ein.

Verwenden Sie die Funktion **RenameColumns**, um eine oder mehrere Spalten einer Tabelle mithilfe von mindestens einem Argumentpaar, das den Namen einer in der Tabelle enthaltenen Spalte (der alte Name, den Sie ersetzen möchten) und den Namen einer in der Tabelle nicht enthaltenen Spalte (der neue Name, den Sie verwenden möchten) angibt. Der alte Name muss bereits in der Tabelle vorhanden sein, und der neue Name darf noch nicht vorhanden sein. Jeder Spaltenname darf nur einmal in der Argumentliste angezeigt werden, entweder als alter Spaltenname oder als neuer Spaltenname. Um eine Spalte in eine vorhandene Spalte umzubenennen, verwerfen Sie zuerst die vorhandene Spalte mit einem Klick auf **DropColumns**, oder benennen Sie die vorhandene Spalte separat um, indem Sie eine Funktion **RenameColumns** innerhalb einer anderen schachteln.

Die Funktion **ShowColumns** schließt Spalten einer Tabelle ein und verwirft alle anderen Spalten. Sie können **ShowColumns** verwenden, um eine einspaltige Tabelle aus einer Tabelle mit mehreren Spalten zu erstellen.  **ShowColumns** schließt Spalten ein, und **DropColumns** schließt Spalten aus.  

Das Ergebnis all dieser Funktionen ist eine neue Tabelle mit angewendeter Transformation. Die ursprüngliche Tabelle wird nicht geändert. Eine vorhandene Tabelle kann nicht mit einer Formel geändert werden. SharePoint, Common Data Service, SQL Server und andere Datenquellen bieten Tools zum Ändern der Spalten von Listen, Entitäten und Tabellen, die häufig als Schema bezeichnet werden. Die Funktionen in diesem Thema transformieren nur eine Eingabe Tabelle, ohne den ursprünglichen in eine Ausgabe Tabelle zu ändern, um Sie weiter zu verwenden.

Die Argumente für diese Funktionen unterstützen die Delegierung. Eine **Filter** Funktion, die als Argument zum Abrufen verknüpfter Datensätze verwendet wird, durchsucht beispielsweise alle Auflistungen, auch wenn **"[dbo]. [ Allnotierungen] ' die** Datenquelle enthält eine Million Zeilen:

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

Die Ausgabe dieser Funktionen unterliegt jedoch dem [Grenzwert für nicht Delegierungs Datensätze](../delegation-overview.md#non-delegable-limits).  In diesem Beispiel werden nur 500-Datensätze zurückgegeben, auch wenn die **realestateagents** -Datenquelle über 501 oder mehr Datensätze verfügt.

Wenn Sie **AddColumns** auf diese Weise verwenden, muss der **Filter** separate Aufrufe an die Datenquelle für jeden dieser ersten Datensätze in **realestateagents**durchführen, wodurch viele netzwerkchatter verursacht werden. Wenn **[dbo]. [ Allcollect]** ist klein genug und ändert sich nicht häufig, Sie können die **Collect** -Funktion in [**OnStart**](signals.md#app) aufrufen, um die Datenquelle in der APP beim Start zwischenzuspeichern. Als Alternative können Sie Ihre APP so strukturieren, dass Sie die zugehörigen Datensätze nur dann abrufen, wenn Sie vom Benutzer angefordert werden.  

## <a name="syntax"></a>Syntax
**AddColumns**( *Tabelle*, *Spaltenname1*, *Formel1* [, *Spaltenname2*, *Formel2*, ... ] )

* *Table*: erforderlich.  Die zu verarbeitende Tabelle.
* *ColumnName(s)* : erforderlich. Name(n) der hinzuzufügenden Spalte(n).  Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)
* *Formel(n)* (erforderlich):  Die für jeden Datensatz der Tabelle auszuwertende(n) Formel(n). Das Ergebnis wird als der Wert der entsprechenden neuen Spalte hinzugefügt. Sie können in dieser Formel auf andere Spalten der Tabelle verweisen.

**DropColumns**( *Tabelle*, *Spaltenname1* [, *Spaltenname2*, ... ] )

* *Table*: erforderlich.  Die zu verarbeitende Tabelle.
* *ColumnName(s)* : erforderlich. Name(n) der zu verwerfenden Spalte(n). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)

**Renamecolumns**( *Table*, *OldColumnName1*, *NewColumnName1* [, *OldColumnName2*, *NewColumnName2*,...])

* *Table*: erforderlich.  Die zu verarbeitende Tabelle.
* *AlterSpaltenname*: erforderlich. Name einer umzubenennenden Spalte aus der ursprünglichen Tabelle. Dieses Element wird als erstes in dem Argumentpaar angezeigt (oder als erstes in jedem Argumentpaar, wenn die Formel mehr als ein Paar enthält). Der Name muss eine Zeichenfolge sein (z.B. **"Name"** in doppelten Anführungszeichen).
* *NeuerSpaltenname*: erforderlich. Der neue Name. Dieses Element wird als letztes in dem Argumentpaar angezeigt (oder als letztes in jedem Argumentpaar, wenn die Formel mehr als ein Paar enthält). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Customer Name"** (Kundenname) in doppelten Anführungszeichen).

**ShowColumns**( *Tabelle*, *Spaltenname1* [, *Spaltenname2*, ... ] )

* *Table*: erforderlich.  Die zu verarbeitende Tabelle.
* *ColumnName(s)* : erforderlich. Name(n) der einzuschließenden Spalte(n). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)

## <a name="examples"></a>Beispiele
In den Beispielen in diesem Abschnitt wird die Datenquelle **IceCreamSales** (Eiscremeverkäufe) verwendet, die die Daten in dieser Tabelle enthält:

![](media/function-table-shaping/icecream.png)

Keines dieser Beispiele verändert die Datenquelle **IceCreamSales**. Jede Funktion transformiert den Wert der Datenquelle in eine Tabelle und gibt den Wert als Ergebnis zurück.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )** |Fügt dem Ergebnis die Spalte **Revenue** (Umsatz) hinzu.  **UnitPrice * QuantitySold** (Stückpreis * verkaufte Menge) wird für jeden Datensatz ausgewertet, und das Ergebnis wird in die neue Spalte eingefügt. |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns( IceCreamSales, "UnitPrice" )** |Schließt die Spalte **UnitPrice** aus dem Ergebnis aus. Mit dieser Funktion können Spalten ausgeschlossen und mit **ShowColumns** eingeschlossen werden. |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, "Flavor" )** |Schließt nur die Spalte **Flavor** (Geschmack) im Resultset ein. Mithilfe dieser Funktion können Sie Spalten einschließen und mithilfe der Funktion **DropColumns** ausschließen. |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |Benennt die Spalte **UnitPrice** im Ergebnis um. |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |Benennt die Spalten **UnitPrice** und **QuantitySold** im Ergebnis um. |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |Führt der Reihe nach die folgenden Transformationen aus, beginnend im Kern der Formel: <ol><li>Fügt eine **Revenue**-Spalte basierend auf der Berechnung von **UnitPrice * Quantity** (Stückpreis * Menge) pro Datensatz hinzu.<li>Benennt **UnitPrice** in **Price** (Preis) um.<li>Schließt die Spalte **Quantity** aus.</ol>  Beachten Sie, dass diese Reihenfolge wichtig ist. Angenommen, **UnitPrice** kann nach der Umbenennung nicht berechnet werden. |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>Schritt für Schritt

Probieren wir einige Beispiele aus, die in diesem Thema erwähnt wurden.  

1. Erstellen Sie eine Sammlung, indem Sie ein **[Schalt](../controls/control-button.md)** Flächen-Steuerelement hinzufügen und dessen Eigenschaft **onselect** auf diese Formel festlegen:

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. Wenn Sie die Alt-Taste gedrückt halten, klicken Sie auf die Schaltfläche.

1. Fügen Sie ein zweites **Button** -Steuerelement hinzu, legen Sie dessen **onselect** -Eigenschaft auf diese Formel fest, und führen Sie es aus:

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. Wählen Sie im Menü **Datei** die Option **Sammlungen**aus, und wählen Sie dann **icecreamsales** aus, um diese Sammlung anzuzeigen.
 
    Wie diese Abbildung zeigt, hat die zweite Formel diese Auflistung nicht geändert. Die **AddColumns** -Funktion hat **icecreamsales** als Schreib geschütztes Argument verwendet. die-Funktion hat die Tabelle, auf die dieses Argument verweist, nicht geändert.
    
    ![Sammlungs-Viewer mit drei Datensätzen der Eiskrem Sales-Sammlung, die keine Umsatz Spalte enthält](media/function-table-shaping/ice-cream-sales-collection.png)

1. Wählen Sie **firstexample**aus.

    Wie diese Abbildung zeigt, hat die zweite Formel eine neue Tabelle mit der hinzugefügten Spalte zurückgegeben. Die **clearcollect** -Funktion hat die neue Tabelle in der **firstexample** -Auflistung aufgezeichnet und der ursprünglichen Tabelle etwas hinzugefügt, während Sie durch die Funktion fließt, ohne die Quelle zu ändern:

    ![Sammlungs Anzeige mit drei Datensätzen der ersten Beispiel Sammlung, die eine neue Umsatz Spalte enthält](media/function-table-shaping/first-example-collection.png)

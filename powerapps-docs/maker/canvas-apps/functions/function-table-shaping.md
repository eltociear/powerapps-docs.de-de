---
title: Funktionen „AddColumns“, „DropColumns“, „RenameColumns“ und „ShowColumns“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „AddColumns“, „DropColumns“, „RenameColumns“ und „ShowColumns“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/04/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fc682694bb22ecc63ecc762a735df07950ce29d3
ms.sourcegitcommit: f84095d964fe1fe5cc5290e5edbee284bd768e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096165"
---
# <a name="addcolumns-dropcolumns-renamecolumns-and-showcolumns-functions-in-powerapps"></a>Die Funktionen „AddColumns“, „DropColumns“, „RenameColumns“ und „ShowColumns“ in PowerApps
Formen eine [Tabelle](../working-with-tables.md) durch Hinzufügen, Verwerfen, Umbenennen und Auswählen der [Spalten](../working-with-tables.md#columns)

## <a name="overview"></a>Übersicht
Diese Funktionen formen eine Tabelle, indem sie deren Spalten anpassen:

* Verringern Sie mehreren Spalten in einer Tabelle auf eine einige Spalte, um sie mit Funktionen wie **[Lower](function-lower-upper-proper.md)** oder **[Abs](function-numericals.md)** zu verwenden, die sich nur auf einzelne Spalten beziehen.  
* Fügen Sie einer Tabelle eine berechnete Spalte hinzu (z.B. die Spalte **Gesamtpreis**, die das Ergebnis der Multiplikation von **Quantität** und **Stückpreis** anzeigt).
* Geben Sie einer Spalte für die Benutzer oder die Verwendung in Formeln einen aussagekräftigeren Namen.

Tabellen stellen in PowerApps einen Wert dar, genau wie Zeichenfolgen oder Zahlen.  Sie können eine Tabelle als Argument in einer Formel angeben, und Formeln können eine Tabelle als Ergebnis zurückgeben.

> [!NOTE]
> Die Funktionen, die in diesem Thema wird beschrieben, ändern Sie nicht die ursprüngliche Tabelle. Stattdessen nehmen diese Tabelle als Argument und geben Sie eine neue Tabelle mit einer angewendeten Transformation zurück. Weitere Details erfahren Sie unter [Arbeiten mit Tabellen](../working-with-tables.md).  

Die Spalten einer [Datenquelle](../working-with-data-sources.md) können durch diese Funktionen nicht geändert werden. Daten müssen an ihrer Quelle geändert werden. Sie können einer [Sammlung](../working-with-data-sources.md#collections) mit der **[Collect](function-clear-collect-clearcollect.md)** -Funktion Spalten hinzufügen. Weitere Informationen finden Sie unter [Arbeiten mit Datenquellen](../working-with-data-sources.md).  

## <a name="description"></a>Beschreibung
Die Funktion **AddColumns** fügt einer Tabelle eine Spalte hinzu, und eine Formel definiert die Werte in dieser Spalte. Vorhandene Spalten bleiben unverändert.

Die Formel wird für jeden Datensatz der Tabelle ausgewertet.
[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Die Funktion **DropColumns** schließt Spalten aus einer Tabelle aus.  Alle anderen Spalten bleiben unverändert. **DropColumns** schließt Spalten aus, und **ShowColumns** schließt Spalten ein.

Verwenden Sie die Funktion **RenameColumns**, um eine oder mehrere Spalten einer Tabelle mithilfe von mindestens einem Argumentpaar, das den Namen einer in der Tabelle enthaltenen Spalte (der alte Name, den Sie ersetzen möchten) und den Namen einer in der Tabelle nicht enthaltenen Spalte (der neue Name, den Sie verwenden möchten) angibt. Der alte Name muss bereits in der Tabelle vorhanden sein, und der neue Name darf noch nicht vorhanden sein. Jeder Spaltenname darf nur einmal in der Argumentliste angezeigt werden, entweder als alter Spaltenname oder als neuer Spaltenname. Um eine Spalte in eine vorhandene Spalte umzubenennen, verwerfen Sie zuerst die vorhandene Spalte mit einem Klick auf **DropColumns**, oder benennen Sie die vorhandene Spalte separat um, indem Sie eine Funktion **RenameColumns** innerhalb einer anderen schachteln.

Die Funktion **ShowColumns** schließt Spalten einer Tabelle ein und verwirft alle anderen Spalten. Sie können **ShowColumns** verwenden, um eine einspaltige Tabelle aus einer Tabelle mit mehreren Spalten zu erstellen.  **ShowColumns** schließt Spalten ein, und **DropColumns** schließt Spalten aus.  

Das Ergebnis all dieser Funktionen ist eine neue Tabelle mit angewendeter Transformation. Die ursprüngliche Tabelle wird nicht geändert. Sie können nicht auf eine vorhandene Tabelle mit einer Formel ändern. SharePoint, Common Data Service, SQL Server und anderen Datenquellen bieten Tools, ändern Sie die Spalten aufgelistet, Entitäten und Tabellen, die häufig als Schema bezeichnet werden. Die Funktionen in diesem Thema transformieren eine Eingabetabelle, nur ohne Änderung der ursprünglichen, in eine Ausgabetabelle zur weiteren Verwendung.

Die Argumente für diese Funktionen unterstützen die Delegierung. Z. B. eine **Filter** Funktion als Argument verwendet, um verknüpfte Datensätze durchsucht alle Angebote zu erhalten, wenn die **"[Dbo]. [ AllListings]'** Datenquelle enthält eine Million Zeilen:

```powerapps-dot
AddColumns( RealEstateAgents, 
    "Listings",  
    Filter(  '[dbo].[AllListings]', ListingAgentName = AgentName ) 
)
```

Die Ausgabe dieser Funktionen ist jedoch vorbehaltlich der [nicht Delegieren der Datensätze](../delegation-overview.md#non-delegable-limits).  In diesem Beispiel nur mit 500 Datensätze zurückgegeben werden, wenn die **RealEstateAgents** Datenquelle verfügt über mindestens 501 Datensätze.

Bei Verwendung von **AddColumns** auf diese Weise **Filter** müssen separate Aufrufe an die Datenquelle für die einzelnen in dieser ersten Datensätze, **RealEstateAgents**, wodurch viele Netzwerk-Chatter. Wenn **[Dbo]. [ AllListings]** ist klein genug, und ändert sich nicht häufig können Sie Aufrufen der **sammeln** -Funktion in [ **OnStart** ](signals.md#app) zum Zwischenspeichern von des Datenquelle in Ihrer app Wenn gestartet wurde. Als Alternative können Sie Ihrer app umstrukturieren, so, dass Sie nur, wenn der Benutzer auffordert, der sie die verknüpften Datensätze abzurufen.  

## <a name="syntax"></a>Syntax
**AddColumns**( *Tabelle*, *Spaltenname1*, *Formel1* [, *Spaltenname2*, *Formel2*, ... ] )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *ColumnName(s)*: erforderlich. Name(n) der hinzuzufügenden Spalte(n).  Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)
* *Formel(n)* (erforderlich):  Die für jeden Datensatz der Tabelle auszuwertende(n) Formel(n). Das Ergebnis wird als der Wert der entsprechenden neuen Spalte hinzugefügt. Sie können in dieser Formel auf andere Spalten der Tabelle verweisen.

**DropColumns**( *Tabelle*, *Spaltenname1* [, *Spaltenname2*, ... ] )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *ColumnName(s)*: erforderlich. Name(n) der zu verwerfenden Spalte(n). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)

**RenameColumns**( *Tabelle*, *OldColumnName1*, *NewColumnName1* [, *OldColumnName2*,  *NewColumnName2*,...])

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *AlterSpaltenname*: erforderlich. Name einer umzubenennenden Spalte aus der ursprünglichen Tabelle. Dieses Element wird als erstes in dem Argumentpaar angezeigt (oder als erstes in jedem Argumentpaar, wenn die Formel mehr als ein Paar enthält). Der Name muss eine Zeichenfolge sein (z.B. **"Name"** in doppelten Anführungszeichen).
* *NeuerSpaltenname*: erforderlich. Der neue Name. Dieses Element wird als letztes in dem Argumentpaar angezeigt (oder als letztes in jedem Argumentpaar, wenn die Formel mehr als ein Paar enthält). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Customer Name"** (Kundenname) in doppelten Anführungszeichen).

**ShowColumns**( *Tabelle*, *Spaltenname1* [, *Spaltenname2*, ... ] )

* *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
* *ColumnName(s)*: erforderlich. Name(n) der einzuschließenden Spalte(n). Sie müssen für dieses Argument eine Zeichenfolge angeben (z.B. **"Name"** in doppelten Anführungszeichen)

## <a name="examples"></a>Beispiele
In den Beispielen in diesem Abschnitt wird die Datenquelle **IceCreamSales** (Eiscremeverkäufe) verwendet, die die Daten in dieser Tabelle enthält:

![](media/function-table-shaping/icecream.png)

Keines dieser Beispiele verändert die Datenquelle **IceCreamSales**. Jede Funktion transformiert den Wert der Datenquelle in eine Tabelle und gibt den Wert als Ergebnis zurück.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )** |Fügt dem Ergebnis die Spalte **Revenue** (Umsatz) hinzu.  **UnitPrice * QuantitySold** (Stückpreis * verkaufte Menge) wird für jeden Datensatz ausgewertet, und das Ergebnis wird in die neue Spalte eingefügt. |<style> img { max-width: none; } </style> ![](media/function-table-shaping/icecream-add-revenue.png) |
| **DropColumns( IceCreamSales, "UnitPrice" )** |Schließt die Spalte **UnitPrice** aus dem Ergebnis aus. Mit dieser Funktion können Spalten ausgeschlossen und mit **ShowColumns** eingeschlossen werden. |![](media/function-table-shaping/icecream-drop-price.png) |
| **ShowColumns( IceCreamSales, "Flavor" )** |Schließt nur die Spalte **Flavor** (Geschmack) im Resultset ein. Mithilfe dieser Funktion können Sie Spalten einschließen und mithilfe der Funktion **DropColumns** ausschließen. |![](media/function-table-shaping/icecream-select-flavor.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price")** |Benennt die **UnitPrice** Spalte im Resultset. |![](media/function-table-shaping/icecream-rename-price.png) |
| **RenameColumns( IceCreamSales, "UnitPrice", "Price", "QuantitySold", "Number")** |Benennt die Spalten **UnitPrice** und **QuantitySold** im Ergebnis um. |![](media/function-table-shaping/icecream-rename-price-quant.png) |
| **DropColumns(<br>RenameColumns(<br>AddColumns( IceCreamSales, "Revenue",<br>UnitPrice * QuantitySold ),<br>"UnitPrice", "Price" ),<br>"Quantity" )** |Führt der Reihe nach die folgenden Transformationen aus, beginnend im Kern der Formel: <ol><li>Fügt eine **Revenue**-Spalte basierend auf der Berechnung von **UnitPrice * Quantity** (Stückpreis * Menge) pro Datensatz hinzu.<li>Benennt **UnitPrice** in **Price** (Preis) um.<li>Schließt die Spalte **Quantity** aus.</ol>  Beachten Sie, dass diese Reihenfolge wichtig ist. Angenommen, **UnitPrice** kann nach der Umbenennung nicht berechnet werden. |![](media/function-table-shaping/icecream-all-transforms.png) |

### <a name="step-by-step"></a>Schritt für Schritt

Probieren Sie einige Beispiele von weiter oben in diesem Thema.  

1. Erstellen Sie eine Sammlung durch Hinzufügen einer **[Schaltfläche](../controls/control-button.md)** Steuerelement und die Einstellung der **OnSelect** -Eigenschaft auf diese Formel:

    ```powerapps-dot
    ClearCollect( IceCreamSales, 
        Table(
            { Flavor: "Strawberry", UnitPrice: 1.99, QuantitySold: 20 }, 
            { Flavor: "Chocolate", UnitPrice: 2.99, QuantitySold: 45 },
            { Flavor: "Vanilla", UnitPrice: 1.50, QuantitySold: 35 }
        )
    )
    ```

1. Führen Sie die Formel, durch Auswählen der Schaltfläche, während Sie die Alt-Taste gedrückt halten.

1. Fügen Sie eine zweite **Schaltfläche** steuern, legen Sie dessen **OnSelect** -Eigenschaft auf diese Formel, und führen Sie es:

    ```powerapps-dot
    ClearCollect( FirstExample, 
        AddColumns( IceCreamSales, "Revenue", UnitPrice * QuantitySold )
    ) 
    ```
1. Auf der **Datei** , wählen Sie im Menü **Sammlungen**, und wählen Sie dann **IceCreamSales** um dieser Sammlung anzuzeigen.
 
    Wie die folgende Grafik zeigt, ändern nicht die zweite Formel dieser Sammlung. Die **AddColumns** verwendete Funktion **IceCreamSales** als nur-Lese Argument; nicht die Funktion ändern Sie die Tabelle, auf die dieses Argument verweist.
    
    ![Collection-Viewer, die mit drei Datensätze in der Auflistung, die eine Spalte Umsatz keine Eiskrem-Auftrag](media/function-table-shaping/ice-cream-sales-collection.png)

1. Wählen Sie **FirstExample**.

    Die zweite Formel zurückgegeben, wie die folgende Grafik zeigt, eine neue Tabelle mit die hinzugefügte Spalte. Die **ClearCollect** -Funktion erfasst die neue Tabelle in der **FirstExample** -Auflistung und fügt etwas an die ursprüngliche Tabelle, wie es durch die Funktion übergeben, ohne Änderung der Quelle:

    ![Collection-Viewer, die mit der ersten Beispiel-Auflistung, die eine neue Spalte für den Umsatz enthält drei Datensätze](media/function-table-shaping/first-example-collection.png)

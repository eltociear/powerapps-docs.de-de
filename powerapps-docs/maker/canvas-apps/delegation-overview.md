---
title: Grundlagen der Delegierung in einer Canvas-App | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe von Delegierung große Datasets effizient in einer Canvas-App verarbeiten.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/05/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1d98f01920dbcbf960b1e2bb21159586318e0386
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78403557"
ms.PowerAppsDecimalTransform: true
---
# <a name="understand-delegation-in-a-canvas-app"></a>Grundlagen der Delegierung in einer Canvas-App
Powerapps enthält eine Reihe leistungsfähiger Funktionen zum Filtern, Sortieren und Strukturieren von Tabellen von Daten in einer Canvas-App: die Funktionen " **[Filter](functions/function-filter-lookup.md)** ", " **[Sort](functions/function-sort.md)** " und " **[AddColumns](functions/function-table-shaping.md)** ", um nur ein paar zu benennen. Mit diesen Funktionen können Sie für Ihre Benutzer den genauen Zugriff auf die benötigten Informationen bereitstellen. Für Leser mit Datenbankkenntnissen: Die Verwendung dieser Funktionen entspricht dem Schreiben einer Datenbankabfrage.

Der Schlüssel zur Erstellung von effizienten Apps besteht darin, die Datenmenge gering zu halten, die auf Ihr Gerät übertragen werden muss. Unter Umständen benötigen Sie aus Millionen von Datensätzen nur eine Handvoll von Datensätzen, oder ein einzelner Aggregatwert kann für Tausende von Datensätzen stehen. Vielleicht ist es auch möglich, nur den ersten Satz mit Datensätzen abzurufen, und den Rest erst dann bereitzustellen, wenn er vom Benutzer angefordert wird. Wenn zielgerichtet vorgegangen wird, können die Verarbeitungsleistung, der Arbeitsspeicher und die Netzwerkbandbreite, die für die App erforderlich sind, deutlich gesenkt werden. Dies führt zu kürzeren Reaktionszeiten für Ihre Benutzer – sogar auf Smartphones, die über ein Mobilfunknetz verbunden sind. 

Die *Delegierung* von powerapps-Formeln erfüllt die Notwendigkeit, die Daten zu minimieren, die über das Netzwerk verschoben werden. In Kürze delegiert Power Apps die Verarbeitung von Daten an die Datenquelle, anstatt die Daten zur lokalen Verarbeitung in die APP zu verschieben.

Wenn dies kompliziert wird und der Grund für diesen Artikel ist, liegt es daran, dass nicht alles, was in einer powerapps-Formel ausgedrückt werden kann, an jede Datenquelle delegiert werden kann. Die powerapps-Sprache imitiert die Formelsprache von Excel, die mit vollständigem und sofortigem Zugriff auf eine vollständige Arbeitsmappe im Arbeitsspeicher entwickelt wurde und über eine Vielzahl von numerischen und Text Bearbeitungsfunktionen verfügt. Folglich ist die Sprache von Power apps weitaus umfangreicher als die meisten Datenquellen unterstützen können, einschließlich leistungsfähiger Daten Bank Module wie SQL Server.

**Zum Verwenden von großen Datasets ist die Nutzung von Datenquellen und Formeln erforderlich, für die eine Delegierung möglich ist.** Nur auf diese Weise erzielen Sie für Ihre App eine gute Leistung und können sicherstellen, dass die Benutzer auf alle benötigten Informationen zugreifen können. Achten Sie auf Delegierungswarnungen, die anzeigen, an welcher Stelle keine Delegierung möglich ist. Wenn Sie mit kleinen Datasets arbeiten (weniger als 500 Datensätze), können Sie eine beliebige Datenquelle und Formel verwenden, weil die App Daten lokal verarbeiten kann, falls das Delegieren der Formel nicht möglich ist. 

> [!NOTE]
> Delegierungs Warnungen wurden zuvor in powerapps als "Blue dot"-Vorschläge gekennzeichnet, aber Delegierungs Vorschläge wurden seit der erneuten Klassifizierung als Warnungen erneut klassifiziert. Wenn die Daten in der Datenquelle 500 Datensätze überschreiten und eine Funktion nicht delegiert werden kann, können Power Apps möglicherweise nicht alle Daten abrufen, und Ihre APP weist möglicherweise falsche Ergebnisse auf. Mithilfe von Delegierungswarnungen können Sie Ihre App so verwalten, dass die Ergebnisse richtig sind.

## <a name="delegable-data-sources"></a>Delegierbare Datenquellen
Die Delegierung wird nur für bestimmte tabellarische Datenquellen unterstützt. Wenn eine Datenquelle die Delegierung unterstützt, werden von der zugehörigen [Connector-Dokumentation](https://docs.microsoft.com/connectors/) unterstützt. Diese tabellarischen Datenquellen sind z. b. die beliebtesten und unterstützen die Delegierung:

- [Common Data Service](https://docs.microsoft.com/connectors/commondataservice/) 
- [SharePoint](https://docs.microsoft.com/connectors/sharepointonline/) 
- [SQL Server](https://docs.microsoft.com/connectors/sql/) 

Importierte Excel-Arbeitsmappen (unter Verwendung der Datenquelle **statische Daten zu Ihrer APP hinzufügen** ), Sammlungen und in Kontext Variablen gespeicherte Tabellen erfordern keine Delegierung. Alle diese Daten befinden sich bereits im Arbeitsspeicher, und die vollständige powerapps-Sprache kann angewendet werden.

## <a name="delegable-functions"></a>Delegierbare Funktionen
Der nächste Schritt besteht darin, nur diejenigen Formeln zu verwenden, die delegiert werden können. Hier sind die Formelelemente angegeben, die delegiert werden können. Allerdings ist jede Datenquelle anders, und nicht alle unterstützen alle Elemente. Überprüfen Sie Ihre Formel auf Delegierungswarnungen.

Diese Listen werden sich im Laufe der Zeit ändern. Wir arbeiten daran, die Delegierung für weitere Funktionen und Operatoren zu unterstützen.

### <a name="filter-functions"></a>Filterfunktionen
Die Funktionen **[Filter](functions/function-filter-lookup.md)** , **[Search](functions/function-filter-lookup.md)** und **[LookUp](functions/function-filter-lookup.md)** können delegiert werden.  

In den Funktionen **Filter** und **LookUp** können Sie für Spalten der Tabelle Folgendes verwenden, um die entsprechenden Datensätze auszuwählen:

* **[And](functions/function-logicals.md)** (einschließlich **[&&](functions/operators.md)** ), **[Or](functions/function-logicals.md)** (einschließlich **[||](functions/operators.md)** ), **[Not](functions/function-logicals.md)** (einschließlich **[!](functions/operators.md)** )
* **[In](functions/operators.md)**
* **[=](functions/operators.md)** , **[<>](functions/operators.md)** , **[>=](functions/operators.md)** , **[<=](functions/operators.md)** , **[>](functions/operators.md)** , **[<](functions/operators.md)**
* **[+](functions/operators.md)** , **[-](functions/operators.md)**
* **[TrimEnds](functions/function-trim.md)**
* **[IsBlank](functions/function-isblank-isempty.md)**
* **[Startzwith](functions/function-startswith.md)** ,  **[EndsWith](functions/function-startswith.md)**
* Konstante Werte, die in allen Datensätzen gleich sind, z.B. Steuerelementeigenschaften sowie [globale und Kontextvariablen](working-with-variables.md).

Sie können auch Teile Ihrer Formel verwenden, die zu einem konstanten Wert für alle Datensätze ausgewertet werden. Beispielsweise ist **Left (Language (), 2)** , **Date (2019, 3, 31)** und **Today ()** nicht von Spalten des Datensatzes abhängig und gibt daher denselben Wert für alle Datensätze zurück. Diese Werte können als Konstante an die Datenquelle gesendet werden und blockieren nicht die Delegierung. 

In der obigen Liste werden die folgenden wichtigen Elemente nicht aufgeführt:

* **[If](functions/function-if.md)**
* **[*](functions/operators.md)** , **[/](functions/operators.md)** , **[Mod](functions/function-mod.md)**
* **[Concatenate](functions/function-concatenate.md)** (einschließlich **[&](functions/operators.md)** )
* **[ExactIn](functions/operators.md)**
* Funktionen für die Zeichenfolgenbearbeitung: **[Lower](functions/function-lower-upper-proper.md)** , **[Upper](functions/function-lower-upper-proper.md)** , **[Left](functions/function-left-mid-right.md)** , **[Mid](functions/function-left-mid-right.md)** , **[Len](functions/function-left-mid-right.md)** , ...
* Signale: **[Location](functions/signals.md)** , **[Acceleration](functions/signals.md)** , **[Compass](functions/signals.md)** , ...
* Volatile: **[Rand](functions/function-rand.md)** ,...
* [Sammlungen](working-with-variables.md)

### <a name="sorting-functions"></a>Sortierfunktionen
**[Sort](functions/function-sort.md)** und **[SortByColumns](functions/function-sort.md)** können delegiert werden.

Bei **Sort** kann die Formel nur der Name einer einzelnen Spalte sein und keine anderen Operatoren und Funktionen enthalten.

### <a name="aggregate-functions"></a>Aggregatfunktionen
**[Sum](functions/function-aggregates.md)** , **[Average](functions/function-aggregates.md)** , **[Min](functions/function-aggregates.md)** und **[Max](functions/function-aggregates.md)** können delegiert werden. Diese Delegierung wird derzeit nur von einer begrenzten Anzahl von Datenquellen unterstützt. Weitere Informationen finden Sie in der [Delegierungsliste](delegation-list.md).

Zählfunktionen wie **[CountRows](functions/function-table-counts.md)** , **[CountA](functions/function-table-counts.md)** und **[Count](functions/function-table-counts.md)** können nicht delegiert werden.

Andere Aggregatfunktionen wie **[StdevP](functions/function-aggregates.md)** und **[VarP](functions/function-aggregates.md)** können nicht delegiert werden.

### <a name="table-shaping-functions"></a>Tabellen Strukturierungs Funktionen

**[AddColumns](functions/function-table-shaping.md)** , **[dropcolumns](functions/function-table-shaping.md)** , **[renamecolumns](functions/function-table-shaping.md)** und **[showcolumns](functions/function-table-shaping.md)** unterstützen die Delegierung teilweise.  Formeln in ihren Argumenten können delegiert werden.  Die Ausgabe dieser Funktionen unterliegt jedoch dem Grenzwert für nicht Delegierungs Datensätze.

Wie in diesem Beispiel verwenden die Hersteller häufig **AddColumns** und **Lookup** , um Informationen aus einer Tabelle in eine andere zusammenzuführen, die häufig als Join in der Datenbanksprache bezeichnet wird:

```powerapps-comma
AddColumns( Products; 
    "Supplier Name"; 
    LookUp( Suppliers; Suppliers.ID = Product.SupplierID ).Name 
)
```

Obwohl **Produkte** und **Lieferanten** möglicherweise delegier Bare Datenquellen sind und **Lookup** eine delegier Bare Funktion ist, kann die Ausgabe der **AddColumns** -Funktion nicht delegiert werden. Das Ergebnis der gesamten Formel ist auf den ersten Teil der Datenquelle **Products** beschränkt. Da die **LookUp**-Funktion und die dazugehörige Datenquelle delegierbar sind, kann eine Übereinstimmung für **Suppliers** auch dann überall in der Datenquelle gefunden werden, wenn diese groß ist. 

Wenn Sie **AddColumns** auf diese Weise verwenden, muss die **Suche** separate Aufrufe an die Datenquelle für jeden dieser ersten Datensätze in **Produkten**durchführen, was zu einem großen netzwerkchatter führen kann. Wenn die **Lieferanten** klein genug sind und sich nicht häufig ändern, können Sie die **Collect** -Funktion in [**OnStart**](functions/signals.md) aufrufen, um die Datenquelle in der APP beim Start zwischenzuspeichern. Als Alternative können Sie Ihre APP so strukturieren, dass Sie die zugehörigen Datensätze nur dann abrufen, wenn Sie vom Benutzer angefordert werden.  
 
## <a name="non-delegable-functions"></a>Nicht delegierbare Funktionen
Für alle anderen Funktionen einschließlich der Folgenden wird die Delegierung nicht unterstützt:

* **[First](functions/function-first-last.md)** , **[FirstN](functions/function-first-last.md)** , **[Last](functions/function-first-last.md)** , **[LastN](functions/function-first-last.md)**
* **[Choices](functions/function-choices.md)**
* **[Concat](functions/function-concatenate.md)**
* **[Collect](functions/function-clear-collect-clearcollect.md)** , **[ClearCollect](functions/function-clear-collect-clearcollect.md)**
* **[CountIf](functions/function-table-counts.md)** , **[RemoveIf](functions/function-remove-removeif.md)** , **[UpdateIf](functions/function-update-updateif.md)**
* **[GroupBy](functions/function-groupby.md)** , **[Ungroup](functions/function-groupby.md)**

## <a name="non-delegable-limits"></a>Grenzwerte für Fälle, in denen keine Delegierung möglich ist
Formeln, die nicht delegiert werden können, werden lokal verarbeitet. Dadurch kann die volle Bandbreite der Formelsprache von powerapps verwendet werden. Dies hat aber einen Preis: Alle Daten müssen zuerst auf das Gerät übertragen werden, sodass unter Umständen eine größere Datenmenge über das Netzwerk abgerufen werden muss. Dies kann eine Weile dauern, sodass der Eindruck entsteht, dass Ihre App langsam ist oder hängt.

Um dies zu vermeiden, erzwingt Power apps einen Grenzwert für die Datenmenge, die lokal verarbeitet werden kann: standardmäßig 500 Datensätze.  Wir haben diesen Wert gewählt, damit Sie über vollständigen Zugriff auf kleine Datasets verfügen und die Nutzung Ihrer großen Datasets optimieren können, indem Teilergebnisse angezeigt werden.

Bei der Nutzung dieser Option sollten Sie aber mit Bedacht vorgehen, da sie für Benutzer verwirrend sein kann. Angenommen, Sie verwenden die Funktion **Filter** mit einer Auswahlformel, die nicht delegiert werden kann, für eine Datenquelle mit einer Millionen Datensätzen. Da der Filtervorgang auf lokaler Ebene durchgeführt wird, werden nur die ersten 500 Datensätze überprüft. Wenn der gewünschte Datensatz der 501. oder 500.001. Datensatz ist, wird er nicht berücksichtigt und nicht von der Funktion **Filter** zurückgegeben.

Aggregatfunktion können auch zu Verwirrung führen. Angenommen, Sie verwenden **Average** für eine Spalte der Datenquelle mit einer Million Datensätzen. Da **Average** noch nicht delegiert werden kann, kann nur für die ersten 500 Datensätze der Mittelwert gebildet werden. Wenn Sie hierbei nicht mit Bedacht vorgehen, könnte eine Teilantwort von einem Benutzer Ihrer App als vollständige Antwort verstanden werden.

## <a name="changing-the-limit"></a>Ändern des Grenzwerts
Die Standardzahl für Datensätze lautet 500. Sie können diese Zahl aber für die gesamte App ändern:

1. Klicken Sie auf der Registerkarte **Datei** auf **App-Einstellungen**.
2. Ändern Sie unter **Erweiterte Einstellungen**das **Limit für Daten Zeilen für nicht delegier Bare Abfragen** zwischen 1 und 2000.

In einigen Fällen ist Ihnen möglicherweise bekannt, dass für die Anforderungen Ihres Szenarios ein Grenzwert von 2.000 (oder auch 1.000 oder 1.500) erforderlich ist. Diese Zahl können Sie vorsichtig erhöhen und Ihrem Szenario anpassen. Wenn Sie diese Zahl erhöhen, kann das die Leistung Ihrer App negativ beeinflussen, insbesondere bei Tabellen mit vielen Spalten. Die beste Lösung dafür ist, wenn Sie so viel wie möglich delegieren.

Wenn Sie sicherstellen möchten, dass Ihre Apps auf große Datasets skaliert werden kann, müssen Sie für diese Einstellung den Wert auf 1 reduzieren. Für nicht delegierbare Elemente wird dann genau ein Datensatz zurückgegeben, der beim Testen der App leicht auffindbar sein sollte. Dadurch können unerwartete Ergebnisse vermieden werden, wenn eine Proof of Concept-App in eine Produktionsumgebung überführt werden soll.

## <a name="delegation-warnings"></a>Delegierungswarnungen
Damit Sie leichter erkennen können, was nicht delegiert wird, bietet Power apps eine Warnung (gelbes Dreieck), wenn Sie eine Formel erstellen, die etwas enthält, das nicht delegiert werden kann.

Delegierungswarnungen werden nur für Formeln angezeigt, die für delegierbare Datenquellen verwendet werden. Wenn keine Warnung angezeigt wird und Sie der Meinung sind, dass Ihre Formal nicht richtig delegiert wird, können Sie den Typ der Datenquelle anhand der obigen Liste mit den [delegierbaren Datenquellen](delegation-overview.md#delegable-data-sources) überprüfen.

## <a name="examples"></a>Beispiele
Für dieses Beispiel generieren Sie automatisch eine App mit drei Anzeigen, die auf einer SQL Server-Tabelle mit dem Namen **[dbo].[Fruit]** basieren. Weitere Informationen zum Generieren der App finden Sie im [Thema über Common Data Service](data-platform-create-app.md) auf SQL Server.

![App mit drei Bildschirmen](./media/delegation-overview/products-afd.png)

Die Katalogeigenschaft **Items** ist auf eine Formel festgelegt, die die Funktionen **SortByColumns** und **Search** enthält. Beide Funktionen können delegiert werden.

Geben Sie in das Suchfeld **Apple** ein.

Dann werden im oberen Bereich des Bildschirms vorübergehend Punkte angezeigt, während die App mit SQL Server kommuniziert, um die Suchanforderung zu verarbeiten. Es werden alle Datensätze angezeigt, die den Suchkriterien entsprechen, auch wenn die Datenquelle Millionen von Datensätzen enthält.

![Suchtext-Eingabesteuerelement](./media/delegation-overview/products-apple.png)

Die Suchergebnisse umfassen die Begriffe **Apples**, **Crab apples** und **Pineapple**, weil die Funktion **Search** eine Textspalte vollständig durchsucht. Wenn Sie nur Datensätze suchen wollten, die den Suchbegriff am Anfang des Obstnamens umfassen, können Sie die delegierbare Funktion **Filter** mit einem komplizierteren Suchbegriff verwenden. (Entfernen Sie der Einfachheit halber den Aufruf **SortByColumns**.)

![SortByColumns-Aufruf entfernen](./media/delegation-overview/products-apple-delegationwarning.png)

Die neuen Ergebnisse umfassen dann den Begriff **Apples**, aber nicht die Begriffe **Crab apples** oder **Pineapple**.  Dann wird allerdings neben dem Katalog (und in der Miniaturansicht des Bildschirms auf der Navigationsleiste im linken Bereich, die Miniaturansichten anzeigt) ein gelbes Dreieck und unter einem Teil der Formel eine blaue Wellenlinie angezeigt. Diese Elemente stellen alle jeweils eine Warnung dar. Wenn Sie auf das gelbe Dreieck neben dem Katalog zeigen, wird die folgende Meldung angezeigt:

![Auf Delegierungswarnung zeigen](./media/delegation-overview/products-apple-yellowwarning.png)

SQL Server ist eine delegierbare Datenquelle und **Filter** eine delegierbare Funktion. Allerdings können **Mid** und **Len** nicht an jede beliebige Datenquelle delegiert werden.

Aber es hat funktioniert, oder? Na ja, fast. Das ist der Grund dafür, dass es sich um eine Warnung und nicht um eine rote Wellenlinie handelt.

- Wenn die Tabelle weniger als 500 Datensätze enthält, hat die Formel einwandfrei funktioniert. Alle Datensätze wurden auf das Gerät übertragen, und die Funktion **Filter** wurde lokal angewendet.
- Wenn die Tabelle mehr als 500 Datensätze enthält, gibt die Formel den 501. Datensatz sowie alle weiteren Datensätze nicht mehr zurück, auch wenn die Kriterien erfüllt sind.

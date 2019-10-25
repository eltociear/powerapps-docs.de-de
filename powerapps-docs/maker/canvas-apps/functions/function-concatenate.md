---
title: Funktionen „Concat“ und „Concatenate“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Concat“ und „Concatenate“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0a56230539990ce51cc9270f71d8c2b7c9a1db73
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "71992889"
ms.PowerAppsDecimalTransform: true
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>Funktionen „Concat“ und „Concatenate“ in PowerApps

Verketten einzelne Zeichenfolgen von Text und Zeichenfolgen in [Tabellen](../working-with-tables.md)

## <a name="description"></a>Beschreibung

Die **Concatenate**-Funktion verkettet eine Mischung aus einzelnen Zeichenfolgen und eine einspaltige Tabelle von Zeichenfolgen. Wenn Sie diese Funktion mit einzelnen Zeichen folgen verwenden, entspricht Sie der Verwendung des **&** - [Operators](operators.md).

Die **Concat**-Funktion verkettet das Ergebnis einer Formel, das in allen [Datensätzen](../working-with-tables.md#records) einer Tabelle angewendet wird, was zu einer einzelnen Zeichenfolge führt. Verwenden Sie diese Funktion, um die Zeichenfolgen einer Tabelle zusammenzufassen, wie es die **[Sum](function-aggregates.md)** -Funktion bei Zahlen macht.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Verwenden Sie die [**Split**](function-split.md) -oder [**MatchAll**](function-ismatch.md) -Funktion, um eine Zeichenfolge in eine Tabelle von Teil Zeichenfolgen aufzuteilen.

## <a name="syntax"></a>Syntax

**Concat**( *Tabelle*; *Formel* )

- *Table*: erforderlich.  Die zu verarbeitende Tabelle.
- *Formula*: Erforderlich.  Die auf alle Datensätze der Tabelle anzuwendende Formel.

**Concatenate**( *Zeichenfolge1* [; *Zeichenfolge2*; ...] )

- *Zeichenfolge(n)* : Erforderlich.  Mischung aus einzelnen Zeichenfolgen oder eine einspaltige Tabelle von Zeichenfolgen.

## <a name="examples"></a>Beispiele

In den Beispielen in diesem Abschnitt werden diese globalen Variablen verwendet:

- **FirstName** = "Jane"
- **LastName** = "Doe"
- **Produkte**  =  mit zwei Spalten und vier Zeilen ![Table ](media/function-concatenate/products.png)

Wenn Sie diese globalen Variablen in einer APP erstellen möchten, fügen Sie ein [**Button**](../controls/control-button.md) -Steuerelement ein, und legen **Sie dessen onselect** -Eigenschaft auf diese Formel fest:

```powerapps-comma
Set( FirstName; "Jane" );; Set( LastName; "Doe" );;
Set( Products;
    Table(
        { Name: "Violin"; Type: "String" };
        { Name: "Cello"; Type: "String" };
        { Name: "Trumpet"; Type: "Wind" }
    )
)
```

Wählen Sie die Schaltfläche aus (indem Sie darauf klicken, während Sie die Alt-Taste gedrückt halten).

### <a name="concatenate-function-and-the--operator"></a>Concatenate-Funktion und der &-Operator

Legen Sie für diese Beispiele die **Text** -Eigenschaft eines [**Label**](../controls/control-text-box.md) -Steuer Elements auf eine Formel aus der ersten Spalte der nächsten Tabelle fest.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concatenate (&nbsp;LastName, &nbsp; ", &nbsp;", &nbsp;FirstName &nbsp;)** | Verkettet den Wert in **LastName**, die Zeichenfolge **","** (ein Komma, gefolgt von einem Leerzeichen) und den Wert in **FirstName**. | "Doe, &nbsp;Jane" |
| **LastName &nbsp; & &nbsp; ", &nbsp;" &nbsp; & &nbsp;FirstName** | Identisch mit dem vorherigen Beispiel, mit der Ausnahme, dass anstelle der-Funktion der **&** -Operator verwendet wird. | "Doe, &nbsp;Jane" |
| **Concatenate (&nbsp;FirstName &nbsp; "&nbsp;", &nbsp;LastName &nbsp;)** | Verkettet den Wert in **FirstName**, die Zeichenfolge **""** (ein einzelnes Leerzeichen) und den Wert in " **LastName**". | "Jane &nbsp;Doe" |
| **FirstName &nbsp; & &nbsp; "&nbsp;" &nbsp; & &nbsp;LastName** | Identisch mit dem vorherigen Beispiel mit dem **&** -Operator anstelle der-Funktion. | "Jane &nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>Verketten mit einer einspaltigen Tabelle

Fügen Sie in diesem Beispiel ein leeres [ **, vertikales**](../controls/control-gallery.md) Katalog-Steuerelement hinzu, legen Sie dessen **Items** -Eigenschaft auf die Formel in der nächsten Tabelle fest, und fügen Sie dann eine Bezeichnung in der Katalog Vorlage hinzu.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concatenate ("Name: &nbsp;", &nbsp;Products. Name, ", &nbsp;Type: &nbsp;", &nbsp;Products. Type)** | Verkettet für jeden Datensatz in der **Products** -Tabelle die Zeichenfolge **"Name:"** , den Namen des Produkts, die Zeichenfolge **", Type:"** und den Typ des Produkts.  | ![Tabelle mit Produkten](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat-Funktion

Legen Sie für diese Beispiele die **Text** -Eigenschaft einer Bezeichnung auf eine Formel aus der ersten Spalte der nächsten Tabelle fest.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concat (Products, Name & ",")** | Wertet den Ausdrucks **Namen & ","** für jeden Datensatz von **Produkten** aus und verkettet die Ergebnisse zu einer einzelnen Text Zeichenfolge.  | "Violine, &nbsp;Cello, &nbsp;Trumpet &nbsp;" |
| **Concat (Filter (&nbsp;Products, &nbsp;Type &nbsp; = &nbsp; "String" &nbsp;), Name & ",")** | Wertet den Formel **Namen & ","** für jeden Datensatz von **Produkten** aus, der dem **Filtertyp = "String"** entspricht, und verkettet die Ergebnisse zu einer einzelnen Text Zeichenfolge.   | "Violine, &nbsp;Cello &nbsp;" |

### <a name="trimming-the-end"></a>Kürzen des Endes

Die beiden letzten Beispiele enthalten am Ende des Ergebnisses ein zusätzliches ",". Die-Funktion fügt ein Komma und ein Leerzeichen an den **namens** Wert jedes Datensatzes in der Tabelle an, einschließlich des letzten Datensatzes.

In einigen Fällen sind diese zusätzlichen Zeichen nicht von Bedeutung. Beispielsweise wird ein einzelnes Leerzeichen nicht angezeigt, wenn Sie das Ergebnis in einer Bezeichnung anzeigen. Wenn Sie diese zusätzlichen Zeichen entfernen möchten, verwenden Sie die [**left**](function-left-mid-right.md) -oder [**Match**](function-ismatch.md) -Funktion.

Legen Sie für diese Beispiele die **Text** -Eigenschaft einer Bezeichnung auf eine Formel aus der ersten Spalte der nächsten Tabelle fest.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Left (Concat (&nbsp;Products, &nbsp;Name &nbsp; & &nbsp; ", &nbsp;" &nbsp;), Len (&nbsp;Concat (&nbsp;Products, 0Name 1 2 3 ", 4" 5) 6) 7 @no__ t_18 92)** | Gibt das Ergebnis von **Concat** zurück, entfernt jedoch die letzten zwei Zeichen, die das überflüssige Trennzeichen bilden. | "Violine, &nbsp;Cello &nbsp;Trumpet" |
| **Match (Concat (&nbsp;Products, &nbsp;Name &nbsp; & &nbsp; ", &nbsp;" &nbsp;) "," ^ (? &lt;trim &gt;. *), 0 $ "). Trim** | Gibt die Zeichen von **Concat** vom Anfang der Text Zeichenfolge (^) bis zum Ende ($) zurück, enthält jedoch nicht das unerwünschte Komma und den Leerraum am Ende. | "Violine, &nbsp;Cello &nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Split und MatchAll

Wenn Sie **Concat** mit einem Trennzeichen verwendet haben, können Sie den Vorgang umkehren, indem Sie die **Split** -Funktion und die **MatchAll** -Funktion kombinieren.

Fügen Sie für diese Beispiele einen leeren, vertikalen Katalog hinzu, legen Sie dessen **Items** -Eigenschaft auf eine Formel in der nächsten Tabelle fest, und fügen Sie dann eine Bezeichnung in der Katalog Vorlage hinzu.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Split (Concat (&nbsp;Products, &nbsp;Name &nbsp; & &nbsp; ", &nbsp;" &nbsp;) ",", ")** | Teilt die Text Zeichenfolge mit dem Trennzeichen **","** . Die Zeichenfolge endet mit einem Komma und einem Leerzeichen, daher ist die letzte Zeile im Ergebnis eine leere Zeichenfolge.  | ![Tabelle](media/function-concatenate/split.png) |
| **MatchAll (Concat (&nbsp;Products; &nbsp;Name &nbsp; & &nbsp; ", &nbsp;" &nbsp;) "," [^ \s;] + "). Vollständiger Treffer** | Teilt die Text Zeichenfolge basierend auf Zeichen, die keine Leerzeichen oder Kommas sind. Mit dieser Formel werden das zusätzliche Komma und der Leerraum am Ende der Zeichenfolge entfernt. | ![Tabelle](media/function-concatenate/matchall.png)
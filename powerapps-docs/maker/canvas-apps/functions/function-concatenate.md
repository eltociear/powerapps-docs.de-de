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
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992889"
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>Funktionen „Concat“ und „Concatenate“ in PowerApps

Verketten einzelne Zeichenfolgen von Text und Zeichenfolgen in [Tabellen](../working-with-tables.md)

## <a name="description"></a>Beschreibung

Die **Concatenate**-Funktion verkettet eine Mischung aus einzelnen Zeichenfolgen und eine einspaltige Tabelle von Zeichenfolgen. Wenn Sie diese Funktion mit einzelnen Zeichen folgen verwenden, entspricht dies der Verwendung des **&-** [Operators](operators.md).

Die **Concat**-Funktion verkettet das Ergebnis einer Formel, das in allen [Datensätzen](../working-with-tables.md#records) einer Tabelle angewendet wird, was zu einer einzelnen Zeichenfolge führt. Verwenden Sie diese Funktion, um die Zeichenfolgen einer Tabelle zusammenzufassen, wie es die **[Sum](function-aggregates.md)** -Funktion bei Zahlen macht.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Verwenden Sie die [**Split**](function-split.md) -oder [**MatchAll**](function-ismatch.md) -Funktion, um eine Zeichenfolge in eine Tabelle von Teil Zeichenfolgen aufzuteilen.

## <a name="syntax"></a>Syntax

**Concat**( *Tabelle*, *Formel* )

- *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
- *Formel* (erforderlich):  Die auf alle Datensätze der Tabelle anzuwendende Formel.

**Concatenate**( *Zeichenfolge1* [, *Zeichenfolge2*, ...] )

- *Zeichenfolge(n)* : Erforderlich.  Mischung aus einzelnen Zeichenfolgen oder eine einspaltige Tabelle von Zeichenfolgen.

## <a name="examples"></a>Beispiele

In den Beispielen in diesem Abschnitt werden diese globalen Variablen verwendet:

- **FirstName** = "Jane"
- **LastName** = "Doe"
- **Products** =  @ no__t-2table mit zwei Spalten und vier Zeilen @ no__t-3

Wenn Sie diese globalen Variablen in einer APP erstellen möchten, fügen Sie ein [**Button**](../controls/control-button.md) -Steuerelement ein, und legen **Sie dessen onselect** -Eigenschaft auf diese Formel fest:

```powerapps-dot
Set( FirstName, "Jane" ); Set( LastName, "Doe" );
Set( Products,
    Table(
        { Name: "Violin", Type: "String" },
        { Name: "Cello", Type: "String" },
        { Name: "Trumpet", Type: "Wind" }
    )
)
```

Wählen Sie die Schaltfläche aus (indem Sie darauf klicken, während Sie die Alt-Taste gedrückt halten).

### <a name="concatenate-function-and-the--operator"></a>Concatenate-Funktion und der &-Operator

Legen Sie für diese Beispiele die **Text** -Eigenschaft eines [**Label**](../controls/control-text-box.md) -Steuer Elements auf eine Formel aus der ersten Spalte der nächsten Tabelle fest.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concatenate (&nbsp;lastname, &nbsp; ", &nbsp;", &nbsp;firstname @ no__t-5)** | Verkettet den Wert in **LastName**, die Zeichenfolge **","** (ein Komma, gefolgt von einem Leerzeichen) und den Wert in **FirstName**. | "Doe, &nbsp;jane" |
| **LastName @ no__t-1 @ no__t-2 @ no__t-3 ", &nbsp;" &nbsp; @ no__t-6 @ no__t-7firstname** | Identisch mit dem vorherigen Beispiel, mit der Ausnahme, dass der **&-** Operator anstelle der-Funktion verwendet wird. | "Doe, &nbsp;jane" |
| **Concatenate (&nbsp;firstname, &nbsp; "&nbsp;", &nbsp;lastname @ no__t-5)** | Verkettet den Wert in **FirstName**, die Zeichenfolge **""** (ein einzelnes Leerzeichen) und den Wert in " **LastName**". | "Jane @ no__t-0doe" |
| **FirstName @ no__t-1 @ no__t-2 @ no__t-3 "&nbsp;" &nbsp; @ no__t-6 @ no__t-7lastname** | Identisch mit dem vorherigen Beispiel mit dem **&-** Operator anstelle der-Funktion. | "Jane @ no__t-0doe" |

### <a name="concatenate-with-a-single-column-table"></a>Verketten mit einer einspaltigen Tabelle

Fügen Sie in diesem Beispiel ein leeres [ **, vertikales**](../controls/control-gallery.md) Katalog-Steuerelement hinzu, legen Sie dessen **Items** -Eigenschaft auf die Formel in der nächsten Tabelle fest, und fügen Sie dann eine Bezeichnung in der Katalog Vorlage hinzu.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concatenate ("Name: &nbsp;", &nbsp;Products.Name, ", &nbsp;type: &nbsp;", &nbsp;products. Type)** | Verkettet für jeden Datensatz in der **Products** -Tabelle die Zeichenfolge **"Name:"** , den Namen des Produkts, die Zeichenfolge **", Type:"** und den Typ des Produkts.  | ![Tabelle mit Produkten](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat-Funktion

Legen Sie für diese Beispiele die **Text** -Eigenschaft einer Bezeichnung auf eine Formel aus der ersten Spalte der nächsten Tabelle fest.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concat (Products, Name & ",")** | Wertet den Ausdrucks **Namen & ","** für jeden Datensatz von **Produkten** aus und verkettet die Ergebnisse zu einer einzelnen Text Zeichenfolge.  | "Violine, &nbsp;cello, &nbsp;trompete, &nbsp;" |
| **Concat (Filter (&nbsp;products, &nbsp;type @ no__t-3 @ no__t-4 @ no__t-5 "String" &nbsp;), Name & ",")** | Wertet den Formel **Namen & ","** für jeden Datensatz von **Produkten** aus, der dem **Filtertyp = "String"** entspricht, und verkettet die Ergebnisse zu einer einzelnen Text Zeichenfolge.   | "Violine, &nbsp;cello, &nbsp;" |

### <a name="trimming-the-end"></a>Kürzen des Endes

Die beiden letzten Beispiele enthalten am Ende des Ergebnisses ein zusätzliches ",". Die-Funktion fügt ein Komma und ein Leerzeichen an den **namens** Wert jedes Datensatzes in der Tabelle an, einschließlich des letzten Datensatzes.

In einigen Fällen sind diese zusätzlichen Zeichen nicht von Bedeutung. Beispielsweise wird ein einzelnes Leerzeichen nicht angezeigt, wenn Sie das Ergebnis in einer Bezeichnung anzeigen. Wenn Sie diese zusätzlichen Zeichen entfernen möchten, verwenden Sie die [**left**](function-left-mid-right.md) -oder [**Match**](function-ismatch.md) -Funktion.

Legen Sie für diese Beispiele die **Text** -Eigenschaft einer Bezeichnung auf eine Formel aus der ersten Spalte der nächsten Tabelle fest.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Left (Concat (&nbsp;products, &nbsp;name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;), Len (&nbsp;concat (&nbsp;products, 0name @ no__t-11 @ no__t-12 @ no__t-13 ", 4" 5) 6) 7 @ no__t-18 @ no__t-192)** | Gibt das Ergebnis von **Concat** zurück, entfernt jedoch die letzten zwei Zeichen, die das überflüssige Trennzeichen bilden. | "Violine, &nbsp;cello, &nbsp;trompete" |
| **Match (Concat (&nbsp;products, &nbsp;name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;), "^ (? &lt;trim @ no__t-9. *), @no__t-$10"). Trim** | Gibt die Zeichen von **Concat** vom Anfang der Text Zeichenfolge (^) bis zum Ende ($) zurück, enthält jedoch nicht das unerwünschte Komma und den Leerraum am Ende. | "Violine, &nbsp;cello, &nbsp;trompete" |

### <a name="split-and-matchall"></a>Split und MatchAll

Wenn Sie **Concat** mit einem Trennzeichen verwendet haben, können Sie den Vorgang umkehren, indem Sie die **Split** -Funktion und die **MatchAll** -Funktion kombinieren.

Fügen Sie für diese Beispiele einen leeren, vertikalen Katalog hinzu, legen Sie dessen **Items** -Eigenschaft auf eine Formel in der nächsten Tabelle fest, und fügen Sie dann eine Bezeichnung in der Katalog Vorlage hinzu.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Split (Concat (&nbsp;products, &nbsp;name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;), ",")** | Teilt die Text Zeichenfolge mit dem Trennzeichen **","** . Die Zeichenfolge endet mit einem Komma und einem Leerzeichen, daher ist die letzte Zeile im Ergebnis eine leere Zeichenfolge.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll (Concat (&nbsp;products, &nbsp;name @ no__t-3 @ no__t-4 @ no__t-5 ", &nbsp;" &nbsp;), "[^ \s,] +"). Vollständiger Treffer** | Teilt die Text Zeichenfolge basierend auf Zeichen, die keine Leerzeichen oder Kommas sind. Mit dieser Formel werden das zusätzliche Komma und der Leerraum am Ende der Zeichenfolge entfernt. | ![Table](media/function-concatenate/matchall.png)
---
title: Funktionen „Concat“ und „Concatenate“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Concat“ und „Concatenate“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 889f612f3da208d4edfccc43a579ced07933b40d
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66216049"
ms.PowerAppsDecimalTransform: true
---
# <a name="concat-and-concatenate-functions-in-powerapps"></a>Funktionen „Concat“ und „Concatenate“ in PowerApps

Verketten einzelne Zeichenfolgen von Text und Zeichenfolgen in [Tabellen](../working-with-tables.md)

## <a name="description"></a>Beschreibung

Die **Concatenate**-Funktion verkettet eine Mischung aus einzelnen Zeichenfolgen und eine einspaltige Tabelle von Zeichenfolgen. Wenn Sie diese Funktion mit einzelnen Zeichenfolgen verwenden, ist äquivalent zur Verwendung der **&** [Operator](operators.md).

Die **Concat**-Funktion verkettet das Ergebnis einer Formel, das in allen [Datensätzen](../working-with-tables.md#records) einer Tabelle angewendet wird, was zu einer einzelnen Zeichenfolge führt. Verwenden Sie diese Funktion, um die Zeichenfolgen einer Tabelle zusammenzufassen, wie es die **[Sum](function-aggregates.md)** -Funktion bei Zahlen macht.

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

Verwenden der [ **Split** ](function-split.md) oder [ **MatchAll** ](function-ismatch.md) Funktion zum Aufteilen einer Zeichenfolge in eine Tabelle von Teilzeichenfolgen.

## <a name="syntax"></a>Syntax

**Concat**( *Tabelle*; *Formel* )

- *Tabelle* (erforderlich):  Die zu verarbeitende Tabelle.
- *Formel* (erforderlich):  Die auf alle Datensätze der Tabelle anzuwendende Formel.

**Concatenate**( *Zeichenfolge1* [; *Zeichenfolge2*; ...] )

- *Zeichenfolge(n)* : Erforderlich.  Mischung aus einzelnen Zeichenfolgen oder eine einspaltige Tabelle von Zeichenfolgen.

## <a name="examples"></a>Beispiele

In die Beispielen in diesem Abschnitt verwenden Sie diese globale Variablen:

- **FirstName** = "Jane"
- **"LastName"** = "Doe"
- **Produkte** = ![Tabelle mit zwei Spalten und vier Zeilen](media/function-concatenate/products.png)

Um diese globalen Variablen in einer app zu erstellen, fügen Sie eine [ **Schaltfläche** ](../controls/control-button.md) steuern, und legen dessen **OnSelect** -Eigenschaft auf diese Formel:

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

Wählen Sie die Schaltfläche (indem Sie darauf klicken, während Sie die Alt-Taste gedrückt halten).

### <a name="concatenate-function-and-the--operator"></a>Concatenate-Funktion und den &-Operator

Legen Sie für diese Beispiele die **Text** Eigenschaft eine [ **Bezeichnung** ](../controls/control-text-box.md) Steuerelement auf eine Formel aus der ersten Spalte der folgenden Tabelle.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Verketten (&nbsp;"LastName",&nbsp;",&nbsp;",&nbsp;FirstName&nbsp;)** | Der Wert in verkettet **"LastName"** , die Zeichenfolge **","** (ein Komma gefolgt von einem Leerzeichen), und der Wert im **FirstName**. | "Doe, der&nbsp;Jane" |
| **"LastName"&nbsp;&&nbsp;",&nbsp;"&nbsp;&&nbsp;FirstName** | Wie im vorherigen Beispiel, außer Sie verwenden die **&** Operator anstelle der Funktion. | "Doe, der&nbsp;Jane" |
| **Verketten (&nbsp;FirstName,&nbsp;"&nbsp;",&nbsp;"LastName"&nbsp;)** | Der Wert in verkettet **FirstName**, die Zeichenfolge **""** (ein einzelnes Leerzeichen), und der Wert in **"LastName"** . | "Jane&nbsp;Doe" |
| **FirstName&nbsp;&&nbsp;"&nbsp;"&nbsp;&&nbsp;"LastName"** | Im vorherigen Beispiel identisch mit der **&** Operator anstelle der Funktion. | "Jane&nbsp;Doe" |

### <a name="concatenate-with-a-single-column-table"></a>Verketten Sie mit einer einspaltigen Tabelle

In diesem Beispiel fügen Sie eine leere, vertikale [ **Katalog** ](../controls/control-gallery.md) steuern, legen Sie dessen **Elemente** Eigenschaft, um die Formel in der folgenden Tabelle, und fügen Sie dann in der Katalogvorlage eine Bezeichnung hinzu.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concatenate( "Name:&nbsp;";&nbsp;Products.Name; ",&nbsp;Type:&nbsp;";&nbsp;Products.Type )** | Für jeden Datensatz in die **Produkte** Tabelle, die Zeichenfolge verkettet **"Name:"** , den Namen des Produkts, die Zeichenfolge **", Typ:"** und den Typ des Produkts.  | ![Tabelle von Produkten](media/function-concatenate/single-column.png) |

### <a name="concat-function"></a>Concat-Funktion

Legen Sie für diese Beispiele die **Text** -Eigenschaft einer Bezeichnung auf eine Formel aus der ersten Spalte der folgenden Tabelle.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Concat( Products; Name & ", " )** | Wertet den Ausdruck **Name der & ","** für jeden Datensatz der **Produkte** und die Ergebnisse in eine einzelne Zeichenfolge verkettet.  | "Violine,&nbsp;Cello,&nbsp;Trumpet,&nbsp;" |
| **Concat( Filter(&nbsp;Products;&nbsp;Type&nbsp;=&nbsp;"String"&nbsp;); Name & ", " )** | Wertet die Formel **Name der & ","** für jeden Datensatz der **Produkte** , die den Filter entspricht **Typ = "String"** , und die Ergebnisse in einer Zeichenfolge verkettet.   | "Violine,&nbsp;Cello,&nbsp;" |

### <a name="trimming-the-end"></a>Verkürzen des Endes

Die letzten beiden Beispiele enthalten zusätzliche "," am Ende des Resultsets. Fügt die Funktion, ein Komma und ein Leerzeichen, die **Namen** Wert, der jeder Datensatz in der Tabelle, einschließlich des letzten Datensatzes.

In einigen Fällen sind diese zusätzlichen Zeichen zulässig. Z. B. einen ersten Trennzeichen nicht angezeigt, wenn Sie das Ergebnis in eine Bezeichnung angezeigt. Wenn Sie diese zusätzlichen Zeichen entfernen möchten, verwenden Sie die [ **Links** ](function-left-mid-right.md) oder [ **Übereinstimmung** ](function-ismatch.md) Funktion.

Legen Sie für diese Beispiele die **Text** -Eigenschaft einer Bezeichnung auf eine Formel aus der ersten Spalte der folgenden Tabelle.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Links ("concat" (&nbsp;Produkte&nbsp;Namen&nbsp;&&nbsp;",&nbsp;"&nbsp;), Len (&nbsp;"concat" (&nbsp;Produkte&nbsp;Namen&nbsp; & &nbsp;",&nbsp;"&nbsp;)&nbsp;)&nbsp;-&nbsp;2)** | Gibt das Ergebnis des **"concat"** aber entfernt die letzten beiden Zeichen, die das überflüssige Trennzeichen zu bilden. | "Violine,&nbsp;Cello,&nbsp;Trumpet" |
| **Übereinstimmung ("concat" (&nbsp;Produkte&nbsp;Namen&nbsp;&&nbsp;",&nbsp;"&nbsp;), "^ (?&lt; Trim&gt;. *),&nbsp;$") .trim** | Gibt die Zeichen des **"concat"** vom Anfang der Zeichenfolge (^) am Ende ($), aber nicht die unerwünschte Komma und Leerzeichen am Ende enthält. | "Violine,&nbsp;Cello,&nbsp;Trumpet" |

### <a name="split-and-matchall"></a>Teilen und MatchAll

Wenn Sie verwendet **"concat"** mit einem Trennzeichen, können Sie den Vorgang umkehren, aus der **Split** und **MatchAll** Funktionen.

Diese Beispiele hinzufügen, einen Katalog leer, vertikalen, legen Sie seine **Elemente** -Eigenschaft auf eine Formel in der folgenden Tabelle, und fügen Sie dann in der Katalogvorlage eine Bezeichnung hinzu.

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Split ("concat" (&nbsp;Produkte&nbsp;Namen&nbsp;&&nbsp;",&nbsp;"&nbsp;), ",")** | Teilt die Zeichenfolge mit dem Trennzeichen **","** . Damit die letzte Zeile in das Ergebnis eine leere Zeichenfolge ist, endet die Zeichenfolge durch ein Komma und Leerzeichen.  | ![Table](media/function-concatenate/split.png) |
| **MatchAll ("concat" (&nbsp;Produkte&nbsp;Namen&nbsp;&&nbsp;",&nbsp;"&nbsp;); "[^ \s,]+"). FullMatch** | Teilt die Zeichenfolge anhand der Zeichen, die Leerzeichen oder Kommas sind. Diese Formel wird entfernt, die zusätzliches Komma und Leerzeichen am Ende der Zeichenfolge. | ![Table](media/function-concatenate/matchall.png)
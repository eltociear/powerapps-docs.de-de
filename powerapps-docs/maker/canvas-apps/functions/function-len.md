---
title: Funktion „Len“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Len-Funktion in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 07b706d9cc0a61e204669646734cdcaf7fc50946
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730635"
ms.PowerAppsDecimalTransform: true
---
# <a name="len-function-in-power-apps"></a>Len-Funktion in powerapps
Gibt die Länge einer Textzeichenfolge zurück

## <a name="description"></a>Beschreibung
Wenn Sie eine einzelne Zeichenfolge als Argument angeben, entspricht der Rückgabewert der Länge als Zahl.  Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) angeben, die Zeichenfolgen enthält, ist der Rückgabewert eine einspaltige Tabelle, die die Länge jeder Zeichenfolge enthält. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

Wenn Sie eine [leere](function-isblank-isempty.md) Zeichenfolge angeben, gibt **len** 0 zurück.

## <a name="syntax"></a>Syntax
**Len**( *String* )

* *Zeichenfolge*: erforderlich. Die zu messende Zeichenfolge.

**Len**( *EinspaltigeTabelle* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die gemessen werden sollen.

## <a name="examples"></a>Beispiele
### <a name="single-string"></a>Einzelne Zeichenfolge
Bei den Beispielen in diesem Abschnitt ist die [Datenquelle](../working-with-data-sources.md) ein Texteingabe-Steuerelement mit dem Namen **Author**, das die Zeichenfolge „E. E. Cummings“.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Len( Author.Text )** |Misst die Länge der Zeichenfolge im **Autor**-Steuerelement. |14 |
| **Len( "" )** |Misst die Länge einer leeren Zeichenfolge. |0 |

### <a name="single-column-table"></a>Einspaltige Tabelle
Für das erste Beispiel in diesem Abschnitt erhält die Datenquelle den Namen **People** und enthält die folgenden Daten:

![](media/function-len/people-table.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Len( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;) )** |In der **Adress**[-Spalte](../working-with-tables.md#columns) der **People**-Tabelle:<br><ul><li>Misst die Länge jeder einzelnen Zeichenfolge.</li><li>Gibt eine einspaltige Tabelle zurück, die die Länge jeder einzelnen Zeichenfolge enthält.</li> |<style> img { max-width: none } </style> ![](media/function-len/people-table-len.png) |
| **Len( [ "Hello"; "to the"; "World"; "" ] )** |In der **[Value](function-value.md)** -Spalte der linearen Tabelle:<br><ul><li>Misst die Länge jeder einzelnen Zeichenfolge.</li><li>Gibt eine einspaltige Tabelle zurück, die die Länge jeder einzelnen Zeichenfolge enthält.</li> |![](media/function-len/people-table-len-inline.png) |


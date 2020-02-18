---
title: Funktionen „Left“, „Mid“ und „Right“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen "Left", "Mid" und "Right" in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/07/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 2a8f89dff09d34d7492f325f54f73c4c736adc24
ms.sourcegitcommit: ee1960fe32136a621e653d6ff2f13d87017830a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77145412"
ms.PowerAppsDecimalTransform: true
---
# <a name="left-mid-and-right-functions-in-power-apps"></a>Funktionen "Left", "Mid" und "Right" in powerapps
Extrahiert die linken, mittleren oder rechten Teil einer Textzeichenfolge

## <a name="description"></a>Beschreibung
Die Funktionen **Left**, **Mid** und **Right** geben einen Teil einer Zeichenfolge zurück.

* **Left** gibt die ersten Zeichen einer Zeichenfolge zurück.
* **Mid** gibt die mittleren Zeichen einer Zeichenfolge zurück.
* **Right** gibt die letzten Zeichen einer Zeichenfolge zurück.

Wenn Sie eine einzelne Zeichenfolge als Argument angeben, gibt die Funktion den Teil der Zeichenfolge zurück, den Sie angefordert haben. Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) mit einer Zeichenfolge angeben, gibt die Funktion eine einspaltige Tabelle aus den Teilen der Zeichenfolge zurück, die Sie angefordert haben. Mehrspaltige Tabellen können, wenn angegeben, in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

Ist die Anfangsposition negativ oder hinter dem Ende des Strings, gibt die **Mid**-Funktion eine *leere* Zeichenfolge zurück.  Mithilfe der **[Len](function-len.md)** -Funktion kann die Länge einer Zeichenfolge überprüft werden. Wenn mehr Zeichen angefordert werden als die Zeichenfolge enthält, gibt die Funktion so viele Zeichen wie möglich zurück.

## <a name="syntax"></a>Syntax
**Left**( *Zeichenfolge*; *AnzahlDerZeichen* )<br>**Mid**( *Zeichenfolge*; *StartingPosition* [; *anzahlungenzeichen* ])<br>**Right**( *Zeichenfolge*; *AnzahlDerZeichen* )

* *Zeichenfolge*: erforderlich. Die Zeichenfolge, aus der das Ergebnis extrahiert werden soll
* *Anfangsposition*: erforderlich (nur bei **Mid**).  Die Anfangsposition.  Das erste Zeichen von der Zeichenfolge befindet sich an Position 1.
* *Anzahlungzeichen* : erforderlich (nur**Links** und **Rechts** ).  Die Anzahl der zurückzugebenden Zeichen.  Wenn der Wert für die **Mid** -Funktion weggelassen wird, gibt die-Funktion den Teil von der Anfangsposition bis zum Ende der Zeichenfolge zurück.

**Left**( *einspaltigeTabelle*; *AnzahlDerZeichen* )<br>**Mid**( *singlecolumntable*; *StartingPosition* [; *anzahlenzeichen* ])<br>**Right**( *einspaltigeTabelle*; *AnzahlDerZeichen* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle aus Zeichenfolgen, aus denen die Ergebnisse extrahiert werden sollen
* *Anfangsposition*: erforderlich (nur bei **Mid**).  Die Anfangsposition.  Das erste Zeichen von der Zeichenfolge befindet sich an Position 1.
* *Anzahlungzeichen* : erforderlich (nur**Links** und **Rechts** ).  Die Anzahl der zurückzugebenden Zeichen.  Wenn der Wert für die **Mid** -Funktion weggelassen wird, gibt die-Funktion den Teil von der Anfangsposition bis zum Ende der Zeichenfolge zurück.

## <a name="examples"></a>Beispiele
### <a name="single-string"></a>Einzelne Zeichenfolge
In den Beispielen in diesem Abschnitt wird ein Texteingabe-Steuerelement als [Datenquelle](../working-with-data-sources.md) verwendet. Das Steuerelement hat den Namen **Autor** und enthält die Zeichenfolge „E. E. Cummings“.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Left( Author.Text; 5 )** |Extrahiert bis zu fünf Zeichen vom Anfang der Zeichenfolge |„E. E.“ |
| **Mid( Author.Text; 7; 4 )** |Extrahiert ab dem siebten Zeichen bis zu vier Zeichen aus der Zeichenfolge |„Cumm“ |
| **Mid (Author. Text, 7)** |Extrahiert alle Zeichen, beginnend mit dem siebten Zeichen, aus der Zeichenfolge. |"Cummings" |
| **Right( Author.Text; 5 )** |Extrahiert bis zu fünf Zeichen aus dem Ende der Zeichenfolge |„mings“ |

### <a name="single-column-table"></a>Einspaltige Tabelle
In jedem Beispiel in diesem Abschnitt werden Zeichen folgen aus der **Adress** [Spalte](../working-with-tables.md#columns) der Datenquelle namens **People**extrahiert, und es wird eine einspaltige Tabelle mit den Ergebnissen zurückgegeben:

![](media/function-left-mid-right/people-table.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Left( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;); 8 )** |Extrahiert die ersten acht Zeichen einer Zeichenfolge |<style>IMG {max-width: None}</style> ![](media/function-left-mid-right/people-table-left.png) |
| **Mid( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;); 5; 7 )** |Extrahiert ab dem fünften Zeichen die mittleren sieben Zeichen einer Zeichenfolge |![](media/function-left-mid-right/people-table-mid.png) |
| **Right( ShowColumns(&nbsp;People;&nbsp;"Address"&nbsp;); 7 )** |Extrahiert die letzten sieben Zeichen einer Zeichenfolge |![](media/function-left-mid-right/people-table-right.png) |

### <a name="step-by-step-example"></a>Schritt-für-Schritt-Beispiel
1. Importieren oder erstellen Sie eine [Sammlung](../working-with-data-sources.md#collections) namens **Inventory** (Inventar), und zeigen Sie sie in einem Katalog an. Dies wird im ersten Verfahren unter [Anzeigen von Bildern und Text in einem Katalog](../show-images-text-gallery-sort-filter.md) beschrieben.
2. Legen Sie die **[Text](../controls/properties-core.md)** -Eigenschaft der unteren Beschriftung im Katalog auf diese Funktion fest:
   
    **Right(ThisItem.ProductName; 3)**
   
    Die Bezeichnung zeigt die letzten drei Zeichen eines jeden Produktnamens an.


---
title: "Funktionen „Left“, „Mid“ und „Right“ | Microsoft-Dokumentation"
description: "Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Left“, „Mid“ und „Right“ in PowerApps"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 2cf54b1225578b2bb2bdefa8c0bd02dc0c9c0283
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="left-mid-and-right-functions-in-powerapps"></a>Die Funktionen „Left“, „Mid“ und „Right“ in PowerApps
Extrahiert die linken, mittleren oder rechten Teil einer Textzeichenfolge

## <a name="description"></a>Beschreibung
Die Funktionen **Left**, **Mid** und **Right** geben einen Teil einer Zeichenfolge zurück.

* **Left** gibt die ersten Zeichen einer Zeichenfolge zurück.
* **Mid** gibt die mittleren Zeichen einer Zeichenfolge zurück.
* **Right** gibt die letzten Zeichen einer Zeichenfolge zurück.

Wenn Sie eine einzelne Zeichenfolge als Argument angeben, gibt die Funktion den Teil der Zeichenfolge zurück, den Sie angefordert haben. Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) mit einer Zeichenfolge angeben, gibt die Funktion eine einspaltige Tabelle aus den Teilen der Zeichenfolge zurück, die Sie angefordert haben. Mehrspaltige Tabellen können, wenn angegeben, in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

Ist die Anfangsposition negativ oder hinter dem Ende des Strings, gibt die **Mid**-Funktion eine *leere* Zeichenfolge zurück.  Mithilfe der **[Len](function-len.md)**-Funktion kann die Länge einer Zeichenfolge überprüft werden. Wenn mehr Zeichen angefordert werden als die Zeichenfolge enthält, gibt die Funktion so viele Zeichen wie möglich zurück.

## <a name="syntax"></a>Syntax
**Left**( *Zeichenfolge*, *AnzahlDerZeichen* )<br>**Mid**( *Zeichenfolge*, *Anfangsposition*, *AnzahlDerZeichen* )<br>**Right**( *Zeichenfolge*, *AnzahlDerZeichen* )

* *Zeichenfolge*: erforderlich. Die Zeichenfolge, aus der das Ergebnis extrahiert werden soll
* *Anfangsposition*: erforderlich (nur bei **Mid**).  Die Anfangsposition.  Das erste Zeichen von der Zeichenfolge befindet sich an Position 1.
* *AnzahlDerZeichen*: erforderlich.  Die Anzahl der zu zurückzugebenden Zeichen

**Left**( *einspaltigeTabelle*, *AnzahlDerZeichen* )<br>**Mid**( *einspaltigeTabelle*, *Anfangsposition*, *AnzahlDerZeichen* )<br>**Right**( *einspaltigeTabelle*, *AnzahlDerZeichen* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle aus Zeichenfolgen, aus denen die Ergebnisse extrahiert werden sollen
* *Anfangsposition*: erforderlich (nur bei **Mid**).  Die Anfangsposition.  Das erste Zeichen von der Zeichenfolge befindet sich an Position 1.
* *AnzahlDerZeichen*: erforderlich.  Die Anzahl der zu zurückzugebenden Zeichen

## <a name="examples"></a>Beispiele
### <a name="single-string"></a>Einzelne Zeichenfolge
In den Beispielen in diesem Abschnitt wird ein Texteingabe-Steuerelement als [Datenquelle](../working-with-data-sources.md) verwendet. Das Steuerelement hat den Namen **Autor** und enthält die Zeichenfolge „E. E. Cummings“.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Left( Author.Text, 5 )** |Extrahiert bis zu fünf Zeichen vom Anfang der Zeichenfolge |„E. E.“ |
| **Mid( Author.Text, 7, 4 )** |Extrahiert ab dem siebten Zeichen bis zu vier Zeichen aus der Zeichenfolge |„Cumm“ |
| **Right( Author.Text, 5 )** |Extrahiert bis zu fünf Zeichen aus dem Ende der Zeichenfolge |„mings“ |

### <a name="single-column-table"></a>Einspaltige Tabelle
In jedem Beispiel in diesem Abschnitt werden Zeichenfolgen aus der **Adress**[spalte](../working-with-tables.md#columns) dieser Datenquelle namens **People** (Personen) extrahiert, und es wird eine einspaltige Tabelle mit den Ergebnissen zurückgegeben:

![](media/function-left-mid-right/people-table.png)

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Left( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 8 )** |Extrahiert die ersten acht Zeichen einer Zeichenfolge |<style> img { max-width: none } </style> ![](media/function-left-mid-right/people-table-left.png) |
| **Mid( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 5, 7 )** |Extrahiert ab dem fünften Zeichen die mittleren sieben Zeichen einer Zeichenfolge |![](media/function-left-mid-right/people-table-mid.png) |
| **Right( ShowColumns(&nbsp;People,&nbsp;"Address"&nbsp;), 7 )** |Extrahiert die letzten sieben Zeichen einer Zeichenfolge |![](media/function-left-mid-right/people-table-right.png) |

### <a name="step-by-step-example"></a>Schritt-für-Schritt-Beispiel
1. Importieren oder erstellen Sie eine [Sammlung](../working-with-data-sources.md#collections) namens **Inventory** (Inventar), und zeigen Sie sie in einem Katalog an. Dies wird im ersten Verfahren unter [Anzeigen von Bildern und Text in einem Katalog](../show-images-text-gallery-sort-filter.md) beschrieben.
2. Legen Sie die **[Text](../controls/properties-core.md)**-Eigenschaft der unteren Beschriftung im Katalog auf diese Funktion fest:
   
    **Right(ThisItem.ProductName, 3)**
   
    Die Bezeichnung zeigt die letzten drei Zeichen eines jeden Produktnamens an.


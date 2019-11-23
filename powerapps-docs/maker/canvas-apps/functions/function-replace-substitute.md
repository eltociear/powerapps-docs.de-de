---
title: Funktionen „Replace“ und „Substitute“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen „Replace“ und „Substitute“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ff0e016f6ab1ad4f66651ccd3cfa2711f1d85a38
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992384"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>Die Funktionen „Replace“ und „Substitute“ in PowerApps
Ersetzen Sie einen Teil einer Textzeichenfolge durch eine andere Zeichenfolge.

## <a name="description"></a>Beschreibung
Die **Replace**-Funktion identifiziert den zu ersetzenden Text anhand der Anfangsposition und Länge.  

Die **Substitute**-Funktion identifiziert den zu ersetzenden Text anhand einer Übereinstimmung mit einer Zeichenfolge. Wenn mehrere Übereinstimmungen gefunden werden, können Sie alle ersetzen oder eine zum Ersetzen angeben.

Wenn Sie eine einzelne Zeichenfolge übergeben, ist der Rückgabewert die geänderte Zeichenfolge. Wenn Sie eine einspaltige [Tabelle](../working-with-tables.md) übergeben, die Zeichenfolgen enthält, ist der Rückgabewert eine einspaltige Tabelle mit geänderten Zeichenfolgen. Mehrspaltige Tabellen können in einspaltige Tabellen umgeformt werden, wie unter [Arbeiten mit Tabellen](../working-with-tables.md) beschrieben.

## <a name="syntax"></a>Syntax
**Replace**( *String*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *Zeichenfolge*: erforderlich. Die zu verarbeitende Zeichenfolge
* *Anfangsposition*: erforderlich. Zeichenposition, ab der ersetzt werden soll. Das erste Zeichen von *String* befindet sich an Position 1.
* *AnzahlDerZeichen*: erforderlich. Die Anzahl der zu ersetzenden Zeichen in *String*
* *NeueZeichenfolge*: erforderlich. Die Ersatzzeichenfolge. Die Anzahl der Zeichen in diesem Argument kann sich von dem *NumberOfCharacters*-Argument unterscheiden.

**Substitute**( *Zeichenfolge*, *alte Zeichenfolge*, *NewString* [, *InstanceNumber* ])

* *Zeichenfolge*: erforderlich. Die zu verarbeitende Zeichenfolge
* *AlteZeichenfolge*: erforderlich. Die zu ersetzende Zeichenfolge
* *NeueZeichenfolge*: erforderlich. Die Ersatzzeichenfolge. *AlteZeichenfolge* und *NeueZeichenfolge* können unterschiedlich lang sein.
* *AnzahlDerInstanzen*: optional. Verwenden Sie dieses Argument, um anzugeben, welche Instanz von *oldstring* ersetzt werden soll, wenn die *Zeichenfolge* mehr als eine Instanz enthält. Wenn Sie dieses Argument nicht angeben, werden alle Instanzen ersetzt.

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die verarbeitet werden sollen.
* *Anfangsposition*: erforderlich. Zeichenposition, ab der ersetzt werden soll.  Das erste Zeichen einer jeden Zeichenfolge in der Tabelle ist an Position 1.
* *AnzahlDerZeichen*: erforderlich. Die Zahl der zu ersetzenden Zeichen in jeder Zeichenfolge
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. Die Anzahl der Zeichen in diesem Argument kann sich von dem *NumberOfCharacters*-Argument unterscheiden.

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die verarbeitet werden sollen.
* *AlteZeichenfolge*: erforderlich.  Die zu ersetzende Zeichenfolge
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. *AlteZeichenfolge* und *NeueZeichenfolge* können unterschiedlich lang sein.
* *AnzahlDerInstanzen*: optional. Verwenden Sie dieses Argument, um anzugeben, welche Instanz von *oldstring* ersetzt werden soll, wenn die *Zeichenfolge* mehr als eine Instanz enthält. Wenn Sie dieses Argument nicht angeben, werden alle Instanzen ersetzt.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Replace ("abcdefghijk",&nbsp;6,&nbsp;5,&nbsp;"*")** | Ersetzt fünf Zeichen in "abcdefghijk" durch ein einzelnes "*"-Zeichen, beginnend mit dem sechsten Zeichen ("f"). | "abcde * k" |
| **Replace (&nbsp;"2019",&nbsp;3,&nbsp;2,&nbsp;"20"&nbsp;)** | Ersetzt die letzten zwei Zeichen von "2019" durch "20". | "2020" |
| **Replace (&nbsp;"123456",&nbsp;1,&nbsp;3,&nbsp;"_"&nbsp;)** | Ersetzt die ersten drei Zeichen von "123456" durch ein einzelnes "_"-Zeichen. | "_456" | 
| **Ersetzen Sie (&nbsp;"Sales&nbsp;Data",&nbsp;"Sales",&nbsp;"Cost"&nbsp;).** | Ersetzt die Zeichenfolge "Cost" für "Sales". | "Kostendaten" | 
| **Ersatz ("Quarter&nbsp;1,&nbsp;2018", "1", "2", 1)** | Ersetzt nur die erste Instanz von "1" durch "2", da das vierte Argument (*instancenverber*) mit 1 bereitgestellt wird. |  "Quartal 2, 2018" |
| **Ersatz ("Quarter&nbsp;1,&nbsp;2011", "1", "2", 3)** | Ersetzt nur die dritte Instanz von "1" durch "2", da das vierte Argument (*Instanznummer*) mit einem 3 bereitgestellt wird. | "Quartal 1, 2012" |
| **Ersatz ("Quarter&nbsp;1,&nbsp;2011", "1", "2")** | Ersetzt alle Instanzen von "1" durch "2", da das vierte Argument (*instancenverber*) nicht bereitgestellt wird. | "Quartal 2, 2022" |
| **Replace (<br>[&nbsp;"Quarter&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;2,&nbsp;2011",<br>"Quarter&nbsp;4,&nbsp;2019"],<br>9, 1, "3")** | Ersetzt das neunte Zeichen in jedem Datensatz der einspaltigen Tabelle durch "3". | [&nbsp;"Quarter&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"Quartal&nbsp;3,&nbsp;2019"&nbsp;] |
| **Ersatz (<br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3", 1)** | Da das vierte Argument (*instancenenumber*) mit einem Wert von 1 angegeben wird, ersetzt nur die erste Instanz von "1" in jedem Datensatz der einspaltigen Tabelle mit "3". | [&nbsp;"Qtr&nbsp;3,&nbsp;2018",<br>"Quarter&nbsp;3,&nbsp;2011",<br>"Q3,&nbsp;2019"&nbsp;] |
| **Ersatz (<br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quartal&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3")** | Da das vierte Argument (*instancenverber*) nicht bereitgestellt wird, ersetzt alle Instanzen von "1" in jedem Datensatz der einspaltigen Tabelle mit "3". | [&nbsp;"Qtr&nbsp;3,&nbsp;2038",<br>"Quarter&nbsp;3,&nbsp;2033",<br>"Q3,&nbsp;2039"&nbsp;] |  
 



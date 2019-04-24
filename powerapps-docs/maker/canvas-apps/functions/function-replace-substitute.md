---
title: Funktionen „Replace“ und „Substitute“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax für die Funktionen „Replace“ und „Substitute“ in PowerApps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/02/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fca1953402c87ca13bc3560b827cde03a47a8e92
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551604"
---
# <a name="replace-and-substitute-functions-in-powerapps"></a>Die Funktionen „Replace“ und „Substitute“ in PowerApps
Ersetzen Sie einen Teil einer Textzeichenfolge durch eine andere Zeichenfolge.

## <a name="description"></a>Beschreibung
Die **Replace**-Funktion identifiziert den zu ersetzenden Text anhand der Anfangsposition und Länge.  

Die **Substitute**-Funktion identifiziert den zu ersetzenden Text anhand einer Übereinstimmung mit einer Zeichenfolge. Wenn mehr als eine Übereinstimmung gefunden wird, können Sie alle ersetzen oder geben Sie einen ersetzen.

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
* *AnzahlDerInstanzen*: optional. Verwenden Sie dieses Argument an die Instanz von *Altezeichenfolge* Wenn ersetzen *Zeichenfolge* enthält mehr als eine Instanz. Wenn Sie dieses Argument nicht angeben, werden alle Instanzen ersetzt werden.

**Replace**( *SingleColumnTable*, *StartingPosition*, *NumberOfCharacters*, *NewString* )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die verarbeitet werden sollen.
* *Anfangsposition*: erforderlich. Zeichenposition, ab der ersetzt werden soll.  Das erste Zeichen einer jeden Zeichenfolge in der Tabelle ist an Position 1.
* *AnzahlDerZeichen*: erforderlich. Die Zahl der zu ersetzenden Zeichen in jeder Zeichenfolge
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. Die Anzahl der Zeichen in diesem Argument kann sich von dem *NumberOfCharacters*-Argument unterscheiden.

**Substitute**( *SingleColumnTable*, *OldString*, *NewString* [, *InstanceNumber* ] )

* *EinspaltigeTabelle*: erforderlich. Eine einspaltige Tabelle mit Zeichenfolgen, die verarbeitet werden sollen.
* *AlteZeichenfolge*: erforderlich.  Die zu ersetzende Zeichenfolge
* *NeueZeichenfolge*: erforderlich.  Die Ersatzzeichenfolge. *AlteZeichenfolge* und *NeueZeichenfolge* können unterschiedlich lang sein.
* *AnzahlDerInstanzen*: optional. Verwenden Sie dieses Argument an die Instanz von *Altezeichenfolge* Wenn ersetzen *Zeichenfolge* enthält mehr als eine Instanz. Wenn Sie dieses Argument nicht angeben, werden alle Instanzen ersetzt werden.

## <a name="examples"></a>Beispiele

| Formel | Beschreibung | Ergebnis |
|---------|-------------|--------|
| **Replace( "abcdefghijk",&nbsp;6,&nbsp;5,&nbsp;"*" )** | Ersetzt "Abcdefghijk" fünf Zeichen mit einem einzelnen "*"-Zeichen, beginnend mit dem sechsten Zeichen ("f"). | "abcde*k" |
| **Ersetzen (&nbsp;"2019",&nbsp;3,&nbsp;2&nbsp;"20"&nbsp;)** | Ersetzt die letzten beiden Zeichen von "2019" mit "20". | "2020" |
| **Ersetzen (&nbsp;"123456",&nbsp;1&nbsp;3,&nbsp;"_"&nbsp;)** | Ersetzt die ersten drei Zeichen des "123456" mit einem einzelnen "_"-Zeichen. | "_456" | 
| **Ersetzen (&nbsp;"Sales&nbsp;Daten",&nbsp;"Vertrieb"&nbsp;"Kosten"&nbsp;)** | Ersetzt die Zeichenfolge "Kosten" für "Sales". | "Kostendaten" | 
| **Substitute( "Quarter&nbsp;1,&nbsp;2018", "1", "2", 1 )** | Nur die erste Instanz von "1" mit "2" ersetzt, da das vierte Argument (*InstanceNumber*) wird mit 1 bereitgestellt. |  "Quartal 2, 2018" |
| **Substitute( "Quarter&nbsp;1,&nbsp;2011", "1", "2", 3 )** | Nur die dritte Instanz von "1" mit "2" ersetzt, da das vierte Argument (*InstanceNumber*) wird mit einem 3 bereitgestellt. | "Quartal 1, 2012" |
| **Substitute( "Quarter&nbsp;1,&nbsp;2011", "1", "2" )** | Ersetzt alle Instanzen von "1" mit "2", da das vierte Argument (*InstanceNumber*) ist nicht enthalten. | "Quartal 2, 2022" |
| **Ersetzen (<br>[&nbsp;"Quartal&nbsp;1&nbsp;2018",<br>"Quartal&nbsp;2,&nbsp;2011"<br>"Quartal&nbsp;4&nbsp;2019"],<br>9 "," 1 ","3")** | Das neunte Zeichen in jedem Datensatz der einspaltige Tabelle mit "3" ersetzt. | [&nbsp;"Quartal&nbsp;3,&nbsp;2018",<br>"Quartal&nbsp;3,&nbsp;2011",<br>"Quarter&nbsp;3,&nbsp;2019"&nbsp;] |
| **Substitute( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3", 1 )** | Da das vierte Argument (*InstanceNumber*) erfolgt mit dem Wert 1, ersetzt nur die erste Instanz von "1" in jedem Datensatz der einspaltige Tabelle mit "3". | [&nbsp;"Qtr&nbsp;3,&nbsp;2018",<br>"Quartal&nbsp;3,&nbsp;2011",<br>"Q3,&nbsp;2019"&nbsp;] |
| **Substitute( <br>[&nbsp;"Qtr&nbsp;1,&nbsp;2018",<br>"Quarter&nbsp;1,&nbsp;2011",<br>"Q1,&nbsp;2019"&nbsp;],<br>"1", "3" )** | Da das vierte Argument (*InstanceNumber*) ist nicht angegeben wird, ersetzt alle Instanzen von "1" in jedem Datensatz der einspaltige Tabelle mit "3". | [&nbsp;"Qtr&nbsp;3,&nbsp;2038",<br>"Quartal&nbsp;3,&nbsp;2033",<br>"Q3,&nbsp;2039"&nbsp;] |  
 



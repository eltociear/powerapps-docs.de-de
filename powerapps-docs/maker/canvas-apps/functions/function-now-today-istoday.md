---
title: "Funktionen „Now“, „Today“ und „IsToday“ | Microsoft-Dokumentation"
description: "Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktionen „Now“, „Today“ und „IsToday“ in PowerApps"
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
ms.openlocfilehash: 483922d2c96c23d1d2672aed7e284e30d38f298a
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="now-today-and-istoday-functions-in-powerapps"></a>Die Funktionen „Now“, „Today“ und „IsToday“ in PowerApps
Gibt das aktuelle Datum und die Uhrzeit zurück und prüft, ob ein Datum/Uhrzeit-Wert heute ist

## <a name="description"></a>Beschreibung
Die **Now**-Funktion gibt das aktuelle Datum und die Uhrzeit als Datum/Uhrzeit-Wert zurück.

Die **Today**-Funktion gibt das aktuelle Datum als Datum/Uhrzeit-Wert zurück. Der Uhrzeitanteil ist Mitternacht. **Today** hat den gesamten Tag (ab Mitternacht heute bis Mitternacht morgen) den gleichen Wert.

Die **IsToday**-Funktion testet, ob ein Datum/Uhrzeit-Wert zwischen Mitternacht heute und Mitternacht morgen liegt. Diese Funktion gibt einen booleschen Wert zurück, der **TRUE** oder **FALSE** ist.

Alle diese Funktionen funktionieren mit der lokalen Zeit des aktuellen Benutzers.

Weitere Informationen finden Sie unter [Arbeiten mit Datums- und Uhrzeitangaben](../show-text-dates-times.md).

## <a name="syntax"></a>Syntax
**Now**()

**Today**()

**IsToday**( *DateTime* )

* *DatumUhrzeit*: erforderlich.  Der zu prüfende Datum/Uhrzeit-Wert.

## <a name="examples"></a>Beispiele
Für die Beispiele in diesem Abschnitt ist die aktuelle Uhrzeit **3:59 Uhr** am **12. Februar 2015**, und die Sprache ist **En-US**.

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Text( Now(), "mm/dd/yyyy hh:mm:ss" )** |Ruft das aktuelle Datum und die Uhrzeit ab und zeigt sie als Zeichenfolge an |„02/12/2015 03:59:00“ |
| **Text( Today(), "mm/dd/yyyy hh:mm:ss" )** |Ruft nur das aktuelle Datum ab, sodass der Zeitanteil auf Mitternacht festgelegt bleibt, und zeigt dieses als Zeichenfolge an |„02/12/2015 00:00:00“ |
| **IsToday( Now() )** |Prüft, ob das aktuelle Datum und die Uhrzeit zwischen Mitternacht heute und Mitternacht morgen liegen |**TRUE** |
| **IsToday( Today() )** |Prüft, ob das aktuelle Datum zwischen Mitternacht heute und Mitternacht morgen liegt |**TRUE** |
| **Text( DateAdd( Now(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |Ruft das aktuelle Datum und die Uhrzeit ab, fügt dem aktuellen Datum 12 Tage hinzu und zeigt es als Zeichenfolge an |„02/24/2015 03:59:00“ |
| **Text( DateAdd( Today(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |Ruft das aktuelle Datum ab, das Ergebnis 12 Tage hinzugefügt, und zeigt ihn als Zeichenfolge |„02/24/2015 00:00:00“ |
| **IsToday( DateAdd( Now(), 12 ) )** |Prüft, ob das aktuelle Datum und die Uhrzeit plus 12 Tage zwischen Mitternacht heute und Mitternacht morgen liegen |**FALSE** |
| **IsToday( DateAdd( Today(), 12 ) )** |Prüft, ob das aktuelle Datum plus 12 Tage zwischen Mitternacht heute und Mitternacht morgen liegt |**FALSE** |


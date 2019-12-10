---
title: Funktion „Split“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Split-Funktion in powerapps
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d58c4b64f558ec2a9348a9a9433b9a55f69419db
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730104"
ms.PowerAppsDecimalTransform: true
---
# <a name="split-function-in-power-apps"></a>Split-Funktion in powerapps
Teilt eine Textzeichenfolge in eine Tabelle von Teilzeichenfolgen auf.

## <a name="description"></a>Beschreibung
Die **Split**-Funktion teilt eine Textzeichenfolge in eine Tabelle von Teilzeichenfolgen auf.  Mit der **Split**-Funktion können Sie durch Trennzeichen getrennte Listen, Datumsangaben, deren Komponenten durch einen Schrägstrich getrennt sind, und andere Zeichenfolgen, in denen ein eindeutiges Trennzeichen verwendet wird, aufteilen.  

Zum Aufteilen der Textzeichenfolge wird ein Trennzeichen verwendet.  Bei dem Trennzeichen kann es sich um 0 (null), ein oder mehr Zeichen handeln, die als Ganzes in der Textzeichenfolge verglichen werden.  Bei Verwendung einer Zeichenfolge der Länge 0 (null) bzw. einer *leeren* Zeichenfolge wird jedes Zeichen einzeln herausgetrennt.  Die verglichenen Trennzeichen werden nicht im Ergebnis zurückgegeben.  Wenn kein übereinstimmendes Trennzeichen gefunden wird, wird die gesamte Textzeichenfolge als einzelnes Ergebnis zurückgegeben.

Verwenden Sie die **[Concat](function-concatenate.md)** -Funktion, um die Zeichenfolge ohne Trennzeichen erneut zu kombinieren. 
 
Verwenden Sie die **[MatchAll](function-ismatch.md)** -Funktion, um eine Zeichenfolge mit einem regulären Ausdruck aufzuteilen.

In den Beispielen wird gezeigt, wie **Split** mit den **[ersten](function-first-last.md)** und **[letzten](function-first-last.md)** Funktionen verwendet werden kann, um eine einzelne Zeichenfolge mit Trennzeichen zu extrahieren.  Die **[Match](function-ismatch.md)** -Funktion ist oft eine präzisere und leistungsfähigere Wahl für diejenigen, die mit regulären Ausdrücken vertraut sind.

## <a name="syntax"></a>Syntax
**Split**( *Text*; *Trennzeichen* )

* *Text*: erforderlich.  Der aufzuteilende Text.
* *Trennzeichen*: erforderlich.  Das beim Aufteilen der Zeichenfolge zu verwendende Trennzeichen.  Dieses kann 0 (null), ein oder mehr Zeichen umfassen.

## <a name="examples"></a>Beispiele

### <a name="basic-usage"></a>Grundlegende Nutzung

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| `Split( "Apples, Oranges, Bananas"; "," )` |Teilt die unterschiedlichen Früchte anhand des Kommatrennzeichens auf.  Die Aufteilung erfolgt nur auf Grundlage des Kommas ohne Berücksichtigung des Leerzeichens hinter ihm, sodass vor „&nbsp;Orangen“ und „&nbsp;Bananen“ ein Leerzeichen steht. |<style> img { max-width: none; } </style> ![](media/function-split/fruit1.png) |
| `TrimEnds( Split( "Apples, Oranges, Bananas"; "," ) )` |Wie im vorherigen Beispiel, jedoch wird in diesem Fall das Leerzeichen durch die [ **TrimEnds**-Funktion](function-trim.md) entfernt, die auf die durch die **Split**-Funktion erzeugte Tabelle mit einer einzelnen Spalte angewendet wird. Wir hätten auch das Trennzeichen **„,&nbsp;“** verwenden können, in dem das Trennzeichen nach dem Komma enthalten ist. Bei Verwendung dieses Trennzeichens treten jedoch Probleme auf, wenn kein Leerzeichen oder zwei Leerzeichen vorhanden sind. |<style> img { max-width: none; } </style> ![](media/function-split/fruit2.png) |
| `Split( "08/28/17"; "/" )` |Teilt das Datum auf, wobei als Trennzeichen ein Schrägstrich verwendet wird. |<style> img { max-width: none; } </style> ![](media/function-split/date.png) |

### <a name="different-delimiters"></a>Unterschiedliche Trennzeichen

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| `Split( "Hello, World"; "," )` |Teilt die Wörter auf, wobei als Trennzeichen ein Komma verwendet wird.  Das zweite Ergebnis beginnt mit einem Leerzeichen, da dies das direkt auf das Komma folgende Zeichen war. |<style> img { max-width: none; } </style> ![](media/function-split/comma.png) |
| `Split( "Hello, World"; "o" )` |Teilt die Zeichenfolge auf, wobei als Trennzeichen das Zeichen „o“ verwendet wird. |<style> img { max-width: none; } </style> ![](media/function-split/o.png) |
| `Split( "Hello, World"; "l" )` |Teilt die Zeichenfolge auf, wobei als Trennzeichen das Zeichen „l“ verwendet wird. Da sich zwischen den beiden Buchstaben **l** in **Hello** keine Zeichen befanden, wurde ein *leerer* Wert zurückgegeben. |<style> img { max-width: none; } </style> ![](media/function-split/l.png) |
| `Split( "Hello, World"; "ll" )` |Teilt die Zeichenfolge auf, wobei als Trennzeichen das doppelte Zeichen „ll“ verwendet wird. |<style> img { max-width: none; } </style> ![](media/function-split/ll.png) |
| `Split( "Hello, World"; "%" )` |Teilt die Zeichenfolge auf, wobei als Trennzeichen das Prozentzeichen verwendet wird. Da dieses Trennzeichen nicht in der Zeichenfolge enthalten ist, wird die gesamte Zeichenfolge als ein Ergebnis zurückgegeben. |<style> img { max-width: none; } </style> ![](media/function-split/percent.png) |
| `Split( "Hello, World"; "" )` |Teilt die Zeichenfolge auf, wobei als Trennzeichen eine leere Zeichenfolge (0 Zeichen) verwendet wird. Dadurch wird die Zeichenfolge in jedes einzelne Zeichen aufgeteilt. |<style> img { max-width: none; } </style> ![](media/function-split/none.png) |

### <a name="substring-extraction"></a>Substring-Extraktion

| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| `First( Split( Last( Split( "Bob Jones <bob.jones@contoso.com>"; "<" ) ).Result; ">" ) ).Result` | Teilt die Zeichenfolge auf Grundlage eines öffnenden Trenn Zeichens (<) auf und extrahiert die Zeichenfolge rechts vom Trennzeichen mit der **letzten**.  Die Formel teilt dann das Ergebnis basierend auf dem schließenden Trennzeichen (>) und extrahiert die Zeichenfolge auf der linken Seite des Trenn Zeichens mit der **rechten**Seite. | "bob.jones@contoso.com" |
| `Match( "Bob Jones <bob.jones@contoso.com>"; "<(?<email>.+)>" ).email` | Führt die gleiche Trennzeichen basierte Extraktion wie im letzten Beispiel aus, verwendet jedoch stattdessen die **Match** -Funktion und einen regulären Ausdruck. | "bob.jones@contoso.com" |


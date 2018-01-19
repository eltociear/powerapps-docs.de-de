---
title: "Funktion „Split“ | Microsoft-Dokumentation"
description: "Referenzinformationen einschließlich Syntax und Beispielen für die Split-Funktion in PowerApps"
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
ms.date: 08/28/2017
ms.author: gregli
ms.openlocfilehash: e1953767c40edbe27a232678bdeaab8cebfdea17
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="split-function-in-powerapps"></a>Split-Funktion in PowerApps
Teilt eine Textzeichenfolge in eine Tabelle von Teilzeichenfolgen auf.

## <a name="description"></a>Beschreibung
Die **Split**-Funktion teilt eine Textzeichenfolge in eine Tabelle von Teilzeichenfolgen auf.  Mit der **Split**-Funktion können Sie durch Trennzeichen getrennte Listen, Datumsangaben, deren Komponenten durch einen Schrägstrich getrennt sind, und andere Zeichenfolgen, in denen ein eindeutiges Trennzeichen verwendet wird, aufteilen.  

Zum Aufteilen der Textzeichenfolge wird ein Trennzeichen verwendet.  Bei dem Trennzeichen kann es sich um 0 (null), ein oder mehr Zeichen handeln, die als Ganzes in der Textzeichenfolge verglichen werden.  Bei Verwendung einer Zeichenfolge der Länge 0 (null) bzw. einer *leeren* Zeichenfolge wird jedes Zeichen einzeln herausgetrennt.  Die verglichenen Trennzeichen werden nicht im Ergebnis zurückgegeben.  Wenn kein übereinstimmendes Trennzeichen gefunden wird, wird die gesamte Textzeichenfolge als einzelnes Ergebnis zurückgegeben.

Mit der **[Concat](function-concatenate.md)**-Funktion können Sie die Zeichenfolgen wieder zusammenfügen (ohne die Trennzeichen).  

## <a name="syntax"></a>Syntax
**Split**( *Text*, *Trennzeichen* )

* *Text*: erforderlich.  Der aufzuteilende Text.
* *Trennzeichen*: erforderlich.  Das beim Aufteilen der Zeichenfolge zu verwendende Trennzeichen.  Dieses kann 0 (null), ein oder mehr Zeichen umfassen.

## <a name="examples"></a>Beispiele
| Formel | Beschreibung | Ergebnis |
| --- | --- | --- |
| **Split( "Apples,&nbsp;Oranges,&nbsp;Bananas", "," )** |Teilt die unterschiedlichen Früchte anhand des Kommatrennzeichens auf.  Die Aufteilung erfolgt nur auf Grundlage des Kommas ohne Berücksichtigung des Leerzeichens hinter ihm, sodass vor „&nbsp;Orangen“ und „&nbsp;Bananen“ ein Leerzeichen steht. |<style> img { max-width: none; } </style> ![](media/function-split/fruit1.png) |
| **TrimEnds( Split( "Apples,&nbsp;Oranges,&nbsp;Bananas", "," ) )** |Wie im vorherigen Beispiel, jedoch wird in diesem Fall das Leerzeichen durch die [ **TrimEnds**-Funktion](function-trim.md) entfernt, die auf die durch die **Split**-Funktion erzeugte Tabelle mit einer einzelnen Spalte angewendet wird. Wir hätten auch das Trennzeichen **„,&nbsp;“** verwenden können, in dem das Trennzeichen nach dem Komma enthalten ist. Bei Verwendung dieses Trennzeichens treten jedoch Probleme auf, wenn kein Leerzeichen oder zwei Leerzeichen vorhanden sind. |<style> img { max-width: none; } </style> ![](media/function-split/fruit2.png) |
| **Split( "08/28/17", "/" )** |Teilt das Datum auf, wobei als Trennzeichen ein Schrägstrich verwendet wird. |<style> img { max-width: none; } </style> ![](media/function-split/date.png) |
| **Split( "Hello,&nbsp;World", "," )** |Teilt die Wörter auf, wobei als Trennzeichen ein Komma verwendet wird.  Das zweite Ergebnis beginnt mit einem Leerzeichen, da dies das direkt auf das Komma folgende Zeichen war. |<style> img { max-width: none; } </style> ![](media/function-split/comma.png) |
| **Split( "Hello,&nbsp;World", "o" )** |Teilt die Zeichenfolge auf, wobei als Trennzeichen das Zeichen „o“ verwendet wird. |<style> img { max-width: none; } </style> ![](media/function-split/o.png) |
| **Split( "Hello,&nbsp;World", "l" )** |Teilt die Zeichenfolge auf, wobei als Trennzeichen das Zeichen „l“ verwendet wird. Da sich zwischen den beiden Buchstaben **l** in **Hello** keine Zeichen befanden, wurde ein *leerer* Wert zurückgegeben. |<style> img { max-width: none; } </style> ![](media/function-split/l.png) |
| **Split( "Hello,&nbsp;World", "ll" )** |Teilt die Zeichenfolge auf, wobei als Trennzeichen das doppelte Zeichen „ll“ verwendet wird. |<style> img { max-width: none; } </style> ![](media/function-split/ll.png) |
| **Split( "Hello,&nbsp;World", "%" )** |Teilt die Zeichenfolge auf, wobei als Trennzeichen das Prozentzeichen verwendet wird. Da dieses Trennzeichen nicht in der Zeichenfolge enthalten ist, wird die gesamte Zeichenfolge als ein Ergebnis zurückgegeben. |<style> img { max-width: none; } </style> ![](media/function-split/percent.png) |
| **Split( "Hello,&nbsp;World", "" )** |Teilt die Zeichenfolge auf, wobei als Trennzeichen eine leere Zeichenfolge (0 Zeichen) verwendet wird. Dadurch wird die Zeichenfolge in jedes einzelne Zeichen aufgeteilt. |<style> img { max-width: none; } </style> ![](media/function-split/none.png) |


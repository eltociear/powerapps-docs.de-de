---
title: Funktion „Find“ | Microsoft-Dokumentation
description: Referenzinformationen einschließlich Syntax und Beispielen für die Funktion „Find“ in PowerApps
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 8e95f03c934e0989269ff9ec21b432f609cb13ad
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "31826083"
---
# <a name="find-function-in-powerapps"></a>Funktion „Find“ in PowerApps
Sucht nach einer Textzeichenfolge in einer anderen Zeichenfolge (falls vorhanden)

## <a name="description"></a>Beschreibung
Die **Find**-Funktion sucht innerhalb einer anderen Zeichenfolge nach einer Zeichenfolge und beachtet dabei Groß-/Kleinschreibung. Wenden Sie zuerst die **[Lower](function-lower-upper-proper.md)**-Funktion auf die Argumente an, um die Groß-und Kleinschreibung außer Acht zu lassen.

**Find** gibt die Anfangsposition der Zeichenfolge zurück, die gefunden wurde.  Position 1 ist das erste Zeichen der Zeichenfolge. **Find** gibt *blank* zurück, wenn die Zeichenfolge, in der Sie suchen, nicht die Zeichenfolge enthält, nach der Sie suchen.

## <a name="syntax"></a>Syntax
**Find**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *ZuSuchendeZeichenfolge*: erforderlich.  Die zu suchende Zeichenfolge
* *InnerhalbDerZeichenfolge*: erforderlich.  Die Zeichenfolge, in der gesucht werden soll
* *Anfangsposition*: optional.  Die Anfangsposition der Suche.  Position 1 ist das erste Zeichen.


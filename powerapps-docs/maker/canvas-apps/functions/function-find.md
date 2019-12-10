---
title: Funktion „Find“ | Microsoft-Dokumentation
description: Referenzinformationen, einschließlich Syntax und Beispielen, für die Funktion "Find" in powerapps
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
ms.openlocfilehash: 62254bf46836ffc8ed5fa5b7685561b611db49a7
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730978"
ms.PowerAppsDecimalTransform: true
---
# <a name="find-function-in-power-apps"></a>Funktion "Find" in powerapps
Sucht nach einer Textzeichenfolge in einer anderen Zeichenfolge (falls vorhanden)

## <a name="description"></a>Beschreibung
Die **Find**-Funktion sucht innerhalb einer anderen Zeichenfolge nach einer Zeichenfolge und beachtet dabei Groß-/Kleinschreibung. Wenden Sie zuerst die **[Lower](function-lower-upper-proper.md)** -Funktion auf die Argumente an, um die Groß-und Kleinschreibung außer Acht zu lassen.

**Find** gibt die Anfangsposition der Zeichenfolge zurück, die gefunden wurde.  Position 1 ist das erste Zeichen der Zeichenfolge. **Find** gibt *blank* zurück, wenn die Zeichenfolge, in der Sie suchen, nicht die Zeichenfolge enthält, nach der Sie suchen.

## <a name="syntax"></a>Syntax
**Find**( *FindString*; *WithinString* [; *StartingPosition* ] )

* *ZuSuchendeZeichenfolge*: erforderlich.  Die zu suchende Zeichenfolge
* *InnerhalbDerZeichenfolge*: erforderlich.  Die Zeichenfolge, in der gesucht werden soll
* *Anfangsposition*: optional.  Die Anfangsposition der Suche.  Position 1 ist das erste Zeichen.


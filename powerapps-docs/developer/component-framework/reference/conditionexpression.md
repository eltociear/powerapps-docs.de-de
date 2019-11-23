---
title: ConditionExpression | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd90b3fd-a4b4-4999-8b53-d2a5dce4966b
ms.openlocfilehash: 10f7275643c0df4c2a4099a80b490fb5e27ce318
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345541"
---
# <a name="conditionexpression"></a>ConditionExpression

[!INCLUDE [conditionexpression-description](includes/conditionexpression-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="attributename"></a>AttributeName

Der Name der Daten Satz Spalte, auf die der Filter angewendet werden soll.

**Typ**: `string`

### <a name="conditionoperator"></a>conditionoperator

Der Operator, mit dem die Bedingung ausgewertet wird.

**Typ**: `enum`

Der `conditionOperator` Wert ist eine Enumeration mit den folgenden möglichen Werten.

|Value|Member|
|--|--|
|-1|Gar|
|0|Hoch|
|1|NotEqual|
|2|GreaterThan|
|3|LessThan|
|4|Des greaterequal|
|5|Lessequal|
|6|mögen|
|8|In|
|12|Normal|
|14|Yesterday|
|15|Today|
|Uhr|Morgigen|
|Uhr|Last7Days|
|Jahren|Next7Days|
|19.07.2016|Lastwoche|
|20|Bis|
|22.11.2016|Lastmonat|
|23|ThisMonth|
|25|Auf|
|26|Onorbefore|
|27,5|Onorafter|
|28|Lastjahr|
|27|ThisYear|
|33|Lastxdays|
|34|Nextxdays|
|37|Lastx Monate|
|38|Nextxmonate|
|49|Inhalt|
|70|Infiniscalperiodandyear|
|75|Durchschnittlich|
|76|Diskutiert|
|77|Notunder|
|78|Aboveorequal|
|79|Unterorgleich|
|87|Container Values|

### <a name="entityaliasname"></a>entityaliasname

Der Entitätstyp Name, sodass das Filtern für verknüpfte Entitäten verwendet werden kann.

**Typ**: `string`

### <a name="value"></a>value

Der Wert, der von der Bedingung ausgewertet wird.

**Typ**: `string | string[]`

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
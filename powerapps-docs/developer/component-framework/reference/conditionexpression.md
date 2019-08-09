---
title: ConditionExpression | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd90b3fd-a4b4-4999-8b53-d2a5dce4966b
---

# <a name="conditionexpression"></a>ConditionExpression

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [conditionexpression-description](includes/conditionexpression-description.md)]

## <a name="properties"></a>Eigenschaften

## <a name="attributename"></a>attributeName

Der Name der Datensatzspalte, auf die der Filter angewendet wird.

**Typ**: `string`

## <a name="conditionoperator"></a>conditionOperator

Der Operator, der zu Bewerten der Bedingung verwendet wird.

**Typ**: `enum`

Der `conditionOperator`-Wert ist eine Enumeration mit folgenden möglichen Werten:

|Value|Mitglied|
|--|--|
|-1|Keine|
|0|Gleich|
|1|NotEqual|
|2|GreaterThan|
|3|LessThan|
|4|GreaterEqual|
|5|LessEqual|
|6|Gefällt mir|
|8|Für|
|12|Null|
|14|Yesterday|
|15|Today|
|16|Morgen|
|17|Last7Days|
|18|Next7Days|
|19|LastWeek|
|20|ThisWeek|
|22|LastMonth|
|23|ThisMonth|
|25|On|
|26|OnOrBefore|
|27|OnOrAfter|
|28|LastYear|
|29|ThisYear|
|33|LastXDays|
|34|NextXDays|
|37|LastXMonths|
|38|NextXMonths|
|49|Enthält|
|70|InFiscalPeriodAndYear|
|75|Über|
|76|Unter|
|77|Nicht Unter|
|78|Über oder Gleich|
|79|Unter oder Gleich|
|87|ContainValues|

## <a name="entityaliasname"></a>entityAliasName

Entitätsaliasname, damit Filterung bei verknüpften Entitäten verwendet werden kann.

**Typ**: `string`

## <a name="value"></a>Wert

Der Wert, der von der Bedingung ausgewertet wird.

**Typ**: `string | string[]`


### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
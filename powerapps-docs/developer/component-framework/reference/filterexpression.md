---
title: FilterExpression | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19ad54b8-e044-4f07-a18e-b00d26b75832
---

# <a name="filterexpression"></a>FilterExpression

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [filterexpression-description](includes/filterexpression-description.md)]

## <a name="properties"></a>Eigenschaften

## <a name="conditions"></a>Bedingungen

Der Satz der Bedingungen im Zusammenhang mit diesem Filter.

**Typ**: [ConditionExpression](conditionexpression.md)[]

## <a name="filteroperator"></a>filterOperator

Der Operator, der zum kombinieren von Bedingungen in diesem Filter verwendet wird.

**Typ**: `enum`

Der `filterOperator`-Wert ist eine Enumeration mit folgenden möglichen Werten:

|Value|Mitglied|
|--|--|
|0|And|
|1|Or|

## <a name="filters"></a>Filter

Alle untergeordnete Filter, die ausgewertet werden sollen, nachdem dieser Filter ausgewertet ist.

**Typ**: [FilterExpression](filterexpression.md)[]<br />

### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
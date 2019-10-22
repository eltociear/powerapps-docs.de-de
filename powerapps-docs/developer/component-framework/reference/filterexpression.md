---
title: Filter Expression | Microsoft-Dokumentation
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
ms.assetid: 19ad54b8-e044-4f07-a18e-b00d26b75832
ms.openlocfilehash: 7b613238f28987b688d4f2299506fa91b72a99a7
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343977"
---
# <a name="filterexpression"></a>Filter Expression

[!INCLUDE [filterexpression-description](includes/filterexpression-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="conditions"></a>Voraus

Der Satz von Bedingungen, der diesem Filter zugeordnet ist.

**Type**: [conditionexpression](conditionexpression.md)[]

### <a name="filteroperator"></a>Filteroperator

Der Operator, der zum Kombinieren von Bedingungen in diesem Filter verwendet wird.

**Typ**: `enum`

Der `filterOperator` Wert ist eine Enumeration mit den folgenden möglichen Werten.

|Value|Member|
|--|--|
|0|And|
|1|Or|

### <a name="filters"></a>Filter

Alle untergeordneten Filter, die nach der Auswertung dieses Filters ausgewertet werden sollen.

**Type**: [Filter Expression](filterexpression.md)[]<br />

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
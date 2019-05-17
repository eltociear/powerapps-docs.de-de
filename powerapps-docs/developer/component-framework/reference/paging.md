---
title: Paging | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12891e96-972c-4289-bbde-2bc261cd1f12
---

# <a name="paging"></a>Paging

[!INCLUDE [paging-description](includes/paging-description.md)]

## <a name="totalresultcount"></a>totalResultCount

Gesamtanzahl der Ergebnisse auf dem Server für die aktuelle Abfrage.

**Typ**: `number`

## <a name="hasnextpage"></a>hasNextPage

Ob der Ergebnissatz rückwärts geblättert werden kann.

**Typ**: `boolean`

## <a name="haspreviouspage"></a>hasPreviousPage

Ob der Ergebnissatz rückwärts geblättert werden kann.

**Typ**: `boolean`

## <a name="methods"></a>Methoden

|Methode | Beschreibung |
| ------|-------------|
|[loadNextPage](paging/loadnextpage.md)|[!INCLUDE [loadnextpage-description](paging/includes/loadnextpage-description.md)]|
|[loadPreviousPage](paging/loadpreviouspage.md)|[!INCLUDE [loadpreviouspage-description](paging/includes/loadpreviouspage-description.md)]|
|[Zurücksetzen](paging/reset.md)|[!INCLUDE [reset-description](paging/includes/reset-description.md)]|
|[setPageSize](paging/setpagesize.md)|[!INCLUDE [setpagesize-description](paging/includes/setpagesize-description.md)]|


### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
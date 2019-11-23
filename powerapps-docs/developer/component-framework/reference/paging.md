---
title: Paging | Microsoft-Dokumentation
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
ms.assetid: 12891e96-972c-4289-bbde-2bc261cd1f12
ms.openlocfilehash: ccf68c94e0b11f8a1227199609a9c21c1923ad7b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342183"
---
# <a name="paging"></a>Paging

[!INCLUDE [paging-description](includes/paging-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="totalresultcount"></a>totalresultcount

Gesamtanzahl der Ergebnisse auf dem Server für die aktuelle Abfrage.

**Typ**: `number`

### <a name="hasnextpage"></a>hasnextpage

Gibt an, ob das Resultset rückwärts eingefügt werden kann.

**Typ**: `boolean`

### <a name="haspreviouspage"></a>haspreviouspage

Gibt an, ob das Resultset rückwärts eingefügt werden kann.

**Typ**: `boolean`

## <a name="methods"></a>Anzuwenden

|Anzuwenden | Beschreibung |
| ------|-------------|
|[loadnextpage](paging/loadnextpage.md)|[!INCLUDE [loadnextpage-description](paging/includes/loadnextpage-description.md)]|
|[loadpreviouspage](paging/loadpreviouspage.md)|[!INCLUDE [loadpreviouspage-description](paging/includes/loadpreviouspage-description.md)]|
|[Festlegen](paging/reset.md)|[!INCLUDE [reset-description](paging/includes/reset-description.md)]|
|[setPageSize](paging/setpagesize.md)|[!INCLUDE [setpagesize-description](paging/includes/setpagesize-description.md)]|
|PageSize|Die Anzahl der Datensätze, die pro datasetseite zurückgegeben werden sollen. In Formularen geht das DataSet page size (Anzahl der Zeilen) mit der Formatierung (Anzahl der Zeilen), und bei anderen können Sie Ihre persönlichen Optionen auswählen.|


### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
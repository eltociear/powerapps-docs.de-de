---
title: getGridType (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a441c08c-df32-433e-b666-4253f2cf878c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getgridtype-client-api-reference"></a>getGridType (Client-API-Referenz)



[!INCLUDE[./includes/getGridType-description.md](./includes/getGridType-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`var gridType = gridContext.getGridType();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Gibt einen der folgenden Werte zurück:

|Value |Beschreibung |
|--|--|
|1|HomePageGrid|
|2|Unterraster|

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext). 



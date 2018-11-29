---
title: getRows (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getrows-client-api-reference"></a>getRows (Client-API-Referenz)



[!INCLUDE[./includes/getRows-description.md](./includes/getRows-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`var allRows = gridContext.getGrid().getRows();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Sammlung

**Beschreibung**: Eine Sammlung von Zeilen im Raster.

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext).

Soehe [Sammlungen (Client-API-Referenz)](../../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.


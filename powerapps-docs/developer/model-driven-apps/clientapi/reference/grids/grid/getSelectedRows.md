---
title: getSelectedRows (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 49f39f0f-33ef-41d1-9ab3-14966ae075b5
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getselectedrows-client-api-reference"></a>getSelectedRows (Client-API-Referenz)



[!INCLUDE[./includes/getSelectedRows-description.md](./includes/getSelectedRows-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`var allSelectedRows = gridContext.getGrid().getSelectedRows();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Sammlung

**Beschreibung**: Eine Sammlung von ausgewählten Zeilen im Raster.

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext).

Soehe [Sammlungen (Client-API-Referenz)](../../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.


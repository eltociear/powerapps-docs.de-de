---
title: removeOnLoad (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
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
# <a name="removeonload-client-api-reference"></a>removeOnLoad (Client-API-Referenz)



[!INCLUDE[./includes/removeOnLoad-description.md](./includes/removeOnLoad-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`gridContext.removeOnLoad(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die aus dem **OnLoad**-Ereignis entfernt werden soll.

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext).

### <a name="related-topics"></a>Verwandte Themen

[addOnLoad](addOnLoad.md) 



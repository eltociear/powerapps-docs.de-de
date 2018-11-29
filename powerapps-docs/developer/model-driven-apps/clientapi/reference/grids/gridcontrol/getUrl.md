---
title: getUrl (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f2023d7d-5877-4436-abe6-e81ca68b8ec0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="geturl-client-api-reference"></a>getUrl (Client-API-Referenz)



[!INCLUDE[./includes/getUrl-description.md](./includes/getUrl-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`gridContext.getUrl(client);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|client|Zahl|No|Gibt den Clienttyp an. Geben Sie einen der folgenden Werte an:<br/>0: Browser<br/>1: MobileApplication|

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Die URL des aktuellen Unterrastersteuerelements.

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext).




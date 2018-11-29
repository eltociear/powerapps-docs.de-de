---
title: isvisible (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d22cd046-064c-47ef-9e46-5cc4c8b6e280
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isvisible-client-api-reference"></a>isVisible (Client-API-Referenz)



[!INCLUDE[./includes/isVisible-description.md](./includes/isVisible-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Schreibgeschütztes Raster

## <a name="syntax"></a>Syntax

`viewSelector.isVisible();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Beschreibung**: true, wenn sichtbar; sonst false.

## <a name="remarks"></a>Anmerkungen

Wenn das Unterrastersteuerelement nicht so konfiguriert ist, dass die Ansichtsauswahl angezeigt wird, wird durch Aufrufen dieser Methode für **ViewSelector**, die von der Methode GridControl.getViewSelector zurückgegeben wird, ein Fehler ausgelöst.

Informationen zum Abrufen des `viewSelector`-Objekt finden Sie unter [ViewSelector](../viewselector.md).




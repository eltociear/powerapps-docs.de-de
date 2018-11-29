---
title: getEntityReference (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: b8e23eee-f20f-4db9-9cc6-7fa5dd7ce2bb
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentityreference-client-api-reference"></a>getEntityReference (Client-API-Referenz)



[!INCLUDE[./includes/getEntityReference-description.md](./includes/getEntityReference-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`gridEntity.getEntityReference();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Suche

**Beschreibung**: Der Suchobjekt, das auf den Datensatz in der Zeile verweist. Das Objekt hat die folgenden Attribute:
- **entityType**: Zeichenfolge. Der logische Name für den Datensatz in der Zeile. Dieselben Daten, die von der **GridEntity**.[getEntityName](getEntityName.md)-Methode zurückgegeben werden.
- **id**: Zeichenfolge. Die Id für den Datensatz in der Zeile. Dieselben Daten, die von der **GridEntity**.[getId](getId.md)-Methode zurückgegeben werden.
- **name**: Zeichenfolge. Der primäre Attributwert für den Datensatz in der Zeile. Dieselben Daten, die von der **GridEntity**.[getPrimaryAttributeValue](getPrimaryAttributeValue.md)-Methode zurückgegeben werden.

## <a name="remarks"></a>Anmerkungen

Informationen zum Abrufen des `gridEntity`-Objekts finden Sie unter [GridEntity](../gridentity.md). 


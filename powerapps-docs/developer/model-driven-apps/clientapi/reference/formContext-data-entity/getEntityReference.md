---
title: getEntityReference (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1a66f93d-a47c-4316-91f1-dcf5d09f9d19
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

## <a name="syntax"></a>Syntax

`formContext.data.entity.getEntityReference();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Suchobjekt.

**Beschreibung**: Das zurückgesendete Objekt hat folgende drei Attribute:

- **entityType**: Zeichenfolge. Logischer Name des Entitätsdatensatzes. Zum Beispiel: "Firma".
- **id**: Zeichenfolge. GUID-Wert des Entitätsdatensatzes.
- **name**: (Optional) Zeichenfolge. Name des Entitätsdatensatzes. 




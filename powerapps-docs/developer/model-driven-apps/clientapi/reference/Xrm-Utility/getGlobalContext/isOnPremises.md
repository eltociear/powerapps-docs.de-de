---
title: isOnPremise (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 855767c5-c48f-47a2-8f99-52423221d974
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isonpremise-client-api-reference"></a>isOnPremise (Client-API-Referenz)



Gibt ein angebenden booleschen Wert zurück, wenn die modellgesteuerte Instanz lokal oder online gehostet wird. 

## <a name="syntax"></a>Syntax

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.isOnPremises();
```

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Beschreibung**: **true**, wenn die modellgestütze App-Instanz lokal ist; andernfalls **false**.

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)




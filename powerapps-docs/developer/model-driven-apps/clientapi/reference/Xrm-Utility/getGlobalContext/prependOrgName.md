---
title: prependOrgName (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="prependorgname-client-api-reference"></a>prependOrgName (Client-API-Referenz)



Setzt den aktuellen eindeutigen Namen der Organisation vor eine Zeichenfolge, normalerweise ein URL-Pfad.

## <a name="syntax"></a>Syntax

 ```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.prependOrgName(sPath);
```

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|sPath |String |Ja |Ein lokaler Pfad zu einer Ressource. |

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Eine Pfadzeichenfolge mit dem Namen der Organisation im folgenden Format:

`"/"+ orgName + sPath`

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)



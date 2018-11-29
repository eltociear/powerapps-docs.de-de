---
title: getVersion (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2fd5c43e-5a01-431d-ac2c-abefdb8d06ac
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getversion-client-api-reference"></a>getVersion (Client-API-Referenz)



Gibt die Versionennummer der modellgestützten App-Instanz zurück.

## <a name="syntax"></a>Syntax

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getVersion();
``` 
## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Version der modellgestützten App-Instanz. Beispiel:

`"9.0.0.1103"`

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)

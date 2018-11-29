---
title: getAdvancedConfigSetting (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="getadvancedconfigsetting-client-api-reference"></a>GetAdvancedConfigSetting (Client-API-Referenz)



Gibt Informationen zu erweiterten Konfigurationseinstellungen für die Organisation zurück. 

## <a name="syntax"></a>Syntax

```JavaScript
var globalContext = Xrm.Utility.getGlobalContext();
globalContext.getAdvancedConfigSetting(setting);
```

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|Einstellung |String |Ja |Name der Konfigurationseinstellung. <br/>Nur die folgenden beiden Konfigurationen werden unterstützt: **"MaxChildIncidentNumber"** und **"MaxIncidentMergeNumber"** |

## <a name="return-value"></a>Rückgabewert

Gibt den erweiterten Konfigurationseinstellungswert zurück.

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility.getGlobalContext](../getGlobalContext.md)




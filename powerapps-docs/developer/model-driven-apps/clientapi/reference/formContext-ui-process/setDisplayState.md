---
title: setDisplayState (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 21368fac-d4bc-4f75-8a9c-cce098fa0b45
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setdisplaystate-client-api-reference"></a>setDisplayState (Client-API-Referenz)



[!INCLUDE[./includes/setDisplayState-description.md](./includes/setDisplayState-description.md)]

## <a name="syntax"></a>Syntax

`formContext.ui.process.setDisplayState(state);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|state|String|Ja|Geben Sie "erweitert" ,"verkleinert", oder "unverankert" an. Der "unverankerte" Status kann im Webclient nicht angewendet werden.|

### <a name="related-topics"></a>Verwandte Themen

[getDisplayState](getDisplayState.md)

[formContext.ui.process](../formContext-ui-process.md)




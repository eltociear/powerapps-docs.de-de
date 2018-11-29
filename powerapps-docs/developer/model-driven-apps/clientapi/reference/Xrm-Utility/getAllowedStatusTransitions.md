---
title: getAllowedStatusTransitions (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 28c36741-0070-435c-a42f-49f4dda2ef7f
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="getallowedstatustransitions-client-api-reference"></a>getAllowedStatusTransitions (Client-API-Referenz)



[!INCLUDE[./includes/getAllowedStatusTransitions-description.md](./includes/getAllowedStatusTransitions-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Utility.getAllowedStatusTransitions(entityName,stateCode).then(successCallback, errorCallback)`

## <a name="parameters"></a>Parameter

|Name |Typ |Erforderlich |Beschreibung |
|---|---|---|---|
|entityName|String|Ja|Der logische Name der Entität.|
|stateCode|Zahl|Ja|Der Statuscode, um die zulässigen Statusübergangswerte herauszufinden.|
|successCallback|Funktion|No|Die auszuführende Funktion, wenn der Vorgang erfolgreich war.|
|errorCallback|Funktion|No|Die auszuführende Funktion, wenn der Vorgang fehlgeschlagen ist.|


### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility](../xrm-utility.md)




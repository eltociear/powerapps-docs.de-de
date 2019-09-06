---
title: removeOnPreProcessStatusChange (Client-API-Referenz) in Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 06/30/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: MSFTMan
ms.author: Deonhe
manager: KVivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="removeonpreprocessstatuschange-client-api-reference"></a>removeOnPreProcessStatusChange (Client-API-Referenz)

[!INCLUDE[](../../../../../../includes/cc_applies_to_update_9_0_0.md)]

[!INCLUDE[./includes/removeOnPreProcessStatusChange-description.md](./includes/removeOnPreProcessStatusChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.removeOnPreProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die aus dem [OnPreProcessStatusChange](../../events/onpreprocessstatuschange.md)-Ereignis entfernt werden soll.|

### <a name="related-topics"></a>Verwandte Themen

[addOnProcessStatusChange](addOnProcessStatusChange.md)
 
[formContext.data.process](../../formContext-data-process.md)
 



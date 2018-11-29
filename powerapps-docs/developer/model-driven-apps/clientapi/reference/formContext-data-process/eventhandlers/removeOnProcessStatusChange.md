---
title: removeOnProcessStatusChange (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5e41f59e-ddb3-4d47-b45b-454aa9e04439
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonprocessstatuschange-client-api-reference"></a>removeOnProcessStatusChange (Client-API-Referenz)



[!INCLUDE[./includes/removeOnProcessStatusChange-description.md](./includes/removeOnProcessStatusChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.removeOnProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die aus dem [OnProcessStatusChange](../../events/onprocessstatuschange.md)-Ereignis entfernt werden soll.|

### <a name="related-topics"></a>Verwandte Themen

[addOnProcessStatusChange](addOnProcessStatusChange.md)
 
[formContext.data.process](../../formContext-data-process.md)
 



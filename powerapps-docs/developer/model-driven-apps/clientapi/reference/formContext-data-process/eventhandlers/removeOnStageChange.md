---
title: removeOnStageChange (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonstagechange-client-api-reference"></a>removeOnStageChange (Client-API-Referenz)

[!INCLUDE[./includes/removeOnStageChange-description.md](./includes/removeOnStageChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.removeOnStageChange(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die aus dem [OnStageChange](../../events/onstagechange.md)-Ereignis entfernt werden soll.|

### <a name="related-topics"></a>Verwandte Themen

[addOnStageChange](addOnStageChange.md)
 
[formContext.data.process](../../formContext-data-process.md)
 



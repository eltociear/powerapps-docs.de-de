---
title: removeOnPreStageChange (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 08/05/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
author: MsftMan
ms.author: DeonHe
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonprestagechange-client-api-reference"></a>removeOnPreStageChange (Client-API-Referenz)

[!INCLUDE[./includes/removeOnPreStageChange-description.md](./includes/removeOnPreStageChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.removeOnPreStageChange(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die aus dem [OnPreStageChange](../../events/onprestagechange.md)-Ereignis entfernt werden soll.|

### <a name="related-topics"></a>Verwandte Themen

[addOnPreStageChange](addOnPreStageChange.md)
 
[formContext.data.process](../../formContext-data-process.md)
 



---
title: removeOnResultOpened (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonresultopened-client-api-reference"></a>removeOnResultOpened (Client-API-Referenz)



Entfernt einen Ereignishandler aus dem [OnResultOpened](../events/onresultopened.md)-Ereignis. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.removeOnResultOpened(myFunction);
```

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja|Die Funktion, die aus dem **OnResultOpened**-Ereignis entfernt werden soll.|

### <a name="related-topics"></a>Verwandte Themen

[OnResultOpened-Ereignis](../events/onresultopened.md)

[addOnResultOpened](addOnResultOpened.md) 



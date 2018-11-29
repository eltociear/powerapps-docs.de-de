---
title: addOnPostSearch (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c398dbca-0ead-487a-8a92-35b1f2953bf6
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonpostsearch-client-api-reference"></a>removeOnPostSearch (Client-API-Referenz)



Entfernt einen Ereignishandler aus dem [PostSearch](../events/postsearch.md)-Ereignis. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>";
kbSearchControl.removeOnPostSearch(myFunction);
```

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja|Die Funktion, die aus dem **PostSearch**-Ereignis entfernt werden soll.| 

### <a name="related-topics"></a>Verwandte Themen

[PostSearch-Ereignis](../events/postsearch.md)

[addOnPostSearch](addOnPostSearch.md) 



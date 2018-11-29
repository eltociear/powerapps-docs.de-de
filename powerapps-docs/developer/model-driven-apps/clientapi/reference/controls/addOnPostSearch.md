---
title: addOnPostSearch (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9d000628-5dbe-45bd-9c47-e19187ffdae7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonpostsearch-client-api-reference"></a>addOnPostSearch (Client-API-Referenz)



Fügt einen Ereignishandler für das [PostSearch](../events/postsearch.md)-Ereignis hinzu. 

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>";
kbSearchControl.addOnPostSearch(myFunction);
```

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja|Die Funktion, die für das **PostSearch**-Ereignis hinzugefügt werden soll. Der [Ausführungskontext](../../clientapi-execution-context.md) wird automatisch bei der ersten der zu den Funktionen übergeben, die mithilfe des Codes festgelegt wird.| 

### <a name="related-topics"></a>Verwandte Themen

[PostSearch-Ereignis](../events/postsearch.md)

[removeOnPostSearch](removeOnPostSearch.md)
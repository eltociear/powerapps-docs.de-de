---
title: addOnResultOpened (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5f0eabe1-985a-4e89-b23a-72657208ae7e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonresultopened-client-api-reference"></a>addOnResultOpened (Client-API-Referenz)



Fügt einen Ereignishandler für das [OnResultOpened](../events/onresultopened.md)-Ereignis hinzu. 

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.addOnResultOpened(myFunction);
```

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja|Die Funktion, die für das **OnResultOpened**-Ereignis hinzugefügt werden soll. Der [Ausführungskontext](../../clientapi-execution-context.md) wird automatisch bei der ersten der zu den Funktionen übergeben, die mithilfe des Codes festgelegt wird.|

### <a name="related-topics"></a>Verwandte Themen

[OnResultOpened-Ereignis](../events/onresultopened.md)

[removeOnResultOpened](removeOnResultOpened.md)

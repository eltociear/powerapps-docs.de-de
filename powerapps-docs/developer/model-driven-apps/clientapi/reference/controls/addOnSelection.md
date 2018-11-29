---
title: addOnSelection (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 66cfb2ff-4d78-4bb9-8dc0-e214ae1d2880
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonselection-client-api-reference"></a>addOnSelection (Client-API-Referenz)



Fügt einen Ereignishandler für das [OnSelection](../events/onselection.md)-Ereignis hinzu. 

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.addOnSelection(myFunction);
```

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja|Die Funktion, die für das **OnSelection**-Ereignis hinzugefügt werden soll. Der [Ausführungskontext](../../clientapi-execution-context.md) wird automatisch bei der ersten der zu den Funktionen übergeben, die mithilfe des Codes festgelegt wird.|

### <a name="related-topics"></a>Verwandte Themen

[OnSelection-Ereignis](../events/onselection.md)

[removeOnSelection](removeOnSelection.md)
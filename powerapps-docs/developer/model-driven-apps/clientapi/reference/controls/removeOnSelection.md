---
title: removeOnSelection (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 3ca41e3e-af2b-4aa8-8233-64a8c276d0ef
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeonselection-client-api-reference"></a>removeOnSelection (Client-API-Referenz)



Entfernt einen Ereignishandler aus dem [OnSelection](../events/onselection.md)-Ereignis. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.removeOnSelection(myFunction);
```

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja|Die Funktion, die aus dem **OnSelection**-Ereignis entfernt werden soll.| 

### <a name="related-topics"></a>Verwandte Themen

[addOnSelection](addOnSelection.md)



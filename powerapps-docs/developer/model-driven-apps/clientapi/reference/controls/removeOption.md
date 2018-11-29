---
title: removeOption (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 09fd288c-d687-4976-b708-29a466fc35b1
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removeoption-client-api-reference"></a>removeOption (Client-API-Referenz)



Entfernt eine Option aus einem Steuerelement. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

optionset, multiselectoptionset

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).removeOption(value);`

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|Wert |Zahl |Ja|Der Wert der Option, die Sie entfernen möchten.|

### <a name="related-topics"></a>Verwandte Themen

[addOption](addOption.md)

[clearOptions](clearOptions.md)

 



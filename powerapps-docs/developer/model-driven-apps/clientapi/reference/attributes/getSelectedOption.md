---
title: Xrm.Device| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: ce572df6-aae6-431a-aa95-73eee544c7e9
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getselectedoption-client-api-reference"></a>getSelectedOption (Client-API-Referenz)



Gibt das Optionsobjekt oder einem Optionsobjekte-Array zurück, die in einem **optionset**- bzw. **multiselectoptionset**-Attribut ausgewählt werden. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

optionset, multiselectoptionset

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getSelectedOption()`

## <a name="return-value"></a>Rückgabewert

**Typ**: Optionsobjekt für optionset; Array von Optionsobjekten für multiselectoptionset. 

**Beschreibung**: Gibt das Objekt mit Text- und Werteigenschaften zurück.

### <a name="related-topics"></a>Verwandte Themen
[getInitialValue (Client-API-Referenz)](getInitialValue.md)

[getOption (Client-API-Referenz)](getOption.md)

[getOptions (Client-API-Referenz)](getOptions.md)

[getText (Client-API-Referenz)](getText.md)


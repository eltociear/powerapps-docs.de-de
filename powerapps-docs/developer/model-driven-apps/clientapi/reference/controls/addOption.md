---
title: addOption (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9798f168-7b94-411d-9aed-6471042ff11a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addoption-client-api-reference"></a>addOption (Client-API-Referenz)



Fügt einem Steuerelement eine Option hinzu. 

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

OptionSet, MultiSelectOptionSet

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).addOption(option, index);`

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|option |Objekt |Ja|Die hinzuzufügende Option. Das Objekt hat die folgenden Attribute:<br/>**- text**: Zeichenfolge. Die Beschriftung für die Option.<br/>**- value**: Zahl. Der Wert für die Option.|
|index |Zahl |No|Die Indexposition zum Platzieren der neuen Option in. Falls nicht verfügbar, wird die Option dem Ende hinzugefügt.|

### <a name="related-topics"></a>Verwandte Themen

[clearOptions](clearOptions.md)

[removeOption](removeOption.md)
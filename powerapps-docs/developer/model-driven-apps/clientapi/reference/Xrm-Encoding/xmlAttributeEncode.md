---
title: xmlAttributeEncode| MicrosoftDocs
description: 'Die Client API-Methode decodiert die angegebene Zeichenfolge, damit sie in einem XML-Attribut verwendet werden kann.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 909443cd-12b5-4a73-9904-8ae623d22c81
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xmlattributeencode-client-api-reference"></a>xmlAttributeEncode (Client-API-Referenz)



[!INCLUDE[./includes/xmlAttributeEncode-description.md](./includes/xmlAttributeEncode-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Encoding.xmlAttributeEncode(arg)`

## <a name="parameters"></a>Parameter

|Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|arg        | String           | Erforderlich  |Zu verschlüsselnde Zeichenfolge.  |


## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Verschlüsselte Zeichenfolge.

## <a name="related-topics"></a>Verwandte Themen
[xmlEncode](xmlEncode.md)
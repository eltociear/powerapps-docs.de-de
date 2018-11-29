---
title: htmlDecode| MicrosoftDocs
description: 'Die Client API-Methode konvertiert Zeichenfolgen, die in eine decodierte Zeichenfolge HTML-codiert dazu geführt haben.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4ef7160b-ac01-4d08-8a98-f8e3012ef20b
author: KumarVivek
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="htmldecode-client-api-reference"></a>htmlDecode (Client API Referenz)



[!INCLUDE[./includes/htmlDecode-description.md](./includes/htmlDecode-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Encoding.htmlDecode(arg)`

## <a name="parameters"></a>Parameter

|Parametername        | Typ           | Erforderlich  |Beschreibung  |
| ------------- |-------------| -----|-----|
|arg        | String           | Erforderlich  |HTML kodierte Zeichenfolge zu dekodieren..  |


## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Dekodierte Zeichenfolge.

## <a name="related-topics"></a>Verwandte Themen

[xmlEncode](htmlEncode.md)

[xmlAttributeEncode](htmlAttributeEncode.md)

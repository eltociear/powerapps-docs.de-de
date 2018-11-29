---
title: get method für Sammlungen (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="get-method-for-collections-client-api-reference"></a>get-Methode für Sammlungen (Client-API-Referenz)



[!INCLUDE[./includes/get-description.md](./includes/get-description.md)]

## <a name="syntax"></a>Syntax

`collection.get([String][Number][delegate function(attribute, index)])`

## <a name="parameters"></a>Parameter

|Parameter  |Rückgabewert |Rückgabetyp  |
|---------|------|-------|
|Keiner  |Alle Objekte in der Sammlung  |Array|
|String  |Das Objekt, wobei der Name dem Argument entspricht<br/><br/>Die Objekte, die im **formContext.data.process**-Namespace zurückgegeben werden, enthalten keine Namen. Daher wird bei Verwendung des Zeichenfolgenparameters für diese Methode kein Objekt zurückgegeben.  |Objekt|
|Zahl  |Das Objekt, bei dem der Index der Zahl entspricht.  |Objekt|
|Delegatfunktion (Attribut, index)  |Alle Objekte, die die Stellvertretungsfunktion veranlassen, **true** zurückzugeben.  |Array|


### <a name="related-topics"></a>Verwandte Themen
[Sammlungen in Client API](../collections.md)

[forEach](forEach.md)

[getLength](getLength.md)


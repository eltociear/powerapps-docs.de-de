---
title: addOnLoad (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 03e970ee-7ed3-4df2-9670-222d76a479fd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonload-client-api-reference"></a>addOnLoad (Client-API-Referenz)



[!INCLUDE[./includes/addOnLoad-description.md](./includes/addOnLoad-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.addOnLoad(myFunction)`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die ausgeführt werden soll, wenn die Formulardaten geladen werden.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../clientapi-execution-context.md).
### <a name="related-topics"></a>Verwandte Themen

[removeOnLoad](removeOnLoad.md)

[Formulardaten OnLoad-Ereignis](../events/form-data-onload.md)


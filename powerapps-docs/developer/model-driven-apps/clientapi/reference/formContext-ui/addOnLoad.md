---
title: addOnLoad (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 31a146de-9e25-43be-ae3e-83a2a5c86543
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

`formContext.ui.addOnLoad(myFunction)`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die für das Formular [OnLoad](../events/form-onload.md)-Ereignis ausgeführt werden soll.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../clientapi-execution-context.md).|

### <a name="related-topics"></a>Verwandte Themen

[removeOnLoad](removeOnLoad.md)

[Formular OnLoad-Ereignis](../events/form-onload.md)

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)


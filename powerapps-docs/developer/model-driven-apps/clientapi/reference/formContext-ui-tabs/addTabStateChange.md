---
title: addTabStateChange (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 51b0dbf3-28bd-4eea-9ee9-50b322e9af9b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addtabstatechange-client-api-reference"></a>addTabStateChange (Client-API-Referenz)



[!INCLUDE[./includes/addTabStateChange-description.md](./includes/addTabStateChange-description.md)].

## <a name="syntax"></a>Syntax

`tabObj.addTabStateChange(myFunction);` 

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die für das [TabStateChange](../events/tabstatechange.md)-Ereignis ausgeführt werden soll.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../clientapi-execution-context.md).|

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)



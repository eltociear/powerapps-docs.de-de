---
title: addOnPreStageChange (Client-API-Referenz) in Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 07/19/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: msftman
ms.author: deonhe
manager: KVivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="addonprestagechange-client-api-reference"></a>addOnPreStageChange (Client-API-Referenz)

[!INCLUDE[./includes/addOnStageChange-description.md](./includes/AddOnPreStageChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.addOnPreStageChange(myFunction);`

## <a name="parameter"></a>Parameter

Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die ausgeführt wird, **bevor** sich die Phase des Geschäftsprozessflusses ändert. Die Funktion wird dem Start der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../../clientapi-execution-context.md).<br/><br/>Sie sollten einen Verweis auf eine benante Funktion anstelle einer anonymen Funktion verwenden, wenn Sie später den Ereignishandler entfernen möchten.|

Diese Client-API wird nur im einheitliche Client unterstützt. Der Vorgängerwebclient unterstützt diese Client-API nicht.

### <a name="related-topics"></a>Verwandte Themen

- [addOnStageChange](addOnStageChange.md)
 
- [removeOnStageChange](removeOnStageChange.md)

- [formContext.data.process](../../formContext-data-process.md)
 



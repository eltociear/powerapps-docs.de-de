---
title: addOnStageSelected (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5982770c-d5a4-415a-a32d-3734b6210bb9
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonstageselected-client-api-reference"></a>addOnStageSelected (Client-API-Referenz)



[!INCLUDE[./includes/addOnStageSelected-description.md](./includes/addOnStageSelected-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.addOnStageSelected(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die ausgeführt werden muss, wenn sich die Phase des Geschäftsprozessflusses ändert.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../../clientapi-execution-context.md).<br/><br/>Sie sollten einen Verweis auf eine benante Funktion anstelle einer anonymen Funktion verwenden, wenn Sie später den Ereignishandler entfernen möchten.|

### <a name="related-topics"></a>Verwandte Themen

[removeOnStageSelected](removeOnStageSelected.md)
 
[formContext.data.process](../../formContext-data-process.md)
 



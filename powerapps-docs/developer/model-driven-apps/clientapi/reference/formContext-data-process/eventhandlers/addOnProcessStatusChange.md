---
title: addOnProcessStatusChange (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2bf30298-f52b-4ab7-8833-4838f0d87e12
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonprocessstatuschange-client-api-reference"></a>addOnProcessStatusChange (Client-API-Referenz)



[!INCLUDE[./includes/addOnProcessStatusChange-description.md](./includes/addOnProcessStatusChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.addOnProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die ausgeführt werden muss, wenn sich der Status des Geschäftsprozessflusses ändert.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../../clientapi-execution-context.md).<br/><br/>Sie sollten einen Verweis auf eine benante Funktion anstelle einer anonymen Funktion verwenden, wenn Sie später den Ereignishandler entfernen möchten.|

### <a name="related-topics"></a>Verwandte Themen

[removeOnProcessStatusChange](removeOnProcessStatusChange.md)
 
[formContext.data.process](../../formContext-data-process.md)


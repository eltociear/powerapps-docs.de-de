---
title: addOnStageChange (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d18136d2-a3cf-4440-8e6b-1703594acd79
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonstagechange-client-api-reference"></a>addOnStageChange (Client-API-Referenz)



[!INCLUDE[./includes/addOnStageChange-description.md](./includes/addOnStageChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.addOnStageChange(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die ausgeführt werden muss, wenn sich die Phase des Geschäftsprozessflusses ändert.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../../clientapi-execution-context.md).<br/><br/>Sie sollten einen Verweis auf eine benante Funktion anstelle einer anonymen Funktion verwenden, wenn Sie später den Ereignishandler entfernen möchten.|

### <a name="related-topics"></a>Verwandte Themen
 
[removeOnStageChange](removeOnStageChange.md)

[formContext.data.process](../../formContext-data-process.md)
 



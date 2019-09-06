---
title: addOnPreProcessStatusChange (Client-API-Referenz) in Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 08/05/2017
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="addonpreprocessstatuschange-client-api-reference"></a>addOnPreProcessStatusChange (Client-API-Referenz)

[!INCLUDE[](../../../../../../includes/cc_applies_to_update_9_0_0.md)]

[!INCLUDE[./includes/addOnPreProcessStatusChange-description.md](./includes/addOnPreProcessStatusChange-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.addOnPreProcessStatusChange(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die ausgeführt werden muss, wenn sich der Status des Geschäftsprozessflusses ändert. Die Funktion wird dem Start der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../../clientapi-execution-context.md).<br/><br/>Sie sollten einen Verweis auf eine benante Funktion anstelle einer anonymen Funktion verwenden, wenn Sie später den Ereignishandler entfernen möchten.|

Diese Client-API wird nur im einheitliche Client unterstützt. Der Vorgängerwebclient unterstützt diese Client-API nicht.

### <a name="related-topics"></a>Verwandte Themen

[removeOnPreProcessStatusChange](removeOnPreProcessStatusChange.md)

[formContext.data.process](../../formContext-data-process.md)

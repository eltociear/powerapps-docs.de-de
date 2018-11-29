---
title: getProcessInstance (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4ed6c991-59c9-4a69-90d4-635f3f1d397b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getprocessinstances-client-api-reference"></a>getProcessInstances (Client-API-Referenz)



[!INCLUDE[./includes/getProcessInstances-description.md](./includes/getProcessInstances-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.getProcessInstances(callbackFunction(object));`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|callbackFunction|Funktion|Ja|Die Rückruffunktion übergibt ein Objekt mit den folgenden Attributen und den entsprechenden Werten als Schlüssel-Wert-Paare. Alle zurückgegebenen Werte sind vom Zeichenfolgentyp, außer **CreatedOnDate**, das vom Typ [Datum](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date) ist. <br/>- CreatedOn (veraltet)<br/>- CreatedOnDate<br/>- ProcessDefinitionID<br/>- ProcessDefinitionName<br/>- ProcessInstanceID<br/>- ProcessInstanceName<br/>- StatusCodeName<br/><br/>Die Prozessinstanzen werden in Übereinstimmung mit den Rechten des Benutzers gefiltert.|

### <a name="related-topics"></a>Verwandte Themen

[setActiveProcessInstance](setActiveProcessInstance.md)

[formContext.data.process](../formContext-data-process.md)
 



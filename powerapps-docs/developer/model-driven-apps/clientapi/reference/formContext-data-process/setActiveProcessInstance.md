---
title: setActiveProcessInstance (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c01a9445-00b6-4152-a482-df830f91a3ea
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setactiveprocessinstance-client-api-reference"></a>setActiveProcessInstance (Client-API-Referenz)



[!INCLUDE[./includes/setActiveProcessInstance-description.md](./includes/setActiveProcessInstance-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.setActiveProcessInstance(processInstanceId, callbackFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|processInstanceId|String|Ja|Die ID der Prozessinstanz wird als aktive Instanz festgelegt.|
|callbackFunction|Funktion|No|Eine Funktion, die aufgerufen wird, wenn der Vorgang abgeschlossen ist. Dieser Rückruffunktion wird einer der folgenden Zeichenfolgenwerte übergeben, um anzuzeigen, ob der Vorgang erfolgreich war:<br/>- **Erfolg**: Der Vorgang war erfolgreich.<br/>- **ungültig**: Die processInstanceId ist ungültig oder der Prozess ist nicht aktiviert.|

### <a name="related-topics"></a>Verwandte Themen

[getProcessInstances](getProcessInstances.md)

[formContext.data.process](../formContext-data-process.md)
 



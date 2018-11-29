---
title: setActiveProcess (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0d4c2d8a-a2fb-4cdd-9153-041646068992
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setactiveprocess-client-api-reference"></a>setActiveProcess (Client-API-Referenz)



[!INCLUDE[./includes/setActiveProcess-description.md](./includes/setActiveProcess-description.md)]

Wenn es eine aktive Instanz des Prozesses gibt, wird der Entitätsdatensatz mit der Prozessinstanz-ID geladen. Falls es keine aktive Instanz des aktuellen Prozesses gibt, wird eine neue Prozessinstanz erstellt und den Entitätsdatensatz wird mit der Prozessinstanz-ID geladen Falls es mehrere Instanzen des aktuellen Prozesses gibt, wird der Datensatz mit der ersten Instanz des aktiven Prozesses gemäß der Standardlogik geladen (die zuletzt verwendete Prozessinstanz pro Benutzer).

## <a name="syntax"></a>Syntax

`formContext.data.process.setActiveProcess(processId, callbackFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|processInstanceId|String|Ja|Die ID der Prozessinstanz wird als aktiver Prozess festgelegt.|
|callbackFunction|Funktion|No|Eine Funktion, die aufgerufen wird, wenn der Vorgang abgeschlossen ist. Dieser Rückruffunktion wird einer der folgenden Zeichenfolgenwerte übergeben, um anzuzeigen, ob der Vorgang erfolgreich war:<br/>- **Erfolg**: Der Vorgang war erfolgreich.<br/>- **ungültig**: Die processId ist ungültig oder der Prozess ist nicht aktiviert.|

### <a name="related-topics"></a>Verwandte Themen

[getActiveProcess](getActiveProcess.md)

[setActiveProcessInstance](../setActiveProcessInstance.md)

[formContext.data.process](../../formContext-data-process.md)
 



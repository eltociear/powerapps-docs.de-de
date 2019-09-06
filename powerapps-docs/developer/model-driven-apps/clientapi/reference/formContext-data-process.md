---
title: form Context.data.process (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: Erfahren Sie mehr über das Verwenden modellgestützten Apps mithilfe von Client-API.
ms.date: 06/30/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 32e8d1d0-4093-4588-a517-2930eec34dce
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="formcontextdataprocess-client-api-reference"></a>formContext.data.process (Client-API-Referenz)



Stellt Ereignisse, Objekte und Methoden zum Interagieren mit den Geschäftsprozessfluss-Daten in einem Formular bereit. Informationen zu Methoden, um mit der Geschäftsprozessflusssteuerung des Formulars zu interagieren finden Sie unter [formContext.ui.process (Client-API-Referenz)](formContext-ui-process.md) .

## <a name="process-events-and-event-handler-methods"></a>Prozessereignisse und Ereignishandlermethoden

Verwenden Sie die folgenden Ereignisse und Ereignishandlermethoden, um Skripts für Geschäftsprozessflüsse zu schreiben.

|Ereignis | Ereignishandlermethoden|
|--|--|
|[OnPreProcessStatusChange](events/onpreprocessstatuschange.md)|[addOnPreProcessStatusChange](formContext-data-process/eventhandlers/addOnPreProcessStatusChange.md)<br/>[removeOnPreProcessStatusChange](formContext-data-process/eventhandlers/removeOnPreProcessStatusChange.md)|
|[OnProcessStatusChange](events/onprocessstatuschange.md)|[addOnProcessStatusChange](formContext-data-process/eventhandlers/addOnProcessStatusChange.md)<br/>[removeOnProcessStatusChange](formContext-data-process/eventhandlers/removeOnProcessStatusChange.md)|
|[OnStageChange](events/OnStageChange.md)|[addOnStageChange](formContext-data-process/eventhandlers/addOnStageChange.md)<br/>[removeOnStageChange](formContext-data-process/eventhandlers/removeOnStageChange.md)|
|[OnStageSelected](events/OnStageSelected.md)|[addOnStageSelected](formContext-data-process/eventhandlers/addOnStageSelected.md)<br/>[removeOnStageSelected](formContext-data-process/eventhandlers/removeOnStageSelected.md)|

## <a name="active-process-methods"></a>ActiveProcess-Methoden

Verwenden Sie diese Methoden, um Informationen zu dem aktiven Prozess abzurufen, und , um einen anderen Prozess als aktiven Prozess festzulegen.

|Name | Beschreibung |
|--|--|
|[getActiveProcess](formcontext-data-process/activeprocess/getActiveProcess.md)|[!INCLUDE[formcontext-data-process/activeprocess/includes/getActiveProcess-description.md](formcontext-data-process/activeprocess/includes/getActiveProcess-description.md)]|
|[setActiveProcess](formcontext-data-process/activeprocess/setActiveProcess.md)|[!INCLUDE[formcontext-data-process/activeprocess/includes/setActiveProcess-description.md](formcontext-data-process/activeprocess/includes/setActiveProcess-description.md)]|

## <a name="process-methods"></a>Prozessmethoden 

Ein Prozess enthält die Daten eines Geschäftsprozessfluss. Verwenden Sie die Methoden, um auf Eigenschaften des Prozesses zuzugreifen.

|Name | Beschreibung |
|--|--|
|[getId](formcontext-data-process/process/getId.md)|[!INCLUDE[formcontext-data-process/process/includes/getId-description.md](formcontext-data-process/process/includes/getId-description.md)]|
|[getName](formcontext-data-process/process/getName.md)|[!INCLUDE[formcontext-data-process/process/includes/getName-description.md](formcontext-data-process/process/includes/getName-description.md)]|
|[getStages](formcontext-data-process/process/getStages.md)|[!INCLUDE[formcontext-data-process/process/includes/getStages-description.md](formcontext-data-process/process/includes/getStages-description.md)]|
|[isRendered](formcontext-data-process/process/isRendered.md)|[!INCLUDE[formcontext-data-process/process/includes/isRendered-description.md](formcontext-data-process/process/includes/isRendered-description.md)]|


## <a name="processinstance-methods"></a>ProcessInstance-Methoden

Verwenden Sie diese Methoden, um Informationen zu allen Prozessinstanzen für einen Entitätsdatensatz abzurufen und , um eine Prozessinstanz als aktive Instanz festzulegen.

|Name | Beschreibung |
|--|--|
|[getProcessInstances](formContext-data-process/getProcessInstances.md)|[!INCLUDE[formcontext-data-process/includes/getProcessInstances-description.md](formcontext-data-process/includes/getProcessInstances-description.md)]|
|[setActiveProcessInstance](formContext-data-process/setActiveProcessInstance.md)|[!INCLUDE[formcontext-data-process/includes/setActiveProcessInstance-description.md](formcontext-data-process/includes/setActiveProcessInstance-description.md)]|


## <a name="instance-methods"></a>Instanzmethoden 

Eine Prozessinstanz enthält die Daten für eine Instanz des Geschäftsprozessflusses. Verwenden Sie die Methoden, um auf Eigenschaften der Prozessinstanz zuzugreifen.

|Name | Beschreibung |
|--|--|
|[getInstanceId](formcontext-data-process/instance/getInstanceId.md)|[!INCLUDE[formcontext-data-process/instance/includes/getInstanceId-description.md](formcontext-data-process/instance/includes/getInstanceId-description.md)]|
|[getInstanceName](formcontext-data-process/instance/getInstanceName.md)|[!INCLUDE[formcontext-data-process/instance/includes/getInstanceName-description.md](formcontext-data-process/instance/includes/getInstanceName-description.md)]|
|[getStatus](formcontext-data-process/instance/getStatus.md)|[!INCLUDE[formcontext-data-process/instance/includes/getStatus-description.md](formcontext-data-process/instance/includes/getStatus-description.md)]|
|[setStatus](formcontext-data-process/instance/setStatus.md)|[!INCLUDE[formcontext-data-process/instance/includes/setStatus-description.md](formcontext-data-process/instance/includes/setStatus-description.md)]|

## <a name="active-stage-methods"></a>Aktive Phasenmethoden

Verwenden Sie diese Methoden, um Informationen zur aktiven Phase abzurufen, und , um eine andere Phase als aktive Phase Entität festzulegen.

|Name | Beschreibung |
|--|--|
|[getActiveStage](formcontext-data-process/activestage/getActiveStage.md)|[!INCLUDE[formcontext-data-process/activestage/includes/getActiveStage-description.md](formcontext-data-process/activestage/includes/getActiveStage-description.md)]|
|[setActiveStage](formcontext-data-process/activestage/setActiveStage.md)|[!INCLUDE[formcontext-data-process/activestage/includes/setActiveStage-description.md](formcontext-data-process/activestage/includes/setActiveStage-description.md)]|

## <a name="stage-methods"></a>Phasenmethoden 

Eine Phase enthält die Daten einer Phase in einem Geschäftsprozessfluss. Verwenden Sie die Methoden, um auf Eigenschaften der Phase zuzugreifen.
|Name | Beschreibung|
|--|--|
|[getCategory](formcontext-data-process/stage/getCategory.md)|[!INCLUDE[formcontext-data-process/stage/includes/getCategory-description.md](formcontext-data-process/stage/includes/getCategory-description.md)]|
|[getEntityName](formcontext-data-process/stage/getEntityName.md)|[!INCLUDE[formcontext-data-process/stage/includes/getEntityName-description.md](formcontext-data-process/stage/includes/getEntityName-description.md)]|
|[getId](formcontext-data-process/stage/getId.md)|[!INCLUDE[formcontext-data-process/stage/includes/getId-description.md](formcontext-data-process/stage/includes/getId-description.md)]|
|[getName](formcontext-data-process/stage/getName.md)|[!INCLUDE[formcontext-data-process/stage/includes/getName-description.md](formcontext-data-process/stage/includes/getName-description.md)]|
|[getNavigationBehavior](formcontext-data-process/stage/getNavigationBehavior.md)|[!INCLUDE[formcontext-data-process/stage/includes/getNavigationBehavior-description.md](formcontext-data-process/stage/includes/getNavigationBehavior-description.md)]|
|[getStatus](formcontext-data-process/stage/getStatus.md)|[!INCLUDE[formcontext-data-process/stage/includes/getStatus-description.md](formcontext-data-process/stage/includes/getStatus-description.md)]|
|[getSteps](formcontext-data-process/stage/getSteps.md)|[!INCLUDE[formcontext-data-process/stage/includes/getSteps-description.md](formcontext-data-process/stage/includes/getSteps-description.md)]|

## <a name="step-methods"></a>Schrittmethoden

Ein Schritt enthält die Daten für einen Schritt in einem Geschäftsprozessfluss. Verwenden Sie die Methoden, um auf Eigenschaften des Schritts zuzugreifen.

|Name | Beschreibung|
|--|--|
|[getAttribute](formcontext-data-process/step/getAttribute.md)|[!INCLUDE[formcontext-data-process/step/includes/getAttribute-description.md](formcontext-data-process/step/includes/getAttribute-description.md)]|
|[getName](formcontext-data-process/step/getName.md)|[!INCLUDE[formcontext-data-process/step/includes/getName-description.md](formcontext-data-process/step/includes/getName-description.md)]|
|[getProgress](formcontext-data-process/step/getProgress.md)|[!INCLUDE[formcontext-data-process/step/includes/getProgress-description.md](formcontext-data-process/step/includes/getProgress-description.md)]|
|[isRequired](formcontext-data-process/step/isRequired.md)|[!INCLUDE[formcontext-data-process/step/includes/isRequired-description.md](formcontext-data-process/step/includes/isRequired-description.md)]|
|[setProgress](formcontext-data-process/step/setProgress.md)|[!INCLUDE[formcontext-data-process/step/includes/setProgress-description.md](formcontext-data-process/step/includes/setProgress-description.md)]|

## <a name="navigation-methods"></a>Navigationsmethoden

Verwenden Sie diese Methoden, um die zu den nächsten und vorherigen Phasen zu gelangen. Diese beiden Methoden verursachen ein OnStageChange-Ereignis.

|Name | Beschreibung|
|--|--|
|[moveNext](formContext-data-process/navigation/moveNext.md)|[!INCLUDE[formcontext-data-process/navigation/includes/moveNext-description.md](formcontext-data-process/navigation/includes/moveNext-description.md)]|
|[movePrevious](formContext-data-process/navigation/movePrevious.md)|[!INCLUDE[formcontext-data-process/navigation/includes/movePrevious-description.md](formcontext-data-process/navigation/includes/movePrevious-description.md)]|

## <a name="other-useful-methods"></a>Weitere hilfreiche Methoden

Mithilfe dieser Methoden, um Informationen zu Phasen im aktiven Pfad, zu aktivierten Prozessen und zur ausgewählten Phase zu suchen.

|Name | Beschreibung|
|--|--|
|[getActivePath](formContext-data-process/activepath/getActivePath.md)|[!INCLUDE[formcontext-data-process/activepath/includes/getActivePath-description.md](formcontext-data-process/activepath/includes/getActivePath-description.md)]|
|[getEnabledProcesses](formContext-data-process/getEnabledProcesses.md)|[!INCLUDE[formcontext-data-process/includes/getEnabledProcesses-description.md](formcontext-data-process/includes/getEnabledProcesses-description.md)]|
|[getSelectedStage](formContext-data-process/getSelectedStage.md)|[!INCLUDE[formcontext-data-process/includes/getSelectedStage-description.md](formcontext-data-process/includes/getSelectedStage-description.md)]|

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui.process (Client-API-Referenz)](formContext-ui-process.md)

[Verständnis des Xrm-Objektmodells](../understand-clientapi-object-model.md)

[Steuerelemente (Client-API-Referenz)](controls.md)





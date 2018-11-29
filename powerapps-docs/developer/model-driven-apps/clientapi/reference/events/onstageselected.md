---
title: OnStageSelected-Ereignis (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1ef0f11c-6188-4492-ae61-260a402223b8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="onstageselected-event-client-api-reference"></a>OnStageSelected-Rasterereignis (Client-API-Referenz)



Dieses Ereignis tritt auf, wenn die Geschäftsprozessflusssteuerung ausgewählt wird. Sie können die Phasenauswahl nicht mithilfe von Code in einem Handler für dieses Ereignis abbrechen.

Sie können die [getEventArgs](../executioncontext/getEventArgs.md)-Methode verwenden, um ein Objekt abzurufen, das über die folgende Methode verfügt:

**getStage**: Gibt ein Phasenobjekt zurück, das die ausgewählte Phase darstellt. Weitere Informationen: [Phasenmethoden](../formContext-data-process.md#stage-methods).

## <a name="methods-supported-for-this-event"></a>Unterstütze Möglichkeiten für das Ereignis
- **formContext.data.process**.[addOnStageSelected](../formcontext-data-process/eventhandlers/addOnStageSelected.md)-Methode, um Ereignishandler für das Ereignis hinzuzufügen.
- **formContext.data.process**.[removeOnStageSelected](../formcontext-data-process/eventhandlers/addOnStageSelected.md)-Methode, um Ereignishandler vom Ereignis zu entfernen. 




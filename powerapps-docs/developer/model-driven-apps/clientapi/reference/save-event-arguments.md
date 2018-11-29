---
title: Speichern von Ereignisargumenten (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: dff20ae0-c9ec-4413-9cd1-0ff77639ad91
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="save-event-arguments-client-api-reference"></a>Ereignisargumente speichern (Client-API-Referenz)



Wen das [OnSave](events/form-onsave.md)-Formularereignis auftritt, können Sie die [getEventArgs](executioncontext/getEventArgs.md)-Methode des Ausführungskontextobjekts verwenden, um ein Objekt abzurufen, das Methoden enthält, die Sie verwenden können, um das Speichern-Ereignis zu verwalten.

|Methode|Beschreibung|
|--|--|
|[getSaveMode](save-event-arguments/getSaveMode.md)|[!INCLUDE[save-event-arguments/includes/getSaveMode-description.md](save-event-arguments/includes/getSaveMode-description.md)]|
|[isDefaultPrevented](save-event-arguments/isDefaultPrevented.md)|[!INCLUDE[save-event-arguments/includes/isDefaultPrevented-description.md](save-event-arguments/includes/isDefaultPrevented-description.md)]|
|[preventDefault](save-event-arguments/preventDefault.md)|[!INCLUDE[save-event-arguments/includes/preventDefault-description.md](save-event-arguments/includes/preventDefault-description.md)]|


## <a name="related-topics"></a>Verwandte Themen

[Client-API-Ausführungskontext](../clientapi-execution-context.md)

[Ausführungskontextmethoden](execution-context.md)


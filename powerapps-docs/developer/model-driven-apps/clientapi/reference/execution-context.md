---
title: Client API-Ausführung in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: 1fcbf0fd-4e47-4352-a555-9315f7e57331
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="execution-context-client-api-reference"></a>Ausführungskontext (Client API Referenz)



Der Ausführungskontext definiert den Ereigniskontext, an dem Ihr Code ausgeführt wird. Weitere Informationen: [Client API-Ausführungskontext](../clientapi-execution-context.md).

Der Ausführungskontext stellt die folgenden Methoden bereit.

|Methode |Beschreibung |
|---|---|
|[getDepth](executioncontext/getDepth.md)|Gibt einen Wert zurück, der die Reihenfolge angibt, in der dieser Handler ausgeführt wird.|
|[getEventArgs](executioncontext/getEventArgs.md)|Gibt ein Objekt mit Möglichkeiten zurück, das Ereignis **OnSave** zu verwalten.|
|[getEventSource](executioncontext/getEventSource.md)|Gibt einen Verweis auf das Objekt zurück, auf dem das Ereignis aufgetreten ist.|
|[getFormContext](executioncontext/getFormContext.md)|Gibt einen Verweis auf ein Formular oder ein Element im Formular zurück, für das die Methode aufgerufen wurde.|
|[getSharedVariable](executioncontext/getSharedVariable.md)|Ruft eine Variable ab, die mithilfe von [setSharedVariable](executioncontext/setSharedVariable.md) festgelegt wurde.|
|[setSharedVariable](executioncontext/setSharedVariable.md)|Legt den Wert für eine Variable fest, die von einem Handler verwendet werden kann, nachdem der aktuelle Handler seine Ausführung beendet.|

### <a name="related-topics"></a>Verwandte Themen

[Client-API-Ausführungskontext](../clientapi-execution-context.md)

[Ereignis-Argumente speichern](save-event-arguments.md)

[Grundlegendes zum Client API-Objektmodell](../understand-clientapi-object-model.md) 


---
title: getEventsSource (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
description: 'Infos zur getEventSource-Methode, die einen Verweis auf das Objekt zurückgibt, auf dem das Ereignis aufgetreten ist.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9f3b2fed-fde5-46e4-8c59-43aa51aa82df
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="geteventsource-client-api-reference"></a>getEventSource (Client-API-Referenz)



Gibt einen Verweis auf das Objekt zurück, auf dem das Ereignis aufgetreten ist.

## <a name="syntax"></a>Syntax

`ExecutionContextObj.getEventSource()`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Objekt.

**Beschreibung**: Gibt das Objekt vom **Xrm**-Objektmodell zurück, das die Ursache des Ereignisses ist, nicht ein HTM LDOM-Objekt. Beispielsweise gibt diese Methode in einem [OnChange](../events/attribute-onchange.md)-Ereignis das **formContext.data.entity**-Attributobjekt zurück, das das geänderte Attribut darstellt.


### <a name="related-topics"></a>Verwandte Themen
[Context-Ausführungen](../execution-context.md)






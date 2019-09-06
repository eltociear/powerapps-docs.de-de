---
title: onPreProcessStatusChange-Ereignis (Client-API-Referenz) in Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 06/30/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: MSFTMan
ms.author: Deonhe
manager: KVivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="onpreprocessstatuschange-event-client-api-reference"></a>onPreProcessStatusChange-Ereignis (Client-API-Referenz)

[!INCLUDE[](../../../../../includes/cc_applies_to_update_9_0_0.md)]

Dieses Ereignis tritt auf, **bevor** der Status einer Prozessinstanz wechselt. 

Verwenden Sie die **formContext.data.process**.[addOnPreProcessStatusChange](../formContext-data-process/eventhandlers/addOnPreProcessStatusChange.md)-Methode, um Ereignishandler für dieses Ereignis hinzuzufügen, und die **formContext.data.process**.[removeOnPreProcessStatusChange](../formContext-data-process/eventhandlers/removeOnPreProcessStatusChange.md)-Methode, um diese zu entfernen. 

Über ein Webressourcenskript, das für das onPreProcessStatusChange-Ereignis registriert wurde, kann ein Entwickler folgende Schritte für das executionContext-Objekt aufrufen, das an das Webressourcenskript übergeben wird: 

`executionContext.getEventArgs().preventDefault();` 

Wenn Sie `preventDefault` aufrufen:

- Die Statusänderung wird nicht verarbeitet. Die Prozessinstanz bleibt in der ursprünglichen Phase im Originalzustand.
- Die Speichern des Hauptformulars wird nicht verarbeitet. Wenn das Hauptformular in einem geänderten Status war, bleibt es im geänderten Status.
- Webressourcen mit onProcessStatusChange-Registrierung werden nicht aufgerufen.

Diese Client-API wird nur im einheitlichen Client unterstützt. Der Vorgängerwebclient unterstützt diese Client-API nicht.

## <a name="methods-supported-for-this-event"></a>Unterstütze Möglichkeiten für das Ereignis
- **formContext.data.process**.[addOnPreProcessStatusChange](../formcontext-data-process/eventhandlers/addOnPreProcessStatusChange.md)-Methode, um Ereignishandler für dieses Ereignis hinzuzufügen.
- **formContext.data.process**.[removeOnPreProcessStatusChange](../formcontext-data-process/eventhandlers/removeOnPreProcessStatusChange.md)-Methode, um Ereignishandler vom Ereignis zu entfernen. 

---
title: Form data OnLoad Ereignis (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: fb13c0a1-0e00-4592-8e58-3c2412141fbd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="form-data-onload-event-client-api-reference"></a>Formulardaten OnLoad-Ereignis (Client-API-Referenz)



Dieses Ereignis tritt immer auf, wenn Formulardaten geladen werden, speziell:

- Beim erstmaligen Laden einer Seite
- Wenn die Seitendaten explizit mithilfe der formContext.data-Methode aktualisiert werden.[Aktualisieren](../formContext-data/refresh.md).
- Wenn die Daten für eine Seite beim Speichern eines Datensatzes aktualisiert werden, wenn er Änderungen enthält.
 
Verwenden Sie die formContext.data.[addOnLoad](../formContext-data/addOnLoad.md) und formContext.data.[removeOnLoad](../formContext-data/removeOnLoad.md)-Methode, um Ereignishandler für das Ereignis zu verwalten. 




---
title: TabStateChange-Ereignis (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="tabstatechange-event-client-api-reference"></a>TabStateChange-Ereignis (Client-API-Referenz)



Das Ereignis tritt auf, wenn der Parameter **DisplayState** der Registerkarte aufgrund einer Benutzerinteraktion sich ändert oder wenn die [setDisplayState](../formContext-ui-tabs/setDisplayState.md)-Methode in Code angewendet wird. 

Verwenden Sie dieses Ereignis, wenn die Eigenschaft **src** eines IFRAMEs auf der Registerkarte ändern möchten. Wenn Sie die Eigenschaft IFrame.**src** des OnLoad-Ereignisses für ein IFRAME auf einer ausgeblendeten Registerkarte festlegen, wird der Wert überschrieben, wenn die Registerkarte erweitert wird.

Verwenden Sie die [addTabStateChange](../formContext-ui-tabs/addTabStateChange.md)-Methode, um Ereignishandler für dieses Ereignis hinzuzufügen, und die [removeTabStateChange](../formContext-ui-tabs/removeTabStateChange.md)-Methode, um diese zu entfernen.




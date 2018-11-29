---
title: Nachschlagesteuerungs-PreSearch-Ereignis (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="lookup-control-presearch-event-client-api-reference"></a>PreSearch-Ereignis Nachschlagesteuerelement (Client-API-Referenz)



Dieses Ereignis tritt auf, kurz bevor das Suchen-Steuerelement ein Dialogfeld startet, um Datensätze zu suchen. Es gibt keine UI, um für dieses Ereignis Ereignishandler festzulegen. Sie müssen die [addPreSearch](../controls/addpresearch.md)- und [removePreSearch](../controls/removepresearch.md)-Methode im Nachschlagesteuerelement verwenden, um von Ereignishandler für das Ereignis hinzuzufügen oder zu entfernen.

Verwenden Sie dieses Ereignis mit anderen Suchen-Steuerelementmethoden, um die Ergebnisse zu ändern, die in einer Suche nach dem auf Basis der Formulardaten angezeigt werden, die aktuell waren, kurz bevor das Nachschlagesteuerelement Suchergebnisse anzeigt, damit der Benutzer eines auswählt. 

## <a name="related-topics"></a>Verwandte Themen

[addCustomFilter](../controls/addCustomFilter.md)




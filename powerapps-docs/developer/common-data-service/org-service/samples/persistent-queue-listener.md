---
title: 'Beispiel: Persistenter Warteschlangenlistener (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie eine Azure Service Bus-Listeneranwendung für einen persistenten Warteschlangenendpunktvertrag geschrieben wird.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-persistent-queue-listener"></a>Beispiel: Persistenter Warteschlangenlistener

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/sample-persistent-queue-listener -->

Dieses Beispiel zeigt, wie eine Azure Service Bus-Listeneranwendung für einen persistenten Warteschlangenendpunktvertrag geschrieben wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PersistentQueueListener) herunterladen.

Der Listener wartet, bis eine eine Nachricht im Servicebus veröffentlicht wird und in der Endpunktwarteschlange verfügbar ist. Wenn eine Nachricht in der Warteschlange verfügbar ist, liest der Listener die Nachricht, druckt den Ausführungskontext in der Konsole aus und entfernt die Nachricht aus der Warteschlange.

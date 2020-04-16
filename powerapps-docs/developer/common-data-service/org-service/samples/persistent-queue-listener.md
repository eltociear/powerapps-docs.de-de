---
title: 'Beispiel: Persistenter Warteschlangenlistener (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie eine Azure Service Bus-Listeneranwendung für einen persistenten Warteschlangenendpunktvertrag geschrieben wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: f277caf86819ee00ead90855a6d60e09e76ec077
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155706"
---
# <a name="sample-persistent-queue-listener"></a>Beispiel: Persistenter Warteschlangenlistener

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-persistent-queue-listener -->

Dieses Beispiel zeigt, wie eine Azure Service Bus-Listeneranwendung für einen persistenten Warteschlangenendpunktvertrag geschrieben wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/PersistentQueueListener) herunterladen.

Der Listener wartet, bis eine eine Nachricht im Servicebus veröffentlicht wird und in der Endpunktwarteschlange verfügbar ist. Wenn eine Nachricht in der Warteschlange verfügbar ist, liest der Listener die Nachricht, druckt den Ausführungskontext in der Konsole aus und entfernt die Nachricht aus der Warteschlange.

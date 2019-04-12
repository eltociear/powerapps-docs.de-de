---
title: 'Beispiel: REST-Listener (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie ein Azure Service Bus-Listener für einen REST-Endpunktvertrag geschrieben wird.'
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
# <a name="sample-rest-listener"></a>Beispiel: REST-Listener

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rest-listener -->

Dieses Beispiel zeigt, wie ein `Azure Service Bus` Listener für einen `REST`-Endpunktvertrag geschrieben wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RESTListener) herunterladen.

Dieses Beispiel registriert ein Remote-Plug-In, das immer dann ausgeführt wird, wenn eine Nachricht an einen `REST`-Endpunkt auf dem Servicebus veröffentlicht wird. Wenn das Plug-In ausgeführt wird, druckt es auf der Konsole den Inhalt des Ausführungskontexts aus, der in der Nachricht enthalten ist.

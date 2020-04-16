---
title: 'Beispiel: REST-Listener (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie ein Azure Service Bus-Listener für einen REST-Endpunktvertrag geschrieben wird.
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
ms.openlocfilehash: 336350bc0a4c61b1342b36c6e4cce519e9501578
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155666"
---
# <a name="sample-rest-listener"></a>Beispiel: REST-Listener

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rest-listener -->

Dieses Beispiel zeigt, wie ein `Azure Service Bus` Listener für einen `REST`-Endpunktvertrag geschrieben wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RESTListener) herunterladen.

Dieses Beispiel registriert ein Remote-Plug-In, das immer dann ausgeführt wird, wenn eine Nachricht an einen `REST`-Endpunkt auf dem Servicebus veröffentlicht wird. Wenn das Plug-In ausgeführt wird, druckt es auf der Konsole den Inhalt des Ausführungskontexts aus, der in der Nachricht enthalten ist.

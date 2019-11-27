---
title: 'Beispiel: REST-Listener (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie ein Azure Service Bus-Listener für einen REST-Endpunktvertrag geschrieben wird.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 03e5fbf4511a651baccc79ef512d7439a23cee6f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748728"
---
# <a name="sample-rest-listener"></a>Beispiel: REST-Listener

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-rest-listener -->

Dieses Beispiel zeigt, wie ein `Azure Service Bus` Listener für einen `REST`-Endpunktvertrag geschrieben wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RESTListener) herunterladen.

Dieses Beispiel registriert ein Remote-Plug-In, das immer dann ausgeführt wird, wenn eine Nachricht an einen `REST`-Endpunkt auf dem Servicebus veröffentlicht wird. Wenn das Plug-In ausgeführt wird, druckt es auf der Konsole den Inhalt des Ausführungskontexts aus, der in der Nachricht enthalten ist.

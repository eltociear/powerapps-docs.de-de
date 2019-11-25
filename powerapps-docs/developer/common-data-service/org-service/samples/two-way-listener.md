---
title: 'Beispiel: Bidirektionaler Listener (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel zeigt, wie ein Azure Service Bus-Listener für einen bidirektionalen Endpunktvertrag geschrieben wird.
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
ms.openlocfilehash: 66918421cb999ccb3d24764172bbf43062b49f6e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748707"
---
# <a name="sample-two-way-listener"></a>Beispiel: Bidirektionaler Listener

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-two-way-listener -->

Dieses Beispiel zeigt, wie ein `Azure Service Bus` für Listener einen bidirektionalen Endpunktvertrag schreiben muss. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/TwoWayListener) herunterladen.

Dieses Beispiel registriert ein Remote-Service-Plug-In, das immer dann ausgeführt wird, wenn eine Nachricht an einen bidirektionalen Endpunkt auf `Azure Service Bus` veröffentlicht wird. Wenn das Plug-In ausgeführt wird, druckt es auf der Konsole den Inhalt des Ausführungskontexts aus, der in der Nachricht enthalten ist.

---
title: 'Beispiel: Eindirektionaler Listener (Common Data Service) | Microsoft-Dokumentation'
description: Diese Beispiel zeigt, wie die Anwendung ein Remote-Dienst-Plug-In registriert, das ausgeführt wird, wenn eine-Nachricht an einen eindirektionalen Endpunkt gesendet wird.
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
ms.openlocfilehash: 9cce040d4fb011570c591adf221a06292c8efbff
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748739"
---
# <a name="sample-one-way-listener"></a>Beispiel: Eindirektionaler Listener

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-one-way-listener -->

Dieses Beispiel zeigt, wie ein `Azure Service Bus`-Listener für einen eindirektionalen Endpunktvertrag geschrieben wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OneWayListeners) herunterladen.

Diese Beispiel-Listener-Anwendung registriert ein Remote-Dienst-Plug-In, das immer dann ausgeführt wird, wenn eine Nachricht an einen eindirektionalen Endpunkt auf dem `Azure Service Bus` gesendet wird. Wenn das Plug-In ausgeführt wird, gibt es an die Konsole den Inhalt des in der Nachricht enthaltenen -Ausführungskontexts aus. 

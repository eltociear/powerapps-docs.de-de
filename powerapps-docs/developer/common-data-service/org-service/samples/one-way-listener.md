---
title: 'Beispiel: Eindirektionaler Listener (Common Data Service) | Microsoft-Dokumentation'
description: Diese Beispiel zeigt, wie die Anwendung ein Remote-Dienst-Plug-In registriert, das ausgeführt wird, wenn eine-Nachricht an einen eindirektionalen Endpunkt gesendet wird.
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
ms.openlocfilehash: 5e588160d35ccc86155134584b4031eb795e4191
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155722"
---
# <a name="sample-one-way-listener"></a>Beispiel: Eindirektionaler Listener

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/sample-one-way-listener -->

Dieses Beispiel zeigt, wie ein `Azure Service Bus`-Listener für einen eindirektionalen Endpunktvertrag geschrieben wird. Sie können das Beispiel [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/OneWayListeners) herunterladen.

Diese Beispiel-Listener-Anwendung registriert ein Remote-Dienst-Plug-In, das immer dann ausgeführt wird, wenn eine Nachricht an einen eindirektionalen Endpunkt auf dem `Azure Service Bus` gesendet wird. Wenn das Plug-In ausgeführt wird, gibt es an die Konsole den Inhalt des in der Nachricht enthaltenen -Ausführungskontexts aus. 

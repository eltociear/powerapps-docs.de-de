---
title: Geschäftslogik in einer Common Data Service anwenden | Microsoft-Dokumentation
description: Informationen über verschiedene Typen der Geschäftslogik, die Sie in Ihrer App verwenden können
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9267f8385e19d3c0b87a36b495a4ff2b88b4d420
ms.sourcegitcommit: f70be39855e4931312fe0035525586a15ed4487b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2019
ms.locfileid: "2922367"
---
# <a name="apply-business-logic-in-common-data-service"></a>Geschäftslogik anwenden in Common Data Service
Für die Anwendung der Geschäftslogik in Common Data Service stehen mehrere Optionen zur Verfügung. 

## <a name="business-rules"></a>Geschäftsregeln
Sie können Geschäftsregeln und Empfehlungen erstellen, um Logik und Validierungen anzuwenden, ohne -Code zu schreiben oder Plug-ins zu erstellen. Geschäftsregeln bieten eine einfache Schnittstelle, um sich schnell ändernden und häufig verwendeten Regeln zu implementieren und zu verwalten.

Definieren Sie *Geschäftsregeln* für eine Entität, die für alle Entitätsformen und auf Serverebene gelten. Die für eine Entität definierten Geschäftsregeln gelten sowohl für *Canvas-Apps* als auch für *modellgesteuerte Apps*, wenn die Entität in der App verwendet wird. Weitere Informationen finden Sie unter [Erstellen einer Geschäftsregel für eine Entität](data-platform-create-business-rule.md)

> [!NOTE]
> Um eine Geschäftsregel zu definieren, die für ein Formular in einer modellgesteuerten Anwendung gilt, siehe [Geschäftsregeln für ein modellgesteuertes App-Formular](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md) erstellen.

## <a name="power-automate"></a>Power Automate
Power Automate verfügt über mehrere verschiedene Flows, mit denen Sie automatisierte Workflows innerhalb von Common Data Service oder zwischen Common Data Service und einer anderen App oder einem anderen Dienst erstellen können, die bzw. der zum Synchronisieren von Dateien, Abrufen von Benachrichtigungen, Sammeln von Daten und mehr verwendet werden kann. 


|Flowtyp  |Beschreibung  |Weitere Informationen  |
|---------|---------|---------|
|Geschäftsprozessflüsse     | Definieren Sie eine Reihe von Schritte, die in einer modellgesteuerten Power Apps-App ausgeführt wird, denen Benutzer folgen, um ein erwünschtes Ergebnis zu erzielen.        | [Weitere Informationen](/power-automate/create-business-process-flow)     |
|Automatisierte Flows     |  Erstellen eines Flows, der eine oder mehrere Aufgaben automatisch ausführt, nachdem er durch ein Ereignis ausgelöst wurde.    | [Weitere Informationen](/power-automate/get-started-logic-flow)        |
|Schaltflächenflows   | Führen Sie sich wiederholende Aufgaben jederzeit von jedem beliebigen Ort aus über eine Flow-App auf Ihrem Mobilgerät aus.        | [Weitere Informationen](/power-automate/introduction-to-button-flows)        |
|Geplante Flows   | Erstellen Sie einen Flow, der eine oder mehrere Aufgaben nach einem Zeitplan ausführt.    | [Weitere Informationen](/power-automate/run-scheduled-tasks)        |
|Benutzeroberflächenflows   | Zeichen Sie die Wiedergabe manueller Schritte in veralteter Software auf und automatisieren Sie diese.    | [Weitere Informationen](/power-automate/ui-flows/overview)     |


## <a name="classic-common-data-service-processes"></a>Klassische Common Data Service-Prozesse
Sie können auch die klassischen Common Data Service-Prozesse verwenden, also Workflows und Aktionen. Weitere Informationen: [Power AutomateVerwendung von Workflowprozessen](/flow/workflow-processes) und [Power Automate: Aktionsübersicht](/flow/actions).

### <a name="see-also"></a>Siehe auch

[Geschäftslogik in modellgesteuerten Apps anwenden](../model-driven-apps/guide-staff-through-common-tasks-processes.md)

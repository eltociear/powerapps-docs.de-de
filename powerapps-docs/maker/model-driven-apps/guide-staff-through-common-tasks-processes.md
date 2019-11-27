---
title: Wenden Sie angepasste Geschäftslogik mit Geschäftsregeln und Flüssen in Modell-angetriebene Apps an | MicrosoftDocs
description: Informationen über verschiedene Typen der Geschäftslogik, die Sie in Ihrer App verwenden können
ms.custom: ''
ms.date: 08/02/2018
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
ms.openlocfilehash: 5ef65c12c20772a5eb8375b23290dd462b209173
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701969"
---
# <a name="apply-custom-business-logic-with-business-rules-and-flows-in-model-driven-apps"></a>Wenden Sie angepasste Geschäftslogik mit Geschäftsregeln und Flüssen in Modell-angetriebene Apps an

Die Definition und Durchsetzung konsistenter Geschäftsprozesse ist eine der wichtigsten Gründe für die Verwendung von modellgesteuerten Apps. Konsistente Prozesse helfen dabei, sicherzustellen, das sich die Benutzer einer modellgesteuerten App auf ihre Arbeit konzentrieren können und nicht daran denken müssen, eine Reihe manueller Schritte ausführen zu müssen. 

## <a name="business-rules"></a>Geschäftsregeln

Unternehmensregeln bieten eine einfache Schnittstelle, um schnell sich ändernde und häufig verwendeten Regeln zu implementieren und zu verwalten. Der *Umfang* einer Geschäftsregel definiert, wo die Geschäftsregel ausgeführt wird:

|||  
|-|-|  
|**Wenn Sie dieses Element auswählen...**|**Ist der Bereich...**|  
|**Entität**|Alle Formulare und Server|  
|**Alle Formulare**|Alle Formulare|  
|Bestimmtes Formular (z. B. **Firma**-Formular)|Nur dieses Formular| 

Weitere Informationen zum Festlegen der Unternehmensregeln für ein Formular in einer Modell-angetriebenen App finden Sie unter [Erstellen von Geschäftsregeln um Lokik in einem Modell-angetriebenen App-Formular anzuwenden.](create-business-rules-recommendations-apply-logic-form.md)

> [!NOTE]
> Um eine Geschäftsregel für eine Entität zu definieren, damit diese auf der Serverebene für *Canvas-Apps* und *Modell-angetriebene Apps* angezeigt wird, gehen Sie zu[Geschäftsregel für eine Enität erstellen](/powerapps/maker/common-data-service/data-platform-create-business-rule).

## <a name="flows"></a>Flows  
  
Microsoft Flow umfasst mehrere Arten von Prozessen, die jeweils für einen anderen Zweck entwickelt wurden:  

-   Automatisierte Flows Erstellen eines Flows, der eine oder mehrere Aufgaben automatisch ausführt, nachdem er durch ein Ereignis ausgelöst wurde. Weitere Informationen: [Erstellen eines Flows](/flow/get-started-logic-flow)
    
-   Schaltflächenflows. Führen Sie sich wiederholende Aufgaben aus, indem Sie einfach auf eine Schaltfläche auf Ihrem mobilen Gerät tippen. Weitere Informationen: [Einführung in Schaltflächenflows](/flow/introduction-to-button-flows)
  
-   Geplante Flows. Legen Sie einen Flow an, der eine oder mehrere Aufgaben in einem Zeitplan ausführt, z.B. einmal täglich, zu einem bestimmten Datum oder nach einer bestimmten Zeit. Weitere Informationen: [Ausführen von Flows nach einem Zeitplan](/flow/run-scheduled-tasks)
  
-   Geschäftsprozessflows.  Stellen Sie sicher, dass die Mitarbeiter die Daten konsistent eingeben und jedes Mal, wenn sie in einer App arbeiten, die gleichen Schritte ausführen, indem sie einen Geschäftsprozessflow anlegen. Weitere Informationen: [Übersicht über Geschäftsprozessflüsse](/flow/business-process-flows-overview)

-   Workflow und Aktionen. Dynamics 365-Customizer können mit den klassischen Common Data Service-Prozessen, d.h. Workflows und Aktionen, vertraut sein. Weitere Informationen: [Verwendung von Workflowprozessen](/flow/workflow-processes) und [Aktionsübersicht](/flow/actions)
  
## <a name="next-step"></a>Nächster Schritt

[Erstellen von Geschäftsregeln, um Logik in einem Modell-getriebenen App-Formular anzuwenden](create-business-rules-recommendations-apply-logic-form.md)

### <a name="see-also"></a>Siehe auch

[Business-Logik mit Common Data Service anwenden](../common-data-service/cds-processes.md)

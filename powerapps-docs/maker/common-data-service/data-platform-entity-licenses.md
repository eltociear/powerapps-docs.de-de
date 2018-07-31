---
title: Lizenzanforderungen für Entitäten | Microsoft-Dokumentation
description: In diesem Artikel werden die Lizenzanforderungen für Entitäten in Common Data Service (CDS) für Apps erläutert.
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: clwesene
ms.openlocfilehash: 758d5b5ff2c552a4c4ccbf210062f35d4e53209c
ms.sourcegitcommit: efea7ed5ad8e80c87ba423fb094fa94b4e864d75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39265508"
---
# <a name="license-requirements-for-entities"></a>Lizenzanforderungen für Entitäten
Die Entwickler von Apps können die meisten Entitäten verwenden, die in Common Data Service (CDS) für Apps verfügbar sind (einschließlich benutzerdefinierte Entitäten und Entitäten, die Teil von Common Data Model sind), um Apps und Flows für Benutzer zu erstellen, die über eine Lizenz für PowerApps-Plan 1 oder Microsoft Flow-Tarif 1 besitzen. In einigen Fällen enthalten Entitäten komplexe Geschäftslogiken oder sind an Dynamics 365-Anwendungen gebunden, die erfordern, dass die Benutzer der App über eine bestimmte Lizenz verfügen. 


|Einrichtung  |Beschreibung  |Anforderung  |
|---------|---------|---------|
|Entitäten mit komplexer Geschäftslogik  | Hierbei handelt es sich um Entitäten, die komplexe serverseitige Geschäftslogik verwenden. Zum Beispiel eine Entität, die einen Echtzeitworkflow oder ein Code-Plug-in verwendet.     | [PowerApps-Plan 2](https://powerapps.microsoft.com/pricing/) oder [Flow-Plan 2](https://flow.microsoft.com/pricing/)  | 
|Eingeschränkte Entitäten    | Dabei handelt es sich um Entitäten, die nicht standardmäßig im Lieferumfang der von Common Data Service für Apps enthalten sind, sondern über eine Dynamics 365-Anwendung oder eine Drittanbieterlösung bezogen werden müssen. Zum Beispiel die Entitäten Knowledge-Artikel, Ziel und Berechtigung.    | [Ein Dynamics 365-Plan](https://dynamics.microsoft.com/pricing/)    |


> [!NOTE]
> Apps und Flows, die diese Entitäten verwenden, erfordern, dass der Benutzer (nicht der Entwickler) der App oder des Flows über die richtige Lizenz verfügt.

## <a name="entities-with-complex-business-logic"></a>Entitäten mit komplexer Geschäftslogik
Entitäten, die folgende komplexe serverseitige Logik enthalten, erfordern, dass die Benutzer einer App oder eines Flows, die diese Entitäten verwenden, über eine Lizenz für PowerApps-Plan 2 oder Microsoft Flow-Tarif 2 verfügen:

* Code-Plug-Ins (weitere Informationen finden Sie unter [Plug-in development (Entwicklung von Plug-Ins)](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development))
* Echtzeitworkflows (weitere Informationen finden Sie unter [Workflowprozesse](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes))

    > [!NOTE]
    >  Nur Workflows, die in einen Echtzeitworkflow konvertiert werden, werden als synchron und in Echtzeit ausgeführt betrachtet. Workflows, die im Hintergrund ausgeführt werden, können vom entsprechenden PowerApps-Plan weiterhin verwendet werden und erfordern keine zusätzlichen Lizenzen.

Überprüfen Sie die Liste der Plug-In-Assemblys und Workflows, die in Ihrer Umgebung konfiguriert sind, um zu ermitteln, ob Sie komplexe Geschäftslogiken zu Ihren Entitäten hinzugefügt haben. Die Liste der Entitäten, die nach der Installation einer Dynamics 365-Anwendung eine serverseitige Logik enthalten können, finden Sie unter [Komplexe Entitäten, die PowerApps Plan 2-Lizenzen erfordern](data-platform-complex-entities.md) 

### <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>Auswirkungen auf Lizenzanforderungen durch das Hinzufügen von komplexer Geschäftslogik
Die Ersteller von Apps können in CDS für Apps Code-Plug-Ins und Echtzeitworkflows zu Entitäten hinzufügen. Dadurch können sich jedoch die Lizenzanforderungen für die Benutzer von bereits bereitgestellten Apps ändern. Die Ersteller von Apps sollten also beim Hinzufügen von komplexer Geschäftslogik zu einer Entität bedacht vorgehen und zuerst überprüfen, welche Apps die Entität verwenden und ob die Benutzer dieser Apps über die erforderlichen Lizenzen verfügen.

## <a name="restricted-entities"></a>Eingeschränkte Entitäten
Bestimmte Entitäten, die an die Funktionalität von Dynamics 365-Anwendungen gebunden sind, erfordern, dass die Benutzer der App über die entsprechenden Lizenzen für die Anwendung verfügen, wenn diese Datensätze innerhalb der Entitäten erstellen, aktualisieren oder löschen möchten. Eine vollständige Liste der eingeschränkten Entitäten finden Sie unter [Restricted entities requiring Dynamics 365 licenses (Eingeschränkte Entitäten, die Dynamics 365-Lizenzen erfordern)](data-platform-restricted-entities.md).

## <a name="licensing-examples"></a>Beispiel für die Lizenzierung
Barbara und Martin erstellen Apps mithilfe von CDS für Apps in PowerApps, um ihre Daten zu speichern.

Barbara erstellt zwei Canvas-Apps:

* App 1 verwendet die Entität „Contact“ (Kontakt) zusammen mit einer benutzerdefinierten Entität, die zugehörige Informationen speichert.
* App 2 verwendet die Entität „Contact“ zusammen mit der Entität „Incident“, bei der es sich um eine eingeschränkte Entität handelt.

Martin erstellt zwei modellgesteuerte Apps:

* App 3 verwendet die Entität „Contact“ (Kontakt) zusammen mit einer benutzerdefinierten Entität, die zugehörige Informationen speichert.
* App 4 verwendet die Entität „Contact“ zusammen mit der Entität „Incident“, bei der es sich um eine eingeschränkte Entität handelt.

Barbara und Martin benötigen folgende Lizenzen:
* Barbara benötigt eine Lizenz für PowerApps-Plan 1, um Canvas-Apps mithilfe von CDS für Apps zu erstellen. Wenn sie eine Datenbank oder eine benutzerdefinierte Entität erstellen möchte, benötigt sie eine Lizenz für PowerApps-Plan 2.

* Martin benötigt eine Lizenz für PowerApps-Plan 2, um modellgesteuerte Apps zu erstellen.

Die Benutzer der Apps benötigen folgende Lizenzen:
* Die Benutzer von App 1 benötigen nur eine Lizenz für PowerApps-Plan 1 oder -Plan 2, da die App keine Entitäten mit komplexer Geschäftslogik und keine eingeschränkten Entitäten enthält.

* Die Benutzer von App 2 benötigen eine Lizenz für Dynamics 365 for Customer Service, Enterprise Edition (oder einen Dynamics 365- oder Dynamics 365 Customer Engagement-Plan), da die App eine eingeschränkte Entität enthält.

* Die Benutzer von App 3 benötigen eine Lizenz für PowerApps-Plan 2, da es sich um eine modellgesteuerte App handelt.

* Die Benutzer von App 4 benötigen eine Lizenz für Dynamics 365 for Customer Service, Enterprise Edition (oder einen Dynamics 365- oder Dynamics 365 Customer Engagement-Plan), da die App eine eingeschränkte Entität enthält.

    Der Dynamics 365 for Customer Service-Plan enthält eine Lizenz für PowerApps-Plan 2, die es dem Benutzer ermöglicht, modellgesteuerte Apps auszuführen.

Achten Sie darauf, was geschieht, wenn Martin einen Echtzeitworkflow zu der benutzerdefinierten Entität hinzufügt, die Barbara und Martin für ihre Apps verwenden.

Barbara und Martin benötigen folgende Lizenzen:
* Barbara benötigt weiterhin eine Lizenz für PowerApps-Plan 1, um Canvas-Apps mithilfe von CDS für Apps zu erstellen.

* Martin benötigt weiterhin eine Lizenz für PowerApps-Plan 2, um modellgesteuerte Apps zu erstellen.

Die Benutzer der Apps benötigen folgende Lizenzen:
* Die Benutzer von App 1 benötigen nun eine Lizenz für PowerApps-Plan 2, da die App eine Entität mit Echtzeitworkflow enthält.

* Die Benutzer von App 2 benötigen weiterhin eine Lizenz für Dynamics 365 for Customer Service, Enterprise Edition (oder einen Dynamics 365- oder Dynamics 365 Customer Engagement-Plan), da die App eine eingeschränkte Entität enthält. 

* Die Benutzer von App 3 benötigen weiterhin eine Lizenz für PowerApps-Plan 2, da es sich um eine modellgesteuerte App handelt.

* Die Benutzer von App 4 benötigen weiterhin eine Lizenz für Dynamics 365 for Customer Service, Enterprise Edition (oder einen Dynamics 365- oder Dynamics 365 Customer Engagement-Plan), da die App eine eingeschränkte Entität enthält.

    Der Dynamics 365 for Customer Service-Plan enthält eine Lizenz für PowerApps-Plan 2, die es dem Benutzer ermöglicht, modellgesteuerte Apps auszuführen.

Die einzige App, auf die sich diese Änderung auswirkt, ist App 1. Für diese war zuvor eine Lizenz für PowerApps-Plan 1 erforderlich, nun ist jedoch eine Lizenz für PowerApps-Plan 2 erforderlich, da sie eine Entität mit komplexer Geschäftslogik enthält. 

## <a name="more-about-licensing"></a>Weitere Informationen zur Lizenzierung
Weitere Informationen zu PowerApps- und Dynamics 365-Lizenzen finden Sie unter [Licensing overview (Übersicht über die Lizenzierung)](../../administrator/pricing-billing-skus.md).

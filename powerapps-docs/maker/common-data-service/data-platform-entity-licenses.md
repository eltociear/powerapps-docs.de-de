---
title: Lizenzanforderungen für Entitäten | Microsoft Docs
description: Eine Erläuterung der Lizenzanforderungen für Unternehmen unter Common Data Service.
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/20/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0a6b950c35043ecf47f45373f758ce62953945e7
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156524"
---
# <a name="license-requirements-for-entities"></a>Lizenzanforderungen für Entitäten

> [!IMPORTANT]
> Aktuelle Informationen zu den Lizenzbestimmungen für Unternehmen finden Sie im [Power Apps Lizenzhandbuch](https://go.microsoft.com/fwlink/p/?linkid=2085130).

App-Ersteller können die meisten der innerhalb von Common Data Service verfügbaren Entitäten (einschließlich benutzerdefinierter Entitäten und Entitäten, die Teil des gemeinsamen Datenmodells sind) verwenden, um Anwendungen und Abläufe für Benutzer zu erstellen, die eine Lizenz für Power Apps Plan 1 oder Power Automate Plan 1 haben. In einigen Fällen enthalten Entitäten komplexe Geschäftslogik oder sind an Dynamics 365-Anwendungen gebunden, die von App-Benutzer eine bestimmte Lizenz erfordern. 


|Entität    |Beschreibung    |Anforderung    |
|---------|---------|---------|
|Entitäten mit komplexer Geschäftslogik   | Dies sind Entitäten, die komplexe serverseitige Geschäftslogik verwenden. Beispielsweise jede Entität, die ein Echtzeitworkflow- oder Code-Plug-In verwendet.       |  [Power Apps Plan 2](https://powerapps.microsoft.com/pricing/) oder [Flow Plan 2](https://flow.microsoft.com/pricing/)        |
|Eingeschränkte Entitäten  |  Dies sind Entitäten, die nicht standardmäßig mit Common Data Service versehen sind, aber in einer modellgetriebenen App in Dynamics 365 (z.B. Dynamics 365 Sales oder Dynamics 365 Customer Service) oder einer Drittanbieterlösung enthalten sind. Beispielsweise die Entitäten für Wissensartikel, Ziel und Anspruch.     |  [Ein Dynamics 365-Plan](https://dynamics.microsoft.com/pricing/)      | 


> [!NOTE]
> Apps und Flows, die diese Entitäten verwenden, erfordern vom App- und Flow-Benutzer eine entsprechende Lizenz, nicht vom Hersteller oder Entwickler der App oder des Flows.

## <a name="entities-with-complex-business-logic"></a>Entitäten mit komplexer Geschäftslogik
Entitäten, die die folgende komplexe serverseitige Logik beinhalten, erfordern, dass Benutzer einer App oder eines Flow, die diese Entitäten verwendet, eine Power Apps Plan 2 oder Power Automate Plan 2 Lizenz besitzen:

* Code-Plug-Ins (weitere Informationen finden Sie unter [Plug-In-Entwicklung](/powerapps/developer/common-data-service/plug-ins))
* Echtzeitworkflows (weitere Informationen finden Sie unter [Workflowprozesse](/flow/workflow-processes))

    > [!NOTE]
    >  Nur Workflows, die in einen Echtzeitworkflow konvertiert werden, werden als in Echtzeit und synchron betrachtet. Workflows, die im Hintergrund laufen, können weiterhin mit dem entsprechenden Power Apps-Plan verwendet werden und benötigen keine zusätzlichen Lizenzen.

Um zu wissen ob Sie Ihren Entitäten komplexere Geschäftslogik hinzugefügt haben, oder nicht, überprüfen Sie die Liste der Plug-In-Assemblys und Workflows, die in Ihrer Umgebung konfiguriert sind. Eine Liste der Entitäten, die nach der Installation einer modellgetriebenen Anwendung in Dynamics 365 serverseitige Logik enthalten können (z.B. Dynamics 365 Sales oder Dynamics 365 Customer Service), finden Sie unter [Komplexe Entitäten, die Power Apps Plan 2 Lizenzen erfordern](data-platform-complex-entities.md).  

### <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>Auswirkungen von Lizenzanforderungen, wenn komplexe Geschäftslogik hinzugefügt wird
App-Erstellerkönnen Code Plug-Ins und Echtzeit-Workflows zu Entitäten innerhalb von Common Data Service hinzufügen, aber dadurch könnten sich die Lizenzanforderungen für Benutzer von bereits installierten Apps ändern. App-Hersteller sollten vorsichtig sein, wenn Sie einer Entität komplexer Geschäftslogik hinzufügen und sollten zuerst überprüfen, welche Apps die Entität verwenden und ob die Benutzer dieser Apps die entsprechenden Lizenzen haben.

## <a name="restricted-entities"></a>Eingeschränkte Entitäten
Bestimmte Entitäten, die an die Funktionsweise von Dynamics 365-Anwendungen gebunden sind, benötigen von App-Benutzern die entsprechende Lizenz für die Anwendung, wenn Sie Datensätzen in den Entitäten erstellen, aktualisieren bzw. löschen möchten. Eine vollständige Liste der eingeschränkten Entitäten finden Sie unter [Eingeschränkten Entitäten, die Dynamics 365-Lizenzen erfordern](data-platform-restricted-entities.md).

## <a name="licensing-examples"></a>Lizenzierungsbeispiele
Barb und Isaac erstellen Apps in Power Apps mit Common Data Service, um ihre Daten zu speichern.

Barb erstellt zwei Canvas-Apps:

* App 1 &ndash; verwendet die Terminentität zusammen mit einer benutzerdefinierten Entität, die zugehörige Informationen speichert
* App 2 &ndash; verwendet die Terminentität zusammen mit der Vorfallentität, die eine eingeschränkte Entität ist

Isaac erstellt zwei modellgesteuerte Apps:

* App 3 &ndash; verwendet die Terminentität zusammen mit einer benutzerdefinierten Entität, die zugehörige Informationen speichert
* App 4 &ndash; verwendet die Terminentität zusammen mit der Vorfallentität, die eine eingeschränkte Entität ist

Barb und Isaac benötigen die folgenden Lizenzen:
* Barb benötigt eine Power Apps Plan 1 Lizenz, um Canvas-Apps mit Common Data Service zu erstellen. Wenn sie eine Datenbank erstellen oder eine benutzerdefinierte Entität erstellen muss, benötigt sie eine Power Apps Plan 2 Lizenz.

* Isaac benötigt eine Power Apps Plan 2 Lizenz, um modellgetriebene Anwendungen zu erstellen.

App-Benutzer benötigen die folgenden Lizenzen:
* App 1-Benutzer benötigen nur eine Power Apps Plan 1 oder Plan 2 Lizenz, da die App keine Entitäten mit komplexer Geschäftslogik oder eingeschränkte Entitäten enthält.

* App 2 Benutzer benötigen eine Dynamics 365 Customer Service, Enterprise Edition Lizenz (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement Plan), da die App eine eingeschränkte Entität beinhaltet.

* App 3 Benutzer benötigen eine Power Apps Plan 2 Lizenz, da es sich um eine modellgetriebene App handelt.

* App 4-Benutzer benötigen eine Dynamics 365 for Customer Service, Enterprise Edition-Lizenz (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement Plan), da die App eine eingeschränkte Entität beinhaltet.

    Der Dynamics 365 for Customer Service-Plan beinhaltet eine Power Apps-Lizenz für Plan 2, die es Benutzern ermöglicht, modellgetriebene Anwendungen auszuführen.

Sehen wir uns jetzt an, was passiert, wenn Isaac der benutzerdefinierten Entität einen Echtzeitworkflow hinzugefügt, den Barb und Isaac in ihren Apps verwenden.

Barb und Isaac benötigen die folgenden Lizenzen:
* Barb benötigt noch eine Power Apps Plan 1 Lizenz, um Canvas-Apps mit Common Data Service zu erstellen.

* Isaac benötigt noch eine Power Apps Plan 2 Lizenz, um modellgetriebene Anwendungen zu erstellen.

App-Benutzer benötigen die folgenden Lizenzen:
* App 1-Benutzer benötigen nun eine Power Apps Plan 2-Lizenz, da die App eine Entität mit einem Echtzeit-Workflow enthält.

* App 2-Benutzer benötigen weiterhin eine Dynamics 365 for Customer Service, Enterprise Edition-Lizenz (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement-Plan), da die App eine eingeschränkte Entität beinhaltet. 

* App 3 Benutzer benötigen weiterhin eine Power Apps Plan 2 Lizenz, da es sich um eine modellgetriebene App handelt.

* App 4-Benutzer benötigen weiterhin eine Dynamics 365 for Customer Service, Enterprise Edition-Lizenz (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement Plan), da die App eine eingeschränkte Entität beinhaltet.

    Der Dynamics 365 for Customer Service-Plan beinhaltet eine Power Apps-Lizenz für Plan 2, die es Benutzern ermöglicht, modellgetriebene Anwendungen auszuführen.

Die einzige, die von dieser Änderung betroffen ist, ist App 1, die bisher eine Power Apps Plan 1-Lizenz benötigte, nun aber eine Power Apps Plan 2-Lizenz benötigt, da sie eine Entität mit komplexer Geschäftslogik enthält. 

## <a name="more-about-licensing"></a>Weitere Informationen zur Lizenzierung
Weitere Informationen zu Power Apps und Dynamics 365 Lizenzen finden Sie unter [Lizenzübersicht](../../administrator/pricing-billing-skus.md).

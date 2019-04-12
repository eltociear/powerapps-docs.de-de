---
title: Lizenzanforderungen für Entitäten | Microsoft Docs
description: Eine Erläuterung der Lizenzanforderungen für Entitäten in Common Data Service.
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 05/01/2018
ms.author: lanced
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="license-requirements-for-entities"></a>Lizenzanforderungen für Entitäten
App-Hersteller können die meisten Entitäten verwenden, die in Common Data Service verfügbar sind (einschließlich benutzerdefinierter Entitäten und Entitäten, die Teil des allgemeinen Datenmodells sind), um Apps und Flows für Benutzer zu erstellen, die eine PowerApps-Plan 1 oder Microsoft Flow Plan 1-Lizenz haben. In einigen Fällen enthalten Entitäten komplexe Geschäftslogik oder sind an Dynamics 365-Anwendungen gebunden, die von App-Benutzer eine bestimmte Lizenz erfordern. 


|Entität    |Beschreibung    |Anforderung    |
|---------|---------|---------|
|Entitäten mit komplexer Geschäftslogik   | Dies sind Entitäten, die komplexe serverseitige Geschäftslogik verwenden. Beispielsweise jede Entität, die ein Echtzeitworkflow- oder Code-Plug-In verwendet.       |  [PowerApps-Plan 2](https://powerapps.microsoft.com/pricing/) oder [Flow-Plan 2](https://flow.microsoft.com/pricing/)        |
|Eingeschränkte Entitäten  |  Dies sind Entitäten, die nicht zum Standard von Common Data Service gehören, sondern in einer Dynamics 365 Customer Engagement-Anwendung oder einer Drittanbieter-Lösung enthalten sind. Beispielsweise die Entitäten für Wissensartikel, Ziel und Anspruch.     |  [Ein Dynamics 365-Plan](https://dynamics.microsoft.com/pricing/)      | 


> [!NOTE]
> Apps und Flows, die diese Entitäten verwenden, erfordern vom App- und Flow-Benutzer eine entsprechende Lizenz, nicht vom Hersteller oder Entwickler der App oder des Flows.

## <a name="entities-with-complex-business-logic"></a>Entitäten mit komplexer Geschäftslogik
Für Entitäten, die die folgende komplexe serverseitige Logik enthalten, benötigen Benutzer einer App oder eines Flows, der diese Entitäten verwendet, eine PowerApps-Plan 2- oder Microsoft Flow Plan 2-Lizenz:

* Code-Plug-Ins (weitere Informationen finden Sie unter [Plug-In-Entwicklung](https://docs.microsoft.com/dynamics365/customer-engagement/developer/plugin-development))
* Echtzeitworkflows (weitere Informationen finden Sie unter [Workflowprozesse](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes))

    > [!NOTE]
    >  Nur Workflows, die in einen Echtzeitworkflow konvertiert werden, werden als in Echtzeit und synchron betrachtet. Workflows, die im Hintergrund ausgeführt werden, können mit dem entsprechenden PowerApps-Plan weiterhin verwendet werden und erfordern keine zusätzlichen Lizenzen.

Um zu wissen ob Sie Ihren Entitäten komplexere Geschäftslogik hinzugefügt haben, oder nicht, überprüfen Sie die Liste der Plug-In-Assemblys und Workflows, die in Ihrer Umgebung konfiguriert sind. Die Liste der Entitäten, die möglicherweise serverseitige Logik enthalten, nachdem Sie eine Dynamics 365-Anwendung eingerichtet haben, finden Sie unter [Komplexe Entitäten, die PowerApps-Plan 2-Lizenzen benötigen](data-platform-complex-entities.md)  

### <a name="impacting-license-requirements-when-adding-complex-business-logic"></a>Auswirkungen von Lizenzanforderungen, wenn komplexe Geschäftslogik hinzugefügt wird
App-Hersteller können Entitäten in Code-Plug-Ins und Echtzeitworkflows in Common Data Service hinzufügen, ändern dabei jedoch die Lizenzanforderungen für Benutzer von bereits bereitgestellten Apps. App-Hersteller sollten vorsichtig sein, wenn Sie einer Entität komplexer Geschäftslogik hinzufügen und sollten zuerst überprüfen, welche Apps die Entität verwenden und ob die Benutzer dieser Apps die entsprechenden Lizenzen haben.

## <a name="restricted-entities"></a>Eingeschränkte Entitäten
Bestimmte Entitäten, die an die Funktionsweise von Dynamics 365-Anwendungen gebunden sind, benötigen von App-Benutzern die entsprechende Lizenz für die Anwendung, wenn Sie Datensätzen in den Entitäten erstellen, aktualisieren bzw. löschen möchten. Eine vollständige Liste der eingeschränkten Entitäten finden Sie unter [Eingeschränkten Entitäten, die Dynamics 365-Lizenzen erfordern](data-platform-restricted-entities.md).

## <a name="licensing-examples"></a>Lizenzierungsbeispiele
Barb und Isaac erstellen Apps in PowerApps mit Common Data Service, um ihre Daten zu speichern.

Barb erstellt zwei Canvas-Apps:

* App 1 &ndash; verwendet die Terminentität zusammen mit einer benutzerdefinierten Entität, die zugehörige Informationen speichert
* App 2 &ndash; verwendet die Terminentität zusammen mit der Vorfallentität, die eine eingeschränkte Entität ist

Isaac erstellt zwei modellgesteuerte Apps:

* App 3 &ndash; verwendet die Terminentität zusammen mit einer benutzerdefinierten Entität, die zugehörige Informationen speichert
* App 4 &ndash; verwendet die Terminentität zusammen mit der Vorfallentität, die eine eingeschränkte Entität ist

Barb und Isaac benötigen die folgenden Lizenzen:
* Barb benötigt noch eine PowerApps-Plan 1-Lizenz, um Canvas-Apps mithilfe von Common Data Service zu erstellen. Wenn sie eine Datenbank oder eine benutzerdefinierte Entität erstellen muss, benötigt Sie eine PowerApps-Plan 2-Lizenz.

* Isaac benötigt eine PowerApps-Plan 2-Lizenz, um modellgesteuerte Apps zu erstellen.

App-Benutzer benötigen die folgenden Lizenzen:
* App 1-Benutzer benötigen nur eine PowerApps-Plan 1 oder Plan 2-Lizenz, da die App keine Entitäten mit komplexer Geschäftslogik oder eingeschränkten Entitäten enthält.

* App 2-Benutzer benötigen eine Lizenz für Dynamics 365 for Customer Service, Enterprise edition (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement Plan), da die App eine eingeschränkte Entität enthält.

* App 3 Benutzer benötigen eine PowerApps-Plan 2-Lizenz , da es eine modellgesteuerte App ist.

* App 4-Benutzer benötigen eine Lizenz für Dynamics 365 for Customer Service, Enterprise edition (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement Plan), da die App eine eingeschränkte Entität enthält.

    Der Dynamics 365 for Customer Service-Plan enthält eine PowerApps-Plan 2-Lizenz, die Benutzern ermöglicht, modellgesteuerte Apps auszuführen.

Sehen wir uns jetzt an, was passiert, wenn Isaac der benutzerdefinierten Entität einen Echtzeitworkflow hinzugefügt, den Barb und Isaac in ihren Apps verwenden.

Barb und Isaac benötigen die folgenden Lizenzen:
* Barb benötigt noch eine PowerApps-Plan 1-Lizenz, um Canvas-Apps mithilfe von Common Data Service zu erstellen.

* Isaac benötigt noch eine PowerApps-Plan 2-Lizenz, um modellgesteuerte Apps zu erstellen.

App-Benutzer benötigen die folgenden Lizenzen:
* Benutzer der App 1 benötigen jetzt eine PowerApps-Plans 2-Lizenz, da die App einer Entität mit einem Echtzeitworkflow enthält.

* App 2-Benutzer benötigen noch eine Lizenz für Dynamics 365 for Customer Service, Enterprise edition (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement Plan), da die App eine eingeschränkte Entität enthält. 

* App 3 Benutzer benötigen noch eine PowerApps-Plan 2-Lizenz , da es eine modellgesteuerte App ist.

* App 4-Benutzer benötigen noch eine Lizenz for Dynamics 365 for Customer Service, Enterprise edition (oder einen Dynamics 365 oder Dynamics 365 Customer Engagement Plan), da die App eine eingeschränkte Entität enthält.

    Der Dynamics 365 for Customer Service-Plan enthält eine PowerApps-Plan 2-Lizenz, die Benutzern ermöglicht, modellgesteuerte Apps auszuführen.

Die einzige App, die von dieser Änderung betroffen ist, ist App 1, die zuvor eine PowerApps-Plan 1-Lizenz erforderte, aber jetzt eine PowerApps-Plan 2-Lizenz benötigt, da sie eine Entität mit komplexer Geschäftslogik enthält. 

## <a name="more-about-licensing"></a>Weitere Informationen zur Lizenzierung
Weitere Informationen zu PowerApps und Dynamics 365-Lizenzen finden Sie unter [Lizenzierungsübersicht](../../administrator/pricing-billing-skus.md).

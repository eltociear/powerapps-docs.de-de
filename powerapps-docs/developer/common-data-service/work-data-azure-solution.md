---
title: Arbeiten mit Dynamics 365-Daten in Ihrer Azure-Lösung (Common Data Service für Apps) | Microsoft Docs
description: 'Das ServiceBusPlugin-Plug-In enthält die Geschäftslogik für die Veröffentlichung des Dynamics 365-Nachrichtenausführungskontexts auf dem Azure-Servicebus. Um dieses Plug-In verwenden zu können, müssen Sie einen Azure-Servicebus-Lösungsendpunkt und einen Schritt für das Plug-In registrieren. Der Schritt definiert, welche Nachrichten- und Entitätskombination, die durch den Dynamics 365-Kernvorgang verarbeitet wird, die Ausführung des Plug-Ins auslösen sollte. ServiceBusPlugin kann nur für die asynchrone Ausführung registriert werden.'
keywords: ''
ms.date: 10/31/2018
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: 1ef66369-71c9-3b89-ac1a-09d523ca737b
author: brandonsimons
ms.author: jdaly
manager: ryjones
ms.reviewer: null
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="work-with-common-data-service-for-apps-data-in-your-azure-solution"></a>Arbeiten mit Common Data Service für Apps-Daten in Ihrer Azure-Lösung

Ein internes Plug-In mit Namen ServiceBusPlugin wird mit Dynamics 365 (online) Common Data Service für Apps bereitgestellt. Das Plug-In enthält die Geschäftslogik für die Veröffentlichung des Dynamics 365-Nachrichtenausführungskontexts im Azure Service Bus. Um dieses Plug-In verwenden zu können, müssen Sie einen Azure-Servicebus-Lösungsendpunkt und einen Schritt für das Plug-In registrieren. Der Schritt definiert, welche Nachrichten- und Entitätskombination, die durch den Dynamics 365-Kernvorgang verarbeitet wird, die Ausführung des Plug-Ins auslösen sollte. ServiceBusPlugin kann nur für die asynchrone Ausführung registriert werden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Registrieren eines Azure-fähigen Plug-Ins mithilfe des Plug-In-Registrierungstools](walkthrough-register-azure-aware-plug-in-using-plug-in-registration-tool.md).  
  
 Darüber hinaus können Sie ein benutzerdefiniertes Plug-In schreiben, das die erforderlichen Codezeilen für die Veröffentlichung über den Servicebus enthält. Das Plug-In wird auf ähnliche Weise registriert, außer dass es im Sandkasten und unter teilweiser Vertrauenswürdigkeit ausgeführt werden muss. Weitere Informationen über das Schreiben eines benutzerdefinierten Plug-Ins, das im Azure Service Bus veröffentlicht werden kann, finden Sie unter [Schreiben eines benutzerdefinierten Azure-fähigen Plug-Ins](write-custom-azure-aware-plugin.md).  
  
 Sie können außerdem eine benutzerdefinierte Workflowaktivität schreiben, die den Ausführungskontext auch über den Servicebus veröffentlichen und diese Aktivität in Ihren Workflow integrieren kann. Beispielcode für eine benutzerdefinierte Azure-fähige Workflowaktivität wird in folgendem Thema bereitgestellt: [Beispiel: Azure-fähige benutzerdefinierte Workflowaktivität](/dynamics365/customer-engagement/developer/sample-azure-aware-custom-workflow-activity) 
  
### <a name="see-also"></a>Siehe auch  
[Schreiben eines Plug-In](write-plug-in.md)<br/>   
[Ereignisausführungspipeline](event-framework.md#event-execution-pipeline)<br/>   
[ServiceEndPoint-Entität](reference/entities/serviceendpoint.md)<br/>
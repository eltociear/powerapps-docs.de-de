---
title: Azure-Integration (Common Data Service) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 06/01/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 46f7c5506f8c26a70188e8b3cec59b26bf13cb1e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861859"
---
# <a name="azure-integration"></a>Azure-Integration

Common Data Service unterstützt die Integration in Azure. Entwickler können Plug-Ins mit Common Data Service registrieren, die Laufzeit-Nachrichtendaten, die als Ausführungskontext bekannt sind, an eine oder mehrere Azure-Lösungen in der Cloud weitergeben können. Dies ist besonders wichtig, da Azure eine von zwei unterstützten Lösungen für die Kommunikation von Laufzeitkontexten ist, die in einem Plug-in an externe Geschäftsanwendungen (LOB, Line-of-Business) geliefert werden. Die andere Lösung ist die externe Kunden-Endpunkt-Zugriffskapazität von einem Plug-In, das im Sandkasten angemeldet ist.

Der Azure Service Bus bietet einen sicheren und zuverlässigen Kommunikationskanal zwischen Common Data Service-Laufzeitdaten und externen cloudbasierten Line-of-Business (LOB)-Anwendungen. Diese Funktion ist besonders hilfreich, um verteilte Common Data Service-Systeme oder andere Common Data Service-Server mit Geschäftsdatenänderungen synchron zu halten.

## <a name="key-elements-of-the-connection"></a>Schlüsselelemente der Verbindung  

 Die Schlüsselelemente, die die Verbindung zwischen Common Data Service und dem Azure Service Bus implementieren, werden später beschrieben. Ein Diagramm im nächsten Abschnitt zeigt diese Elemente in Betrieb.  
  
### <a name="data-context"></a>Datenkontext 

 Der *Datenkontext* enthält die Geschäftsdaten, die als Teil der gegenwärtigen Common Data Service-Operation verarbeitet werden. Diese Verarbeitung wurde initiiert, als eine Anfrage von einem Benutzer, Workflow oder einer Anwendung zur Durchführung eine bestimmte Operation an die Dynamics 365-Plattform gestellt wurde. Der Datenkontext wird allen Plug-Ins oder benutzerdefinierten Workflow-Aktivitäten weitergeleitet, die für die Ereignis-Pipeline registriert wurden, um bei der spezifischen Anfragen- und Entitätskombination, die derzeit verarbeitet wird, ausgeführt zu werden. Der Datenkontext ist vom Typ <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>, wenn er entlang der Ereignisausführungspipeline weitergeleitet wird und <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> wenn er zum Service-Bus bekannt übergeben wird.  
  
 Der Datenkontext, der in der Message enthalten ist, die zu Azure Service Bus übergeben wird, kann zusätzlich zum binären Standard-.NET Format in XML oder JSON formatiert werden. Dies ermöglicht plattformübergreifende Interoperabilität, bei der mit Azure gehostete nicht-.NET-Clients Common Data Service-Daten vom Service-Bus lesen können. 

> [!IMPORTANT]
> Wenn die Größe der gesamten HTTP-Nutzlast 192 Kb überschreitet, werden die folgenden Eigenschaften entfernt:
>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.ParentContext>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.InputParameters>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PreEntityImages>
> - <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.PostEntityImages>
>
> Einige Operationen enthalten diese Eigenschaften nicht. 
>
> - Wenn die Größe der Nutzlast unter 192Kb liegt, nachdem die zusätzlichen Daten entfernt wurden, wird der vom System gesendeten [BrokeredMessage](/dotnet/api/microsoft.servicebus.messaging.brokeredmessage) eine zusätzliche `MessageMaxSizeExceeded`-Eigenschaft hinzugefügt. Dadurch wird angegeben, dass einige der Daten abgeschnitten wurde.
> - Wenn die Größe der Nutzlast 192 Kb überschreitet, nachdem die zusätzlichen Daten entfernt wurden, wird ein Fehler generiert wird die Meldung wird nicht gesendet.
  
 Weitere Informationen zu den zuvor beschriebenen Technologien finden Sie unter:
 - [Ereignisausführungspipeline](event-framework.md#event-execution-pipeline)
 - [Schreiben einer Listener-Anwendung für eine Microsoft Azure-Lösung](write-listener-application-azure-solution.md).  
  
### <a name="plug-ins"></a>Plug-Ins

Plug-Ins sind eine von zwei Methoden, die angewendet werden, um die Message zu posten, die den Datenkontext zu Azure Service Bus enthält. Die andere Methode ist eine benutzerdefinierte Workflowaktivität. Es gibt zwei Typen von Plug-Ins, die durch die Common Data Service-Azure-Verbindungsfunktion unterstützt werden: benutzerdefinierte und vordefinierte (OOB). In beiden Fällen wird es empfohlen, dass Sie die Plug-Ins registrieren, damit sie für beste Systemleistung asynchron ausgeführt werden.  
  
Ein Azure-fähiges OOB-Plug-In wird mit Common Data Service bereitgestellt und kann unter Verwendung des Plug-In-Registrierungstools registriert werden. Dieses Plug-In wird in vollständiger Vertrauensstellung mit der Common Data Service ausgeführt. Sie müssen in der Ereignisausführungspipeline einen Plug-In-"Schritt" registrieren, in dem die Message und Entitätskombination identifiziert werden, die die Ausführung des Plug-Ins auslöst, um die Postingmitteilung durchzuführen. Wenn das Plug-In durchgeführt wird, benachrichtigt es den asynchronen Service durch einen Service-Endpunktmitteilungsservice (<xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>), um den gegenwärtigen Anfragedatenkontext zu Azure Service Bus zu posten.  
  
Sie können auch Ihr eigenes benutzerdefiniertes “Azure-fähiges” Plug-In schreiben. Das benutzerdefinierte Plug-In wird im Modus der teilweisen Vertrauenswürdigkeit in der Sandbox ausgeführt. Ein benutzerdefiniertes Plug-In kann das Posten des Datenkontext zum Service-Bus durch den Service-Endpunktbenachrichtigungsservice einleiten. Das Hinzufügen von Code zum Aufrufen dieses Dienstes macht das Plug-in "Azure-fähig". 
 
Weitere allgemeine Informationen zu Plug-Ins finden Sie unter [Schreiben eines Plug-Ins](write-plug-in.md). Weitere Informationen zu Azure-fähigen Plug-Ins finden Sie unter [Schreiben eines benutzerdefinierten Azure-fähigen Plug-Ins](write-custom-azure-aware-plugin.md).  
  
### <a name="custom-workflow-activities"></a>Benutzerdefinierte Workflowaktivitäten

Ähnlich wie Plug-Ins können benutzerdefinierte Workflowaktivitäten geschrieben werden, um das Posten des aktuellen Anfragemessage-Datenkontexts zu Azure Service Bus zu schreiben, indem der Service-Endpunktbenachrichtigungservice verwendet wird. Weitere Informationen: [Workflowerweiterungen](workflow/workflow-extensions.md) 
  
### <a name="asynchronous-service"></a>Asynchroner Service

Wenn der asynchrone Service vom Service-Endpunktbenachrichtigungsservice benachrichtigt wird, behandelt er das Posten des Datenkontexts der Anfragemessage, die derzeit von der Ereignisausführungspipeline zu Azure Service Bus verarbeitet wird. Jede Veröffentlichung wird durch einen Systemauftrag des asynchronen Services ausgeführt. Ein Benutzer kann den Status der einzelnen Systemaufträge mithilfe der **Systemaufträge**-Ansicht der Power Apps-Webanwendung anzeigen.  
  
Weitere Informationen über den asynchronen Dienst finden Sie unter [Asynchroner Dienst](asynchronous-service.md).  
  
### <a name="microsoft-azure-service-bus"></a>Microsoft Azure Service Bus

Der Service-Bus verteilt den Anforderungsmeldungs-Datenkontext zwischen Common Data Service und Azure Service Bus-Lösungs-Listener-Anwendungen. Der Service-Bus bietet auch Datensicherheit, damit nur autorisierte Anwendungen auf die geposteten Dynamics 365-Daten zugreifen können.  Die Autorisierung von Common Data Service zum Veröffentlichen des Datenkontexts für den Service-Bus und für Listener-Anwendungen zum Lesen wird durch Azure Shared Access Signatures (SAS) verwaltet.  
  
  
 Weitere Informationen zum Service Bus finden Sie unter [Service Bus](https://azure.microsoft.com/services/service-bus/). Weitere Informationen zur Service Bus-Authentifizierung finden Sie unter: [Service Bus-Authentifizierung und -Autorisierung](https://azure.microsoft.com/documentation/articles/service-bus-authentication-and-authorization/).  
  
### <a name="microsoft-azure-solution"></a>Microsoft Azure-Lösung

Damit die Common Data Service- und Azure-Verbindung funktioniert, muss es mindestens eine Lösung in einem Azure Service Bus-Lösungskonto geben, bei dem die Lösung einen oder mehrere Service-Endpunkte enthält. Für einen Relayendpunktvertrag muss eine Listener-Anwendung, die "Common Data Service-fähig" ist, aktiv den Endpunkt auf die Common Data Service-Anfrage auf dem Servicebus überwachen. Für einen Warteschlangenendpunktvertrag muss ein Listener nicht aktiv überwachen. Ein Listener wird Common Data Service-fähig, wenn er mit der <xref:Microsoft.Xrm.Sdk>-Assembly verknüpft wird, sodass der Typ <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> definiert ist. Weitere Informationen: [Einen Listener für eine Microsoft Azure-Lösung schreiben](write-listener-application-azure-solution.md)  
  
Common Data Service unterstützt das Senden von Ereignisdaten an eine Azure Event Hubs-Lösung. Weitere Informationen zu Event-Hubs finden Sie unter [Arbeiten mit Event-Daten in Ihrer Azure Event Hub-Lösung](work-event-data-azure-event-hub-solution.md).  
  
<a name="bkmk_describing"></a>  
 
## <a name="common-data-service-to-service-bus-scenario"></a>Common Data Service zum Service Bus-Szenario  

Identifizieren wir nun ein Szenario, das die vorher erwähnten Verbingungskomponenten implementiert. Als Voraussetzung wurde SAS so konfiguriert, dass es Common Data Service als unterstützten Aussteller akzeptiert, und die Azure Service Bus-Lösung ist mit Regeln konfiguriert, die es Common Data Service erlauben, zu dem Endpunkt zu veröffentlichen, wo der Listener ist.  
  
Das folgende Diagramm zeigt die physischen Elemente an, die das Szenario bilden.  
  
![Ein Dynamics 365-zu-Service Bus-Szenario](media/crm-v5s-az.png "Common Data Service zum Sevicebus-Szenario")  
  
Die Ereignisreihenfolge in diesem Diagramm ist die folgende:  
  
1. Eine Listener-Anwendung ist auf einem Azure Service Bus-Lösungsendpunkt registriert und beginnt aktiv auf den Remote-Ausführungskontext von Common Data Service auf dem Service Bus zu warten.  

2. Ein Benutzer führt einen Vorgang in Common Data Service aus, der die Ausführung des registrierten OOB-Plug-Ins oder eines benutzerdefinierten Azure-fähigen Plug-Ins auslöst. Das Plug-In initiiert eine Veröffentlichung über einen asynchronen Servicesystemauftrag des aktuellen Datenkontexts zum Servicebus.  
3. Die von Common Data Service veröffentlichten Ansprüche werden authentifiziert. Der Servicebus verteilt dann den Remoteausführungskontext an den Listener. Der Listener verarbeitet die Kontextinformationen und führt einige geschäftliche Aufgaben mit diesen Informationen durch. Der Servicebus informiert den asynchronen Service über die erfolgreiche Veröffentlichung und setzt den jeweiligen Systemauftrag auf den Status "abgeschlossen".  
  
<a name="bkmk_establising"></a>  

## <a name="establish-a-contract-between-common-data-service-and-an-azure-solution"></a>Einrichten eines Vertrags zwischen Common Data Service und einer Azure-Lösung

Für jeden Lösungsendpunkt konfigurieren Sie einen Vertrag, der die Verarbeitung dieser "Nachrichten" des Remoteausführungskontexts auf dem Servicebus regelt, sowie die Sicherheit, die auf diesem Endpunkt verwendet werden soll. Servicebusnachrichten werden an einem Endpunkt mithilfe eines der hier aufgeführten unterstützten Verträge empfangen.  
  
### <a name="queue"></a>Warteschlange

Ein Warteschlangenvertrag bietet eine Nachrichtenwarteschlange in der Cloud. Mit einem Warteschlangenendpunktvertrag muss ein Listener nicht aktiv Nachrichten auf dem Endpunkt überwachen. Für Warteschlangen gibt es destruktive und nicht-destruktive Lesevorgänge. Ein destruktiver Lesevorgang liest eine verfügbare Nachricht aus der Warteschlange, wonach die Nachricht entfernt wird. Bei einem nicht-destruktiven Lesevorgang wird die Nachricht nicht aus der Warteschlange entfernt.  
  
Die Art der Warteschlange, die von Common Data Service unterstützt wird, wird persistente Warteschlange genannt. Persistente Warteschlangen bieten eine lange aber begrenzte Nachrichtenverfügbarkeit als per Code angegeben werden kann.  
  
### <a name="one-way"></a>Unidirektional

Ein unidirektionaler Vertrag benötigt einen aktiven Listener. Wenn es keinen aktiven Listener auf einem Endpunkt gibt, schlägt das Posten zum Service-Bus fehl. Common Data Service versucht in exponentiell immer größeren Zeitspannen zu posten, bis die asynchrone Systemaufgabe, die die Anfrage postet, schließlich abgebrochen wird und der Status wieder auf "Fehler" festgelegt wird.  
  
### <a name="two-way"></a>Bidirektional

Ein bidirektionaler Vertrag ähnelt einem unidirektionalen Vertrag, außer dass ein Zeichenfolgewert vom Listener zum Plug-In oder der benutzerdefinierten Workflowaktivität zurückgegeben werden kann, die den Post eingeleitet haben.  
  
### <a name="rest"></a>REST

Ein REST-Vertrag ist einem bidirektionalen Vertrag auf einem REST-Endpunkt ähnlich.  
  
### <a name="topic"></a>Thema

Ähnlich wie eine Warteschlange, mit dem Unterschied, dass ein oder mehrere Listener den Empfang von Nachrichten von dem Thema abonnieren können.  
  
### <a name="event-hub"></a>-Ereignishub

Diese Vertragsart gilt für Azure Event Hub-Lösungen.  
  
> [!IMPORTANT]
>  Um diese Verträge nutzen zu können, müssen Sie Ihre Listener-Anwendungen mit dem [Azure SDK](https://www.windowsazure.com/develop/downloads/) v1.7 oder höher schreiben.  
  
Die Identifikation der Sicherheit, die ein Vertrag verwendet, ist Teil seiner Konfiguration. Ein Vertrag kann die Transportsicherheit verwenden, die Transport Layer Security (TLS) oder Secure Sockets Layer (SSL) (HTTPS) verwendet.  
  
Die Anspruchsauthentifizierung wird für den sicheren Zugriff auf den Servicebus verwendet. Der zur Authentifizierung des Servicebusses verwendete Anspruch wird in Common Data Service generiert und vom AppFabricIssuer-Zertifikat signiert, das in der Common Data Service-Konfigurationsdatenbank angegeben ist.  
  
<a name="bkmk_management"></a>

## <a name="manage-run-time-errors"></a>Verwaltung von Laufzeitfehlern  

Wenn ein Fehler aufgetreten ist, nachdem ein Beitrag in den Servicebus versucht wurde, überprüfen Sie den Status des zugehörigen Systemauftrags in der Webanwendung, um weitere Informationen über den Fehler zu erhalten. Wenn der Servicebus ausgefallen ist oder kein Listener/Endpunkt/ein verfügbar ist, wird die aktuelle Meldung, die in Common Data Service verarbeitet wird, nicht zum Bus veröffentlicht. Der asynchrone Service versucht weiterhin, die Nachricht in einem exponenziellen Muster zu veröffentlichen, wobei er versucht, die Veröffentlichung erst oft und dann in länger werdenden Intervallen durchzuführen. Bei einem internen Common Data Service-Fehler werden keine Nachrichtenveröffentlichungen versucht. Bei einem externen Servicebus- oder Netzwerkfehler befindet sich der jeweilige Systemauftrag in einem "Wartezustand".
---
title: Azure Integration (Common Data Service for Apps) | Microsoft Docs
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="azure-integration"></a>Azure-Integration

Der Common Data Service (CDS) für Apps unterstützt die Integration mit Azure. Entwickler können Plug-Ins bei CDS for Apps registrieren, die Laufzeit-Nachrichtendaten, den so genannten Ausführungskontext, an eine oder mehrere Azure-Lösungen in der Cloud weitergeben können. Dies ist besonders wichtig, da Azure eine von zwei unterstützten Lösungen für die Kommunikation von Laufzeitkontexten ist, die in einem Plug-in an externe Geschäftsanwendungen (LOB, Line-of-Business) geliefert werden. Die andere Lösung ist die externe Kunden-Endpunkt-Zugriffskapazität von einem Plug-In, das im Sandkasten angemeldet ist.

Der Azure Service Bus bietet einen sicheren und zuverlässigen Kommunikationskanal zwischen CDS für Apps Laufzeitdaten und externen Cloud-basierten Line-of-Business (LOB)-Anwendungen. Diese Funktion ist besonders nützlich, um unterschiedliche CDS for Apps-Systeme oder andere CDS for Apps-Server mit Geschäftsdatenänderungen zu synchronisieren.

## <a name="key-elements-of-the-connection"></a>Schlüsselelemente der Verbindung  

 Die Schlüsselelemente, die die Verbindung zwischen CDS for Apps und dem Azure Service Bus realisieren, werden später beschrieben. Ein Diagramm im nächsten Abschnitt zeigt diese Elemente in Betrieb.  
  
 ### <a name="data-context"></a>Datenkontext 

 Der *Datenkontext* enthält die Geschäftsdaten, die als Teil der gegenwärtigen -CDS for Apps-Operation verarbeitet werden. Diese Verarbeitung wurde initiiert, als eine Anfrage von einem Benutzer, Workflow oder einer Anwendung zur Durchführung eine bestimmte Operation an die Dynamics 365-Plattform gestellt wurde. Der Datenkontext wird allen Plug-Ins oder benutzerdefinierten Workflow-Aktivitäten weitergeleitet, die für die Ereignis-Pipeline registriert wurden, um bei der spezifischen Anfragen- und Entitätskombination, die derzeit verarbeitet wird, ausgeführt zu werden. Der Datenkontext ist vom Typ <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>, wenn er entlang der Ereignisausführungspipeline weitergeleitet wird und <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> wenn er zum Service-Bus bekannt übergeben wird.  
  
 Der Datenkontext, der in der Message enthalten ist, die zu Azure Service Bus übergeben wird, kann zusätzlich zum binären Standard-.NET Format in XML oder JSON formatiert werden. Dies ermöglicht plattformübergreifende Interoperabilität, bei der mit Azure gehostete nicht-.NET-Clients CDS for Apps-Daten vom Service-Bus lesen können. 

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
 Plug-Ins sind eine von zwei Methoden, die angewendet werden, um die Message zu posten, die den Datenkontext zu Azure Service Bus enthält. Die andere Methode ist eine benutzerdefinierte Workflowaktivität. Es gibt zwei Typen von Plug-Ins, die durch die Dynamics 365-Azure-Verbindungsfunktion unterstützt werden: Benutzerdefinierte und vordefinierte (OOB). In beiden Fällen wird es empfohlen, dass Sie die Plug-Ins registrieren, damit sie für beste Systemleistung asynchron ausgeführt werden.  
  
 Ein Azure-fähiges OOB-Plug-In wird mit CDS for Apps bereitgestellt und kann unter Verwendung des Plug-In-Registrierungstools im CDS-Download registriert werden. Dieses Plug-in wird in vollem Vertrauen auf die CDS for Apps-Plattform ausgeführt. Sie müssen in der Ereignisausführungspipeline einen Plug-In-"Schritt" registrieren, in dem die Message und Entitätskombination identifiziert werden, die die Ausführung des Plug-Ins auslöst, um die Postingmitteilung durchzuführen. Wenn das Plug-In durchgeführt wird, benachrichtigt es den asynchronen Service durch einen Service-Endpunktmitteilungsservice (<xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>), um den gegenwärtigen Anfragedatenkontext zu Azure Service Bus zu posten.  
  
 Sie können auch Ihr eigenes benutzerdefiniertes “Azure-fähiges” Plug-In schreiben. Das benutzerdefinierte Plug-In wird im Modus der teilweisen Vertrauenswürdigkeit in der Sandbox ausgeführt. Ein benutzerdefiniertes Plug-In kann das Posten des Datenkontext zum Service-Bus durch den Service-Endpunktbenachrichtigungsservice einleiten. Das Hinzufügen von Code zum Aufrufen dieses Dienstes macht das Plug-in "Azure-fähig". 
 
 Weitere allgemeine Informationen zu Plug-Ins finden Sie unter [Schreiben eines Plug-Ins](write-plug-in.md). Weitere Informationen zu Azure-fähigen Plug-Ins finden Sie unter [Schreiben eines benutzerdefinierten Azure-fähigen Plug-Ins](write-custom-azure-aware-plugin.md).  
  
 ### <a name="custom-workflow-activities"></a>Benutzerdefinierte Workflowaktivitäten  
 Ähnlich wie Plug-Ins können benutzerdefinierte Workflowaktivitäten geschrieben werden, um das Posten des aktuellen Anfragemessage-Datenkontexts zu Azure Service Bus zu schreiben, indem der Service-Endpunktbenachrichtigungservice verwendet wird. Weitere Informationen: [Workflowerweiterungen](workflow/workflow-extensions.md) 
  
 ### <a name="asynchronous-service"></a>Asynchroner Service  
 Wenn der asynchrone Service vom Service-Endpunktbenachrichtigungsservice benachrichtigt wird, behandelt er das Posten des Datenkontexts der Anfragemessage, die derzeit von der Ereignisausführungspipeline zu Azure Service Bus verarbeitet wird. Jede Veröffentlichung wird durch einen Systemauftrag des asynchronen Services ausgeführt. Ein Benutzer kann den Status der einzelnen Systemaufträge mithilfe der **Systemaufträge**-Ansicht der PowerApps-Webanwendung anzeigen.  
  
 Weitere Informationen über den asynchronen Dienst finden Sie unter [Asynchroner Dienst](asynchronous-service.md).  
  
 ### <a name="microsoft-azure-service-bus"></a>Microsoft Azure Service Bus  
 Der Service-Bus verteilt den Anfragemessage-Datenkontext zwischen CDS for Apps und Azure Service Bus-Lösungs-Listener-Anwendungen. Der Service-Bus bietet auch Datensicherheit, damit nur autorisierte Anwendungen auf die geposteten Dynamics 365-Daten zugreifen können.  Autorisierung von CDS for Apps zum Posten des Datenkontexts zum Service-Bus und für Listener-Anwendungen zum Lesen wird entweder durch oder Azure Shared Access Signatures (SAS) verwaltet.  
  
  
 Weitere Informationen zum Service Bus finden Sie unter [Service Bus](https://azure.microsoft.com/en-us/services/service-bus/). Weitere Informationen zur Service Bus-Authentifizierung finden Sie unter: [Service Bus-Authentifizierung und -Autorisierung](https://azure.microsoft.com/en-us/documentation/articles/service-bus-authentication-and-authorization/).  
  
 ### <a name="microsoft-azure-solution"></a>Microsoft Azure-Lösung

 Damit das CDS for Apps und die Azure-Verbindung funktionieren, muss es mindestens eine Lösung in einem Azure Service Bus-Lösungskonto geben, bei dem die Lösung einen oder mehrere Service-Endpunkte enthält. Für einen Relayendpunktvertrag muss eine Listener-Anwendung, die "CDS for Apps-fähig" ist, aktiv den Endpunkt auf die CDS for Apps-Anfrage auf dem Servicebus überwachen. Für einen Warteschlangenendpunktvertrag muss ein Listener nicht aktiv überwachen. Ein Listener wird "CDS for Apps-fähig", wenn er mit dem <xref:Microsoft.Xrm.Sdk>-Assembly verknüpft wird, damit der Typ <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext> definiert ist. Weitere Informationen finden Sie unter [Listener für eine Microsoft Azure-Lösung schreiben](write-listener-application-azure-solution.md).  
  
 CDS for Apps unterstützt das Senden von Ereignisdaten eine Azure Event Hubs-Lösung. Weitere Informationen zu Event-Hubs finden Sie unter [Arbeiten mit Event-Daten in Ihrer Azure Event Hub-Lösung](work-event-data-azure-event-hub-solution.md).  
  
<a name="bkmk_describing"></a>  
 
## <a name="cds-for-apps-to-service-bus-scenario"></a>CDS für Apps zum Service Bus Szenario  

 Identifizieren wir nun ein Szenario, das die vorher erwähnten Verbingungskomponenten implementiert. Als Voraussetzung wurde SAS konfiguriert, um CDS for Apps als unterstützten Aussteller zu erkennen und die Azure Service Bus-Lösung mit Regeln konfiguriert, die es CDS for Apps ermöglichen, an den Endpunkt zu posten, an dem sich der Listener befindet.  
  
 Das folgende Diagramm zeigt die physischen Elemente an, die das Szenario bilden.  
  
 ![Dynamics 365-zu-Service Bus-Szenario](media/crm-v5s-az.png "CDS for Apps-zu-Service Bus-Szenario")  
  
 Die Ereignisreihenfolge in diesem Diagramm ist die folgende:  
  
1. Eine Listener-Anwendung ist auf einem Azure Service Bus-Lösungsendpunkt registriert und beginnt aktiv auf den Remote-Ausführungskontext von CDS for Apps auf dem Service Bus zu warten.  

2. Ein Benutzer führt in CDS for Apps einen Vorgang aus, der die Ausführung des registrierten OOB-Plugins oder eines benutzerdefinierten Azure-fähigen Plugins auslöst. Das Plug-In initiiert eine Veröffentlichung über einen asynchronen Servicesystemauftrag des aktuellen Datenkontexts zum Servicebus.  
  
3. Die von CDS for Apps geposteten Forderungen werden authentifiziert. Der Servicebus verteilt dann den Remoteausführungskontext an den Listener. Der Listener verarbeitet die Kontextinformationen und führt einige geschäftliche Aufgaben mit diesen Informationen durch. Der Servicebus informiert den asynchronen Service über die erfolgreiche Veröffentlichung und setzt den jeweiligen Systemauftrag auf den Status "abgeschlossen".  
  
<a name="bkmk_establising"></a>  
 
## <a name="establish-a-contract-between-cds-for-apps-and-an-azure-solution"></a>Einen Vertrag zwischen CDS for Apps und einer Azure-Lösung abschließen.  
 Für jeden Lösungsendpunkt konfigurieren Sie einen Vertrag, der die Verarbeitung dieser "Nachrichten" des Remoteausführungskontexts auf dem Servicebus regelt, sowie die Sicherheit, die auf diesem Endpunkt verwendet werden soll. Servicebusnachrichten werden an einem Endpunkt mithilfe eines der hier aufgeführten unterstützten Verträge empfangen.  
  
 **Warteschlange**  
 Ein Warteschlangenvertrag bietet eine Nachrichtenwarteschlange in der Cloud. Mit einem Warteschlangenendpunktvertrag muss ein Listener nicht aktiv Nachrichten auf dem Endpunkt überwachen. Für Warteschlangen gibt es destruktive und nicht-destruktive Lesevorgänge. Ein destruktiver Lesevorgang liest eine verfügbare Nachricht aus der Warteschlange, wonach die Nachricht entfernt wird. Bei einem nicht-destruktiven Lesevorgang wird die Nachricht nicht aus der Warteschlange entfernt.  
  
 Der Typ der von CDS for Apps unterstützten Warteschlange wird als persistente Warteschlange bezeichnet. Persistente Warteschlangen bieten eine lange aber begrenzte Nachrichtenverfügbarkeit als per Code angegeben werden kann.  
  
 **Unidirektional**  
 Ein unidirektionaler Vertrag benötigt einen aktiven Listener. Wenn es keinen aktiven Listener auf einem Endpunkt gibt, schlägt das Posten zum Service-Bus fehl. CDS for Apps wird den Beitrag in exponentiell immer größeren Zeitspannen erneut versuchen, bis der asynchrone Systemauftrag, der die Anfrage veröffentlicht, schließlich abgebrochen wird und sein Status auf "Fehlgeschlagen" gesetzt wird.  
  
 **Bidirektional**  
 Ein bidirektionaler Vertrag ähnelt einem unidirektionalen Vertrag, außer dass ein Zeichenfolgewert vom Listener zum Plug-In oder der benutzerdefinierten Workflowaktivität zurückgegeben werden kann, die den Post eingeleitet haben.  
  
 **REST**  
 Ein REST-Vertrag ist einem bidirektionalen Vertrag auf einem REST-Endpunkt ähnlich.  
  
 **Thema**  
 Ähnlich wie eine Warteschlange, mit dem Unterschied, dass ein oder mehrere Listener den Empfang von Nachrichten von dem Thema abonnieren können.  
  
 **Event Hub**  
 Diese Vertragsart gilt für Azure Event Hub-Lösungen.  
  
> [!IMPORTANT]
>  Um diese Verträge nutzen zu können, müssen Sie Ihre Listener-Anwendungen mit dem [Azure SDK](http://www.windowsazure.com/develop/downloads/) v1.7 oder höher schreiben.  
  
 Die Identifikation der Sicherheit, die ein Vertrag verwendet, ist Teil seiner Konfiguration. Ein Vertrag kann die Transportsicherheit verwenden, die Transport Layer Security (TLS) oder Secure Sockets Layer (SSL) (HTTPS) verwendet.  
  
 Die Anspruchsauthentifizierung wird für den sicheren Zugriff auf den Servicebus verwendet. Der zur Authentifizierung des Servicebusses verwendete Anspruch wird in CDS for Apps generiert und vom AppFabricIssuer-Zertifikat signiert, das in der CDS for Apps-Konfigurationsdatenbank angegeben ist.  
  
<a name="bkmk_management"></a>

## <a name="manage-run-time-errors"></a>Verwaltung von Laufzeitfehlern  

 Wenn ein Fehler aufgetreten ist, nachdem ein Beitrag in den Servicebus versucht wurde, überprüfen Sie den Status des zugehörigen Systemauftrags in der Webanwendung, um weitere Informationen über den Fehler zu erhalten. Wenn der Servicebus ausgefallen ist oder kein Listener/Endpunkt/ein verfügbar ist, wird die aktuelle Meldung, die in CDS for Apps verarbeitet wird, nicht an den Bus weitergegeben. Der asynchrone Service versucht weiterhin, die Nachricht in einem exponenziellen Muster zu veröffentlichen, wobei er versucht, die Veröffentlichung erst oft und dann in länger werdenden Intervallen durchzuführen. Bei einem internen CDS for Apps-Fehler werden keine Nachrichtenveröffentlichungen versucht. Bei einem externen Servicebus- oder Netzwerkfehler befindet sich der jeweilige Systemauftrag in einem "Wartezustand".
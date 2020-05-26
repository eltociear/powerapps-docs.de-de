---
title: Service Protection API-Beschränkungen (Common Data Service) | Microsoft Docs
description: Verstehen Sie die Serviceschutzgrenzen für API-Anforderungen.
ms.custom: ''
ms.date: 04/20/2020
ms.reviewer: pehecke
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
ms.openlocfilehash: 9f349a913056fe2a964db537b62774eccabdc21e
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275794"
---
# <a name="service-protection-api-limits"></a>API-Grenzwerte für den Serviceschutz

Um eine konsistente Verfügbarkeit und Leistung für alle zu gewährleisten, wenden wir einige Einschränkungen für die Verwendung von APIs anwenden. Diese Einschränkungen wurden entwickelt, um zu erkennen, wenn Client-Anwendungen außergewöhnliche Anforderungen an die Server-Ressourcen stellen.

Die Beschränkungen sollten normale Benutzer interaktiver Clients nicht betreffen. Nur Client-Anwendungen, die außergewöhnliche API-Anforderungen ausführen, sollten betroffen sein. Der Grenzwert bietet einen gewissen Schutz vor dem unwillkürlichen und unerwarteten Anstieg des Anforderungsvolumens, das die Verfügbarkeit und Leistungsfähigkeit der Common Data Service Plattform gefährdet.

Wenn eine Client-Anwendung außergewöhnlich anspruchsvolle Anfragen stellt, folgt die Common Data Service dem üblichen Muster für Online-Dienste. Wir geben einen Fehler zurück, der darauf hinweist, dass zu viele Anfragen gestellt wurden.

- Mit der Web API erhalten wir einen Fehler [429 Too Many Requests](https://developer.mozilla.org/docs/Web/HTTP/Status/429).
- Mit dem Organisationsdienst erhalten Sie einen [OrganizationServiceFault](/dotnet/api/microsoft.xrm.sdk.organizationservicefault) Fehler mit einem von drei spezifischen Fehlercodes. Weitere Informationen: [Zurückgegebene Fehler zur Dienstschutz-API-Beschränkung](#service-protection-api-limit-errors-returned)


## <a name="impact-on-client-applications"></a>Auswirkungen auf Kundenanwendungen

Es liegt in der Verantwortung der Client-Anwendungen, Fehler bei der Dienstschutz-API-Limitierung zu verwalten. Die genaue Art und Weise, wie man mit diesem Fehler umgeht, hängt von der Art des Antrags ab. 

### <a name="interactive-client-applications"></a>Interaktive Client-Anwendungen

Die Dienstschutz-Grenzwerte sind so hoch, dass es selten vorkommen sollte, dass eine Person, die eine interaktive Client-Anwendung verwendet, bei normaler Nutzung auf sie stößt. Es ist jedoch möglich, wenn die Client-Anwendung Massenoperationen zulässt. Client-Anwendungsentwickler sollten sich darüber im Klaren sein, wie API-Beschränkungen für den Dienstschutz durchgesetzt werden, und die Benutzeroberfläche so gestalten, dass das Potenzial für Benutzer, extrem anspruchsvolle Anfragen an den Server zu senden, reduziert wird. Sie sollten jedoch weiterhin damit rechnen, dass Dienstschutz-API-Grenzwertfehler auftreten können, und darauf vorbereitet sein, mit ihnen umzugehen.

Client-Anwendungsentwickler sollten den Fehler nicht einfach werfen, um dem Benutzer die Meldung anzuzeigen. Die Fehlermeldung ist nicht für Endbenutzer bestimmt. Siehe [Wiederherstellungsoperationen](#retry-operations) für spezifische Strategien.

### <a name="data-integration-applications"></a>Anwendungen zur Datenintegration

Anwendungen, die zum Laden von Daten in das CDS oder zur Durchführung von Massenaktualisierungen entwickelt wurden, müssen auch in der Lage sein, Fehler bei der Dienstschutz-API-Limitierung zu verwalten. Diese Anwendungen priorisieren den Durchsatz, damit sie ihre Arbeit in kürzester Zeit abschließen können. Diese Anwendungen müssen über eine Strategie zur Wiederholung von Operationen verfügen. Es gibt mehrere Strategien, die sie anwenden können, um den maximalen Durchsatz zu erzielen. Weitere Informationen: [Wie man den Durchsatz maximiert](#how-to-maximize-throughput).

### <a name="portal-applications"></a>Portal-Anwendungen

Portalanwendungen senden in der Regel Anfragen von anonymen Benutzern über ein einziges Diensthauptkonto. Da die API-Grenzwerte für den Dienstschutz auf einer Pro-Benutzer-Basis basieren, können Portalanwendungen die API-Grenzwerte für den Dienstschutz auf der Grundlage des Verkehrsaufkommens im Portal erreichen. Wie bei interaktiven Client-Anwendungen wird nicht erwartet, dass die Dienstschutz-API Fehler für den Portal-Endbenutzer anzeigt. Es wird erwartet, dass die Benutzeroberfläche weitere Anfragen deaktivieren und eine Meldung anzeigen sollte, dass der Server ausgelastet ist. Die Meldung kann den Zeitpunkt enthalten, zu dem die Anwendung mit der Annahme neuer Anfragen beginnen kann.

## <a name="impact-on-plug-ins-and-custom-workflow-activities"></a>Auswirkungen auf Plug-ins und benutzerdefinierte Workflow-Aktivitäten

Plug-ins und benutzerdefinierte Workflow-Aktivitäten wenden Geschäftslogik an, die durch eingehende Anfragen ausgelöst wird. Serviceschutz-Limits werden nicht auf Plug-ins und benutzerdefinierte Workflow-Aktivitäten angewendet. Plug-ins und benutzerdefinierte Workflow-Aktivitäten werden hochgeladen und innerhalb des isolierten Sandbox-Dienstes ausgeführt. Common Data Service-Operationen, die über den Sandbox-Dienst aufgerufen werden, verwenden nicht die öffentlichen API-Endpunkte.

Wenn Ihre Anwendung Operationen ausführt, die benutzerdefinierte Logik auslösen, wird die Anzahl der von Plug-ins oder benutzerdefinierten Workflow-Aktivitäten gesendeten Anfragen nicht zu den API-Beschränkungen für den Dienstschutz gezählt. Die zusätzliche Berechnungszeit, die diese Operationen beisteuern, wird jedoch zu der ursprünglichen Anfrage hinzugefügt, die sie ausgelöst hat. Diese Berechnungszeit ist Teil der API-Beschränkungen für den Dienstschutz. Weitere Informationen: [Wie Dienstschutz-API-Beschränkungen durchgesetzt werden](#how-service-protection-api-limits-are-enforced)

## <a name="retry-operations"></a>Operationen wiederholen

Wenn ein Dienstschutz-API-Limit-Fehler auftritt, gibt er einen Wert an, der die Dauer angibt, bevor neue Anfragen des Benutzers bearbeitet werden können.

- Wenn ein 429-Fehler von der Web-API zurückgegeben wird, enthält die Antwort ein [Retry-After](https://developer.mozilla.org/docs/Web/HTTP/Headers/Retry-After) mit der Anzahl der Sekunden.
- Mit dem Organisationsdienst wird ein Wert [Zeitspanne](/dotnet/api/system.timespan) in der <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault> zurückgegeben.<xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails> Sammeln Sie mit dem Schlüssel `Retry-After`.

### <a name="interactive-application-re-try"></a>Interaktive Anwendung erneut versuchen 

Handelt es sich bei dem Client um eine interaktive Anwendung, sollten Sie eine Meldung anzeigen, dass der Server ausgelastet ist, während Sie die Anfrage des Benutzers erneut versuchen. Möglicherweise möchten Sie dem Benutzer die Möglichkeit geben, den Vorgang abzubrechen. Erlauben Sie Benutzern nicht, weitere Anfragen einzureichen, bis die von Ihnen gesendete vorherige Anfrage abgeschlossen ist.

### <a name="non-interactive-application-re-try"></a>Nicht-interaktive Anwendung erneut versuchen

Wenn es sich bei dem Client nicht um eine interaktive Anwendung handelt, ist es üblich, einfach abzuwarten, bis die Dauer abgelaufen ist, bevor die Anfrage erneut gesendet wird. Dies geschieht üblicherweise durch Pausieren der Ausführung des aktuellen Threads mit [Thread.sleep](/dotnet/api/system.threading.thread.sleep) oder gleichwertigen Methoden.



## <a name="how-service-protection-api-limits-are-enforced"></a>Wie werden die Grenzen der Service Protection API durchgesetzt?

Die API-Limits für den Dienstschutz werden innerhalb eines gleitenden Fensters von 5 Minuten (300 Sekunden) ausgewertet. Wenn eines der Limits innerhalb der vorhergehenden 300 Sekunden überschritten wird, wird bei nachfolgenden Anforderungen zum Schutz des Dienstes bis zum Ende der Dauer von "Retry-After" ein Fehler "Service Protection API Limit" zurückgegeben.

Die API-Limits für den Dienstschutz werden pro Benutzer ausgewertet. Jeder authentifizierte Benutzer ist unabhängig begrenzt. Nur die Benutzerkonten, die außergewöhnliche Anforderungen stellen, werden eingeschränkt. Andere Benutzer sind davon nicht betroffen.

Die API-Beschränkungen für den Dienstschutz werden auf der Grundlage von drei Aspekten durchgesetzt:

- Die Anzahl der Anfragen, die von einem Benutzer gesendet wurden.
- Die kombinierte Ausführungszeit wurde benötigt, um von einem Benutzer gesendete Anfragen zu bearbeiten.
- Die Anzahl der von einem Benutzer gesendeten gleichzeitigen Anfragen.

Wenn die einzige Beschränkung in der Anzahl der von einem Benutzer gesendeten Anfragen bestünde, wäre es möglich, diese zu umgehen. Der anderen Aspekte wurden hinzugefügt, um diesen Versuchen entgegenzuwirken. Beispiel:

- Sie könnten weniger Anfragen senden, indem Sie sie in Batch-Operationen bündeln.
  - Die kombinierte Ausführungszeitbegrenzung wirkt dem entgegen.
- Anstatt Anfragen einzeln nacheinander zu senden, könnten Sie eine große Anzahl gleichzeitiger Anfragen innerhalb des 5-minütigen Schiebefensters senden, bevor die API-Beschränkungen für den Dienstschutz durchgesetzt werden.
  - Die Begrenzung gleichzeitiger Anfragen wirkt dem entgegen.

Jeder in Ihrer Umgebung verfügbare Webserver setzt diese Beschränkungen unabhängig voneinander durch. Die meisten Umgebungen werden mehr als einen Webserver haben. Testumgebungen wird nur ein einziger Webserver zugewiesen. Die tatsächliche Anzahl der Webserver, die Ihrer Umgebung zur Verfügung stehen, hängt von mehreren Faktoren ab, die Teil des von uns angebotenen verwalteten Dienstes sind. Einer der Faktoren ist, wie viele Benutzerlizenzen Sie erworben haben.

Die folgende Tabelle beschreibt die standardmäßigen Dienstschutz-API-Limits, die *pro Webserver* innerhalb des 5-minütigen Schiebefensters durchgesetzt werden.

|Kennzahl|Beschreibung|Limit pro Webserver|
|--|--|--|
|Anzahl von Anforderungen|Die kumulative Anzahl der vom Benutzer gestellten Anfragen.|6000|
|Ausführungszeit|Die kombinierte Ausführungszeit aller vom Benutzer gestellten Anfragen.| 20 Minuten (1200 Sekunden)|
|Anzahl gleichzeitiger Anfragen|Die Anzahl der gleichzeitigen Anfragen des Benutzers|52|

> [!IMPORTANT]
> Diese Grenzwerte können sich ändern und zwischen verschiedenen Umgebungen variieren. Diese Zahlen stellen Standardwerte dar und sollen Ihnen eine Vorstellung davon vermitteln, welche Werte Sie erwarten können.

### <a name="the-retry-after-duration"></a>Die Dauer der Wiederholung nach dem Löschen

Die Dauer der `Retry-After` hängt von der Art der Vorgänge ab, die in den vorangegangenen 5 Minuten gesendet wurden. Je anspruchsvoller die Anfragen sind, desto länger dauert die Wiederherstellung des Servers.

Heute können Sie aufgrund der Art und Weise, wie die Limits ausgewertet werden, davon ausgehen, dass die Anzahl der Anfragen und Ausführungszeitlimits für einen Zeitraum von 5 Minuten überschritten werden, bevor die API-Limits für den Dienstschutz in Kraft treten. Das Überschreiten der Anzahl gleichzeitiger Anfragen führt jedoch sofort zu einem Fehler. Wenn die Anwendung weiterhin solche anspruchsvollen Anfragen sendet, wird die Dauer verlängert, um die Auswirkungen auf die gemeinsamen Ressourcen zu minimieren. Dies führt dazu, dass der individuelle Wiederholungszeitraum nach der Dauer länger ist, was bedeutet, dass Ihre Anwendung längere Zeiträume der Inaktivität sieht, während sie wartet. Dieses Verhalten kann sich in Zukunft ändern.

Wenn möglich, empfehlen wir, zu versuchen, eine konsistente Rate zu erreichen, indem Sie mit einer geringeren Anzahl von Anfragen beginnen und diese allmählich erhöhen, bis Sie beginnen, die Grenzen der API für den Dienstschutz zu erreichen. Lassen Sie sich danach vom Server mitteilen, wie viele Anfragen er innerhalb von 5 Minuten bearbeiten kann. Wenn Sie die maximale Anzahl von Anfragen innerhalb dieses 5-Minuten-Zeitraums begrenzen und die Anzahl der Anfragen allmählich erhöhen, wird die Wiederholungsdauer nach dem Versuch gering gehalten, wodurch der Gesamtdurchsatz optimiert und Server-Ressourcen-Spitzen minimiert werden.

## <a name="service-protection-api-limit-errors-returned"></a>Zurückgegebene Dienstschutz-API-Begrenzungsfehler

Dieser Abschnitt beschreibt die drei Arten von API-Grenzwertfehlern für den Dienstschutz, die zurückgegeben werden können, sowie die Faktoren, die diese Fehler verursachen, und mögliche Abhilfestrategien.

- Die Seite **Fehlercode** ist der numerische Fehlerwert, der vom Organisationsdienst <xref:Microsoft.Xrm.Sdk.OrganizationServiceFault> zurückgegeben wird. <xref:Microsoft.Xrm.Sdk.BaseServiceFault.ErrorDetails>.
- Die Seite **Hex-Code** ist der hexadezimale Fehlerwert, der von der Web API zurückgegeben wird.

### <a name="number-of-requests"></a>Anzahl von Anforderungen

Dieses Limit zählt die Gesamtzahl der Anfragen während des vorangegangenen Zeitraums von 300 Sekunden.

| Fehlercode | Hex-Code | Nachricht |
|------------|------------|-------------------------------------|
|`-2147015902`|`0x80072322`|`Number of requests exceeded the limit of 6000 over time window of 300 seconds.`|

Es wird nicht erwartet, dass ein typischer Benutzer einer interaktiven Anwendung in der Lage sein wird, 1.200 Anfragen pro Minute zu senden, um dieses Limit zu überschreiten, es sei denn, die Anwendung ermöglicht es Benutzern, Massenoperationen durchzuführen.

Wenn eine Listenansicht z.B. die Auswahl von 250 Datensätzen auf einmal ermöglicht und einem Benutzer erlaubt, eine Operation an all diesen Datensätzen durchzuführen, müsste der Benutzer diese Operation 24 Mal in einer Zeitspanne von 300 Sekunden durchführen. Der Benutzer müsste den Vorgang auf jeder Liste innerhalb von 12,5 Sekunden abschließen.

Wenn Ihre Anwendung diese Möglichkeit bietet, sollten Sie einige der folgenden Strategien in Betracht ziehen:

- Verringern der Gesamtzahl der Datensätze, die in einer Liste ausgewählt werden können. Wenn die Anzahl der in einer Liste angezeigten Elemente auf 50 reduziert wird, müsste der Benutzer diesen Vorgang innerhalb von 300 Sekunden 120 Mal durchführen. Der Benutzer müsste den Vorgang auf jeder Liste innerhalb von 2,5 Sekunden abschließen.
- Kombinieren Sie die ausgewählten Vorgänge zu einem Stapel. Ein Batch kann bis zu 1000 Operationen enthalten und vermeidet die Begrenzung der Anzahl von Anfragen. Sie müssen jedoch auf die Ausführungsfrist vorbereitet sein.

### <a name="execution-time"></a>Ausführungszeit

Diese Grenze verfolgt die kombinierte Ausführungszeit der eingehenden Anfragen während der vorangegangenen 300-Sekunden-Periode.

| Fehlercode | Hex-Code | Nachricht |
|------------|------------|-------------------------------------|
|`-2147015903`|`0x80072321`|`Combined execution time of incoming requests exceeded limit of 1,200,000  milliseconds over time window of 300 seconds. Decrease number of concurrent requests or reduce the duration of requests and try again later.`|

Einige Operationen erfordern mehr Ressourcen als andere. Batch-Operationen, das Importieren von Lösungen und hochkomplexe Abfragen können sehr anspruchsvoll sein. Diese Vorgänge können bei gleichzeitigen Anfragen auch gleichzeitig durchgeführt werden. Daher ist es möglich, innerhalb des 5-Minuten-Fensters Operationen anzufordern, die zusammen mehr als 20 Minuten Rechenzeit erfordern.

Diese Beschränkung kann auftreten, wenn Strategien mit Batch-Operationen und gleichzeitigen Anfragen verwendet werden, um die Begrenzung der Anzahl der Anfragen zu vermeiden.

### <a name="concurrent-requests"></a>Gleichzeitige Anfragen

Dieses Limit verfolgt die Gesamtzahl der gleichzeitigen Anfragen während des vorangegangenen Zeitraums von 300 Sekunden.

| Fehlercode | Hex-Code | Nachricht |
|------------|------------|-------------------------------------|
|`-2147015898`|`0x80072326`|`Number of concurrent requests exceeded the limit of 52.`|

Client-Anwendungen sind nicht darauf beschränkt, Anfragen einzeln nacheinander zu senden. Der Client kann parallele Programmiermuster oder verschiedene Methoden anwenden, um mehrere Anträge gleichzeitig zu senden. Der Server kann erkennen, wenn er auf mehrere Anfragen desselben Benutzers gleichzeitig antwortet. Wenn diese Anzahl gleichzeitiger Anfragen überschritten wird, wird dieser Fehler ausgelöst.

Das gleichzeitige Senden von Anfragen kann ein wichtiger Teil einer Strategie zur Maximierung des Durchsatzes sein, aber es ist wichtig, dies unter Kontrolle zu halten.

Bei Verwendung von [Parallele Programmierung in .NET](/dotnet/standard/parallel-programming/) hängt der Standardgrad der Parallelität von der Anzahl der CPU-Kerne auf dem Server ab, auf dem der Code ausgeführt wird. Sie sollte 52 nicht überschreiten. Die Eigenschaft [ParallelOptions.MaxDegreeOfParallelism](/dotnet/api/system.threading.tasks.paralleloptions.maxdegreeofparallelism) kann eingestellt werden, um eine maximale Anzahl gleichzeitiger Aufgaben zu definieren.

## <a name="how-to-maximize-throughput"></a>Wie Sie den Durchsatz maximieren

Wenn Sie eine Anwendung haben, die den Durchsatz priorisieren muss, um die meisten Daten in kürzester Zeit zu bewegen, gibt es einige Strategien, die Sie anwenden können.

### <a name="let-the-server-tell-you-how-much-it-can-handle"></a>Lassen Sie sich vom Server mitteilen, wie viel er verkraften kann

Versuchen Sie nicht zu berechnen, wie viele Anfragen gleichzeitig zu senden sind. Jede Umgebung kann unterschiedlich sein. Erhöhen Sie allmählich die Rate, mit der Sie Anfragen senden, bis Sie beginnen, die Limits zu erreichen, und hängen Sie dann vom Wert für das API-Limit `Retry-After` des Dienstschutzes ab, um Ihnen mitzuteilen, wann Sie weitere Anfragen senden müssen. Dieser Wert hält Ihren Gesamtdurchsatz auf dem höchstmöglichen Niveau.

### <a name="use-multiple-threads"></a>Verwenden von Multi-Threads

Die höhere Begrenzung der Anzahl gleichzeitiger Threads ist etwas, mit dem Ihre Anwendung eine deutliche Leistungsverbesserung erzielen kann. Dies trifft zu, wenn Ihre einzelnen Operationen relativ schnell ablaufen. Je nach Art der Daten, die Sie verarbeiten, müssen Sie möglicherweise die Anzahl der Threads anpassen, um einen optimalen Durchsatz zu erzielen.

Weitere Informationen:

- [Task Parallel Library mit Web API verwenden](#use-task-parallel-library-with-web-api)
- [Task Parallel Library mit CrmServiceClient verwenden](#use-task-parallel-library-with-crmserviceclient)

### <a name="avoid-batching"></a>Batching vermeiden

Im Organisationsdienst war die herkömmliche Vorgehensweise, <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> zu verwenden, um mehrere Operationen zu bündeln. Der Hauptvorteil besteht darin, dass dadurch die Gesamtmenge der SOAP-XML-Payload, die über die Leitung gesendet werden muss, reduziert wird. Dies bietet einen gewissen Leistungsvorteil, wenn Netzwerklatenz ein Problem ist.

In der Vergangenheit waren die ExecuteMultiple-Operationen aufgrund der möglichen Auswirkungen auf die Leistung auf jeweils nur zwei beschränkt. Dies ist nicht mehr der Fall, da die API-Beschränkungen für den Dienstschutz diese Beschränkung überflüssig gemacht haben.

In den meisten Szenarien werden einzelne Anfragen am schnellsten und mit einem hohen Grad an Parallelität gesendet. Wenn Sie der Meinung sind, dass die Batch-Größe die Leistung verbessern könnte, ist es am besten, mit einer kleinen Batch-Größe von 10 zu beginnen und die Gleichzeitigkeit zu erhöhen, bis Sie beginnen, Fehler bei der Dienstschutz-API-Limitierung zu erhalten, die Sie erneut versuchen werden.

Bei Verwendung der Web API bedeutet der kleinere JSON-Payload, die für einzelne Anfragen über das Kabel gesendet wird, dass die Netzwerklatenz kein Problem darstellt. Der Gesamtbetrag der Payload, der mit $batch gesendet wird, ist größer als das Senden von Einzelanfragen. Verwenden Sie $batch nur, wenn Sie Transaktionen mit Changesets verwalten möchten. Weitere Informationen: [Ausführen von Batch-Operationen mit der Web-API](webapi/execute-batch-operations-using-web-api.md)

> [!NOTE]
> Batch-Operationen sind keine gültige Strategie zur Umgehung der Berechtigungsgrenzen. Dienstschutz-API-Limits und Berechtigungslimits werden separat ausgewertet. Berechtigungsbeschränkungen basieren auf CRUD-Operationen und fallen unabhängig davon an, ob sie in einer Stapelverarbeitung enthalten sind oder nicht. Weitere Informationen: [Berechtigungsgrenzen](../../maker/common-data-service/api-limits-overview.md#entitlement-limits)

### <a name="remove-the-affinity-cookie"></a>Entfernen Sie das Affinitäts-Cookie

Wenn Sie eine Verbindung zu einem Dienst in Azure herstellen, wird ein Cookie mit der Antwort zurückgegeben, und alle Ihre nachfolgenden Anfragen werden versuchen, an denselben Server weitergeleitet zu werden, es sei denn, die Kapazitätsverwaltung erzwingt einen Wechsel zu einem anderen Server. Wenn Sie dieses Cookie entfernen, wird jede von Ihnen gesendete Anfrage an einen der in Frage kommenden Server weitergeleitet. Dies erhöht den Durchsatz, da pro Server Beschränkungen gelten. Dadurch können Sie einfach mehr Server verwenden, falls diese verfügbar sind.

> [!NOTE]
> Diese Strategie sollte nur von Anwendungen verwendet werden, die eine Optimierung des Durchsatzes anstreben. Interaktive Client-Anwendungen profitieren von dem Affinitäts-Cookie, da es die Wiederverwendung von zwischengespeicherten Daten ermöglicht, die sonst neu erstellt werden müssten, was zu einer schlechteren Leistung führen würde.

Der folgende Code zeigt, wie Cookies bei der Initialisierung eines HttpClients mit der Web API deaktiviert werden können, vorausgesetzt, Sie verwenden einen benutzerdefinierten HttpMessageHandler zur Verwaltung der Authentifizierung. Weitere Informationen: [Beispiel zur Demonstration eines DelegatingHandlers](authenticate-oauth.md#example-demonstrating-a-delegatinghandler)

```csharp
HttpMessageHandler messageHandler = new OAuthMessageHandler(
    config,
    new HttpClientHandler() { UseCookies = false }
    );
HttpClient httpClient = new HttpClient(messageHandler)
```

Wenn Sie CrmServiceClient verwenden, fügen Sie Folgendes zum Knoten AppSettings in der Datei App.config hinzu:

```xml
<add key="PreferConnectionAffinity" value="false" /> 
```

### <a name="optimize-your-connection"></a>Optimieren Sie Ihre Verbindung

Sie können einen höheren Durchsatz erwarten, indem Sie die Verbindung optimieren. Unterstützender .NET-Beispielcode verwendet diese Einstellungen:

```csharp
//Change max connections from .NET to a remote service default: 2
System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
//Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4 
System.Threading.ThreadPool.SetMinThreads(100, 100);
//Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server 
System.Net.ServicePointManager.Expect100Continue = false;
//Can decreas overall transmission overhead but can cause delay in data packet arrival
System.Net.ServicePointManager.UseNagleAlgorithm = false;
```
Weitere Informationen: [Verwaltete Verbindungen](/dotnet/framework/network-programming/managing-connections)

## <a name="strategies-to-manage-service-protection-api-limits"></a>Strategien zur Verwaltung der Grenzen der Service Protection API

In diesem Abschnitt wird beschrieben, wie Sie Ihre Clients und Systeme so gestalten können, dass Dienstschutz-API-Limit-Fehler vermieden werden. Vielleicht möchten Sie auch überlegen, wie Sie Ihre Lizenzen verwalten, um die Auswirkungen zu verringern.

### <a name="update-your-client-application"></a>Aktualisieren Sie Ihre Client-Anwendung

API-Beschränkungen für den Dienstschutz werden seit 2018 auf CDS angewandt, aber es gibt viele Client-Anwendungen, die vor diesen Beschränkungen geschrieben wurden. Diese Clients haben diese Fehler nicht erwartet und können die Fehler nicht richtig handhaben. Sie sollten diese Anwendungen aktualisieren und die Muster anwenden, die in den nachstehenden Abschnitten [Benutzung des Organisationsdienstes](#using-the-organization-service) oder [Benutzung der Web API](#using-the-web-api) beschrieben sind.

### <a name="move-towards-real-time-integration"></a>Auf dem Weg zur Echtzeit-Integration

Denken Sie daran, dass der Hauptpunkt der API-Beschränkungen für den Schutz von Diensten darin besteht, die Auswirkungen sehr anspruchsvoller Anfragen zu mildern, die über einen kurzen Zeitraum auftreten. Wenn Ihre aktuellen Geschäftsprozesse von großen periodischen nächtlichen, wöchentlichen oder monatlichen Aufträgen abhängen, die versuchen, große Datenmengen in kurzer Zeit zu verarbeiten, überlegen Sie, wie Sie eine Echtzeit-Datenintegrationsstrategie ermöglichen könnten. Wenn Sie auf Prozesse verzichten können, die sehr anspruchsvolle Operationen erfordern, können Sie die Auswirkungen reduzieren, die die Grenzen des Dienstschutzes haben werden.

## <a name="using-the-web-api"></a>Verwenden der Web-API

Wenn Sie die Web API mit einer Client-Bibliothek verwenden, kann es sein, dass sie das für 429 Fehler erwartete Wiederholungsverhalten unterstützt. Wenden Sie sich an den Herausgeber der Kundenbibliothek.

Wenn Sie Ihre eigene Bibliothek geschrieben haben, können Sie Verhaltensweisen einschließen, die denen in diesem Beispielcode für einen Helper [Web API CDSWebApiService-Klasse Beispiel (C#)](webapi/samples/cdswebapiservice.md) ähnlich sind.

```csharp
private async Task<HttpResponseMessage> SendAsync(
    HttpRequestMessage request,
    HttpCompletionOption httpCompletionOption = HttpCompletionOption.ResponseHeadersRead,
    int retryCount = 0)
{
    HttpResponseMessage response;
    try
    {
        //The request is cloned so it can be sent again.
        response = await httpClient.SendAsync(request.Clone(), httpCompletionOption);
    }
    catch (Exception)
    {
        throw;
    }

    if (!response.IsSuccessStatusCode)
    {
        if ((int)response.StatusCode != 429)
        {
            //Not a service protection limit error
            throw ParseError(response);
        }
        else
        {
            // Give up re-trying if exceeding the maxRetries
            if (++retryCount >= config.MaxRetries)
            {
                throw ParseError(response);
            }

            int seconds;
            //Try to use the Retry-After header value if it is returned.
            if (response.Headers.Contains("Retry-After"))
            {
                seconds = int.Parse(response.Headers.GetValues("Retry-After").FirstOrDefault());
            }
            else
            {
                //Otherwise, use an exponential backoff strategy
                seconds = (int)Math.Pow(2, retryCount);
            }
            Thread.Sleep(TimeSpan.FromSeconds(seconds));

            return await SendAsync(request, httpCompletionOption, retryCount);
        }
    }
    else
    {
        return response;
    }
}
```

Vielleicht möchten Sie auch [Polly](https://github.com/App-vNext/Polly) verwenden, eine .NET-Bibliothek für Ausfallsicherheit und Behandlung transienter Fehler, die es Entwicklern ermöglicht, Richtlinien wie Retry, Circuit Breaker, Timeout, Bulkhead Isolation und Fallback in einer flüssigen und thread-sicheren Weise auszudrücken.

### <a name="http-response-headers"></a>HTTP-Antwort-Header

Wenn Sie HTTP-Anforderungen mit der Web-API verwenden, können Sie die verbleibenden Grenzwerte mit den folgenden HTTP Header verfolgen:

|Kopfzeile  |Wertbeschreibung  |
|---------|---------|
|`x-ms-ratelimit-burst-remaining-xrm-requests`|Die verbleibende Anzahl von Anforderungen für diese Verbindung|
|`x-ms-ratelimit-time-remaining-xrm-requests`|Die kombinierte verbleibende Dauer für alle Verbindungen, die dasselbe Benutzerkonto verwenden|

Sie sollten sich nicht auf diese Werte verlassen, um zu kontrollieren, wie viele Anfragen Sie senden. Sie sind für Debugging-Zwecke vorgesehen. Wenn Sie das Affinitäts-Cookie entfernen, werden diese Werte neu gesetzt, wenn Sie eine Verbindung zu einem anderen Server herstellen.

### <a name="use-task-parallel-library-with-web-api"></a>Aufgaben-Parallelbibliothek mit Web API verwenden

Um einen optimalen Durchsatz zu erreichen, sollten Sie Multi-Threads-Verfahren verwenden. Die Task Parallel Library (TPL) macht Entwickler produktiver, indem sie den Prozess des Hinzufügens von Parallelität und Gleichzeitigkeit zu Anwendungen vereinfacht.

Siehe diese Beispiele unter Verwendung der [Web API CDSWebApiService Klasse Beispiel (C#)](webapi/samples/cdswebapiservice.md):

- [Web-API CDSWebApiService-Beispiel für parallele Operationen (C#)](webapi/samples/cdswebapiservice-parallel-operations.md)
- [Web-API CDSWebApiService Async Parallel Operations Beispiel (C#)](webapi/samples/cdswebapiservice-async-parallel-operations.md)


## <a name="using-the-organization-service"></a>Verwenden des Organisationsservice

Wenn Sie den Organisationsdienst verwenden, empfehlen wir Ihnen, <xref:Microsoft.Xrm.Tooling.Connector> zu verwenden.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. Diese Klasse implementiert die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methoden und kann alle zurückgegebenen Dienstschutz-API-Limitfehler verwalten. 

Seit Xrm.Tooling.Konnektor Version 9.0.2.16 wird die Anfrage nach dem Zeitraum Wiederholung nach der Dauer automatisch angehalten und erneut gesendet.

Wenn Ihre Anwendung derzeit die niedrigstufige <xref:Microsoft.Xrm.Sdk.Client> verwendet. <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> oder <xref:Microsoft.Xrm.Sdk.WebServiceClient>.<xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> Klassen. Sie sollten in der Lage sein, diese durch die CrmServiceClient-Klasse zu ersetzen. Die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> wird außer Betrieb genommen.

Weitere Informationen:

- [Windows-Client-Anwendungen mit den XRM-Werkzeugen erstellen](/xrm-tooling/build-windows-client-applications-xrm-tools).
- [Außer Betrieb nehmen des Office365-Authentifizierungstyps und der OrganizationServiceProxy-Klasse für die Verbindung mit Common Data Service](/power-platform/important-changes-coming#deprecation-of-office365-authentication-type-and-organizationserviceproxy-class-for-connecting-to-common-data-service)

### <a name="use-task-parallel-library-with-crmserviceclient"></a>Aufgaben-Parallelbibliothek mit CrmServiceClient verwenden

Um einen optimalen Durchsatz zu erreichen, sollten Sie Mehrfach-Threads verwenden. Die Task Parallel Library (TPL) macht Entwickler produktiver, indem sie den Prozess des Hinzufügens von Parallelität und Gleichzeitigkeit zu Anwendungen vereinfacht.

TPL kann mit <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> verwendet werden, da CrmServiceClient eine <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.Clone>-Methode enthält, die es ermöglicht, mehrere Instanzen des Clients mit TPL zu verwalten. Ein Beispiel finden Sie unter [Beispiel: Aufgaben-Parallelbibliothek mit CrmServiceClient](xrm-tooling/sample-tpl-crmserviceclient.md).

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

Dieser Abschnitt enthält häufig gestellte Fragen. Wenn Sie Fragen haben, die nicht beantwortet werden, stellen Sie diese bitte über die Schaltfläche **Feedback** unten auf dieser Seite ein, um Feedback zu dieser Seite einzureichen.

### <a name="im-using-an-etl-application-i-licensed-how-do-i-get-optimum-throughput"></a>Ich verwende eine ETL-Anwendung, die ich lizenziert habe. Wie erreiche ich einen optimalen Durchsatz?

Arbeiten Sie mit dem Anbieter der ETL-Anwendung zusammen, um zu erfahren, welche Einstellungen anzuwenden sind. Stellen Sie sicher, dass Sie eine Version des Produkts verwenden, die das Verhalten "Retry-After" unterstützt.

### <a name="see-also"></a>Siehe auch

[Verwalten Power Platform / Lizenzierung und Lizenzverwaltung / Anforderungsgrenzen und -zuordnungen](/power-platform/admin/api-request-limits-allocations)<br />
[Common Data Service Übersicht über API-Grenzwerte](../../maker/common-data-service/api-limits-overview.md)<br />
[Verwendung der Common Data Service Web-API](webapi/overview.md)<br />
[Verwendung von Common Data Service Organisationsdienst](org-service/overview.md)

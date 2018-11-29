---
title: Mehrerer Anforderungen mithilfe des Organisationsservices ausführen (Common Data Service für Apps)| Microsoft Docs
description: ExecuteMultipleRequest-Message unterstützt die Massenmessage von höheren durchlaufenden Szenarien in Common Data Service für Apps.
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
# <a name="execute-multiple-requests-using-the-organization-service"></a>Ausführen mehrerer Anfragen mithilfe des Organisationsservices

<!-- 

https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/org-service/use-executemultiple-improve-performance-bulk-data-load 

-->
Hauptzweck des Ausführens von mehreren Anforderungen ist es, die Leistung in der Hochwartezeitumgebung zu verbessern, indem Sie den gesamten Datenbestand reduzieren, der über das Netzwerk gesendet wird.

Sie können die <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> Message verwendenm, um höhere durchlaufenden Szenarien in Common Data Service für Apps zu unterstützen. <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> nimmt eine Eingang-Collection der <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest.Requests>-Nachricht entgegen, führt jede Nachrichtenanforderung in der Reihenfolge in der Collection aus, und gibt optional eine Collection von <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses> mit jeder Reaktion auf die Nachricht oder dem aufgetretenen Fehler zurück. Jede Messageanforderung in der Eingabesammlung wird in einer separaten Datenbanktransaktion verarbeitet. <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> wird über <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> ausgeführt. Methode.  
  
Generell verhält sich <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> genauso, als ob Sie jede Messageanforderung separat in der Eingabeanforderungssammlung ausführen, nur mit besserer Leistung. Die Verwendung der <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.CallerId>-Parameter des Serviceproxys wird berücksichtigt und wird bei der Ausführung jeder Message in der Eingabeanforderungssammlung angewendet. Plug-Ins und Workflowaktivitäten werden ausgeführt, wie es für jede verarbeitete Message zu erwarten ist.  
  
Benutzerdefinierter Code in Form von Plug-Ins und benutzerdefinierter Workflowaktivitäten kann sogar <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> ausführen. Allerdings gibt es mehrere wichtige Punkte zu beachten. Eine Ausnahme, die von einem synchronen, registrierten Plug-In ausgelöst wird, wird, wird im <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault>-Parameter des Antwortsammlungselements zurückgegeben. Falls ein Plug-In innerhalb einer Datenbanktransaktion ausgeführt wird, führt das Plug-In <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> aus, und ein Transaktionsrollback wird gestartet. In diesem Rollback sind alle Daten enthalten, die von Anforderungen stammen, die von <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> ausgeführt werden.  
  
<a name="example"></a>

## <a name="example"></a>Beispiel

 Im folgenden Beispielcode wird ein einzelnes <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> dargestellt, das mehrere Erstellen-Vorgänge ausführt. Die Laufzeitausführungsoptionen namens *Einstellungen* werden zur Steuerung der Anforderungsverarbeitung und der zurückgegebenen Ergebnisse verwendet. Diese Laufzeitoptionen werden im nächsten Abschnitt näher erläutert.  
  
```csharp

// Create an ExecuteMultipleRequest object.
requestWithResults = new ExecuteMultipleRequest()
{
    // Assign settings that define execution behavior: continue on error, return responses. 
    Settings = new ExecuteMultipleSettings()
    {
        ContinueOnError = false,
        ReturnResponses = true
    },
    // Create an empty organization request collection.
    Requests = new OrganizationRequestCollection()
};

// Create several (local, in memory) entities in a collection. 
EntityCollection input = GetCollectionOfEntitiesToCreate();

// Add a CreateRequest for each entity to the request collection.
foreach (var entity in input.Entities)
{
    CreateRequest createRequest = new CreateRequest { Target = entity };
    requestWithResults.Requests.Add(createRequest);
}

// Execute all the requests in the request collection using a single web method call.
ExecuteMultipleResponse responseWithResults =
    (ExecuteMultipleResponse)service.Execute(requestWithResults);

// Display the results returned in the responses.
foreach (var responseItem in responseWithResults.Responses)
{
    // A valid response.
    if (responseItem.Response != null)
        DisplayResponse(requestWithResults.Requests[responseItem.RequestIndex], responseItem.Response);

    // An error has occurred.
    else if (responseItem.Fault != null)
        DisplayFault(requestWithResults.Requests[responseItem.RequestIndex], 
            responseItem.RequestIndex, responseItem.Fault);
}
```
  
Weitere Informationen: [Beispiel: Mehrere Anforderungen in einer Transaktion ausführen](samples/execute-multiple-requests.md)
  
<a name="options"></a>
 
## <a name="specify-run-time-execution-options"></a>Angeben von Laufzeitausführungsoptionen  

Der <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest.Settings>-Parameter von <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> gilt für alle Anforderungen in der Anforderungssammlung, die das Ausführungsverhalten und die zurückgegebenen Ergebnisse steuert. Es folgt eine ausführlichere Betrachtung dieser Optionen.  
  
|ExecuteMultipleSettings-Member|Beschreibung|  
|------------------------------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings.ContinueOnError>|Wenn `true`, setzen Sie die Verarbeitung der folgenden Anforderung in der Sammlung fort, selbst wenn bei der Verarbeitung der aktuellen Anforderung ein Fehler in der Sammlung zurückgegeben wurde. Wenn `false`, setzen Sie die Verarbeitung folgenden Anforderung nicht fort.|  
|<xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings.ReturnResponses>|Wenn `true`, geben Sie Antworten von jeder verarbeiteten Messageanforderung zurück. Wenn `false`, geben Sie keine Antworten zurück.<br /><br /> Wenn es auf `true` festgelegt ist, und eine Anforderung keine Antwort zurückgibt, da es so entworfen wurde, wird <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem> für diese Anforderungen auf `null` festgelegt.<br /><br /> Doch auch wenn es `false` ist, wird die <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses>-Sammlung nicht leer sein, falls Fehler zurückgegeben werden. Wenn Fehler zurückgegeben werden, gibt es für jede verarbeitete Anforderung, die einen Fehler zurückgab ein Antwortelement in der Sammlung und <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> wird auf den aktuellen Fehler festgelegt, der aufgetreten ist.|  
  
 Geben in einer Anforderungssammlung mit sechs Anforderungen die dritte und fünfte Anforderung beispielsweise Fehler zurück, zeigt die folgenden Tabelle was die <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses>-Sammlung enthalten würde.  
  
|Einstellungen|Inhalte der Antwortsammlung|  
|--------------|-----------------------------------|  
|ContinueOnError=true, ReturnResponses=true|6 Antwortelemente: bei 2 wurde <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> auf einen Wert festgelegt.|  
|ContinueOnError=false, ReturnResponses=true|3 Antwortelemente: bei 1 wurde <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> auf einen Wert festgelegt.|  
|ContinueOnError=true, ReturnResponses=false|2 Antwortelemente: bei 2 wurde <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> auf einen Wert festgelegt.|  
|ContinueOnError=false, ReturnResponses=false|1 Antwortelement: bei 1 wurde <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.Fault> auf einen Wert festgelegt.|  
  
 Ein <xref:Microsoft.Xrm.Sdk.ExecuteMultipleResponseItem.RequestIndex>-Parameter im Antwortelement gibt, beginnend bei null, die Sequenznummer der Anforderung an, der die Anforderung zugeordnet ist. Im vorherigen Beispiel verfügt die dritte Anforderung beispielsweise über einen Anforderungsindex von 2.  
  
<a name="limitations"></a>

## <a name="run-time-limitations"></a>Laufzeitbeschränkungen

Es gibt mehrere Beschränkungen, die zur mit der Verwendung von <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> in Beziehung stehen, wie in der folgenden Liste beschrieben.  
  
-   **Keine Rekursion zulässig** <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>-  kann <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> nicht aufrufen. Ein <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>-Element, das in der Anforderungssammlung gefunden wird, verursacht einen Fehler für das Anforderungselement.  
  
-   **Maximale Batchgröße** Es gibt eine Beschränkung bei der Anzahl von Anforderungen, die einer Anforderungssammlung hinzugefügt werden können. Wird dieser Grenzwert überschritten, wird ein Fehler ausgelöst, bevor die erste Anforderung ausgeführt wird. Eine Limit von 1000 Anforderungen ist typisch, obwohl die maximale Menge für die CDS for Apps Bereitstellung festgelegt werden kann.
  
-   **Einschränkung von gleichzeitigen Aufrufe**  Für CDS für Apps gibt es eine Beschränkung von 2 gleichzeitig ausgeführten <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>-Elementen pro Organisation. Wird dieser Grenzwert überschritten, wird ein *Server Ausgelastet*-Fehler ausgelöst, bevor die erste Anforderung ausgeführt wird. 

  
<a name="fault"></a>

## <a name="handle-a-batch-size-fault"></a>Behandeln eines Batchgrößenfehlers

Was kann getan werden, wenn die Eingabeanforderungssammlung die maximale Batchgröße überschreitet? Ihr Code kann die maximale Batchgröße nicht direkt durch den Bereitstellungswebdienst abfragen, sofern er nicht unter einem Konto mit der Rolle "Bereitstellungsadministrator" ausgeführt wird.  
  
Glücklicherweise gibt es eine andere Möglichkeit, die Sie verwenden können. Wenn die Anzahl der Anforderungen in der <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest.Requests>-Eingabesammlung die maximale Batchgröße überschreitet, die für eine Organisation zulässig ist, wird vom <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>-Aufruf ein Fehler zurückgegeben. Die maximale Batchgröße wird im Fehler zurückgegeben. Ihr Code kann nach diesen Wert prüfen, die Größe der Eingabeanforderungssammlung anpassen, um innerhalb des angegebenen Grenzwerts zu liegen, und <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> erneut senden. Der folgende Codeausschnitt stellt einen Teil dieser Logik dar.  
  
```csharp
catch (FaultException<OrganizationServiceFault> fault)
{
    // Check if the maximum batch size has been exceeded. The maximum batch size is only included in the fault if it
    // the input request collection count exceeds the maximum batch size.
    if (fault.Detail.ErrorDetails.Contains("MaxBatchSize"))
    {
        int maxBatchSize = Convert.ToInt32(fault.Detail.ErrorDetails["MaxBatchSize"]);
        if (maxBatchSize < requestWithResults.Requests.Count)
        {
            // Here you could reduce the size of your request collection and re-submit the ExecuteMultiple request.
            // For this sample, that only issues a few requests per batch, we will just print out some info. However,
            // this code will never be executed because the default max batch size is 1000.
            Console.WriteLine("The input request collection contains %0 requests, which exceeds the maximum allowed (%1)",
                requestWithResults.Requests.Count, maxBatchSize);
        }
    }
    // Re-throw so Main() can process the fault.
    throw;
}
```

### <a name="see-also"></a>Siehe auch

[Verwenden von Messages mithilfe des Organisationsservices](use-messages.md)<br />
[Verwenden von ExecuteAsync](use-executeAsync.md)<br />
[Verwenden von ExecuteTransaction](use-executetransaction.md)<br />

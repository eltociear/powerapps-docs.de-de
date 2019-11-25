---
title: Ausführen von Nachrichten in einer einzelnen Datenbanktransaktion (Common Data Service) | Microsoft-Dokumentation
description: Sie können mehrere Organisationsserviceanforderungen in einer einzelnen Datenbanktransaktion mit der ExecuteTransactionRequest-Message-Anforderung ausführen.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 2e1d8b71ff915cc49f2c711adee4095043af000c
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748689"
---
# <a name="execute-messages-in-a-single-database-transaction"></a>Führt Nachrichten in einer einzelnen Datenbanktransaktion aus.

 Es ist eine allgemeine Anforderung in Geschäftsanwendungen, Änderungen mehrerer Datensätze im System zu koordinieren, sodass entweder alle Datenänderungen erfolgreich sind oder keine. Unter Datenbankbedingungen ist dies bekannt als Ausführung von mehreren Vorgängen in einer einzelnen Transaktion mit der Möglichkeit eines Rollbacks aller Datenänderungen, falls einer der Vorgänge nicht erfolgreich ist.  
  
 Sie können mehrere Organisationsdienstanforderungen in einer einzelnen Datenbanktransaktion mit der  <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest>-Nachrichtenanforderung ausführen. Um diese Nachricht zu verwenden, füllen Sie die <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest.Requests>-Sammlung mit mehreren Organisationsanforderungen aus, die in der Transaktion ausgeführt werden sollen. Setzen Sie <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest.ReturnResponses> auf `true`, wenn Sie in der <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionResponse.Responses>-Sammlung eine Sammlung von Antworten erhalten möchten, eine für jede ausgeführte Nachrichtenanforderung. Nachrichtenanforderung in der <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest.Requests>-Sammlung werden in der Reihenfolge ausgeführt, in der sie in der Sammlung angezeigt werden. Das Element bei Index 0 wird zuerst ausgeführt. Dieselbe Reihenfolge wird in der Sammlung <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleResponse.Responses> beibehalten.  
  
 Wenn eine der Anforderungen fehlschlägt und die Transaktion zurückgesetzt wird, werden alle Datenänderungen, die während der Transaktion ausgeführt wurde, rückgängig gemacht. Darüber hinaus wird <xref:Microsoft.Xrm.Sdk.ExecuteTransactionFault> zurückgegeben und gibt den Index für die Anforderungssammlung der Anforderungsnachricht an, die den Fehler verursachte.  
  
 <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> enthält eine oder mehrere <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest>-Instanzen.  Eine <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest>-Instanz enthält möglicherweise nicht <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest>. Weitere Informationen zu <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> finden Sie unter [Ausführen mehrere Anfragen mithilfe des Organisationsservices](execute-multiple-requests.md). 

## <a name="example"></a>Beispiel

Dieses Beispiel verwendet einen einzelnen Internet-Methodenaufruf, um alle Message-Anforderungen in der Sammlung als Teil einer einzelnen Datenbanktransaktion auszuführen. Die Einstellungen, die zum Ändern des Ausführungsverhaltens geändert werden müssen, werden ebenfalls angezeigt.

```csharp
// Create an ExecuteTransactionRequest object.
var requestToCreateRecords = new ExecuteTransactionRequest()
{
// Create an empty organization request collection.
Requests = new OrganizationRequestCollection(),
ReturnResponses = true
};

// Create several (local, in memory) entities in a collection. 
var input = new EntityCollection()
{
EntityName = Account.EntityLogicalName,
Entities = {
            new Account { Name = "ExecuteTransaction Example Account 1" },
            new Account { Name = "ExecuteTransaction Example Account 2" },
            new Account { Name = "ExecuteTransaction Example Account 3" },
            new Account { Name = "ExecuteTransaction Example Account 4" },
            new Account { Name = "ExecuteTransaction Example Account 5" }
        }
};

// Add a CreateRequest for each entity to the request collection.
foreach (var entity in input.Entities)
{
CreateRequest createRequest = new CreateRequest { Target = entity };
requestToCreateRecords.Requests.Add(createRequest);
}

// Execute all the requests in the request collection using a single web method call.
try
{
var responseForCreateRecords =
    (ExecuteTransactionResponse)svc.Execute(requestToCreateRecords);

int i = 0;
// Display the results returned in the responses.
foreach (var responseItem in responseForCreateRecords.Responses)
{
    if (responseItem != null)
    Console.WriteLine("Created " + ((Account)requestToCreateRecords.Requests[i].Parameters["Target"]).Name
        + " with account id as " + responseItem.Results["id"].ToString());
    i++;
}
}
catch (FaultException<OrganizationServiceFault> ex)
{
Console.WriteLine("Create request failed for the account{0} and the reason being: {1}",
    ((ExecuteTransactionFault)(ex.Detail)).FaultedRequestIndex + 1, ex.Detail.Message);
throw;
}
```

### <a name="see-also"></a>Siehe auch

[Verwenden von Messages mithilfe des Organisationsservices](use-messages.md)<br />
[Ausführen mehrerer Anfragen mithilfe des Organisationsservices](execute-multiple-requests.md)
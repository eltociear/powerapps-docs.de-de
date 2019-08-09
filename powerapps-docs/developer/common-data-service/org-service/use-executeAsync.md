---
title: Verwenden von ExecuteAsync zum asynchronen Ausführen von Messages (Common Data Service) | Microsoft Docs
description: 'Sie können die ExecuteAsync-Message verwenden, um Lösungen asynchron zu importieren'
ms.custom: ''
ms.date: 06/08/2019
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
# <a name="use-executeasync-to-execute-messages-asynchronously"></a>Verwenden von ExecuteAsync zum asynchronen Ausführen von Messages

Bis auf zwei sind alle Datenvorgänge unter Verwendung der SDK-Assembly-Anfrageklassen synchron.

Das Importieren einer Lösung ist ein Vorgang, der beträchtliche Ressourcen erfordern kann, es gibt also eine Option zum asynchronen Ausführen dieses Vorgangs unter Verwendung der <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest>-Anfrageklasse. Die <xref:Microsoft.Crm.Sdk.Messages.DeleteAndPromoteRequest>-Anfrageklasse führt ähnliche ressourcenintensive Vorgänge aus.

Das asynchrone Importieren einer Lösung verbessert die Systemleistung durch das Zurückstellen der Message-Ausführung auf einen späteren Zeitpunkt, zu dem die Serverlast möglicherweise geringer ist. Interaktive Benutzer müssen nicht auf die Zielnachricht, bis die Zielnachricht ausgeführt wird, um fortzufahren. Dies ist besonders nützlich beim Importieren von Lösungen, deren Ausführung einige Minuten oder mehr dauern kann.  
  
> [!NOTE]
>  <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest> und <xref:Microsoft.Crm.Sdk.Messages.DeleteAndPromoteRequest> sind die einzigen Anfrageklassen, die mit der Message `ExecuteAsync` verwendet werden können.
  
Verwenden Sie die <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest>-Anfrageklasse, um eine Message asynchron auszuführen. Konfigurieren Sie die Anforderung und übergeben Sie die Anforderungsinstanz als Argument an <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>. <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncResponse> wird mit der ID des asynchronen Auftrags zurückgegeben. Sie können (optional) den Auftrag mithilfe der ID abfragen, um seinen aktuellen Status herauszufinden.  
  
Sie können die <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>-Anfrageklasse verwenden, um mehrere Lösungen der Warteschlange hinzuzufügen, die asynchron importiert werden sollen. Dazu können Sie eine oder mehrere `ExecuteAsync`-Message-Anfragen einer `ExecuteMultiple`-Message-Anforderung hinzufügen. Aufgrund der Drosselungseinschränkungen, die die Systemleistung verbessern, darf nur eine Meldung, die nur asynchron ausgeführt wird, für eine Organisation gleichzeitig ausgeführt werden.

Weitere Informationen zur `ExecuteMultiple`-Message finden Sie unter [Ausführen mehrerer Anfragen mithilfe des Organisationsservices](execute-multiple-requests.md).  

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die <xref:Microsoft.Xrm.Sdk.Messages.ExecuteAsyncRequest>-Message-Anforderungsklasse mit der <xref:Microsoft.Crm.Sdk.Messages.ImportSolutionRequest>-Message-Anforderungsklasse verwendet wird.

```csharp
string ManagedSolutionLocation = @"C:\temp\ManagedSolutionForImportExample.zip";

byte[] fileBytes = File.ReadAllBytes(ManagedSolutionLocation);

ImportSolutionRequest impSolReq = new ImportSolutionRequest()
{
CustomizationFile = fileBytes
};

ExecuteAsyncRequest asyncReq = new ExecuteAsyncRequest()
{
Request = impSolReq
};

var asyncResp = (ExecuteAsyncResponse)svc.Execute(asyncReq);

Guid asyncOperationId = asyncResp.AsyncJobId;
```
Sie können dann die [AsyncOperation](../reference/entities/asyncoperation.md)-Entität mithilfe des `asyncOperationId`-Werts für den Systemauftrag abrufen, der mit [AsyncOperationId](../reference/entities/asyncoperation.md#BKMK_AsyncOperationId) übereinstimmt, um zu erkennen, wann der [StatusCode](../reference/entities/asyncoperation.md#BKMK_StatusCode)-Wert angibt, ob der Vorgang erfolgreich war (30), fehlgeschlagen ist (31) oder storniert wurde (32).

### <a name="see-also"></a>Siehe auch

[Verwenden von Messages mithilfe des Organisationsservices](use-messages.md)<br />
[Verwenden von ExecuteTransaction](use-executetransaction.md)<br />
[Ausführen mehrerer Anfragen mithilfe des Organisationsservices](execute-multiple-requests.md)


  
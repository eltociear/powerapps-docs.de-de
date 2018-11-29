---
title: Erkennen von doppelten Daten mithilfe des Organisationsservices (Common Data Service für Apps)| Microsoft Docs
description: 'Der Organisationsservice ermöglicht es Ihnen, doppelte Datensätze im Common Data Service (CDS) für Apps zu erkennen, um die Integrität der Daten zu gewährleisten.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="detect-duplicate-data-using-the-organization-service"></a>Duplikaterkennung mithilfe des Organisation-Service

Der Common Data Service (CDS) Organisationsservice ermöglicht es Ihnen, doppelte Datensätze zu erkennen, um die Integrität der Daten zu gewährleisten. Ausführliche Informationen zum Erkennen von doppelten Daten mithilfe des Codes, finden Sie unter [Erkennen von doppelten Daten mithilfe von Code](../detect-duplicate-data-with-code.md). 

> [!NOTE]
> Stellen Sie sicher, dass entsprechende Duplikaterkennungsregeln vorhanden sind. CDS for Apps enthält standardmäßig Duplikaterkennungsregeln für Konten, Kontakte und Leads, nicht aber für andere Arten von Datensätzen. Wenn Sie das System von Duplikate für andere Datensatztypen erkennen soll, müssen Sie eine neue Regel erstellen. <br/>- Informationen darüber, wie Sie eine Duplikaterkennungsregel mithilfe der Benutzeroberfläche erstellen, finden Sie unter [Einrichten einer Duplikaterkennungsregel, um Ihre Daten sauber zu halten](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).<br/>- Weitere Informationen zum Erstellen von Duplikaterkennungsregeln mit Code [Duplikatregelentitäten](../duplicaterule-entities.md).


## <a name="use-retrieveduplicatesrequest-message-to-detect-duplicates-before-you-create-or-update-record"></a>Verwenden Sie die Meldung RetrieveDuplicatesRequest, um Duplikate zu erkennen, bevor Sie einen Datensatz erstellen oder aktualisieren.

Sie können programmgesteuert überprüfen, ob eine Entität ein Duplikat ist oder zum Duplikat wird, bevor Sie sie erstellen oder aktualisieren, indem Sie die Klasse <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest> verwenden.

```csharp
var account = new Account();
account.Name = "Sample Account";

var request = new RetrieveDuplicatesRequest()
{
    BusinessEntity = account,
    MatchingEntityName = account.LogicalName,
    PagingInfo = new PagingInfo() { PageNumber = 1, Count = 50 }
};

var response = (RetrieveDuplicatesResponse)svc.Execute(request);

if (response.DuplicateCollection.Entities.Count >= 1)
{
    Console.WriteLine("{0} Duplicate records found.", response.DuplicateCollection.Entities.Count);
}
```

## <a name="use-suppressduplicatedetection-parameter-to-throw-errors-when-you-create-or-update-record"></a>Verwenden des SuppressDuplicateDetection-Parameters, um Fehler beim Erstellen oder Aktualisieren von Datensätzen auszugeben.

Wenn Sie möchten, dass die Plattform einen Fehler auslöst, wenn ein neuer Datensatz, den Sie erstellen, als doppelter Datensatz erkannt wird, oder wenn Sie einen bestehenden Datensatz aktualisieren, damit Regeln zur Erkennung von Duplikaten ausgewertet werden, müssen Sie die Klassen <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode verwenden und den `SuppressDuplicateDetection`-Parameter, der auf `false`festgelegt ist, anwenden.

Der folgende Code löst eine `InvalidOperationException` Ausnahmeregelung mit der Meldung `A record was not created or updated because a duplicate of the current record already exists.` aus, wenn Folgendes true ist:

- Die Duplikaterkennung wird für die Umgebung aktiviert, wenn ein Datensatz erstellt oder aktualisiert wird.
- In der Firmaenentität ist die Duplikaterkennung aktiviert
- Eine Duplikaterkennungsregel wird veröffentlicht, die überprüft, ob der Firmennamewert eine genaue Übereinstimmung mit einem bereits existierenden Datensatz hat.
- Es gibt einen vorhandenen Account mit dem Namen `Sample Account`

```csharp
var account = new Account();
account.Name = "Sample Account";

var request = new CreateRequest();
request.Target = account;
request.Parameters.Add("SuppressDuplicateDetection", false);

try
{
    svc.Execute(request);
}
catch (FaultException<OrganizationServiceFault> ex)
{
    switch (ex.Detail.ErrorCode)
    {
        case -2147220685:
            throw new InvalidOperationException(ex.Detail.Message);
        default:
            throw ex;
    }
}
```

### <a name="see-also"></a>Siehe auch
[Erkennen von doppelten Daten mit der Web-API](../webapi/manage-duplicate-detection-create-update.md)


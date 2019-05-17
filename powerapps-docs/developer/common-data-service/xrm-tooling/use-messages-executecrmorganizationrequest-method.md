---
title: Verwenden von Messages mithilfe der ExecuteCrmOrganizationRequest-Methode (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie, wie Nachrichten mit der ExecuteCrmOrganizationRequest-Methode verwendet werden. Diese Beispiele zeigen, wie die CreateRequest- und RetrieveMultipleRequest-Nachricht mit der CrmServiceClient.String)-Methode ausgeführt wird.'
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 1ba60f67-522d-4540-a6f9-0787d7074a79
caps.latest.revision: 17
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-messages-with-the-executecrmorganizationrequest-method"></a>Verwenden von Nachrichten der ExecuteCrmOrganizationRequest-Methode
  
Die folgenden Codebeispiele demonstrieren, wie Sie mithilfe der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>-Methode Nachrichten ausführen können.  
  
## <a name="example-1-createrequest-message"></a>Beispiel 1: CreateRequest-Nachricht  

 Das folgende Codebeispiel demonstriert, wie Sie die <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Nachricht mithilfe der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> Methode. Erstellen Sie in diesem Beispiel eine Firma und zeigen Sie dann im Antwortobjekt die ID an.  
  
```csharp 
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{  
    var request = new CreateRequest();  
    var newAccount = new Entity("account");  
    newAccount.Attributes.Add("name", "Sample Test Account");  
    request.Target = newAccount;  
    var response = (CreateResponse)svc.ExecuteCrmOrganizationRequest(request);  
  
    // Display the ID of the newly created account record.  
    Console.WriteLine("Account record created with the following ID: {0}", response.id.ToString());  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", svc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(svc.LastCrmException.Message);  
    Console.WriteLine(svc.LastCrmException.Source);  
    Console.WriteLine(svc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
## <a name="example-2-retrievemultiplerequest"></a>Beispiel 2: RetrieveMultipleRequest  

 Das folgende Codebeispiel demonstriert, wie Sie die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>-Nachricht mithilfe der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> Methode. In diesem Beispiel führen Sie eine Mehrfachabrufanforderung aus, um alle Kontakte im System abzurufen und die vollständigen Namen anzuzeigen.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{  
  
    var userSettingsQuery = new QueryExpression("contact");  
    userSettingsQuery.ColumnSet.AllColumns = true;  
    var retrieveRequest = new RetrieveMultipleRequest()  
    {  
        Query = userSettingsQuery  
    };  
    EntityCollection EntCol = (svc.ExecuteCrmOrganizationRequest(retrieveRequest) as RetrieveMultipleResponse).EntityCollection;  
    foreach (var a in EntCol.Entities)  
    {  
        Console.WriteLine("Account name: {0} {1}", a.Attributes["firstname"], a.Attributes["lastname"]);  
    }  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", svc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(svc.LastCrmException.Message);  
    Console.WriteLine(svc.LastCrmException.Source);  
    Console.WriteLine(svc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
### <a name="see-also"></a>Siehe auch  

[Verwenden von XRM-Tooling zur Herstellung einer Verbindung mit Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Verwenden der XRM-Tooling-API zur Ausführung von Aktionen in Common Data Service](use-xrm-tooling-execute-actions.md)

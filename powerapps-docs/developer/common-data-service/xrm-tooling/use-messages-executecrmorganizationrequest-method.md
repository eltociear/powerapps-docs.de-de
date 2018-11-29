---
title: Verwenden von Messages mithilfe der ExecuteCrmOrganizationRequest-Methode (Common Data Service für Apps) | Microsoft Docs
description: 'Erfahren Sie, wie Nachrichten mit der ExecuteCrmOrganizationRequest-Methode verwendet werden. Diese Beispiele zeigen, wie die CreateRequest- und RetrieveMultipleRequest-Nachricht mit der CrmServiceClient.String)-Methode ausgeführt wird.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
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

<!-- TODO:
In addition to using the <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> method, you can now use the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> method to execute the xRM and CDS for Apps Customer Engagement messages. Similar to the <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> method, the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> method takes a message request class as a parameter and returns a message response class. For a list of messages that you can execute using the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> method, see [xRM Messages in the Organization Service](../org-service/xrm-messages-organization-service.md) and [CDS for Apps Messages in the Organization Service](../org-service/organization-service-messages.md).   -->
  
 Die folgenden Codebeispiele demonstrieren, wie Sie mithilfe der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>-Methode Nachrichten ausführen können.  
  
## <a name="example-1-createrequest-message"></a>Beispiel 1: CreateRequest-Nachricht  

 Das folgende Codebeispiel demonstriert, wie Sie die <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Nachricht mithilfe der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> Methode. Erstellen Sie in diesem Beispiel eine Firma und zeigen Sie dann im Antwortobjekt die ID an.  
  
```csharp 
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", "<Domain>"),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected.  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to.  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    CreateRequest request = new CreateRequest();  
    Entity newAccount = new Entity("account");  
    newAccount.Attributes.Add("name", "Sample Test Account");  
    request.Target = newAccount;  
    CreateResponse response = (CreateResponse)crmSvc.ExecuteCrmOrganizationRequest(request);  
  
    // Display the ID of the newly created account record.  
    Console.WriteLine("Account record created with the following ID: {0}", response.id.ToString());  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", crmSvc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(crmSvc.LastCrmException.Message);  
    Console.WriteLine(crmSvc.LastCrmException.Source);  
    Console.WriteLine(crmSvc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
## <a name="example-2-retrievemultiplerequest"></a>Beispiel 2: RetrieveMultipleRequest  

 Das folgende Codebeispiel demonstriert, wie Sie die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>-Nachricht mithilfe der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*> Methode. In diesem Beispiel führen Sie eine Mehrfachabrufanforderung aus, um alle Kontakte im System abzurufen und die vollständigen Namen anzuzeigen.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", "<Domain>"),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected.  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to.  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    QueryExpression userSettingsQuery = new QueryExpression("contact");  
    userSettingsQuery.ColumnSet.AllColumns = true;  
    var retrieveRequest = new RetrieveMultipleRequest()  
    {  
        Query = userSettingsQuery  
    };  
    EntityCollection EntCol = (crmSvc.ExecuteCrmOrganizationRequest(retrieveRequest) as RetrieveMultipleResponse).EntityCollection;  
    foreach (var a in EntCol.Entities)  
    {  
        Console.WriteLine("Account name: {0} {1}", a.Attributes["firstname"], a.Attributes["lastname"]);  
    }  
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("An error occurred: {0}", crmSvc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(crmSvc.LastCrmException.Message);  
    Console.WriteLine(crmSvc.LastCrmException.Source);  
    Console.WriteLine(crmSvc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
### <a name="see-also"></a>Siehe auch  

<!-- TODO:
[Use Messages (Request and Response Classes) with the Execute Method](../org-service/use-messages-request-response-classes-execute-method.md)<br /> -->
[Verwenden von XRM-Tooling, um eine Verbindung mit CDS für Apps herzustellen](use-crmserviceclient-constructors-connect.md)<br />
[Verwenden der XRM-Tooling-API, um Aktionen in CDS für Apps auszuführen](use-xrm-tooling-execute-actions.md)

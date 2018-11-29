---
title: Nutzung von XRM-Tools mit generierten Klassen mithilfe des Codegenerierungstools (Common Data Service für Apps) | Microsoft Docs
description: Die CrmServiceClient-Klasse kann zum Einrichten Ihrer Entität- und Datenkontextklassen mithilfe des Codegenerierungstool verwendet werden. Das Beispiel zeigt das Herstellen einer Verbindung mit CDS für Apps mithilfe einer Instance dieser Klasse. Anschließend wird der Wert des OrganizationServiceProxy-Objekts auf die CrmServiceClient.OrganizationServiceProxy-Eigenschaft gesetzt.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 7c81c1e5-2229-4a15-8374-6ee9456d18a9
caps.latest.revision: 19
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-xrm-tooling-with-classes-generated-using-the-code-generation-tool"></a>Verwendung von XRM-Tooling mit Klassen, die durch das Code-Generierungstool erstellt wurden

<!-- TODO:
The <xref:Microsoft.Xrm.Tooling.Connector> assembly doesn’t directly provide interfaces for the entity and data context classes generated using the code-generation tool. However, you can use the CDS for Apps connection created by the <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> class to set up your entity and data context classes by using the code-generation tool. More information: [Create Early Bound Entity Classes with the Code Generation Tool (CrmSvcUtil.exe)](../org-service/create-early-bound-entity-classes-code-generation-tool.md) -->
  
 Um die „CDS für Apps”-Verbindung zu verwenden, die von der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse erstellt wurde, erstellen Sie eine Verbindung zu CDS für Apps mithilfe einer Instanz dieser Klasse und legen Sie dann den Wert des <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>-Objekts auf die <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.OrganizationServiceProxy>-Eigenschaft fest. -Eigenschaft verfügbar.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>",“<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected.  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy prox = crmSvc.OrganizationServiceProxy;   
}  
else  
{  
    // Display the last error.  
    Console.WriteLine("Error occurred: {0}", crmSvc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(crmSvc.LastCrmException.Message);  
    Console.WriteLine(crmSvc.LastCrmException.Source);  
    Console.WriteLine(crmSvc.LastCrmException.StackTrace);  
  
    return;  
}  
  
```  
  
> [!NOTE]
>  Die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> Klasse ist nicht vor Bedrohungen geschützt. Bei der Arbeit mit Entitäts- und Datenkontextklassen, die über das Codegenerierungstool oder über LINQ erstellt werden, um Daten zu erhalten, sollten Sie überlegen, ein Sperrschema in Ihrem Code zu erstellen, falls er in einer Umgebung mit mehreren Threads ausgeführt wird.  
  
### <a name="see-also"></a>Siehe auch  

<!-- TODO:
[Use the IOrganizationService Web Service to Read and Write Data or Metadata](../org-service/use-organization-service-read-write-data-metadata.md)<br /> -->
[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)

---
title: Nutzen von XRM-Tooling zum Löschen von Daten (Common Data Service) | Microsoft Docs
description: 'Verwenden der CrmServiceClient-Klasse, um Daten aus Common Data Service zu löschen'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 7e503d2c-89df-4846-8528-632b5ee12bd5
caps.latest.revision: 14
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-xrm-tooling-to-delete-data"></a>Verwendung von XRM-Tooling zum Löschen von Daten

Es gibt zwei Möglichkeiten in der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse zum Löschen von Daten in Common Data Service: <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.DeleteEntity(System.String,System.Guid,System.Guid)> und <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.DeleteEntityAssociation(System.String,System.Guid,System.String,System.Guid,System.String,System.Guid)>.  
  
## <a name="deleteentity"></a>DeleteEntity  

DeleteEntity wird verwendet, um eine einzelne Datenzeile aus Common Data Service zu entfernen. Um diese Möglichkeit zu nutzen, müssen Sie den Entitätsschemanamen und die GUID der Zeile kennen, die Sie entfernen möchten.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", <Domain>),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    // Delete the entity record  
    crmSvc.DeleteEntity("account", <accountId>);  
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
  
## <a name="deleteentityassociation"></a>DeleteEntityAssociation  

DeleteEntityAssociation entfernt die viele-zu-viele-Zuordnung zwischen Datensätzen in den Entitäten. In diesem Beispiel entfernen wir die Zuordnung zwischen einem Datensatz in Lead- und Firmenentitäten.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", <Domain>),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected  
if (crmSvc != null && crmSvc.IsReady)  
{  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    Guid accountId = new Guid("<Account_GUID>");  
    Guid leadId = new Guid("<Lead_GUID>");  
    string accountLeadRelationshipName= "accountleads_association";   
    crmSvc.DeleteEntityAssociation("account" , accountId, "lead" ,  leadId, accountLeadRelationshipName)  
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

[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
[Verwenden von XRM-Tooling zur Herstellung einer Verbindung mit Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Verwenden der XRM-Tooling-API zur Ausführung von Aktionen in Common Data Service](use-xrm-tooling-execute-actions.md)

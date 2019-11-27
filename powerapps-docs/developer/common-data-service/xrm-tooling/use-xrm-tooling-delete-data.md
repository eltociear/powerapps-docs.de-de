---
title: Verwendung von XRM-Tools zum Löschen von Daten (Common Data Service) | Microsoft-Dokumentation
description: Verwenden der CrmServiceClient-Klasse, um Daten aus Common Data Service zu löschen
ms.custom: ''
ms.date: 03/20/2019
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
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ac21ffa82890c580f8683b555601a064c848d9e4
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748323"
---
# <a name="use-xrm-tooling-to-delete-data"></a>Verwendung von XRM-Tooling zum Löschen von Daten

Es gibt zwei Möglichkeiten, um in der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> Klasse Daten in Common Data Service: <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.DeleteEntity(System.String,System.Guid,System.Guid)> und <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.DeleteEntityAssociation(System.String,System.Guid,System.String,System.Guid,System.String,System.Guid)> zu löschen.  
  
## <a name="deleteentity"></a>DeleteEntity  

`DeleteEntity` wird verwendet, um eine einzelne Datenzeile aus Common Data Service zu entfernen. Um diese Möglichkeit zu nutzen, müssen Sie den Entitätsschemanamen und die GUID der Zeile kennen, die Sie entfernen möchten.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected  
if (svc != null && svc.IsReady)  
{  
    // Delete the entity record  
    svc.DeleteEntity("account", <accountId>);  
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
  
## <a name="deleteentityassociation"></a>DeleteEntityAssociation  

`DeleteEntityAssociation` entfernt die viele-zu-viele-Zuordnung zwischen Datensätzen in den Entitäten. In diesem Beispiel entfernen wir die Zuordnung zwischen einem Datensatz in Lead- und Firmenentitäten.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected  
if (svc != null && svc.IsReady)  
{  
    Guid accountId = new Guid("<Account_GUID>");  
    Guid leadId = new Guid("<Lead_GUID>");  
    string accountLeadRelationshipName= "accountleads_association";   
    svc.DeleteEntityAssociation("account" , accountId, "lead" ,  leadId, accountLeadRelationshipName)  
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

[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
[Verwenden von XRM-Tools, um eine Verbindung zu Common Data Service herzustellen](use-crmserviceclient-constructors-connect.md)<br />
[Use XRM Tooling API to execute actions in Common Data Service](use-xrm-tooling-execute-actions.md)

---
title: Nutzen von XRM-Tooling zur Datenaktualisierung (Common Data Service für Apps) | Microsoft Docs
description: 'Verwenden der CrmServiceClient-Klasse, um Daten in CDS für Apps zu aktualisieren'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 8ec3d4ca-d836-4e7e-b2bf-9d9f806bd145
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
# <a name="use-xrm-tooling-to-update-data"></a>Verwendung von XRM-Tooling zum Aktualisieren von Daten

Es gibt zwei Methoden in der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse, um Daten in CDS für Apps zu aktualisieren: <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.UpdateEntity(System.String,System.String,System.Guid,System.Collections.Generic.Dictionary{System.String,Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper},System.String,System.Boolean,System.Guid)> und <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.UpdateStateAndStatusForEntity(System.String,System.Guid,System.String,System.String,System.Guid)>.  
  
Für eine Updateaktion mithilfe der XRM-Tooling-API ist eine Datennutzlast erforderlich. Die Datennutzlast ist ein Dictionary\<string, CrmDataTypeWrapper>-Objekt. <xref:Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper> wird verwendet, um der Schnittstelle mitzuteilen, welche Verarbeitung auf den Datenpunkt angewendet werden soll, auf den verwiesen wird.  
  
## <a name="updateentity"></a>UpdateEntity  

Dies ist die Ankermethode zum Aktualisieren eines jeden Datensatzes in CDS für Apps, mit Ausnahme des Einstellungsstatus oder des Status eines Datensatzes. Zur Verwendung müssen Sie die folgenden Informationen zu berücksichtigen: der Schemaname der Entität, die Sie aktualisieren möchten, das Primärschlüsselfeld der Entität, die Sie aktualisieren möchten, die GUID des Datensatzes, den Sie aktualisieren möchten, und das Datennutzlastarray, mit dem aktualisiert werden soll.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", “<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected  
if (crmSvc != null && crmSvc.IsReady)  
{  
    //Display the CRM version number and org name that you are connected to  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",   
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    // Update the account record  
    Dictionary<string, CrmDataTypeWrapper> updateData = new Dictionary<string, CrmDataTypeWrapper>();  
    updateData.Add("name", new CrmDataTypeWrapper("Updated Sample Account Name", CrmFieldType.String));  
    updateData.Add("address1_city", new CrmDataTypeWrapper("Boston", CrmFieldType.String));  
    updateData.Add("telephone1", new CrmDataTypeWrapper("555-0161", CrmFieldType.String));   
    bool updateAccountStatus = crmSvc.UpdateEntity("account","accountid",_accountId,updateData);  
  
    // Validate if the account record was updated successfully, and then display the updated information  
    if (updateAccountStatus == true)  
    {  
        Console.WriteLine("Updated the account details as follows:");  
        Dictionary<string, object> data = crmSvc.GetEntityDataById("account", accountId, null);  
        foreach (var pair in data)  
        {  
            if ((pair.Key == "name") || (pair.Key == "address1_city") || (pair.Key == "telephone1"))  
            {  
                Console.WriteLine(pair.Key.ToUpper() + ": " + pair.Value);  
            }  
        }  
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
  
## <a name="updatestateandstatusforentity"></a>UpdateStateAndStatusForEntity 
 
Diese Methode wird verwendet, um den Status eines Datensatzes in CDS für Apps festzulegen. So starten z. B. alle Datensätze im Allgemeinen in einem „geöffneten“ Status. Der Name des Status wird basierend auf dem Typ des Datensatzes und sogar je nach Auswahl des Entwicklers geändert. Ein Angebot enthält beispielsweise mehrere mögliche Status: **Entwurf**, **Aktiv**, **Schließen**, **Verloren**, **Gewonnen**.  
  
<!-- TODO:
> [!TIP]
>  You can use the OptionSets.cs file in the SDK\SampleCode\CS\HelperCode folder of the SDK download package to view and use the global option sets available for various entities in CDS for Apps. For more information about global option sets, see [Customize Global Option Sets](../org-service/customize-global-option-sets.md).   -->
  
Zum Aktualisieren des Status einer Entität müssen Sie wissen, wie der Soll-Zustand und der Status lauten, entweder nach Namen nach IDs. Sowohl die Namen als auch die IDs finden Sie, indem Sie die Metadaten für die Entität abrufen und auf die Felder „Status“ und „Zustand“ achten. In diesem Beispiel wird veranschaulicht, wie Sie den Status eines Firmendatensatzes auf **Inaktiv** festgelegen.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserName>", "<Password>", “<Domain>”),"<Server>", "<Port>", "<OrgName>");  
  
// Verify that you are connected  
if (crmSvc != null && crmSvc.IsReady)  
{   
    //Display the CRM version number and org name that you are connected to  
    Console.WriteLine("Connected to CRM! (Version: {0}; Org: {1}",  
    crmSvc.ConnectedOrgVersion, crmSvc.ConnectedOrgUniqueName);  
  
    // Here are the state and status code values  
    // statecode = 1 ( Inactive )   
    // statuscode = 2 ( Inactive )   
  
    crmSvc.UpdateStateAndStatusForEntity("account" , accountId , 1 , 2 );  
  
    // the same command using the second form of the method  
    crmSvc.UpdateStateAndStatusForEntity("account" , accountId , "Inactive" , "Inactive");  
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
[Verwenden von XRM-Tooling, um eine Verbindung mit CDS für Apps herzustellen](use-crmserviceclient-constructors-connect.md)<br />
[Verwenden der XRM-Tooling-API, um Aktionen in CDS für Apps auszuführen](use-xrm-tooling-execute-actions.md)<br />
<!-- TODO:
[Work with attribute metadata](../org-service/work-attribute-metadata.md) -->

---
title: Nutzen von XRM-Tooling zum Aktualisieren von Daten (Common Data Service) | Microsoft Docs
description: 'Verwenden der CrmServiceClient-Klasse, um Daten in Common Data Service zu aktualisieren'
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 8ec3d4ca-d836-4e7e-b2bf-9d9f806bd145
caps.latest.revision: 14
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-xrm-tooling-to-update-data"></a>Verwendung von XRM-Tooling zum Aktualisieren von Daten

Es gibt zwei Möglichkeiten in der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse zum Aktualisieren von Daten in Common Data Service: <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.UpdateEntity(System.String,System.String,System.Guid,System.Collections.Generic.Dictionary{System.String,Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper},System.String,System.Boolean,System.Guid)> und <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.UpdateStateAndStatusForEntity(System.String,System.Guid,System.String,System.String,System.Guid)>.  
  
Für eine Updateaktion mithilfe der XRM-Tooling-API ist eine Datennutzlast erforderlich. Die Datennutzlast ist ein Dictionary\<string, CrmDataTypeWrapper>-Objekt. <xref:Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper> wird verwendet, um der Schnittstelle mitzuteilen, welche Verarbeitung auf den Datenpunkt angewendet werden soll, auf den verwiesen wird.  
  
## <a name="updateentity"></a>UpdateEntity  

Dies ist die Ankermethode zum Aktualisieren eines jeden Datensatzes in Common Data Service, mit Ausnahme des Einstellungsstatus oder des Status eines Datensatzes. Zur Verwendung müssen Sie die folgenden Informationen zu berücksichtigen: der Schemaname der Entität, die Sie aktualisieren möchten, das Primärschlüsselfeld der Entität, die Sie aktualisieren möchten, die GUID des Datensatzes, den Sie aktualisieren möchten, und das Datennutzlastarray, mit dem aktualisiert werden soll.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected  
if (svc != null && svc.IsReady)  
{ 
   // Update the account record  
    Dictionary<string, CrmDataTypeWrapper> updateData = new Dictionary<string, CrmDataTypeWrapper>();  
    updateData.Add("name", new CrmDataTypeWrapper("Updated Sample Account Name", CrmFieldType.String));  
    updateData.Add("address1_city", new CrmDataTypeWrapper("Boston", CrmFieldType.String));  
    updateData.Add("telephone1", new CrmDataTypeWrapper("555-0161", CrmFieldType.String));   
    bool updateAccountStatus = svc.UpdateEntity("account","accountid",_accountId,updateData);  
  
    // Validate if the account record was updated successfully, and then display the updated information  
    if (updateAccountStatus == true)  
    {  
        Console.WriteLine("Updated the account details as follows:");  
        Dictionary<string, object> data = svc.GetEntityDataById("account", accountId, null);  
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
    Console.WriteLine("An error occurred: {0}", svc.LastCrmError);  
  
    // Display the last exception message if any.  
    Console.WriteLine(svc.LastCrmException.Message);  
    Console.WriteLine(svc.LastCrmException.Source);  
    Console.WriteLine(svc.LastCrmException.StackTrace);  
  
    return;  
}  
```  
  
## <a name="updatestateandstatusforentity"></a>UpdateStateAndStatusForEntity
 
Diese Methode wird verwendet, um den Status eines Datensatzes in Common Data Service festzulegen. So starten z. B. alle Datensätze im Allgemeinen in einem „geöffneten“ Status. Der Name des Status wird basierend auf dem Typ des Datensatzes und sogar je nach Auswahl des Entwicklers geändert. Ein Angebot enthält beispielsweise mehrere mögliche Status: **Entwurf**, **Aktiv**, **Schließen**, **Verloren**, **Gewonnen**.  
  
Zum Aktualisieren des Status einer Entität müssen Sie wissen, wie der Soll-Zustand und der Status lauten, entweder nach Namen nach IDs. Sowohl die Namen als auch die IDs finden Sie, indem Sie die Metadaten für die Entität abrufen und auf die Felder „Status“ und „Zustand“ achten. In diesem Beispiel wird veranschaulicht, wie Sie den Status eines Firmendatensatzes auf **Inaktiv** festgelegen.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected  
if (svc != null && svc.IsReady)  
{   
    // Here are the state and status code values  
    // statecode = 1 ( Inactive )   
    // statuscode = 2 ( Inactive )   
  
    svc.UpdateStateAndStatusForEntity("account" , accountId , 1 , 2 );  
  
    // the same command using the second form of the method  
    svc.UpdateStateAndStatusForEntity("account" , accountId , "Inactive" , "Inactive");  
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
[Verwenden von XRM-Tooling zur Herstellung einer Verbindung mit Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Verwenden der XRM-Tooling-API zur Ausführung von Aktionen in Common Data Service](use-xrm-tooling-execute-actions.md)<br />


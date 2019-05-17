---
title: Nutzen von XRM-Tooling zum Abrufen von Daten (Common Data Service) | Microsoft Docs
description: 'Verwenden der CrmServiceClient-Klasse, um Daten aus Common Data Service abzurufen'
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 2afc057e-8f70-4bea-bad4-d01e18ed92fd
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
# <a name="use-xrm-tooling-to-retrieve-data"></a>XRM-Tools verwenden, um Daten abzurufen

Es gibt zahlreiche Möglichkeiten in der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse zum Abrufen von Daten in Common Data Service. Die folgenden Beispiele zeigen, wie Sie einen Datensatz nach ID oder durch FetchXML-Abfrage abrufen können.  
  
## <a name="getentitydatabyid"></a>GetEntityDataById  

Diese Methode sucht eine Entität über die angegebene ID Im vorliegenden Beispiel steht geben wir Null für den Feldlistenwert an, um alle Attribute des angegebenen Entitätsdatensatzes (Firma) abzurufen, und dann den Namen des abgerufenen Firmendatensatzes anzuzeigen.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{  
    Dictionary<string, object> data = svc.GetEntityDataById("account", <Account_ID>, null);  
    foreach (var pair in data)  
    {  
        if (pair.Key == "name")  
        {  
            Console.WriteLine("Name of the account is {0}", pair.Value);  
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
  
## <a name="getentitydatabyfetchsearchec"></a>GetEntityDataByFetchSearchEC  

Diese Methode sucht die Entität auf der Grundlage der angegebenen `FetchXML`-Abfrage. In diesem Beispiel rufen wir die Zählung aller Firmendatensätze im System ab und zeigen sie an.  
  
```csharp  
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{   
    string fetchXML =   
        @"<fetch version='1.0' output-format='xml-platform' mapping='logical' distinct='false' returntotalrecordcount='true' >  
            <entity name='account'>  
              <attribute name='accountid' />  
            </entity>  
        </fetch>";  
    var queryResult = crmSvc.GetEntityDataByFetchSearchEC(fetchXML);  
    if (queryResult != null)  
    {  
        Console.WriteLine(String.Format("Account Records Count : {0}", queryResult.TotalRecordCount));  
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

[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
[Verwenden von XRM-Tooling zur Herstellung einer Verbindung mit Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Verwenden der XRM-Tooling-API zur Ausführung von Aktionen in Common Data Service](use-xrm-tooling-execute-actions.md)

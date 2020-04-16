---
title: Verwendung von XRM-Tools zum Abrufen von Daten (Common Data Service) | Microsoft-Dokumentation
description: Verwenden der CrmServiceClient-Klasse, um Daten aus Common Data Service abzurufen
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: 8de9abf4a377e91ad936a21429902ac426a088ae
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154846"
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
[Verwenden von XRM-Tools, um eine Verbindung zu Common Data Service herzustellen](use-crmserviceclient-constructors-connect.md)<br />
[Use XRM Tooling API to execute actions in Common Data Service](use-xrm-tooling-execute-actions.md)

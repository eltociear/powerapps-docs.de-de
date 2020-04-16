---
title: Verwendung von XRM-Tools zum Erstellen von Daten (Common Data Service) | Microsoft-Dokumentation
description: Verwenden der CrmServiceClient-Klasse, um Daten in Common Data Service zu erstellen
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: f6a03552-1f07-4d4b-b7ae-fa246a0d7c29
caps.latest.revision: 14
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 883577685cfcb0930484421d4ade4ba2e654abed
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154858"
---
# <a name="use-xrm-tooling-to-create-data"></a>Verwendung von XRM-Tooling zum Erstellen von Daten

Es gibt sieben Möglichkeiten, um in der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse neue Daten und Zuordnungen zu erstellen. Eine Erstellungsaktion mit der XRM-Tooling-API erfordert eine Datennutzlast. Die Datennutzlast hat die Gestalt eines `Dictionary<string, CrmDataTypeWrapper>`-Objekts. <xref:Microsoft.Xrm.Tooling.Connector.CrmDataTypeWrapper> wird verwendet, um der Schnittstelle mitzuteilen, welche Verarbeitung auf den Datenpunkt angewendet werden soll, auf den verwiesen wird. Einige der Methoden zum Erstellen von Daten werden in diesem Thema aufgelistet.  
  
## <a name="createnewrecord"></a>CreateNewRecord  

Diese Methode wird verwendet, um Entitätsdaten jedes Typs in Common Data Service zu erstellen. Um sie zu verwenden, müssen Sie den Schemanamen der Entität, in der Sie einen Datensatz erstellen möchten, können, und Sie müssen eine Datennutzlast für die Übergane erstellen. In diesem Beispiel wird ein Kontodatensatz erstellt.

```csharp
CrmServiceClient svc = new CrmServiceClient("connectionstring");  
// Verify that you are connected  
if (svc != null && svc.IsReady)  
{  
    // Create an account record  
    Dictionary<string, CrmDataTypeWrapper> inData = new Dictionary<string, CrmDataTypeWrapper>();  
    inData.Add("name", new CrmDataTypeWrapper("Sample Account Name", CrmFieldType.String));  
    inData.Add("address1_city", new CrmDataTypeWrapper("Redmond", CrmFieldType.String));  
    inData.Add("telephone1", new CrmDataTypeWrapper("555-0160", CrmFieldType.String));  
    accountId = ctrl.CrmConnectionMgr.svc.CreateNewRecord("account", inData);  
  
    // Verify if the account is created.  
    if (accountId != Guid.Empty)  
    {  
        Console.WriteLine(“Account created.”);  
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
In diesem Beispiel haben wir ein Datennutzlast-Objekt mit der Bezeichnung `indata` erstellt. Anschließend füllten wir es mit der allgemeinen Syntax: `crmFieldName , new CrmDataTypeWrapper(data,CrmFieldType)`. Nach der Einrichtung des `indata`-Objekts für die zu erstellenden Werte riefen wir die `CreateNewRecord`-Methode auf und gaben dabei den logischen Entitätsnamen für das Konto und die Daatennutzlast an (`indata`).  
  
> [!NOTE]
> Sie können einen Entitätsdatensatz auch mit XRM-Tooling durch Ausführung der <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest>-Meldung mit der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmOrganizationRequest*>-Methode erstellen. Weitere Informationen: [Nachrichten mit der ExecuteCrmOrganizationRequest-Methode verwenden](use-messages-executecrmorganizationrequest-method.md)  
  
## <a name="createannotation"></a>CreateAnnotation
  
Diese Methode wird verwendet, um ein Notizenobjekt zu erstellen und an einen Entitätsdatensatz anzuhängen. Während Sie alle Variablen für die Notiz im ersten Durchlauf eingeben können, müssen Sie nur die Felder für den Betreff und den Notizentext ausfüllen. In der Praxis wird dies allgemein verwendet, um systemgenerierte Notizen an eine Entität anzuhängen, oder um in Common Data Service gespeicherte Notizen an eine Entität anzuhängen. Wenn Sie Ihre eigene UI für die Generierung von Notizen für Ihren Benutzer angeben, ist dies auch die Weise, in der Sie die Notiz an die Eigentümerentität in Common Data Service anhängen. Dieses Beispiel setzt das vorherige Beispiel fort und erstellt eine Notiz zu dem neu erstellten Konto.  
  
```csharp
CrmServiceClient svc = new CrmServiceClient(connectionstring);  
  
// Verify that you are connected.  
if (svc != null && svc.IsReady)  
{  
    // Create and attach a note.  
    inData.Clear();   
    inData.Add("subject", new CrmDataTypeWrapper("This is a NOTE from the API" , CrmFieldType.String));
    inData.Add("notetext", new CrmDataTypeWrapper("This is text that will go in the body of the note" , CrmFieldType.String));  
    Guid noteID = svc.CreateAnnotation("account", accountId, inData);  
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
[Use XRM Tooling API to execute actions in Common Data Service](use-xrm-tooling-execute-actions.md)

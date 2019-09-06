---
title: XRM-Tooling zur Ausführung von Aktionen in Common Data Service verwenden | MicrosoftDocs
description: 'Ein Objekt der CrmServiceClient-Klasse kann verwendet werden, um Operationen mit Daten in Dynamics 365 zu erstellen, abzurufen, zu aktualisieren und zu löschen'
ms.custom: ''
ms.date: 03/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 72e9238d-e0fb-453b-b1ab-3a15ffb19838
caps.latest.revision: 13
ms.author: nabuthuk
manager: kvivek
author: Nkrb
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="use-xrm-tooling-to-execute-a-web-request-against-web-api"></a>Verwenden von XRM-Tooling, um eine Webanforderung anhand von Web-API auszuführen

Das Klassenobjekt <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> wird verwenden, um Aktionen mit Ihren Dynamics 365-Daten ausführen, z. B. Daten erstellen, aktualisieren, abrufen oder löschen.

Sie können jetzt die <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>--> Methode zum Ausführen einer Webanforderung anhand der XRM-Web-API.

Das folgende Codebeispiel demonstriert die Ausführung einer Webanforderung mithilfe von <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>--> Methode. 

>[!NOTE]
> Diese Methode gilt nur, wenn der Authentifizierungstyp als `OAuth` oder `Certificate` angegeben ist.

## <a name="create-a-record"></a>Erstellen eines Datensatzes

Das folgende Codebeispiel demonstriert, die Erstellung eines Datensatzes mithilfe von <!--<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest>--> Methode. Erstellen Sie in diesem Beispiel eine Firma und zeigen Sie dann im Antwortobjekt die ID an.  

```csharp
 Dictionary<string, List<string>> ODataHeaders = new Dictionary<string, List<string>>() {
        { "Accept", new List<string>() { "application/json" } },
        {"OData-MaxVersion", new List<string>(){"4.0"}},
        {"OData-Version", new List<string>(){"4.0"}}
      };

using (CrmServiceClient svc = new CrmServiceClient(conn))
 {
    if (svc.IsReady)
    {
      HttpResponseMessage response = svc.ExecuteCrmWebRequest(HttpMethod.Get, "accounts?$select=name", "{ \"name\":\"Test Account\"}", ODataHeaders, "application/json");

    if (response.IsSuccessStatusCode)
     {
        var accountUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();
        Console.WriteLine("Account URI: {0}", accountUri);
       }
    else
     {
       Console.WriteLine(response.ReasonPhrase);
        }

  }
    else
      {
        Console.WriteLine(svc.LastCrmError);
           }
}
```
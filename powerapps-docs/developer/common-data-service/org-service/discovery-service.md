---
title: Verwenden des Suchdienstes mit SDK Assemblys (Common Data Service) | Microsoft Docs
description: 'Beschreibt, wie Sie den Suchdienst mit .NET SDK-Assemblies verwenden können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-discovery-service-with-the-sdk-assemblies"></a>Verwenden Sie den Suchdienst mit SDK Assemblys

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]


Um den Suchdienst mit SDK Assemblys zu verwenden, fügen Sie einen Verweis auf die `Microsoft.Xrm.Sdk.dll`-Assembly Ihrem Visual Studio-Projekt hinzu, und dann ein `using`-Statement, um auf den <xref:Microsoft.Xrm.Sdk.Discovery>-Namespace zuzugreifen. 

Der <xref:Microsoft.Xrm.Sdk.Client.DiscoveryServiceProxy> implementiert die <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService>-Schnittstelle.

Die Schnittstelle <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService> bietet die Methode <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)>, mit der Sie eine Instanz der abstrakten Klasse <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> übergeben.

## <a name="regional-discovery-services"></a>Regionale Suchdienste

Wenn Sie den <xref:Microsoft.Xrm.Sdk.Client.DiscoveryServiceProxy> instanziieren, müssen Sie eine URL für ein regionales Rechenzentrum mit einem der folgenden Werte angeben.

[!INCLUDE [regional-discovery-services](../../../includes/regional-discovery-services.md)]

> [!NOTE]
> Wenn Sie die Region des Benutzers nicht kennen, müssen Sie die verfügbaren Regionen durchlaufen, bis Sie Ergebnisse erhalten. Die Web API bietet einen einzelnen globalen Suchdienst. Weitere Informationen: [Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API](../webapi/discover-url-organization-web-api.md)

## <a name="discovery-service-messages"></a>Suchdienstmeldungen

Es gibt drei Nachrichten, die Sie verwenden können, die alle von der abstrakten Klasse <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> erben.

 In der folgenden Tabelle werden die mit der <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)>-Methode unterstützten Meldungen aufgeführt:  
  
|Meldung|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveUserIdByExternalIdRequest>|Ruft die ID eines angemeldeten Benutzers in Common Data Service ab.|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationRequest>|Ruft Informationen zu einer einzelnen Organisation ab.|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest>|Ruft Informationen zu allen Organisationen ab, zu denen der Benutzer gehört.|  

## <a name="example"></a>Beispiel

Der folgende Code für eine Konsolenanwendung verwendet die Meldung <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest>, um alle Organisationen für einen Benutzer abzurufen.

```csharp
using System;
using System.Linq;
using Microsoft.Xrm.Sdk.Discovery;
using Microsoft.Xrm.Sdk.Client;
using System.ServiceModel.Description;

namespace DiscoveryServiceSample
{
  class Program
  {

    static OrganizationDetailCollection GetOrganizationDetails(DiscoveryServiceProxy svc)
    {

      var request = new RetrieveOrganizationsRequest()
      {
        AccessType = EndpointAccessType.Default,
        Release = OrganizationRelease.Current
      };
      try
      {
        var response = (RetrieveOrganizationsResponse)svc.Execute(request);
        return response.Details;
      }
      catch (Exception)
      {
        throw;
      }
    }
    static void Main(string[] args)
    {
      string canadaUrl = "https://disco.crm3.dynamics.com/XRMServices/2011/Discovery.svc";
      Uri discoveryUri = new Uri(canadaUrl);

      ClientCredentials creds = new ClientCredentials();
      creds.UserName.UserName = "you@yourorg.onmicrosoft.com";
      creds.UserName.Password = "yourPassword";

      using (var svc = new DiscoveryServiceProxy(discoveryUri, null, creds, null))
      {

        OrganizationDetailCollection details = GetOrganizationDetails(svc);

        details.ToList().ForEach(x =>
        {
          Console.WriteLine("Organization Name: {0}", x.FriendlyName);
          Console.WriteLine("Unique Name: {0}", x.UniqueName);
          Console.WriteLine("Endpoints:");
          foreach (var endpoint in x.Endpoints)
          {
            Console.WriteLine("  Name: {0}", endpoint.Key);
            Console.WriteLine("  URL: {0}", endpoint.Value);
          }
          Console.WriteLine();
        });
      };
      Console.ReadLine();
    }
  }
}

```

Die Ergebnisse können für einen Benutzer mit Zugriff auf zwei Instanzen so aussehen:

```
Organization Name: Organization A
Unique Name: orga
Endpoints:
  Name: WebApplication
  URL: https://orgaservice.crm3.dynamics.com/
  Name: OrganizationService
  URL: https://orgaservice.api.crm3.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgaservice.api.crm3.dynamics.com/XRMServices/2011/OrganizationData.svc

Organization Name: Organization B
Unique Name: orgb
Endpoints:
  Name: WebApplication
  URL: https://orgbservice.crm3.dynamics.com/
  Name: OrganizationService
  URL: https://orgbservice.api.crm3.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgbservice.api.crm3.dynamics.com/XRMServices/2011/OrganizationData.svc
```

> [!NOTE]
> Der `OrganizationDataService` ist der veraltete Organisationsdatendienst, nicht die Web API. Dieser Service enthält keine URL für die Web API.


### <a name="see-also"></a>Siehe auch

[Suchdienste](../discovery-service.md)<br />
[Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API.](../webapi/discover-url-organization-web-api.md)
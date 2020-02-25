---
title: Verwenden des Suchdienstes mit SDK Assemblies (Common Data Service) | Microsoft-Dokumentation
description: Beschreibt, wie Sie den Suchdienst mit den APIs verwenden können, die in SDK-Assemblies enthalten sind.
ms.custom: ''
ms.date: 1/16/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1eaf51018a94a226a5fa240a6f18f6107dc833dd
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2975685"
---
# <a name="use-the-discovery-service-with-the-sdk-assemblies"></a>Verwenden Sie den Suchdienst mit SDK Assemblys

> [!IMPORTANT]
> Ab dem 2. März 2020 wird der *regionale* Suchdienst [veraltet sein](/power-platform/important-changes-coming#regional-discovery-service-is-deprecated).
> 
> Informationen wie der Übergang zur Nutzung des *globalen* Suchdienstes erfolgt, finden Sie unter [Code ändern, um globalen Suchdienst zu verwenden](../webapi/discovery-orgsdk-to-webapi.md).

[!INCLUDE [cc-discovery-service-description](../includes/cc-discovery-service-description.md)]

Um den Suchdienst mit SDK Assemblys APIs zu verwenden, fügen Sie einen Verweis auf die `Microsoft.Xrm.Sdk.dll` Assembly in Ihrem Visual Studio Projekt hinzu, und fügen dann ein `using` Anweisung hinzu, um auf den <xref:Microsoft.Xrm.Sdk.Discovery> Namespace zuzugreifen.

Der <xref:Microsoft.Xrm.Sdk.WebServiceClient.DiscoveryWebProxyClient> implementiert die <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService>-Schnittstelle.

Die Schnittstelle <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService> bietet die Methode <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)>, mit der Sie eine Instanz der abstrakten Klasse <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> übergeben.

## <a name="regional-discovery-services"></a>Regionale Suchdienste

Wenn Sie den <xref:Microsoft.Xrm.Sdk.WebServiceClient.DiscoveryWebProxyClient> instanziieren, müssen Sie eine URL für ein regionales Rechenzentrum mit einem der folgenden Werte angeben.

[!INCLUDE [regional-discovery-services](../../../includes/regional-discovery-services.md)]

> [!NOTE]
> Wenn Sie die Region des Benutzers nicht kennen, müssen Sie die verfügbaren Regionen durchlaufen, bis Sie Ergebnisse erhalten. Ein einzelner globaler Suchdienst ist ebenfalls verfügbar. Weitere Informationen: [Ermitteln Sie die URL für Ihre Organisation](../webapi/discover-url-organization-web-api.md)

## <a name="discovery-service-messages"></a>Suchdienstmeldungen

Es gibt drei Nachrichten, die Sie verwenden können, die alle von der abstrakten Klasse <xref:Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest> erben.

 In der folgenden Tabelle werden die mit der <xref:Microsoft.Xrm.Sdk.Discovery.IDiscoveryService.Execute(Microsoft.Xrm.Sdk.Discovery.DiscoveryRequest)>-Methode unterstützten Meldungen aufgeführt:  
  
|Meldung|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveUserIdByExternalIdRequest>|Ruft die ID eines angemeldeten Benutzers in Common Data Service ab|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationRequest>|Ruft Informationen zu einer einzelnen Organisation ab.|  
|<xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest>|Ruft Informationen zu allen Organisationen ab, zu denen der Benutzer gehört.|  

## <a name="example"></a>Beispiel

Der folgende Code für eine Konsolenanwendung verwendet die Meldung <xref:Microsoft.Xrm.Sdk.Discovery.RetrieveOrganizationsRequest>, um alle Organisationen für einen Benutzer abzurufen.

```csharp
using System;
using System.Linq;
using Microsoft.Xrm.Sdk.Discovery;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Xrm.Sdk.WebServiceClient;

namespace DiscoveryServiceSample
{
    class Program
    {
        //These sample application registration values are available for all online instances.
        // this sample requires ADAL.net 5.2 + 
        public static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d";

        static OrganizationDetailCollection GetOrganizationDetails(DiscoveryWebProxyClient svc)
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
            string authority = @"https://login.microsoftonline.com/common";
            string northAmericaResourceUrl = "https://disco.crm.dynamics.com";
            string discoveryUrl = $"{northAmericaResourceUrl}/XRMServices/2011/Discovery.svc/web";
            Uri discoveryUri = new Uri(discoveryUrl);

            AuthenticationContext authContext = new AuthenticationContext(authority, false);
            string username = "you@yourorg.onmicrosoft.com";
            string password = "yourPassword"; 

            AuthenticationResult authResult = null;
            if (username != string.Empty && password != string.Empty)
            {
                UserPasswordCredential cred = new UserPasswordCredential(username, password);
                authResult = authContext.AcquireTokenAsync(northAmericaResourceUrl, clientId, cred).Result;
            }

           
            using (var svc = new DiscoveryWebProxyClient(discoveryUri))
            {
                svc.HeaderToken = authResult.AccessToken;

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
  URL: https://orgaservice.crm.dynamics.com/
  Name: OrganizationService
  URL: https://orgaservice.api.crm.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgaservice.api.crm.dynamics.com/XRMServices/2011/OrganizationData.svc

Organization Name: Organization B
Unique Name: orgb
Endpoints:
  Name: WebApplication
  URL: https://orgbservice.crm.dynamics.com/
  Name: OrganizationService
  URL: https://orgbservice.api.crm.dynamics.com/XRMServices/2011/Organization.svc
  Name: OrganizationDataService
  URL: https://orgbservice.api.crm.dynamics.com/XRMServices/2011/OrganizationData.svc
```

> [!NOTE]
> Der `OrganizationDataService` ist der veraltete Organisationsdatendienst, nicht die Web API. Dieser Service enthält keine URL für die Web API.


### <a name="see-also"></a>Siehe auch

[Suchdienste](../discovery-service.md)<br />
[Die URL für Ihre Organisation entdecken](../webapi/discover-url-organization-web-api.md)

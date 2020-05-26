---
title: 'Global Discovery Service-Beispiel (C #) (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie Sie über die OData V4 RESTful API auf den globalen Ermittlungsdienst zugreifen
ms.custom: ''
ms.date: 4/16/2020
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 86bda5aad070aadf68c587032c8a796b96d75eee
ms.sourcegitcommit: 223c3d19ec4fbe43fcc7a16b76423c00f8602ecd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "3266410"
---
# <a name="global-discovery-service-sample-c"></a>Globaler Discovery Service Beispiel (C#)

Dieses Beispiel zeigt, wie Sie über die OData V4 RESTful API auf den Ermittlungsdienst zugreifen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Dieses Beispiel ist auf Github verfügbar unter [https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery)

## <a name="what-this-sample-does"></a>Funktionsweise:

Dieses Beispiel gibt die verfügbaren Common Data Service-Instanzen für angegebene Benutzeranmeldeinformationen zurück.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Dieses Beispiel verwendeten Anmeldeinformationen in der verwendet App.config-Datei, aber nicht die URL, die in die Verbindungszeichenfolge konfiguriert ist. Stattdessen werden nur die Benutzeranmeldeinformationen und die Client-ID verwendet.

### <a name="demonstrates"></a>Demonstriert

Dieses Beispiel verwendet einen HttpClient zur Authentifizierung mit ADAL und ruft den Suchdienst auf, um Informationen über verfügbare Instanzen zurückzugeben, mit denen der Benutzer eine Verbindung herstellen kann.

Das Beispiel hängt von der `GetInstances` Methode und der `Instance` Klasse unten ab:

```csharp
/// <summary>
/// Uses the global discovery service to return environment instances
/// </summary>
/// <param name="username">The user name</param>
/// <param name="password">The password</param>
/// <returns>A list of Instances</returns>
static List<Instance> GetInstances(string username, string password)
{

    string GlobalDiscoUrl = "https://globaldisco.crm.dynamics.com/";
    HttpClient client = new HttpClient();
    client.DefaultRequestHeaders.Authorization = 
        new AuthenticationHeaderValue("Bearer", GetAccessToken(username, password, 
        new Uri("https://disco.crm.dynamics.com/api/discovery/")));
    client.Timeout = new TimeSpan(0, 2, 0);
    client.BaseAddress = new Uri(GlobalDiscoUrl);

    HttpResponseMessage response = 
        client.GetAsync("api/discovery/v2.0/Instances", HttpCompletionOption.ResponseHeadersRead).Result;

    if (response.IsSuccessStatusCode)
    {
        //Get the response content and parse it.
        string result = response.Content.ReadAsStringAsync().Result;
        JObject body = JObject.Parse(result);
        JArray values = (JArray)body.GetValue("value");

        if (!values.HasValues)
        {
            return new List<Instance>();
        }

        return JsonConvert.DeserializeObject<List<Instance>>(values.ToString());
    }
    else
    {
        throw new Exception(response.ReasonPhrase);
    }
}
```


```csharp
/// <summary>
  /// Object returned from the Discovery Service.
  /// </summary>
  class Instance
  {
    public string Id { get; set; }
    public string UniqueName { get; set; }
    public string UrlName { get; set; }
    public string FriendlyName { get; set; }
    public int State { get; set; }
    public string Version { get; set; }
    public string Url { get; set; }
    public string ApiUrl { get; set; }
    public DateTime LastUpdated { get; set; }
  }
```

                                                                                                                    '''
---
title: 'Global Discovery Service-Beispiel (C #) (Common Data Service) | Microsoft Docs'
description: Dieses Beispiel zeigt, wie Sie über die OData V4 RESTful API auf den globalen Ermittlungsdienst zugreifen
ms.custom: ''
ms.date: 1/16/2020
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
ms.openlocfilehash: c65092ed5b34bd06645e92f691cfe07ffc3eb233
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155014"
---
# <a name="global-discovery-service-sample-c"></a>Globaler Discovery Service Beispiel (C#)

Dieses Beispiel zeigt, wie Sie über die OData V4 RESTful API auf den Ermittlungsdienst zugreifen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Dieses Beispiel ist auf Github verfügbar unter [https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/GlobalDiscovery)

## <a name="what-this-sample-does"></a>Funktionsweise''
'' Dieses Beispiel gibt die verfügbaren Common Data Service-Instanzen für angegebene Benutzeranmeldeinformationen zurück.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Dieses Beispiel verwendeten Anmeldeinformationen in der verwendet App.config-Datei, aber nicht die URL, die in die Verbindungszeichenfolge konfiguriert ist.
Stattdessen wird es nur die Anmeldeinformationen und das clientid nutzen.
''''''''''''
### <a name="demonstrates"></a>Demonstriert

In diesem Beispiel wird ein HttpClient verwendet, um mithilfe von ADAL (v2.29) die Authentifizierung zu nutzen und den Globalen Ermittlungsdienst anzurufen, um die Informationen über verfügbare Instanzen anzurufen, mit der Benutzer eine Verbindung herstellen können.

Das Beispiel hängt von der `GetInstances` Methode und der `Instance` Klasse unten ab:

```csharp    
    /// <summary>
    /// Uses the Discovery Service to return organization instances.
    /// </summary>
    /// <param name="clientId">The Azure AD client (app) registration</param>
    /// <param name="username">The user name</param>
    /// <param name="password">The password</param>
    /// <returns>A List of Instances</returns>
    static List<Instance> GetInstances(string clientId, string username, string password)
    {

      string GlobalDiscoUrl = "https://globaldisco.crm.dynamics.com/";
      AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.com", false);

      UserCredential cred = new UserCredential(username, password);
      AuthenticationResult authResult = authContext.AcquireToken(GlobalDiscoUrl, clientId, cred);
'
      HttpClient client = new HttpClient();
      client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);
      client.Timeout = new TimeSpan(0, 2, 0);
      client.BaseAddress = new Uri(GlobalDiscoUrl);

      HttpResponseMessage response = client.GetAsync("api/discovery/v2.0/Instances", HttpCompletionOption.ResponseHeadersRead).Result;


      if (response.IsSuccessStatusCode)
      {
        //Get the response content and parse it.
        string result = response.Content.ReadAsStringAsync().Result;
        JObject body = JObject.Parse(result);
        JArray values = (JArray)body.GetValue("value");''

        if (!values.HasValues)
        {
          return new List<Instance>();
        }'

        return JsonConvert.DeserializeObject<List<Instance>>(values.ToString());
      }'
      else
      {
        throw new Exception(response.ReasonPhrase);
      }'
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
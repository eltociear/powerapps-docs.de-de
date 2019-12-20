---
title: 'Schnellstartbeispiel: Abrufen von Common Data Service-Umgebungen über die Online Management API| MicrosoftDocs'
description: Das C#-Beispiel zeigt, wie Sie sich gegenüber der Online Management API authentifizieren und dann alle Common Data Service-Umgebungen von Ihrem Office 365-Mandant abrufen können.
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: conceptual
ms.assetid: 63600a55-a1f0-491f-83f6-b3252566d27e
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
ms.openlocfilehash: 520079abf73c0367628de3bca01b316554b3af8c
ms.sourcegitcommit: 8f32eed48adf4b24b9ca607bbf6db3d19749c46f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "2830525"
---
# <a name="quick-start-sample-retrieve-common-data-service-environements-using-online-management-api"></a>Schnellstartbeispiel: Abrufen von Common Data Service-Umgebungen über die Online Management API 

Das C#-Beispiel zeigt, wie Sie sich gegenüber der Online Management API authentifizieren und dann alle Common Data Service-Umgebungen von Ihrem Office 365-Mandant abrufen können.

Das Hilfecodebeispiel verwendet die Authentifizierung [Helfercode](sample-authentication-helper.md), um die Online Management API mithilfe von OAuth 2.0 Protokoll einfach zu authentifizieren und den Zugriffstoken in der Kopfzeile der Anforderung zu übergeben.

## <a name="what-this-sample-does"></a>Was tut dieses Beispiel?

Das Beispiel führt die folgenden Aufgaben aus:

1. Verwendet die **ConnectToAPI**-Methode, um mit der Online Management API eine Verbindung herzustellen.

    a. Ruft die **DiscoverAuthority**-Methode Authentifizierungshilfecode auf und übergibt in die Service URL, um die Autoritätsinformationen abzurufen.

    b. Verwendet eine HttpClient-Instanz an, um mit dem Online Management API-Service eine Verbindung herzustellen.

    c. Gibt die API-Dienst-Basisadresse und den maximalen dem Zeitraum der Ausführungszeit an.
1. Verwendet **RetrieveInstancesAsync-Methode**, um eine HTTP-Anforderung auszuführen, um alle Customer Enagement-Instanzen im Office 365 Mandanten zu akquirieren und zeigt anschließend die Antwort an.

## <a name="run-this-sample"></a>Beispiel ausführen
Bevor Sie dieses Beispiel ausführen können, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Eine der Administratorrollen im Office 365 Mandanten. [Office 365 Administratorrollen](get-started-online-management-api.md#office-365-admin-roles)anzeigen
- Visual Studio 2015 oder höher; Internetkonnektivität ist erforderlich für das Herunterladen/Wiederherstellung von Assemblys im NuGet Paket.
- .NET Framework 4.6.2

Um das Beispiel auszuführen:
1. [Laden Sie herunter](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/online-management-api) das Beispiel, und extrahieren Sie es.
2. Doppelklicken Sie auf die Visual Studio-Lösungsdatei (.sln) unter dem C#-Ordner an der extrahierten Speicherort, um die Lösung in Visual Studio zu öffnen.
3. In der Datei **Programs.cs** geben Sie eine weitere URL Service an, wenn die Region nicht Nordamerika ist. Eine Liste der Service-URL-Werte für weltweite Regionen, siehe [Service-URL](get-started-online-management-api.md#service-url).
    ```csharp
    //TODO: Change this value if your Office 365 tenant is in a different region than North America

    private static string _serviceUrl = "https://admin.services.crm.dynamics.com";
    ```
4. In der Datei **HelperCode** > **AuthenticationHelper.cs** aktualisieren Sie die Werte von `_clientId` und `_redirectURL` entsprechend.

    ```csharp
    // TODO: Substitute your app registration values here.
    // These values are obtained on registering your application with the 
    // Azure Active Directory.
    private static string _clientId = "<GUID>";    //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    private static string _redirectUrl = "<Url>";  //e.g. "app://e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
    ```
5. Speichern Sie die Änderungen und starten Sie dann das Debugging, indem Sie F5 drücken oder wählen Sie **Debuggen** > **Debugging starten** aus.

## <a name="code-sample-listing"></a>Codebeispielliste 

Hier ist der vollständige Beispielcode:

```csharp
using Microsoft.Crm.Sdk.Samples.HelperCode;
using System;
using System.Net.Http;
using System.Threading.Tasks;


namespace Microsoft.Crm.Sdk.Samples
{
    /// <summary>
    /// This sample retrieves Customer Engagement instances
    /// in your Office 365 tenant.
    /// </summary>    

    class RetrieveInstances
    {
        private HttpClient httpClient;

        //TODO: Change this value if your Office 365 tenant is in a different region than North America
        private static string _serviceUrl = "https://admin.services.crm.dynamics.com";

        private void ConnectToAPI()
        {
            Console.WriteLine("Connecting to the Online Management API service...");

            // Discover authority for the Online Management API service
            var authority = Authentication.DiscoverAuthority(_serviceUrl);

            // Authenticate to the Online Management API service by 
            // passing in the discovered authority 
            Authentication auth = new Authentication(authority.Result.ToString());            

            // Use an HttpClient object to connect to Online Management API service.           
            httpClient = new HttpClient(auth.ClientHandler, true);

            // Specify the API service base address and the max period of execution time 
            httpClient.BaseAddress = new Uri(_serviceUrl);
            httpClient.Timeout = new TimeSpan(0, 2, 0);            
        }

        public async Task RetrieveInstancesAsync()
        {
            HttpRequestMessage myRequest = new HttpRequestMessage(HttpMethod.Get, "/api/v1.1/instances");
            HttpResponseMessage myResponse = await httpClient.SendAsync(myRequest);

            if (myResponse.IsSuccessStatusCode)
            {
                var result = myResponse.Content.ReadAsStringAsync().Result;
                Console.WriteLine("Your instances retrieved from Office 365 tenant: \n{0}", result);
            }
            else
            {
                Console.WriteLine("The request failed with a status of '{0}'",
                       myResponse.ReasonPhrase);
            }
        }

        static public void Main(string[] args)
        {
            RetrieveInstances app = new RetrieveInstances();
            try
            {
                // Connect to the Online Management API. 
                app.ConnectToAPI();

                // Run your request
                Task.WaitAll(Task.Run(async () => await app.RetrieveInstancesAsync()));
            }
            catch (System.Exception ex) { DisplayException(ex); }
            finally
            {
                if (app.httpClient != null)
                { app.httpClient.Dispose(); }
                Console.WriteLine("Press <Enter> to exit the program.");
                Console.ReadLine();
            }
        }

        /// <summary> Helper method to display exceptions </summary> 
        private static void DisplayException(Exception ex)
        {
            Console.WriteLine("The application terminated with an error.");
            Console.WriteLine(ex.Message);
            while (ex.InnerException != null)
            {
                Console.WriteLine("\t* {0}", ex.InnerException.Message);
                ex = ex.InnerException;
            }
        }
    }
}
```

### <a name="related-topics"></a>Verwandte Themen  

[Erste Schritte mitOnline Management API](get-started-online-management-api.md)

[Vorgänge, die von Online Management API unterstützt werden](operations-supported.md)

[Online Management API-Referenz](/rest/api/admin.services.crm.dynamics.com)

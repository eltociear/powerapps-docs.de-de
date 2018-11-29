---
title: 'Schnellstart: Web API-Beispiel (C#) (Common Data Service for Apps)| Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie Sie sich mit einem Common Data Service for Apps-Server authentifizieren und dann einen grundlegenden Web API-Vorgang aufrufen, die WhoAmI-Funktion.'
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
# <a name="quick-start-web-api-sample-c"></a>Schnellstart: Web API-Beispiel (C#)

In diesem Schnellstart erstellen Sie eine einfache Konsolenanwendung, um eine Verbindung mit Ihrer Common Data Service for Apps-Umgebung mithilfe der Web-API herzustellen.

Sie authentifizieren sich mithilfe von OAuth2 und verwenden [HttpClient](/dotnet/api/system.net.http.httpclient), um eine `GET`-Anforderung an die <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> zu senden. Die Antwort wird ein <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> sein. Sie zeigen den `UserId`-Eigenschaftswertwert an.

> [!NOTE]
> Dieses Schnellstartbeispiel enthält keine Fehlerbehandlung. Dies ist ein minimales Beispiel dafür, was Sie benötigen, um eine Verbindung mit der Web-API herzustellen und sie zu verwenden.

## <a name="prerequisites"></a>Voraussetzungen

 - Visual Studio (2017 empfohlen)
 - Internetverbindung
 - Gültiges Benutzerkonto für eine Common Data Service for Apps-Instanz
    - Ihr Benutzername
    - Ihr Kennwort
 - URL zur CDS for Apps-Umgebung, mit der Sie eine Verbindung herstellen möchten
 - Grundlegendes Verständnis der Visual C#-Sprache

> [!NOTE]
> Zum Authentifizieren mithilfe von OAuth2 müssen Sie eine App haben, die in Azure Active Directory registriert ist. Dieses Schnellstartbeispiel stellt einen App-Registrierungs-Clientid-Wert bereit, den Sie für die Ausführung von Beispielcode verwenden können, der von Microsoft veröffentlicht wurde. Für Ihre eigenen Anwendungen müssen Sie Ihre Apps registrieren. Weitere Informationen: [Exemplarische Vorgehensweise: Registrieren einer App bei Azure Active Directory](../walkthrough-register-app-azure-active-directory.md)

## <a name="create-visual-studio-project"></a>Erstellen eines Visual Studio-Projekts

1. Erstellen eines neuen Konsolen-App (.NET Framework)-Projekts mit .NET Framework 4.6.2

    ![Starten eines Konsolen-App-Projekts](../media/quick-start-web-api-console-app-csharp-1.png)

    > [!NOTE]
    > Dieser Screenshot zeigt den Namen `WebAPIQuickStart`an, aber Sie können für das Projekt und die Lösung einen beliebigen Namen auswählen. 

1. Klicken Sie in **Lösungs-Explorer** mit der rechten Maustaste auf das von Ihnen erstellte Projekt und wählen Sie im Kontextmenü **NuGet-Pakete verwalten...** aus.

    ![NuGet-Pakete hinzufügen](../media/quick-start-web-api-console-app-csharp-2.png)

1. Navigieren Sie zum `Microsoft.IdentityModel.Clients.ActiveDirectory` NuGet-Paket.
1. Wählen Sie **Version** 2.29.0 und installieren Sie sie.

    ![Installieren des Microsoft.IdentityModel.Clients.ActiveDirectory NuGet-Pakets](../media/quick-start-web-api-console-app-csharp-3.png)

    > [!IMPORTANT]
    > **Installieren Sie nicht die neueste Version dieses NuGet-Pakets.**
    >
    > Dieses Beispiel ist von der Fähigkeit zur Übergabe von Benutzeranmeldeinformationen ohne ein separates Azure-Anmeldungsdialogfeld abhängig, das in der Version 3.x dieser Bibliothek nicht verfügbar ist.

    > [!NOTE]
    > Sie müssen **Ich stimme zu** im Dialogfeld **Lizenz-Abnahme** auswählen.

1. Navigieren Sie zum `Newtonsoft.Json` NuGet-Paket und installieren Sie die aktuelle Version.

    ![Installieren des Microsoft.IdentityModel.Clients.ActiveDirectory NuGet-Pakets](../media/quick-start-web-api-console-app-csharp-4.png)

## <a name="edit-programcs"></a>Bearbeiten von Program.cs

1. Fügen Sie diese Using-Anweisungen am Anfang von `Program.cs` hinzu

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System.Net.Http.Headers;
    using System.Net.Http;
    using Newtonsoft.Json.Linq;
    ```

1. Ersetzen Sie die `Main`-Methode durch den folgenden Code:

    ```csharp
    static void Main(string[] args)
    {
        // Set these values:
        // e.g. https://yourorg.crm.dynamics.com
        string url = "<your environment url>";
        // e.g. you@yourorg.onmicrosoft.com
        string userName = "<your user name>";
        // e.g. y0urp455w0rd
        string password = "<your password>";

        // Azure Active Directory registered app clientid for Microsoft samples
        string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d";

        var userCredential = new UserCredential(userName, password);
        string apiVersion = "9.0";
        string webApiUrl = $"{url}/api/data/v{apiVersion}/";

        //Authenticate using IdentityModel.Clients.ActiveDirectory
        var authParameters = AuthenticationParameters.CreateFromResourceUrlAsync(new Uri(webApiUrl)).Result;
        var authContext = new AuthenticationContext(authParameters.Authority, false);
        var authResult = authContext.AcquireToken(url, clientId, userCredential);
        var authHeader = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

        using (var client = new HttpClient())
        {
            client.BaseAddress = new Uri(webApiUrl);
            client.DefaultRequestHeaders.Authorization = authHeader;

            // Use the WhoAmI function
            var response = client.GetAsync("WhoAmI").Result;

            if (response.IsSuccessStatusCode)
            {
                //Get the response content and parse it.  
                JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                Guid userId = (Guid)body["UserId"];
                Console.WriteLine("Your UserId is {0}", userId);
            }
            else
            {
                Console.WriteLine("The request failed with a status of '{0}'",
                            response.ReasonPhrase);
            }

            Console.WriteLine("Press any key to exit.");
            Console.ReadLine();
        }       
    }
    ```

1. Bearbeiten Sie die folgenden Werte, um Informationen für die Umgebung hinzuzufügen:

    ```csharp
    // e.g. https://yourorg.crm.dynamics.com
    string url = "<your environment url>";
    // e.g. you@yourorg.onmicrosoft.com
    string userName = "<your user name>";
    // e.g. y0urp455w0rd
    string password = "<your password>";
    ```

## <a name="run-the-program"></a>Ausführen des Programms

1. Drücken Sie F5, um das Programm auszuführen. Die Ausgabe sollte wie folgt aussehen:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

### <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich eine Verbindung mit der Web-API hergestellt.

<!-- TODO: Include link to next steps topics -->
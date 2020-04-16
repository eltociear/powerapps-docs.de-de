---
title: 'Schnellstart: Web-API-Beispiel (C#) (Common Data Service) | Microsoft-Dokumentation'
description: Dieses Beispiel veranschaulicht, wie Sie mit einem Common Data Service Server authentifizieren und dann einen grundlegenden Web-API-Vorgang, die WhoAmI-Funktion, aufrufen.
ms.custom: ''
ms.date: 02/02/2019
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 84ba00bfe3d634fcf4ad64e0447b6dc5dcb7d049
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155050"
---
# <a name="quick-start-web-api-sample-c"></a>Schnellstart: Web API-Beispiel (C#)

In diesem Schnellstart erstellen Sie eine einfache Konsolenanwendung, um eine Verbindung mit Ihrer Common Data Service-Umgebung mit Hilfe der Web-API herzustellen. 

Sie authentifizieren sich und verwenden eine <xref:System.Net.Http.HttpClient>, um eine `GET`-Anfrage an die <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> zu senden, die Antwort ist eine <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" />. Sie zeigen den Wert der Eigenschaft `UserId` an.

> [!NOTE]
> Dies ist ein sehr einfaches Beispiel, um zu zeigen, wie man mit einem Minimum an Code verbunden wird. Der folgende [Erweiterte Schnellstart](enhanced-quick-start.md) baut auf diesem Beispiel auf, um bessere Konstruktionsmuster anzuwenden.

## <a name="prerequisites"></a>Voraussetzungen

 - Visual Studio (2017 empfohlen)
 - Internetverbindung
 - Gültiges Benutzerkonto für eine Common Data Service-Instanz
    - Ihr Benutzername
    - Ihr Kennwort
 - URL zur Common Data Service-Umgebung, mit der Sie eine Verbindung herstellen möchten
 - Grundlegendes Verständnis der Visual C#-Sprache

> [!NOTE]
> Für die Authentifizierung müssen Sie eine App im Azure Active Directory registriert haben. Dieses Schnellstartbeispiel bietet einen Wert für die App-Registrierung `clientid`, den Sie verwenden können, um von Microsoft veröffentlichten Beispielcode auszuführen. Für Ihre eigenen Anwendungen müssen Sie Ihre Apps registrieren. Weitere Informationen: [Exemplarische Vorgehensweise: Registrieren einer App mit Azure Active Directory](../walkthrough-register-app-azure-active-directory.md)

## <a name="create-visual-studio-project"></a>Visual Studio-Projekt erstellen

1. Erstellen Sie ein neues Konsolen-App (.NET Framework) Projekt mit **.NET Framework 4.6.2**.

    ![Starten eines Konsolen-App-Projekts](../media/quick-start-web-api-console-app-csharp-1.png)

    > [!NOTE]
    > Dieser Screenshot zeigt den Namen `WebAPIQuickStart`an, aber Sie können für das Projekt und die Lösung einen beliebigen Namen auswählen.

    > [!IMPORTANT]
    > **Bekanntes Problem bei Visual Studio 2015**
    > 
    > Wenn Sie Ihr Projekt/Lösung in VS 2015 im Debug-Modus ausführen, können Sie möglicherweise keine Verbindung herstellen. Dies geschieht unabhängig davon, ob Sie ein Zielframework von 4.6.2 oder höher verwenden. Dies kann auftreten, weil der Visual Studio-Hostingprozess gegen .NET 4.5 kompiliert ist, was bedeutet, dass er standardmäßig TLS 1.2 nicht unterstützt. Sie können den Visual Studio-Hostingprozess als Umgehung deaktivieren. 
    >
    > Klicken Sie mit der rechten Maustaste auf den Namen Ihres Projekts in Visual Studio und dann auf **Eigenschaften**. Auf der Registerkarte **Debuggen** können Sie die Option **Visual Studio-Hostingprozess aktivieren** deaktivieren. 
    >
    > Dies wirkt sich nur auf das Debugging-Umgebung in VS 2015 aus. Es hat keinen Einfluss auf die erstellten Binärdateien bzw. ausführbaren Datei. Das gleiche Problem tritt nicht in Visual Studio 2017 auf.

1. Klicken Sie im **Lösungs-Explorer** mit der rechten Maustaste auf das von Ihnen erstellte Projekt und wählen Sie im Kontextmenü **NuGet-Pakete verwalten...** aus.

    ![NuGet-Paket hinzufügen](../media/quick-start-web-api-console-app-csharp-2.png)

1. Navigieren Sie zum `Microsoft.IdentityModel.Clients.ActiveDirectory` NuGet-Paket.
1. Wählen Sie **Version** 2.29.0 und installieren Sie sie.

    ![Installieren des Microsoft.IdentityModel.Clients.ActiveDirectory NuGet-Pakets](../media/quick-start-web-api-console-app-csharp-3.png)

    > [!IMPORTANT]
    > **Installieren Sie nicht die neueste Version dieses NuGet-Pakets.**
    >
    > Dieses Beispiel ist von der Fähigkeit zur Übergabe von Benutzeranmeldeinformationen ohne ein separates Azure-Anmeldungsdialogfeld abhängig, das in der Version 3.x dieser Bibliothek nicht verfügbar ist.

    > [!NOTE]
    > Sie müssen **Ich stimme zu** im Dialogfeld **Lizenz-Abnahme** auswählen.

1. Navigieren Sie zum `Newtonsoft.Json` NuGet-Paket und installieren Sie die neueste Version.

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
    Um den Wert `url` zu erhalten:

    1. Wählen Sie auf der [https://make.powerapps.com](https://make.powerapps.com)-Seite mit der entsprechenden Umgebung **Einstellungen** ![Schaltfläche Einstellungen](media/settings-icon.png) und wählen Sie **Erweiterte Anpassungen**. Wählen Sie dann **Entwicklerressourcen**.
    1. Suchen Sie auf der Seite **Entwicklerressourcen** nach dem Wert der **Instanzen-Web-API** und kopieren Sie ihn. 

        Es sollte in etwa so aussehen wie `https://yourorgname.api.crm.dynamics.com/api/data/v9.1/`. Aber für dieses Beispiel müssen Sie das letzte Teil (`/api/data/v9.1/`) so abschneiden, dass es nur `https://yourorgname.api.crm.dynamics.com` ist.

    Verwenden Sie für die Variablen `userName` und `password` die gleichen Anmeldeinformationen, die Sie auch für die Anmeldung bei der Website [https://make.powerapps.com](https://make.powerapps.com) verwendet haben.

## <a name="run-the-program"></a>Ausführen des Programms

1. Drücken Sie F5, um das Programm auszuführen. Die Ausgabe sollte wie folgt aussehen:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

### <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich eine Verbindung mit der Web-API hergestellt.

Das Schnellstart-Beispiel zeigt einen einfachen Ansatz zum Erstellen eines Visual Studio-Projekts ohne Ausnahmebehandlung oder Methode zum Aktualisieren des Zugriffstokens. 

Dies reicht aus, um zu überprüfen, ob Sie eine Verbindung herstellen können, aber es stellt kein gutes Muster für den Aufbau einer App dar.

Das Thema [Erweiterte Schnellstart](enhanced-quick-start.md) zeigt, wie man Methoden zur Behandlung von Ausnahmen implementiert, die Methode der grundlegenden Authentifizierung mit Hilfe von Verbindungszeichenketten, eine wiederverwendbare Methode zur Aktualisierung des Zugriffstokens und führt in die Erstellung von wiederverwendbaren Methoden zur Durchführung von Datenoperationen ein.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie Ihren Code für ein besseres Design strukturieren können.

> [!div class="nextstepaction"]
> [Verbesserter Schnellstart](enhanced-quick-start.md)<br/>

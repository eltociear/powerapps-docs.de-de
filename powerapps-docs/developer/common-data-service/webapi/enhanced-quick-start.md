---
title: Verbesserte Schnellstartfunktion (Common Data Service) | Microsoft Docs
description: 'Erstellen Sie ein neues Projekt in Visual Studio, um eine Konsolenanwendung zu unterstützen, die Common Data Service-Web-API verwendet'
ms.custom: ''
ms.date: 02/02/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 08377156-32c7-492a-8e66-50a47a330dc6
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
manager: ''
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="enhanced-quick-start"></a>Verbesserte Schnellstartfunktion

Dieses Thema zeigt, wie Sie den Code im [Schnellstartthema](quick-start-console-app-csharp.md) überarbeiten können, indem Sie wiederverwendbare <xref:System.Net.Http.HttpClient> und Fehlerbehandlungsmethoden hinzufügen. Führen Sie die Schritte im [Schnellstartthema](quick-start-console-app-csharp.md) aus, um ein neues Visual Studio-Projekt zu erstellen, bevor Sie mit diesem Thema beginnen.

## <a name="enable-passing-credentials-in-a-connection-string"></a>Aktivieren der Übergabe von Anmeldeinformationen in einer Verbindungszeichenfolge

Das Einfügen von Benutzeranmeldeinformationen in Ihren Code auf die gleiche Weise wie im [Schnellstartbeispiel](quick-start-console-app-csharp.md) ist keine gute Vorgehensweise. 

Wie Sie die Benutzeranmeldeinformationen erfassen, hängt von der Art des Clients ab, den Sie erstellen. Für diese Konsolenanwendung werden wir die Anmeldeinformationen innerhalb der `App.config` setzen, da es eine bequeme Möglichkeit ist, die Anmeldeinformationen aus dem Code zu verschieben. Es ist auch die Methode, die in den [Web-API-Datenoperationen Samples (C#)](web-api-samples-csharp.md) verwendet wird, so dass Sie, wenn Sie diese Methode verstehen, leicht sehen können, wie die verschiedenen Samples funktionieren.

Um dies zu ermöglichen, sind drei Schritte erforderlich:

1. [Referenz auf System.Configuration zum Visual Studio-Projekt hinzufügen](#1-add-reference-to-systemconfiguration-to-the-visual-studio-project)
1. [Bearbeiten der Anwendungskonfigurationsdatei](#2-edit-the-application-configuration-file)
1. [Hinzufügen mit Anweisung zur Program.cs](#3-add-using-statement-to-programcs)


### <a name="add-reference-to-systemconfiguration-to-the-visual-studio-project"></a>Referenz auf System.Configuration zum Visual Studio-Projekt hinzufügen

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Referenzen** und wählen Sie **Referenz hinzufügen...**.
1. Suchen Sie im Dialog **Referenzmanager** nach `System.Configuration` und aktivieren Sie das Kontrollkästchen, um diese Referenz zu Ihrem Projekt hinzuzufügen.
1. Klicken Sie auf **OK**, um das Dialogfeld **Reference Manager** zu schließen.
  
### <a name="edit-the-application-configuration-file"></a>Bearbeiten der Anwendungskonfigurationsdatei

Öffnen Sie im **Lösungs-Explorer** die Datei **App.config**. Sie sollte ungefähr so aussehen:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.2" />
    </startup>
</configuration>
```

Bearbeiten Sie das Element `<configuration>`, um einen Knoten `connectionStrings` hinzuzufügen, wie unten gezeigt:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.2" />
    </startup>
  <connectionStrings>
    <!--Online using Office 365-->
    <add name="Connect"
         connectionString="Url=https://yourorg.api.crm.dynamics.com;Username=yourname@yourorg.onmicrosoft.com;Password=y0urp455w0rd; />
  </connectionStrings>
</configuration>
```
Dadurch entsteht eine Verbindungszeichenfolge, die namentlich referenziert werden kann, in diesem Fall `Connect`, sodass Sie bei Bedarf mehr als eine Verbindung definieren können.

Bearbeiten Sie die Werte für die Verbindungszeichenfolge `Url`, `Username` und `Password` in der `connectionString` so, dass sie mit dem übereinstimmen, was Sie für die Verbindung zu Ihrer Common Data Service-Umgebung benötigen.

### <a name="add-using-statement-to-programcs"></a>Hinzufügen mit Anweisung zur Program.cs

Fügen Sie dies oben in Ihrer Program.cs-Datei mit der Anweisung hinzu:

```csharp
using System.Configuration;
```

## <a name="add-helper-code"></a>Helfercode hinzufügen

Im [Schnellstartbeispiel](quick-start-console-app-csharp.md) befindet sich der gesamte Code innerhalb der Datei `program.cs`. Wir werden den Code, der sich mit dem Verbinden und Erstellen einer <xref:System.Net.Http.HttpClient> beschäftigt, in eine separate Datei mit Hilfsmethoden verschieben. 

Diese Helfer werden auch in der [SampleHelper.cs](https://github.com/Microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/SampleHelpers.cs) verwendet, die von den [Web-API-Datenoperationen Samples (C#)](web-api-samples-csharp.md) verwendet wird. Wenn Sie diese Helfer verstehen, werden Sie verstehen, wie sie in den Proben verwendet werden.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Ihr Projekt und wählen Sie **Add** > **Class...** (oder drücken Sie `Shift`+`Alt`+`C`), um das Dialogfenster **Neues Element hinzufügen** zu öffnen.
1. Geben Sie einen Namen für Ihre Klasse an. Um dem Muster zu folgen, das von den [Web-API-Datenoperationen Samples (C#)](web-api-samples-csharp.md) verwendet wird, nennen Sie es `SampleHelpers.cs`. 

    > [!NOTE]
    > Der Name der Klasse bestimmt, wie Sie auf diese Hilfseigenschaften und Methoden innerhalb Ihrer `Program.cs` verweisen. Die restlichen Anweisungen erwarten, dass Sie es `SampleHelpers` genannt haben, also denken Sie daran, wenn Sie es anders benannt haben.

1. Fügen Sie die folgenden `using`-Statements hinzu:

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    using System;
    using System.Linq;
    using System.Net.Http;
    using System.Net.Http.Headers;
    using System.Threading.Tasks;
    ```

1. Füge die folgenden Eigenschaften und Methoden zu deiner `SampleHelper`-Klasse hinzu:

    ```csharp
    //These sample application registration values are available for all online instances.
    //You can use these while running sample code, but you should get your own for your own apps
    public static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d";
    public static string redirectUrl = "app://58145B91-0C36-4500-8554-080854F2AC97";

    /// <summary>
    /// Method used to get a value from the connection string
    /// </summary>
    /// <param name="connectionString"></param>
    /// <param name="parameter"></param>
    /// <returns>The value from the connection string that matches the parameter key value</returns>
    public static string GetParameterValueFromConnectionString(string connectionString, string parameter)
    {
      try
      {
        return connectionString.Split(';').Where(s => s.Trim().StartsWith(parameter)).FirstOrDefault().Split('=')[1];
      }
      catch (Exception)
      {
        return string.Empty;
      }
    }

    /// <summary>
    /// Returns an HttpClient configured with an OAuthMessageHandler
    /// </summary>
    /// <param name="connectionString">The connection string to use.</param>
    /// <param name="clientId">The client id to use when authenticating.</param>
    /// <param name="redirectUrl">The redirect Url to use when authenticating</param>
    /// <param name="version">The version of Web API to use. Defaults to version 9.1 </param>
    /// <returns>An HttpClient you can use to perform authenticated operations with the Web API</returns>
    public static HttpClient GetHttpClient(string connectionString, string clientId, string redirectUrl, string version = "v9.1")
    {
      string url = GetParameterValueFromConnectionString(connectionString, "Url");
      string username = GetParameterValueFromConnectionString(connectionString, "Username");
      string password = GetParameterValueFromConnectionString(connectionString, "Password");
      try
      {
        HttpMessageHandler messageHandler = new OAuthMessageHandler(url, clientId, redirectUrl, username, password,
                      new HttpClientHandler());

        HttpClient httpClient = new HttpClient(messageHandler)
        {
          BaseAddress = new Uri(string.Format("{0}/api/data/{1}/", url, version)),

          Timeout = new TimeSpan(0, 2, 0)  //2 minutes
        };

        return httpClient;
      }
      catch (Exception)
      {
        throw;
      }
    }

    /// <summary> Displays exception information to the console. </summary>
    /// <param name="ex">The exception to output</param>
    public static void DisplayException(Exception ex)
    {
      Console.WriteLine("The application terminated with an error.");
      Console.WriteLine(ex.Message);
      while (ex.InnerException != null)
      {
        Console.WriteLine("\t* {0}", ex.InnerException.Message);
        ex = ex.InnerException;
      }
    }
    ```

1. Füge die Klasse `OAuthMessageHandler` innerhalb des Namensraums deiner Datei `SampleHelpers.cs` hinzu.

    > [!NOTE]
    > Fügen Sie dies nicht innerhalb der Klasse `SampleHelpers` selbst hinzu.

    Diese Klasse stellt sicher, dass das Zugriffstoken bei jeder Ausführung einer Aktion aktualisiert wird. Jeder Zugriffstoken verfällt nach etwa einer Stunde. Diese Klasse implementiert eine <xref:System.Net.Http.DelegatingHandler>, die mit dem Authentifizierungskontext der Azure Active Directory Authentication Library (ADAL) funktioniert, um die Methode `AquireToken` jedes Mal aufzurufen, wenn eine Operation ausgeführt wird, so dass Sie den Ablauf von Token nicht explizit verwalten müssen.

    ```csharp
    /// <summary>
    ///Custom HTTP message handler that uses OAuth authentication thru ADAL.
    /// </summary>
    class OAuthMessageHandler : DelegatingHandler
    {
      private AuthenticationHeaderValue authHeader;

      public OAuthMessageHandler(string serviceUrl, string clientId, string redirectUrl, string username, string password,
              HttpMessageHandler innerHandler)
          : base(innerHandler)
      {
        // Obtain the Azure Active Directory Authentication Library (ADAL) authentication context.
        AuthenticationParameters ap = AuthenticationParameters.CreateFromResourceUrlAsync(
                new Uri(serviceUrl + "/api/data/")).Result;
        AuthenticationContext authContext = new AuthenticationContext(ap.Authority, false);
        //Note that an Azure AD access token has finite lifetime, default expiration is 60 minutes.
        AuthenticationResult authResult;
        if (username != string.Empty && password != string.Empty)
        {

          UserCredential cred = new UserCredential(username, password);
          authResult = authContext.AcquireToken(serviceUrl, clientId, cred);
        }
        else
        {
          authResult = authContext.AcquireToken(serviceUrl, clientId, new Uri(redirectUrl), PromptBehavior.Auto);
        }

        authHeader = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);
      }

      protected override Task<HttpResponseMessage> SendAsync(
                HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)
      {
        request.Headers.Authorization = authHeader;
        return base.SendAsync(request, cancellationToken);
      }
    }
    ```

## <a name="update-programcs"></a>Program.cs aktualisieren

Nachdem Sie nun die Änderungen an [Enable passing credentials in a connection string](#enable-passing-credentials-in-a-connection-string) und [Add helper code](#add-helper-code) vorgenommen haben, können Sie die Methode `Main` in Ihrer `Program.cs` aktualisieren, um nur Folgendes zu enthalten:

```csharp
static void Main(string[] args)
{
  try
  {
    //Get configuration data from App.config connectionStrings
    string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

    using (HttpClient client = SampleHelpers.GetHttpClient(connectionString, SampleHelpers.clientId, SampleHelpers.redirectUrl))
    {
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
  catch (Exception ex)
  {
    SampleHelpers.DisplayException(ex);
    Console.WriteLine("Press any key to exit.");
    Console.ReadLine();
  }
}
```

Dies ist weniger Code und Sie haben eine Fehlerbehandlung und die Möglichkeit hinzugefügt, das Zugriffstoken bei jeder Verwendung der `HttpClient` zu aktualisieren.

Drücken Sie F5, um das Programm auszuführen. Genau wie das [Schnellstartbeispiel](quick-start-console-app-csharp.md) sollte die Ausgabe so aussehen:

    ```
    Your UserId is 969effb0-98ae-478c-b547-53a2968c2e75
    Press any key to exit.
    ```

## <a name="create-re-usable-methods"></a>Erstellen von wiederverwendbaren Methoden

Während wir die Gesamtmenge des Codes in der Methode `Program.cs` `main` reduziert haben, werden Sie kein Programm schreiben, um nur eine Operation aufzurufen, und es ist nicht realistisch, so viel Code zu schreiben, nur um eine einzelne Operation aufzurufen.

Dieser Abschnitt zeigt, wie Sie dies ändern können:

  ```csharp
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
  ```
für dies:

  ```csharp
  WhoAmIResponse response = WhoAmI(client);
        Console.WriteLine("Your system user ID is: {0}", response.UserId);
  ```

Bevor Sie beginnen, ist es eine gute Idee, die Web-API-Referenz aufzurufen und diese Themen zu überprüfen:
- <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> 
- <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" />

Beachten Sie, wie die <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> eine <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> zurückgibt und die <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> drei `GUID` Eigenschaften enthält: `BusinessUnitId`, `UserId` und `OrganizationId`;

Der Code, den wir hinzufügen werden, besteht einfach darin, diese in eine wiederverwendbare Methode zu modellieren, die eine `HttpClient` als Parameter akzeptiert.

> [!NOTE]
> Wie Sie das genau machen, ist eine Frage der persönlichen Präferenz. Dieses Design wird wegen seiner relativen Einfachheit angeboten.

Führen Sie in Ihrem Visual Studio-Projekt die folgenden Schritte aus:

1. Bearbeiten Sie die Klasse `Program`, um sie zu einer Teilklasse zu machen.

    Oben angekommen, ändern Sie dies:

    `class Program`

    Und profitieren Sie von:

    `partial class Program`

1. Erstellen Sie eine neue Klasse mit dem Namen `ProgramMethods.cs`.

    Ändern Sie dies unter `ProgramMethods.cs`:

    `class ProgramMethods`

    Und profitieren Sie von:

    `partial class Program`

    Auf diese Weise ist die Klasse `Program` in der Datei `ProgramMethods.cs` nur eine Erweiterung der ursprünglichen Klasse `Program` in der Datei `Program.cs`. 

1. Fügen Sie die folgenden Anweisungen mit Hilfe von Anweisungen an den Anfang der Datei `ProgramMethods.cs` ein.

    ```csharp
    using Newtonsoft.Json.Linq;
    using System;
    using System.Net.Http;
    ```

1. Fügen Sie die folgende Methode zur Klasse `Program` in der Datei `ProgramMethods.cs` hinzu.

    ```csharp
    public static WhoAmIResponse WhoAmI(HttpClient client) {
      WhoAmIResponse returnValue = new WhoAmIResponse();
      //Send the WhoAmI request to the Web API using a GET request. 
      HttpResponseMessage response = client.GetAsync("WhoAmI",
              HttpCompletionOption.ResponseHeadersRead).Result;
      if (response.IsSuccessStatusCode)
      {
          //Get the response content and parse it.
          JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
          returnValue.BusinessUnitId = (Guid)body["BusinessUnitId"];
          returnValue.UserId = (Guid)body["UserId"];
          returnValue.OrganizationId = (Guid)body["OrganizationId"];
      }
      else
      {
          throw new Exception(string.Format("The WhoAmI request failed with a status of '{0}'",
                  response.ReasonPhrase));
      }
      return returnValue;
    }
    ```

1. Füge die folgende Klasse außerhalb der Klasse `Program` hinzu, aber innerhalb des Namensraums der Datei `ProgramMethods.cs`.

    ```csharp
    public class WhoAmIResponse
    {
        public Guid BusinessUnitId { get; set; } 
        public Guid UserId { get; set; }
        public Guid OrganizationId { get; set; }
    }
    ```

1. Bei der Methode `Program` `main` in der Originaldatei `Program.cs`:

    Ersetzen Sie dies:

    ```csharp
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
    ```
    Damit:

    ```csharp
    WhoAmIResponse response = WhoAmI(client);
    Console.WriteLine("Your system user ID is: {0}", response.UserId);
    ```

1. Drücken Sie F5, um das Beispiel auszuführen, und Sie sollten die gleichen Ergebnisse wie zuvor erhalten.


## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme beim Ausführen dieser Samples haben, können Sie alle PowerApps-Beispiele aus dem GitHub-Repository unter [https://github.com/Microsoft/PowerApps-Samples](https://github.com/Microsoft/PowerApps-Samples) herunterladen.

Dieses Beispiel basiert auf der [SimpleWebApi](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/SimpleWebApi) im Ordner `PowerApps-Samples-master\PowerApps-Samples-master\cds\webapi\C#\SimpleWebApi`.

Sie sollten in der Lage sein, die Datei `SimpleWebApi.sln` in Visual Studio zu öffnen und das Sample auszuführen. Es sollte für Sie funktionieren, solange Sie über gültige Zugangsdaten verfügen.

> [!IMPORTANT]
> Alle Beispiele auf dem GitHub Repo sind so konfiguriert, dass sie eine gemeinsame App.config verwenden, die sich bei `PowerApps-Samples-master\cds\App.config` befindet. Wenn Sie Ihre Verbindungszeichenfolge festlegen, müssen Sie diese Datei bearbeiten. Wenn Sie dies tun, können Sie alle Samples ausführen, ohne Ihre Anmeldeinformationen erneut festzulegen.

## <a name="create-a-template-project"></a>Erstellen eines Template-Projekts

Bevor Sie das Thema verlassen, sollten Sie darüber nachdenken, das Projekt als Projektvorlage zu speichern. Sie können die Vorlage dann wieder für zukünftige Lernprojekte verwenden und sich etwas Zeit und Aufwand bei der Erstellung neue Projekte ersparen. Wählen Sie dazu im Menü **Datei** die Option **Exportvorlage**, aus, während das Projekt in Microsoft Visual Studio geöffnet ist. Befolgen Sie Anweisungen des [Vorlagenexportassistenten](https://docs.microsoft.com/visualstudio/ide/how-to-create-project-templates) zum Erstellen der Vorlage.  
  
## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie die folgenden Ressourcen, um mehr zu erfahren:

> [!div class="nextstepaction"]
> [Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br /><br />
> [Probieren Sie Web API Datenoperationen Beispiele (C#)](web-api-samples-csharp.md)<br /><br />
> [Überprüfung von Web-API-Beispielen (C#) auf GitHub](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23)


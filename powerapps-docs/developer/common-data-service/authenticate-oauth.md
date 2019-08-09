---
title: Verwendung von OAuth mit Common Data Service (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie, wie Sie die Authentifizierung mit OAuth mit dem Common Data Service durchführen können'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-oauth-with-common-data-service"></a>OAuth mit Common Data Service verwenden

[OAuth 2.0](https://oauth.net/2/) ist das branchenübliche Protokoll für die Autorisierung. Nachdem die Personen Anmeldeinformationen zur Authentifizierung bereitgestellt haben, stellt OAuth fest, ob sie berechtigt sind, auf die Ressourcen zuzugreifen.

Client-Anwendungen müssen die Verwendung von OAuth für den Datenzugriff über die Web-API unterstützen. OAuth ermöglicht eine Zwei-Faktor-Authentifizierung (2FA) oder eine zertifikatsbasierte Authentifizierung für Server-zu-Server-Anwendungsszenarien.

OAuth benötigt für die Authentifizierung einen Identitätsanbieter. Für Common Data Service ist der Identitätsanbieter Azure Active Directory (AAD). Um sich mit AAD über ein Microsoft-Arbeits- oder Schulkonto zu authentifizieren, verwenden Sie die Azure Active Directory Authentication Libraries (ADAL).

> [!NOTE]
> In diesem Thema werden allgemeine Konzepte für die Anbindung an Common Data Service mit OAuth mit den ADAL-Bibliotheken vorgestellt. Dieser Inhalt konzentriert sich darauf, wie ein Entwickler eine Verbindung zu Common Data Service herstellen kann, nicht aber auf die Funktionsweise von OAuth oder den ADAL-Bibliotheken. Ausführliche Informationen zur Authentifizierung finden Sie in der Azure Active Directory-Dokumentation. [Was ist Authentifizierung](/azure/active-directory/develop/authentication-scenarios) ist ein guter Ausgangspunkt.
>
>Die von uns zur Verfügung gestellten Muster sind mit entsprechenden Registrierungswerten vorkonfiguriert, so dass Sie sie ohne Generierung einer eigenen App-Registrierung ausführen können. Wenn Sie eigene Apps veröffentlichen, müssen Sie eigene Registrierungswerte verwenden.

## <a name="app-registration"></a>App-Registrierung

Wenn Sie sich über OAuth verbinden, müssen Sie zunächst eine Anwendung in Ihrem Azure AD-Mandant registrieren. Wie Sie Ihre App registrieren sollten, hängt von der Art der App ab, die Sie erstellen möchten.

Beginnen Sie in allen Fällen mit den grundlegenden Schritten zur Registrierung einer App, die im AAD-Thema beschrieben ist: [Schnellstart: Registrieren einer App mit dem Azure Active Directory v1.0-Endpunkt](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app). Für spezifische Common Data Service-Anweisungen siehe [Exemplarische Vorgehensweise: Registrieren einer App bei Azure Active Directory > Erstellen einer Anwendungsregistrierung](walkthrough-register-app-azure-active-directory.md#create-an-application-registration).

Die Entscheidungen, die in diesem Schritt treffen müssen, hängt größtenteils von der Wahl des Anwendungstyps ab.

### <a name="types-of-app-registration"></a>Arten der App-Registrierung

Wenn Sie eine App bei Azure AD registrieren, ist eine der Entscheidungen, die Sie treffen müssen, der Anwendungstyp. Es gibt zwei Arten von Anwendungen, die Sie registrieren können:

|Anwendungstyp|Beschreibung|
|--|--|
|Web-App / API|**Webclient**<br />Eine Art von [Client-Anwendung](/azure/active-directory/develop/developer-glossary#client-application), die den gesamten Code auf einem Webserver ausführt.<br /><br />**Benutzer-Agent-basierter Client**<br />Ein Typ von [Client-Anwendung](/azure/active-directory/develop/developer-glossary#client-application), der Code von einem Webserver herunterlädt und innerhalb eines Benutzeragenten (z.B. eines Webbrowsers) ausgeführt wird, wie beispielsweise eine Single Page Application (SPA). 
|
|einheitlich|EinTyp von [Client-Anwendung](/azure/active-directory/develop/developer-glossary#client-application), der nativ auf einem Gerät installiert wird. |

Wenn Sie **Web-App / API** auswählen, müssen Sie eine **Anmelde-URL** angeben, die die URL ist, unter der Azure AD die Authentifizierungsantwort sendet, einschließlich eines Token, wenn die Authentifizierung erfolgreich war. Während Sie eine App entwickeln, ist diese in der Regel auf `http://localhost/appname:[port]` gesetzt, so dass Sie Ihre App lokal entwickeln und debuggen können. Wenn Sie Ihre App veröffentlichen, müssen Sie diesen Wert auf die veröffentlichte URL der App ändern.

Wenn Sie **Native** wählen, müssen Sie eine Umleitungs-URI bereitstellen. Dies ist eine eindeutige Kennung, an die Azure AD den Benutzer-Agenten in einer OAuth 2.0-Anfrage weiterleitet. Dies ist normalerweise ein Wert, der so formatiert ist: `//app:<guid>`. 

### <a name="giving-access-to-common-data-service"></a>Zugriff gewähren auf Common Data Service

Wenn Ihre Anwendung ein Client ist, der es dem authentifizierten Benutzer ermöglicht, Operationen auszuführen, müssen Sie die Anwendung so konfigurieren, dass die Access Dynamics 365 als Berechtigung von Organisationsbenutzern vergeben wird.

Konkrete Schritte hierzu finden Sie unter [Exemplarische Vorgehensweise: Registrieren einer App bei Azure Active Directory > Berechtigungen anwenden](walkthrough-register-app-azure-active-directory.md#apply-permissions).

<!-- TODO Verify this -->
 Wenn Ihre Anwendung die Server-zu-Server (S2S)-Authentifizierung verwendet, ist dieser Schritt nicht erforderlich. Diese Konfiguration erfordert einen bestimmten Systembenutzer, und die Operationen werden von diesem Benutzerkonto und nicht von jedem Benutzer durchgeführt, der authentifiziert werden muss.

### <a name="enable-implicit-flow"></a>Impliziten Fluss aktivieren

Wenn Sie eine App für eine Single Page Application (SPA) konfigurieren, müssen Sie das Manifest bearbeiten, um den `oauth2AllowImplicitFlow`-Wert auf `true` zu setzen. Mehr Informationen: [Exemplarische Vorgehensweise: Registrierung und Konfiguration einer SPA-Anwendung mit adal.js](walkthrough-registering-configuring-simplespa-application-adal-js.md)

### <a name="use-client-secrets--certificates"></a>Verwenden von geheimen Clientschlüsseln und Zertifikaten

Für Server-zu-Server-Szenarien wird es kein interaktives Benutzerkonto zur Authentifizierung geben. In diesen Fällen müssen Sie einige Mittel bereitstellen, um zu bestätigen, dass die Anwendung vertrauenswürdig ist. Dies geschieht über geheime Clientschlüssel oder Zertifikate.

Für Apps, die mit dem Applikationstyp **Web App /API** registriert sind, können Sie Geheimnisse konfigurieren. Diese werden über den Bereich **Schlüssel** unter **API Zugriff** in den **Einstellungen** für die App-Registrierung eingestellt. 

Für beide Anwendungsarten können Sie ein Zertifikat hochladen.

Weitere Informationen: [Als App verbinden](#connect-as-an-app)

## <a name="use-adal-libraries-to-connect"></a>Verwenden Sie ADAL-Bibliotheken, um eine Verbindung herzustellen.

Verwenden Sie eine der von Microsoft unterstützten Azure Active Directory Authentication Libraries (ADAL) Client-Bibliotheken. [Azure Active Directory Authentication Libraries > Von Microsoft unterstützte Client-Bibliotheken](/azure/active-directory/develop/active-directory-authentication-libraries#microsoft-supported-client-libraries).

Diese Bibliotheken sind für verschiedene Plattformen verfügbar, wie in der folgenden Tabelle dargestellt:

|Plattform|Bibliothek|
|--|--|
|.NET-Client, Windows Store, UWP, Xamarin |ADAL .NET v3|
|.NET-Client, Windows Store, Windows Phone 8.1|ADAL .NET v2|
|JavaScript|ADAL.js|
|iOS, macOS|ADAL|
|Android|ADAL|
|Node.js|ADAL|
|Java|ADAL4J|
|Python|ADAL|

> [!NOTE]
> Derzeit verwenden alle unsere Beispiele die.NET-Client-Bibliotheken, mit Ausnahme von [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung zu verbinden](oauth-cross-origin-resource-sharing-connect-single-page-application.md), die die JavaScript ADAL.js Library verwendet.

## <a name="adal-net-client-library-versions"></a>ADAL .NET Client-Bibliotheksversionen

Es gibt zwei Bibliotheken, die .NET-Clients unterstützen. Die ADAL .NET v3 Bibliothek ist die neueste, ersetzt aber nicht die ADAL.NET v2 Bibliothek.

> [!IMPORTANT]
> Wenn Sie Xrm.Tooling für .NET Framework-Anwendungen verwenden, müssen Sie die ADAL.NET v2-Bibliothek verwenden.

Einer der wesentlichen Unterschiede zwischen den .NET Client-Versionen besteht darin, dass die v2-Bibliothek die Unterstützung für die Übergabe von Benutzeranmeldeinformationen bietet. Die v3-Bibliothek verlangt, dass Benutzeranmeldeinformationen interaktiv über ein Browser-Popup erfasst werden.

Wenn Sie Xrm.Tooling nicht verwenden, können Sie die ADAL.NET v2 oder v3 Client-Bibliotheken mit der Web-API verwenden. Ein Beispiel für die Verwendung der v3-Client-Bibliothek finden Sie unter : [ADAL v3 WhoAmI sample](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/ADALV3WhoAmI/ADALV3WhoAmI).

## <a name="use-the-accesstoken-with-your-requests"></a>Verwenden Sie den AccessToken für Ihre Anfragen.

Der Sinn der Verwendung der ADAL-Bibliotheken besteht darin, ein Token zu erhalten, das Sie in Ihre Anfragen aufnehmen können. Dies erfordert nur ein paar Zeilen Code und nur ein paar weitere Zeilen, um einen HttpClient zur Ausführung einer Anfrage zu konfigurieren.

### <a name="simple-example"></a>Ein einfaches Beispiel

Im Folgenden finden Sie die Mindestmenge an Code, die benötigt wird, um eine einzelne Web-Api-Anfrage auszuführen, aber es ist nicht der empfohlene Ansatz:

```csharp
class SampleProgram
{
    private static string serviceUrl = "https://yourorg.crm.dynamics.com"; 
    private static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d"; 
    private static string userName = "you@yourorg.onmicrosoft.com";
    private static string password = "yourpassword";

    static void Main(string[] args)
    {

        AuthenticationContext authContext = 
        new AuthenticationContext("https://login.microsoftonline.com/common", false);  
        UserCredential credential = new UserCredential(userName, password);
        AuthenticationResult result = authContext.AcquireToken(serviceUrl, clientId, credential);
        //The access token
        string accessToken = result.AccessToken;

        using (HttpClient client = new HttpClient()) {
        client.BaseAddress = new Uri(serviceUrl);
        client.Timeout = new TimeSpan(0, 2, 0);  //2 minutes  
        client.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");
        client.DefaultRequestHeaders.Add("OData-Version", "4.0");
        client.DefaultRequestHeaders.Accept.Add(
            new MediaTypeWithQualityHeaderValue("application/json"));
        HttpRequestMessage request = 
            new HttpRequestMessage(HttpMethod.Get, "/api/data/v9.0/WhoAmI");
        //Set the access token
        request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);
        HttpResponseMessage response = client.SendAsync(request).Result;
        if (response.IsSuccessStatusCode)
        {
            //Get the response content and parse it.  
            JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
            Guid userId = (Guid)body["UserId"];
            Console.WriteLine("Your system user ID is: {0}", userId);
        }

    }
}
```

Dieser einfache Ansatz stellt kein gutes Muster dar, da der `AccessToken` in etwa einer Stunde abläuft. ADAL-Bibliotheken speichern den Token für Sie und aktualisieren ihn bei jedem Aufruf der `AcquireToken`-Methode.

### <a name="example-demonstrating-a-delegatinghandler"></a>Beispiel zur Demonstration eines DelegatingHandlers

Der empfohlene Ansatz ist die Implementierung einer von <xref:System.Net.Http.DelegatingHandler> abgeleiteten Klasse, die an den Konstruktor des <xref:System.Net.Http.HttpClient> übergeben wird. Dieser Handler ermöglicht es Ihnen, die <xref:System.Net.Http.HttpClient>.<xref:System.Net.Http.HttpClient.SendAsync*> zu überschreiben. Methode, so dass ADAL die `AcquireToken`-Methode mit jeder vom http-Client gesendeten Anforderung aufruft.

Das Folgende ist ein Beispiel für eine benutzerdefinierte Klasse, die von <xref:System.Net.Http.DelegatingHandler> abgeleitet ist.

```csharp
  /// <summary>  
  ///Custom HTTP message handler that uses OAuth authentication thru ADAL.  
  /// </summary>  
  class OAuthMessageHandler : DelegatingHandler
  {
    private UserCredential _credential;
    private AuthenticationContext _authContext = 
      new AuthenticationContext("https://login.microsoftonline.com/common", false);
    private string _clientId;
    private string _serviceUrl;

    public OAuthMessageHandler(string serviceUrl, string clientId, string userName, string password,
            HttpMessageHandler innerHandler)
        : base(innerHandler)
    {
      _credential = new UserCredential(userName, password);
      _clientId = clientId;
      _serviceUrl = serviceUrl;
    }

    protected override Task<HttpResponseMessage> SendAsync(
             HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)
    {
      try
      {
        request.Headers.Authorization =
        new AuthenticationHeaderValue("Bearer", _authContext.AcquireToken(_serviceUrl, _clientId, _credential).AccessToken);
      }
      catch (Exception ex)
      {
        throw ex;
      }      
      return base.SendAsync(request, cancellationToken);
    }
  }
```

Mit dieser `OAuthMessageHandler`-Klasse würde das oben gezeigte einfache Programm so aussehen, mit einer zusätzlichen Fehlerbehandlung:

```csharp
class SampleProgram
{
    private static string serviceUrl = "https://yourorg.crm.dynamics.com"; 
    private static string clientId = "51f81489-12ee-4a9e-aaae-a2591f45987d"; 
    private static string userName = "you@yourorg.onmicrosoft.com";
    private static string password = "yourpassword";

    static void Main(string[] args)
    {
       HttpMessageHandler messageHandler;

      try
      {
        messageHandler = new OAuthMessageHandler(serviceUrl, clientId, userName, password,
                         new HttpClientHandler());
        //Create an HTTP client to send a request message to the CRM Web service.  
        using (HttpClient client = new HttpClient(messageHandler))
        {
          //Specify the Web API address of the service and the period of time each request   
          // has to execute.  
          client.BaseAddress = new Uri(serviceUrl);
          client.Timeout = new TimeSpan(0, 2, 0);  //2 minutes
          client.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");
          client.DefaultRequestHeaders.Add("OData-Version", "4.0");
          client.DefaultRequestHeaders.Accept.Add(
              new MediaTypeWithQualityHeaderValue("application/json"));

          //Send the WhoAmI request to the Web API using a GET request.   
          var response = client.GetAsync("api/data/v9.0/WhoAmI",
                  HttpCompletionOption.ResponseHeadersRead).Result;
          if (response.IsSuccessStatusCode)
          {
            //Get the response content and parse it.  
            JObject body = JObject.Parse(response.Content.ReadAsStringAsync().Result);
            Guid userId = (Guid)body["UserId"];
            Console.WriteLine("Your system user ID is: {0}", userId);
          }
          else
          {
            throw new Exception(response.ReasonPhrase);
          }
        }
      }
      catch (Exception ex)
      {
        DisplayException(ex);
      }
    }

    /// <summary> Displays exception information to the console. </summary>  
    /// <param name="ex">The exception to output</param>  
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
```

Auch wenn dieses Beispiel <xref:System.Net.Http.HttpClient>.<xref:System.Net.Http.HttpClient.GetAsync*> verwendet. statt des überschriebenen <xref:System.Net.Http.HttpClient.SendAsync*>, gilt es für jede der <xref:System.Net.Http.HttpClient>-Methoden, die eine Anforderung senden.


## <a name="connect-as-an-app"></a>Als App verbinden

Einige Anwendungen, die Sie erstellen werden, sind nicht dazu gedacht, von einem Benutzer interaktiv ausgeführt zu werden. Beispielsweise können Sie eine Web-Client-Anwendung erstellen, die Operationen mit Common Data Service-Daten ausführen kann, oder eine Konsolenanwendung, die eine geplante Aufgabe in irgendeiner Form ausführt. 

Während Sie diese Szenarien mit Anmeldeinformationen für einen normalen Benutzer erreichen könnten, müsste dieses Benutzerkonto eine kostenpflichtige Lizenz verwenden. Dies ist nicht die empfohlene Verfahrensweise.

In diesen Fällen können Sie einen speziellen Anwendungsbenutzer erstellen, der an eine von Azure Active Directory registrierte Anwendung gebunden ist und entweder ein für die App konfiguriertes Schlüsselgeheimnis verwenden oder ein [X.509](https://www.itu.int/rec/T-REC-X.509/en)-Zertifikat hochladen. Ein weiterer Vorteil dieses Ansatzes ist, dass er keine kostenpflichtige Lizenz verbraucht.

### <a name="requirements-to-connect-as-an-app"></a>Anforderungen für die Verbindung als App

Um sich als App zu verbinden, benötigen Sie:
 - Eine registrierte App
 - Einen Common Data Service-Benutzer, der an die registrierte App gebunden ist
 - Verbinden Sie sich entweder über das Anwendungsgeheimnis oder über einen Zertifikat-Fingerabdruck.

#### <a name="register-your-app"></a>Registrieren Sie die App

Wenn Sie eine App registrieren, befolgen Sie die meisten der Schritte, die unter [Exemplarische Vorgehensweise: Registrieren einer App bei Azure Active Directory](walkthrough-register-app-azure-active-directory.md) beschrieben sind, mit den folgenden Ausnahmen:

 - Sie müssen die Berechtigung **Zugriff auf Dynamics 365 als Organisationsbenutzer** erteilen.
 
    Diese Anwendung ist an ein bestimmtes Benutzerkonto gebunden.

 - Sie müssen ein Geheimnis für die App-Registrierung konfigurieren ODER ein Public-Key-Zertifikat hochladen.

Wählen Sie während der Registrierung der App den Abschnitt **Schlüssel** auf der Seite **Einstellungen**.

So fügen Sie ein Zertifikat hinzu:
1. Wählen Sie **Öffentlichen Schlüssel hochladen** aus.
2. Wählen Sie die Datei aus, die Sie hochladen möchten. Es muss einer der folgenden Dateitypen sein: .cer,.pem,.crt.

So fügen Sie ein Passwort hinzu:

1. Fügen Sie eine Beschreibung für den Schlüssel hinzu.
2. Wählen Sie eine Dauer aus.
3. Wählen Sie **Speichern** aus. 

  Die Spalte ganz rechts enthält den Schlüsselwert, nachdem Sie die Konfigurationsänderungen gespeichert haben. Achten Sie darauf, den Schlüssel für die Verwendung in Ihrem Client-Anwendungscode zu kopieren, da er nach dem Verlassen dieser Seite nicht mehr zugänglich ist.

#### <a name="common-data-service-user-account-bound-to-the-registered-app"></a>Ein Common Data Service-Benutzerkonto, das an die registrierte App gebunden ist


Das erste, was Sie tun müssen, ist, eine benutzerdefinierte Sicherheitsrolle zu erstellen, die definiert, welchen Zugriff und welche Rechte dieses Konto innerhalb der Common Data Service-Organisationen hat. Weitere Information finden Sie unter [Erstellen oder Konfigurieren einer benutzerdefinierten Sicherheitsrolle](/power-platform/admin/database-security#create-or-configure-a-custom-security-role)

Nachdem Sie die benutzerdefinierte Sicherheitsrolle erstellt haben, müssen Sie das Benutzerkonto erstellen, das sie verwenden wird.

<!-- Almost exactly the same intructions below can be found in powerapps-docs\developer\common-data-service\use-multi-tenant-server-server-authentication.md -->

#### <a name="manually-create-a-common-data-service-application-user"></a>Erstellen Sie einen Common Data Service Anwendungsbenutzer  

 Die Vorgehensweise, um diesen Benutzer zu erstellen, unterscheidet sich vom Erstellen eines lizenzierten Benutzers. Verwenden Sie die folgenden Schritte:  
  
1. Gehen Sie zu **Einstellungen** > **Sicherheit** > **Benutzer**  
  
2. Klicken Sie in der Dropdownliste der Ansichten auf **Anwendungsbenutzer**.  
  
3. Klicken Sie auf **Neu**. Überprüfen Sie dann, ob Sie das Formular **Anwendungsbenutzer** verwenden.  
  
    Wenn Sie die Felder **Anwendungs-ID**, **URI der Anwendungs-ID** und **Objekt-ID von Azure AD** im Formular nicht sehen, müssen Sie aus der Liste **Anwendungsbenutzer** auswählen:  
  
   ![Auswählen eines Anwendungsbenutzersformulars](media/select-application-user-form.PNG "Auswählen eines Anwendungsbenutzersformulars")  
  
4. Hinzufügen der entsprechenden Werte zu den Feldern:  
  
   |Feld|Value|  
   |-----------|-----------|
   |**Benutzername**| Ein Name für den Benutzer|
   |**Anwendungs-ID**|Der Anwendungs-ID-Wert für die Anwendung, die bei Azure AD registriert ist.|  
   |**Vollständiger Name**|Der Name Ihrer Anwendung.|  
   |**Primäre E-Mail-Adresse**|Die E-Mail-Adresse des Benutzers.|  
  
    Die Felder **URI der Anwendungs-ID** und **Objekt-ID von Azure AD** sind gesperrt und können Sie keine Werte für diese Felder festlegen.  
  
    Wenn Sie diesen Benutzer erstellen, werden die Werte für diese Felder aus Azure AD basierend auf dem Wert der **Anwendungs-ID** abgerufen, wenn Sie den Benutzer speichern.  
  
5. Ordnen Sie den Anwendungsbenutzer der von Ihnen erstellten benutzerdefinierten Sicherheitsrolle zu.

#### <a name="connect-using-the-application-secret"></a>Verbindung über das Anwendungsgeheimnis herstellen

Wenn Sie sich mit einem für die Anwendung konfigurierten Secret verbinden, verwenden Sie die <xref:Microsoft.IdentityModel.Clients.ActiveDirectory.ClientCredential>-Klasse, die in den Parametern `clientId` und `clientSecret` übergeben wird, anstatt ein <xref:Microsoft.IdentityModel.Clients.ActiveDirectory.UserCredential> mit den Parametern `userName` und `password`.
```csharp
string serviceUrl = "https://yourorg.crm.dynamics.com";
string clientId = "<your app id>";
string secret = "<your app secret>";

AuthenticationContext authContext = new AuthenticationContext("https://login.microsoftonline.com/common", false);
ClientCredential credential = new ClientCredential(clientId, secret);

AuthenticationResult result = authContext.AcquireToken(serviceUrl, credential);

string accessToken = result.AccessToken;
```
#### <a name="connect-using-a-certificate-thumbprint"></a>Verbindung über einen Zertifikatsfingerabdruck herstellen

Wenn Sie sich mit einem Zertifikat und mit der <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> verbinden, können Sie Code wie den folgenden verwenden:

```csharp
string CertThumbPrintId = "DC6C689022C905EA5F812B51F1574ED10F256FF6";
string AppID = "545ce4df-95a6-4115-ac2f-e8e5546e79af";
string InstanceUri = "https://yourorg.crm.dynamics.com";

string ConnectionStr = $@"AuthType=Certificate;
                        SkipDiscovery=true;url={InstanceUri};
                        thumbprint={CertThumbPrintId};
                        ClientId={AppID};
                        RequireNewInstance=true";
using (CrmServiceClient svc = new CrmServiceClient(ConnectionStr))
{
    if (svc.IsReady)
    {
    //your code goes here
    }

}
```


### <a name="see-also"></a>Siehe auch

[Authentifizierung mit Common Data Service-Webdiensten](authentication.md)<br />
[Authentifizierung mit .NET Framework-Anwendungen](authenticate-dot-net-framework.md)

---
title: 'Web-API-Hilfscode: Authentifizierungsklasse (Common Data Service für Apps) | Microsoft Docs'
description: Die Authentifizierungsklasse hilft beim Einrichten einer überprüften Verbindung mit einem "Common Data Service für Apps"-Webdienst
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a7b5931c-3142-4616-a331-1e07b4d8845d
caps.latest.revision: 11
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-helper-code-authentication-class"></a>Internet-API-Hilfecode: Authentifizierungsklasse

Verwenden Sie die `Authentication`-Klasse, um das Einrichten einer überprüften Verbindung mit einem "Common Data Service für Apps"-Webdienst zu unterstützen. Diese Klasse unterstützt zwei Authentifizierungsprotokolle: [Windows-Authentifizierung](https://docs.microsoft.com/en-us/windows-server/security/windows-authentication/windows-authentication-overview) für Common Data Service für Apps on-premises oder [OAuth 2.0](http://oauth.net/2/) für Common Data Service für Apps (online) oder Bereitstellungen mit Internetzugriff (IFDs). Diese Klasse basiert auf der Authentifizierungs-Bibliothek (ADAL) von Microsoft Azure Active Directory ([ADAL](https://docs.microsoft.com/en-us/dotnet/api/microsoft.identitymodel.clients.activedirectory?view=azure-dotnet)) zur Verarbeitung des OAuth-Protokolls.  
  
Die `Authentication` befindet sich in der Datei "Authentication.cs" in der [CRM SDK-Web-API-Hilfe-Bibliothek](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/). Sie wurde für die Zusammenarbeit mit der Hilfsklassenhierarchie `Configuration` entworfen, um das Einrichten einer sicheren Verbindung mit Ihrem "Common Data Service für Apps"-Service über ein Objekt vom Typ System.Net.Http.[HttpMessageHandler](https://msdn.microsoft.com/library/hh138091\(v=vs.110\).aspx) zu ermöglichen. Weitere Informationen finden Sie unter [Verwenden der "Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
## <a name="authentication-processing"></a>Authentifizierungsprozess
 
Der Mechanismus, den die `Authentication`-Klasse verwendet, um sich bei einem „Common Data Service für Apps”-Service zu authentifizieren, hängt von den Informationen ab, die Sie dem Konstruktor mit dem `Configuration`-Parameter übergeben. Er versucht, ein vom HttpMessageHandler abgeleitetes Objekt zu erstellen, das Sie dann verwenden können, um eine System.Net.Http.[HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient\(v=vs.110\).aspx)-Instanz zu instantiieren, um eine sichere, dauerhafte Kommunikationssitzung mit dem „Common Data Service für Apps”-Service bereitzustellen.  
  
 Zuerst wird ein kurzer Discoveryhandshake mit dem angegebenen "Common Data Service für Apps"-Service ausgeführt, um zu bestimmen, ob OAuths oder die von Windows systemeigene Authentifizierung verwendet wird.  
  
- Wenn OAuth verwendet wird, wird ein `OAuthMessageHandler`-Objekt mit der Authentifizierungsbehörde erstellt, die im Handshake ermittelt wurde. Diese Klasse, die von System.Net.Http.[DelegatingHandler](/dotnet/api/system.net.http.delegatinghandler) abgeleitet wird, aktualisiert den OAuth-Zugangstoken bei jeder Anforderung, sodass Sie den Tokenablauf nicht explizit verwalten müssen.  
  
- Wenn die Windows-Authentifizierung verwendet wird und Benutzeranmeldeinformationen bereitgestellt wurden, werden diese Anmeldeinformationen verwendet, um einen [HttpClientHandler](/dotnet/api/system.net.http.httpclienthandler) zu erstellen.  
  
- Wenn Windows-Authentifizierung verwendet wird, aber die Benutzeranmeldeinformationen nicht bereitgestellt wird, wird ein HttpClientHandler mit den standardmäßigen Netzwerkanmeldeinformationen erstellt.  
  
## <a name="class-hierarchy-and-members"></a>Klassenhierarchie und -mitglieder  
 Die folgende Tabelle gibt Aufschluss über öffentliche Mitglieder der `Authentication`-Klasse.  
<!-- TODO:  
|||  
|-|-|  
|![Common Data Service for Apps Web API Helper Library&#45;Authentication Class Diagram](../media/web-api-helper-library-authentication-class-diagram.png "Common Data Service for Apps Web API Helper Library-Authentication Class Diagram")|**Authentication class**<br /><br /> *Properties:*<br /><br /> `Authority` – the URL of the server that manages OAuth authentication.<br /><br /> `ClientHandler` – the [HttpMessageHandler](https://msdn.microsoft.com/library/hh138091\(v=vs.110\).aspx)-derived object that provides the network credentials or authorization access token for message requests.<br /><br /> `Context` – the [AuthenticationContext](https://msdn.microsoft.com/library/microsoft.identitymodel.clients.activedirectory.authenticationcontext.aspx) for an authentication event.<br /><br /> *Methods:*<br /><br /> `AquireToken` – For OAuth, returns an [AuthenticationResult](https://msdn.microsoft.com/library/microsoft.identitymodel.clients.activedirectory.authenticationresult.aspx),  containing the refresh and access tokens, for the current authentication context.<br /><br /> `Authentication` – Initializes an instance of this class using the `Configuration` parameter.<br /><br /> `DiscoverAuthority` – Discovers the authentication authority of the Common Data Service for Apps web service.<br /><br /> <br /><br /> **OAuthMessageHandler class**<br /><br /> This nested class sets the authorization header for each sent message for Common Data Service for Apps (online) and IFD deployments.|   -->
  
## <a name="usage"></a>Verwendung  
 Die `Configuration`- und `Authentication`-Klassen sind so konzipiert, dass sie im Tandem verwendet werden, um eine sichere Verbindung zum Ziel "Common Data Service für Apps"-Service einzurichten.  Erstellen Sie zuerst ein Objekt vom Typ `Configuration`, und führen ihn als einzelnen Parameter für den `Authentication`-Konstruktor fort.  Nach der erfolgreichen Erstellung können Sie die `ClientHandler`-Eigenschaft verwenden, um eine sichere, authentifizierte, dauerhafte HTTP-Client-Verbindung zum "Common Data Service für Apps"-Service herzustellen.  
  
 Eine gebräuchliche Möglichkeit, um diesen Vorgang zu erzielen, der durch die meisten Web API C#-Beispiele verwendet wird, ist, die abgeleitete Klasse `FileConfiguration` zu verwenden, um Informationen von ordnungsgemäß erstellten Anwendungskonfigurationsdateien zu lesen, wie in der Darstellung in den folgenden Zeilen veranschaulicht.  
  
```csharp  
  
FileConfiguration config = new FileConfiguration(null);  
Authentication auth = new Authentication(config);  
httpClient = new HttpClient(auth.ClientHandler, true);  
  
```  
  
 Weitere Informationen über diese Verwendungsweise finden Sie im folgenden Abschnitt [FileConfiguration-Verbindungseinstellungen](web-api-helper-code-configuration-classes.md#bkmk_FileConfigconnectionsettings). Obwohl die `Authentication`-Klasse mehrere öffentliche Eigenschaften und Methoden enthält, werden diese hauptsächlich bereitgestellt, um die Erstellung der `ClientHandler`-Eigenschaft zu unterstützen. Der Zugriff erfolgt selten direkt über die meisten Clientanwendungen.  
  
## <a name="class-listing"></a>Klassenlisten  

Den aktuellen Code für diese Klasse finden Sie im [CRM SDK-Web-API-Hilfebibliothek](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode) NuGet-Paket.  
  
```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;  
using System;  
using System.Net;  
using System.Net.Http;  
using System.Net.Http.Headers;  
using System.Security;  
using System.Threading.Tasks;  
  
namespace Microsoft.Crm.Sdk.Samples.HelperCode  
{  
    /// <summary>  
    /// Manages user authentication with the Dynamics CRM Web API (OData v4) services. This class uses Microsoft Azure  
    /// Active Directory Authentication Library (ADAL) to handle the OAuth 2.0 protocol.   
    /// </summary>  
    public class Authentication  
    {  
        private Configuration _config = null;  
        private HttpMessageHandler _clientHandler = null;  
        private AuthenticationContext _context = null;  
        private string _authority = null;  
  
        #region Constructors  
        /// <summary>  
        /// Base constructor.  
        /// </summary>  
        public Authentication() { }  
  
        /// <summary>  
        /// Establishes an authentication session for the service.  
        /// </summary>  
        /// <param name="config">A populated configuration object.</param>  
        public Authentication(Configuration config)  
            : base()  
        {  
            if (config == null)  
                throw new Exception("Configuration cannot be null.");  
  
            _config = config;  
  
            SetClientHandler();  
        }  
  
        /// <summary>  
        /// Custom constructor that allows adding an authority determined asynchronously before   
        /// instantiating the Authentication class.  
        /// </summary>  
        /// <remarks>For a WPF application, first call DiscoverAuthorityAsync(), and then call this  
        /// constructor passing in the authority value.</remarks>  
        /// <param name="config">A populated configuration object.</param>  
        /// <param name="authority">The URL of the authority.</param>  
        public Authentication(Configuration config, string authority)  
            : base()  
        {  
            if (config == null)  
                throw new Exception("Configuration cannot be null.");  
  
            _config = config;  
            Authority = authority;  
  
            SetClientHandler();  
        }  
        #endregion Constructors  
  
        #region Properties  
        /// <summary>  
        /// The authentication context.  
        /// </summary>  
        public AuthenticationContext Context  
        {  
            get  
            { return _context; }  
  
            set  
            { _context = value; }  
        }  
  
        /// <summary>  
        /// The HTTP client message handler.  
        /// </summary>  
        public HttpMessageHandler ClientHandler  
        {  
            get  
            { return _clientHandler; }  
  
            set  
            { _clientHandler = value; }  
        }  
  
        /// <summary>  
        /// The URL of the authority to be used for authentication.  
        /// </summary>  
        public string Authority  
        {  
            get  
            {  
                if (_authority == null)  
                    _authority = DiscoverAuthority(_config.ServiceUrl);  
  
                return _authority;  
            }  
  
            set { _authority = value; }  
        }  
        #endregion Properties  
  
        #region Methods  
        /// <summary>  
        /// Returns the authentication result for the configured authentication context.  
        /// </summary>  
        /// <returns>The refreshed access token.</returns>  
        /// <remarks>Refresh the access token before every service call to avoid having to manage token expiration.</remarks>  
        public AuthenticationResult AcquireToken()  
        {  
            if (_config != null && (!string.IsNullOrEmpty(_config.Username) && _config.Password != null))  
            {  
                UserCredential cred = new UserCredential(_config.Username, _config.Password);  
                return _context.AcquireToken(_config.ServiceUrl, _config.ClientId, cred);  
            }  
            return _context.AcquireToken(_config.ServiceUrl, _config.ClientId, new Uri(_config.RedirectUrl),  
                PromptBehavior.Auto);  
        }  
  
        /// <summary>  
        /// Returns the authentication result for the configured authentication context.  
        /// </summary>  
        /// <param name="username">The username of a CRM system user in the target organization. </param>  
        /// <param name="password">The password of a CRM system user in the target organization.</param>  
        /// <returns>The authentication result.</returns>  
        /// <remarks>Setting the username or password parameters to null results in the user being prompted to  
        /// enter log-on credentials. Refresh the access token before every service call to avoid having to manage  
        /// token expiration.</remarks>  
        public AuthenticationResult AcquireToken(string username, SecureString password)  
        {  
  
            try  
            {  
                if (!string.IsNullOrEmpty(username) && password != null)  
                {  
                    UserCredential cred = new UserCredential(username, password);  
                    return _context.AcquireToken(_config.ServiceUrl, _config.ClientId, cred);  
                }  
            }  
            catch (Exception e)  
            {  
                throw new Exception("Authentication failed. Verify the configuration values are correct.", e);  
            }  
            return null;  
        }  
  
        /// <summary>  
        /// Discover the authentication authority.  
        /// </summary>  
        /// <returns>The URL of the authentication authority on the specified endpoint address, or an empty string  
        /// if the authority cannot be discovered.</returns>  
         public static string DiscoverAuthority(string serviceUrl)  
        {  
            try  
            {  
                AuthenticationParameters ap = AuthenticationParameters.CreateFromResourceUrlAsync(  
                    new Uri(serviceUrl + "api/data/")).Result;  
  
                return ap.Authority;  
            }  
            catch (HttpRequestException e)  
            {  
                throw new Exception("An HTTP request exception occurred during authority discovery.", e);  
            }  
            catch (System.Exception e )  
            {  
                // This exception ocurrs when the service is not configured for OAuth.  
                if( e.HResult == -2146233088 )  
                {  
                    return String.Empty;  
                }  
                else  
                {  
                    throw e;  
                }  
            }  
        }  
  
        /// <summary>  
        /// Discover the authentication authority asynchronously.  
        /// </summary>  
        /// <param name="serviceUrl">The specified endpoint address</param>  
        /// <returns>The URL of the authentication authority on the specified endpoint address, or an empty string  
        /// if the authority cannot be discovered.</returns>  
        public static async Task<string> DiscoverAuthorityAsync(string serviceUrl)  
        {  
            try  
            {  
                AuthenticationParameters ap = await AuthenticationParameters.CreateFromResourceUrlAsync(  
                    new Uri(serviceUrl + "api/data/"));  
  
                return ap.Authority;  
            }  
            catch (HttpRequestException e)  
            {  
                throw new Exception("An HTTP request exception occurred during authority discovery.", e);  
            }  
            catch (Exception e)  
            {  
                // These exceptions ocurr when the service is not configured for OAuth.  
  
                // -2147024809 message: Invalid authenticate header format Parameter name: authenticateHeader  
                if (e.HResult == -2146233088 || e.HResult == -2147024809)  
                {  
                    return String.Empty;  
                }  
                else  
                {  
                    throw e;  
                }  
            }  
        }  
  
        /// <summary>  
        /// Sets the client message handler as appropriate for the type of authentication  
        /// in use on the web service endpoint.  
        /// </summary>  
        private void SetClientHandler()  
        {  
            // Check the Authority to determine if OAuth authentication is used.  
            if (String.IsNullOrEmpty(Authority))  
            {  
                if (_config.Username != String.Empty)  
                {  
                    _clientHandler = new HttpClientHandler()  
                    { Credentials = new NetworkCredential(_config.Username, _config.Password, _config.Domain) };  
                }  
                else  
                // No username is provided, so try to use the default domain credentials.  
                {  
                    _clientHandler = new HttpClientHandler()  
                    { UseDefaultCredentials = true };  
                }  
            }  
            else  
            {  
                _clientHandler = new OAuthMessageHandler(this, new HttpClientHandler());  
                _context = new AuthenticationContext(Authority, false);  
            }  
        }  
        #endregion Methods  
  
        /// <summary>  
        /// Custom HTTP client handler that adds the Authorization header to message requests. This  
        /// is required for IFD and Online deployments.  
        /// </summary>  
        class OAuthMessageHandler : DelegatingHandler  
        {  
            Authentication _auth = null;  
  
            public OAuthMessageHandler( Authentication auth, HttpMessageHandler innerHandler )  
                : base(innerHandler)  
            {  
                _auth = auth;  
            }  
  
            protected override Task<HttpResponseMessage> SendAsync(  
                HttpRequestMessage request, System.Threading.CancellationToken cancellationToken)  
            {  
                // It is a best practice to refresh the access token before every message request is sent. Doing so  
                // avoids having to check the expiration date/time of the token. This operation is quick.  
                request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", _auth.AcquireToken().AccessToken);  
  
                return base.SendAsync(request, cancellationToken);  
            }  
        }  
    }  
}  
```  
  
### <a name="see-also"></a>Siehe auch  

[Erste Schritte mit dem Web API (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Starten eines Web-API-Projekts in Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Verwenden der Common Data Service für Apps-Web-API-Hilfe-Bibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md)<br />
[Hilfscode: Konfigurationsklasse](web-api-helper-code-configuration-classes.md)<br />
[Hilfecode: CrmHttpResponseException-Klasse](web-api-helper-code-crmhttpresponseexception-class.md)

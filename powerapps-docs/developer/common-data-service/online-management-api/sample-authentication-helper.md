---
title: 'Beispiel: Authentifizieren Sie Helfer für die Online Management API für Dynamics 365 for Customer Engagement | MicrosoftDocs zu verwenden'
description: Helfercode zum Authentifizieren bei Online Management API.
ms.date: 11/27/2017
ms.service: crm-online
ms.topic: conceptual
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: a96fff7c-814e-4fa1-98b6-7a2875ee0234
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="sample-authentication-helper-for-the-online-management-api"></a>Beispiel: Authentifizierungshilfe für die Online Management API 

Das Hilfecodebeispiel bietet die folgenden Möglichkeiten, um die Online Management API mithilfe von OAuth 2.0 Protokoll einfach zu authentifizieren und den Zugriffstoken in der Kopfzeile der Nachrichten zu übergeben.

## <a name="discoverauthority-method"></a>DiscoverAuthority-Methode
Diese Weise gibt eine Azure AD Herausforderung aus, um die Autoritätsinformationen anhand der Servic-URL der API zu ermitteln. Eine Liste der Online Management API Service-URLs, siehe [Service-URLs](get-started-online-management-api.md#service-url) 

## <a name="acquiretoken-method"></a>AcquireToken-Methode
Diese Methode ruft das Zugriffstoken anhand der ermittelten Ressource und Client-ID ab und leitet die URL der App um, die Sie registrierten Sie in Azure AD. Beachten Sie, dass Sie die URL der Ressource anstelle von Service-URL der API verwenden, da sie unterschiedlich sind.


## <a name="sendasync-method"></a>SendAsync-Methode

Dabei handelt sich um einen benutzerdefinierten HTTP-Handler, der die Header **Autorisierung** und **Sprache-akzeptieren** den Nachrichtenanforderungen in der Clientanwendung hinzufügt.

## <a name="code-sample-listing"></a>Codebeispielliste 

Hier ist der vollständige Authentifizierungshilfebeispielcode:

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Threading.Tasks;

namespace Microsoft.Crm.Sdk.Samples.HelperCode
{
    /// <summary>
    /// Manages authentication to the Online Management API service.
    /// Uses Microsoft Azure Active Directory Authentication Library (ADAL) 
    /// to handle the OAuth 2.0 protocol. 
    /// </summary>
    public class Authentication
    {
        private HttpMessageHandler _clientHandler = null;
        private AuthenticationContext _authContext = null;
        private string _authority = null;        
        private string _serviceUrl = null;

        // Static variable to hold the Resource. This will be discovered
        // and then used later for acquiring access token
        private static string _resource = null;        

        // TODO: Substitute your app registration values here.
        // These values are obtained on registering your application with the 
        // Azure Active Directory.
        private static string _clientId = "<GUID>";     //e.g. "e5cf0024-a66a-4f16-85ce-99ba97a24bb2"
        private static string _redirectUrl = "<Url>";  //e.g. "app://s7cf7712-b773-4f16-92b3-34cs97a25cc7"

        #region Constructors
        /// <summary>
        /// Base constructor.
        /// </summary>
        public Authentication() { }

        /// <summary>
        /// Custom constructor that allows adding an authority determined asynchronously before 
        /// instantiating the Authentication class.
        /// </summary>                
        /// <param name="authority">The URL of the authority.</param>
        public Authentication(string authority)
            : base()
        {
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
            { return _authContext; }

            set
            { _authContext = value; }
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
                {
                    var authority = DiscoverAuthority(_serviceUrl.ToString());
                    _authority = authority.Result.ToString();
                }


                return _authority;
            }

            set { _authority = value; }
        }
        #endregion Properties

        #region Methods
        /// <summary>
        /// Discover the authentication authority asynchronously.
        /// </summary>
        /// <param name="serviceUrl">The specified endpoint address</param>
        /// <returns>The URL of the authentication authority on the specified endpoint address, or an empty string
        /// if the authority cannot be discovered.</returns>
        public static async Task<string> DiscoverAuthority(string _serviceUrl)
        {
            try
            {
                AuthenticationParameters ap = await AuthenticationParameters.CreateFromResourceUrlAsync(
                    new Uri(_serviceUrl + "/api/aad/challenge"));
                _resource = ap.Resource;
                return ap.Authority;
            }
            catch (HttpRequestException e)
            {
                throw new Exception("An HTTP request exception occurred during authority discovery.", e);
            }
            catch (Exception e)
            {
                throw e;
            }
        }

        /// <summary>
        /// Returns the authentication result for the configured authentication context.
        /// </summary>
        /// <returns>The refreshed access token.</returns>
        /// <remarks>Refresh the access token before every service call to avoid having to manage token expiration.</remarks>
        public AuthenticationResult AcquireToken()
        {
            return _authContext.AcquireToken(_resource, _clientId, new Uri(_redirectUrl),
                PromptBehavior.Always);
        }

        /// <summary>
        /// Sets the client message handler.
        /// </summary>
        private void SetClientHandler()
        {
            _clientHandler = new OAuthMessageHandler(this, new HttpClientHandler());
            _authContext = new AuthenticationContext(Authority, false);
        }

        #endregion Methods

        /// <summary>
        /// Custom HTTP client handler that adds the "Authorization" and "Accept-Language" headers to message requests.
        /// </summary>
        class OAuthMessageHandler : DelegatingHandler
        {
            Authentication _auth = null;

            public OAuthMessageHandler(Authentication auth, HttpMessageHandler innerHandler)
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

                // Set the "Accept-Language" header
                request.Headers.Add("Accept-Language", "en-US");

                return base.SendAsync(request, cancellationToken);
            }
        }
    }
}
```

### <a name="related-topics"></a>Verwandte Themen  

[Erste Schritte mitOnline Management API](get-started-online-management-api.md)

[Vorgänge, die von Online Management API unterstützt werden](operations-supported.md)

[Online Management API-Referenz](/rest/api/admin.services.crm.dynamics.com)

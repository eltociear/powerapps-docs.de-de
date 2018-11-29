---
title: Verbinden mit den Common Data Service for Apps-Webservices über OAuth (Common Data Service for Apps) | Microsoft Docs
description: 'Erfahren Sie, wie mit den Dynamics 365 Customer Engagement-Webdiensten mithilfe OAuths zu verbinden und die ADAL-API die OAuths 2.0-Authentifizierung mit den Dynamics 365-Webdienstidentitätsanbieter zu verwalten.'
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
# <a name="connect-to-web-services-using-oauth"></a>Mithilfe von OAuth mit Webdiensten verbinden

OAuth ist die Authentifizierungsmethode, die von der Common Data Service-Web-API unterstützt wird und eine von zwei Authentifizierungsmethoden für den Organisationsdienst ist – die andere ist die Azure Active Directory-Authentifizierung. Ein Vorteil der Verwendung von OAuth besteht darin, dass die Anwendung mehrstufige Authentifizierung unterstützen kann. Sie können OAuth-Authentifizierung verwenden, wenn die Anwendung entweder eine Verbindung mit dem Organisationsdienst oder dem Suchdienst herstellt.  
  
 Methodenaufrufe an die Webdienste müssen mit dem Identitätsanbieter für diesen Dienstendpunkt autorisiert werden. Die Autorisierung wird genehmigt, wenn ein gültiges OAuth 2.0 (Benutzer-)Zugriffstoken, das von Azure Active Directory ausgestellt wurde, in den Kopfzeilen der Nachrichtenanforderungen angegeben wird.  
  
 Die empfohlene Authentifizierungs-API für die Verwendung mit der CDS for Apps Web-API ist die [Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/), die für eine Vielzahl von Plattformen und Programmiersprachen verfügbar ist. Die ADAL API verwaltet die OAuth 2.0 Authentifizierung mit dem CDS for Apps Web Service-Identitätsanbieter. Weitere Details zum tatsächlichen verwendeten OAuth-Protokol finden Sie unter [Verwenden von OAuth zur Authentifizierung beim CRM-Dienst](http://blogs.msdn.com/b/crm/archive/2013/12/12/use-oauth-to-authenticate-with-the-crm-service.aspx).  
 
> [!NOTE]
> Sie müssen die ADAL 2.0-Bibliotheken verwenden. Alle Dynamics 365 Customer Engagement-Tools, Assemblys und Hilfsprogramme benötigen die von ADAL 2.0 unterstützten Muster.
> Die ADAL 3.0-Bibliotheken benötigen eine Anmeldeseite, um die Benutzerkonteninformationen zu erfassen. Sie bieten keine Möglichkeiten, diese Kontoinformationen monitorlos zu übergeben, wie von Dynamics 365 Customer Engagement erfordert. 

Bevor Sie OAuth-Authentifizierung verwenden können, um eine Verbindung mit CDS for Apps-Webdiensten herzustellen, muss Ihre Anwendung zuerst bei Azure Active Directory registriert werden. Azure Active Directory wird verwendet, um zu überprüfen, dass die Anwendung berechtigt zum Zugriff auf Geschäftsdaten ist, die in einem CDS for Apps-Mandant gespeichert werden.  
  
## <a name="authenticate-using-adal"></a>Authentifizieren mithilfe von ADAL  
 Grundlegende OAuth-Webdienstauthentifizierung mithilfe ADAL erfolgt mit nur ein paar wenigen Codezeilen.  
  
```csharp  
// TODO Substitute your correct CRM root service address,   
string resource = "https://mydomain.crm.dynamics.com";  
  
// TODO Substitute your app registration values that can be obtained after you  
// register the app in Active Directory on the Microsoft Azure portal.  
string clientId = "e5cf0024-a66a-4f16-85ce-99ba97a24bb2";  
string redirectUrl = "http://localhost/SdkSample";  
  
// Authenticate the registered application with Azure Active Directory.  
AuthenticationContext authContext =   
    new AuthenticationContext("https://login.windows.net/common", false);  
AuthenticationResult result = authContext.AcquireToken(resource, clientId, new Uri(redirectUrl));  
```  
  
 Der Authentifizierungskontext wird mit einem bekannten Behördenanbieter zurückgegeben. Wenn Sie den Azure Active Directory-Mandanten, der mit der von Ihnen aufgerufenen CDS for Apps-Instanz verbunden ist, nicht kennen, können Sie eine konstante Zeichenfolge von `https://login.windows.net/common` verwenden, die die Autoritäts-URL für ein Szenario mit mehreren Mandanten ist. Eine andere Möglichkeit, um die Behörde dynamisch zur Laufzeit zu erkunden, wird weiter unten in diesem Thema beschrieben.  
  
 Die nächste Zeile des Codes ruft Authentifizierungsergebnis ab, das das Zugriffstoken enthält, das Sie suchen. Sie können mit diesem Token dem Webdienst Messageanforderungen senden.  
  
 Einige weitere interessante Elemente in diesem Code sind die verwendeten Zeichenfolgenwerte. Die Ressourcenvariable enthält die Transport Layer Security (TLS) oder Secure Sockets Layer (SSL)-Stammadressen, einschließlich der Domäne (Organisation) Ihres CDS for Apps-Servers. Die `clientId` und `redirectUrl` Variablen enthalten die Registrierungsinformationen der App, die das Ergebnis der Registrierung der App bei Azure Active Directory sind. Weitere Informationen zur Appregistrierung finden Sie unter [Exemplarische Vorgehensweise: Registrieren einer Dynamics 365-App bei Azure Active Directory](/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory).  
  
## <a name="use-the-access-token-in-message-requests"></a>Das Zugriffstoken in den Messageanforderungen verwenden  
 Abhängig von der von Ihnen verwendeten CDS for Apps-API gibt es zwei verschiedene Methoden, um eine Nachrichtenanforderung an die Webdienste zu senden. Für die Web-API würden Sie normalerweise eine HTTP-Meldungsanforderung senden. Für den Organisationsdienst würden Sie eine Messageanforderung mithilfe des Webclientproxys senden.  
  
### <a name="http-message-request"></a>HTTP-Messageanforderung  
 Sobald Sie das Zugriffstoken haben, müssen Sie die Autorisierungskopfzeile der Messageanforderung festlegen, die Sie dem Webdienst zum Zugriffstokenwert senden und den Tokentyp von `Bearer` angeben. Weitere Informationen zur Autorisierungskopfzeile finden Sie im Abschnitt 14.8 über das [HTTP/1.1-Protokoll](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html). Der folgende Code veranschaulicht, wie dies mithilfe der `System.Net.Http.HttpClient`-Klasse erfolgt.  
  
```csharp  
using (HttpClient httpClient = new HttpClient())  
{  
    httpClient.Timeout = new TimeSpan(0, 2, 0);  // 2 minutes  
    httpClient.DefaultRequestHeaders.Authorization =   
        new AuthenticationHeaderValue("Bearer", result.AccessToken);  
```  
  
### <a name="web-client-requests"></a>Webclientanforderungen

Legen Sie einfach den <xref:Microsoft.Xrm.Sdk.WebServiceClient.WebProxyClient`1.HeaderToken>-Eigenschaftswert für das Zugriffstoken fest, wenn Sie <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> oder <xref:Microsoft.Xrm.Sdk.WebServiceClient.DiscoveryWebProxyClient> des Organisationsdiensts verwenden.  
  
## <a name="refresh-the-access-token"></a>Das Zugriffstoken aktualisieren

Es ist eine empfohlene Vorgehensweise, das Zugriffstoken vor jedem Aufruf einer CDS for Apps Webservicemethode zu aktualisieren. Um das Zugriffstoken zu aktualisieren, das durch ADAL zwischengespeichert wird, rufen Sie einfach erneut die `AcquireToken`-Methode auf, wobei derselbe Kontext verwendet wird.  
  
```csharp    
AuthenticationResult result = authContext.AcquireToken(resource, clientId, new Uri(redirectUrl));  
```  
  
Danach legen Sie erneut die Autorisierungskopfzeile mit `result.AccessToken` fest, wenn Sie die Web-API verwenden, oder die <xref:Microsoft.Xrm.Sdk.WebServiceClient.WebProxyClient`1.HeaderToken>, wenn Sie den Organisationsdienst verwenden.  
  
```csharp    
httpClient.DefaultRequestHeaders.Authorization =   
    new AuthenticationHeaderValue("Bearer", result.AccessToken);  
```  
  
## <a name="discover-the-authority-at-run-time"></a>Ermitteln Sie die Behörde zur Laufzeit

Die Authentifizierungsbehörden-URL und die Ressourcen-URL können dynamisch zur Laufzeit mithilfe des folgenden ADAL-Codes bestimmt werden. Dies ist die empfohlene Methode, die zu verwenden ist, im Vergleich zur bekannten Behörden-URL, die zuvor in einem Codeausschnitt gezeigt wurde.  
  
```csharp    
AuthenticationParameters ap = AuthenticationParameters.CreateFromResourceUrlAsync(  
                        new Uri("https://mydomain.crm.dynamics.com/api/data/")).Result;  
  
String authorityUrl = ap.Authority;  
String resourceUrl  = ap.Resource;  
```  
  
Für die Web-API besteht eine andere Möglichkeit, die Behörden-URL zu erhalten darin, irgendeine Messageanforderung an den Webdienst zu senden, ohne ein Zugriffstoken anzugeben. Dies wird als *Trägerabfrage* bezeichnet. Die Antwort kann analysiert werden, um die Behörden-URL zu erhalten.  
  
```csharp  
httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", "");  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Registrieren einer Dynamics 365-App bei Azure Active Directory](/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory)   
 [Mehrstufige Authentifizierungsdokumentation](https://azure.microsoft.com/en-us/documentation/services/multi-factor-authentication/)   
 [OAuth 2.0](http://oauth.net/2/)

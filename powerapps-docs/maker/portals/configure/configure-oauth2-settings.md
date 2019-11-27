---
title: Konfigurieren der OAuth2-Anbietereinstellungen für ein Portal | MicrosoftDocs
description: Anweisungen, OAuth2-Providereinstellungen für ein Portal hinzuzufügen und zu konfigurieren.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: be576425067079549d3174e6d6306814a6ddb13a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755441"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>Konfigurieren von OAuth2-Anbietereinstellungen für Portale

Für externe OAuth 2.0-Identitätsanbieter ist die Registrierung einer "Anwendung" bei einem Drittanbieter erforderlich, um eine "Client-ID "und ein "Client-Secret" zu erhalten. Häufig muss für die Anwendung eine Umleitungs-URL angegeben werden, über die der Identitätsanbieter die Benutzer zurück zum Portal leitet (vertrauende Partei). Das Client-ID und das Client-Secret werden als Portalwebsiteeinstellungen konfiguriert, um eine sichere Verbindung zwischen der vertrauende Partei und dem Identitätsanbieter einzurichten. Die Einstellungen basieren auf den Eigenschaften der Klassen [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx), [TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx), [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx) und [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx).  

Die unterstützten Anbieter sind:

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]-Account
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>Erstellen von OAuth-Anwendungen

Wenn ein OAuth-Anbieter App-Einstellungen verwendet, die einen Umleitungs-URI-Wert benötigen, geben Sie <https://portal.contoso.com/or> https://portal.contoso.com/signin-\[Anbieter\] an. Dies hängt davon ab, wie der Anbieter die Umleitungs-URI prüft (einige Anbietern benötigen den vollständigen URL-Pfad zusammen mit dem Domänennamen). Ersetzen Sie den Namen des Anbieters durch den \[Anbieter\] in der Umleitungs-URI.

### <a name="google"></a>Google

[Google OAuth2 API-Anmeldeinformationen-Anweisungen](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. Öffnen Sie die [Google Developers-Konsole](https://console.developers.google.com/).  
2. Erstellen Sie ein API-Projekt oder Öffnen Sie eine vorhandenes Projekt.
3. Navigieren Sie zu**APIs & Auth** &gt;**APIs**und unter **Soziale APIs** wählen Sie**Google+ API**und dann wählen Sie**API aktivieren**
4. Navigieren Sie zu**APIs & Authentifizierung** &gt;**Zustimmungsbildschirm**.
    - Geben Sie eine**E-Mail-Adresse** an.
    - Geben Sie einen benutzerdefinierten**Produktname** an.
    - Wählen Sie**Speichern** aus.
5. Navigieren Sie zu**APIs & Authentifizierung** &gt;**Anmeldeinformationen** und erstellen Sie eine neue Client-ID.
   - Anwendungstyp: **Webanwendung**
   - Berechtigte [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] Ursprünge: https://portal.contoso.com
   - Autorisierte Umleitungs-URIs: https://portal.contoso.com/signin-google 
   - Klicken Sie auf **Neue Client-ID erstellen**.

### <a name="facebook-app-settings"></a>Facebook-App-Einstellungen

1. Öffnen Sie das [Facebook-Entwickler-App-Dashboard](https://developers.facebook.com/apps)  
2. Klicken Sie auf **Eine neue App hinzufügen**.
3. Wählen Sie **Website** aus.
4. Wählen Sie **Überspringen und App ID erstellen**.
    - Legen Sie einen **Anzeigenamen** fest.
    - Wählen Sie eine **Kategorie**.
    - Wählen Sie **App-ID erstellen** aus.

5. Wenn Sie sich im Dashboard für die neue App befinden, navigieren Sie zu **Einstellungen** &gt;**Grundlegend** (Registerkarte) und fügen Sie die folgenden Details hinzu:
    - App-Domänen (optional): portal.contoso.com 
    - Kontakt-E-Mail: *&lt;Ihre E-Mail-Adresse&gt;* 
    - Wählen Sie **Plattform hinzufügen**, und wählen Sie dann **Website** aus. 
    - Site-URL: https://portal.contoso.com/ oder https://portal.contoso.com/signin-facebook

6. Wählen Sie **Änderungen speichern**.
7. Navigieren Sie zur Registerkarte **Status & Prüfung** &gt; **Status**.
8. Wählen Sie **Ja**, wenn Sie dazu aufgefordert werden, um die App und alle ihre Funktionen für die Allgemeinheit verfügbar zu machen. Sie müssen die gültigen Daten in Schritt 5 oben eingefüllt haben, um die Einstellung zu aktivieren.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]-Anwendungseinstellungen

1. Öffnen Sie das [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]-Account Entwicklercenter](https://account.live.com/developers/applications/index)  
2. Klicken Sie auf **Anwendung erstellen**, und geben Sie einen **Anwendungsnamen** an.
3. Klicken Sie auf **Ich stimme zu**, um die Bedingungen anzunehmen.
4. Öffnen Sie **Einstellungen** &gt;**API-Einstellungen** und anschließend den Wert Umleitungs-URL wie https://portal.contoso.com/signin-microsoft 

### <a name="twitter-apps-settings"></a>Twitter-App-Einstellungen

1. Öffnen Sie [Twitter Application Management](https://apps.twitter.com/). 
2. Wählen Sie **Neue App erstellen** aus.

    - Geben Sie einen **Namen** und eine **Beschreibung** für Ihre App an.
    - Die Website URL als https://portal.contoso.com festlegen
    - Legen Sie den Rückruf der URL als https://portal.contoso.com oder https://portal.contoso.com/signin-twitter fest.

3. Klicken Sie auf **Twitter-Anwendung erstellen**.

### <a name="linkedin-app-settings"></a>LinkedIn-App-Einstellungen

1. Öffnen Sie [LinkedIn Developer Network](https://www.linkedin.com/secure/developer).  
2. Wählen Sie **Neue Anwendung hinzufügen** aus.

    - Geben Sie **Anwendungsname**, **Beschreibung** usw. an.
    - Die Website URL als https://portal.contoso.com festlegen
    - Legen Sie OAuth-Benutzervereinbarung/Standardumfang fest: r\_basicprofie und r\_emailaddress
    - OAuth 2.0 Umleitungs-URL : https://portal.contoso.com/signin-linkedin festlegen.

3. Wählen Sie **Anwendung hinzufügen** aus.

### <a name="yahoo-ydn-app-settings"></a>Yahoo! YDN App-Einstellungen

1. Öffnen Sie [Yahoo! Developer Network](https://developer.yahoo.com/apps).
2. Wählen Sie **Eine App erstellen** aus.
    
    - Geben Sie den **Anwendungsnamen** an.
    - Anwendungstyp: **Webanwendung**.
    - Rückruf-Domäne: portal.contoso.com

3. Wählen Sie **App erstellen** aus.

## <a name="create-site-settings-by-using-oauth2"></a>Erstellen von Websiteeinstellungen mithilfe von OAuth2

Das Anwendungsdashboard für jeden Anbieter zeigt die Client-ID (App-ID, Consumer-Schlüssel) und das Client-Secret (App-Secret, Consumer-Secret) für jede Anwendung an. Verwenden Sie diese beiden Werte, um die Portalwebsiteeinstellungen zu konfigurieren.

>[!Note]
> Eine Standard-OAuth2-Konfiguration benötigt nur die folgenden Einstellungen (mit Facebook als Beispiel):
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

Ersetzen Sie den `[provider]`-Tag im Websiteeinstellungsnamen durch einen bestimmten Identitätsanbieternamen: Facebook, Google, Yahoo,[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn oder Twitter.

|**Website-Einstellungsname**                                           |**Beschreibung**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled                | Aktiviert oder deaktiviert die externe Anmeldung und Registrierung. Standard: true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[provider\]/ClientId                   | Erforderlich. Der Client-ID-Wert aus der Anbieter-Anwendung. Sie wird möglicherweise auch als App-ID oder als Consumer-Schlüssel bezeichnet.  Die folgenden Einstellungsnamen sind für Abwärtskompatibilität zulässig: Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[provider\]/ClientSecret               | Erforderlich. Der Client-Secret-Wert aus der Anbieter-Anwendung. Er wird möglicherweise auch als App-Secret oder als Consumer-Secret bezeichnet.  Die folgenden Einstellungsnamen sind für Abwärtskompatibilität zulässig: Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[provider\]/AuthenticationType         | Der OWIN-Authentifizierungs-Middleware-Typ. Beispiel: yahoo. [authenticationoptions.authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Scope                      | Eine durch Kommas getrennte Liste von Berechtigungen zur Anfrage. [microsoftaccountauthenticationoptions.scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Caption                    | Der Text, den der Benutzer auf der Anmelde-Benutzeroberfläche anzeigen kann. [microsoftaccountauthenticationoptions.caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Authentication/OpenAuth/\[provider\]/BackchannelTimeout         | Timeoutwert in Millisekunden für die Back-Channel-Kommunikation. [microsoftaccountauthenticationoptions.backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Authentication/OpenAuth/\[provider\]/CallbackPath               | Der Anforderungspfad innerhalb des Basispfades der Anwendung an die der Benutzer-Agent verwiesen wird. [microsoftaccountauthenticationoptions.callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx).                                                         |  
| Authentication/OpenAuth/\[provider\]/SignInAsAuthenticationType | Der Name einer anderen Authentifizierungsmiddleware, die für die Ausstellung einer **userClaimsIdentity** zuständig ist. [microsoftaccountauthenticationoptions.signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Authentication/OpenAuth/\[provider\]/AuthenticationMode         | Der OWIN-Authentifizierungs-Middleware-Modus. [security.authenticationoptions.authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>Siehe auch

[Konfigurieren der Portalauthentifizierung](configure-portal-authentication.md)  
[Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md)  
[OpenID Connect-Anbietereinstellungen für Portale](configure-openid-settings.md)   
[WS-Federation-Anbietereinstellungen für Portale](configure-ws-federation-settings.md)  
[SAML 2.0-Anbietereinstellungen für Portale](configure-saml2-settings.md)

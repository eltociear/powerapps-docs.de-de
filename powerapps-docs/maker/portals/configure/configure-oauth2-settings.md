---
title: Konfigurieren von OAuth2-Anbieter Einstellungen für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von OAuth2-Anbieter Einstellungen für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 25a26e6298fa3257f3db6d04ffd2937e8e71d3a1
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978529"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>Konfigurieren von OAuth2-Anbieter Einstellungen für Portale

Der auf OAuth 2,0 basierende externe Identitäts Anbieter umfasst das Registrieren einer Anwendung mit einem Drittanbieter Dienst, um das Paar "Client-ID" und "Client Geheimnis" zu erhalten. Häufig muss für diese Anwendung eine Umleitungs-URL angegeben werden, die es dem Identitäts Anbieter ermöglicht, Benutzer zurück an das Portal (vertrauende Seite) zu senden. Die Client-ID und der geheime Client Schlüssel werden als Portal Site Einstellungen konfiguriert, um eine sichere Verbindung von der vertrauenden Seite mit dem Identitäts Anbieter herzustellen. Die Einstellungen basieren auf den Eigenschaften der Klassen " [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]accountauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx)", " [twitterauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx)", " [facebookauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx)" und " [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx) ".  

Folgende Anbieter werden unterstützt:

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] Konto
- Twitter
- Facebook
- Google
- Zuzugreifen
- Yahoo

## <a name="create-oauth-applications"></a>Erstellen von OAuth-Anwendungen

Wenn ein OAuth-Anbieter App-Einstellungen verwendet, die einen Umleitungs-URI-Wert erfordern, geben Sie in der Regel <http://portal.contoso.com/or> http://portal.contoso.com/signin-\ [Anbieter\], abhängig davon, wie der Anbieter die Umleitung des Umleitungs-URIs ausführt (bei manchen Anbietern muss der vollständige URL-Pfad zusammen mit der Domänen Name). Ersetzen Sie anstelle des \[Anbieters\] im Umleitungs-URI den Namen des Anbieters.

### <a name="google"></a>Google

[Anmelde Informationen für die Google OAuth2-API](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. [Google Developer Console](https://console.developers.google.com/) öffnen  
2. Erstellen eines API-Projekts oder Öffnen eines vorhandenen Projekts
3. Wechseln Sie zu**APIs & Authentifizierung** &gt;**APIs**, und wählen Sie unter **soziale APIs**die Option**Google + API**und dann**API aktivieren** aus.
4. Wechseln Sie zu**APIs &** Authentifizierung &gt;**Zustimmungs Bildschirm**.
    - Angeben einer**e-Mail-Adresse**.
    - Geben Sie einen benutzerdefinierten**Produktnamen**an.
    - Wählen Sie**Speichern**aus.
5. Wechseln Sie zu**APIs &** Authentifizierung &gt;**Anmelde** Informationen, und erstellen Sie eine neue Client-ID.
   - Anwendungstyp:**Webanwendung**
   - Autorisierte [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] Ursprünge: http://portal.contoso.com
   - Autorisierte Umleitungs-URIs: http://portal.contoso.com/signin-google 
   - Wählen Sie **Client-ID erstellen**aus.

### <a name="facebook-app-settings"></a>Facebook-App-Einstellungen

1. [Dashboard für Facebook-Entwickler-App](https://developers.facebook.com/apps) öffnen  
2. Wählen Sie **neue APP hinzufügen**aus.
3. Wählen Sie **Website**aus.
4. Wählen Sie über **springen und APP-ID erstellen**aus.
    - Geben Sie einen **anzeigen Amen**an.
    - Wählen Sie eine **Kategorie**aus.
    - Wählen Sie **App-ID erstellen**aus.

5. Navigieren Sie im Dashboard für die neue APP zu **Einstellungen** &gt;**Basic** (Registerkarte), und fügen Sie die folgenden Details hinzu:
    - App-Domänen (optional): Portal.contoso.com 
    - Kontakt-e-Mail: *&lt;e-Mail-Adresse Ihrer Wahl&gt;* 
    - Klicken Sie auf **Plattform hinzufügen**, und wählen Sie dann **Website**aus. 
    - Website-URL: http://portal.contoso.com/ oder http://portal.contoso.com/signin-facebook

6. Wählen Sie **Änderungen speichern**aus.
7. Wechseln Sie zu **Status &** Registerkarte &gt; **Status** .
8. Wählen Sie **Ja** aus, wenn Sie dazu aufgefordert werden, die APP und alle zugehörigen Features der allgemeinen Öffentlichkeit zur Verfügung zu stellen. Sie müssen die gültigen Daten in Schritt 5 oben ausgefüllt haben, um diese Einstellung zu aktivieren.

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>Anwendungseinstellungen [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]

1. [Entwickler Center für[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]-Konto](https://account.live.com/developers/applications/index) öffnen  
2. Wählen Sie **Anwendung erstellen** aus, und geben Sie einen **Anwendungsnamen**an.
3. Wählen Sie **akzeptieren** aus, um die Nutzungsbedingungen zu akzeptieren.
4. Wechseln Sie zu **Einstellungen** &gt;**API-Einstellungen**, und legen Sie dann die Umleitungs-URL als http://portal.contoso.com/signin-microsoft 

### <a name="twitter-apps-settings"></a>Twitter-App-Einstellungen

1. Öffnen Sie die [Twitter-Anwendungs Verwaltung](https://apps.twitter.com/). 
2. Wählen Sie **neue APP erstellen**aus.

    - Geben Sie einen **Namen** und eine **Beschreibung** für Ihre APP an.
    - Legen Sie die Website-URL als http://portal.contoso.com fest.
    - Legen Sie die Rückruf-URL als http://portal.contoso.com oder http://portal.contoso.com/signin-twitter fest.

3. Wählen Sie **Ihre Twitter-Anwendung erstellen**aus.

### <a name="linkedin-app-settings"></a>LinkedIn-App-Einstellungen

1. Öffnen Sie das [LinkedIn Developer Network](https://www.linkedin.com/secure/developer).  
2. Wählen Sie **neue Anwendung hinzufügen**aus.

    - Geben Sie einen **Anwendungsnamen**, eine **Beschreibung**usw. an.
    - Legen Sie Website-URL als http://portal.contoso.com fest.
    - OAuth-Benutzervereinbarung/Standardbereich festlegen: r\_basicprofie und r\_EmailAddress
    - OAuth 2,0-Umleitungs-URL festlegen: http://portal.contoso.com/signin-linkedin.

3. Wählen Sie **Anwendung hinzufügen**aus.

### <a name="yahoo-ydn-app-settings"></a>Yahoo! YDN-App-Einstellungen

1. Öffnen Sie [Yahoo! Developer Network](https://developer.yahoo.com/apps).
2. Wählen Sie **app erstellen**aus.
    
    - Geben Sie einen **Anwendungsnamen**an.
    - Anwendungstyp: **Webanwendung**.
    - Rückruf Domäne: Portal.contoso.com

3. Wählen Sie **app erstellen**aus.

## <a name="create-site-settings-by-using-oauth2"></a>Erstellen von Site Einstellungen mithilfe von OAuth2

Das Anwendungs Dashboard für jeden Anbieter zeigt die Client-ID (app-ID, consumerschlüssel) und den geheimen Client Schlüssel (geheimer App-Schlüssel, consumergeheimnis) für jede Anwendung an. Verwenden Sie diese beiden Werte, um die Portal Website Einstellungen zu konfigurieren.

>[!Note]
> Eine standardmäßige OAuth2-Konfiguration erfordert nur die folgenden Einstellungen (mit Facebook als Beispiel):
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

Ersetzen Sie das `[provider]`-Tag im Namen der Website Einstellung durch einen bestimmten Identitäts Anbieter Namen: Facebook, Google, Yahoo,[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn oder Twitter.

|**Name der Standort Einstellung**                                           |**Description** (Beschreibung)                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentifizierung/Registrierung/externzuweisung aktiviert                | Aktiviert oder deaktiviert die Anmeldung und Registrierung externer Konten. Standardwert: true                                                                                                                                                                                                                                                                         |
| Authentifizierung/openauth/\[Provider\]/ClientID                   | Erforderlich. Der Client-ID-Wert aus der Anbieter Anwendung. Sie kann auch als APP-ID oder consumerschlüssel bezeichnet werden.  Die folgenden Einstellungs Namen sind aus Gründen der Abwärtskompatibilität zulässig: Authentication/openauth/Twitter/consumerkey <ul><li>Authentifizierung/openauth/Facebook/AppID</li><li>Authentifizierung/openauth/LinkedIn/consumerkey</li> |
| Authentifizierung/openauth/\[Provider\]/ClientSecret               | Erforderlich. Der geheime Client Wert aus der Anbieter Anwendung. Sie kann auch als geheimer App-Schlüssel oder consumergeheimnis bezeichnet werden.  Die folgenden Einstellungs Namen sind aus Gründen der Abwärtskompatibilität zulässig: Authentifizierung/openauth/Twitter/consumersecret <ul><li>Authentifizierung/openauth/Facebook/appsecret</li><li>Authentifizierung/openauth/LinkedIn/consumersecret</li> |
| Authentifizierung/openauth/\[Provider\]/AuthenticationType         | Der owin-Authentifizierungs-Middleware-Typ. Beispiel: Yahoo. [authenticationoptions. AuthenticationType](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).                                                                                                                                |  
| Authentifizierung/openauth/\[Provider\]/Scope                      | Eine durch Kommas getrennte Liste der Berechtigungen, die angefordert werden sollen. [microsoftaccountauthenticationoptions. Scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx).                                                                                                                |  
| Authentifizierung/openauth/\[Provider\]/Caption                    | Der Text, den der Benutzer auf einer Anmelde Benutzeroberfläche anzeigen kann. [microsoftaccountauthenticationoptions. Caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx).                                                                                              |  
| Authentifizierung/openauth/\[Provider\]/BackchannelTimeout         | Timeout Wert in Millisekunden für die Back-Channel-Kommunikation. [microsoftaccountauthenticationoptions. backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx).                                                                         |  
| Authentifizierung/openauth/\[Provider\]/CallbackPath               | Der Anforderungs Pfad innerhalb des Basis Pfads der Anwendung, in dem der Benutzer-Agent zurückgegeben wird. [microsoftaccountauthenticationoptions. callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx).                                                         |  
| Authentifizierung/openauth/\[Provider\]/SignInAsAuthenticationType | Der Name einer anderen Authentifizierungs Middleware, die für die tatsächliche Ausgabe einer**userclaimsidentity**zuständig ist. [microsoftaccountauthenticationoptions. signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx). |  
| Authentifizierung/openauth/\[Provider\]/authenticationMode         | Der owin-Authentifizierungs-Middleware-Modus. [Security. authenticationoptions. AuthenticationMode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                       |  

### <a name="see-also"></a>Siehe auch

[Konfigurieren der Portal Authentifizierung](configure-portal-authentication.md)  
[Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md)  
[Öffnen Sie die Einstellungen des ID Connect-Anbieters für Portale](configure-openid-settings.md)   
[WS-Verbund-Anbieter Einstellungen für Portale](configure-ws-federation-settings.md)  
[SAML 2,0-Anbieter Einstellungen für Portale](configure-saml2-settings.md)

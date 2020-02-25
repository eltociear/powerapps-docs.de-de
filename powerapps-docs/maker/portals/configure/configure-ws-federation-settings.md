---
title: Konfigurieren von WS-Verbund-Anbietereinstellungen für ein Portal | MicrosoftDocs
description: Anweisungen, WS-Federation-Providereinstellungen für ein Portal hinzuzufügen und zu konfigurieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f210a5c806ce3ac894e647fc882a4e3d8f4c0167
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977663"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>Konfigurieren von WS-Federation-Anbietereinstellungen für Portale

Ein einzelner [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] Verbunddienste-Server (oder ein anderer [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)-kompatibler Sicherheitstokendienst, STS) kann als Identitätsanbieter hinzugefügt werden. Darüber hinaus kann ein einzelner [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]-ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/)-Namespace als Satz einzelner Identitätsanbieter konfiguriert werden. Die Einstellungen für AD FS und ACS basieren auf den Eigenschaften der Klasse [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx).

## <a name="create-an-ad-fs-relying-party-trust"></a>Erstellen einer AD FS-Vertrauensstellung der vertrauenden Seite

Verwenden des AD FS Management-Tools und wählen Sie **Vertrauensstellungen** &gt; **Vertrauensstellungen** der vertrauenden Seite aus.

1.  Wählen Sie **Hinzufügen einer Vertrauensstellung der vertrauenden Seite**.
2.  Willkommen: Wählen Sie **Start**.
3.  Datenquelle auswählen: Wählen Sie **Daten zur vertrauenden Seite manuell eingeben** aus und klicken Sie auf **Weiter**.
4.  Anzeigenamen eingeben: Geben Sie einen **Namen** ein, und klicken Sie auf **Weiter**.
    Beispiel: https://portal.contoso.com/
5.  Profil auswählen: Wählen Sie **AD FS 2.-Profil** und dann **Weiter** aus.
6.  Zertifikat konfigurieren: Klicken Sie auf **Weiter**.
7.  URL konfigurieren: Aktivieren Sie das Kontrollkästchen **Unterstützung für WS-Federation Passive-Protokoll aktivieren**.

WS-Federation Passive-Protokoll-URL der vertrauenden Seite: https://portal.contoso.com/signin-federation eingeben

-   Hinweis: AD FS erfordert, dass auf das Portal über **HTTPS** ausgeführt wird.

    > [!Note]
    > Der resultierende Endpunkt in den folgenden Einstellungen: Endpunkttyp: **WS-Verbund**
    > -   Bindung: **POST**
    > -   Index: n/v (0)
    > -   URL: **https://portal.contoso.com/signin-federation**

8.  Konfigurieren Sie Identitäten: Geben Sie https://portal.contoso.com/ an, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Weiter** aus.
    Ggf. können mehr Identitäten für jedes zusätzliche vertrauende Portal hinzugefügt werden. Benutzer sind in der Lage, sich über beliebige oder alle verfügbaren Identitäten zu authentifizieren.
9.  Ausstellungs-Autorisierungsregeln wählen : **Wählen Sie Allen Benutzern erlauben, auf diese vertrauende Seite zugreifen** und klicken Sie dann auf **Weiter**.
10.  Vertrauensstellung hinzufügen vorbereiten: Klicken Sie auf **Weiter**.
11.  Wählen Sie **Schließen** aus.

Fügen Sie die **Namens-ID** für die vertrauenden Seite hinzu:

**Umwandeln [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] des Kontonamens** in den **Namen-ID**-Anspruch (Transformieren eines eingehenden Anspruchs):
- Typ des eingehenden Anspruchs: Windows-Kontoname
- Typ des ausgehenden Anspruchs: Name-ID
- Ausgehendes Namen-ID-Format: Nicht angegeben
- Alle Anspruchswerte durchleiten

### <a name="create-ad-fs-site-settings"></a>AD FS-Standorteinstellungen erstellen

Wenden Sie die Portalwebsiteeinstellungen an, indem Sie die oben aufgeführte AD FS-Vertrauensstellung der vertrauenden Seite nutzen.

> [!Note]
> Eine standardmäßige AD FS (STS)-Konfiguratoin nutzt nur die folgenden Einstellungen (Beispielswerte):
> - Authentication/WsFederation/ADFS/MetadataAddress - https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust
>   - Verwenden Sie den Wert des Attributs **entityID** im Stammelement der Verbundmetadaten (öffnen Sie **URL MetadataAddress**, der in einem Browser der Wert in der obigen Websiteeinstellung ist)
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-federation

Die **WS-Federation-Metadaten** können in **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** abgerufen, indem Sie folgende Schritte auf dem AD FS-Server ausführen:

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      Website-Einstellungsname                      |                                                                                                                                                                                                                                                 Beschreibung                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentication/Registration/ExternalLoginEnabled       |                                                                                                                                                                                                                Aktiviert oder deaktiviert die externe Anmeldung und Registrierung. Standard: true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | Erforderlich. Die [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)-Metadaten-URLAD des AD FS-Servers (STS). Endet standardmäßig mit dem Pfad:/FederationMetadata/2007-06/FederationMetadata.xml. Beispiel:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>. Weitere Informationen: [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx). |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            Erforderlich. Der OWIN-Authentifizierungs-Middleware-Typ. Geben Sie den Wert des [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata)-Attributs im Stammverzeichnis der Verbundmetadaten-XML an. Beispiel: https://adfs.contoso.com/adfs/services/trust. Weitere Informationen: [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              Erforderlich. Die AD FS-ID der vertrauenden Seite. Beispiel: `https://portal.contoso.com/`. Weitere Informationen: [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx).                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     Erforderlich. Der passive AD FS-WS-Federation-Endpunkt. Beispiel: https://portal.contoso.com/signin-federation. Weitere Informationen: [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx).                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           Empfohlen. Der Text, den der Benutzer auf der Anmelde-Benutzeroberfläche anzeigen kann. Standard: ADFS. Weitere Informationen: [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx).                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             Ein optionaler eingeschränkter Pfad für den Authentifizierungs-Callback. Weitere Informationen: [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx).                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               Der Wert "wreply", der bei der Abmeldung verwendet wird. Weitere Informationen: [WsFederationAuthenticationOptions.SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx).                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         Timeoutwert für die Back-Channel-Kommunikation. Beispiel: 00:05:00 (5 Min.). Weitere Informationen: [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx).                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  Legt fest, ob eine Metadatenaktualisierung nach einem SecurityTokenSignatureKeyNotFoundException versucht wird. Weitere Informationen: [WsFederationAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx).                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   Gibt an, dass die Authentifizierungssitzungslebensdauer (z. B. Cookies) mit den dem Authentifizierungstoken übereinstimmen soll. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            Der OWIN-Authentifizierungs-Middleware-Modus. Weitere Informationen: [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            Der AuthenticationType, der verwendet wird, wenn die System.Security.Claims.ClaimsIdentity erstellt wird. Weitere Informationen: [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx).                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         Durch Kommas getrennte Liste der Zielgruppe-URL. Weitere Informationen: [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              Durch Kommas getrennte Liste der Aussteller-URLs. Weitere Informationen: [TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               Die Abweichungen, wenn Zeiten überprüft werden.                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     Der Anspruchstyp, der von ClaimsIdentity verwendet wird, um den Nameanspruch zu speichern.                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     Der Anspruchstyp, der von ClaimsIdentity verwendet wird, um den Rollenanspruch zu speichern.                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     Gibt an, Wert, ob Tokens einen Ablaufwert besitzen müssen.                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       Ein Wert, der angibt, ob ein System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> gültig sein kann, wenn es nicht signiert ist.                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               Ein boolescher Wert zum Steuern, ob das ursprüngliche Token gespeichert wird, wenn eine Sitzung erstellt wird.                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   Der Wert, der angibt, ob das System.IdentityModel.Tokens.JwtSecurityToken.Actor validiert sein soll.                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               Ein boolescher Wert, der steuert, ob die Zielgruppe während der Tokenüberprüfung überprüft wird.                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                Ein boolescher Wert, der steuert, ob der Aussteller während der Tokenüberprüfung überprüft wird.                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               Ein boolescher Wert, der steuert, ob die Lebensdauer während der Tokenüberprüfung überprüft wird.                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         Ein boolescher Wert, der steuert, ob die Überprüfung von System.IdentityModel.Tokens.SecurityKey der Signierung des securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> aufgerufen wird.                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       Gibt einen Parameter "whr" in der Identitätsanbieterumleitungs-URL an. Weitere Informationen: [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation).                                                                                                                                       |

## <a name="ws-federation-settings-for-pn-azure-active-directory"></a>WS-Verbunds-Einstellungen für [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Der vorherige Abschnitt, in dem AD FS beschrieben wird, kann auch auf [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)) angewendet weden, da [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD sich wie ein normaler [WS-Federation](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide)-konformer Sicherheitstokendienst verhält. Um sich am [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] Management Portal](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) anzumelden und ein vorhandenes Verzeichnis zu erstellen oder auszuwählen. Wenn kein Verzeichnis verfügbar ist, folgen Sie den Anweisungen zum [Hinzufügen einer Anwendung](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) zu einem Verzeichnis.

1.  Klicken Sie im Menü **Anwendungen** auf das Verzeichnis, klicken Sie auf die Schaltfläche **Hinzufügen**.
2.  Wählen Sie **Hinzufügen einer Anwendung, die meine Organisation entwickelt**.
3.  Geben Sie einen benutzerdefinierten **Name** für die Anwendung an und wählen Sie den Typ **Webanwendung und/oder Internet API**
4.  Geben Sie für **Anmelde-URL** und **App-ID-URI** die URL des Portals an https://portal.contoso.com/
    - Dies entspricht dem **wtrealm**-Webseiteneinstellungswert.
5.  Zu diesem Zeitpunkt wird eine Neuanmeldung erstellt. Navigieren Sie zum Abschnitt **Konfigurieren** im Menü.
6.  Unter dem Abschnitt **einmalige Anmeldung** aktualisieren Sie den ersten **Antwort-URL**-Eintrag und tragen einen Pfad in die URL ein: https://portal.contoso.com/signin-azure-ad.
    - Dies entspricht dem **Wreply**-Webseiteneinstellungswert.
7.  Klicken Sie im Fuß auf **Speichern**.
8.  Im Fußzeilenmenü klicken Sie auf **Endpunkte anzeigen** und sehen sich das Feld **Verbundmetadatendokument** an.

    - Dies entspricht dem **MetadataAddress**-Webseiteneinstellungswert.
    - Fügen Sie diese URL in ein Browserfenster ein, um die Verbundmetadaten-XML anzuzeigen und das Attribut **entityID** des Stammelements zu beachten
    - Dies entspricht dem **AuthenticationType**-Webseiteneinstellungwert.

> [!Note]
> Eine standardmäßige [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD-Konfiguratoin nutzt nur die folgenden Einstellungen (Beispielswerte):
> - Authentication/WsFederation/ADFS/MetadataAddress - https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - Verwenden Sie den Wert des Attributs **entityID** im Stammelement der Verbundmetadaten (öffnen Sie **URL MetadataAddress**, der in einem Browser der Wert in der obigen Websiteeinstellung ist)
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>Siehe auch

[Konfigurieren der Portalauthentifizierung](configure-portal-authentication.md)  
[Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md)  
[OAuth2-Anbietereinstellungen für Portale](configure-oauth2-settings.md)  
[OpenID Connect-Anbietereinstellungen für Portale](configure-openid-settings.md)  
[SAML 2.0-Anbietereinstellungen für Portale](configure-saml2-settings.md)  

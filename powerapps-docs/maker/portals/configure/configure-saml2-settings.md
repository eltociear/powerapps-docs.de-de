---
title: Konfigurieren der SAML 2.0-Anbietereinstellungen für ein Portal | MicrosoftDocs
description: Anweisungen, SAML 2.0-Providereinstellungen für ein Portal hinzuzufügen und zu konfigurieren.
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4126ba564027291d8bbcb853f0769aa67f0de7d7
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979115"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>Konfigurieren von SAML 2.0-Anbietereinstellungen für Portale

Zur Bereitstellung der externen Authentifizierung können Sie mindestens ein [SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)-kompatiblen Identitätsanbieter (IdP) hinzufügen. In diesem Dokument wird beschrieben, wie verschiedene Identitätsanbieter eingerichtet werden, um sie mit dem Portal, das als Dienstanbieter (SP) agiert, zu integrieren.  

## <a name="ad-fs-idp"></a>AD FS (IdP)

Einstellungen für einen Identitätsanbieter wie [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)].

### <a name="create-an-ad-fs-relying-party-trust"></a>Erstellen einer AD FS-Vertrauensstellung der vertrauenden Seite

> [!Note]
> Siehe [Konfigurieren des AD FS unter Verwendung von PowerShell](#configure-ad-fs-by-using-powershell) unten, um Informationen dazu zu erhalten, wie diese Schritte in einem [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]-Skript ausgeführt werden.

Wählen Sie im [!include[](../../../includes/pn-adfs-short.md)]-Management-Tool **Dienst** > **Anspruchsbeschreibungen** aus.

1.  Klicken Sie auf **Anspruchsbeschreibung hinzufügen** ...
2.  Angeben des Anspruchs:

    -  Anzeigename: **Persistenter Bezeichner**

    -  Anspruchsbezeichner: **urn:oasis:names:tc:SAML:2.0:nameid-format:persistent**

    -  Kontrollkästchen **aktivieren** für: Veröffentlichen Sie die Anspruchsbeschreibung in den Verbundmetadaten als Anspruchstyp, die dieser Verbunddienst annehmen kann

    -  Kontrollkästchen **aktivieren** für: Veröffentlichen Sie die Anspruchsbeschreibung in den Verbundmetadaten als Anspruchstyp, die dieser Verbunddienst senden kann

3.  Wählen Sie **OK** aus.

Verwenden Sie das [!include[](../../../includes/pn-adfs-short.md)] Management-Tool, und wählen Sie **Vertrauensstellungen** >**Vertrauensstellungen der vertrauenden Seite** aus.

1. Wählen Sie **Hinzufügen einer Vertrauensstellung der vertrauenden Seite**.
2. Willkommen: Wählen Sie **Start**.
3. Datenquelle auswählen: Wählen Sie **Daten zur vertrauenden Seite manuell eingeben** aus und klicken Sie auf **Weiter**.
4. Anzeigenamen eingeben: Geben Sie einen Namen ein, und klicken Sie auf **Weiter**.
   Beispiel: https://portal.contoso.com/
5. Profil auswählen: Wählen Sie **AD FS 2.-Profil** und dann **Weiter** aus.
6. Zertifikat konfigurieren: Klicken Sie auf **Weiter**.
7. URL konfigurieren: Aktivieren Sie das Kontrollkästchen **Unterstützung für das SAML 2.0 WebSSO-Protokoll**.
   SAML 2.0 SSO-Dienst-URL der vertrauenden Seite: Geben Sie https://portal.contoso.com/signin-saml2 ein
   - Hinweis: [!include[](../../../includes/pn-adfs-short.md)] erfordert, dass das Portal über HTTPS ausgeführt wird.

   > [!Note] 
   > Der resultierende Endpunkt hat die folgenden Einstellungen: 
   > - Endpunkttyp: **SAML Assertion Consume Endpoints**             
   > - Bindung: **POST**                                            
   > - Index: n/v (0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. Konfigurieren Sie Identitäten: Geben Sie https://portal.contoso.com/ an, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Weiter** aus.
   Ggf. können mehr Identitäten für jedes zusätzliche vertrauende Portal hinzugefügt werden. Benutzer sind in der Lage, sich über beliebige oder alle verfügbaren Identitäten zu authentifizieren.
9. Ausstellungs-Autorisierungsregeln wählen : **Wählen Sie Allen Benutzern erlauben, auf diese vertrauende Seite zugreifen** und klicken Sie dann auf **Weiter**.
10. Vertrauensstellung hinzufügen vorbereiten: Klicken Sie auf **Weiter**.
11. Wählen Sie **Schließen** aus.

Fügen Sie die **Namens-ID** für die vertrauenden Seite hinzu:

**Umwandeln[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] des Kontonamens** in den **Namen-ID**-Anspruch (Transformieren eines eingehenden Anspruchs):

- Typ des eingehenden Anspruchs: **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]-Kontoname**

- Typ des ausgehenden Anspruchs: **Name-ID**

- Ausgehendes Namens-ID-Format: **Persistenter Bezeichner**

- Alle Anspruchswerte durchleiten

### <a name="create-site-settings"></a>Erstellen von Website-Einstellungen

Wenden Sie die Portalwebsiteeinstellungen an, indem Sie die oben aufgeführte [!include[](../../../includes/pn-adfs-short.md)]-Vertrauensstellung der vertrauenden Seite nutzen.

> [!Note]
> Eine standardmäßige [!include[](../../../includes/pn-adfs-short.md)] (IdP)-Konfiguration verwendet nur die folgenden Einstellungen (mit Beispielwerten): Authentication/SAML2/ADFS/MetadataAddress - <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust    
>   -   Verwenden Sie den Wert des Attributs **entityID** im Stammelement der Verbundmetadaten (öffnen Sie **URL MetadataAddress**, der in einem Browser der Wert in der obigen Websiteeinstellung ist) 
> - Authentication/SAML2/ADFS/ServiceProviderRealm - https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2  
>   Die **Federation-Metadaten** können in **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** abgerufen werden, indem Sie das folgende Skript auf dem [!include[](../../../includes/pn-adfs-short.md)]-Server ausführen: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

Sie können mehrere IdP-Dienste konfigurieren, indem Sie den Tag [provider] durch eine Bezeichnung ersetzen. Jede eindeutige Beschriftung steht für eine Gruppe von Einstellungen, die sich auf einen IdP bezieht. Beispiele: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, MyIdP


| Website-Einstellungsname                                             | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled              | Aktiviert oder deaktiviert die externe Anmeldung und Registrierung. Standard: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[provider]/MetadataAddress             | Erforderlich. Die [WS-Federation](https://msdn.microsoft.com/library/bb498017.aspx)-Metadaten-URL des [!include[](../../../includes/pn-adfs-short.md)] (STS)-Servers. Sie Endet standardmäßig mit dem Pfad:/FederationMetadata/2007-06/FederationMetadata.xml. Beispiel: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[provider]/AuthenticationType          | Erforderlich. Der OWIN-Authentifizierungs-Middleware-Typ. Geben Sie den Wert des [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata)-Attributs im Stammverzeichnis der Verbundmetadaten-XML an. Beispiel: `https://adfs.contoso.com/adfs/services/trust`. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[provider]/ServiceProviderRealm<br>oder <br>Authentication/SAML2/[provider]/Wtrealm                      | Erforderlich. Die [!include[](../../../includes/pn-adfs-short.md)]-ID der vertrauenden Seite. Beispiel: `https://portal.contoso.com/`. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[provider]/AssertionConsumerServiceUrl<br>oder<br>Authentication/SAML2/[provider]/Wreply                       | Erforderlich. Der [!include[](../../../includes/pn-adfs-short.md)] SAML Consumer Assertion-Endpunkt. Beispiel: https://portal.contoso.com/signin-saml2. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[provider]/Caption                     | Empfohlen. Der Text, den der Benutzer auf der Anmelde-Benutzeroberfläche anzeigen kann. Standard: [provider]. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[provider]/CallbackPath                | Ein optionaler eingeschränkter Pfad für den Authentifizierungs-Callback. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[provider]/BackchannelTimeout          | Timeoutwert für die Back-Channel-Kommunikation. Beispiel: 00:05:00 (5 Min.). [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[provider]/UseTokenLifetime            | Gibt an, dass die Authentifizierungssitzungslebensdauer (z. B. Cookies) mit der des Authentifizierungstokens übereinstimmen soll. [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/SAML2/[provider]/AuthenticationMode          | Der OWIN-Authentifizierungs-Middleware-Modus. [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[provider]/SignInAsAuthenticationType  | Der AuthenticationType, der verwendet wird, wenn die System.Security.Claims.ClaimsIdentity erstellt wird. [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[provider]/ValidAudiences              | Durch Kommas getrennte Liste der Zielgruppe-URL. [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[provider]/ClockSkew                   | Die Abweichungen, wenn Zeiten überprüft werden.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[provider]/RequireExpirationTime       | Gibt an, Wert, ob Tokens einen Ablaufwert besitzen müssen.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[provider]/ValidateAudience            | Ein boolescher Wert, der steuert, ob die Zielgruppe während der Tokenüberprüfung überprüft wird.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>Anmeldung, die der IdP initiiert hat

[!include[](../../../includes/pn-adfs-short.md)] unterstützt das Profil des [IdP-initiierten einmaligen Anmeldens](https://technet.microsoft.com/library/jj127245.aspx) der SAML 2.0-[Spezifikation](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline). Damit das Portal (Dienstanbieter) korrekt auf die vom IdP initiierte SAML-Anforderung reagieren kann, muss der [RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx)-Parameter richtig codiert werden.  

Der grundlegende String-Wert des in den SAML-RelayState codierten Parameters muss das folgende Format haben: **ReturnUrl=/content/sub-content/**, wobei **/content/sub-content/** der Pfad zur gewünschten Webseite auf dem Portal (Dienstanbieter) ist. Der Pfad kann durch jede gültige Webseite im Portal ersetzt werden. Der Zeichenfolgenwert ist codiert und in einer Containerzeichenfolge des folgenden Formats platziert: **RPID=&lt;URL encoded RPID&gt;&RelayState=&lt;URL encoded RelayState&gt;**. Die gesamte Zeichenfolge wird noch einmal codiert und zu einem anderen Container des Formats **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> RPID/RelayState&gt;** codiert.

Wenn Sie beispielsweise den Dienstanbieterpfad: **/content/sub-content/** und die ID der vertrauenden Seite, nämlich **https://portal.contoso.com/** haben, erstellen Sie die URL mit diesen Schritten:

Codieren Sie Sie den Wert ReturnUrl=/content/sub-content/

-   um ReturnUrl%3D%2Fcontent%2Fsub-content%2F zu erhalten

<!-- -->

-   Codieren Sie den Wert https://portal.contoso.com/

<!-- -->

-   um https%3A%2F%2Fportal.contoso.com%2F zu erhalten

<!-- -->

-   Codieren Sie Sie den Wert RPID=https%3A%2F%2Fportal.contoso.com%2F&RelayState=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

<!-- -->

-   um RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F zu erhalten

<!-- -->

-   Stellen Sie den AD FS IdP-initiiierten SSO-Pfad voran, um die abschließende URL abzurufen.

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

Das folgende [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]-Skript kann verwendet werden, um die URL zu konstruieren (speichern Sie es mit dem Namen Get-IdPInitiatedUrl.ps1).

```
<#

.SYNOPSIS 

Constructs an IdP-initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER rpid

The relying party identifier.

.PARAMETER adfsPath

The AD FS IdP initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$rpid,

[parameter(position=2)]

$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($rpid)

$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")

$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid

Write-Output $idpInitiatedUrl
```

## <a name="saml-20-settings-for-pn-azure-active-directory"></a>SAML 2.0-Einstellungen für [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Im vorherigen Abschnitt wird beschrieben, dass [!include[](../../../includes/pn-adfs-short.md)] auf für [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx) angewendet werden kann, da sich [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD wie ein normaler [SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;-konformer IdP verhält. Um zu beginnen, melden Sie sich am [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] Management Portal](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) an und erstellen ein Verzeichnis oder wählen ein vorhandenes Verzeichnis. Wenn kein Verzeichnis verfügbar ist, folgen Sie den Anweisungen zum [Hinzufügen einer Anwendung](https://msdn.microsoft.com/library/azure/dn132599.aspx) zu einem Verzeichnis.  

1.  Klicken Sie im Menü **Anwendungen** auf das Verzeichnis, klicken Sie auf die Schaltfläche **Hinzufügen**.
2.  Wählen Sie **Hinzufügen einer Anwendung, die meine Organisation entwickelt**.
3.  Geben Sie einen benutzerdefinierten Namen für die Anwendung an und wählen Sie den Typ **Webanwendung und/oder Web-API**.
4.  Geben Sie für **Anmelde-URL** und **App-ID-URI** die URL des Portals für beide Felder an https://portal.contoso.com/.
    Dies entspricht dem **ServiceProviderRealm**-Webseiteneinstellungswert (Wtrealm).
5. Zu diesem Zeitpunkt wird eine Neuanmeldung erstellt. Navigieren Sie zum Abschnitt **Konfigurieren** im Menü.

    Unter dem Abschnitt **einmalige Anmeldung** aktualisieren Sie den ersten **Antwort-URL**-Eintrag und tragen einen Pfad in die URL https://portal.contoso.com/signin-azure-ad ein.

    Dies entspricht dem **AssertionConsumerServiceUrl**-Webseiteneinstellungswert (Wreply).

6. Im Fußzeilenmenü klicken Sie auf **Endpunkte anzeigen** und sehen sich das Feld **Verbundmetadatendokument** an.

Dies entspricht dem **MetadataAddress**-Webseiteneinstellungswert.

-   Fügen Sie diese URL in ein Browserfenster ein, um die Verbundmetadaten-XML anzuzeigen und das Attribut **entityID** des Stammelements zu beachten
-   Dies entspricht dem**AuthenticationType**-Webseiteneinstellungwert.

> [!Note]
> Eine standardmäßige [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD-Konfiguration verwendet nur die folgenden Einstellungen (mit Beispielwerten): Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType - <https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - Verwenden Sie den Wert des Attributs **entityID** im Stammelement der Verbundmetadaten (öffnen Sie **URL MetadataAddress**, der in einem Browser der Wert in der obigen Websiteeinstellung ist) 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm - <https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl - <https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Shibboleth Identity Provider 3

Verwenden Sie folgende Richtlinien für die Konfiguration von [Shibboleth Identity Provider](https://wiki.shibboleth.net/confluence/display/IDP30/Home) als einen IdP-Service. Im Folgenden wird angenommen, dass der IdP in der Domäne https://idp.contoso.com gehostet wird.  

Die Verbundmetadaten-URL ist https://idp.contoso.com/idp/shibboleth

-   Der IdP muss für die Generierungen oder Bereitstellung eines persistenten Bezeichners konfiguriert sein. Befolgen Sie den Anweisungen, um die [Persistent Identifier Generation](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration) zu aktivieren.  

-   Die IdP-Verbundmetadaten (&lt;IDPSSODescriptor&gt;) müssen konfiguriert werden, um eine [SSO-Umleitungsbindung](https://shibboleth.net/about/advanced.html) einzubeziehen. [Beispiel](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample).  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

Konfigurieren Sie die vertrauende Seiten des Dienstanbieters indem Sie die Datei [metadata-providers.xml](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration) einrichten.  

-   Alle Dienstanbieter-Verbundmetadaten (&lt;SPSSODescriptor&gt;) müssen eine Assertionsconsumerservice-Post-Bindung enthalten. Eine Option ist es, einen [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) zu verwenden und eine Konfigurationsdatei zu referenzieren, die Folgendes enthält:  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

Das Location-Attribut, dass dem**AssertionConsumerServiceUrl**-Webseiteneinstellungswert (Wreply) entspricht.

-   Die Dienstanbieter-Verbundmetadaten sollten das Attribut **entityID** für den EntityDescriptor angeben, das der Einstellung **AuthenticationType** entspricht.

**&lt;EntityDescriptor entityID=<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> Eine standardmäßige Shibboleth-Konfiguratoin nutzt nur die folgenden Einstellungen (Beispielswerte):   
> Authentication/SAML2/Shibboleth/MetadataAddress - https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType - https://idp.contoso.com/idp/shibboleth 
> -   Verwenden Sie den Wert des Attributs **entityID** im Stammelement der Verbundmetadaten (öffnen Sie **URL MetadataAddress**, der in einem Browser der Wert in der obigen Websiteeinstellung ist)  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm - https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>Anmeldung, die der IdP initiiert hat

Shibboleth unterstützt das [IdP-initiierte SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO)-Profil der SAML 2.0-[Spezifikationen](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline). Damit das Portal (Dienstanbieter) korrekt auf die vom IdP initiierte SAML-Anforderung reagieren kann, muss der RelayState-Parameter richtig codiert werden.  

Der grundlegende String-Wert des in den SAML-RelayState codierten Parameters muss das folgende Format haben: **ReturnUrl=/content/sub-content/**, wobei **/content/sub-content/** der Pfad zur gewünschten Webseite auf dem Portal (Dienstanbieter) ist. Der Pfad kann durch jede gültige Webseite im Portal ersetzt werden. Die vollständige IdP-initiierte SSO-URL muss im Format URL <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> encoded provider ID&gt;&target=&lt;URL encoded return path&gt; sein.

Beim Dienstanbieterpfad **/content/sub-content/** und **https://portal.contoso.com/** als ID der vertrauenden Seite ist die endgültige URL https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

Das folgende [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]-Skript kann verwendet werden, um die URL zu konstruieren (speichern Sie es mit dem Namen Get-ShibbolethIdPInitiatedUrl.ps1).

```
<# 

.SYNOPSIS

Constructs an IdP initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER providerId

The relying party identifier.

.PARAMETER shibbolethPath

The Shibboleth IdP-initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-ShibbolethIdPInitiatedUrl.ps1 -path "/content/sub-content/" -providerId "https://portal.contoso.com/" -shibbolethPath "https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$providerId,

[parameter(position=2)]

$shibbolethPath = https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($providerId)

$idpInitiatedUrl = {0}?providerId={1}&target={2} -f $shibbolethPath, $encodedRpid, $encodedPath

Write-Output $idpInitiatedUrl
```

## <a name="configure-ad-fs-by-using-powershell"></a>Konfigurieren des AD FS unter Verwendung von PowerShell

Der Prozess des Hinzufügens einer Vertrauensstellung der vertrauenden Seite in [!include[](../../../includes/pn-adfs-short.md)] kann auch ausgeführt werden, indem Sie das folgende [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]-Skript auf dem [!include[](../../../includes/pn-adfs-short.md)]-Server ausführen (speichern Sie die Datei mit dem Namen Add-AdxPortalRelyingPartyTrustForSaml.ps1). Nachdem Sie das Skript ausgeführt haben, fahren Sie mit der Konfiguration der Portalwebsiteeinstellungen fort.

```
<# 

.SYNOPSIS

Adds a SAML 2.0 relying party trust entry for a website.

.PARAMETER domain

The domain name of the portal.

.EXAMPLE

PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com

#>

param

(

[parameter(Mandatory=$true,Position=0)]

$domain,

[parameter(Position=1)]

$callbackPath = /signin-saml2

)

$VerbosePreference = Continue

$ErrorActionPreference = Stop

Import-Module adfs

Function Add-CrmRelyingPartyTrust

{

param (

[parameter(Mandatory=$true,Position=0)]

$name

)

$identifier = https://{0}/ -f $name

$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)

$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }

$issuanceTransformRules = @'

@RuleTemplate = MapClaims

@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);

'@

Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules

}

# add the 'Identity Provider' claim description if it is missing

if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {

Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true

}

# add the portal relying party trust

Add-CrmRelyingPartyTrust $domain
```

### <a name="see-also"></a>Siehe auch

[Konfigurieren der Portalauthentifizierung](configure-portal-authentication.md)  
[Festlegen der Authentifizierungsidentität für ein Portal](set-authentication-identity.md)  
[OAuth2-Anbietereinstellungen für Portale](configure-oauth2-settings.md)  
[OpenID Connect-Anbietereinstellungen für Portale](configure-openid-settings.md)  
[WS-Federation-Anbietereinstellungen für Portale](configure-ws-federation-settings.md)  

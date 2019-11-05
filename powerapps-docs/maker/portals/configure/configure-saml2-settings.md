---
title: Konfigurieren von SAML 2,0-Anbieter Einstellungen für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von SAML 2,0-Anbieter Einstellungen für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: af5b0ae8eddb68127c7271fccb4696a23fedfc60
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542742"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>Konfigurieren von SAML 2,0-Anbieter Einstellungen für Portale

Zum Bereitstellen externer Authentifizierung können Sie mindestens einen [SAML 2,0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)– kompatiblen Identitäts Anbieter (IDP) hinzufügen. In diesem Dokument wird beschrieben, wie Sie verschiedene Identitäts Anbieter für die Integration in ein Portal einrichten, das als Dienstanbieter fungiert.  

## <a name="ad-fs-idp"></a>AD FS (IDP)

Einstellungen für einen Identitäts Anbieter, z. b. [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)].

### <a name="create-an-ad-fs-relying-party-trust"></a>Erstellen einer AD FS Vertrauensstellung der vertrauenden Seite

> [!Note]
> Informationen dazu, wie Sie diese Schritte in einem [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] Skript ausführen, finden Sie weiter unten unter [Konfigurieren von AD FS mithilfe von PowerShell](#configure-ad-fs-by-using-powershell).

Wechseln Sie mithilfe des [!include[](../../../includes/pn-adfs-short.md)] Verwaltungs Tools zu **Dienst** > **Anspruchs Beschreibungen**.

1.  Wählen Sie **Anspruchs Beschreibung hinzufügen**aus.
2.  Geben Sie den Anspruch an:

    -  Anzeige Name: beständiger **Bezeichner**

    -  Anspruchs Bezeichner: **urn: Oasis: names: TC: SAML: 2.0: NameID-Format: persistent**

    -  **Aktivieren** des Kontrollkästchens für: veröffentlichen Sie diese Anspruchs Beschreibung in Verbund Metadaten als Anspruchstyp, der von diesem Verbund Dienst akzeptiert werden kann.

    -  **Aktivieren** des Kontrollkästchens für: veröffentlichen Sie diese Anspruchs Beschreibung in Verbund Metadaten als Anspruchstyp, den dieser Verbund Dienst senden kann.

3.  Wählen Sie **OK** aus.

Wählen Sie mit dem [!include[](../../../includes/pn-adfs-short.md)] Verwaltungs Tool Vertrauens Stellungen >Vertrauens Stellungen der **vertrauenden** **Seite**aus.

1. Wählen Sie Vertrauensstellung der **vertrauenden Seite hinzufügen**
2. Willkommen: Wählen Sie **Start**aus.
3. Datenquelle auswählen: Wählen Sie **die Option Daten über die vertrauende Seite manuell eingeben**aus, und klicken Sie dann auf **weiter**.
4. Anzeigen Amen angeben: Geben Sie einen Namen ein, und klicken Sie dann auf **weiter**.
   Beispiel: https://portal.contoso.com/
5. Wählen Sie Profil: Wählen Sie **AD FS 2,0-Profil**aus, und klicken Sie dann auf **weiter**.
6. Zertifikat konfigurieren: Klicken Sie auf **weiter**.
7. URL konfigurieren: Aktivieren Sie das Kontrollkästchen **Unterstützung für das SAML 2,0 WebSSO-Protokoll aktivieren** .
   SAML 2,0 SSO-Dienst-URL der vertrauenden Seite: Eingabe https://portal.contoso.com/signin-saml2
   - Hinweis: [!include[](../../../includes/pn-adfs-short.md)] erfordert, dass das Portal auf HTTPS ausgeführt wird.

   > [!Note] 
   > Der resultierende Endpunkt verfügt über die folgenden Einstellungen: 
   > - **Endpunkttyp: SAML-Assertionen verbrauchen Endpunkte**             
   > - Bindung: **Post**                                            
   > - Index: n/v (0)                                              
   > - URL: **https://portal.contoso.com/signin-saml2**

8. Konfigurieren von Identitäten: Geben Sie https://portal.contoso.com/ an, klicken Sie auf **Hinzufügen**, und wählen Sie dann **weiter**
   Gegebenenfalls können Sie weitere Identitäten für jedes zusätzliche Portal der vertrauenden Seite hinzufügen. Benutzer können sich über alle verfügbaren Identitäten hinweg authentifizieren.
9. Wählen Sie Ausstellungs Autorisierungs Regeln aus: Wählen Sie **allen Benutzern Zugriff auf diese vertrauende Seite gestatten**aus, und klicken Sie dann auf **weiter**.
10. Bereit zum Hinzufügen der Vertrauensstellung: Klicken Sie auf **weiter**
11. Klicken Sie auf **Schließen**.

Fügen Sie der Vertrauensstellung der vertrauenden Seite den Anspruch **namens-ID** hinzu:

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name** in **Name-ID** -Anspruch umwandeln (einen eingehenden Anspruch transformieren):

- Eingehender Anspruchstyp: **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Kontoname**

- Typ des ausgehenden Anspruchs: **namens-ID**

- ID-Format des ausgehenden namens: beständiger **Bezeichner**

- Alle Anspruchs Werte weiterleiten

### <a name="create-site-settings"></a>Erstellen von Site Einstellungen

Wenden Sie Portal Site Einstellungen an, die auf das obige [!include[](../../../includes/pn-adfs-short.md)] Vertrauensstellung der vertrauenden Seite verweisen

> [!Note]
> Eine IDP-Konfiguration (Standard [!include[](../../../includes/pn-adfs-short.md)]) verwendet nur die folgenden Einstellungen (mit Beispiel Werten): Authentication/saml2/ADFS/MetadataAddress-<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/saml2/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust    
>   -   Verwenden Sie den Wert des **EntityID** -Attributs im Root-Element der Verbund Metadaten (Öffnen Sie die **MetadataAddress-URL** in einem Browser, der der Wert der obigen Website Einstellung ist). 
> - Authentication/saml2/ADFS/serviceproviderrealm- https://portal.contoso.com/  
> - Authentifizierung/saml2/ADFS/assertionconsumerserviceurl- https://portal.contoso.com/signin-saml2  
>   Die Verbund **Metadaten** können in **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** abgerufen werden, indem Sie das folgende Skript auf dem [!include[](../../../includes/pn-adfs-short.md)] Server ausführen: `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

Sie können mehrere IDP-Dienste konfigurieren, indem Sie eine Bezeichnung für das Tag [Provider] ersetzen. Jede eindeutige Bezeichnung bildet eine Gruppe von Einstellungen, die mit einem IDP verknüpft sind. Beispiele: ADFS, [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD, myidp


| Name der Standort Einstellung                                             | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentifizierung/Registrierung/externzuweisung aktiviert              | Aktiviert oder deaktiviert die Anmeldung und Registrierung externer Konten. Standardwert: true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/saml2/[Anbieter]/MetadataAddress             | Erforderlich. Die Metadaten-URL des [WS-](https://msdn.microsoft.com/library/bb498017.aspx) Verbunds des STS-Servers ([!include[](../../../includes/pn-adfs-short.md)]). Dies endet häufig mit dem Pfad:/FederationMetadata/2007-06/FederationMetadata. Xml. Beispiel: `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`. [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/saml2/[Anbieter]/AuthenticationType          | Erforderlich. Der owin-Authentifizierungs-Middleware-Typ. Geben Sie den Wert des [EntityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) -Attributs im Stammverzeichnis der Verbund Metadaten-XML-Datei an. Beispiel: `https://adfs.contoso.com/adfs/services/trust`. [!include[](../../../includes/proc-more-information.md)] " [authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) "                                                            |  
| Authentication/saml2/[Anbieter]/ServiceProviderRealm<br>oder <br>Authentication/saml2/[Anbieter]/Wtrealm                      | Erforderlich. Der [!include[](../../../includes/pn-adfs-short.md)] Bezeichner der vertrauenden Seite. Beispiel: `https://portal.contoso.com/`. [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions. wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/saml2/[Anbieter]/AssertionConsumerServiceUrl<br>oder<br>Authentication/saml2/[Anbieter]/Wreply                       | Erforderlich. Der [!include[](../../../includes/pn-adfs-short.md)] SAML-Consumer-assertionsendpunkt. Beispiel: https://portal.contoso.com/signin-saml2. [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions. wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/saml2/[Anbieter]/Caption                     | Empfohlen. Der Text, den der Benutzer auf einer Anmelde Benutzeroberfläche anzeigen kann. Standardwert: [Provider]. [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions. Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/saml2/[Anbieter]/CallbackPath                | Ein optionaler eingeschränkter Pfad für die Verarbeitung des Authentifizierungs Rückrufs. [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions. callbackpath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/saml2/[Anbieter]/BackchannelTimeout          | Der Timeout Wert für die Back-Channel-Kommunikation. Beispiel: 00:05:00 (5 Minuten). [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions. backchanneltimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/saml2/[Anbieter]/UseTokenLifetime            | Gibt an, dass die Lebensdauer der Authentifizierungs Sitzung (z. b. Cookies) dem des Authentifizierungs Tokens entsprechen soll. [Wsfederationauthenticationoptions. usetokenlifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                                                                                               |  
| Authentication/saml2/[Anbieter]/authenticationMode          | Der owin-Authentifizierungs-Middleware-Modus. [!include[](../../../includes/proc-more-information.md)] " [authenticationoptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx) "                                                                                                                                                                                                                                                                              |  
| Authentication/saml2/[Anbieter]/SignInAsAuthenticationType  | Der beim Erstellen der System. Security. Claims. ClaimsIdentity verwendete AuthenticationType. [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions. signinasauthenticationtype](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/saml2/[Anbieter]/ValidAudiences              | Durch Trennzeichen getrennte Liste von Zielgruppen-URLs. [!include[](../../../includes/proc-more-information.md)] [tokenvalidationparameters. Zuweisung](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/saml2/[Anbieter]/ClockSkew                   | Die Zeit Schiefe, die beim Überprüfen der Zeiten angewendet werden soll.                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/saml2/[Anbieter]/RequireExpirationTime       | Ein Wert, der angibt, ob Token einen Ablauf Wert aufweisen müssen.                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/saml2/[Anbieter]/ValidateAudience            | Ein boolescher Wert, der steuert, ob die Zielgruppe während der tokenüberprüfung überprüft wird.                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>IDP-initiierte Anmeldung

[!include[](../../../includes/pn-adfs-short.md)] unterstützt das [IDP-initiierte Single Sign-on (SSO)-](https://technet.microsoft.com/library/jj127245.aspx) Profil der SAML 2,0- [Spezifikation](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline). Damit das Portal (Dienstanbieter) ordnungsgemäß auf die vom IDP initiierte SAML-Anforderung antwortet, muss der [relaystate](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) -Parameter ordnungsgemäß codiert werden.  

Der grundlegende Zeichen folgen Wert, der in den SAML-relaystate-Parameter codiert werden soll, muss im Format " **Rückkehrer" = "/Content/Sub-Content/** " vorliegen, wobei " **/Content/Sub-Content/** " der Pfad zu der Webseite ist, zu der Sie im Portal (Dienstanbieter) wechseln möchten. Der Pfad kann durch eine beliebige gültige Webseite im Portal ersetzt werden. Der Zeichen folgen Wert wird codiert und in einer Container Zeichenfolge mit dem Format **rpid =&lt;URL-codiertes rpid-&gt;& relaystate =&lt;URL-codiertes relaystate-&gt;** platziert. Die gesamte Zeichenfolge wird erneut codiert und einem anderen Container im Format **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> codierten rpid/relaystate-&gt;** hinzugefügt.

Wenn Sie z. b. den Dienstanbieter Pfad **/Content/Sub-Content/** und die ID der vertrauenden Seite **https://portal.contoso.com/** , erstellen Sie die URL mit den folgenden Schritten:

Codieren Sie den Wert "rückkehrnurl =/Content/Sub-Content/".

-   So erhalten Sie die wieder kehrmenge% 3D% 2fcontent% 2fsub-Content% 2F

<!-- -->

-   Codieren Sie den Wert https://portal.contoso.com/

<!-- -->

-   zum erhalten von HTTPS %3 a %2 f %2 f-Portal. %2 f

<!-- -->

-   Codieren Sie den Wert rpid = HTTPS %3 a %2 f %2 f Portal. %2 f %2 f & relaystate = wieder kehrnurl% 3D% 2F Content% 2F Sub-Content% 2F

<!-- -->

-   So erhalten Sie rpid %3 d HTTPS %2 5 3a %2 5 2F %2 5 2fportal. c% 252F% 26relaystate% 3dreturnurl% 253d% 252fcontent% 252fsub-Content% 252F

<!-- -->

-   Fügen Sie dem AD FS IDP-initiierten SSO-Pfad voran, um die endgültige URL zu erhalten.

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

Das folgende [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] Skript kann verwendet werden, um die URL zu erstellen (Speichern Sie in einer Datei namens Get-IdPInitiatedUrl. ps1).

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

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>SAML 2,0-Einstellungen für [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Der vorherige Abschnitt, der [!include[](../../../includes/pn-adfs-short.md)] beschreibt, kann auch auf [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)angewendet werden, da sich [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD wie ein standardmäßiger [SAML 2,0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;kompatibler IDP verhält. Melden Sie sich zunächst bei der [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] Verwaltungsportal](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) an, und erstellen oder wählen Sie ein vorhandenes Verzeichnis aus. Wenn ein Verzeichnis verfügbar ist, befolgen Sie die Anweisungen zum [Hinzufügen einer Anwendung](https://msdn.microsoft.com/library/azure/dn132599.aspx) zum Verzeichnis.  

1.  Wählen Sie im Menü**Anwendungen** des Verzeichnisses die Option **Hinzufügen**aus.
2.  Wählen Sie eine von meinem Unternehmen **entwickelte Anwendung hinzufügen**aus.
3.  Geben Sie einen benutzerdefinierten Namen für die Anwendung an, und wählen Sie dann den Typ **Webanwendung und/oder Web-API**aus.
4.  Geben Sie für die **Anmelde-URL** und den**App-ID-URI**die URL des Portals für beide Felder https://portal.contoso.com/ an.
    Dies entspricht dem **Service providerrealm** (wtrealm)-Website Einstellungs Wert.
5. An diesem Punkt wird eine neue Anwendung erstellt. Wechseln Sie im Menü zum Abschnitt **Konfigurieren** .

    Aktualisieren Sie im Abschnitt " **Single Sign-on** " den ersten **Antwort-URL** -Eintrag, um einen Pfad in der URL https://portal.contoso.com/signin-azure-ad einzuschließen.

    Dies entspricht dem Wert der Website Einstellung **assertionconsumerserviceurl** (wreply).

6. Wählen Sie im Fußzeile-Menü **Endpunkte anzeigen** aus, und notieren Sie sich das Feld Verbund **Metadaten-Dokument** .

Dies entspricht dem **MetadataAddress** -Website Einstellungs Wert.

-   Fügen Sie diese URL in einem Browserfenster ein, um die Verbund Metadaten-XML anzuzeigen, und notieren Sie sich das **EntityID** -Attribut des Root-Elements.
-   Dies entspricht dem Wert der Website Einstellung**AuthenticationType** .

> [!Note]
> Eine Standard [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD-Konfiguration verwendet nur die folgenden Einstellungen (mit Beispiel Werten): Authentication/saml2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentifizierung/saml2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType-<https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - Verwenden Sie den Wert des**EntityID** -Attributs im Root-Element der Verbund Metadaten (Öffnen Sie die**MetadataAddress-URL** in einem Browser, der der Wert der obigen Website Einstellung ist). 
> - Authentifizierung/saml2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/serviceproviderrealm-<https://portal.contoso.com/>  
> - Authentifizierung/saml2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/assertionconsumerserviceurl-<https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Shibboleth-Identitäts Anbieter 3

Verwenden Sie die folgenden Richtlinien, um den [Shibboleth-Identitäts Anbieter](https://wiki.shibboleth.net/confluence/display/IDP30/Home) ordnungsgemäß als IDP-Dienst zu konfigurieren. Im folgenden wird davon ausgegangen, dass der IDP auf dem Domänen https://idp.contoso.com gehostet wird.  

Die Verbund Metadaten-URL ist https://idp.contoso.com/idp/shibboleth

-   Der IDP muss so konfiguriert werden, dass er einen permanenten Bezeichner generiert oder bedient. Befolgen Sie die Anweisungen, um die [permanente bezeichnergenerierung](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration)zu aktivieren.  

-   Die IDP-Verbund Metadaten (&lt;idpssodescriptor&gt;) müssen so konfiguriert werden, dass Sie eine [SSO-Umleitungs Bindung](https://shibboleth.net/about/advanced.html)einschließen. [Beispiel](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample).  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

Konfigurieren Sie die Dienstanbieter (vertrauende Seiten), indem Sie die [Metadata-Providers. XML](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration)-Datei einrichten.  

-   Alle Verbund Metadaten des Dienstanbieters (&lt;spssodescriptor-&gt;) müssen einen Consumer-Consumerdienst nach der Bindung enthalten. Eine Möglichkeit besteht darin, ein [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) zu verwenden und auf eine Konfigurationsdatei zu verweisen, die Folgendes enthält:  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

Das Location-Attribut entspricht der Einstellung**assertionconsumerserviceurl** (wreply).

-   Die Verbund Metadaten des Dienstanbieters sollten ein **EntityID** -Attribut für den EntityDescriptor angeben, der der **AuthenticationType** -Einstellung entspricht.

**&lt;EntityDescriptor EntityID =<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> Eine standardmäßige Shibboleth-Konfiguration verwendet nur die folgenden Einstellungen (mit Beispiel Werten):   
> Authentifizierung/saml2/Shibboleth/MetadataAddress- https://idp.contoso.com/idp/shibboleth   
> -   Authentication/saml2/Shibboleth/AuthenticationType- https://idp.contoso.com/idp/shibboleth 
> -   Verwenden Sie den Wert des **EntityID** -Attributs im Root-Element der Verbund Metadaten (Öffnen Sie die **MetadataAddress-URL** in einem Browser, der der Wert der obigen Website Einstellung ist).  
> -   Authentication/saml2/Shibboleth/serviceproviderrealm- https://portal.contoso.com/ 
> -   Authentication/saml2/Shibboleth/assertionconsumerserviceurl- https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>IDP-initiierte Anmeldung

Shibboleth unterstützt das [IDP-initiierte SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) -Profil der SAML 2,0- [Spezifikation](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline). Damit das Portal (Dienstanbieter) ordnungsgemäß auf die vom IDP initiierte SAML-Anforderung antwortet, muss der relaystate-Parameter ordnungsgemäß codiert werden.  

Der grundlegende Zeichen folgen Wert, der in den SAML-relaystate-Parameter codiert werden soll, muss im Format " **Rückkehrer" = "/Content/Sub-Content/** " vorliegen, wobei " **/Content/Sub-Content/** " der Pfad zu der Webseite ist, zu der Sie im Portal (Dienstanbieter) wechseln möchten. Der Pfad kann durch eine beliebige gültige Webseite im Portal ersetzt werden. Die vollständige IDP-initiierte SSO-URL sollte im Format <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> codierte Anbieter-ID&gt;& Target =&lt;URL-codiertem Rückgabe Pfad&gt;sein.

Wenn z. b. der Dienstanbieter Pfad **/Content/Sub-Content/** und die ID der vertrauenden Seite **https://portal.contoso.com/** , ist die endgültige URL https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

Das folgende [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] Skript kann verwendet werden, um die URL zu erstellen (Speichern Sie in einer Datei namens Get-ShibbolethIdPInitiatedUrl. ps1).

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

## <a name="configure-ad-fs-by-using-powershell"></a>Konfigurieren von AD FS mithilfe von PowerShell

Der Vorgang zum Hinzufügen einer Vertrauensstellung der vertrauenden Seite in [!include[](../../../includes/pn-adfs-short.md)] kann auch durch Ausführen des folgenden [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] Skripts auf dem [!include[](../../../includes/pn-adfs-short.md)] Server ausgeführt werden (Speichern Sie die Inhalte in einer Datei namens Add-AdxPortalRelyingPartyTrustForSaml. ps1). Nachdem Sie das Skript ausgeführt haben, fahren Sie mit dem Konfigurieren der Portal Website Einstellungen fort.

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

[Konfigurieren der Portal Authentifizierung](configure-portal-authentication.md)  
[Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md)  
[OAuth2-Anbieter Einstellungen für Portale](configure-oauth2-settings.md)  
[Open ID Connect-Anbieter Einstellungen für Portale](configure-openid-settings.md)  
[WS-Verbund-Anbieter Einstellungen für Portale](configure-ws-federation-settings.md)  

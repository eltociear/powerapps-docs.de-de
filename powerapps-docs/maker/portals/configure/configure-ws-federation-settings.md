---
title: Konfigurieren von WS-Verbund-Anbieter Einstellungen für ein Portal | MicrosoftDocs
description: Anweisungen zum Hinzufügen und Konfigurieren von WS-Verbund-Anbieter Einstellungen für ein Portal.
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2a668f501a54472da0335344997c049794794783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542703"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>Konfigurieren von WS-Verbund-Anbieter Einstellungen für Portale

Ein einzelner [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] Verbund Dienste-Server kann (oder ein anderer [WS-](https://msdn.microsoft.com/library/bb498017.aspx)Verbund – konformer Sicherheitstokendienst) als Identitäts Anbieter hinzugefügt werden. Außerdem kann ein einzelner [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) -Namespace als Satz einzelner Identitäts Anbieter konfiguriert werden. Die Einstellungen für AD FS und ACS basieren auf den Eigenschaften der Klasse [wsfederationauthenticationoptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx) .

## <a name="create-an-ad-fs-relying-party-trust"></a>Erstellen einer AD FS Vertrauensstellung der vertrauenden Seite

Wechseln Sie mithilfe des AD FS Verwaltungs Tools zu Vertrauens Stellungen &gt; Vertrauens Stellungen der **vertrauenden** **Seite**.

1.  Wählen Sie Vertrauensstellung der **vertrauenden Seite hinzufügen**
2.  Willkommen: Wählen Sie **Start**aus.
3.  Datenquelle auswählen: Wählen Sie **die Option Daten über die vertrauende Seite manuell eingeben**aus, und klicken Sie dann auf **weiter**.
4.  Anzeigen Amen angeben: Geben Sie einen **Namen**ein, und klicken Sie dann auf **weiter**.
    Beispiel: https://portal.contoso.com/
5.  Wählen Sie Profil: Wählen Sie **AD FS 2,0-Profil**aus, und klicken Sie dann auf **weiter**.
6.  Zertifikat konfigurieren: Klicken Sie auf **weiter**.
7.  URL konfigurieren: Aktivieren Sie das Kontrollkästchen **Unterstützung für das passive WS-Verbund Protokoll aktivieren** .

Passive WS-Verbund-Protokoll-URL der vertrauenden Seite: Eingabe https://portal.contoso.com/signin-federation

-   Hinweis: AD FS erfordert, dass das Portal auf **https**ausgeführt wird.

    > [!Note]
    > Der resultierende Endpunkt verfügt über die folgenden Einstellungen: Endpunkttyp: **WS-** Verbund
    > -   Bindung: **Post**
    > -   Index: n/v (0)
    > -   URL: **https://portal.contoso.com/signin-federation**

8.  Konfigurieren von Identitäten: Geben Sie https://portal.contoso.com/ an, klicken Sie auf **Hinzufügen**, und wählen Sie dann **weiter**
    Gegebenenfalls können weitere Identitäten für jedes zusätzliche Portal der vertrauenden Seite hinzugefügt werden. Benutzer können sich über alle verfügbaren Identitäten hinweg authentifizieren.
9.  Wählen Sie Ausstellungs Autorisierungs Regeln aus: Wählen Sie **allen Benutzern Zugriff auf diese vertrauende Seite gestatten**aus, und klicken Sie dann auf **weiter**.
10.  Bereit zum Hinzufügen der Vertrauensstellung: Klicken Sie auf **weiter**
11.  Klicken Sie auf **Schließen**.

Fügen Sie der Vertrauensstellung der vertrauenden Seite den Anspruch **namens-ID** hinzu:

**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name** in **Name-ID** -Anspruch umwandeln (einen eingehenden Anspruch transformieren):
- Eingehender Anspruchstyp: Windows-Kontoname
- Typ des ausgehenden Anspruchs: namens-ID
- ID-Format des ausgehenden namens: nicht angegeben
- Alle Anspruchs Werte weiterleiten

### <a name="create-ad-fs-site-settings"></a>Erstellen AD FS Site Einstellungen

Wenden Sie Portal Site Einstellungen an, die auf das obige AD FS Vertrauensstellung der vertrauenden Seite verweisen

> [!Note]
> Eine Standard AD FS Konfiguration (STS) verwendet nur die folgenden Einstellungen (mit Beispiel Werten):
> - Authentifizierung/wsfederation/ADFS/MetadataAddress- https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/wsfederation/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust
>   - Verwenden Sie den Wert des **EntityID** -Attributs im Root-Element der Verbund Metadaten (Öffnen Sie die **MetadataAddress-URL** in einem Browser, der der Wert der obigen Website Einstellung ist).
> - Authentifizierung/wsfederation/ADFS/wtrealm- https://portal.contoso.com/
> - Authentifizierung/wsfederation/ADFS/wreply- https://portal.contoso.com/signin-federation

Die **WS-Verbund Metadaten** können in **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** abgerufen werden, indem das folgende Skript auf dem AD FS Server ausgeführt wird:

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      Name der Standort Einstellung                      |                                                                                                                                                                                                                                                 Beschreibung                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentifizierung/Registrierung/externzuweisung aktiviert       |                                                                                                                                                                                                                Aktiviert oder deaktiviert die Anmeldung und Registrierung externer Konten. Standardwert: true                                                                                                                                                                                                                 |
|      Authentifizierung/wsfederation/ADFS/MetadataAddress       | Erforderlich. Die Metadaten-URL des [WS-](https://msdn.microsoft.com/library/bb498017.aspx) Verbunds des STS-Servers (AD FS). Dies endet häufig mit dem Pfad:/FederationMetadata/2007-06/FederationMetadata. Xml. Beispiel:<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>. Weitere Informationen finden Sie unter [wsfederationauthenticationoptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx). |
|     Authentication/wsfederation/ADFS/AuthenticationType     |            Erforderlich. Der owin-Authentifizierungs-Middleware-Typ. Geben Sie den Wert des [EntityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) -Attributs im Stammverzeichnis der Verbund Metadaten-XML-Datei an. Beispiel: https://adfs.contoso.com/adfs/services/trust. Weitere Informationen finden Sie unter [authenticationoptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx).             |
|          Authentifizierung/wsfederation/ADFS/wtrealm           |                                                                                                              Erforderlich. Der AD FS Bezeichner der vertrauenden Seite. Beispiel: `https://portal.contoso.com/`. Weitere Informationen finden Sie unter [wsfederationauthenticationoptions. wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx).                                                                                                               |
|           Authentifizierung/wsfederation/ADFS/wreply           |                                                                                                     Erforderlich. Der passive Endpunkt des AD FS WS-Verbunds. Beispiel: https://portal.contoso.com/signin-federation. Weitere Informationen finden Sie unter [wsfederationauthenticationoptions. wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx).                                                                                                     |
|          Authentifizierung/wsfederation/ADFS/Beschriftung           |                                                                                                           Empfohlen. Der Text, den der Benutzer auf einer Anmelde Benutzeroberfläche anzeigen kann. Standard: ADFS. Weitere Informationen finden Sie unter [wsfederationauthenticationoptions. Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx).                                                                                                            |
|        Authentication/wsfederation/ADFS/callbackpath        |                                                                                                             Ein optionaler eingeschränkter Pfad für die Verarbeitung des Authentifizierungs Rückrufs. Weitere Informationen finden Sie unter [wsfederationauthenticationoptions. callbackpath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx).                                                                                                              |
|       Authentifizierung/wsfederation/ADFS/signoutwreply        |                                                                                                                               Der während der Abmeldung verwendete "wreply"-Wert. Weitere Informationen finden Sie unter [wsfederationauthenticationoptions. signoutwreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx).                                                                                                                               |
|     Authentifizierung/wsfederation/ADFS/backchanneltimeout     |                                                                                                         Der Timeout Wert für die Back-Channel-Kommunikation. Beispiel: 00:05:00 (5 Minuten). Weitere Informationen finden Sie unter: [wsfederationauthenticationoptions. backchanneltimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx).                                                                                                         |
| Authentication/wsfederation/ADFS/aktuauthentication/aktuneissuerkeynotfound |                                                                                  Bestimmt, ob nach der securitytokensignaturekeynotfoundexception eine Metadatenaktualisierung versucht werden soll. Weitere Informationen finden Sie unter: [wsfederationauthenticationoptions. authentionissuerkeynotfound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx).                                                                                  |
|      Authentifizierung/wsfederation/ADFS/usetokenlifetime      |                                                                                                   Gibt an, dass die Lebensdauer der Authentifizierungs Sitzung (z. b. Cookies) dem des Authentifizierungs Tokens entsprechen soll. [Wsfederationauthenticationoptions. usetokenlifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx).                                                                                                   |
|     Authentifizierung/wsfederation/ADFS/authenticationMode     |                                                                                                                                            Der owin-Authentifizierungs-Middleware-Modus. Weitere Informationen finden Sie unter [authenticationoptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx).                                                                                                                                             |
| Authentication/wsfederation/ADFS/signinasauthenticationtype |                                                                                            Der beim Erstellen der System. Security. Claims. ClaimsIdentity verwendete AuthenticationType. Weitere Informationen finden Sie unter [wsfederationauthenticationoptions. signinasauthenticationtype](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx).                                                                                            |
|       Authentifizierung/wsfederation/ADFS/validaudiences       |                                                                                                                                         Durch Trennzeichen getrennte Liste von Zielgruppen-URLs. Weitere Informationen finden Sie unter [tokenvalidationparameters. Zuweisung](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx).                                                                                                                                          |
|        Authentifizierung/wsfederation/ADFS/Validierer        |                                                                                                                                              Durch Trennzeichen getrennte Liste der Aussteller-URLs. Weitere Informationen finden Sie unter [tokenvalidationparameters. valider](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx).                                                                                                                                               |
|         Authentifizierung/wsfederation/ADFS/clockschief          |                                                                                                                                                                                                                               Die Zeit Schiefe, die beim Überprüfen der Zeiten angewendet werden soll.                                                                                                                                                                                                                                |
|       Authentication/wsfederation/ADFS/nameclaimtype        |                                                                                                                                                                                                                     Der Anspruchstyp, der von der ClaimsIdentity zum Speichern des Namens Anspruchs verwendet wird.                                                                                                                                                                                                                      |
|       Authentication/wsfederation/ADFS/roleclaimtype        |                                                                                                                                                                                                                     Der Anspruchstyp, der von der ClaimsIdentity zum Speichern des Rollen Anspruchs verwendet wird.                                                                                                                                                                                                                      |
|   Authentifizierung/wsfederation/ADFS/Requirements ExpirationTime    |                                                                                                                                                                                                                     Ein Wert, der angibt, ob Token über einen Wert vom Typ "Ablauf" verfügen müssen.                                                                                                                                                                                                                      |
|    Authentifizierung/wsfederation/ADFS/Requirements signedtokens     |                                                                                                                                                                       Ein Wert, der angibt, ob ein System. IdentityModel. Tokens. SecurityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> gültig sein kann, wenn es nicht signiert ist.                                                                                                                                                                       |
|      Authentifizierung/wsfederation/ADFS/savesignintoken       |                                                                                                                                                                                                               Ein boolescher Wert, der steuert, ob das ursprüngliche Token gespeichert wird, wenn eine Sitzung erstellt wird.                                                                                                                                                                                                                |
|       Authentifizierung/wsfederation/ADFS/validateactor        |                                                                                                                                                                                                   Ein Wert, der angibt, ob System. IdentityModel. Tokens. jwtsecuritytoken. Actor überprüft werden soll.                                                                                                                                                                                                    |
|      Authentifizierung/wsfederation/ADFS/validateaudience      |                                                                                                                                                                                                               Ein boolescher Wert, der steuert, ob die Zielgruppe während der tokenüberprüfung überprüft wird.                                                                                                                                                                                                               |
|       Authentifizierung/wsfederation/ADFS/validateissuer       |                                                                                                                                                                                                                Ein boolescher Wert, der steuert, ob der Aussteller während der tokenüberprüfung überprüft wird.                                                                                                                                                                                                                |
|      Authentifizierung/wsfederation/ADFS/validatelifetime      |                                                                                                                                                                                                               Ein boolescher Wert, der steuert, ob die Gültigkeitsdauer während der tokenüberprüfung überprüft wird.                                                                                                                                                                                                               |
|  Authentication/wsfederation/ADFS/validateissuersigningkey  |                                                                                                                                                         Ein boolescher Wert, der steuert, ob die Überprüfung des System. IdentityModel. Tokens. SecurityKey-Elements, das die SecurityToken-xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> signiert hat, aufgerufen wird.                                                                                                                                                          |
|            Authentifizierung/wsfederation/ADFS/WHR             |                                                                                                                                       Gibt einen "whr"-Parameter in der Umleitungs-URL des Identitäts Anbieters an. Weitere Informationen finden Sie unter [wsfederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation).                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>WS-Verbund Einstellungen für [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]

Der vorherige Abschnitt, der AD FS beschreibt, kann auch auf [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)) angewendet werden, da sich [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD wie ein standardmäßiger [WS-Verbund-](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide) kompatibler Sicherheitstokendienst verhält. Melden Sie sich zum Einstieg beim [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] Verwaltungsportal](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal) an, und erstellen oder wählen Sie ein vorhandenes Verzeichnis aus. Wenn ein Verzeichnis verfügbar ist, befolgen Sie die Anweisungen zum [Hinzufügen einer Anwendung](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) zum Verzeichnis.

1.  Wählen Sie im Menü **Anwendungen** des Verzeichnisses die Option **Hinzufügen**aus.
2.  Wählen Sie eine von meinem Unternehmen **entwickelte Anwendung hinzufügen**aus.
3.  Geben Sie einen benutzerdefinierten **Namen** für die Anwendung an, und wählen Sie dann den Typ **Webanwendung und/oder Web-API**aus.
4.  Geben Sie für die **Anmelde-URL** und den **App-ID-URI**die URL des Portals für beide Felder https://portal.contoso.com/ an.
    - Dies entspricht dem Wert der **wtrealm** -Website Einstellung.
5.  An diesem Punkt wird eine neue Anwendung erstellt. Wechseln Sie im Menü zum Abschnitt **Konfigurieren** .
6.  Aktualisieren Sie im Abschnitt " **Single Sign-on** " den ersten **Antwort-URL** -Eintrag, um einen Pfad in der URL https://portal.contoso.com/signin-azure-ad einzuschließen.
    - Dies entspricht dem Wert der **wreply** -Website Einstellung.
7.  Wählen Sie in der Fußzeile **Speichern** aus.
8.  Wählen Sie im Fußzeile-Menü **Endpunkte anzeigen** aus, und notieren Sie sich das Feld Verbund **Metadaten-Dokument** .

    - Dies entspricht dem **MetadataAddress** -Website Einstellungs Wert.
    - Fügen Sie diese URL in einem Browserfenster ein, um die Verbund Metadaten-XML anzuzeigen, und notieren Sie sich das **EntityID** -Attribut des Root-Elements.
    - Dies entspricht dem Wert der Website Einstellung **AuthenticationType** .

> [!Note]
> Eine Standard-[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD-Konfiguration verwendet nur die folgenden Einstellungen (mit Beispiel Werten):
> - Authentifizierung/wsfederation/ADFS/MetadataAddress- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/wsfederation/ADFS/AuthenticationType- https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - Verwenden Sie den Wert des **EntityID** -Attributs im Root-Element der Verbund Metadaten (Öffnen Sie die **MetadataAddress-URL** in einem Browser, der der Wert der obigen Website Einstellung ist).
> - Authentifizierung/wsfederation/ADFS/wtrealm- https://portal.contoso.com/
> - Authentifizierung/wsfederation/ADFS/wreply- https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>Siehe auch

[Konfigurieren der Portal Authentifizierung](configure-portal-authentication.md)  
[Festlegen der Authentifizierungs Identität für ein Portal](set-authentication-identity.md)  
[OAuth2-Anbieter Einstellungen für Portale](configure-oauth2-settings.md)  
[Open ID Connect-Anbieter Einstellungen für Portale](configure-openid-settings.md)  
[SAML 2,0-Anbieter Einstellungen für Portale](configure-saml2-settings.md)  

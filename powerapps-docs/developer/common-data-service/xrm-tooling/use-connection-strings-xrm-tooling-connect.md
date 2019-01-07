---
title: Verwenden von Verbindungszeichenfolgen in XRM-Tooling zum Verbinden mit Common Data Service für Apps (Common Data Service für Apps) | Microsoft Docs
description: XRM-Tooling ermöglicht Ihnen die Verbindung mit Ihrer Common Data Service für Apps-Umgebung durch Verwendung von Verbindungszeichenfolgen
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a98b2fce-df49-4b60-91f4-a4446aa61cd3
caps.latest.revision: 21
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-connection-strings-in-xrm-tooling-to-connect-to-common-data-service-for-apps"></a>Verwenden von Verbindungszeichenfolgen in XRM-Tooling zum Verbinden mit Common Data Service für Apps

Mit CDS für Apps ermöglicht das XRM-Tooling Ihnen die Verbindung mit Ihrer CDS für Apps-Umgebung durch Verwendung von Verbindungszeichenfolgen. Dies ähnelt dem Konzept von Verbindungszeichenfolgen, das in SQL Server verwendet wird. Verbindungszeichenfolgen erhalten native Unterstützung in Konfigurationsdateien inklusive der Möglichkeit der Verschlüsselung der Konfigurationsabschnitte für maximale Sicherheit. Dies ermöglicht es Ihnen, CDS für Apps-Verbindungen zur Bereitstellungszeit zu konfigurieren und nicht hartcodiert in der Anwendung, um eine Verbindung zu Ihrer CDS für Apps-Umgebung herzustellen.  
  
<a name="Create"></a> 

## <a name="create-a-connection-string"></a>Erstellen einer Verbindungszeichenfolge

 Sie geben diese Verbindungszeichenfolge in der Datei app.config oder web.config für das Projekt an, wie im folgenden Beispiel angezeigt.  
  
```xml  
<connectionStrings>  
    <add name="MyCDSServer" connectionString="AuthType=AD;Url=http://contoso:8080/Test;" />  
</connectionStrings>  
```  
  
> [!IMPORTANT]
>  Wenn Sie vertrauliche Informationen zur Datei app.config oder web.config hinzufügen, z. B. ein Firmenkennwort, müssen Sie sicherstellen, dass geeignete Sicherheitsvorkehrungen zum Schutz dieser Informationen getroffen werden.  
  
 Nachdem Sie die Verbindungszeichenfolge erstellt haben, verwenden Sie diese, um ein <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Objekt zu erstellen.  
  
```csharp  
//Use the connection string named "MyCDSServer"  
//from the configuration file  
CrmServiceClient crmSvc = new CrmServiceClient(ConfigurationManager.ConnectionStrings["MyCDSServer"].ConnectionString);  
```  
  
> [!NOTE]
>  Sie müssen die folgende `using`-Direktive in Ihrem Code verwenden, um auf den `System.Configuration`-Namespace verweisen, um auf die Verbindungszeichenfolge in Ihrem Code zuzugreifen: `using System.Configuration;`  
  
 Nachdem Sie ein <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Objekt erstellt haben, können Sie das Objekt verwenden, um Aktionen in CDS für Apps auszuführen. Weitere Informationen: [XRM-Tooling zur Ausführung von Aktionen in CDS für Apps verwenden](use-xrm-tooling-execute-actions.md)  
  
<a name="Parameters"></a>

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen

 Die Verbindungszeichenfolge enthält eine Reihe von Name-Wert-Paaren, getrennt durch Semikolons. Die folgende Tabelle enthält unterstützte Parameter, die in beliebiger Reihenfolge eingegeben werden können.  
  
|Parametername|Beschreibung|  
|--------------------|-----------------|  
|`ServiceUri`, `Service Uri`, `Url` oder `Server`|Gibt die URL für die CDS für Apps-Umgebung an. Die URL kann das http- oder https-Protokoll verwenden, und der Port ist optional. Standardmäßig wird der Port 80 für das http-Protokoll und 443 für das https-Protokoll verwendet. Die Server-URL ist normalerweise im Format `https://`*`<organization-name>`*`.crm.dynamics.com`<br /><br /> Der Organisationsname muss angegeben werden.|  
|`Domain`|Gibt die Domäne an, die Anmeldeinformationen von Benutzern überprüft.|  
|`UserName`, `User Name`, `UserId` oder `User Id`|Gibt die Benutzerkennung an, die den Anmeldeinformationen zugeordnet ist.|  
|`Password`|Gibt das Kennwort für den Benutzernamen, das den Anmeldeinformationen zugeordnet ist.|  
|`HomeRealmUri` oder `Home Realm Uri`|Gibt den Startbereichs-URL an.|  
|`AuthenticationType` oder `AuthType`|Gibt den Authentifizierungstyp an, um eine Verbindung mit der CDS für Apps-Umgebung herzustellen. Gültige Werte sind: `AD`, `IFD` (AD FS) aktiviert, `OAuth` oder `Office365`.<br /><br /> -   `AD` und `IFD` sind nur für lokale CDS für Apps-Umgebungen zulässig.<br />-   `OAuth` ist für CDS für Apps- und lokale Umgebungen zulässig.<br />-   `Office365` ist nur für CDS für Apps-Umgebungen zulässig.|  
|`RequireNewInstance`|Definiert, ob die vorhandene Verbindung wieder verwendet wird, wenn  Sie aufgerufen wird, solange die Verbindung noch aktiv ist. Standardwert ist `false`, der angibt, dass die bestehende Verbindung wiederverwendet wird. Wenn auf `true` festgelegt, wird das System gezwungen, eine eindeutige Verbindung herzustellen.|  
|`ClientId`, `AppId` oder `ApplicationId`|Gibt die `ClientID` an, die zugewiesen wird, wenn Sie Ihre Anwendung in Azure Active Directory oder in Active Directory Federation Services (AD FS) registriert haben.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`RedirectUri` oder `ReplyUrl`|Gibt die Umleitungs-URI der Anwendung an, die Sie in Azure Active Directory oder in Active Directory Federation Services (AD FS) registriert haben.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`TokenCacheStorePath`|Gibt den vollständigen Pfad zum Speicherort an, an dem der Benutzertoken gespeichert werden soll. Der laufende Prozess muss über Zugriff auf den angegebenen Pfad verfügen. Es ist die Prozesszuständigkeit, diesen Pfad festzulegen und zu konfigurieren.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`LoginPrompt`|Gibt an, ob der Benutzer zur Eingabe der Anmeldeinformationen aufgefordert wird, wenn die Anmeldeinformationen nicht angegeben wurden. Gültige Werte sind:<br /><br /> -   `Always`: Fordert immer den Benutzer auf, Anmeldeinformationen anzugeben.<br />-   `Auto`: Ermöglicht dem Benutzer, in der Anmeldungssteuerelement-Benutzeroberfläche auszuwählen, ob die Eingabeaufforderung angezeigt wird oder nicht.<br />-   `Never`: Fordert den Benutzer nicht auf, Anmeldeinformationen anzugeben. Wenn für die Verwendung einer Verbindungsmethode keine Benutzeroberfläche bereitgestellt wird, müssen Sie diesen Wert verwenden.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`StoreName` oder `CertificateStoreName`|Definiert den Speichernamen, unter dem das Zertifikat für den Fingerabdruck gefunden wird. Wenn festgelegt, ist der Fingerabdruck erforderlich.|
|`Thumbprint` oder `CertThumbprint`| Definiert den Fingerabdruck des Zertifikats, der während einer S2S-Verbindung verwendet wird. Wenn festgelegt, ist die AppID erforderlich und die Benutzer-ID und das Kennwort werden ignoriert.|
|`SkipDiscovery`|Gibt an, ob Instanz-Erkennung aufgerufen wird, um die Verbindungs-uri für eine bestimmte Instanz zu bestimmen. Ab Nuget-Version Microsoft.CrmSdk.XrmTooling.CoreAssembly 9.0.2.7, Standard = true. Standard der ältere Versionen ist false. <br/> Hinweis: Wenn Sie true  festlegen, ist es wichtig, dass der Benutzer den entsprechenden und präzisen URI für die Zielinstanz zur Verfügung hat.| 
  
<a name="Examples"></a>

## <a name="connection-string-examples"></a>Beispiele für Verbindungszeichenfolgen
 
Die folgenden Beispiele veranschaulichen, wie Sie Verbindungszeichenfolgen für die Verbindung mit Bereitstellungen und Authentifizierungsszenarien verwenden können.  

<!-- TODO: Get rid of on-premises examples & settings? or just comment them out? -->

<!-- ### Integrated on-premises authentication  
  
```xml
<add name="MyCRMServer" connectionString="AuthType=AD;Url=http://contoso:8080/Test;" />  
```  
  
### Named account using on-premises authentication  
  
```xml  
<add name="MyCRMServer" connectionString="AuthType=AD;Url=http://contoso:8080/Test; Domain=CONTOSO; Username=jsmith; Password=passcode" />  
```  
   -->
### <a name="named-account-using-office-365"></a>Benanntes Konto unter Verwendung von Office 365  
  
```xml
<add name="MyCDSServer" 
 connectionString="
  AuthType=Office365;
  Username=jsmith@contoso.onmicrosoft.com; 
  Password=passcode;
  Url=https://contoso.crm.dynamics.com"/>  
```  
  
### <a name="oauth-using-named-account-in-office-365-with-ux-to-prompt-for-authentication"></a>OAuth unter Verwendung des benannten Kontos in Office 365 mit UX zur Abfrage der Authentifizierungsbestätigung  
  
```xml
<add name="MyCDSServer"
 connectionString="
  AuthType=OAuth;
  Username=jsmith@contoso.onmicrosoft.com;
  Password=passcode;
  Url=https://contosotest.crm.dynamics.com;
  AppId=<GUID>;
  RedirectUri =app://<GUID>;
  TokenCacheStorePath =c:\MyTokenCache;
  LoginPrompt=Auto"/>  
```  
  
<!-- ### OAuth using named account in CDS for Apps on-premises with UX to prompt for authentication  
  
```xml
<add name="MyCRMServer" connectionString="AuthType=OAuth;Username=jsmith@contoso.onmicrosoft.com; Password=passcode;Url=https://contoso:8080/Test;AppId=<GUID>;RedirectUri=app://<GUID>;TokenCacheStorePath =c:\MyTokenCache;LoginPrompt=Auto"/>  
```  
  
### IFD using a named account with delegation to a sub realm  
  
```xml
<add name="MyCRMServer" connectionString="AuthType=IFD;Url=http://contoso:8080/Test; HomeRealmUri=https://server-1.server.com/adfs/services/trust/mex/;Domain=CONTOSO; Username=jsmith; Password=passcode" />  
```   -->

### <a name="certificate-based-authentication"></a>Zertifikatsbasierte Authentifizierung

```xml
<add name="MyCDSServer" 
  connectionString="
  AuthType=Certificate;
  SkipDiscovery=true;
  url={InstanceUri};
  thumbprint={CertThumbPrintId};
  ClientId={AppId};
  RequireNewInstance=true"
  />
```

  
<a name="ConnectionStatus"></a>

## <a name="determine-your-connection-status"></a>Bestimmung Ihres Verbindungsstatus

 Um zu bestimmen, ob die Verbindungsaufforderung erfolgreich war, überprüfen Sie den Wert für <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.IsReady>. -Eigenschaft verfügbar. Wenn der Wert **true** ist, ist die Verbindung erfolgreich undSie können mit der Arbeit beginnen. Andernfalls überprüfen Sie die Werte der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmError>- und <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmException>- Eigenschaften, um die Ursache für den Verbindungsfehler festzustellen.  
  
### <a name="see-also"></a>Siehe auch

[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)<br />
[CrmServiceClient-Konstruktoren verwenden, um eine Verbindung mit CDS für Apps herzustellen](use-crmserviceclient-constructors-connect.md)<br />
[XRM-Tooling zur Ausführung von Aktionen in CDS für Apps verwenden](use-xrm-tooling-execute-actions.md)<br />
<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>

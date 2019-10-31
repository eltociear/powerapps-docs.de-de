---
title: 'Verwenden Sie Verbindungszeichenfolgen in XRM-Tools, um eine Verbindung zu Common Data Service (Common Data Service)| Microsoft Docs herzustellen.'
description: 'XRM-Tools ermöglichen es Ihnen, sich mit Ihrer Common Data Service-Umgebung zu verbinden, indem Sie Verbindungszeichenfolgen verwenden.'
ms.custom: ''
ms.date: 03/27/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a98b2fce-df49-4b60-91f4-a4446aa61cd3
caps.latest.revision: 21
author: MattB-msft
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-connection-strings-in-xrm-tooling-to-connect-to-common-data-service"></a>Verwenden Sie Verbindungszeichenfolgen in XRM-Tools, um eine Verbindung mit Common Data Service herzustellen.

Mit Common Data Service ermöglicht XRM-Tooling die Verbindung zu Ihrer Common Data Service-Umgebung über Verbindungszeichenfolgen. Dies ähnelt dem Konzept von Verbindungszeichenfolgen, das in **SQL Server** verwendet wird. Verbindungszeichenfolgen erhalten native Unterstützung in Konfigurationsdateien inklusive der Möglichkeit der Verschlüsselung der Konfigurationsabschnitte für maximale Sicherheit. Dies ermöglicht es Ihnen, Common Data Service-Verbindungen zur Bereitstellungszeit zu konfigurieren und nicht harten Code in Ihrer Anwendung, um eine Verbindung zu Ihrer Common Data Service-Umgebung herzustellen.  


<a name="Create"></a> 

## <a name="create-a-connection-string"></a>Erstellen einer Verbindungszeichenfolge

 Sie geben diese Verbindungszeichenfolge in der Datei `app.config` oder `web.config` für das Projekt an, wie im folgenden Beispiel angezeigt.  
  
```xml  
<connectionStrings>  
    <add name="MyCDSServer" connectionString="AuthType=Office365;Url=http://contoso:8080/Test;UserName=jsmith@contoso.onmicrosoft.com; 
  Password=passcode" />  
</connectionStrings>  
```  
  
> [!IMPORTANT]
> Wenn Sie vertrauliche Informationen zu `app.config` oder `web.config file` hinzufügen, z. B. ein Firmenkennwort, müssen Sie sicherstellen, dass geeignete Sicherheitsvorkehrungen zum Schutz dieser Informationen getroffen werden.  
  
 Nachdem Sie die Verbindungszeichenfolge erstellt haben, verwenden Sie diese, um ein <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Objekt zu erstellen.  
  
```csharp  
//Use the connection string named "MyCDSServer"  
//from the configuration file  
CrmServiceClient svc = new CrmServiceClient(ConnectionString);  
```  
  
> [!NOTE]
> Sie müssen die folgende `using`-Direktive in Ihrem Code verwenden, um auf den `System.Configuration`-Namespace verweisen, um auf die Verbindungszeichenfolge in Ihrem Code zuzugreifen: `using System.Configuration;`  
  
 Nachdem Sie ein <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Objekt erstellt haben, können Sie mit diesem Objekt Aktionen in Common Data Service durchführen. Mehr Informationen: [Verwenden Sie XRM-Tools, um Aktionen in Common Data Service auszuführen](use-xrm-tooling-execute-actions.md)  
  
<a name="Parameters"></a>

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen

 Die Verbindungszeichenfolge enthält eine Reihe von Name-Wert-Paaren, getrennt durch Semikolons. Die folgende Tabelle enthält unterstützte Parameter, die in beliebiger Reihenfolge eingegeben werden können.  
  
|Parametername|Beschreibung|  
|--------------------|-----------------|  
|`ServiceUri`, `Service Uri`, `Url` oder `Server`|Gibt die URL zur Umgebung Common Data Service an. Die URL kann das http- oder https-Protokoll verwenden, und der Port ist optional. Standardmäßig wird der Port 80 für das http-Protokoll und 443 für das https-Protokoll verwendet. Die Server-URL ist normalerweise im Format `https://`*`<organization-name>`*`.crm.dynamics.com`<br /><br /> Der Organisationsname muss angegeben werden.|  
|`Domain`|Gibt die Domäne an, die Anmeldeinformationen von Benutzern überprüft.|  
|`UserName`, `User Name`, `UserId` oder `User Id`|Gibt die Benutzerkennung an, die den Anmeldeinformationen zugeordnet ist.|  
|`Password`|Gibt das Kennwort für den Benutzernamen, das den Anmeldeinformationen zugeordnet ist.|  
|`HomeRealmUri` oder `Home Realm Uri`|Gibt den Startbereichs-URL an.|  
|`AuthenticationType` oder `AuthType`|Gibt den Authentifizierungstyp an, mit dem die Verbindung zur Common Data Service-Umgebung hergestellt werden soll. Gültige Werte sind: `AD`, `IFD` (AD FS) aktiviert, `OAuth` oder `Office365`.<br /><br /> -   `AD` und `IFD` sind nur für lokale Common Data Service Umgebungen zulässig.<br />-   `OAuth` ist für Common Data Service und lokale Umgebungen zulässig.<br />-   `Office365` ist nur für Common Data Service Umgebungen erlaubt.|  
|`RequireNewInstance`|Definiert, ob die vorhandene Verbindung wieder verwendet wird, wenn  Sie aufgerufen wird, solange die Verbindung noch aktiv ist. Standardwert ist `false`, der angibt, dass die bestehende Verbindung wiederverwendet wird. Wenn auf `true` festgelegt, wird das System gezwungen, eine eindeutige Verbindung herzustellen.|  
|`ClientId`, `AppId` oder `ApplicationId`|Gibt die `ClientID` an, die bei der Registrierung Ihrer Anwendung in Azure Active Directory oder Active Directory Federation Services (AD FS) zugewiesen wurde.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`RedirectUri` oder `ReplyUrl`|Gibt die Redirect-URI der Anwendung an, die Sie in Azure Active Directory oder Active Directory Federation Services (AD FS) registriert haben.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`TokenCacheStorePath`|Gibt den vollständigen Pfad zum Speicherort an, an dem der Benutzertoken gespeichert werden soll. Der laufende Prozess muss über Zugriff auf den angegebenen Pfad verfügen. Es ist die Prozesszuständigkeit, diesen Pfad festzulegen und zu konfigurieren.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`LoginPrompt`|Gibt an, ob der Benutzer zur Eingabe der Anmeldeinformationen aufgefordert wird, wenn die Anmeldeinformationen nicht angegeben wurden. Gültige Werte sind:<br /><br /> -   `Always`: Fordert immer den Benutzer auf, Anmeldeinformationen anzugeben.<br />-   `Auto`: Ermöglicht dem Benutzer, in der Anmeldungssteuerelement-Benutzeroberfläche auszuwählen, ob die Eingabeaufforderung angezeigt wird oder nicht.<br />-   `Never`: Fordert den Benutzer nicht auf, Anmeldeinformationen anzugeben. Wenn für die Verwendung einer Verbindungsmethode keine Benutzeroberfläche bereitgestellt wird, müssen Sie diesen Wert verwenden.<br /><br /> Dieser Parameter gilt nur, wenn `OAuth` als Authentifizierungstyp angegeben ist.|  
|`StoreName` oder `CertificateStoreName`|Definiert den Speichernamen, unter dem das Zertifikat für den Fingerabdruck gefunden wird. Wenn festgelegt, ist der Fingerabdruck erforderlich.|
|`Thumbprint` oder `CertThumbprint`| Definiert den Fingerabdruck des Zertifikats, der während einer S2S-Verbindung verwendet wird. Wenn festgelegt, ist die AppID erforderlich und die Benutzer-ID und das Kennwort werden ignoriert.|
|`SkipDiscovery`|Gibt an, ob Instanz-Erkennung aufgerufen wird, um die Verbindungs-URI für eine bestimmte Instanz zu bestimmen. Ab NuGet Release Microsoft.CrmSdk.XrmTooling.CoreAssembly Version 9.0.2.7, default = true. Standard der ältere Versionen ist false. <br/> Hinweis: Wenn Sie true  festlegen, ist es wichtig, dass der Benutzer den entsprechenden und präzisen URI für die Zielinstanz zur Verfügung hat.|

<a name="Examples"></a>

## <a name="connection-string-examples"></a>Beispiele für Verbindungszeichenfolgen
 
Die folgenden Beispiele veranschaulichen, wie Sie Verbindungszeichenfolgen für die Verbindung mit Online-Bereitstellungen und Authentifizierungsszenarien verwenden können. Die Beispiele für Verbindungszeichenfolgen für lokale und IFD-Deployment-Instanzen sind nun in der Dokumentation Dynamics 365 Customer Engagement (on-premises) unter: [Verwenden Sie Verbindungszeichenfolgen in XRM-Tools, um eine Verbindung herzustellen](/dynamics365/customer-engagement/on-premises/developer/xrm-tooling/use-connection-strings-xrm-tooling-connect). 

### <a name="named-account-using-office-365"></a>Benanntes Konto mit Office 365.  
  
```xml
<add name="MyCDSServer" 
 connectionString="
  AuthType=Office365;
  Username=jsmith@contoso.onmicrosoft.com; 
  Password=passcode;
  Url=https://contoso.crm.dynamics.com"/>  
```  
  
### <a name="oauth-using-named-account-in-office-365-with-ux-to-prompt-for-authentication"></a>OAuth mit benanntem Konto in Office 365 mit UX zur Abfrage der Authentifizierung  
  
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
[Verwenden Sie CrmServiceClient Konstruktoren, um sich mit Common Data Service zu verbinden.](use-crmserviceclient-constructors-connect.md)<br />
[Verwenden Sie XRM-Tools, um Aktionen in Common Data Service auszuführen](use-xrm-tooling-execute-actions.md)<br />
<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>

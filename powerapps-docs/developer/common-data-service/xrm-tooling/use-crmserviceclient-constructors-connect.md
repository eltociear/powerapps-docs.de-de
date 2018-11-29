---
title: 'CrmServiceClient-Konstruktoren verwenden, um eine Verbindung mit CDS für Apps herzustellen (Common Data Service für Apps) | Microsoft Docs'
description: 'Sie können eine Instanz der CrmServiceClient-Klasse herstellen und nutzen dann einen der Konstruktoren, um eine Verbindung zu Common Data Service für Apps herzustellen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 74862506-a955-4846-a148-ac266f65592f
caps.latest.revision: 27
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-crmserviceclient-constructors-to-connect-to-cds-for-apps"></a>CrmServiceClient-Konstruktoren verwenden, um eine Verbindung mit CDS für Apps herzustellen

Wenn Sie eine Verbindung mit CDS für Apps herstellen, erstellen Sie eine Instanz der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse und nutzen dann einen der Konstruktoren, um eine Verbindung herzustellen. Alle Aufrufe zu CDS für Apps unter Verwendung der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse sind threadsicher.  
  
Abgesehen von den Konstruktoren, die in diesem Thema beschrieben werden, können Sie auch Verbindungszeichenfolgen mit <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> verwenden, um eine Verbindung mit CDS für Apps herzustellen. Weitere Informationen: [Verwenden von Verbindungszeichenfolgen in XRM-Tooling zum Verbinden mit CDS für Apps](use-connection-strings-xrm-tooling-connect.md)  
  
<a name="orgServiceproxy"></a>

## <a name="connect-to-cds-for-apps-using-organizationserviceproxy"></a>Mithilfe von OrganizationServiceProxy zu CDS für Apps verbinden

 Verwenden Sie nachfolgenden Konstruktor, um eine Verbindung mit CDS für Apps mithilfe der vom Benutzer zur Verfügung gestellten <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>-Instanz herzustellen.  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient(<externalOrgServiceProxy>);  
```  
  
<a name="orgWebProxyClient"></a>

## <a name="connect-to-cds-for-apps-using-organizationwebproxyclient"></a>Mithilfe von OrganizationWebProxyClient zu CDS für Apps verbinden

 Verwenden Sie nachfolgenden Konstruktor, um eine Verbindung mit CDS für Apps mithilfe der vom Benutzer zur Verfügung gestellten <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient>-Instanz herzustellen.  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient(<externalOrgWebProxyClient>);  
```  
  
<a name="Office365"></a>

## <a name="connect-to-cds-for-apps-office-365"></a>Mit CDS für Apps verbinden (Office 365)

 Verwenden Sie den folgenden Konstruktor, um eine Verbindung mit Ihrer CDS für Apps-Instanz in Office 365 herzustellen.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient("<crmUserId>", CrmServiceClient.MakeSecureString("<crmPassword>"), "<crmRegion>", "<orgName>", useUniqueInstance:false, useSsl:false, <orgDetail>, isOffice365:false);  
```  
  
 Gültige Werte für die `<crmRegion>`-Parameter sind:  `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`,  `Oceania`, `JPN`, `CAN`, `IND`, und `NorthAmerica2`. Wenn Sie dies auf `String.Empty` festgelegt haben, werden Server in jeder dieser Regionen für die CDS für Apps-Organisation gesucht. Für den `<orgName>` Parameter können Sie entweder den eindeutigen Namen oder den Anzeigenamen angeben.  
  
 Die folgenden Parameter sind optional:  `useUniqueInstance`, `useSsl` und `orgDetail`.  
  
<a name="Office365oAuth"></a>

## <a name="connect-to-cds-for-apps-office-365-using-oauth"></a>Mithilfe von OAuth mit CDS für Apps (Office 365) verbinden
 
 Verwenden Sie den folgenden Konstruktor zur Nutzung des OAuth-Protokolls, um eine Verbindung mit Ihrer CDS für Apps-Instanz in Office 365 herzustellen. Der OAuth-Support wird in CDS für Apps eingeführt.  
  
> [!NOTE]
>  Global Discovery unterstützt jetzt für alle die Instanzsuche, regional und global. Für den `OAuth`-Authentifizierungstyp wird der `crmRegion`-Parameterwert global auf `Online Region  = Don't Know` festgelegt, außer dort, wo spezielle Regionsregeln erforderlich sind. Deutschland und Nordamerika 2 werden nicht gescannt, wenn `Online Region = Don't Know` gewählt ist.

```csharp  
CrmServiceClient crmSvc = new CrmServiceClient("<crmUserId>", CrmServiceClient.MakeSecureString("<crmPassword>"), "<crmRegion>", "<orgName>", useUniqueInstance:false, <orgDetail>,  
                  <user>, <clientId>, <redirectUri>, <tokenCachePath>, <externalOrgWebProxyClient>, PromptBehavior.Auto);  
```  
  
 Dieser Konstruktor verwendet die [Microsoft Azure Active Directory Authentication Library (ADAL)](/azure/active-directory/develop/active-directory-authentication-libraries) zur Authentifizierung der Benutzer. Wenn die Benutzeranmeldeinformationen (Benutzername und Kennwort) nicht angegeben sind, wird ADAL den Benutzer zur Angabe der Anmeldeinformationen auffordern, abhängig vom `PromptBehavior`-Parameter, der (optional) im Kontruktor angegeben ist. ADAL authentifiziert die Anmeldeinformationen mithilfe des OAuth-Protokolls, erhält die Zugriffs- und Aktualisierungstoken von Azure Active Directory und verwendet dann das Zugriffstoken, um Anfragen an CDS für Apps zu stellen.  
  
 Gültige Werte für die `<crmRegion>`-Parameter sind: `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` und `NorthAmerica2`. Wenn Sie dies auf **String.Empty** festgelegt haben, werden Server in jeder dieser Regionen für die CDS für Apps-Organisation gesucht. Für den `<orgName>` Parameter können Sie entweder den eindeutigen Namen oder den Anzeigenamen angeben.  
  
<!-- No on-premises or IFD enabled for this version yet
<a name="ActiveDirectory"></a>

## Connect to CDS for Apps on-premises (Active Directory)

Use the following constructor to connect to an on-premises instance with Active Directory authentication.  
  
```csharp  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<credential>"), authType, "<hostName>", "<port>", "<orgName>", useUniqueInstance:false, useSsl:false, <orgDetail>);  
  
```  
  
 This will run an Active Directory authentication based on the specified domain. For the `<hostName>` parameter, specify the host name of your CDS for Apps server, for example: `cdstest`. For the `<orgName>` parameter, you can specify either the unique or friendly name.  
The following parameters are optional: `useUniqueInstance`, `useSsl`, and `orgDetail`.  
  
<a name="IFD"></a> 
  
## Connect to CDS for Apps Internet-facing deployment (IFD) 
 
 Use the following constructor to connect to a CDS for Apps IFD instance.  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<credential>"), authType, "<hostName>", "<port>", "<orgName>", useUniqueInstance:false, useSsl:false, <orgDetail>);  
  
```  
  
 This will run a claims-based authentication based on the specified local domain. This is useful for customers that use AD FS, and have configured their CDS for Apps server as claims, where the user population lives in the same AD FS domain as the CDS for Apps server. For the `<hostName>` parameter, specify the host name of your CDS for Apps server, for example, `cdstest`. For the `<orgName>` parameter, you can specify either the unique or friendly name.  
  
 The following parameters are optional: `useUniqueInstance`,  `useSsl`, and `orgDetail`.  
  
<a name="OPoAuth"></a> 

## Connect to CDS for Apps Internet-facing deployment (IFD) using OAuth

 Use the following constructor to use the OAuth protocol in Active Directory Federation Services (AD FS) in Windows Server 2012 R2 to connect to a CDS for Apps IFD instance. For this constructor to work, the computer where CDS for Apps is installed must have been configured to use AD FS 2.2 as the security token service (STS).  
  
```csharp
CrmServiceClient crmSvc = new CrmServiceClient("<crmUserId>", CrmServiceClient.MakeSecureString("<crmPassword>"), "<domain>","<homeRealm>", "<hostName>", "<port>", "<orgName>", useSsl, useUniqueInstance,   
                        <orgDetail>, <user>, <clientId>, <redirectUri>, <tokenCachePath>, externalOrgWebProxyClient, PromptBehavior.Auto);  
  
```  
 The `clientId` and `redirectUri` values for the application supporting OAuth should be registered in the IFD server.  
  
 If the user credentials (user name and password) aren’t specified, ADAL prompts the user to provide the credentials depending on the `PromptBehavior` parameter (optional) specified in the constructor. ADAL authenticates the user using the security token from AD FS, and uses the token to perform actions in CDS for Apps.  
  
<a name="ClaimsBased"></a>
   
## Connect to CDS for Apps (claims-based)
  
 Use the following constructor to use claims-based authentication.  
  
```  
CrmServiceClient crmSvc = new CrmServiceClient(new System.Net.NetworkCredential("<UserId>", "<password>", “<domain>”, "<homeRealm>"),"<hostName>", "<port>", "<orgName>");    
```  
  
 This will run a claims-based authentication against the specified Home realm. This is useful for customers that use AD FS, and have configured their CDS for Apps server as claims, where the user population lives in the same AD FS domain as the CDS for Apps server. For the `<hostName>` parameter, specify the host name of your CDS for Apps server, for example, `cdstest`. For the `<orgName>` parameter, you can specify either the unique or friendly name.  
   -->
  
 ## <a name="connect-to-dynamics-365-online-using-certificate-based-authentication"></a>Mithilfe der zertifikatsbasierten Authentifizierung mit Dynamics 365 (online) verbinden
 Verwenden Sie den folgenden Konstruktor, um die zertifikatsbasierte Authentifizierung zu nutzen.
 
 ```csharp
 CrmServiceClient CrmSvc = new CrmServiceClient("<certificate>", "<certificateStoreName>", "<certificateThumbPrint>", "<instanceUrl>", <useUniqueInstance>, <orgDetail>, <clientId>, <redirectUri>, <tokenCachePath>);
 ```
 Dadurch wird die zertifikatsbasierte Authentifizierung ausgeführt. Die Werte `clientId` und `redirectUri` für die Anwendung werden angegeben, wenn Sie eine App im **Azure-Portal** registrieren. 
 
 Die folgenden Parameter sind optional: `useUniqueInstance`,  `useSsl` und `orgDetail`.
 
<a name="Determine"></a>

## <a name="determine-your-connection-status"></a>Bestimmung Ihres Verbindungsstatus
 
 Um zu bestimmen, ob die Verbindungsaufforderung erfolgreich war, überprüfen Sie den Wert für <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.IsReady>. -Eigenschaft verfügbar. Wenn der Wert **true** ist, ist die Verbindung erfolgreich undSie können mit der Arbeit beginnen. Andernfalls überprüfen Sie die Werte des <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>. <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmError> und <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.LastCrmException> Eigenschaften, um die Ursache für den Verbindungsfehler festzustellen.  
  
### <a name="see-also"></a>Siehe auch

[Verwenden von Verbindungszeichenfolgen in XRM-Tooling zum Verbinden mit CDS für Apps](use-connection-strings-xrm-tooling-connect.md)<br />
[Verwenden von Windows PowerShell-Cmdlets für XRM-Tooling, um eine Verbindung mit CDS für Apps herzustellen](use-powershell-cmdlets-xrm-tooling-connect.md)<br />
[Verwenden der XRM-Tooling-API zur Ausführung von Aktionen in CDS für Apps](use-xrm-tooling-execute-actions.md)
<xref:Microsoft.Xrm.Tooling.Connector.AuthenticationType><br />
[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)
<!-- TODO:[Sample: Quick Start for CDS for Apps](../sample-quick-start.md)-->


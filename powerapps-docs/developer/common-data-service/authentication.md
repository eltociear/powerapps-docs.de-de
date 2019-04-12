---
title: Authentifizierung mit Common Data Service-Webservices (Common Data Service) | Microsoft Docs
description: 'Stellt Authentifizierungsoptionen vor, die vom Software-Framework abhängen, das Sie verwenden.'
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
# <a name="authentication-with-common-data-service-web-services"></a>Authentifizierung mit Common Data Service-Webdiensten

Wenn Sie Client-Anwendungen erstellen, die Common Data Service-Webdienste verwenden, müssen Sie diese authentifizieren um den Zugriff auf Daten zu erhalten. Wie Sie authentifizieren , ist abhängig vom Software-Framework, das Sie verwenden und vom Webdienst mit dem verbunden werden soll.

## <a name="net-framework-applications"></a>.NET Framework Anwendungen

Wenn die Client-Anwendung .NET Framework verwendet, haben Sie zwei Möglichkeiten:

- OAuth
- Office 365

### <a name="oauth"></a>OAuth

OAuth ist das bevorzugte Mittel zur Authentifizierung, da es Zugriff auf *beides*, sowohl auf die OData RESTful Webdienste (Web API und OData Global Discovery Service) als auch auf die SOAP-Webservices (Organisationsservice und Suchdienst) bietet. 

OAuth ist auch erforderlich, um Folgendes zu unterstützen: 
 - Azure Active Directory-Konfigurationen für bedingten Zugriff, wie z. B. Zweistufige Authentifizierung (2FA)
 - Verwendung von geheimen Clientschlüsseln zur Aktivierung von Server-zu-Server-Authentifizierungsszenarien.
 - Cross-Origin Resource Sharing (CORS) zur Anbindung einer Single Page Application (SPA)

Weitere Informationen: [Verwenden von OAuth mit Common Data Service](authenticate-oauth.md)

### <a name="office-365"></a>Office 365

Office 365-Authentifizierung erfordert die Verwendung von .NET Framework SDK-Assemblys mit ausschließlich SOAP-Webdiensten.

Die Verwendung der Office 365-Authentifizierung erfordert nicht, dass Sie Ihre Anwendungen registrieren, wie mit OAuth notwendig. Sie müssen einfach einen Benutzerprinzipalname (UPN,User Principal Name) und Ihr Kennwort für einen gültigen Benutzer angeben.

Weitere Informationen: [Authentifizierung mit .NET Framework-Anwendungen](authenticate-dot-net-framework.md)

## <a name="all-other-software-frameworks"></a>Alle anderen Software-Frameworks

Wenn Sie etwas anderes als.NET Framework verwenden, müssen Sie sich mit OAuth authentifizieren und die OData RESTful-Webdienste (Web API und OData Global Discovery Service) verwenden.

Weitere Informationen: [Verwenden von OAuth mit Common Data Service](authenticate-oauth.md)

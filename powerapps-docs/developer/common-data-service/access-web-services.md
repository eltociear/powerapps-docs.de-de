---
title: Zugriff auf externe Webservices (Common Data Service) | MicrosoftDocs
description: 'Erfahren Sie, wie Sie über ein benutzerdefiniertes Plug-in oder eine Workflow-Aktivität auf einen Webservice zugreifen können.'
ms.custom: ''
ms.date: 2/6/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="access-external-web-services"></a>Zugriff auf externe Webservices

Plugins und benutzerdefinierte Workflow-Aktivitäten, die in der Sandbox ausgeführt werden, können über die Protokolle HTTP und HTTPS auf das Netzwerk zugreifen. Diese Funktion bietet Unterstützung für den Zugriff auf gängige Webdienste wie Social Sites, Newsfeeds, Webservices und mehr. Die folgenden Internet-Zugriffsbeschränkungen gelten für diese Sandboxfunktion.  
  
- Nur die HTTP- und HTTPS-Protokolle sind erlaubt.
- Der Zugriff auf localhost (Loopback) ist nicht erlaubt.
- IP-Adressen können nicht verwendet werden. Sie müssen eine benannte Internetadresse verwenden, die die DNS-Namensauflösung erfordert.
- Anonyme Authentifizierung wird unterstützt und empfohlen. Es gibt keine Vorkehrung für die Aufforderung des angemeldeten Benutzers zur Eingabe oder zum Speichern von Anmeldeinformationen.

Andere Methoden des Zugriffs auf Webdienste sind die Verwendung von Webhooks und die [!INCLUDE [pn_azure_service_bus](../../includes/pn_azure_service_bus.md)]. Weitere Informationen zu diesen Themen finden Sie unter den untenstehenden Links.

## <a name="see-also"></a>Siehe auch

[Plug-Ins](plug-ins.md)<br />
[Workflowerweiterungen](workflow/workflow-extensions.md)<br />
[Azure-Integration](azure-integration.md)<br />
[Web-Hooks verwenden](use-webhooks.md)<br />
[Beispiel: Webzugriff über ein Sandkasten-Plug-In](org-service/samples/web-access-plugin.md)

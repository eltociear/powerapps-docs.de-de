---
title: Erstellen von Windows-Clientanwendungen mit den XRM-Tools (Common Data Service)| Microsoft Docs
description: 'XRM-Tools sind ein Satz neuer APIs, der den Aufbau von Windows-Client-Anwendungen für Common Data Service unterstützt.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: e2f22576-1705-4854-a804-a1ca232c0cfc
caps.latest.revision: 33
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="build-windows-client-applications-using-the-xrm-tools"></a>Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools

XRM-Tools ist ein Satz von APIs auf der Grundlage der Common Data Service-Assembly-APIs (Organisationsdienst und Suchdienst), der Support zum Erstellen von Windows-Client-Anwendungen für Common Data Service bereitstellt. Es bietet die folgenden Funktionen:  
  
- Unterstützt alle Authentifizierungsmodi für die Anmeldung bei Common Data Service, einschließlich OAuth.  
- Bietet PowerShell-Unterstützung für die Authentifizierung und die Verbindung mit Common Data Service.  
- Bietet Threadsicherheit für in Common Data Service durchgeführte Aktionen in einer Multithread-Umgebung. Weitere Informationen [Multithreading in Komponenten](https://msdn.microsoft.com/library/vstudio/3es4b6yy.aspx), [Threadsichere Komponenten](https://msdn.microsoft.com/library/vstudio/a8544e2s.aspx)  
- Bietet eine gemeinsame Windows Presentation Foundation-Anmeldesteuerung für Common Data Service für ein einheitliches Anmeldeerlebnis bei Common Data Service aus Ihren Windows-Clientanwendungen.  
- Unterstützt die sichere Speicherung der Anmeldeinformationen und ihre Wiederverwendung für die automatische Anmeldung bei Common Data Service nach der ersten Anmeldung.  
- Bietet integrierte Diagnosenachverfolgung und Leistungsberichte für die in Common Data Service durchgeführten Aktionen, die Sie auf der Grundlage der Anforderungen Ihrer Organisation konfigurieren können.  
  
## <a name="components-of-xrm-tooling"></a>Komponenten des XRM-Toolings  

XRM-Tooling hat die folgenden drei Komponenten:  
  
- **Schnittstelle für Entwickler**: Dies bietet Interaktions- und Wrapper-Methoden auf niedriger Ebene für die Common Data Service-SDK-Assembly-APIs. Dies ist eine instrumentierte API, die eine threadsichere Umgebung für Aufrufe an Common Data Service mit integrierten Diagnosefunktionen bietet, mit deren Hilfe Sie die Leistung einzelner Aufrufe prüfen können. Außerdem bietet es einen Standardsatz von Verfolgungslistener für die Debugunterstützung. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.Connector>.  
  
- **Allgemeines Anmeldungssteuerelement:** Dies ist ein WPF-Benutzersteuerelement mit einer gemeinsamen Benutzeroberfläche für die Anmeldung bei Common Data Service. Das Anmeldungssteuerelement unterstützt alle Authentifizierungsmodi, die von Common Data Service unterstützt werden. Das allgemeine Anmeldungssteuerelement verfügt über integrierte Verschlüsselung für die sichere Speicherung Ihrer/s Anmeldeinformationen/Profils und die anschließende Wiederverwendung zur Laufzeit für die automatische Anmeldung bei Common Data Service. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.CrmConnectControl>.  
  
- **Webressourcenhilfsprogramm**: Dies bietet Unterstützung für den Zugriff auf Informationen aus den beiden folgenden Arten von Webressourcen in Common Data Service: Bild und XML. Sie können auf ein Bild von einer Common Data Service-Webressource aus zugreifen und es als WPF-BitmapImage-Objekt zurückgeben. Entsprechend kann eine XML-Webressource als Zeichenfolge zurückgegeben werden. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.WebResourceUtility>.  
  
## <a name="client-applications-that-use-xrm-tooling"></a>Client-Anwendungen, die XRM-Tooling verwenden

Die folgenden Anwendungen in der aktuellen Version von Common Data Service verwenden WPF-Anmeldungssteuerelemente zum Authentifizieren von Benutzern bei Common Data Service aus der Client-Anwendung:  
  
- Unified Service Desk. Weitere Informationen: [Unified Service Desk erweitern](/dynamics365/customer-engagement/unified-service-desk/extend-unified-service-desk)

<!-- TODO: fix links when files added to admin guide

- Package Deployer tool. More information: [Deploy packages using Dynamics 365 Package Deployer and Windows PowerShell](../../administrator/deploy-packages-using-package-deployer-windows-powershell.md)   

- Configuration Migration tool. More information [Manage your configuration data](../../administrator/manage-configuration-data.md)  

-->
  
### <a name="see-also"></a>Siehe auch

[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
<!-- TODO:
[Use the Common Data Service Organization service](use-microsoft-dynamics-365-organization-service.md)<br />
[Discover the URL for Your Organization With IDiscoveryService Web Service](org-service/discover-url-organization-organization-service.md)<br />
[Write Applications and Server Extensions](extend-dynamics-365-server.md)<br /> -->
[Blog: PowerShell-Modul für die Ausführung von Datenvorgängen und die Bearbeitung der Benutzer- und Systemeinstellungen in CRM](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)
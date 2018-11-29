---
title: Erstellen von Windows-Clientanwendungen mit den XRM-Tools (Common Data Service for Apps)| Microsoft Docs
description: 'XRM-Tools sind ein Satz neuer APIs, der den Aufbau von Windows-Client-Anwendungen für CDS for Apps unterstützt.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
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

XRM-Tools ist ein Satz von APIs auf der Grundlage der Common Data Service for Apps-Assembly-APIs (Organisationsdienst und Suchdienst), der Support zum Erstellen von Windows-Client-Anwendungen für CDS for Apps bereitstellt. Es bietet die folgenden Funktionen:  
  
- Unterstützt alle Authentifizierungsmodi für die Anmeldung in CDS for Apps.  
- Bietet PowerShell-Unterstützung für die Authentifizierung und die Verbindung mit CDS for Apps.  
- Bietet Threadsicherheit für in CDS for Apps durchgeführte Aktionen in einer Multithread-Umgebung. Weitere Informationen [Multithreading in Komponenten](https://msdn.microsoft.com/library/vstudio/3es4b6yy.aspx), [Threadsichere Komponenten](https://msdn.microsoft.com/library/vstudio/a8544e2s.aspx)  
- Bietet eine gemeinsame Windows Presentation Foundation-Anmeldesteuerung für CDS for Apps für ein einheitliches Anmeldeerlebnis bei CDS for Apps aus Ihren Windows-Clientanwendungen.  
- Unterstützt die sichere Speicherung der Anmeldeinformationen und ihre Wiederverwendung für die automatische Anmeldung bei CDS for Apps nach der ersten Anmeldung.  
- Bietet integrierte Diagnosenachverfolgung und Leistungsberichte für die in CDS for Apps durchgeführten Aktionen, die Sie auf der Grundlage der Anforderungen Ihrer Organisation konfigurieren können.  
  
## <a name="components-of-xrm-tooling"></a>Komponenten des XRM-Toolings  

XRM-Tooling hat die folgenden drei Komponenten:  
  
- **Schnittstelle für Entwickler**: Dies bietet Interaktions- und Wrapper-Methoden auf niedriger Ebene für die CDS for Apps-SDK-Assembly-APIs. Dies ist ein instrumentiertes API, das eine threadsichere Umgebung für Aufrufe zu CDS for Apps mit integrierten Diagnosefunktionen bietet, mit deren Hilfe Sie die Leistung einzelner Aufrufe prüfen können. Außerdem bietet es einen Standardsatz von Verfolgungslistener für die Debugunterstützung. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.Connector>.  
  
- **Allgemeines Anmeldungssteuerelement**: Dies ist ein WPF-Benutzersteuerelement mit einer gemeinsamen Benutzeroberfläche für die Anmeldung bei CDS for Apps. Das Anmeldungssteuerelement unterstützt alle Authentifizierungsmodi, die von CDS for Apps unterstützt werden. Das allgemeine Anmeldungssteuerelement verfügt über integrierte Verschlüsselung für die sichere Speicherung Ihrer/s Anmeldeinformationen/Profils und die anschließende Wiederverwendung zur Laufzeit für die automatische Anmeldung bei CDS for Apps. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.CrmConnectControl>.  
  
- **Webressourcenhilfsprogramm**: Dies bietet Unterstützung für den Zugriff auf Informationen aus den beiden folgenden Arten von Webressourcen in CDS for Apps: Bild und XML. Sie können auf ein Bild von einer CDS for Apps-Webressource aus zugreifen und es als WPF-BitmapImage-Objekt zurückgeben. Entsprechend kann eine XML-Webressource als Zeichenfolge zurückgegeben werden. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.WebResourceUtility>.  
  
## <a name="client-applications-that-use-xrm-tooling"></a>Client-Anwendungen, die XRM-Tooling verwenden

Die folgenden Anwendungen in der aktuellen Version von CDS for Apps verwenden WPF-Anmeldungssteuerelemente zum Authentifizieren von Benutzern bei CDS for Apps aus der Client-Anwendung:  
  
- Unified Service Desk. Weitere Informationen: [Unified Service Desk erweitern](/dynamics365/customer-engagement/unified-service-desk/extend-unified-service-desk)

<!-- TODO: fix links when files added to admin guide

- Package Deployer tool. More information: [Deploy packages using Dynamics 365 Package Deployer and Windows PowerShell](../../administrator/deploy-packages-using-package-deployer-windows-powershell.md)   

- Configuration Migration tool. More information [Manage your configuration data](../../administrator/manage-configuration-data.md)  

-->
  
### <a name="see-also"></a>Siehe auch

[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
<!-- TODO:
[Use the CDS for Apps Organization service](use-microsoft-dynamics-365-organization-service.md)<br />
[Discover the URL for Your Organization With IDiscoveryService Web Service](org-service/discover-url-organization-organization-service.md)<br />
[Write Applications and Server Extensions](extend-dynamics-365-server.md)<br /> -->
[Blog: PowerShell-Modul für die Ausführung von Datenvorgängen und die Bearbeitung der Benutzer- und Systemeinstellungen in CRM](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)
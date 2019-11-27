---
title: Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools (Common Data Service) | Microsoft-Dokumentation
description: XRM-Tools sind ein Satz neuer APIs, der den Aufbau von Windows-Client-Anwendungen für Common Data Service unterstützt.
ms.custom: ''
ms.date: 03/27/2019
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
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4b05e59426f507b10645a20044a67ee28620f2e6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753966"
---
# <a name="build-windows-client-applications-using-the-xrm-tools"></a>Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools

XRM-Tools ist ein Satz von APIs auf der Grundlage der Common Data Service-Assembly-APIs (Organisationsdienst und Ermittlungsdienst), der Unterstützung beim Erstellen von Windows-Client-Anwendungen für Common Data Service bereitstellt. Es bietet die folgenden Funktionen:  
  
- Unterstützt alle Authentifizierungsmodi für die Anmeldung bei der Common Data Service-Instanz.  
- Bietet PowerShell-Unterstützung für die Authentifizierung und die Verbindung mit der Common Data Service-Instanz.  
- Bietet Threadsicherheit für in Common Data Service durchgeführte Aktionen in einer Multithread-Umgebung. Weitere Informationen [Multithreading in Komponenten](https://msdn.microsoft.com/library/vstudio/3es4b6yy.aspx), [Threadsichere Komponenten](https://msdn.microsoft.com/library/vstudio/a8544e2s.aspx)  
- Bietet eine gemeinsame Windows Presentation Foundation-Anmeldesteuerung für Common Data Service für ein einheitliches Anmeldeerlebnis bei Common Data Service aus Ihren Windows-Clientanwendungen.  
- Unterstützt die sichere Speicherung der Anmeldeinformationen und ihre Wiederverwendung für die automatische Anmeldung bei Common Data Service nach der ersten Anmeldung.  
- Bietet integrierte Diagnosenachverfolgung und Leistungsberichte für die in Common Data Service durchgeführten Aktionen, die Sie auf der Grundlage der Anforderungen Ihrer Organisation konfigurieren können.  

## <a name="components-of-xrm-tooling"></a>Komponenten des XRM-Toolings  

XRM-Tooling hat die folgenden drei Komponenten:  
  
- **Schnittstelle für Entwickler**: Dies bietet Interaktions- und Wrapper-Methoden auf niedriger Ebene für die Common Data Service-SDK-Assembly-APIs. Dies ist ein instrumentiertes API, das eine threadsichere Umgebung für Aufrufe an Common Data Service mit integrierten Diagnosefunktionen bietet, mit deren Hilfe Sie die Leistung einzelner Aufrufe prüfen können. Außerdem bietet es einen Standardsatz von Verfolgungslistener für die Debugunterstützung. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.Connector>.  
  
- **Allgemeines Anmeldungssteuerelement**: Dies ist ein WPF-Benutzersteuerelement mit einer gemeinsamen Benutzeroberfläche für die Anmeldung bei Common Data Service. Das Anmeldungssteuerelement unterstützt alle Authentifizierungsmodi, die von Common Data Service unterstützt werden. Das allgemeine Anmeldungssteuerelement verfügt über integrierte Verschlüsselung für die sichere Speicherung Ihrer/s Anmeldeinformationen/Profils und die anschließende Wiederverwendung zur Laufzeit für die automatische Anmeldung bei Common Data Service. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.CrmConnectControl>.  
  
- **Webressourcenhilfsprogramm**: Dies bietet Unterstützung für den Zugriff auf Informationen aus den beiden folgenden Arten von Webressourcen in Common Data Service: Bild und XML. Sie können auf ein Bild von einer Common Data Service-Webressource aus zugreifen und es als WPF-BitmapImage-Objekt zurückgeben. Entsprechend kann eine XML-Webressource als Zeichenfolge zurückgegeben werden. Der Namespace für diese Komponente ist <xref:Microsoft.Xrm.Tooling.WebResourceUtility>.  
  
## <a name="client-applications-that-use-xrm-tooling"></a>Client-Anwendungen, die XRM-Tooling verwenden

Die folgenden Anwendungen in der aktuellen Version von Common Data Service verwenden WPF-Aanmeldungssteuerelemente zum Authentifizieren von Benutzern bei Common Data Service aus der Client-Anwendung:  
  
- Unified Service Desk. Weitere Informationen: [Unified Service Desk erweitern](/dynamics365/customer-engagement/unified-service-desk/extend-unified-service-desk)

<!--Package Deployer tool. More information: [Deploy packages using Package Deployer and Windows PowerShell](../../administrator/deploy-packages-using-package-deployer-windows-powershell.md)-->   

<!--Configuration Migration tool. More information [Manage your configuration data](../../administrator/manage-configuration-data.md)-->  
  
### <a name="see-also"></a>Siehe auch

[Beispiel: Schnellstart für XRM Tooling API](sample-quick-start-xrm-tooling-api.md)<br />
[Blog: PowerShell-Modul für die Ausführung von Datenvorgängen und die Bearbeitung der Benutzer- und Systemeinstellungen in Common Data Service](https://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)


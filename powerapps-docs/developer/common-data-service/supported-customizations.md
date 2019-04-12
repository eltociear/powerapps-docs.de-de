---
title: Unterstützte Anpassungen für Common Data Service (Common Data Service) | Microsoft Docs
description: 'Lesen Sie, wie Sie Common Data Service anpassen können, indem Sie Tools verwenden, die im PowerApps-Portal verfügbar sind oder in den Dokumenten beschrieben werden.'
ms.custom: ''
ms.date: 01/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

<!-- This is the portion of the old topic that applies to Common Data Service
https://docs.microsoft.com/dynamics365/customer-engagement/developer/supported-extensions
 -->


# <a name="supported-customizations-for-common-data-service"></a>Unterstützte Anpassungen für Common Data Service

Sie können Common Data Service anpassen, indem Sie Tools verwenden, die im PowerApps-Portal verfügbar sind oder die in der offiziellen Dokumentation beschrieben werden. Diese Anpassungen werden unterstützt und können aktualisiert werden.

Anpassungen, die mit anderen Methoden als den hier beschriebenen Methoden vorgenommen werden, sind nicht unterstützt und können während Updates und Upgrades auf Common Data Service Probleme verursachen. Weitere Informationen finden Sie unter [Nicht unterstützte Anpassungen](#unsupported-customizations).

Die Themen, die in technischen Artikeln auf Microsoft-Websites wie docs.microsoft.com, msdn.microsoft.com oder technet.microsoft.com veröffentlicht werden, werden unterstützt,sind jedoch möglicherweise nicht erweiterungsfähig.


## <a name="customizations-using-powerapps-portal"></a>Anpassungen mithilfe des PowerApps-Portals

Es gibt eine Reihe von Tools, die in Common Data Service enthalten sind und die Sie für die Anpassung verwenden können. Die Anpassungen, die mithilfe von PowerApps-Portal-Tools und Webanwendungen vorgenommen werden, werden vollständig unterstützt und sind vollständig aktualisierbar.

Die folgenden Anpassungsmethoden können verwendet werden, um vollständig unterstützte Anpassungen zu erstellen:

- Anpassungen im PowerApps-Portal oder im Lösungsexplorer. Weitere Informationen finden Sie unter [Neuheiten bei Common Data Service](../../maker/common-data-service/data-platform-intro.md)

- Einstellungen in der Webanwendung. Weitere Informationen finden Sie unter [Verwalten von PowerApps](../../administrator/admin-guide.md).

- Reporting Services. Weitere Informationen finden Sie unter [Berichte und Analysen-Handbuch für Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365).

> [!NOTE]
> Vollständig unterstützt bedeutet, dass Entwicklersupport Unterstützung für Anpassungen bieten kann und dass Anwendungssupport Kunden beim Ausführen dieser Änderungen helfen kann.

Weitere Informationen zur Verwendung der Anpassungstools in der Webanwendung finden Sie unter [Was ist Common Data Service?](../../maker/common-data-service/data-platform-intro.md).


## <a name="customizations-applied-using-code"></a>Mit Code angewendete Anpassungen

Die Dokumentation auf dieser Website für Entwickler, technischen Artikel und der Beispielcode, der auf dieser Website veröffentlicht wird und die Informationen, die vom Common Data Service-Developer Support Team freigegeben wurden, sind in den Bereich der Anpassungen enthalten, die mithilfe von Code angewendet werden. Die bestimmten Aktionen und Ebenen der Supportfähigkeit und Aktualisierbarkeit werden weiter unten in diesem Thema beschrieben.

### <a name="common-data-service-web-services"></a>Common Data Service-Webdienste

Die Verwendung von Webdiensten werden vollständig unterstützt. Hierzu zählen unter anderem folgende: Web-API, Organisations-Service, Suchdienst und der Oranisations-Datendienst. Wir bemühen uns, die APIs abwärtskompatibel zu halten, behalten uns jedoch das Recht vor, APIs für zusätzliche Features zu ändern. Entitätsattribute können sich in zukünftigen Versionen möglicherweise auch ändern.

### <a name="solution-file"></a>Lösungsdatei

Die Änderung einer Datei einer nicht verwalteten Lösung wird unterstützt, wie in dieser Dokumentation beschrieben. Bestimmte Anpassungsaufgaben für modellgesteuerte Apps können mithilfe dieser Schritte ausgeführt werden:

1. Exportieren einer Lösungskomponente als nicht verwaltete Lösung.
2. Extrahieren der Inhalte des Lösungspakets.
3. Bearbeiten der Customizations.xml-Datei.
4. Neupacken der Lösungsdatei.
5. Importieren der geänderten Lösung.

> [!NOTE]
> Änderungen an der Datei `Customizations.xml` müssen dem `CustomizationsSolution.xsd`-Schema entsprechen. Weitere Informationen finden Sie unter [Dateischema für Anpassungslösungen](customization-solutions-file-schema.md).

Die folgenden unterstützten Aufgaben können unter Verwendung dieser Schritte ausgeführt werden:

- Menübandanpassung.
- Anpassung der Anwendungsnavigation mithilfe von SiteMap.
- Formular- und Dashboardanpassung mithilfe FormXml.
- Anpassung gespeicherter Abfragen.

### <a name="plug-ins"></a>Plug-Ins

Die Fähigkeit, eine angepasste Geschäftslogik mithilfe des in dieser Dokumentation beschriebenen Plug-In-Mechanismus zu erstellen, wird vollständig unterstützt und ist aktualisierbar. Plug-Ins können nur im Sandkasten (Isolation) registriert und ausgeführt werden. Weitere Informationen: [Plug-Ins](plug-ins.md).

### <a name="workflow-extensions"></a>Workflowerweiterungen

Die Möglichkeit, angepasste Workflowaktivitäten (Assemblys) zu erstellen, die von Workflowregeln aufgerufen werden können, ist vollständig unterstützt und kann aktualisiert werden. Benutzerdefinierte Workflowaktivitäten können jedoch nur im Sandkasten (Isolation) registriert und aktiviert werden. Weitere Informationen: [Workflowerweiterungen](workflow/workflow-extensions.md) Automatisieren Ihrer Geschäftsprozesse in Customer Engagement

## <a name="support-for-net-framework-versions"></a>Unterstützung für .NET Framework-Versionen

Im Folgenden werden die Unterstützungsüberlegungen für benutzerdefinierten Code, der mit Microsoft .NET Framework 4.6.2. geschrieben wurde, beschrieben.

- Jeder Webdienstclient, der mithilfe von Microsoft .NET Framework 4.6.2. oder höher erstellt wurde, der Webservices aufruft, wird in Common Data Service vollständig unterstützt.

> [!IMPORTANT]
> Sie sollten alle benutzerdefinierten Client-Anwendungen mit Microsoft .NET Framework 4.6.2. oder höher erstellen. Nur Anwendungen sind zulässig, die die Sicherheit auf Transportebene (TLS) 1.2 oder höher verwenden. TLS 1.2 ist nicht das Standardprotokoll, das von .NET Framework 4.5.2 verwendet wird, aber es ist in .NET Framework 4.6.2.
> 
> Wenn Clients für ältere Versionen von Dynamics 365 Customer Engagement eine Verbindung mit einer Version oder einem Bereitstellungstyp herstellen sollen, können Sie sich vorbereiten, indem Sie die Anwendung erneut kompilieren, damit sie .NET Framework 4.6.2 verwenden kann. Weitere Informationen: [Blogbeitrag: Kommende Updates zu Dynamics 365 Customer Engagement-Verbindungssicherheit](https://blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/)

- Sämtliche .NET-Assemblys, die mit Microsoft .NET Framework 4.6.2 für die Verwendung in Common Data Service als eine Plug-In-Assembly oder als eine benutzerdefinierte Workflowaktivität erstellt werden, werden unterstützt.

## <a name="unsupported-customizations"></a>Nicht unterstützte Anpassungen

Änderungen an Common Data Service, die ohne die Verwendung der Methoden, die in dieser Dokumentation beschrieben sind oder Common Data Service-Tools vorgenommen werden, werden nicht unterstützt und werden während Updates oder Upgrades von Common Data Service nicht beibehalten. Alles, was nicht in dieser Dokumentation und den unterstützenden Dokumenten dokumentiert wird, wird nicht unterstützt. Außerdem könnten nicht unterstützte Änderungen Probleme verursachen, wenn Sie durch das Hinzufügen von Hotfixes oder Service Packs aktualisieren, oder wenn Sie Common Data Service aktualisieren. 

Im Folgenden finden Sie eine Liste nicht unterstützter Aktionstypen, nach denen häufig gefragt wird:

- Verweisen von Common Data Service-Dynamic-Link-Libraries (DLLs) abgesehen von Folgenden:

    - Microsoft.Crm.Outlook.Sdk.dll
    - Microsoft.Crm.Sdk.Proxy.dll
    - Microsoft.Xrm.Sdk.dll
    - Microsoft.Xrm.Sdk.Data.dll
    - Microsoft.Xrm.Sdk.Deployment.dll
    - Microsoft.Xrm.Sdk.Workflow.dll
    - Microsoft.Xrm.Tooling.Connector.dll
    - Microsoft.Xrm.Tooling.CrmConnectControl.dll
    - Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll
    - Microsoft.Xrm.Tooling.WebResourceUtility.dll

- Die Nutzung von Anwendungsprogrammierschnittstellen (APIs) abgesehen von den in den Webdiensten: Web-API, Organisationsdienst, Bereitstellungsdienst, Suchdienst, Organisationsdatendienst dokumentierten.

- Plug-In- und Workflow-Assemblys müssen die gesamte notwendige Logik innerhalb der jeweiligen DLL enthalten. Plug-Ins können auf einige Kern-.Net-Assemblys verweisen. Allerdings werden Abhängigkeiten auf .Net-Assemblys nicht unterstützt, die mit Windows-APIs auf niedriger Ebene, wie der Grafikentwurfsschnittstelle, interagieren. Zuvor ließ Dynamics 365 zu, dass Assemblys auf diese Schnittstellen verweist, um aber den Sicherheitsstandards gerecht zu werden, sind Änderungen an dem Verhalten erforderlich.

- Das Erstellen eines Plug-In-Assemblys für eine Standard-Common Data Service-Assembly (Microsoft.Crm.*.dll) oder zum Ausführen eines Updates oder Löschens einer Plattform, die in `pluginassembly` erstellt wurde, wird nicht unterstützt.

- Bearbeiten einer Lösungsdatei zum Bearbeiten von Lösungskomponenten, abgesehen von Menübändern, Formularen, SiteMap oder gespeicherten Abfragen wird nicht unterstützt. Weitere Informationen finden Sie unter [Wann die Anpassungsdatei bearbeitet wird](when-edit-customization-file.md). Das Definieren neuer Lösungskomponenten durch das Bearbeiten der Lösungsdatei wird nicht unterstützt. Das Bearbeiten der Webressourcendateien, die mit einer Lösung exportiert werden, wird nicht unterstützt. Abgesehen von den Schritten, die in [Bearbeiten einer verwalteten Lösung](maintain-managed-solutions.md) dokumentiert werden, wird das Bearbeiten von Inhalten einer verwalteten Lösung nicht unterstützt.

### <a name="outlook-client"></a>Outlook-Client
- Änderungen an einem der Dynamics 365-Formulare oder das Hinzufügen neuer Formulare, wie benutzerdefinierte .aspx-Seiten, direkt in Office Outlook oder Änderungen an .pst-Dateien. Diese Änderungen werden nicht aktualisiert.
- Anpassungen mit anderen Mitteln als den unterstützten Tools vornehmen.

### <a name="see-also"></a>Siehe auch

[Unterstützte Anpassungen für modellgesteuerte Apps](../model-driven-apps/supported-customizations.md)





---
title: 'Übersicht für Entwickler: Common Data Service für Apps | Microsoft-Dokumentation'
description: Informationen dazu, wie Entwickler mithilfe von Common Data Service für Apps einen Beitrag leisten können.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: jdaly
ms.openlocfilehash: 5ed61c77cc0cea3cf25e48b347f8a524cf62dfd5
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-service-for-apps-developer-overview"></a>Übersicht für Entwickler: Common Data Service für Apps
PowerApps bietet Benutzern, Unternehmen, Partnern, unabhängigen Softwareherstellern und Systemintegratoren eine leistungsstarke Plattform für das Erstellen von branchenspezifischen Apps. Der Dienst Common Data Service für Apps wurde in diesem Release von PowerApps neu hinzugefügt. Common Data Service für Apps enthält nun die Kernfunktionen der Plattform Dynamics 365 Customer Engagement.


## <a name="get-started"></a>Erste Schritte
Wenn Sie bereits Erfahrung mit den Dynamics 365 Customer Engagement-Apps haben, können Sie diese Erfahrungen nutzen, um Common Data Service für Apps anzupassen und zu erweitern.

Wenn Sie noch nicht mit Dynamics 365 Customer Engagement-Anwendungen vertraut sind, finden Sie in den folgenden Artikeln eine allgemeine Übersicht über die wichtigsten Konzepte, die Ihnen den Einstieg in die Arbeit mit Common Data Service für Apps erleichtern.

> [!NOTE]
> - Modellgesteuerte Apps sind mit Common Data Service für Apps verbunden. Informationen darüber, wie Entwickler auf Anwendungsebene einen Beitrag leisten können, finden Sie unter [Model-driven apps Developer Overview (Übersicht für Entwickler: Modellgesteuerte Apps)](../model-driven-apps/overview.md). Dieser Abschnitt bezieht sich nur auf Erweiterungen, die Entwickler auf Dienstebene vornehmen können. 
> - Da Common Data Service für Apps und Dynamics 365 Customer Engagement dieselbe Plattform verwenden, finden Sie ausführlichere Informationen für Entwickler im [Entwicklerhandbuch zu Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/developer-guide). In diesen Artikel erhalten Sie eine Übersicht mit Links zum Entwicklerhandbuch und anderen Handbüchern, die weitere Informationen enthalten.


## <a name="tools-and-resources-for-developers"></a>Tools und Ressourcen

Die folgenden Tools und Ressourcen werden von Entwicklern bei der Arbeit mit Lösungen verwendet, die mit Common Data Service für Apps erstellt wurden.

### <a name="tools-available-for-download-from-nuget"></a>Tools, die über NuGet verfügbar sind

Die folgenden Tools werden in NuGet-Paketen verteilt. Der Artikel [Herunterladen von Tools von NuGet](/dynamics365/customer-engagement/developer/download-tools-nuget) umfasst ein PowerShell-Skript, das Sie verwenden können, um die neusten Versionen dieser Tools herunterzuladen und zu extrahieren.

|Tool  |Beschreibung  |
|---------|---------|
|Tool zur Codegenerierung `CrmSvcUtil.exe`|Ein Befehlszeilentool zur Codegenerierung, das früh gebundene .NET Framework-Klassen erstellt, die das Entitätsdatenmodell darstellen, die vom Organisationsdienst verwendet werden. <br />Weitere Informationen finden Sie unter: <br />[Organization Service (Organisationsdienst)](use-web-services.md#organization-service)<br />[Dynamics 365 Customer Engagement Developer Guide: Create early bound entity classes with the code generation tool (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Erstellen von Entitätsklassen mit früher Bindung mithilfe des Codegenerierungstools)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)|
|Tool zur Konfigurationsmigration `DataMigrationUtility.exe`|Wird verwendet, um Konfigurationsinformationen an verschiedene Umgebungen weiterzugeben. Diese Informationen werden verwendet, um benutzerdefinierte Funktionen zu definieren. Sie werden in der Regel in benutzerdefinierten Entitäten gespeichert. Dieses Tool ist nicht für das Verschieben von Unternehmensinformationen bestimmt. <br /> Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Administrator Guide: Move configuration data across instances and organizations with the Configuration Migration tool (Administratorleitfaden für Dynamics 365 Customer Engagement: Verschieben von Konfigurationsinformationen auf mehrere Instanzen und Organisationen mithilfe des Tools zur Konfigurationsmigration)](/dynamics365/customer-engagement/admin/manage-configuration-data).|
|Package Deployer `PackageDeployer.exe`|Wird zum Bereitstellen von Paketen auf Instanzen von Common Data Service für Apps verwendet. Bei einem Paket handelt es sich um eine Einheit, die Lösungen enthält und installiert werden kann. <br /> Weitere Informationen finden Sie unter: <br />[Deploy Solution Packages (Bereitstellen von Lösungspaketen)](introduction-solutions.md#deploy-solution-packages)<br />[Dynamics 365 Customer Engagement Developer Guide: Create packages for the Dynamics 365 Package Deployer (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Erstellen von Paketen für Dynamics 365-Package Deployer)](/dynamics365/customer-engagement/developer/create-packages-package-deployer)|
|Tool zur Plug-In-Registrierung `PluginRegistration.exe`|Ein Tool, das zum Abonnieren von Serverereignissen für Plug-In-Klassen für .NET-Assemblys verwendet wird. <br />Weitere Informationen finden Sie unter: <br />[Erstellen eines Plug-Ins](apply-business-logic-with-code.md#create-a-plug-in)<br />[Exemplarische Vorgehensweise: Registrieren eines Plug-Ins mithilfe des Plug-In-Registrierungstools](/dynamics365/customer-engagement/developer/walkthrough-register-plugin-using-plugin-registration-tool)|
|Solution Packager-Tool `SolutionPackager.exe`|Dabei handelt es sich um ein Tool, das umkehrbar eine mit Common Data Service für Apps komprimierte Lösungsdatei in mehrere XML-Dateien sowie andere Dateien zerlegen kann, damit diese Dateien ganz leicht über ein Quellcodeverwaltungssystem verwaltet werden können.<br /> Weitere Informationen finden Sie unter: <br />[Team development of solutions (Entwicklung von Lösungen im Team)](introduction-solutions.md#team-development-of-solutions)<br />[Verwenden des SolutionPackager-Tools, um eine Lösungsdatei zu komprimieren und zu extrahieren](/dynamics365/customer-engagement/developer/compress-extract-solution-file-solutionpackager)|

### <a name="net-sdk-assemblies"></a>.NET SDK-Assemblys 

Im Folgenden werden Assemblys aufgeführt, die von .NET-Entwicklern verwendet werden können. Sie können die neusten Versionen über die zugehörigen NuGet-Pakete herunterladen.

#### <a name="work-with-data"></a>Arbeiten mit Daten

Verwenden Sie diese Assembly, um mit dem Organisationsdienst und den Ermittlungsdiensten zu interagieren.

Weitere Informationen finden Sie unter [Verwenden des Dynamics 365-Organisationsdiensts](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service).

**NuGet Package**: [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)

|Assembly  |Namespaces  |
|---------|---------|
|Microsoft.Crm.Sdk.Proxy.dll|[Microsoft.Crm.Sdk](/dotnet/api/microsoft.crm.sdk)<br />[Microsoft.Crm.Sdk.Messages](/dotnet/api/microsoft.crm.sdk.messages)|
|Microsoft.Crm.Sdk|[Microsoft.Xrm.Sdk](/dotnet/api/microsoft.xrm.sdk)<br />[Microsoft.Xrm.Sdk.Client](/dotnet/api/microsoft.xrm.sdk.client)<br />[Microsoft.Xrm.Sdk.Discovery](/dotnet/api/microsoft.xrm.sdk.discovery)<br />[Microsoft.Xrm.Sdk.Messages](/dotnet/api/microsoft.xrm.sdk.messages)<br />[Microsoft.Xrm.Sdk.Metadata](/dotnet/api/microsoft.xrm.sdk.metadata)<br />[Microsoft.Xrm.Sdk.Metadata.Query](/dotnet/api/microsoft.xrm.sdk.metadata.query)<br />[Microsoft.Xrm.Sdk.Organization](/dotnet/api/microsoft.xrm.sdk.organization)<br />[Microsoft.Xrm.Sdk.Query](/dotnet/api/microsoft.xrm.sdk.query)<br />[Microsoft.Xrm.Sdk.WebServiceClient](/dotnet/api/microsoft.xrm.sdk.webserviceclient)|

#### <a name="create-process-designer-workflow-extensions"></a>Erstellen von Prozessdesigner-Erweiterungen (für Workflows)

Verwenden Sie diese Assembly, um dem Prozessdesigner benutzerdefinierte Aktivitäten hinzuzufügen. 

Weitere Informationen finden Sie unter [Benutzerdefinierte Workflowaktivitäten (Workflowassemblys)](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies).

**NuGet Package**: [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) 

|Assembly|Namespaces|
|---------|---------|
|Microsoft.Xrm.Sdk.Workflow.dll|[Microsoft.Xrm.Sdk.Workflow](/dotnet/api/microsoft.xrm.sdk.workflow)<br />[Microsoft.Xrm.Sdk.Workflow.Activities](/dotnet/api/microsoft.xrm.sdk.workflow.activities)<br />[Microsoft.Xrm.Sdk.Workflow.Designers](/dotnet/api/microsoft.xrm.sdk.workflow.designers)|

#### <a name="build-windows-client-applications"></a>Erstellen von Windows-Clientanwendungen

Verwenden Sie diese Assemblys, um einfacher eine Verbindung mit dem Organisationsdienst herzustellen und um Windows-Clientanwendungen zu erstellen. 

Weitere Informationen finden Sie unter [Erstellen von Windows-Clientanwendungen mithilfe der XRM-Tools](/dynamics365/customer-engagement/developer/build-windows-client-applications-xrm-tools)

**NuGet-Pakete:**
- [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) (Microsoft.Xrm.Tooling.Connector.dll)
- [Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/) 

|Assembly|Namespaces  |
|---------|---------|
|Microsoft.Xrm.Tooling.Connector.dll|[Microsoft.Xrm.Tooling.Connector](/dotnet/api/microsoft.xrm.tooling.connector)<br />[Microsoft.Xrm.Tooling.Connector.Model](/dotnet/api/microsoft.xrm.tooling.connector.model)|
|Microsoft.Xrm.Tooling.CrmConnectControl.dll|[Microsoft.Xrm.Tooling.CrmConnectControl](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Model](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.model)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Properties](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.properties)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Utility](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.utility)|
|Microsoft.Xrm.Tooling.WebResourceUtility.dll|[Microsoft.Xrm.Tooling.WebResourceUtility](/dotnet/api/microsoft.xrm.tooling.webresourceutility)|

#### <a name="create-packages"></a>Erstellen von Paketen

Verwenden Sie diese Assemblys, um Pakete für Package Deployer zu erstellen.

Weitere Informationen finden Sie unter [Dynamics 365 Customer Engagement Developer Guide: Create packages for the Dynamics 365 Package Deployer (Entwicklerhandbuch zu Dynamics 365 Customer Engagement: Erstellen von Paketen für Dynamics 365-Package Deployer)](/dynamics365/customer-engagement/developer/create-packages-package-deployer)

**NuGet Package**: [Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)

|Assembly|Namespace  |
|---------|---------|
|Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll|[Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase](/dotnet/api/microsoft.xrm.tooling.packagedeployment.crmpackageextentionbase)|

#### <a name="create-custom-virtual-entity-data-providers"></a>Erstellen von Datenanbieter für benutzerdefinierte virtuelle Entitäten

Verwenden Sie diese Assembly, um Datenanbieter für benutzerdefinierte virtuelle Entitäten zu erstellen. 

Weitere Informationen finden Sie unter [Erste Schritte mit virtuellen Entitäten](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve).

**NuGet Package**: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

|Assembly  |Namespaces  |
|---------|---------|
|Microsoft.Xrm.Sdk.Data.dll|[Microsoft.Xrm.Sdk.Data](/dotnet/api/microsoft.xrm.sdk.data)<br />[Microsoft.Xrm.Sdk.Data.CodeGen](/api/microsoft.xrm.sdk.data.codegen)<br />[Microsoft.Xrm.Sdk.Data.Converters](/dotnet/api/microsoft.xrm.sdk.data.converters)<br />[Microsoft.Xrm.Sdk.Data.Exceptions](/dotnet/api/microsoft.xrm.sdk.data.exceptions)<br />[Microsoft.Xrm.Sdk.Data.Expressions](/dotnet/api/microsoft.xrm.sdk.data.expressions)<br />[Microsoft.Xrm.Sdk.Data.Infra](/dotnet/api/microsoft.xrm.sdk.data.infra)<br />[Microsoft.Xrm.Sdk.Data.Mappings](/dotnet/api/microsoft.xrm.sdk.data.mappings)|

#### <a name="extend-outlook-client"></a>Erweitern des Outlook-Clients

Verwenden Sie diese Assembly, um mit Microsoft Dynamics 365 für Outlook und Microsoft Dynamics 365 für Microsoft Office Outlook mit Offlinezugriff zu interagieren. 

Weitere Informationen finden Sie unter [Erweitern von Dynamics 365 Customer Engagement für Outlook](/dynamics365/customer-engagement/developer/extend-customer-engagement-outlook)

**NuGet Package**: [Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)

|Assembly|Namespace|
|---------|---------|
|Microsoft.Crm.Outlook.Sdk.dll|[Microsoft.Crm.Outlook.Sdk](/dotnet/api/microsoft.crm.outlook.sdk)|



### <a name="community-tools-for-common-data-service-for-apps"></a>Communitytools für Common Data Service für Apps

Die Dynamics 365-Community erstellt Tools. Viele der beliebtesten Tools werden über [XrmToolBox](https://www.xrmtoolbox.com/) veröffentlicht. XrmToolBox ist eine Windows-Anwendung, die eine Verbindung mit Common Data Service für Apps herstellt, um Tools bereitzustellen, mit denen die Anpassungs-, Konfigurations- und Vorgangsaufgaben erleichtert werden. Die Anwendung enthält mehr als 30 Plug-Ins, um Verwaltungs-, Anpassungs- oder Konfigurationsaufgaben zu vereinfachen und zu beschleunigen.

Im Folgenden finden Sie eine Liste mit ausgewählten Communitytools, die über XrmToolBox verteilt werden und die Sie für die Arbeit mit Common Data Service für Apps verwenden können.

|Tool  |Beschreibung  |
|---------|---------|
|[Attribute Manager](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)|Wird zum Umbenennen, Löschen oder Ändern von Attributtypen verwendet|
|[Early Bound Generator](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.EarlyBoundGenerator/)|Generiert früh gebundene Entitäten, Optionseinstellungen und Aktionen. Verwendet CrmSvcUtil aus dem SDK und zeigt die Befehlszeile an, die zum Erstellen von Klassen verwendet wird.|
|[Export to Excel](https://www.xrmtoolbox.com/plugins/Ryr.XrmToolBox.ExportToExcel/)|Einfaches Exportieren von Datensätzen aus der ausgewählten Ansicht oder FetchXML in Excel|
|[FetchXML Builder](https://www.xrmtoolbox.com/plugins/Cinteros.Xrm.FetchXmlBuilder/)|Erstellt und testet FetchXml-Abfragen|
|[Metadata Browser](https://www.xrmtoolbox.com/plugins/MsCrmTools.MetadataBrowser/)|Durchsucht die Metadaten Ihrer Dynamics CRM-Organisation|
|[Plugin Trace Viewer](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.PluginTraceViewer/)|Untersucht das Nachverfolgungsprotokoll für Plug-Ins mit einfachen Möglichkeiten zum Filtern und Anzeigen|
|[User Settings Utility](https://www.xrmtoolbox.com/plugins/MsCrmTools.UserSettingsUtility/)|Verwaltet mehrere persönliche Einstellungen von Benutzern gleichzeitig|

> [!NOTE]
> Von der Community erstellte Tools werden von Microsoft nicht unterstützt. Wenden Sie sich an den Herausgeber, wenn Sie Probleme mit oder Fragen zu einem Tool haben.

---
title: Entwicklertools und -ressourcen (Common Data Service) | Microsoft Docs
description: Informationen zu verfügbaren Tools und Ressourcen beim Arbeiten mit Lösungen.
ms.custom: ''
ms.date: 1/31/2019
ms.reviewer: pehecke
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

# <a name="developer-tools-and-resources"></a>Entwicklertools und -ressourcen

Entwickler verwenden die folgenden Tools und Ressourcen, wenn sie mit Lösungen arbeiten, die Common Data Service verwenden.

## <a name="tools-available-for-download-from-nuget"></a>Tools verfügbar zum Herunterladen bei NuGet

Die folgenden Tools werden in NuGet-Paketen verteilt. Das [Entwicklerhandbuch: Herunterladen von Entwicklertools von NuGet](/dynamics365/customer-engagement/developer/download-tools-nuget) enthält ein PowerShell-Skript, das Sie verwenden können, um die neuesten Versionen dieser Tools herunterzuladen und zu extrahieren.

|Tool  |Beschreibung  |
|---------|---------|
|Codeerstellungstool `CrmSvcUtil.exe`|Ein Befehlszeilencodegenerierungstool, das .NET Framework-Klassen mit früher Bindung erzeugt, die das vom Organisationsservice verwendete Entitätsdatenmodell darstellen. <br />Weitere Informationen: <br />[Organisationsdienst](work-with-data-cds.md#organization-service)<br />[Entitätsklassen mit früher Bindung mit dem Codegenerierungstool erstellen (CrmSvcUtil.exe) ](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)|
|Configuration Migration-Tool `DataMigrationUtility.exe`|Wird verwendet, um Konfigurationsdaten in verschiedenen Umgebungen zu verschieben. Konfigurationsdaten werden verwendet, um benutzerdefinierte Funktionen in  zu definieren und sind normalerweise in benutzerdefinierten Entitäten gespeichert. Dieses Tool ist nicht dazu gedacht, Geschäftsdaten zu verschieben. <br /> Weitere Informationen: [Common Data Service-Administratorhandbuch: Verschieben von Konfigurationsdaten über Instanzen und Organisationen hinweg mit dem Konfigurationsmigration-Tool](/dynamics365/customer-engagement/admin/manage-configuration-data)|
|Package Deployer `PackageDeployer.exe`|Wird verwendet, um Pakete in Common Data Service-Instanzen bereitzustellen. Ein Paket ist eine installierbare Einheit, die Lösungen beinhaltet. <br /> Weitere Informationen: <br />[Bereitstellen von Lösungspaketen](introduction-solutions.md#deploy-solution-packages)<br />[Erstellen von Paketen für den Common Data Service Package Deployer](/dynamics365/customer-engagement/developer/create-packages-package-deployer)|
|Plug-In-Registrierungstool `PluginRegistration.exe`|Ein Tool, das verwendet wird, um Plug-In-Klassen der.NET-Assembly für Serverereignisse zu abonnieren. <br />Weitere Informationen: <br />[Plug-In erstellen](apply-business-logic-with-code.md#create-a-plug-in)<br />[Registrieren eines Plug-Ins](register-plug-in.md)|
|SolutionPackager-Tool `SolutionPackager.exe`|Ein Tool, mit dem eine komprimierte Common Data Service-Lösungsdatei reversibel in mehrere XML-Dateien und andere Dateien zerlegt werden kann, sodass diese Dateien durch ein Quellcodeverwaltungssystem leicht verwaltet werden können.<br /> Weitere Informationen: <br />[Teamentwicklung von Lösungen](introduction-solutions.md#team-development-of-solutions)<br />[Verwenden des SolutionPackager-Tools, um eine Lösungsdatei zu komprimieren und zu extrahieren](/dynamics365/customer-engagement/developer/compress-extract-solution-file-solutionpackager)|

## <a name="net-sdk-assemblies"></a>.NET-SDK-Assemblys 

Im Folgenden finden Sie Assemblys, die von NET-Entwicklern verwendet werden können. Die neuesten Versionen stehen in den entsprechenden NuGet-Paketen zum Download bereit.

### <a name="work-with-data"></a>Verwenden von Daten

Verwenden Sie die Assemblys, um mit dem Organisationsservice und den Suchservices zu interagieren.

Weitere Informationen: [Verwenden des Common Data Service-Organisationsservice](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service)

**NuGet-Paket**: [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)

|Assembly  |Namespaces  |
|---------|---------|
|Microsoft.Crm.Sdk.Proxy.dll|[Microsoft.Crm.Sdk](/dotnet/api/microsoft.crm.sdk)<br />[Microsoft.Crm.Sdk.Messages](/dotnet/api/microsoft.crm.sdk.messages)|
|Microsoft.Xrm.Sdk.dll|[Microsoft.Xrm.Sdk](/dotnet/api/microsoft.xrm.sdk)<br />[Microsoft.Xrm.Sdk.Client](/dotnet/api/microsoft.xrm.sdk.client)<br />[Microsoft.Xrm.Sdk.Discovery](/dotnet/api/microsoft.xrm.sdk.discovery)<br />[Microsoft.Xrm.Sdk.Messages](/dotnet/api/microsoft.xrm.sdk.messages)<br />[Microsoft.Xrm.Sdk.Metadata](/dotnet/api/microsoft.xrm.sdk.metadata)<br />[Microsoft.Xrm.Sdk.Metadata.Query](/dotnet/api/microsoft.xrm.sdk.metadata.query)<br />[Microsoft.Xrm.Sdk.Organization](/dotnet/api/microsoft.xrm.sdk.organization)<br />[Microsoft.Xrm.Sdk.Query](/dotnet/api/microsoft.xrm.sdk.query)<br />[Microsoft.Xrm.Sdk.WebServiceClient](/dotnet/api/microsoft.xrm.sdk.webserviceclient)|

### <a name="create-process-designer-workflow-extensions"></a>Erweiterungen für den Prozessdesigner (Workflow) erstellen

Verwenden Sie diese Assembly, um dem Prozessdesigner benutzerdefinierte Aktivitäten hinzuzufügen. 

Weitere Informationen [Benutzerdefinierte Workflowaktivitäten (Workflowassemblys)](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies)

**NuGet-Paket**: [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) 

|Assembly|Namespaces|
|---------|---------|
|Microsoft.Xrm.Sdk.Workflow.dll|[Microsoft.Xrm.Sdk.Workflow](/dotnet/api/microsoft.xrm.sdk.workflow)<br />[Microsoft.Xrm.Sdk.Workflow.Activities](/dotnet/api/microsoft.xrm.sdk.workflow.activities)<br />[Microsoft.Xrm.Sdk.Workflow.Designers](/dotnet/api/microsoft.xrm.sdk.workflow.designers)|

### <a name="build-windows-client-applications"></a>Erstellen von Windows-Clientanwendungen

Verwenden Sie diese Assemblys, um die Verbindung zum Organisationsservice zu erleichtern und Windows-Clientanwendungen zu erstellen. 

Weitere Informationen [Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](/dynamics365/customer-engagement/developer/build-windows-client-applications-xrm-tools)

**NuGet-Pakete**:
- [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) (Microsoft.Xrm.Tooling.Connector.dll)
- [Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/) 

|Assembly|Namespaces  |
|---------|---------|
|Microsoft.Xrm.Tooling.Connector.dll|[Microsoft.Xrm.Tooling.Connector](/dotnet/api/microsoft.xrm.tooling.connector)<br />[Microsoft.Xrm.Tooling.Connector.Model](/dotnet/api/microsoft.xrm.tooling.connector.model)|
|Microsoft.Xrm.Tooling.CrmConnectControl.dll|[Microsoft.Xrm.Tooling.CrmConnectControl](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Model](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.model)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Properties](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.properties)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Utility](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.utility)|
|Microsoft.Xrm.Tooling.WebResourceUtility.dll|[Microsoft.Xrm.Tooling.WebResourceUtility](/dotnet/api/microsoft.xrm.tooling.webresourceutility)|

### <a name="create-packages"></a>Erstellen von Paketen

Verwenden Sie diese Assemblys, um Pakete für den Package Deployer zu erstellen.

Weitere Informationen: [Erstellen von Paketen für den Common Data Service Package Deployer](/dynamics365/customer-engagement/developer/create-packages-package-deployer)

**NuGet-Paket**: [Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)

|Assembly|Namespace  |
|---------|---------|
|Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll|[Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase](/dotnet/api/microsoft.xrm.tooling.packagedeployment.crmpackageextentionbase)|

### <a name="create-custom-virtual-entity-data-providers"></a>Erstellen eines benutzerdefinierten virtuelle Entitätsdatenanbieter

Verwenden Sie diese Assembly, um benutzerdefinierte virtuelle Entitätsdatenanbieter zu erstellen. 

Weitere Informationen: [Erste Schritte mit virtuellen Entitäten](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)

**NuGet-Paket**: [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

|Assembly  |Namespaces  |
|---------|---------|
|Microsoft.Xrm.Sdk.Data.dll|[Microsoft.Xrm.Sdk.Data](/dotnet/api/microsoft.xrm.sdk.data)<br />[Microsoft.Xrm.Sdk.Data.CodeGen](/api/microsoft.xrm.sdk.data.codegen)<br />[Microsoft.Xrm.Sdk.Data.Converters](/dotnet/api/microsoft.xrm.sdk.data.converters)<br />[Microsoft.Xrm.Sdk.Data.Exceptions](/dotnet/api/microsoft.xrm.sdk.data.exceptions)<br />[Microsoft.Xrm.Sdk.Data.Expressions](/dotnet/api/microsoft.xrm.sdk.data.expressions)<br />[Microsoft.Xrm.Sdk.Data.Infra](/dotnet/api/microsoft.xrm.sdk.data.infra)<br />[Microsoft.Xrm.Sdk.Data.Mappings](/dotnet/api/microsoft.xrm.sdk.data.mappings)|

### <a name="extend-outlook-client"></a>Outlook-Client erweitern

Mithilfe dieser Assembly können Sie mit Microsoft Dynamics 365 for Outlook und Microsoft Common Data Service für Microsoft Office Outlook mit Offlinezugriff interagieren. 

Weitere Informationen: [Erweitern von Dynamics 365 for Outlook](/dynamics365/customer-engagement/developer/extend-customer-engagement-outlook)

**NuGet-Paket**: [Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)

|Assembly|Namespace|
|---------|---------|
|Microsoft.Crm.Outlook.Sdk.dll|[Microsoft.Crm.Outlook.Sdk](/dotnet/api/microsoft.crm.outlook.sdk)|


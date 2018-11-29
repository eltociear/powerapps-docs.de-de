---
title: Abonnieren Sie SDK-Assembly-Updates mithilfe von NuGet (Common Data Service for Apps) | Microsoft Docs
description: '.NET-SDK-Assemblys und einige Befehlszeilentools sind durch eine Softwareverteilungswebsite verfügbar nuget.org. Verwendung von NuGet Paketen in Ihrem Anwendungsprojekt ermöglicht Ihnen, das aktuelle Projekt beizubehalten mit den neuesten Versionen der SDK-Assemblys und Tools.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="subscribe-to-sdk-assembly-updates-using-nuget"></a>Abonnieren von SDK-Assemblyaktualisierungen mithilfe von NuGet

.NET-SDK-Assemblys und einige Befehlszeilentools sind durch eine Softwareverteilungswebsite verfügbar [nuget.org.](http://www.nuget.org). Verwendung von NuGet-Paketen in Ihrem Anwendungsprojekt ermöglicht Ihnen, das aktuelle Projekt beizubehalten mit den neuesten Versionen der SDK-Assemblys und Tools. Visual Studio hat diese Funktion seit Version 2010 unterstützt und es gibt sogar einen eigenständigen NuGet-Client für diese Entwickler, die nicht in Visual Studio entwickeln. Ein weiterer Vorteil der Verwendung der NuGet-Pakete in Ihren Projekten besteht darin, dass Assembly-Verweise und Abhängigkeiten für Sie automatisch versorgt werden. NuGet-Pakete sind für allgemeine Common Data Service for Apps und für und sich von ältere Versionen von Dynamics 365 Customer Engagement verfügbar.  
  
<a name="BKMK_GetNuGetPackages"></a>

## <a name="where-to-find-the-nuget-sdk-packages"></a>Bezugsquellen für NuGet SDK-Pakete

Die NuGet-SDK-Pakete befinden sich unter dem [crmsdk](https://www.nuget.org/profiles/crmsdk)-Profil. Dies sind die offiziellen CDS for Apps-Pakete. Wählen Sie ein Paket in der Liste aus, um die Paketdetailseite aufzurufen. Die folgenden sind die aktuellen NuGet-Pakete, die relevant sind für CDS for Apps.  


|Paket|Beschreibung|
|---------|---------|
|[Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)|Enthält die Microsoft.Xrm.Sdk.dll- sowie Microsoft.Crm.Sdk.Proxy.dll-Assemblys und Tools|
|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools/)|Enthält die SDK-Tools, der vom Microsoft Dynamics 365-Team erstellt werden.|
|[Microsoft.CrmSdk.Deployment](https://www.nuget.org/packages/Microsoft.CrmSdk.Deployment/)|Enthält die Microsoft.Xrm.Sdk.Deployment.dll-Assembly|
|[Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)|Enthält die Microsoft.Crm.Outlook.dll-Assembly|
|[Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/)|C#-Hilfecode, erstellt vom Microsoft Dynamics 365 Customer Engagement-Entwicklerdokumentationsteam. Dieser Code ist für die Verwendung mit Internet-API. Diese Klassen bieten Webdienstauthentifizierung Online und lokale Bereitstellungen, und Verbindungszeichenfolgenkonfiguration Fehlerbehandlung. Diese Klassen werden in den Web-API-Beispielen verwendet|
|[Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/)|Enthält die Microsoft.Xrm.Sdk.Workflow.dll-Assembly|
|[Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/)|Enthält die Microsoft.Xrm.Tooling.Connector-Assembly |
|[Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell/)|Enthält die Assemblies für Xrm.Tooling.Connector Powershell |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell/)| Enthält die Assemblies für Package Deployer Powershell        |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf/)|Enthält den Dynamics 365 Package Deployer|
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)|Enthält die Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll-Assembly|
|[Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool/)|Enthält das Plug-In-Registrierungstool, das erforderlich ist, um Plug-In-Assemblys, Workflow-Assemblys virtuelle Entitäten und Dienstendpunkte für Microsoft Dynamics 365 zu verwalten.|
|[Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/)|Enthält die Microsoft.Xrm.Tooling.CrmConnectControl.dll, Microsoft.Xrm.Tooling.Ui.Styles.dll uand Microsoft.Xrm.Tooling.WebResourceUtility.dll-Assemblies|

## <a name="how-to-install-a-package-in-your-project"></a>So installieren Sie ein Paket im Projekt  
 Informationen zum Installieren von NuGet-Paketen im Projekt finden Sie unter [Verwalten von NuGet-Paketen mithilfe des Dialogfelds](http://docs.nuget.org/docs/start-here/managing-nuget-packages-using-the-dialog).  

## <a name="download-tools-from-nuget"></a>Herunterladen von Tools von NuGet

Sie können Tools für die Entwicklung von NuGet mithilfe des PowerShell-Skripts herunterladen, das Sie in diesem Thema finden: [Tools von NuGet herunterladen](../download-tools-nuget.md)
  
### <a name="see-also"></a>Siehe auch  
 [NuGet-Dokumentation](/nuget/)   
 [Installieren von NuGet](http://docs.nuget.org/docs/start-here/installing-nuget)
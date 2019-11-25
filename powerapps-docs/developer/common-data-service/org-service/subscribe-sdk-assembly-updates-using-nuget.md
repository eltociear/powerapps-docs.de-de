---
title: Abonnieren von SDK-Assembly-Updates mit NuGet (Common Data Service) | Microsoft Docs
description: .NET SDK-Assemblies und einige Befehlszeilen-Tools sind über eine Software-Verteilungs-Website namens nuget.org verfügbar. Die Verwendung von NuGet-Paketen in Ihrem Anwendungsprojekt ermöglicht es Ihnen, Ihr Projekt auf dem neuesten Stand der neuesten Versionen der SDK-Assemblies und -Tools zu halten.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: dd5d967cae6988c7949c1c6eca0b862cf42281b0
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752950"
---
# <a name="subscribe-to-sdk-assembly-updates-using-nuget"></a>Abonnieren Sie SDK-Assembly-Updates mit NuGet.

.NET SDK-Assemblies und einige Befehlszeilen-Tools sind über eine Software-Verteilungs-Website namens [nuget.org](https://www.nuget.org) verfügbar. Die Verwendung von NuGet-Paketen in Ihrem Anwendungsprojekt ermöglicht es Ihnen, Ihr Projekt auf dem neuesten Stand der neuesten Versionen der SDK-Assemblies und -Tools zu halten. Visual Studio unterstützt diese Funktion seit Version 2010 und es gibt sogar einen eigenständigen NuGet-Client für Entwickler, die nicht in Visual Studio entwickeln. Ein weiterer Vorteil der Verwendung von NuGet-Paketen in Ihren Projekten besteht darin, dass Assembly-Hinweise und Abhängigkeiten automatisch für Sie erledigt werden.  
  
<a name="BKMK_GetNuGetPackages"></a>

## <a name="where-to-find-the-nuget-sdk-packages"></a>Wo finde ich die NuGet SDK-Pakete?

Das NuGet SDK befindet sich unter dem Profil [crmsdk](https://www.nuget.org/profiles/crmsdk). Dies sind die offiziellen Common Data Service-Pakete. Wählen Sie ein Paket in der Liste aus, um die Paketdetailseite aufzurufen. Nachfolgend sind die aktuellen NuGet-Pakete aufgeführt, die für Common Data Service relevant sind.  


|Paket|Beschreibung|
|---------|---------|
|[Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)|Enthält die Microsoft.Xrm.Sdk.dll- sowie Microsoft.Crm.Sdk.Proxy.dll-Assemblys und Tools|
|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools/)|Enthält die SDK-Tools, die vom Team Microsoft Dynamics 365 erstellt wurden.|
|[Microsoft.CrmSdk.Deployment](https://www.nuget.org/packages/Microsoft.CrmSdk.Deployment/)|Enthält die Microsoft.Xrm.Sdk.Deployment.dll-Assembly|
|[Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)|Enthält die Microsoft.Crm.Outlook.dll-Assembly|
|[Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/)|C#-Helfer-Code, der vom Dokumentationsteam PowerApps geschrieben wurde. Dieser Code ist für die Verwendung mit Internet-API. Diese Klassen bieten Webdienstauthentifizierung Online und lokale Bereitstellungen, und Verbindungszeichenfolgenkonfiguration Fehlerbehandlung. Diese Klassen werden in den Web-API-Beispielen verwendet|
|[Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/)|Enthält die Microsoft.Xrm.Sdk.Workflow.dll-Assembly|
|[Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/)|Enthält die Microsoft.Xrm.Tooling.Connector-Assembly |
|[Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell/)|Enthält die Assemblies für Xrm.Tooling.Connector Powershell |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.PowerShell/)| Enthält die Assemblies für Package Deployer Powershell        |
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf/)|Enthält die Dynamics 365 Package Deployer.|
|[Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)|Enthält die Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll-Assembly|
|[Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool/)|Enthält das Plugin-Registrierungstool, das zur Verwaltung von Plugin-Assemblies, Workflow-Assemblies, virtuellen Berechtigungen und Service-Endpunkten für Microsoft Dynamics 365 erforderlich ist.|
|[Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/)|Enthält die Microsoft.Xrm.Tooling.CrmConnectControl.dll, Microsoft.Xrm.Tooling.Ui.Styles.dll uand Microsoft.Xrm.Tooling.WebResourceUtility.dll-Assemblies|

## <a name="how-to-install-a-package-in-your-project"></a>So installieren Sie ein Paket im Projekt  
 Informationen zur Installation von NuGet-Paketen in Ihrem Projekt finden Sie unter [Verwaltung von NuGet-Paketen über den Dialog](https://docs.nuget.org/docs/start-here/managing-nuget-packages-using-the-dialog).  

## <a name="download-tools-from-nuget"></a>Herunterladen von Tools von NuGet

Sie können die in der Entwicklung verwendeten Tools von NuGet mit dem Powershell-Skript in diesem Thema herunterladen: [Download der Tools von NuGet](../download-tools-nuget.md)
  
### <a name="see-also"></a>Siehe auch  
 [NuGetDokumentation](/nuget/)   
 [InstallierenNuGet](https://docs.nuget.org/docs/start-here/installing-nuget)
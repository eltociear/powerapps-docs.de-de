---
title: Tools von NuGet herunterladen (Common Data Service) Startseite | Microsoft Docs
description: 'Laden Sie die Plug-in-Registrierung, Paketbereitstellung und andere Kerntools von Nuget herunter.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: feb3e634-7c60-46fd-8b92-3f5682b1570b
author: shmcarth
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="download-tools-from-nuget"></a>Herunterladen von Tools von NuGet 

Sie können Tools herunterladen, die bei der Entwicklung von NuGet mithilfe des PowerShell-Skripts verwendet werden, das unten gefunden wird. Zu diesen Tools gehören:

|Tool|NuGet-Paket|
|-|-|
|Codeerstellungstool `CrmSvcUtil.exe`|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools)|
|Configuration Migration-Tool `DataMigrationUtility.exe`|[Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf)|
|Package Deployer `PackageDeployer.exe`|[Microsoft.CrmSdk.XrmTooling.PackageDeployment.WPF](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf)|
|Plug-In-Registrierungstool `PluginRegistration.exe` |[Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool)|
|SolutionPackager-Tool `SolutionPackager.exe`|[Microsoft.CrmSdk.CoreTools](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreTools)|

## <a name="download-tools-using-powershell"></a>Herunterladen von Tools mit PowerShell

1. In Ihrem Windows-Startmenü geben Sie `Windows Powershell` ein und öffnen Sie es.
1. Navigieren Sie zu dem Ordner, in dem Sie die Tools installieren möchten. Beispielsweise, wenn Sie sie im `devtools`-Ordner auf dem D-Laufwerk installieren möchten, geben Sie `cd D:\devtools` ein.
1. Kopieren Sie das folgende PowerShell-Skript in das PowerShell-Fenster und drücken Sie die EINGABETASTE.

    ```powershell
    $sourceNugetExe = "https://dist.nuget.org/win-x86-commandline/latest/nuget.exe"
    $targetNugetExe = ".\nuget.exe"
    Remove-Item .\Tools -Force -Recurse -ErrorAction Ignore
    Invoke-WebRequest $sourceNugetExe -OutFile $targetNugetExe
    Set-Alias nuget $targetNugetExe -Scope Global -Verbose
        
    ##
    ##Download Plugin Registration Tool
    ##
    ./nuget install Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool -O .\Tools
    md .\Tools\PluginRegistration
    $prtFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool.'}
    move .\Tools\$prtFolder\tools\*.* .\Tools\PluginRegistration
    Remove-Item .\Tools\$prtFolder -Force -Recurse
    
    ##
    ##Download CoreTools
    ##
    ./nuget install  Microsoft.CrmSdk.CoreTools -O .\Tools
    md .\Tools\CoreTools
    $coreToolsFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.CoreTools.'}
    move .\Tools\$coreToolsFolder\content\bin\coretools\*.* .\Tools\CoreTools
    Remove-Item .\Tools\$coreToolsFolder -Force -Recurse

    ##
    ##Download Configuration Migration
    ##
    ./nuget install  Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf -O .\Tools
    md .\Tools\ConfigurationMigration
    $configMigFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.ConfigurationMigration.Wpf.'}
    move .\Tools\$configMigFolder\tools\*.* .\Tools\ConfigurationMigration
    Remove-Item .\Tools\$configMigFolder -Force -Recurse
    
    ##
    ##Download Package Deployer 
    ##
    ./nuget install  Microsoft.CrmSdk.XrmTooling.PackageDeployment.WPF -O .\Tools
    md .\Tools\PackageDeployment
    $pdFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf.'}
    move .\Tools\$pdFolder\tools\*.* .\Tools\PackageDeployment
    Remove-Item .\Tools\$pdFolder -Force -Recurse

    ##
    ##Remove NuGet.exe
    ##
    Remove-Item nuget.exe    
    ```

1. Sie finden die Tools in folgenden Ordnen:

- `[Your folder]\Tools\ConfigurationMigration`
- `[Your folder]\Tools\CoreTools`
- `[Your folder]\Tools\PackageDeployment`
- `[Your folder]\Tools\PluginRegistration`

Um die neueste Version der Tools abzurufen, wiederholen Sie diese Schritte.

## <a name="see-also"></a>Siehe auch

[Entwicklertools](developer-tools.md)<br />
[Visual Studio und .NET Framework](org-service/visual-studio-dot-net-framework.md)<br />
[Erstellen früh gebundener Entitätsklassen](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)<br />
[Erstellen von Erweiterungen für das Codegenerierungstool](org-service/extend-code-generation-tool.md)<br />
[Durchsuchen der Metadaten für die Organisation](browse-your-metadata.md)<br />
[Bereitstellen von Paketen mit dem Dynamics 365 Package Deployer und Windows PowerShell](/dynamics365/customer-engagement/admin/deploy-packages-using-package-deployer-windows-powershell)<br />
[Registrieren eines Plug-Ins](register-plug-in.md)<br />

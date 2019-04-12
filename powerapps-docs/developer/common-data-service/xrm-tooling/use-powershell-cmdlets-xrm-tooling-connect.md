---
title: Verwenden von PowerShell-cmdlets für XRM-Tooling zum Verbinden mit Common Data Service (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie, wie Sie Powershell-Cmdlets für XRM-Tooling wie Get-CrmConnection und Get-CrmOrganizations verwenden, um eine Verbindung mit Common Data Service herzustellen und Organisationen abzurufen, auf die der aktuelle Benutzer zugreifen kann'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 81816457-c963-46ca-b350-615fa75f56a7
caps.latest.revision: 27
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-powershell-cmdlets-for-xrm-tooling-to-connect-to-common-data-service"></a>Verwenden von PowerShell-Cmdlets für XRM-Tooling zum Verbinden mit Common Data Service

XRM-Tooling stellt die folgenden Windows PowerShell-Cmdlets bereit, die Sie verwenden können, um eine Verbindung mit Common Data Service herzustellen und Organisationen abzurufen, auf die der aktuelle Benutzer Zugriff hat: `Get-CrmConnection` und `Get-CrmOrganizations`.  
  
<a name="Prereq"></a>   

## <a name="prerequisites"></a>Voraussetzungen  
  
-   Um die XRM Tooling-Cmdlets zu verwenden, benötigen Sie PowerShell Version 3.0 oder höher. Öffnen Sie zur Prüfung der Version ein PowerShell-Fenster und führen Sie dann den folgenden Befehl aus: `$Host`.  
  
-   Legen Sie die Ausführungsrichtlinie für die Ausführung der signierten PowerShell-Skripts fest. Öffnen Sie hierzu als Administrator ein PowerShell-Fenster und führen Sie den folgenden Befehl aus: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned`  
  
<a name="register"></a>   

## <a name="register-the-cmdlets"></a>Registrieren des Cmdlets  

 Bevor Sie die PowerShell-Cmdlets verwenden können, müssen Sie sie registrieren. Die XRM-Werkzeugausstattung PowerShell-Cmdlets werden als NuGet-Paket hier verfügbar: [https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell/). Zum Herunterladen und Registrieren von cmdlets: 
  
1. Öffnen Sie Notizblock und kopieren Sie das folgende Skript:

    ```powershell
    @PowerShell.exe -ExecutionPolicy RemoteSigned -Command "Invoke-Expression -Command ((Get-Content -Path '%~f0' | Select-Object -Skip 2) -join [environment]::NewLine)"
    @exit /b %Errorlevel%
    $currentFolder = Get-Location
    cd $currentFolder
    $sourceNugetExe = "https://dist.nuget.org/win-x86-commandline/latest/nuget.exe"
    $targetNugetExe = ".\nuget.exe"
    Remove-Item .\Tools -Force -Recurse -ErrorAction Ignore
    Invoke-WebRequest $sourceNugetExe -OutFile $targetNugetExe
    Set-Alias nuget $targetNugetExe -Scope Global -Verbose

    ##
    ##Specify the NuGet package source
    ##
    $nugetPackageSource = "https://api.nuget.org/v3/index.json"

    ##
    ##Download XRM Tooling PowerShell cmdlets
    ##
    ./nuget install -source $nugetPackageSource Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell -O .\Tools
    md .\Tools\XRMToolingPowerShell
    $cmdletFolder = Get-ChildItem ./Tools | Where-Object {$_.Name -match 'Microsoft.CrmSdk.XrmTooling.CrmConnector.PowerShell.'}
    move .\Tools\$cmdletFolder\tools\*.* .\Tools\XRMToolingPowerShell
    Remove-Item .\Tools\$cmdletFolder -Force -Recurse

    ##
    ##Remove NuGet.exe
    ##
    Remove-Item nuget.exe
  
1. Save the notepad file as batch file on your computer: **GetTools.bat**.
1. Navigate to the folder where you saved the file, for example C:\SDK, and double-click the **GetTools.bat** file to run the script. This will create a Tools\XRMToolingPowerShell folder in the same location as your **GetTools.bat** file. The Tools\XRMToolingPowerShell folder contains the `RegisterXRMTooling.ps1` script to register the cmdlets, and other associated files.
1. Start PowerShell on your computer with elevated privileges (run as administrator).  
  
1.  At the prompt, change your directory to the folder that contains the PowerShell script for registering the cmdlets. For example:  
  
    ```powershell  
    cd c:\SDK\Tools\XRMToolingPowerShell  
    ```  
  
1.  Führen Sie das `RegisterXRMTooling.ps1`-Skript aus, um die XRM-Tooling-PowerShell-Cmdlets zu registrieren. Geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE:  
  
    ```powershell
    .\RegisterXRMTooling.ps1  
    ```
  
 Sie können jetzt diese PowerShell-Cmdlets verwenden. Um die Cmdlets aufzulisten, die Sie registriert haben, führen Sie den folgenden Befehl im PowerShell-Fenster aus.  
  
```powershell
Get-Help “Crm”  
```  
  
<a name="RetrieveOrgs"></a>   

## <a name="use-the-cmdlet-to-retrieve-organizations-from-common-data-service"></a>Verwenden Sie das Cmdlet, um Organisationen vom Common Data Service abzurufen  

Verwenden Sie das `Get-CrmOrganizations`-Cmdlet, um Organisationen abzurufen, auf die Sie Zugriff haben.  
  
1.  Stellen Sie die Anmeldeinformationen bereit, um eine Verbindung mit der Common Data Service-Instanz herzustellen. Bei Ausführung des folgenden Befehls werden Sie aufgefordert, Ihren Benutzernamen und Ihr Kennwort einzugeben, um eine Verbindung mit der Common Data Service-Instanz herzustellen, und sie wird in der `$Cred`-Variable gespeichert.  
  
    ```powershell  
    $Cred = Get-Credential  
    ```  
2.  Verwenden Sie den folgenden Befehl, um die Organisationen abzurufen, und speichern Sie die Informationen in der Variable `$CRMOrgs`: 

    - Wenn Sie eine Verbindung mit einer Common Data Service-Instanz herstellen:  
  
        ```powershell  
        $CRMOrgs = Get-CrmOrganizations -Credential $Cred -DeploymentRegion NorthAmerica –OnlineType Office365  
        ```  
  
        > [!NOTE]
        >  Für den Parameter `DeploymentRegion` sind gültige Werte `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` und `NorthAmerica2`. Für den `OnlineType` Parameter, definieren Sie `Office365`.
<!--   
    -   If you’re connecting to the on-premises server:  
  
        ```powershell  
        $CRMOrgs = Get-CrmOrganizations –ServerUrl http://<CRM_Server_Host> –Credential $Cred  
        ```      
  
    -   If you’re connecting to the Common Data Service server using the claims-based authentication against the specified Home realm:  
  
        ```powershell  
        $CRMOrgs = Get-CrmOrganizations –ServerUrl http://<CRM_Server_Host> –Credential $Cred –HomRealmURL http://<Identity_Provider_Address>  
        ```   -->
  
3.  Die angegebenen Anmeldeinformationen werden überprüft, wenn Sie den Befehl in Schritt 2 ausführen. Bei der erfolgreichen Ausführung des Befehls geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE, um die Organisationen anzuzeigen, auf die Sie Zugriff besitzen:  
  
    ```powershell  
    $CRMOrgs  
    ```  
  
    <!-- TODO:
     ![Common Data Service organization information](../media/xrmtooling-powershell-1.png)   -->
  
    > [!TIP]
    >  Sie können die Variable, die verwendet wurde, um die abgerufenen Common Data Service-Organisationen (in diesem Fall `$CRMOrgs`) zu speichern, mit dem `Get-CrmConnection`-Cmdlet verwenden, um eine Verbindung mit Common Data Service herzustellen. Um den Namen der Organisation anzugeben, verwenden Sie den folgenden Befehl: `$CRMOrgs.UniqueName`.  
    >   
    >  Wenn mehr als einen Organisationswert in der `$CRMOrgs`-Variable gespeichert ist, können auf die `nth`-Organisation mithilfe des folgenden Befehls verweisen: `$CRMOrgs[n-1]`. Wenn Sie beispielsweise auf den eindeutigen Namen der zweiten Organisation in der `$CRMOrgs`-Variable verweisen, verwenden Sie den folgenden Befehl: `$CRMOrgs[1].UniqueName`. Weitere Informationen: [Zugreifen auf Werte in einem Array](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692791\(v=technet.10\))  
  
<a name="ConnecttoCRM"></a>
   
## <a name="use-the-cmdlet-to-connect-to-common-data-service"></a>Verwenden des Cmdlet zur Herstellung einer Verbindung mit Common Data Service  

Verwenden Sie das Cmdlet `Get-CrmConnection` zur Herstellung einer Verbindung mit einer Common Data Service-Instanz. Mit dem Cmdlet können Sie entweder das allgemeine Anmeldungssteuerelement von XRM-Tooling verwenden, um die Anmeldeinformationen anzugeben und eine Verbindung mit Common Data Service herzustellen oder um die Anmeldeinformationen als Inline-Parameter anzugeben. Weitere Informationen: [Verwenden des allgemeinen XRM-Tooling-Anmeldungssteuerelements](use-xrm-tooling-common-login-control-client-applications.md)

> [!IMPORTANT]
> Vor der Nutzung des `Get-CrmConnection` cmdlets, stellen Sie sicher, dass Sie den folgenden Befehl  verwenden, um mithilfe von TLS 1,2 x PowerShell mit der Customer Engagement Instanz eine Verbindung herzustellen:<br/>
> `[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12`<br/>
> Weitere Informationen zur TLS Anforderung 1.2 für Customer Engagement Verbindung: [Blogbeitrag: Updates, die zur Dynamics 365 Customer Engagement Verbindungssicherheit beitragen](https://blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/)   
  
### <a name="connect-to-common-data-service-by-using-the-common-login-control"></a>Mit dem allgemeinen Anmeldungssteuerelement eine Verbindung mit Common Data Service herstellen  
  
1.  Wenn Sie das allgemeine Anmeldungssteuerelement verwenden möchten, um die Anmeldeinformationen bei der Herstellung einer Verbindung mit der Common Data Service-Instanz bereitzustellen, verwenden Sie den folgenden Befehl. Die Informationen werden in der `$CRMConn`-Variablen gespeichert, damit Sie sie später verwenden können.  
  
    ```powershell  
    $CRMConn = Get-CrmConnection -InteractiveMode  
    ```  
  
2.  Das Dialogfeld **Anmeldesteuerelement** wird angezeigt. Stellen Sie die Anmeldeinformationen bereit, um eine Verbindung mit der Common Data Service-Instanz herzustellen und klicken Sie auf **Anmelden**.  
  
### <a name="connect-to-common-data-service-by-specifying-credentials-inline"></a>Stellen Sie eine Verbindung mit Common Data Service her, indem Sie inline Anmeldeinformationen angeben.  
  
1.  Verwenden Sie die folgenden Befehle, um eine Verbindung mit Common Data Service herzustellen. Beachten Sie, dass diese befehle die `$Cred`-Variable verwenden, um die Anmeldeinformationen beim Abrufen der Organisationen zu speichern. Die Verbindungsinformationen werden in der `$CRMConn`-Variablen gespeichert:

    <!-- -   If you’re connecting to a Common Data Service instance:   -->
  
        ```powershell  
        $CRMConn = Get-CrmConnection -Credential $Cred -DeploymentRegion <Deployment region name> –OnlineType Office365 –OrganizationName <OrgName>  
        ```
  
        > [!NOTE]
        >  For the `DeploymentRegion` parameter, valid values are `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` and `NorthAmerica2`. For the `OnlineType` parameter, specify `Office365`. 
  
    <!-- not available for this version at this time
     -   If you’re connecting to the on-premises server:  
  
        ```powershell  
        $CRMConn = Get-CrmConnection –ServerUrl http://<CRM_Server_Host> -Credential $Cred -OrganizationName <OrgName>  
        ```
  
    -   If you’re connecting to the Common Data Service server using the claims-based authentication against the specified Home realm:  
  
        ```powershell  
        $CRMConn = Get-CrmConnection –ServerUrl http://<CRM_Server_Host> -Credential $Cred -OrganizationName <OrgName> –HomRealmURL http://<Identity_Provider_Address>  
        ```   -->
  
    > [!NOTE]
    > Für den Parameter `OrganizationName` in allen vorangehenden Befehlen können Sie entweder den eindeutigen Namen der Organisation oder den Anzeigenamens angeben. Sie können auch den eindeutigen Namen der Organisation oder den Anzeigenamen verwenden, den Sie mithilfe des `Get-CrmOrganizations`- Cmdlets erhalten und in der `$CRMOrgs`-Variablen gespeichert haben. So können Sie beispielsweise `$CRMOrgs[x].UniqueName` oder `$CRMOrgs[x].FriendlyName` verwenden.  
  
2.  Die angegebenen Anmeldeinformationen werden überprüft, wenn Sie den befehl  in Schritt 1 ausführen. Bei der erfolgreichen Ausführung des cmdlet geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE, um die Verbindungsinformationen und den Status anzuzeigen:  
  
    ```powershell  
    $CRMConn  
    ```  
  
    <!--TODO:
     ![Common Data Service connection information and status](../media/xrm-tooling-powershell-2.png "Common Data Service connection information and status")   -->
  
### <a name="see-also"></a>Siehe auch
  
[Verwenden der XRM-Tooling-API zur Herstellung einer Verbindung mit Common Data Service](use-crmserviceclient-constructors-connect.md)<br />
[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)<br />
[Blog: PowerShell-Modul für die Ausführung von Datenvorgängen und die Bearbeitung der Benutzer- und Systemeinstellungen in CRM](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)
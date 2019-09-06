---
title: 'Verwenden der PowerShell-Cmdlets für XRM-Tools, um eine Verbindung mit Common Data Service (Common Data Service) herzustellen | Microsoft Docs'
description: 'Erfahren Sie, wie Sie Powershell-Cmdlets für XRM-Tools wie Get-CrmConnection und Get-CrmOrganizations verwenden, um eine Verbindung mit Common Data Service herzustellen und Organisationen abzurufen, auf die der aktuelle Benutzer Zugriff hat.'
ms.custom: ''
ms.date: 03/27/2019
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
ms.author: nabuthuk
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-powershell-cmdlets-for-xrm-tooling-to-connect-to-common-data-service"></a>Verwenden Sie PowerShell-Cmdlets für XRM-Tools, um eine Verbindung mit Common Data Service herzustellen.

XRM-Tooling stellt Ihnen die folgenden **Windows PowerShell** Cmdlets zur Verfügung, mit denen Sie eine Verbindung zu Common Data Service herstellen und Organisationen abrufen können, auf die der aktuelle Benutzer Zugriff hat: `Get-CrmConnection` und `Get-CrmOrganizations`.  

> [!NOTE]
> [!INCLUDE[cc-d365ce-note-topic](../includes/cc-d365ce-note-topic.md)] [Verwenden Sie PowerShell-Cmdlets für XRM-Tooling, um die Verbindung mit Customer Engagement herzustellen](/dynamics365/customer-engagement/developer/xrm-tooling/use-powershell-cmdlets-xrm-tooling-connect)
  
<a name="Prereq"></a>   

## <a name="prerequisites"></a>Voraussetzungen  
  
-  Um die XRM Tooling-Cmdlets zu verwenden, benötigen Sie **PowerShell Version 3.0** oder höher. Öffnen Sie zur Prüfung der Version ein **PowerShell**-Fenster und führen Sie dann den folgenden Befehl aus: `$Host`.  
  
-  Legen Sie die Ausführungsrichtlinie für die Ausführung der signierten **PowerShell**-Skripts fest. Öffnen Sie hierzu als **Administrator** ein **PowerShell**-Fenster und führen Sie den folgenden Befehl aus: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned`  
  
<a name="register"></a>   

## <a name="acquire-the-microsoftxrmtoolingcrmconnectorpowershell-cmdlet"></a>Rufen Sie das Cmdlet Microsoft.Xrm.Tooling.CrmConnector.PowerShell ab. 

Bevor Sie das Cmdlet **Microsoft.Xrm.Tooling.CrmConnector.PowerShell** verwenden können, müssen Sie es installieren. Das Cmdlet XRM-Tooling PowerShell ist in der PowerShell Gallery [hier](https://www.powershellgallery.com/packages/Microsoft.Xrm.Tooling.CrmConnector.PowerShell) verfügbar. So laden Sie das Cmdlet herunter und installieren es
  
Öffnen Sie PowerShell oder PowerShell ISE im Admin-Modus und führen Sie den folgenden Befehl aus:

   ```powershell
  Install-Module -Name Microsoft.Xrm.Tooling.CrmConnector.PowerShell
   ```  
Wenn Sie das Modul in der Vergangenheit installiert haben, können Sie es mit dem folgenden Befehl aktualisieren:

   ```powershell
  Update-Module -Name Microsoft.Xrm.Tooling.CrmConnector.PowerShell
   ```
    
Sie sind nun bereit, das Cmdlet **Microsoft.Xrm.Tooling.CrmConnector.PowerShell** zu verwenden. Um die von Ihnen registrierten Funktionen aufzulisten, führen Sie den folgenden Befehl im PowerShell-Fenster aus:  
  
   ```powershell
  Get-Help “Crm”  
   ```  


<a name="RetrieveOrgs"></a>   

## <a name="use-the-cmdlet-to-retrieve-organizations-from-common-data-service"></a>Verwenden Sie das Cmdlet, um Organisationen von Common Data Service abzurufen  

Verwenden Sie das `Get-CrmOrganizations`-Cmdlet, um Organisationen abzurufen, auf die Sie Zugriff haben.  
  

1.  Stellen Sie Ihre Anmeldeinformationen bereit, um eine Verbindung mit Ihrer Common Data Service-Instanz herzustellen. Bei Ausführung des folgenden Befehls werden Sie aufgefordert, Ihren Benutzernamen und Ihr Kennwort einzugeben, um eine Verbindung mit der Common Data Service-Instanz herzustellen, und sie wird in der Datei `$Cred` gespeichert.  

  
    ```powershell  
    $Cred = Get-Credential  
    ```  
2. Verwenden Sie den folgenden Befehl, um die Organisationen abzurufen, und speichern Sie die Informationen in der Variable `$CRMOrgs`

    - Wenn Sie sich mit einer Common Data Service-Instanz verbinden:  
  
        ```powershell  
        $CRMOrgs = Get-CrmOrganizations -Credential $Cred -DeploymentRegion NorthAmerica –OnlineType Office365  
        ```  
  
        > [!NOTE]
        > Für den Parameter `DeploymentRegion` sind gültige Werte `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` und `NorthAmerica2`. Für den `OnlineType` Parameter, definieren Sie `Office365`.
  
  
3.  Die angegebenen Anmeldeinformationen werden überprüft, wenn Sie den Befehl in Schritt 2 ausführen. Bei der erfolgreichen Ausführung des Befehls geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE, um die Organisationen anzuzeigen, auf die Sie Zugriff besitzen:  
  
      ```powershell  
      $CRMOrgs  
      ```  
      > [!div class="mx-imgBorder"]
      > ![Common Data Service-Organisationsinformationen](../media/xrmtooling-powershell-1.png "Common Data Service")
  

> [!TIP]
> Sie können die Variable, die verwendet wurde, um die abgerufenen Common Data Service-Organisationen (in diesem Fall `$CRMOrgs`) zu speichern, mit dem `Get-CrmConnection`-Cmdlet verwenden, um eine Verbindung mit Common Data Service herzustellen. Um den Namen der Organisation anzugeben, verwenden Sie den folgenden Befehl: `$CRMOrgs.UniqueName`.  
>   
> Wenn mehr als einen Organisationswert in der `$CRMOrgs`-Variable gespeichert ist, können auf die `nth`-Organisation mithilfe des folgenden Befehls verweisen: `$CRMOrgs[n-1]`. Wenn Sie beispielsweise auf den eindeutigen Namen der zweiten Organisation in der `$CRMOrgs`-Variable verweisen, verwenden Sie den folgenden Befehl: `$CRMOrgs[1].UniqueName`.
  
<a name="ConnecttoCRM"></a>
   
## <a name="use-the-cmdlet-to-connect-to-common-data-service"></a>Verwenden des Cmdlets, um eine Verbindung mit Common Data Service herzustellen  

Verwenden Sie das Cmdlet `Get-CrmConnection`, um eine Verbindung mit einer Common Data Service-Instanz herzustellen Mit dem Cmdlet können Sie entweder das allgemeine Anmeldungssteuerelement von XRM-Tooling verwenden, um die Anmeldeinformationen anzugeben und eine Verbindung mit Common Data Service herzustellen oder um die Anmeldeinformationen als Inline-Parameter anzugeben. Weitere Informationen: [Verwenden des allgemeinen XRM-Tooling-Anmeldungssteuerelements](use-xrm-tooling-common-login-control-client-applications.md)

> [!IMPORTANT]
> Bevor Sie das Cmdlet `Get-CrmConnection` verwenden, stellen Sie sicher, dass Sie den folgenden Befehl verwenden, um die Verwendung von TLS 1.2 durch PowerShell zur Verbindung mit Ihrer Instanz Common Data Service zu erzwingen.<br/>
> `[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12`<br/>
> Weitere Informationen über die TLS 1.2-Anforderung für Common Data Service Verbindung [Blog Post: Updates zur Common Data Service Verbindungssicherheit ](https://blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/)   
  
### <a name="connect-to-common-data-service-by-using-the-common-login-control"></a>Mit dem allgemeinen Anmeldungssteuerelement eine Verbindung mit Common Data Service herstellen  
  
1.  Wenn Sie das allgemeine Anmeldungssteuerelement verwenden möchten, um die Anmeldeinformationen bei der Herstellung einer Verbindung mit Common Data Service bereitzustellen, verwenden Sie den folgenden Befehl. Die Informationen werden in der `$CRMConn`-Variablen gespeichert, damit Sie sie später verwenden können.  
  
    ```powershell  
    $CRMConn = Get-CrmConnection -InteractiveMode  
    ```  
  
2. Das Dialogfeld **Anmeldesteuerelement** wird angezeigt. Stellen Sie die Anmeldeinformationen bereit, um eine Verbindung mit der Common Data Service-Instanz herzustellen, und klicken Sie auf **Anmelden**.    
  
### <a name="connect-to-common-data-service-by-specifying-credentials-inline"></a>Stellen Sie eine Verbindung mit Common Data Service her, indem Sie die Anmeldeinformationen inline angeben.  
  
1.  Um eine Verbindung mit Common Data Service herzustellen, verwenden Sie die folgenden Befehle. Beachten Sie, dass diese befehle die `$Cred`-Variable verwenden, um die Anmeldeinformationen beim Abrufen der Organisationen zu speichern. Die Verbindungsinformationen werden in der `$CRMConn`-Variablen gespeichert:

     - Wenn Sie sich mit einer Common Data Service-Instanz verbinden, gehen Sie wie folgt vor

        ```powershell  
        $CRMConn = Get-CrmConnection -Credential $Cred -DeploymentRegion <Deployment region name> –OnlineType Office365 –OrganizationName <OrgName>  
        ```
        > [!NOTE]
        > Für den Parameter `DeploymentRegion` sind gültige Werte `NorthAmerica`, `EMEA`, `APAC`, `SouthAmerica`, `Oceania`, `JPN`, `CAN`, `IND` und `NorthAmerica2`. Für den `OnlineType` Parameter, definieren Sie `Office365`. 
  
        > [!NOTE]
        > Für den Parameter `OrganizationName` in allen vorangehenden Befehlen können Sie entweder den eindeutigen Namen der Organisation oder den Anzeigenamens angeben. Sie können auch den eindeutigen Namen der Organisation oder den Anzeigenamen verwenden, den Sie mithilfe des `Get-CrmOrganizations`- Cmdlets erhalten und in der `$CRMOrgs`-Variablen gespeichert haben. So können Sie beispielsweise `$CRMOrgs[x].UniqueName` oder `$CRMOrgs[x].FriendlyName` verwenden.  
  
2.  Die angegebenen Anmeldeinformationen werden überprüft, wenn Sie den befehl  in Schritt 1 ausführen. Bei der erfolgreichen Ausführung des cmdlet geben Sie den folgenden Befehl ein, und drücken Sie die EINGABETASTE, um die Verbindungsinformationen und den Status anzuzeigen:  

      ```powershell  
       $CRMConn  
       ```  

       > [!div class="mx-imgBorder"]
       > ![Common Data Service Verbindungsinformationen und Status](../media/xrm-tooling-powershell-2.png "Common Data Service Verbindungsinformationen und Status") 

  
### <a name="see-also"></a>Siehe auch
  
[Verwenden der XRM Tooling API, um eine Verbindung zu Common Data Service herzustellen](use-crmserviceclient-constructors-connect.md)<br />
[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)<br />
[Blog: PowerShell-Modul für die Ausführung von Datenvorgängen und die Bearbeitung der Benutzer- und Systemeinstellungen in Common Data Service](http://blogs.msdn.com/b/crm/archive/2015/09/25/powershell-module-for-performing-data-operations-and-manipulating-user-and-system-settings-in-crm.aspx)

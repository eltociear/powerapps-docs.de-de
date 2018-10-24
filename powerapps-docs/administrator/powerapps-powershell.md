---
title: PowerShell-Unterstützung (Vorschau) | Microsoft-Dokumentation
description: Hier finden Sie eine Beschreibung der verschiedenen PowerShell-Cmdlets und eine exemplarische Vorgehensweise zu deren Installation und Ausführung.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 08/23/2018
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 0d5d2cee770e03c4e587db0bff624f34395ed92c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42864426"
---
# <a name="powershell-support-for-powerapps-preview"></a>PowerShell-Unterstützung für PowerApps (Vorschau)
Durch die Einführung der Vorschauversion der PowerShell-Cmdlets für App-Ersteller und -Administratoren können Sie viele der Überwachungs- und Verwaltungstasks automatisieren, die auf der [PowerApps-Website](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) oder im [ PowerApps Admin Center](https://admin.powerapps.com) aktuell nur manuell ausgeführt werden können.

## <a name="installation"></a>Installation
So führen Sie die PowerShell-Cmdlets für App-Ersteller aus:

1. Laden Sie die [PowerShell-Skriptdatei](https://go.microsoft.com/fwlink/?linkid=2006349) herunter.

2. Entzippen Sie die Datei in einem Ordner.

3. Öffnen Sie in demselben Ordner als Administrator ein PowerShell-Befehlsfenster.

4. Führen Sie den folgenden PowerShell-Befehl einmalig aus (dies setzt voraus, dass Sie auf dem aktuellen Computer noch nie PowerShell-Befehle ausgeführt haben):

    ```
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Force
    ```

5. Importieren Sie anschließend mit den folgenden Befehle die notwendigen Module:

    ```
    Import-Module .\Microsoft.PowerApps.Administration.PowerShell.psm1 -Force
    Import-Module .\Microsoft.PowerApps.PowerShell.psm1 -Force
    ```

6.  [Aktuell ist ein Problem bekannt](https://powerusers.microsoft.com/t5/Administering-PowerApps/Getting-errors-when-I-try-to-import-the-preview-powerapps/td-p/109036), durch das Sie die PowerShell-Dateien möglicherweise manuell durch den folgenden Befehl zulassen müssen:

    ```
    dir . | Unblock-File
    ```
7. Bevor Sie auf die Befehle zugreifen können, müssen Sie mit dem unten aufgeführten Befehl Ihre Anmeldeinformationen angeben. Diese werden etwa 8 Stunden lang aktualisiert. Anschließend müssen Sie sich erneut anmelden, um die Cmdlets weiter verwenden zu können.

    ```
    # This call will open a prompt to collect the credentials (AAD account & password) that will be used by the commands
    Add-PowerAppsAccount
    ```

    ```
    # Here is how you can pass in credentials (avoiding opening a prompt)
    $pass = ConvertTo-SecureString "password" -AsPlainText -Force
    Add-PowerAppsAccount -Username foo@bar.com -Password $pass
    ```


## <a name="powerapps-cmdlets-for-app-creators-preview"></a>PowerApps-Cmdlets für App-Ersteller (Vorschau)

### <a name="prerequisite"></a>Voraussetzung
Benutzer mit einer gültigen PowerApps-Lizenz können die Vorgänge in diesen Cmdlets ausführen, haben aber nur Zugriff auf Ressourcen wie z.B. Apps und Flows, die für sie erstellt oder freigegeben wurden.

### <a name="cmdlet-list"></a>Cmdlet-Liste
> [!NOTE]
> Wir haben einige der Namen der Cmdlets-Funktionen in der neuesten Version aktualisiert, um die entsprechenden Präfixe hinzuzufügen, um so Konflikte zu vermeiden. Eine Übersicht über die Änderungen finden Sie in der Tabelle unten.

| Zweck | Cmdlet |
| --- | --- |
| Lesen von Umgebungen | Get-PowerAppEnvironment *(bisher Get-PowerAppsEnvironment)* <br> Get-FlowEnvironment
| Lesen, Aktualisieren und Löschen einer Canvas-App | Get-PowerApp *(zuvor Get-App)* <br> Remove-PowerApp *(zuvor Remove-App)* <br> Publish-PowerApp *(zuvor Publish-App)* <br> Set-AppDisplayName *(zuvor Set-PowerAppDisplayName)*<br> Get-PowerAppVersion *(zuvor Get-AppVersion)* <br> Restore-PowerAppVersion *(zuvor Restore-AppVersion)*
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-PowerAppRoleAssignment *(bisher Get-AppRoleAssignment)* <br> Set-PowerAppRoleAssignment *(bisher Set-AppRoleAssignment)* <br> Remove-PowerAppRoleAssignment *(bisher Remove-AppRoleAssignment)*
| Lesen, Aktualisieren und Löschen eines Flows | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow
| Lesen, Aktualisieren und Löschen von Berechtigungen für einen Flow | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole
| Lesen und Reagieren auf Genehmigungen für Flows | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest
| Lesen und Löschen von Verbindungen | Get-PowerAppConnection *(bisher Get-Connection)* <br> Remove-PowerAppConnection *(bisher Remove-Connection)*
| Lesen, Aktualisieren und Löschen von Berechtigungen für Verbindungen | Get-PowerAppConnectionRoleAssignment *(bisher Get-ConnectionRoleAssignment)* <br> Set-PowerAppConnectionRoleAssignment *(bisher Set-ConnectionRoleAssignment)* <br> Remove-PowerAppConnectionRoleAssignment *(bisher Remove-ConnectionRoleAssignment)*
| Lesen und Löschen von Connectors | Get-PowerAppConnector *(bisher Get-Connector)* <br> Remove-PowerAppConnector *(bisher Remove-Connector)*
| Lesen, Aktualisieren und Löschen von Berechtigungen für benutzerdefinierte Connectors | Get-PowerAppConnectorRoleAssignment *(bisher Get-ConnectorRoleAssignment)* <br> Set-PowerAppConnectorRoleAssignment *(bisher Set-ConnectorRoleAssignment)* <br> Remove-PowerAppConnectorRoleAssignment *(bisher Remove-ConnectorRoleAssignment)*


> [!NOTE]
> Mit den folgenden Befehle können Sie die Syntax- und Ansichtsbeispiele für die einzelnen Cmdlets besser nachvollziehen:
>```
>Get-Help Get-PowerAppEnvironment
>Get-Help Get-PowerAppEnvironment -Examples
>Get-Help Get-PowerAppEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>PowerApps-Cmdlets für Administratoren (Vorschau)

### <a name="prerequisite"></a>Voraussetzung
Zur Ausführung der Verwaltungsvorgänge in den Cmdlets für Administratoren benötigen Sie Folgendes:

* eine kostenpflichtige PowerApps Plan 2-Lizenz oder eine PowerApps Plan 2-Testlizenz. Sie können sich unter [http://web.powerapps.com/trial](http://web.powerapps.com/trial) für eine 30-tägige Testlizenz registrieren. Testlizenzen können verlängert werden, wenn sie abgelaufen sind.

* Die Berechtigungen [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), wenn Sie die Ressourcen eines anderen Benutzers durchsuchen müssen. (Beachten Sie, das Umgebungsadministratoren nur Zugriff auf die Umgebungen und Umgebungsressourcen haben, für die sie über die Berechtigungen verfügen.)

### <a name="cmdlet-list"></a>Cmdlet-Liste
> [!NOTE]
> Wir haben einige der Namen der Cmdlets-Funktionen in der neuesten Version aktualisiert, um die entsprechenden Präfixe hinzuzufügen, um so Konflikte zu vermeiden. Eine Übersicht über die Änderungen finden Sie in der Tabelle unten.

| Zweck | Cmdlets
| --- | ---
| Lesen, Aktualisieren und Löschen von Umgebungen & Common Data Service für App-Datenbanken | New-AdminPowerAppEnvironment **\*Neu\*** <br> Set-AdminPowerAppEnvironmentDisplayName **\*Neu\*** <br> Get-AdminPowerAppEnvironment *(bisher Get-AdminEnvironment)* <br> Remove-AdminPowerAppEnvironment *(bisher Remove-AdminEnvironment)* <br> New-AdminPowerAppCdsDatabase **\*Neu\*** <br> Get-AdminPowerAppCdsDatabaseLanguages **\*Neu\*** <br> Get-AdminPowerAppCdsDatabaseCurrencies **\*Neu\*** <br> Get-AdminPowerAppEnvironmentLocations **\*Neu\***
| Lesen, Aktualisieren und Löschen von Berechtigungen für Umgebungen <br><br> *Diese Cmdlets können nur jetzt in Umgebungen ausgeführt werden, die nicht über eine Common Data Service für App-Datenbank verfügen.* | Get-AdminPowerAppEnvironmentRoleAssignment *(bisher Get-AdminEnvironmentRoleAssignment)* <br> Set-AdminPowerAppEnvironmentRoleAssignment *(bisher Set-AdminEnvironmentRoleAssignment)* <br> Remove-AdminPowerAppEnvironmentRoleAssignment *(bisher Remove-AdminEnvironmentRoleAssignment)*
| Lesen, Aktualisieren und Löschen von Canvas-Apps | Get-AdminPowerApp *(bisher Get-AdminApp)* <br> Remove-AdminPowerApp *(bisher Remove-AdminApp)* <br> Get-AdminPowerAppConnectionReferences **\*Neu\*** <br> Set-AdminPowerAppAsFeatured **\*Neu\*** <br> Clear-AdminPowerAppAsFeatured **\*Neu\*** <br> Set-AdminPowerAppAsHero **\*Neu\*** <br> Clear-AdminPowerAppAsHero **\*Neu\*** <br> Set-AdminPowerAppApisToBypassConsent **\*Neu\*** <br> Clear-AdminPowerAppApisToBypassConsent **\*Neu\***
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-AdminPowerAppRoleAssignment *(bisher Get-AdminAppRoleAssignment)* <br> Remove-AdminPowerAppRoleAssignment *(bisher Remove-AdminAppRoleAssignment)* <br> Set-AdminPowerAppRoleAssignment *(bisher Set-AdminAppRoleAssignment)* <br> Set-AdminPowerAppOwner *(bisher Set-AdminAppOwner)*
| Lesen, Aktualisieren und Löschen von Flows | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow <br> Remove-AdminFlowApprovals **\*Neu\***
| Lesen, Aktualisieren und Löschen von Berechtigungen für einen Flow | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole
| Lesen und Löschen von Verbindungen | Get-AdminPowerAppConnection *(bisher Get-AdminConnection)* <br> Remove-AdminPowerAppConnection *(bisher Remove-AdminConnection)*
| Lesen, Aktualisieren und Löschen von Berechtigungen für Verbindungen | Get-AdminPowerAppConnectionRoleAssignment *(bisher Get-AdminConnectionRoleAssignment)* <br> Set-AdminPowerAppEnvironmentConnectionRoleAssignment *(bisher Set-AdminConnectionRoleAssignment)* <br> Remove-AdminPowerAppConnectionRoleAssignment *(bisher Remove-AdminConnectionRoleAssignment)*
| Lesen und Löschen von benutzerdefinierten Connectors | Get-AdminPowerAppConnector *(bisher Get-AdminConnector)* <br> Remove-AdminPowerAppConnector *(bisher Remove-AdminConnector)*
| Lesen, Aktualisieren und Löschen von Berechtigungen für benutzerdefinierte Connectors | Get-AdminPowerAppConnectorRoleAssignment *(bisher Get-AdminConnectorRoleAssignment)*<br> Set-AdminPowerAppConnectorRoleAssignment *(bisher Set-AdminConnectorRoleAssignment)* <br> Remove-AdminPowerAppConnectorRoleAssignment *(bisher Remove-AdminConnectorRoleAssignment)*
| Lesen der PowerApps-Benutzereinstellungen, Benutzeranwendungseinstellungen und Benachrichtigungen | Get-AdminPowerAppsUserDetails
| Lesen und Löschen der Microsoft Flow-Einstellungen eines Benutzers, die für diesen zwar nicht sichtbar sind, aber die Ausführung von Flow unterstützen | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails
| Erstellen, Lesen, Aktualisieren und Löschen von Richtlinien zur Verhinderung von Datenverlust für Ihre Organisation | Get-AdminDlpPolicy *(bisher Get-AdminApiPolicy)* <br> Add-AdminDlpPolicy *(bisher Add-AdminApiPolicy)* <br> Remove-AdminDlpPolicy *(bisher Remove-AdminApiPolicy)* <br> Set-AdminDlpPolicy *(bisher Set-AdminApiPolicy)* <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup

> [!NOTE]
> Mit den folgenden Befehle können Sie die Syntax- und Ansichtsbeispiele für die einzelnen Cmdlets besser nachvollziehen:
>```
>Get-Help Get-AdminPowerAppEnvironment
>Get-Help Get-AdminPowerAppEnvironment -Examples
>Get-Help Get-AdminPowerAppEnvironment -Detailed
>```

## <a name="version-history"></a>Versionsverlauf
| Version | Datum | Aktualisierungen |
| --- | --- | --- |
| 1.0 | 23.04.2018 | <ol> <li> Erster Start der PowerApps-Cmdlets für App-Ersteller (Vorschau), einschließlich Verwaltungs-Cmdlets für Umgebungen, Apps, Flows, Flow-Genehmigungen, Verbindungen und benutzerdefinierte Connectors </li> <li> Erster Start der PowerApps-Cmdlets für Administratoren (Vorschau) einschließlich administrative Cmdlets für Umgebungen, Apps und Flows </li></ol>|
| 2.0 | 24.05.2018 | <ol> <li> Kleinere Fehlerbehebungen in den beiden Cmdlets für App-Ersteller und Administratoren </li> <li> Die folgenden neuen administrativen Cmdlets wurden hinzugefügt: <br> Get-AdminConnection <br> Remove-AdminConnection <br> Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br>Remove-AdminConnectionRoleAssignment <br>Get-AdminConnector  <br>Remove-AdminConnector <br>Set-AdminConnectorRoleAssignment  <br>Get-AdminConnectorRoleAssignment  <br>Remove-AdminConnectorRoleAssignment <br>Get-AdminPowerAppsUserDetails <br>Get-AdminFlowUserDetails <br>Remove-AdminFlowUserDetails <br>Get-AdminApiPolicy  <br>Add-AdminApiPolicy <br>Remove-AdminApiPolicy <br>Set-AdminApiPolicy <br>Add-ConnectorToBusinessDataGroup  <br>Remove-ConnectorFromBusinessDataGroup </li> </ol>
| 3.0 | 30.07.2018 | <ol> <li> Anmeldeinformationen können nun Add-PowerAppsAccount hinzugefügt werden (zur Aktivierung von wiederkehrendem Scripting). </li> <li>  Kleinere Fehlerbehebungen in den Cmdlets für App-Ersteller und Administratoren </li> <li> Präfix „PowerApp“ oder „Flow“ wurde jedem Cmdlet für App-Ersteller hinzugefügt. </li> <li>  Präfix „AdminPowerApp“ oder „AdminFlow“ wurde jedem Cmdlet für Administratoren hinzugefügt. </li> <li> Die folgenden neuen administrativen Cmdlets wurden hinzugefügt: <br> New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent <br> Remove-AdminFlowApprovals </li></ol>
| 4.0 | 15.08.2018 | Ein optionaler Parameter wurde New-AdminPowerAppCdsDatabase hinzugefügt, um die Funktion standardmäßig zu synchronisieren (d.h. keine Rückgaben, solange die Datenbank nicht erfolgreich bereitgestellt wurde)
| 5.0 | 24.08.2018 | Das dadurch verursachte Problem, dass Flow-Admin-Cmdlets abhängig von ihren Sicherheitseinstellungen in einigen Fällen keine Daten zurückgegeben haben, wurde behoben.

## <a name="questions"></a>Fragen?

Wenn Sie Kommentare, Vorschläge oder Fragen haben, können Sie diese im [Community Board zur Verwaltung von PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps) veröffentlichen.

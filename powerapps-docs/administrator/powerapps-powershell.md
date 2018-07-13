---
title: PowerShell-Unterstützung (Vorschau) | Microsoft-Dokumentation
description: Hier finden Sie eine Beschreibung der verschiedenen PowerShell-Cmdlets und eine exemplarische Vorgehensweise zu deren Installation und Ausführung.
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 2cb1e1b83cffee2ccea0a4d4b563de44aaa3e68c
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37896188"
---
# <a name="powershell-support-for-powerapps-preview"></a>PowerShell-Unterstützung für PowerApps (Vorschau)
Durch die Einführung der Vorschauversion der PowerShell-Cmdlets für App-Ersteller und -Administratoren können Sie viele der Überwachungs- und Verwaltungstasks automatisieren, die auf der [PowerApps-Website](https://web.powerapps.com) oder im [ PowerApps Admin Center](https://admin.powerapps.com) aktuell nur manuell ausgeführt werden können.

## <a name="installation"></a>Installation
So führen Sie die PowerShell-Cmdlets für App-Ersteller aus:

1. Laden Sie die [PowerShell-Skriptdatei](https://go.microsoft.com/fwlink/?linkid=872358) herunter.

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
    Add-PowerAppsAccount
    ```


## <a name="powerapps-cmdlets-for-app-creators-preview"></a>PowerApps-Cmdlets für App-Ersteller (Vorschau)

### <a name="prerequisite"></a>Voraussetzung
Benutzer mit einer gültigen PowerApps-Lizenz können die Vorgänge in diesen Cmdlets ausführen, haben aber nur Zugriff auf Ressourcen wie z.B. Apps und Flows, die für sie erstellt oder freigegeben wurden.

### <a name="cmdlet-list"></a>Cmdlet-Liste

| Zweck | Cmdlet |
| --- | --- |
| Lesen von Umgebungen | Get-PowerAppsEnvironment <br> Get-FlowEnvironment
| Lesen, Aktualisieren und Löschen einer Canvas-App | Get-App <br> Remove-App <br> Publish-App <br> Set-AppDisplayName <br> Get-AppVersion <br> Restore-AppVersion
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-AppRoleAssignment <br> Set-AppRoleAssignment <br> Remove-AppRoleAssignment
| Lesen, Aktualisieren und Löschen eines Flows | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow
| Lesen, Aktualisieren und Löschen von Berechtigungen für einen Flow | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole
| Lesen und Reagieren auf Genehmigungen für Flows | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest
| Lesen und Löschen von Verbindungen | Get-Connection <br> Remove-Connection
| Lesen, Aktualisieren und Löschen von Berechtigungen für Verbindungen | Get-ConnectionRoleAssignment <br> Set-ConnectionRoleAssignment <br> Remove-ConnectionRoleAssignment
| Lesen und Löschen von Connectors | Get-Connector <br> Remove-Connector
| Lesen, Aktualisieren und Löschen von Berechtigungen für benutzerdefinierte Connectors | Get-ConnectorRoleAssignment <br> Set-ConnectorRoleAssignment <br> Remove-ConnectorRoleAssignment


> [!NOTE]
> Mit den folgenden Befehle können Sie die Syntax- und Ansichtsbeispiele für die einzelnen Cmdlets besser nachvollziehen:
>```
>Get-Help Get-PowerAppsEnvironment
>Get-Help Get-PowerAppsEnvironment -Examples
>Get-Help Get-PowerAppsEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>PowerApps-Cmdlets für Administratoren (Vorschau)

### <a name="prerequisite"></a>Voraussetzung
Zur Ausführung der Verwaltungsvorgänge in den Cmdlets für Administratoren benötigen Sie Folgendes:

* eine kostenpflichtige PowerApps Plan 2-Lizenz oder eine PowerApps Plan 2-Testlizenz. Sie können sich unter [http://web.powerapps.com/trial](http://web.powerapps.com/trial) für eine 30-tägige Testlizenz registrieren. Testlizenzen können verlängert werden, wenn sie abgelaufen sind.

* Die Berechtigungen [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), wenn Sie die Ressourcen eines anderen Benutzers durchsuchen müssen. (Beachten Sie, das Umgebungsadministratoren nur Zugriff auf die Umgebungen und Umgebungsressourcen haben, für die sie über die Berechtigungen verfügen.)

### <a name="cmdlet-list"></a>Cmdlet-Liste

| Zweck | Cmdlets
| --- | ---
| Lesen und Löschen von Umgebungen | Get-AdminEnvironment <br> Remove-AdminEnvironment
| Lesen, Aktualisieren und Löschen von Berechtigungen für Umgebungen <br><br> *Diese Cmdlets können nur in Umgebungen ausgeführt werden, die nicht über eine Common Data Service for Apps-Datenbank verfügen.* | Get-AdminEnvironmentRoleAssignment <br> Set-AdminEnvironmentRoleAssignment <br> Remove-AdminEnvironmentRoleAssignment
| Lesen und Entfernen von Canvas-Apps | Get-AdminApp <br> Remove-AdminApp
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-AdminAppRoleAssignment <br> Remove-AdminAppRoleAssignment <br> Set-AdminAppRoleAssignment <br> Set-AdminAppOwner
| Lesen, Aktualisieren und Löschen von Flows | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow
| Lesen, Aktualisieren und Löschen von Berechtigungen für einen Flow | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole
| Lesen und Löschen von Verbindungen | Get-AdminConnection <br> Remove-AdminConnection
| Lesen, Aktualisieren und Löschen von Berechtigungen für Verbindungen | Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br> Remove-AdminConnectionRoleAssignment
| Lesen und Löschen von benutzerdefinierten Connectors | Get-AdminConnector <br> Remove-AdminConnector
| Lesen, Aktualisieren und Löschen von Berechtigungen für benutzerdefinierte Connectors | Get-AdminConnectorRoleAssignment <br> Set-AdminConnectorRoleAssignment <br> Remove-AdminConnectorRoleAssignment
| Lesen der PowerApps-Benutzereinstellungen, Benutzeranwendungseinstellungen und Benachrichtigungen | Get-AdminPowerAppsUserDetails
| Lesen und Löschen der Microsoft Flow-Einstellungen eines Benutzers, die für diesen zwar nicht sichtbar sind, aber die Ausführung von Flow unterstützen | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails
| Erstellen, Lesen, Aktualisieren und Löschen von Richtlinien zur Verhinderung von Datenverlust für Ihre Organisation | Get-AdminApiPolicy <br> Add-AdminApiPolicy <br> Remove-AdminApiPolicy <br> Set-AdminApiPolicy <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup

> [!NOTE]
> Mit den folgenden Befehle können Sie die Syntax- und Ansichtsbeispiele für die einzelnen Cmdlets besser nachvollziehen:
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>Fragen?

Wenn Sie Kommentare, Vorschläge oder Fragen haben, können Sie diese im [Community Board zur Verwaltung von PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps) veröffentlichen.

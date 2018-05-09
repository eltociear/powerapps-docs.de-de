---
title: PowerShell-Unterstützung | Microsoft-Dokumentation
description: Beschreibung der verschiedenen PowerShell-Cmdlets und eine Schritt-für-Schritt-Anleitung zu deren Installation und Ausführung
services: powerapps
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms-topic: article
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/23/2018
ms.author: jamesol
ms.openlocfilehash: 69508b2127c5c919db4a334045c6eed3bb9374af
ms.sourcegitcommit: 0a781b50a8551f2e61c22725ef1c43ba4fdf752a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
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

6. Bevor Sie auf die Befehle zugreifen können, müssen Sie mit dem unten aufgeführten Befehl Ihre Anmeldeinformationen angeben. Diese werden etwa 8 Stunden lang aktualisiert. Anschließend müssen Sie sich erneut anmelden, um die Cmdlets weiter verwenden zu können.

    ```
    Add-PowerAppsAccount
    ```

7.  [Aktuell ist ein Problem bekannt](https://powerusers.microsoft.com/t5/Administering-PowerApps/Getting-errors-when-I-try-to-import-the-preview-powerapps/td-p/109036), durch das Sie die PowerShell-Dateien möglicherweise manuell durch den folgenden Befehl zulassen müssen:

    ```
    dir . | Unblock-File
    ```

## <a name="powerapps-cmdlets-for-app-makers-preview"></a>PowerApps-Cmdlets für App-Ersteller (Vorschau)

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

* die Berechtigungen [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), wenn Sie die Ressourcen eines anderen Benutzers durchsuchen müssen. (Beachten Sie, das Umgebungsadministratoren nur Zugriff auf die Umgebungen und Umgebungsressourcen haben, für die sie über die Berechtigungen verfügen.)

### <a name="cmdlet-list"></a>Cmdlet-Liste
| Zweck | Cmdlets
| --- | ---
| Lesen und Löschen von Umgebungen | Get-AdminEnvironment <br> Remove-AdminEnvironment
| Lesen, Aktualisieren und Löschen von Berechtigungen für Umgebungen <br><br> *Diese Cmdlets können nur in Umgebungen ausgeführt werden, die nicht über eine Common Data Service for Apps-Datenbank verfügen.* | Get-AdminEnvironmentRoleAssignment <br> Set-AdminEnvironmentRoleAssignment <br> Remove-AdminEnvironmentRoleAssignment
| Lesen und Entfernen von Canvas-Apps | Get-AdminApp <br> Remove-AdminApp
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-AdminAppRoleAssignment <br> Remove-AdminAppRoleAssignment <br> Set-AdminAppRoleAssignment <br> Set-AdminAppOwner
| Lesen, Aktualisieren und Löschen von Flows | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow  <br> Remove-AdminFlowOwnerRole

> [!NOTE]
> Mit den folgenden Befehle können Sie die Syntax- und Ansichtsbeispiele für die einzelnen Cmdlets besser nachvollziehen:
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>Fragen?

Wenn Sie Kommentare, Vorschläge oder Fragen haben, können Sie diese im [Community Board zur Verwaltung von PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps) veröffentlichen.

---
title: PowerShell-Unterstützung | Microsoft-Dokumentation
description: PowerShell-Unterstützung für PowerApps
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
ms.date: 04/17/2018
ms.author: jamesol
ms.openlocfilehash: 274d34ca56cc993ec26fa4f4ced77bb2aba9985f
ms.sourcegitcommit: e3a2819c14ad67cc4ca6640b9064550d0f553d8f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="powershell-support-for-powerapps-preview"></a>PowerShell-Unterstützung für PowerApps (Vorschau)

Beim Starten der Vorschau der PowerShell-Cmdlets für App-Ersteller und -Administratoren können Sie viele der Überwachungs- und Verwaltungstasks automatisieren, die auf der [PowerApps-Website](https://web.powerapps.com) oder im [ PowerApps Admin Center](https://admin.powerapps.com) aktuell nur manuell ausgeführt werden können.

## <a name="installation"></a>Installation
Zum Ausführen der PowerShell-Cmdlets für App-Ersteller müssen Sie zunächst die folgenden Schritte ausführen:

1. Laden Sie [hier](https://go.microsoft.com/fwlink/?linkid=872358) die PowerShell-Scripts herunter

2. Entzippen Sie die Datei in einen Ordner

3. Öffnen Sie in demselben Ordner als Administrator ein PowerShell-Befehlsfenster

4. Führen Sie anschließend folgenden einmaligen PowerShell-Befehl aus (dies setzt voraus, dass Sie auf dem aktuellen Computer noch nie PowerShell-Befehle ausgeführt haben):

    ```
    Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force
    ```

5. Importieren Sie anschließend mit den folgenden Befehle die notwendigen Module:

    ```
    Import-Module .\Microsoft.PowerApps.Administration.PowerShell.psm1 -Force
    Import-Module .\Microsoft.PowerApps.PowerShell.psm1 -Force
    ```

6. Bevor Sie auf die Befehle zugreifen können, müssen Sie schließlich mit folgendem Befehl Ihre Anmeldeinformationen angeben. Diese Anmeldeinformationen werden etwa 8 Stunden lang aktualisiert. Anschließend müssen Sie sich erneut anmelden, um die Cmdlets weiter verwenden zu können.

    ```
    Add-PowerAppsAccount
    ```

## <a name="powerapps-cmdlets-for-app-makers-preview"></a>PowerApps-Cmdlets für App-Ersteller (Vorschau)

### <a name="prerequisite"></a>Voraussetzung
Alle Benutzer mit einer gültigen PowerApps-Lizenz können die Operationen in diesen Cmdlets ausführen. Sie haben jedoch nur Zugriff auf die Ressourcen (z.B. Apps, Flows usw.), die erstellt oder für sie freigegeben wurden.

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
> Die folgenden Befehle dienen dazu, Syntax- und Ansichtsbeispiele für die einzelnen Cmdlets nachvollziehen zu können:
>```
>Get-Help Get-PowerAppsEnvironment
>Get-Help Get-PowerAppsEnvironment -Examples
>Get-Help Get-PowerAppsEnvironment -Detailed
>```

## <a name="powerapps-cmdlets-for-administrators-preview"></a>PowerApps-Cmdlets für Administratoren (Vorschau)

### <a name="prerequisite"></a>Voraussetzung
Sie benötigen ein Konto mit den folgenden Berechtigungen, um die Verwaltungsvorgänge in den Cmdlets für Administratoren ausführen zu können:

- Eine kostenpflichtige PowerApps Plan 2-Lizenz oder eine PowerApps Plan 2-Testlizenz. Sie können sich unter [http://web.powerapps.com/trial](http://web.powerapps.com/trial) für eine 30-tägige Testlizenz registrieren. Testlizenzen können verlängert werden, wenn sie abgelaufen sind.

- Wenn Sie die Ressourcen eines anderen Benutzers durchsuchen müssen, sind darüber hinaus Berechtigungen für den [globalen Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder den [globalen Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) erforderlich. Andernfalls haben Sie nur Zugriff auf die Umgebungen und Umgebungsressourcen, bei denen Sie über Berechtigungen für den Umgebungsadministrator verfügen.

### <a name="cmdlet-list"></a>Cmdlet-Liste
| Zweck | Cmdlets
| --- | ---
| Lesen und Löschen von Umgebungen | Get-AdminEnvironment <br> Remove-AdminEnvironment
| Lesen, Aktualisieren und Löschen von Berechtigungen für Umgebungen <br><br> *Diese Cmdlets können nur in Umgebungen ausgeführt werden, die nicht über eine Common Data Service für Apps-Datenbank verfügen.* | Get-AdminEnvironmentRoleAssignment <br> Set-AdminEnvironmentRoleAssignment <br> Remove-AdminEnvironmentRoleAssignment
| Lesen und Entfernen von Canvas-Apps | Get-AdminApp <br> Remove-AdminApp
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-AdminAppRoleAssignment <br> Remove-AdminAppRoleAssignment <br> Set-AdminAppRoleAssignment <br> Set-AdminAppOwner
| Lesen, Aktualisieren und Löschen von Flows | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow  <br> Remove-AdminFlowOwnerRole

> [!NOTE]
> Die folgenden Befehle dienen dazu, Syntax- und Ansichtsbeispiele für die einzelnen Cmdlets nachvollziehen zu können:
>```
>Get-Help Get-AdminEnvironment
>Get-Help Get-AdminEnvironment -Examples
>Get-Help Get-AdminEnvironment -Detailed
>```

## <a name="questions"></a>Fragen?

Wenn Sie Kommentare, Vorschläge oder Fragen haben, senden Sie diese an das [PowerApps Community Board für die Verwaltung](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps).

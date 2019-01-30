---
title: PowerShell-Unterstützung (Vorschau) | Microsoft-Dokumentation
description: Hier finden Sie eine Beschreibung der verschiedenen PowerShell-Cmdlets und eine exemplarische Vorgehensweise zu deren Installation und Ausführung.
author: jamesol-msft
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: reference
ms.date: 01/18/2019
ms.author: jamesol
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 0152296adbe01abae2b831576c312a43d1f2a2b8
ms.sourcegitcommit: 3ce7c17f90f87756a072210c8abfbd93733a6d4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397765"
---
# <a name="powershell-support-for-powerapps-preview"></a>PowerShell-Unterstützung für PowerApps (Vorschau)
Durch die Einführung der Vorschauversion der PowerShell-Cmdlets für App-Ersteller und -Administratoren können Sie viele der Überwachungs- und Verwaltungstasks automatisieren, die auf der [PowerApps-Website](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) oder im [ PowerApps Admin Center](https://admin.powerapps.com) aktuell nur manuell ausgeführt werden können.

## <a name="cmdlets"></a>Cmdlets
[Cmdlets](https://docs.microsoft.com/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet) sind Funktionen, die in der PowerShell-Skriptsprache geschrieben sind und in der Windows PowerShell-Umgebung Befehle ausführen. Mithilfe dieser PowerApps-Cmdlets können Sie mit Ihrer Plattform für Geschäftsanwendungen interagieren, ohne das Verwaltungsportal in einem Webbrowser öffnen zu müssen. Diese Cmdlets können mit anderen PowerShell-Funktionen zu komplexen Skripts kombiniert werden, mit denen Sie Ihren Workflow optimieren können. Beachten Sie, dass Sie die Cmdlets auch dann verwenden können, wenn Sie kein Administrator im Mandant sind. In diesem Fall können Sie jedoch nur auf die Ressourcen zugreifen, die Sie besitzen. Cmdlets, die mit dem Begriff „Admin“ beginnen, sind für Benutzerkonten mit Administratorrechten konzipiert.

Cmdlets sind im PowerShell-Katalog als zwei separate Module verfügbar: 
- [Administrator](https://www.powershellgallery.com/packages/Microsoft.PowerApps.Administration.PowerShell/2.0.1)
- [Ersteller](https://www.powershellgallery.com/packages/Microsoft.PowerApps.PowerShell/1.0.1) 

## <a name="installation"></a>Installation
So führen Sie die PowerShell-Cmdlets für App-Ersteller aus:

1. Führen Sie PowerShell als Administrator aus.

   > [!div class="mx-imgBorder"] 
   > ![PowerShell als Administrator ausführen](media/open-powershell-as-admin75.png "PowerShell als Administrator ausführen")

2. Importieren Sie anschließend mit den folgenden Befehle die notwendigen Module:

    ```
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    ```
3. Wenn Sie aufgefordert werden, der Änderung des Repositorywerts *InstallationPolicy* zuzustimmen, geben Sie „A“ ein, um „[A] Ja für alle Module“ anzunehmen, und drücken Sie für jedes Modul die **EINGABETASTE**.

   ![Wert „InstallationPolicy“ annehmen](media/accept-installationpolicy-value75.png "Wert „InstallationPolicy“ annehmen")

4. Bevor Sie auf die Befehle zugreifen können, haben Sie mit dem folgenden Befehl die Möglichkeit, Ihre Anmeldeinformationen anzugeben. Diese werden etwa 8 Stunden lang aktualisiert. Anschließend müssen Sie sich erneut anmelden, um die Cmdlets weiter verwenden zu können.

    ```
    # This call opens prompt to collect credentials (Azure Active Directory account and password) used by the commands 
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

### <a name="cmdlet-list---maker-cmdlets"></a>Cmdlet-Liste: Cmdlets für Ersteller
> [!NOTE]
> Wir haben einige der Namen der Cmdlets-Funktionen in der neuesten Version aktualisiert, um die entsprechenden Präfixe hinzuzufügen, um so Konflikte zu vermeiden. Eine Übersicht über die Änderungen finden Sie in der Tabelle unten.

| Zweck | Cmdlet |
| --- | --- |
| Lesen von Umgebungen | Get-PowerAppEnvironment *(bisher Get-PowerAppsEnvironment)* <br> Get-FlowEnvironment |
| Lesen, Aktualisieren und Löschen einer Canvas-App | Get-PowerApp *(zuvor Get-App)* <br> Remove-PowerApp *(zuvor Remove-App)* <br> Publish-PowerApp *(zuvor Publish-App)* <br> Set-AppDisplayName *(zuvor Set-PowerAppDisplayName)*<br> Get-PowerAppVersion *(zuvor Get-AppVersion)* <br> Restore-PowerAppVersion *(zuvor Restore-AppVersion)* |
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-PowerAppRoleAssignment *(bisher Get-AppRoleAssignment)* <br> Set-PowerAppRoleAssignment *(bisher Set-AppRoleAssignment)* <br> Remove-PowerAppRoleAssignment *(bisher Remove-AppRoleAssignment)* |
| Lesen, Aktualisieren und Löschen eines Flows | Get-Flow <br> Get-FlowRun <br> Enable-Flow <br> Disable-Flow <br> Remove-Flow |
| Lesen, Aktualisieren und Löschen von Berechtigungen für einen Flow | Get-FlowOwnerRole <br> Set-FlowOwnerRole <br> Remove-FlowOwnerRole |
| Lesen und Reagieren auf Genehmigungen für Flows | Get-FlowApprovalRequest <br> Get-FlowApproval <br> RespondTo-FlowApprovalRequest |
| Lesen und Löschen von Verbindungen | Get-PowerAppConnection *(bisher Get-Connection)* <br> Remove-PowerAppConnection *(bisher Remove-Connection)* |
| Lesen, Aktualisieren und Löschen von Berechtigungen für Verbindungen | Get-PowerAppConnectionRoleAssignment *(bisher Get-ConnectionRoleAssignment)* <br> Set-PowerAppConnectionRoleAssignment *(bisher Set-ConnectionRoleAssignment)* <br> Remove-PowerAppConnectionRoleAssignment *(bisher Remove-ConnectionRoleAssignment)* |
| Lesen und Löschen von Connectors | Get-PowerAppConnector *(bisher Get-Connector)* <br> Remove-PowerAppConnector *(bisher Remove-Connector)* |
| Lesen, Aktualisieren und Löschen von Berechtigungen für benutzerdefinierte Connectors | Get-PowerAppConnectorRoleAssignment *(bisher Get-ConnectorRoleAssignment)* <br> Set-PowerAppConnectorRoleAssignment *(bisher Set-ConnectorRoleAssignment)* <br> Remove-PowerAppConnectorRoleAssignment *(bisher Remove-ConnectorRoleAssignment)* |

## <a name="powerapps-cmdlets-for-administrators-preview"></a>PowerApps-Cmdlets für Administratoren (Vorschau)

### <a name="prerequisite"></a>Voraussetzung
Zur Ausführung der Verwaltungsvorgänge in den Cmdlets für Administratoren benötigen Sie Folgendes:

* eine kostenpflichtige PowerApps Plan 2-Lizenz oder eine PowerApps Plan 2-Testlizenz. Sie können sich unter [http://web.powerapps.com/trial](http://web.powerapps.com/trial) für eine 30-tägige Testlizenz registrieren. Testlizenzen können verlängert werden, wenn sie abgelaufen sind.

* Die Berechtigungen [globaler Office 365-Administrator](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504) oder [globaler Azure Active Directory-Administrator](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), wenn Sie die Ressourcen eines anderen Benutzers durchsuchen müssen. (Beachten Sie, das Umgebungsadministratoren nur Zugriff auf die Umgebungen und Umgebungsressourcen haben, für die sie über die Berechtigungen verfügen.)

### <a name="cmdlet-list---admin-cmdlets"></a>Cmdlet-Liste: Cmdlets für Administratoren

| Zweck | Cmdlets
| --- | ---
| Lesen, Aktualisieren und Löschen von Umgebungen & Common Data Service für App-Datenbanken | New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> Get-AdminPowerAppEnvironment *(bisher Get-AdminEnvironment)* <br> Remove-AdminPowerAppEnvironment *(bisher Remove-AdminEnvironment)* <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations |
| Löschen der CDS-Datenbank | Remove-LegacyCDSDatabase **\*Neu\*** | 
| Lesen, Aktualisieren und Löschen von Berechtigungen für Umgebungen <br><br> *Diese Cmdlets können nur jetzt in Umgebungen ausgeführt werden, die nicht über eine Common Data Service für App-Datenbank verfügen.* | Get-AdminPowerAppEnvironmentRoleAssignment *(bisher Get-AdminEnvironmentRoleAssignment)* <br> Set-AdminPowerAppEnvironmentRoleAssignment *(bisher Set-AdminEnvironmentRoleAssignment)* <br> Remove-AdminPowerAppEnvironmentRoleAssignment *(bisher Remove-AdminEnvironmentRoleAssignment)* |
| Lesen, Aktualisieren und Löschen von Canvas-Apps | Get-AdminPowerApp *(bisher Get-AdminApp)* <br> Remove-AdminPowerApp *(bisher Remove-AdminApp)* <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent |
| Lesen, Aktualisieren und Löschen von Berechtigungen für eine Canvas-App | Get-AdminPowerAppRoleAssignment *(bisher Get-AdminAppRoleAssignment)* <br> Remove-AdminPowerAppRoleAssignment *(bisher Remove-AdminAppRoleAssignment)* <br> Set-AdminPowerAppRoleAssignment *(bisher Set-AdminAppRoleAssignment)* <br> Set-AdminPowerAppOwner *(bisher Set-AdminAppOwner)* |
| Lesen, Aktualisieren und Löschen von Flows | Get-AdminFlow <br> Enable-AdminFlow <br> Disable-AdminFlow <br> Remove-AdminFlow <br> Remove-AdminFlowApprovals |
| Lesen, Aktualisieren und Löschen von Berechtigungen für einen Flow | Get-AdminFlowOwnerRole <br> Set-AdminFlowOwnerRole <br> Remove-AdminFlowOwnerRole |
| Lesen und Löschen von Verbindungen | Get-AdminPowerAppConnection *(bisher Get-AdminConnection)* <br> Remove-AdminPowerAppConnection *(bisher Remove-AdminConnection)* |
| Lesen, Aktualisieren und Löschen von Berechtigungen für Verbindungen | Get-AdminPowerAppConnectionRoleAssignment *(bisher Get-AdminConnectionRoleAssignment)* <br> Set-AdminPowerAppEnvironmentConnectionRoleAssignment *(bisher Set-AdminConnectionRoleAssignment)* <br> Remove-AdminPowerAppConnectionRoleAssignment *(bisher Remove-AdminConnectionRoleAssignment)* |
| Lesen und Löschen von benutzerdefinierten Connectors | Get-AdminPowerAppConnector *(bisher Get-AdminConnector)* <br> Remove-AdminPowerAppConnector *(bisher Remove-AdminConnector)* |
| Lesen, Aktualisieren und Löschen von Berechtigungen für benutzerdefinierte Connectors | Get-AdminPowerAppConnectorRoleAssignment *(bisher Get-AdminConnectorRoleAssignment)*<br> Set-AdminPowerAppConnectorRoleAssignment *(bisher Set-AdminConnectorRoleAssignment)* <br> Remove-AdminPowerAppConnectorRoleAssignment *(bisher Remove-AdminConnectorRoleAssignment)* |
| Lesen der PowerApps-Benutzereinstellungen, Benutzeranwendungseinstellungen und Benachrichtigungen | Get-AdminPowerAppsUserDetails |
| Lesen und Löschen der Microsoft Flow-Einstellungen eines Benutzers, die für diesen zwar nicht sichtbar sind, aber die Ausführung von Flow unterstützen | Get-AdminFlowUserDetails <br> Remove-AdminFlowUserDetails |
| Erstellen, Lesen, Aktualisieren und Löschen von Richtlinien zur Verhinderung von Datenverlust für Ihre Organisation | Get-AdminDlpPolicy *(bisher Get-AdminApiPolicy)* <br> New-AdminDlpPolicy *(bisher Add-AdminApiPolicy)* <br> Remove-AdminDlpPolicy *(bisher Remove-AdminApiPolicy)* <br> Set-AdminDlpPolicy *(bisher Set-AdminApiPolicy)* <br> Add-ConnectorToBusinessDataGroup <br>  Remove-ConnectorFromBusinessDataGroup <br/>Add-CustomConnectorToPolicy<br/> Remove-CustomConnectorFromPolicy|

## <a name="tips"></a>Tipps

- Mit „Get-Help ‘CmdletName’“ erhalten Sie eine Liste von Beispielen.

     ![Befehl „Get-Help“](media/get-help-cmdlet.png "Befehl „Get-Help“")

- Wenn Sie nach dem Cmdlet-Namen den Bindestrich (-) eingegeben haben, drücken Sie die TAB-TASTE, um mögliche Eingabetags anzuzeigen.

Beispielbefehle:

```
Get-Help Get-AdminPowerAppEnvironment
Get-Help Get-AdminPowerAppEnvironment -Examples
Get-Help Get-AdminPowerAppEnvironment -Detailed
```

## <a name="operation-examples"></a>Beispiele für Vorgänge

Die folgenden gängigen Szenarios zeigen, wie Sie neue und vorhandene PowerApps-Cmdlets verwenden:

- [Befehle zu Umgebungen](#environments-commands)
- [PowerApps-Befehle](#powerapps-commands)
- [Flow-Befehle](#flow-commands)
- [Befehle zu API-Verbindungen](#api-connection-commands)
- [Befehle zur Richtlinie zur Verhinderung von Datenverlust (DLP)](#data-loss-prevention-dlp-policy-commands)

### <a name="environments-commands"></a>Befehle zu Umgebungen

Mit den folgenden Befehlen erhalten Sie Details zu den Umgebungen im Mandanten und aktualisieren diese:

#### <a name="display-a-list-of-all-environments"></a>Anzeigen einer Liste aller Umgebungen

```
Get-AdminPowerAppEnvironment
```

Gibt eine Liste der einzelnen Umgebungen in Ihrem Mandanten zurück. Sie enthält Details zu jeder Umgebung, wie z.B. Name der Umgebung (GUID), Anzeigename, Speicherort, Ersteller usw.

#### <a name="display-details-of-your-default-environment"></a>Anzeigen von Details zu Ihrer Standardumgebung

```
Get-AdminPowerAppEnvironment –Default
```

Gibt nur Details zur Standardumgebung im Mandanten zurück.

#### <a name="display-details-of-a-specific-environment"></a>Anzeigen von Details zu einer bestimmten Umgebung

```
Get-AdminPowerAppEnvironment –EnvironmentName ‘EnvironmentName’
```

**Hinweis:** Das Feld *EnvironmentName* ist ein eindeutiger Bezeichner. Es ist nicht identisch mit dem Feld *DisplayName* (siehe erstes und zweites Feld in der Ausgabe der folgenden Abbildung).

![Befehl „Get-AdminEnvironment“](media/get-adminenvironment.png "Befehl „Get-AdminEnvironment“")

### <a name="powerapps-commands"></a>PowerApps-Befehle

Diese Vorgänge werden zum Lesen und Ändern von PowerApps-Daten im Mandanten verwendet.

#### <a name="display-a-list-of-all-powerapps"></a>Anzeigen einer Liste aller PowerApps

```
Get-AdminPowerApp
```

Gibt eine Liste aller PowerApps in Ihrem Mandanten zurück. Sie enthält Details zu allen PowerApps, wie z.B. Name der Anwendung (GUID), Anzeigename, Ersteller usw.

#### <a name="display-a-list-of-all-powerapps-that-match-the-input-display-name"></a>Anzeigen einer Liste aller PowerApps, die mit dem eingegebenen Anzeigenamen übereinstimmen

```
Get-AdminPowerApp 'DisplayName'
```

Gibt eine Liste aller PowerApps in Ihrem Mandanten zurück, die mit dem Anzeigenamen übereinstimmen. 

**Hinweis:** Setzen Sie Eingabewerte, die Leerzeichen enthalten, in Anführungszeichen („“).

#### <a name="feature-an-application"></a>Vorstellen einer Anwendung

```
Set-AdminPowerAppAsFeatured –AppName 'AppName'
```

Vorgestellte Anwendungen werden im mobilen PowerApps-Player gruppiert und an den Anfang der Liste gestellt.

**Hinweis:** Wie bei den Umgebungen ist das Feld *AppName* ein eindeutiger Bezeichner und nicht identisch mit dem Feld *DisplayName*. Sie können zum Ausführen von Vorgängen basierend auf dem Anzeigenamen bei einigen Funktionen die Pipeline verwenden (siehe nächste Funktion).

#### <a name="make-an-application-a-hero-app-using-the-pipeline"></a>Festlegen einer Anwendung als Hero-App mithilfe der Pipeline

```
Get-AdminPowerApp 'DisplayName' | Set-AdminPowerAppAsHero
```

Eine Hero-App wird im mobilen PowerApps-Player am Anfang der Liste angezeigt. Es gibt immer nur eine Hero-App.

Die Pipeline (als „|“ zwischen zwei Cmdlets dargestellt) überträgt die Ausgabe des ersten Cmdlets als Eingabewert in das zweite Cmdlet. Dabei wird angenommen, dass die Funktion so geschrieben wurde, dass sie die Pipelinefunktion unterstützt.

**Hinweis:** Nur eine vorgestellte App kann zu einer Hero-App gemacht werden.

#### <a name="display-the-number-of-apps-each-user-owns"></a>Anzeigen der App-Anzahl jedes Benutzers

```
Get-AdminPowerApp | Select –ExpandProperty Owner | Select –ExpandProperty displayname | Group
```

Sie können native PowerShell-Funktionen mit PowerApps-Cmdlets kombinieren, die Daten noch weiter zu bearbeiten. In diesem Beispiel wird die Select-Funktion verwendet, um das Attribut „Besitzer“ (ein Objekt) vom Objekt „Get-AdminApp“ zu isolieren. Anschließend wird der Name des Besitzerobjekts isoliert, indem die Ausgabe in einer anderen Select-Funktion verwendet wird (Pipelining). Zuletzt wird die Ausgabe der zweiten Select-Funktion in der Group-Funktion verwendet. Dadurch wird eine Tabelle mit der Anzahl der Apps jedes Besitzers zurückgegeben.

![Befehl „Get-AdminPowerApp“](media/get-adminpowerapp.png "Befehl „Get-AdminPowerApp“")

#### <a name="display-the-number-of-apps-in-each-environment"></a>Anzeigen der App-Anzahl in jeder Umgebung

```
Get-AdminPowerApp | Select -ExpandProperty EnvironmentName | Group | %{ New-Object -TypeName PSObject -Property @{ DisplayName = (Get-AdminPowerAppEnvironment -EnvironmentName $_.Name | Select -ExpandProperty displayName); Count = $_.Count } }
```

![Befehl „Get-AdminPowerApp“](media/get-adminpowerapp-environment.png "Befehl „Get-AdminPowerApp“")

#### <a name="download-powerapps-user-details"></a>Herunterladen von Details zu PowerApps-Benutzern

```
Get-AdminPowerAppsUserDetails -OutputFilePath '.\adminUserDetails.txt' –UserPrincipalName ‘admin@bappartners.onmicrosoft.com’
```

Mit diesem Befehl werden Details zu PowerApps-Benutzern (grundlegende Nutzungsinformationen zum eingegebenen Benutzer über den Benutzerprinzipalnamen) in einer angegebenen Textdatei gespeichert. Sofern noch keine Datei mit diesem Namen vorhanden ist, wird eine neue Datei erstellt. Andernfalls wird die bestehende Datei überschrieben.

#### <a name="set-logged-in-user-as-the-owner-of-a-powerapp"></a>Festlegen des angemeldeten Benutzers als Besitzer einer PowerApp

```
Set-AdminPowerAppOwner –AppName 'AppName' -AppOwner $Global:currentSession.userId –EnvironmentName 'EnvironmentName'
```

Die Besitzerrolle einer PowerApp wird in den aktuellen Benutzer geändert. Der ursprüngliche Besitzer erhält den Rollentyp „Kann ansehen“.

**Hinweis:** Die Felder „AppName“ und „EnvironmentName“ sind die eindeutigen Bezeichner (GUIDs) und nicht die Anzeigenamen.

### <a name="flow-commands"></a>Flow-Befehle

Mit diesen Befehlen können Sie Daten in Zusammenhang mit Microsoft Flow anzeigen und ändern.

#### <a name="display-all-flows"></a>Anzeigen aller Flows

```
Get-AdminFlow
```

Gibt eine Liste aller Flows im Mandanten zurück.

#### <a name="display-flow-owner-role-details"></a>Anzeigen von Details zur Rolle des Flowbesitzers

```
Get-AdminFlowOwnerRole –EnvironmentName 'EnvironmentName' –FlowName ‘FlowName’
```

Gibt Details zum Besitzer des angegebenen Flows zurück.

**Hinweis:** Wie auch schon bei *Umgebungen* und *PowerApps* ist *FlowName* der eindeutige Bezeichner (GUID) und nicht identisch mit dem Anzeigenamen des Flows.

#### <a name="display-flow-user-details"></a>Anzeigen von Details zum Flowbenutzer

```
Get-AdminFlowUserDetails –UserId $Global:currentSession.userId
```

Gibt Benutzerdetails in Bezug auf die Nutzung des Flows zurück. In diesem Beispiel wird die Benutzer-ID des aktuell angemeldeten Benutzers der PowerShell-Sitzung als Eingabe verwendet.

#### <a name="remove-flow-user-details"></a>Entfernen von Details zum Flowbenutzer

```
Remove-AdminFlowUserDetails –UserId 'UserId'
```

Löscht die Details zu einem Flowbenutzer vollständig aus der Microsoft-Datenbank. Bevor die Details zum Flowbenutzer endgültig gelöscht werden können, müssen alle Flows gelöscht werden, die der eingegebene Benutzer besitzt.

**Hinweis:** Das Feld „UserId“ stellt die Objekt-ID der Azure Active Directory-Datensätze des Benutzers dar. Sie finden die Objekt-ID im [Azure-Portal](https://portal.azure.com) unter **Azure Active Directory** > **Benutzer** > **Profil** > **Objekt-ID**. Wenn Sie von hier aus auf diese Daten zugreifen möchten, müssen Sie ein Administrator sein.

#### <a name="export-all-flows-to-a-csv-file"></a>Exportieren aller Flows in eine CSV-Datei

```
Get-AdminFlow | Export-Csv -Path '.\FlowExport.csv'
```

Exportiert alle Flows in Ihrem Mandanten in eine CSV-Datei mit Tabellenansicht.

### <a name="api-connection-commands"></a>Befehle zu API-Verbindungen

Sie können die API-Verbindungen in Ihrem Mandanten anzeigen und verwalten.

#### <a name="display-all-native-connections-in-your-default-environment"></a>Anzeigen aller nativen Verbindungen in Ihrer Standardumgebung

```
Get-AdminPowerAppEnvironment -Default | Get-AdminConnection
```

Zeigt eine Liste aller API-Verbindungen in Ihrer Standardumgebung an. Native Verbindungen finden Sie im Portal für Ersteller in der Registerkarte **Daten** > **Verbindungen**.

#### <a name="display-all-custom-connectors-in-the-tenant"></a>Anzeigen aller benutzerdefinierten Connectors im Mandanten

```
Get-AdminPowerAppConnector
```

Gibt eine Liste mit Details zu allen benutzerdefinierten Connectors im Mandanten zurück.

### <a name="data-loss-prevention-dlp-policy-commands"></a>Befehle zur Richtlinie zur Verhinderung von Datenverlust (DLP)

Mit diesen Cmdlets steuern Sie die DLP-Richtlinien in Ihrem Mandanten.

#### <a name="display-all-policies"></a>Anzeigen aller Richtlinien

```
Get-AdminDlpPolicy
```

Gibt eine Liste aller Richtlinien zurück.

#### <a name="display-a-filtered-list-of-policies"></a>Anzeigen einer gefilterten Richtlinienliste

```
Get-AdminDlpPolicy 'DisplayName'
```

Verwendet zum Filtern der Richtlinien den Anzeigenamen.

#### <a name="display-all-business-data-only-api-connectors-in-a-policy"></a>Anzeigen aller API-Connectors „Business data only“ (nur Geschäftsdaten) in einer Richtlinie

```
Get-AdminDlpPolicy 'PolicyName' | Select –ExpandProperty BusinessDataGroup
```

Listet die API-Verbindungen auf, die sich im Feld *Business data only* (oder *BusinessDataGroup*) einer eingegebenen Richtlinie befinden.

#### <a name="add-a-connector-to-the-business-data-only-group"></a>Hinzufügen eines Connectors zur Gruppe „Business data only“

```
Add-ConnectorToBusinessDataGroup -PolicyName 'PolicyName' –ConnectorName 'ConnectorName'
```

Fügt der Gruppe „Business data only“ in einer bestimmten DLP-Richtlinie einen Connector hinzu. Weitere Informationen finden Sie in der Auflistung der Connectors nach *DisplayName* und *ConnectorName* (als Eingabe verwendet).

## <a name="version-history"></a>Versionsverlauf
| Version | Date | Aktualisierungen |
| --- | --- | --- |
| 1.0 | 23.04.2018 | <ol> <li> Erster Start der PowerApps-Cmdlets für App-Ersteller (Vorschau), einschließlich Verwaltungs-Cmdlets für Umgebungen, Apps, Flows, Flow-Genehmigungen, Verbindungen und benutzerdefinierte Connectors </li> <li> Erster Start der PowerApps-Cmdlets für Administratoren (Vorschau) einschließlich administrative Cmdlets für Umgebungen, Apps und Flows </li></ol>|
| 2.0 | 24.05.2018 | <ol> <li> Kleinere Fehlerbehebungen in den beiden Cmdlets für App-Ersteller und Administratoren </li> <li> Die folgenden neuen administrativen Cmdlets wurden hinzugefügt: <br> Get-AdminConnection <br> Remove-AdminConnection <br> Get-AdminConnectionRoleAssignment <br> Set-AdminConnectionRoleAssignment <br>Remove-AdminConnectionRoleAssignment <br>Get-AdminConnector  <br>Remove-AdminConnector <br>Set-AdminConnectorRoleAssignment  <br>Get-AdminConnectorRoleAssignment  <br>Remove-AdminConnectorRoleAssignment <br>Get-AdminPowerAppsUserDetails <br>Get-AdminFlowUserDetails <br>Remove-AdminFlowUserDetails <br>Get-AdminApiPolicy  <br>Add-AdminApiPolicy <br>Remove-AdminApiPolicy <br>Set-AdminApiPolicy <br>Add-ConnectorToBusinessDataGroup  <br>Remove-ConnectorFromBusinessDataGroup </li> </ol>
| 3.0 | 30.07.2018 | <ol> <li> Anmeldeinformationen können nun Add-PowerAppsAccount hinzugefügt werden (zur Aktivierung von wiederkehrendem Scripting). </li> <li>  Kleinere Fehlerbehebungen in den Cmdlets für App-Ersteller und Administratoren </li> <li> Präfix „PowerApp“ oder „Flow“ wurde jedem Cmdlet für App-Ersteller hinzugefügt. </li> <li>  Präfix „AdminPowerApp“ oder „AdminFlow“ wurde jedem Cmdlet für Administratoren hinzugefügt. </li> <li> Die folgenden neuen administrativen Cmdlets wurden hinzugefügt: <br> New-AdminPowerAppEnvironment <br> Set-AdminPowerAppEnvironmentDisplayName <br> New-AdminPowerAppCdsDatabase <br> Get-AdminPowerAppCdsDatabaseLanguages <br> Get-AdminPowerAppCdsDatabaseCurrencies <br> Get-AdminPowerAppEnvironmentLocations <br> Get-AdminPowerAppConnectionReferences <br> Set-AdminPowerAppAsFeatured <br> Clear-AdminPowerAppAsFeatured <br> Set-AdminPowerAppAsHero <br> Clear-AdminPowerAppAsHero <br> Set-AdminPowerAppApisToBypassConsent <br> Clear-AdminPowerAppApisToBypassConsent <br> Remove-AdminFlowApprovals </li></ol>
| 4.0 | 15.08.2018 | Ein optionaler Parameter wurde New-AdminPowerAppCdsDatabase hinzugefügt, um die Funktion standardmäßig zu synchronisieren (d.h. keine Rückgaben, solange die Datenbank nicht erfolgreich bereitgestellt wurde)
| 5.0 | 24.08.2018 | Das dadurch verursachte Problem, dass Flow-Admin-Cmdlets abhängig von ihren Sicherheitseinstellungen in einigen Fällen keine Daten zurückgegeben haben, wurde behoben.
| 6.0 | 09.01.2019 | <ol><li>Cmdlets sind jetzt im PowerShell-Katalog als zwei separate Module verfügbar: Administrator und Ersteller.</li> <li>Administratives Cmdlet wurde hinzugefügt: Remove-LegacyCDSDatabase.</li><li> Beispiele für Vorgänge wurden hinzugefügt.</li><li>Möglichkeit zum Verwalten von HTTP- und benutzerdefinierten Connectors in DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust) wurde hinzugefügt.</li></ol>|

## <a name="questions"></a>Fragen?

Wenn Sie Kommentare, Vorschläge oder Fragen haben, können Sie diese im [Community Board zur Verwaltung von PowerApps](https://powerusers.microsoft.com/t5/Administering-PowerApps/bd-p/Admin_PowerApps) veröffentlichen.

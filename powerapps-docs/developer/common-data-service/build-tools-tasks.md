---
title: Aufgaben von Buildtools| Microsoft Docs
description: 'Bei PowerApps build tools handelt es sich um eine Sammlung von PowerApps-spezifischen Azure DevOps-Buildaufgaben, die vermeiden, dass Tools und Skripts manuell heruntergeladen werden müssen, um den Anwendungslebenszyklus von PowerApps zu verwalten. In diesem Thema werden die Aufgaben beschrieben, die verfügbar sind. '
ms.custom: ''
ms.date: 07/21/2019
ms.reviewer: Dean-Haas
ms.service: powerapps
ms.topic: article
author: mikkelsen2000
ms.author: pemikkel
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="build-tools-tasks"></a>Aufgaben von Buildtools

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Einige Arten von Buildaufgaben stehen als Teil der PowerApps build tools zur Verfügung, um Ihnen zu helfen, den Anwendungslebenszyklus unter Verwendung von Azure DevOps zu automatisieren.
  
## <a name="helper-task"></a>Helferaufgabe

Das PowerApps-Toolinstallationsprogramm muss die erste Aufgabe in jeder Build- und Versionspipeline sein. Diese Aufgabe installiert eine Reihe von PowerApps-spezifischen Tools, die für den Agent erforderlich sind, um die PowerApps-Buildaufgaben auszuführen. Diese Aufgabe erfordert keine zusätzlichen Konfigurationsschritte.

## <a name="quality-check"></a>Qualitätsprüfung

Die PowerApps-Prüfungsaufgabe führt eine statische Analyseprüfung Ihrer Lösungen im Zusammenhang mit bewährten Regeln durch, um problematische Muster zu identifizieren, die Sie unbeabsichtigterweise beim Erstellen der Lösung eingeführt haben.

| **Parameter** | **Beschreibung** |
| --- | --- |
| PowerApps-Prüfungsdienst  |   Wählen Sie den Dienstendpunkt für die PowerApps-Prüfung aus. Der Dienstendpunkt wird unter **Dienstverbindungen** in **Projekteinstellungen** definiert.  **HINWEIS:** Die Dienstverbindungsart, die nur für diese bestimmte Aufgabe verwendet werden muss, lautet „PowerApps-Prüfung“. Dies ist eine Dienstprinzipalverbindung. Weitere Informationen dazu, wie Sie Dienstprinzipale konfigurieren, bevor Sie die Aufgabe verwenden können, finden Sie [hier](https://aka.ms/buildtoolsconnection).  |
| Speicherort der zu analysierenden Datei  | Geben Sie an, ob auf eine lokale Datei oder eine Referenzdatei über eine SAS-URL verwiesen wird. 
| Lokale zu analysierende Datei/SAS-URI für zu analysierende Datei |  Geben Sie den Pfad und Dateinamen der zu analysierenden ZIP-Dateien an.   Platzhalter können verwendet werden. Beispielsweise **\*.zip für alle Dateien in allen Unterordnern. Sie können die Dateien direkt angeben oder einen Verweis auf eine Datei über eine SAS-URI.   |
|  Regelsatz |   Geben Sie an, welcher Regelsatz angewendet werden soll. Die folgenden zwei Regelsätze stehen zur Verfügung: **Lösungsprüfung:** Dies ist derselbe Regelsatz, der über das [Hersteller-Portal](https://make.powerapps.com/) ausgeführt wird.    **AppSource:** Dies ist der erweiterte Regelsatz, der verwendet wird, um eine Anwendung zu zertifizieren, bevor sie in [AppSource](https://appsource.microsoft.com/en-US/) veröffentlicht werden kann.   |

### <a name="configure-service-connection-for-powerapps-checker"></a>Konfigurieren der Dienstverbindung für die PowerApps-Prüfung

Bevor Sie die PowerApps-Prüfungsaufgabe konfigurieren können, müssen Sie zunächst die Dienstprinzipale definieren, die verwendet werden, um eine Verbindung mit dem PowerApps-Prüfungsdienst herzustellen. Weitere Informationen zum zugrunde liegenden PowerApps-Prüfungsdienst und zur Authentifizierung finden Sie [hier](https://docs.microsoft.com/en-us/powershell/powerapps/overview?view=pa-ps-latest#get-started-using-the-microsoftpowerappscheckerpowershell-module). Die folgenden Schritte enthalten jedoch alle Informationen, die Sie für den Anfang benötigen.

Nachfolgend wird beschrieben, wie Sie die erforderliche Azure Active Directory-Anwendung (AAD) mit dem [AzureAD-PowerShell-Modul](https://docs.microsoft.com/en-us/powershell/module/azuread/?view=azureadps-2.0) generieren, einen geheimen Clientschlüssel hinzufügen und ihn dann verwenden, um die PowerApps-Prüfungsverbindungszeichenfolge zu konfigurieren.

> [!NOTE]
> Rechte zum Erstellen von Dienstprinzipalen in einem AAD-Mandanten, der für PowerApps (P1/P2) oder D365 CE lizenziert ist, sind erforderlich, um diese Schritte auszuführen. 

1. Öffnen Sie einen PowerShell-Befehl mit Administratorrechten.
![PowerShell-Befehlsfenster](media/pscommand.png "PowerShell-Befehlsfenster")
2. Führen Sie den folgenden Befehl in PowerShell aus: *Install-Module -Name AzureAD*.
![Install-Module-Befehl](media/pscommand-install.png "Install-Module-Befehl")
 
3.  Dies erfordert Sie auf, den Module aus PSGallery zu vertrauen. Klicken Sie auf **A (Ja zu allen)**.
1. Kopieren Sie Folgendes, und fügen Sie es dann in die PowerShell-Eingabeaufforderung ein:

```powershell 
function New-PowerAppsCheckerAzureADApplication
{
    [CmdletBinding()]
    param(
        [Parameter(Mandatory = $true)]
        [Guid]
        $TenantId,
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string]
        $ApplicationDisplayName
    )
    # Using AzureAD as the RM modules, AzureRm.Resource and AzureRm.Profile, do not allow for setting RequiredResourceAccess
    Import-Module AzureAD | Out-Null
    try
    {
        Connect-AzureAD -TenantId $TenantId | Out-Null
    }
    catch [Microsoft.Open.Azure.AD.CommonLibrary.AadAuthenticationFailedException]
    {
        Write-Error "Received a failure result from the connecting to AzureAD, $($_.Exception.Message). Stopping."
        return
    }
    $graphSignInAndReadProfileRequirement = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
    $acc1 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "e1fe6dd8-ba31-4d61-89e7-88639da4683d","Scope"
    $graphSignInAndReadProfileRequirement.ResourceAccess = $acc1
    $graphSignInAndReadProfileRequirement.ResourceAppId = "00000003-0000-0000-c000-000000000000"

    $powerAppsCheckerApiRequirement = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
    $acc1 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "d533b86d-8f67-45f0-b8bb-c0cee8da0356","Scope"
    $acc2 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "640bd519-35de-4a25-994f-ae29551cc6d2","Scope"
    $powerAppsCheckerApiRequirement.ResourceAccess = $acc1,$acc2
    $powerAppsCheckerApiRequirement.ResourceAppId = "c9299480-c13a-49db-a7ae-cdfe54fe0313"

    $application = New-AzureADApplication -DisplayName $ApplicationDisplayName -PublicClient $true -ReplyUrls "urn:ietf:wg:oauth:2.0:oob" -RequiredResourceAccess $graphSignInAndReadProfileRequirement, $powerAppsCheckerApiRequirement
    if ($application -eq $null -or $application.AppId -eq $null)
    {
        Write-Error "Unable to create the application as requested."
    }
    else
    {
        Write-Host "The application $($application.AppId):$ApplicationDisplayName was created in the tenant, $TenantId. You may need to have an administrator grant consent. If running in a userless process, you will need to add a secret or certificate in which to authenticate." 
    }
    return $application
}

# Login to AAD as your user
Connect-AzureAD

# Establish your tenant ID
$tenantId = (Get-AzureADTenantDetail).ObjectId

# Create the AAD application registration using the AzureAD module and the sample script
$newApp = New-PowerAppsCheckerAzureADApplication -ApplicationDisplayName "PowerApps Checker Client" -TenantId $tenantId

# Next step => create a secret via the Admin portal, CLI, or PowerShell module.
 ```

5.  Wenn Sie dazu aufgefordert werden, wählen Sie immer **A (Immer ausführen)** aus.
![Bildschirm für PowerShell-Befehl](media/pscommand-always-run.png "Bildschirm für PowerShell-Befehl")
6. Ein Anmeldedialogfeld wird angezeigt. Melden Sie sich als Benutzer an. Beachten Sie, dass Sie sich in einigen Fällen zweimal anmelden müssen.
7. Nachdem das Skript abgeschlossen ist, werden die Anwendung-ID und der Mandant im Befehlsfenster angezeigt.
8. Melden Sie sich anschließend bei [Azure AD](https://portal.azure.com) an, um den geheimen Clientschlüssel abzurufen.
9. Wählen Sie in Microsoft Azure **Azure Active Directory –> App-Registrierungen –> PowerApps-Prüfungs-Client.**
![Auswählen des Prüfungsclients in Azure](media/azure-select-checker.png "Azure-Screenshot")
10. Klicken Sie im linken Navigationsbereich unter **Verwalten** auf **Zertifikate und geheime Schlüssel**.
11. Wählen Sie im Bildschirm **Zertifikate und geheime Schlüssel** unter **Geheime Clientschlüssel** die Option **Neuer geheimer Clientschlüssel** aus. 
12. Geben Sie eine Beschreibung für den geheimen Clientschlüssel ein, wählen Sie die Ablaufeinstellung, und klicken Sie dann auf **Hinzufügen**.
13. Kopieren Sie den geheimen Clientschlüssel, der auf dem nächsten Bildschirm angezeigt wird. 
![Kopieren des geheimen Clientschlüssels](media/client-secret-copy.png "Kopieren des geheimen Clientschlüssels")
    > [!NOTE]
    > Dies ist das einzige Mal, dass der geheime Clientschlüssel angezeigt wird.
14. Öffnen Sie die Verbindung des PowerApps-Prüfungsdiensts, und fügen Sie den geheimen Clientschlüssel in das Feld **Dienstprinzipalschüssel** ein, und klicken Sie dann **OK**.

Ihre Verbindung ist jetzt bereit, und kann von der [PowerApps-Prüfungsbuildaufgabe](https://aka.ms/buildtoolsdoc) verwendet werden. 

## <a name="solution-tasks"></a>Lösungsaufgaben

Diese Gruppe von Aufgaben führt Aktionen für Lösungen aus und enthält die folgenden Aufgaben:

### <a name="powerapps-import-solution"></a>PowerApps: Lösung importieren

Die Aufgabe zum Importieren einer Lösung importiert eine Lösung in eine Zielumgebung.

| **Parameter** | **Beschreibung** |
|----|----|
| PowerApps: Umgebungs-URL  | Der Dienstendpunkt für die Zielumgebung, in welche Sie die Lösung importieren möchten. Zum Beispiel: *https://powerappsbuildtools.crm.dynamics.com*.  Dienstendpunkte können unter **Dienstverbindungen** in **Projekteinstellungen** definiert werden. |
| Lösungseingabedatei  | Der Pfad und der Dateiname der Datei solution.zip, die in die Zielumgebung importiert werden soll. Beispiel: *$(Build.ArtifactStagingDirectory)\$(SolutionName).zip*.
 |
> [!NOTE] 
> Variablen sind eine bequeme Möglichkeit, wichtige Daten in verschiedene Teile der Pipeline zu übertragen. Eine vollständige Liste von vordefinierten Variablen ist [hier](https://docs.microsoft.com/en-us/azure/devops/pipelines/build/variables?view=azure-devops&tabs=yaml) verfügbar.

### <a name="powerapps-export-solution"></a>PowerApps: Lösung exportieren

Die Aufgabe zum Exportieren einer Lösung exportiert eine Lösung aus einer Quellumgebung.

| **Parameter** | **Beschreibung** |
|----------|-------------|
| PowerApps: Umgebungs-URL | Der Dienstendpunkt für die Quellumgebung, aus der Sie die Lösung exportieren möchten.  Definiert unter **Dienstverbindungen -> Generische Dienstverbindung** in **Projekteinstellungen**. |
| Lösungsname | Der Name der zu exportierenden Lösung. Verwenden Sie immer den Lösungsnamen. Nicht den Anzeigenamen. |
| Lösungsausgabedatei | Der Pfad und der Dateiname der Datei solution.zip, in die die Quellumgebung exportiert werden soll. Beispiel: *$(Build.ArtifactStagingDirectory)\$(SolutionName).zip*. |

> [!NOTE] 
> Variablen sind eine bequeme Möglichkeit, wichtige Daten in verschiedene Teile der Pipeline zu übertragen. Eine vollständige Liste von vordefinierten Variablen ist hier verfügbar.
 
### <a name="powerapps-unpack-solution"></a>PowerApps: Lösung entpacken

Die Aufgabe zum Entpacken einer Lösung nimmt eine komprimierte Lösungsdatei und entpackt sie in mehrere XML-Dateien und andere Dateien, sodass diese Dateien durch ein Quellcodeverwaltungssystem leichter verwaltet werden können.

| **Parameter** | **Beschreibung** |
|------------|---------|
| Lösungseingabedatei | Der Pfad und Dateiname der zu entpackenden Datei solution.zip an. |
| Zielordner zum Entpacken der Lösung | Der Pfad und Zielordner, in den Sie die Lösung entpacken möchten. |
| Lösungstyp | Der Typ der Lösung, die Sie entpacken möchten: **Nicht verwaltet** (empfohlen): *Nur die nicht verwaltete Lösung sollte in das Repo entpackt werden*, **Verwaltet**, **Beide** |


### <a name="powerapps-pack-solution"></a>PowerApps: Lösung verpacken

Packt eine Lösung, die im Quellsteuerelement dargestellt wird, in eine solution.zip-Datei, die in eine Umgebung importiert werden kann.

| **Parameter** | **Beschreibung** |
|------------|---------|
| Lösungsausgabedatei | Der Pfad und der Dateiname der Datei solution.zip, in welche die Zielumgebung gepackt werden soll. |
| Quellordner der zu packenden Lösung | Der Pfad und der Quellordner mit der zu packenden Lösung. |
| Lösungstyp | Der Typ der Lösung, die Sie entpacken möchten: **Nicht verwaltet** (empfohlen):, **Verwaltet**, **Beide** |

### <a name="publish-customizations"></a>Veröffentlichen von Anpassungen

Die Aufgabe für die Veröffentlichung von Anpassungen veröffentlicht alle Anpassungen in einer Umgebung.

| **Parameter** | **Beschreibung** |
|------------|---------|
| PowerApps: Umgebungs-URL | Der Dienstendpunkt für die Umgebung, in der Sie Anpassungen veröffentlichen möchten.  Definiert unter **Dienstverbindungen** in **Projekteinstellungen**. |

### <a name="powerapps-set-solution-version"></a>PowerApps: Lösungsversion festlegen 

Die Aufgabe zum Festlegen der Lösungsversion aktualisiert die Version einer Lösung.

| **Parameter** | **Beschreibung** |
|---------------------------|----|
| PowerApps: Umgebungs-URL  | Der Dienstendpunkt für die Umgebung, in der Sie das Paket bereitstellen möchten.  Definiert unter **Dienstverbindungen** in **Projekteinstellungen**. |
| Paketdatei  | Der Pfad und Dateiname des Pakets, das Sie bereitstellen möchten |

### <a name="powerapps-deploy-package"></a>PowerApps: Bereitstellungspaket

Die Aufgabe zum Bereitstellen eines Pakets stellt ein Paket in einer Umgebung bereit. Das Bereitstellen des Pakets im Gegensatz zu einer einzelnen Lösungsdatei bietet eine Möglichkeit, mehrere Lösungen, Daten und Code in einer Umgebung bereitzustellen.

| **Parameter** | **Beschreibung** |
|---------------------------|----|
| PowerApps: Umgebungs-URL  | Der Dienstendpunkt für die Zielumgebung, in welcher die zu aktualisierende Lösung gespeichert ist.  Definiert unter **Dienstverbindungen** in **Projekteinstellungen**. |
| Lösungsname  | Der Name der Lösung, für die sie eine Versionsnummer festlegen möchten |

## <a name="environment-management-tasks"></a>Umgebungsverwaltungsaufgaben

Umgebungsverwaltungsaufgaben werden verwendet, um allgemeine Umgebungsverwaltungsfunktionen zu automatisieren, und umfassen die folgenden Aufgaben:

### <a name="powerapps-create-environment"></a>PowerApps: Umgebung erstellen

Die Aufgabe zum Erstellen von Umgebungen erstellt eine Umgebung.

> [!NOTE]
> Eine neue Umgebung kann nur bereitgestellt werden, wenn die Lizenz oder Kapazität die Erstellung zusätzlicher Umgebungen zulässt.

| **Parameter** | **Beschreibung** |
|---------|-----------|
| Bereitstellungsregion | Die Region, in der die Umgebung bereitgestellt werden soll. |
| Instanztyp | Der Typ der bereitzustellenden Instanz. Optionen sind „Sandkasten“ oder „Produktion“. |
| Ausgangssprache | Die Ausgangssprache in der Umgebung. |
| Domänenname | Dies ist die umgebungsspezifische Zeichenfolge, die einen Teil der URL bildet. Beispiel für eine Umgebung mit der folgenden URL: *https://powerappsbuildtasks.crm.dynamics.com*, der Domänenname lautet „powerappsbuildtasks“.  HINWEIS: Wenn Sie einen Domänennamen eingeben, der bereits verwendet wird, fügt die Aufgabe der URL einen numerischen Wert an, beginnend mit 0. Für das Beispiel oben könnte die URL *https://powerappsbuildtasks0.crm.dynamics.com* lauten. |
| Anzeigename | Der Anzeigename der Umgebung. |

### <a name="powerapps-delete-environment"></a>PowerApps: Umgebung löschen

Die Aufgabe zum Löschen von Umgebungen löscht eine Umgebung.

| **Parameter** | **Beschreibung** |
|---------|-----------|
| PowerApps: Umgebungs-URL  | Der Dienstendpunkt für die Umgebung, die Sie löschen möchten.  Definiert unter **Dienstverbindungen** in **Projekteinstellungen**. |

### <a name="powerapps-backup-environment"></a>PowerApps: Sicherungsumgebung

Die Aufgabe zum Sichern von Umgebungen sichert eine Umgebung. 

| **Parameter** | **Beschreibung** |
|---------|-----------|
| PowerApps: Umgebungs-URL  | Der Dienstendpunkt für die Umgebung, die Sie sichern möchten.  Definiert unter **Dienstverbindungen** in **Projekteinstellungen**. |
| Sicherungsbeschriftung  | Die Beschriftung, die der Sicherung zugewiesen werden soll.  |

### <a name="powerapps-copy-environment"></a>PowerApps: Umgebung kopieren

Die Aufgabe zum Kopieren von Umgebungen kopiert eine Umgebung in eine Zielumgebung. Zwei Arten von Kopiervorgängen stehen zur Verfügung: vollständig und minimal. Beim vollständigen Kopieren werden sowohl Daten als auch Lösungsmetadaten (Anpassungen) kopiert, während beim minimalen Kopieren die Lösungsmetadaten, nicht aber die tatsächlichen Daten kopiert werden.

> [!NOTE]
> Diese Aufgabe ist nur für D365 CE-Umgebungen verfügbar.  

| **Parameter** | **Beschreibung** |
|---------|-----------|
| PowerApps: Quellumgebungs-URL  | Der Dienstendpunkt für die Umgebung, aus der Sie kopieren möchten.  Definiert unter **Dienstverbindungen** in **Projekteinstellungen**. |
| PowerApps: Zielumgebungs-URL  | Der Dienstendpunkt für die Umgebung, in die Sie kopieren möchten.  Definiert unter **Dienstverbindungen** in **Projekteinstellungen**. |

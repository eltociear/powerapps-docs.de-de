---
title: Bereitstellen und Konfigurieren der Notfallreaktions-App | Microsoft-Dokumentation
description: Detaillierte Anweisungen für IT-Administratoren von Krankenhäusern für die Bereitstellung und Konfiguration der Beispielanwendung in ihrer Organisation.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/30/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- GetStarted
- PowerApps
ms.openlocfilehash: f126a415cfe42e38e2131967a29564fc0255f6bb
ms.sourcegitcommit: b6beb1b76d9ddb0f9846253f895d581bda9012ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2020
ms.locfileid: "80417479"
---
# <a name="deploy-and-configure-the-emergency-response-app"></a>Bereitstellen und Konfigurieren der Notfallreaktions-App

Die Notfallreaktions-App erfordert ein geringes Maß an Einrichtung, um sie an Ihre Anforderungen anzupassen. Dieser Artikel enthält detaillierte Anweisungen für IT-Administratoren von Krankenhäusern für die Bereitstellung und Konfiguration der Anwendung in ihrer Organisation.

Geschätzte Dauer: **35-40 Minuten**.

## <a name="demo-deploy-and-configure-the-emergency-response-app"></a>Demo: Bereitstellen und Konfigurieren der Notfallreaktions-App

Sehen Sie sich an, wie Sie die Notfallreaktions-App bereitstellen und konfigurieren können.

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="deploy-the-emergency-response-app"></a>Bereitstellen der Notfallreaktions-App

Führen Sie die folgenden Schritte aus, um die Beispiel-App für die Notfallreaktion in Ihrer Organisation bereitzustellen.

- [Schritt 1: Registrieren für Power Apps und Erstellen einer Umgebung](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [Schritt 2: Herunterladen des Bereitstellungspakets](#step-2-download-the-deployment-package)
- [Schritt 3: Importieren der Lösungsdatei in Ihre Umgebung](#step-3-import-the-solution-file-into-your-environment)
- [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization)
    - [Schritt 4.1: Laden obligatorischer Konfigurationsdaten](#step-41-load-mandatory-configuration-data)
    - [Schritt 4.2: Laden von Masterdaten](#step-42-load-master-data)
- [Schritt 5: Aktualisieren des Brandings der mobilen App](#step-5-update-the-mobile-app-branding)
- [Schritt 6: Umgehen der Zustimmung für mobile Apps](#step-6-bypass-consent-for-mobile-apps)
- [Schritt 7: Hinzufügen des Azure Application Insights-Schlüssels zu mobilen Apps für Telemetriezwecke](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry)
- [Schritt 8: Freigeben von Canvas-Apps für Benutzer in Ihrer Organisation](#step-8-share-canvas-apps-with-users-in-your-organization)
- [Schritt 9: Festlegen Ihrer mobilen App als herausragende und empfohlene App](#step-9-set-your-mobile-app-as-hero-and-featured-app)
- [Schritt 10: Freigeben der modellgesteuerten App für Administratoren in Ihrer Organisation](#step-10-share-model-driven-app-with-admins-in-your-organization)

### <a name="step-1-sign-up-for-power-apps-and-create-an-environment"></a>Schritt 1: Registrieren für Power Apps und Erstellen einer Umgebung

Wenn Sie noch nicht über Power Apps verfügen, registrieren Sie sich für Power Apps, und erwerben Sie eine geeignete Lizenz.

Weitere Informationen:

-   [Power Apps – Preise](https://powerapps.microsoft.com/pricing/)
-   [Erwerben von Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Nachdem Sie Power Apps erworben haben, erstellen Sie eine Umgebung mit einer Common Data Service-Datenbank.

1.  Melden Sie sich beim [Power Platform Admin Center](https://aka.ms/ppac) an.

2.  Erstellen Sie eine Common Data Service-Umgebung mit der Datenbank. Weitere Informationen: [Erstellen und Verwalten von Umgebungen](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT]
    > Wenn Sie beim Erstellen der Datenbank eine Sicherheitsgruppe für die Datenbank auswählen, können die Apps *nur* für Benutzer freigegeben werden, die Mitglieder der Sicherheitsgruppe sind.

3.  Erstellen Sie in Ihrer Umgebung entsprechende Benutzer. Weitere Informationen: [Erstellen von Benutzern und Zuweisen von Rollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>Schritt 2: Herunterladen des Bereitstellungspakets

Laden Sie das neueste Bereitstellungspaket (.zip) von <https://aka.ms/emergency-response-solution> herunter, das die Lösungsdatei, Images und Datendateien enthält, um die Apps und Geschäftslogik für die Notfallreaktions-App einzurichten.

Extrahieren Sie die Bereitstellungsdatei (.zip) an einem Speicherort auf Ihrem Computer, um den Bereitstellungsprozess zu starten. Der extrahierte Ordner enthält die folgenden Ordner:

| **Ordner/Datei**       | **Beschreibung**  |
|-----------------------|------------------|
| **App Icons**         | Enthält die Standard-App-Symbole für die mobilen Apps (Canvas-Apps)|
| **Data Files**        | Enthält die Stamm- und Beispieldatendateien (. xlsx), damit die Lösung/App funktioniert. Sie können Daten aus diesen Dateien importieren, um mit der Arbeit in der App zu beginnen. Weitere Informationen finden Sie unter [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BI Template** | Enthält die Power BI-Berichtsvorlagendatei (.pbit), die Sie zum Konfigurieren der Berichterstellung für Ihre Organisation verwenden. Weitere Informationen: [Gewinnen von Erkenntnissen mithilfe von Power BI-Dashboards](#get-insights-using-power-bi-dashboards)|
| **PowerShell**        | Enthält Skripts, die Sie zum Konfigurieren Ihrer mobilen Apps (Canvas-Apps) nutzen. |
| **Solution File**     | Enthält die Common Data Service-Lösungsdatei, die die Apps und Metadaten erstellt, die für die Notfallreaktions-App erforderlich sind.  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>Schritt 3: Importieren der Lösungsdatei in Ihre Umgebung

1.  Navigieren Sie zum Speicherort, an dem Sie die Bereitstellungsdatei (.zip) extrahiert haben. Sie finden den Ordner **Solution File** vor. Wir importieren die Datei der verwalteten Lösung (.zip) im Ordner **Solution File** in unsere Umgebung.

2.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

3.  Wählen Sie rechts oben Ihre Umgebung aus.

4.  Wählen Sie im linken Bereich **Lösungen** und dann **Importieren** aus.

    > [!div class="mx-imgBorder"] 
    > ![Lösung importieren](media/conf-import-solution.png "Importieren einer Lösung")

5.  Wählen Sie im Dialogfeld **Lösung importieren** die in Schritt 1 erwähnte Lösungsdatei aus, und befolgen Sie dann die Schritte im Assistenten zum Importieren der Lösung.

6.  Klicken Sie nach dem erfolgreichem Import der Lösung im Importdialogfeld auf **Schließen**.

Anschließend sehen Sie unter **Apps** neue Apps:

> [!div class="mx-imgBorder"] 
> ![Neue Apps](media/conf-apps-new-apps.png "Neue Apps")

Wählen Sie die **Admin-App** aus, um die modellgesteuerte Anwendung zu öffnen, mit der Sie die restlichen Bereitstellungseinstellungen konfigurieren können. Weitere Informationen: [Was sind modellgesteuerte Apps?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![Öffnen der Admin-App](media/conf-admin-app-open.png "Öffnen der Admin-App")

Die Admin-App verfügt über eine Reihe von Entitäten, in denen Sie Daten für Ihr Krankenhaussystem ergänzen und verwalten können. Im unteren Teil des linken Navigationsbereichs können Sie über die Bereichsauswahl einen anderen Bereich auswählen.

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation

Alle für die Notfallreaktions-App erforderlichen Daten sind im Ordner **Data Files** unter Ihrem extrahierten Bereitstellungsordner verfügbar.

Der Ordner **Data Files** enthält die folgenden Dateien und Ordner:

<table style="width:100%">
<tr>
<th>Name</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>Im Stammverzeichnis sind folgende Dateien verfügbar:
<ul>
<li>00 - Acuities Import.xlsx</li>
<li>00 - App Config Import.xlsx</li>
<li>00 - App Import.xlsx</li>
<li>00 - Request Roles Import.xlsx</li>
<li>00 - Supplies Import.xlsx</li>
</ul>
</td>
<td>Dies sind die Konfigurationsdateien, die mithilfe der Admin-App in die folgenden Entitäten importiert werden müssen:
<ul>
<li>Acuities (Pflegestufen)</li>
<li>App Config (Anwendungskonfiguration)</li>
<li>Apps</li>
<li>Request Roles (Rollen anfordern)</li>
<li>Supplies Import (Verbrauchsmaterialien importieren)</li>
</ul>
<br/>Durch Importieren von Daten in diese Entitäten werden Datensätze erstellt, die für das Funktionieren der Notfallreaktions-App erforderlich sind.
<br/>
<br/>
<strong>Achtung:</strong> Stellen Sie sicher, dass Sie die Konfigurationswerte in diesen Entitäten nicht aktualisieren. Eine Ausnahme bilden die Entitäten <strong>Apps</strong> und <strong>App Config</strong>, die später erläutert werden.</td>
</tr>
<tr>
<td>Ordner <strong>Sample Data</strong></td>
<td><p>Der Ordner enthält die Beispieldatendateien (.xlsx), die Sie importieren können, um die Beispieldaten in Ihrer Anwendung aufzufüllen. Die Dateien sind so benannt, dass sie die Reihenfolge angeben, in der die Daten in Ihre App importiert werden sollen. </p>
<p>Sie müssen Daten für die folgenden Entitäten importieren, die die Beispielstammdaten für die Notfallreaktions-App enthalten:
<ul>
<li>Systeme</li>
<li>Regionen</li>
<li>Facilities (Einrichtungen)</li>
<li>Standorte</li>
<li>Abteilungen</li>
</ul>
<p>Wenn Sie anstelle der Beispieldaten Ihre Organisationsdaten importieren möchten, können Sie die Beispieldaten in diesen Excel-Dateien durch Ihre Organisationsdaten ersetzen und dann die Daten in die App importieren.</p>
<p>Sie können Daten auch manuell in diese Entitäten eingeben. Informationen über alle diese Entitäten und Felder in diesen Entitäten finden Sie unter <a href="#manually-configure-and-manage-master-data-for-your-organization"> Manuelles Konfigurieren und Verwalten von Stammdaten für Ihre Organisation</a>.</p></td>
</tr>
<tr>
<td>Ordner <strong>Data Template File for Master Data</strong></td>
<td><p>Der Ordner enthält „leere“ Datendateien (.xlsx) für Stammentitäten, die Sie zum Auffüllen Ihrer Organisationsdaten und zum anschließenden Importieren in die App verwenden können.</p>
<p>Die Dateien sind so benannt, dass sie die Reihenfolge angeben, in der die Daten in Ihre App importiert werden sollen. Dabei handelt es sich um die gleiche Liste von Entitäten, die bereits für den Ordner <strong>Sample Data</strong> erwähnt wurde.</p>
<p>Sie können Daten auch manuell in diese Entitäten eingeben. Informationen über alle diese Entitäten und Felder in diesen Entitäten finden Sie unter <a href="#manually-configure-and-manage-master-data-for-your-organization"> Manuelles Konfigurieren und Verwalten von Stammdaten für Ihre Organisation</a>.</p>
</td>
</tr>
</table>

#### <a name="step-41-load-mandatory-configuration-data"></a>Schritt 4.1: Laden obligatorischer Konfigurationsdaten

Das Importieren der Konfigurationsdaten in die folgenden Entitäten in der Admin-App ist  **obligatorisch**, bevor Sie mit dem nächsten Schritt fortfahren:

| Bereichsname | Entitätsname| Dateiname
|-|-|-
| Standorte | Acuities (Pflegestufen) | 00 - Acuities Import.xlsx
| Verwaltung | Apps Config (App-Konfiguration) | 00 - App Config Import.xlsx
| Verwaltung | Apps | 00 - App Import.xlsx
| Staffing (Personalbedarf) | Request Roles (Rollen anfordern) | 00 - Request Roles Import.xlsx
| Standorte | Supplies (Verbrauchsmaterialien) | 00 - Supplies Import.xlsx

##### <a name="how-to-load-data-from-data-files"></a>Laden von Daten aus Datendateien

So importieren Sie Daten aus einer der Datendateien in eine Entität:

1.  Wählen Sie im linken Navigationsbereich der Admin-App eine Entität aus, in die Sie die Daten laden möchten. Klicken Sie z. B. in der Bereichsauswahl auf **Administration** (Verwaltung) und dann auf **Acuities** (Pflegestufen).

2.  Klicken Sie auf **Aus Excel importieren**, und wählen Sie dann im Ordner **Data Files** (Datendateien) die Datei **00 - Acuities Import.xlsx** aus.

    > [!div class="mx-imgBorder"]
    > ![Importieren aus Excel](media/conf-import-from-excel.png "Importieren aus Excel")

3.  Fahren Sie mit dem Import-Assistenten fort, um die Daten zu importieren.

4.  Nachdem die Daten importiert wurden, wird der importierte Datensatz in der Entität angezeigt:

    > [!div class="mx-imgBorder"] 
    > ![Entitätsdatensatz](media/conf-entity-record.png "Datensatz in der Entität nach Import")

Wiederholen Sie diese Schritte mit anderen Konfigurationsdatenentitäten.

Wenn Sie die Stammdaten manuell eingeben möchten, finden Sie weitere Informationen unter [Manuelles Konfigurieren und Verwalten von Stammdaten für Ihre Organisation](#manually-configure-and-manage-master-data-for-your-organization).

#### <a name="step-42-load-master-data"></a>Schritt 4.2: Laden von Masterdaten

Wie bereits erläutert:
- Sie können die Beispieldatendateien für Masterdatenentitäten im Ordner **Data Files/Sample Data** (Datendateien/Beispieldaten) verwenden, um die Beispieldaten in die erforderlichen Entitäten zu importieren. 

- Sie können die leeren Datendateien für Masterentitäten im Ordner **Data Files/Data Template File for Master Data** (Datendateien/Datenvorlagendatei für Masterdaten) zum Befüllen mit Ihren Organisationsdaten verwenden und die Daten dann in die erforderlichen Entitäten importieren.

Sie können später auch manuell Masterdaten hinzufügen. Weitere Informationen: [Manuelles Konfigurieren und Verwalten von Stammdaten für Ihre Organisation](#manually-configure-and-manage-master-data-for-your-organization)

### <a name="step-5-update-the-mobile-app-branding"></a>Schritt 5: Aktualisieren des Brandings der mobilen App

Sie können das App-Symbol, das Farbschema oder den Anzeigename der mobilen Apps an das Branding Ihrer Organisation anpassen.

Dazu verwenden Sie die Entitäten **App** und **App Config** im Bereich **Administration** (Verwaltung), indem Sie App-Daten und App-Konfigurationsdaten aus der im Ordner **Data Files** (Datendateien) unter dem Bereitstellungspaket verfügbaren Excel-Datei sowie aus Symboldateien im Ordner **App Icons** (App-Symbole) importieren. Eine genaue Erläuterung hierzu finden Sie unter [Schritt 2: Herunterladen des Bereitstellungspakets](#step-2-download-the-deployment-package).

> [!div class="mx-imgBorder"] 
> ![Entitäten „Apps“ und „App Config“](media/conf-app-app-config-entities.png "Entitäten „Apps“ und „App Config“")

1.  Vergewissern Sie sich, dass Sie die Konfigurationsdaten für **Apps** und **App Config**-Entitäten mithilfe der entsprechenden Dateien **App Import.xlsx** bzw. **App Config Import.xlsx** importiert haben.

1.  Nun kopieren wir die App-IDs von Canvas-Apps so, dass wir sie in die von uns importierten **Apps**-Datensätze einfügen können. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1.  Wählen Sie rechts oben Ihre Umgebung aus.

1.  Wählen Sie im linken Bereich **Apps** und dann das Auslassungszeichen (...) für eine Canvas-App gefolgt von **Details** aus.

    > [!div class="mx-imgBorder"] 
    > ![App-Details](media/conf-environments-apps-details.png "App-Details")

1.  Die App-ID wird unten im Bereich  **Details**  für die App angezeigt. Kopieren Sie die App-ID zusammen mit ihrem Namen in eine Editor-Datei.

    > [!div class="mx-imgBorder"] 
    > ![Details zur App-ID](media/conf-details-app-id.png "Details zur App-ID")

1.  Wiederholen Sie für jede Canvas-App die Schritte 4 und 5.

1.  Öffnen Sie die Admin-App, und wählen Sie im linken Navigationsbereich in der Bereichsauswahl **Administration** und dann **Apps** aus. Dadurch werden alle Canvas-App-Datensätze angezeigt, die Sie aus der Datei **App Import.xlsx** importiert haben.

    > [!div class="mx-imgBorder"] 
    > ![Admin-Apps](media/conf-admin-app-records.png "Admin-Apps")

1.  Öffnen Sie einen der App-Datensätze, indem Sie ihn auswählen. Beachten Sie, dass das Feld „Power App ID“ leer ist.

    > [!div class="mx-imgBorder"] 
    > ![Feld „Power App ID“](media/conf-powerapp-id-field.png "Feld „Power App ID“")

1.  Auf der Seite „App-Details“:

    1. Kopieren Sie die App-ID aus der Editor-Datei, in die Sie sie zuvor kopiert haben, in das Feld **Power App ID** (Power-App-ID).

    2. Doppelklicken Sie auf das App-Symbol, und wählen Sie aus dem Ordner **App-Symbole** eine Symboldatei für die App aus. Die Bilddateien werden intuitiv benannt, sodass Sie das richtige Symbol problemlos auswählen können. Wählen Sie z. B. die Datei „Emergency Response App.png“ für die **Notfallreaktions-App** aus. Sie können auch ein benutzerdefiniertes Bild auswählen, das zum Branding Ihrer Organisation passt.

    3. Aktualisieren Sie bei Bedarf die **Beschreibung** oder den **Anzeigenamen** der App.

    4. Aktualisieren Sie bei Bedarf den Wert **Hide App from Menu** (App im Menü ausblenden), mit dem Sie festlegen, ob die App in der App-Liste angezeigt werden soll. Da es sich bei der **Notfallreaktions-App** um eine Container-App handelt, ist der Standardwert **Nein**.

    5. Aktualisieren Sie bei Bedarf den Wert **App Display Rank** (App-Anzeigerang), mit dem Sie die Anzeigeposition der App in der App-Liste festlegen.

    6. Wählen Sie **Speichern**.

1.  Wiederholen Sie für jeden Canvas-App-Eintrag unter **Apps** die Schritte 8 und 9.

1.  Wählen Sie im linken Bereich **App Config** aus.

1.  Wählen Sie den Datensatz **Emergency Response App** (Notfallreaktions-App) aus, um ihn zur Bearbeitung zu öffnen.

    1.  Aktualisieren Sie bei Bedarf die Farben für Ihre App.

    2.  Wählen Sie im Feld **Device Sharing Enabled** (Gerätefreigabe aktiviert) entweder **Yes** (Ja) oder **No** (Nein) aus, um anzugeben, ob in den mobilen Apps die Option **Sign Out** (Abmelden) verfügbar sein soll oder nicht. Wenn Sie **Yes** (Ja) auswählen, ist die Option **Sign Out** (Abmelden) verfügbar.

    > [!div class="mx-imgBorder"] 
    > ![Feld „Device Sharing Enabled“](media/conf-device-sharing-enabled-field.png "Feld „Device Sharing Enabled“")

1.  Wählen Sie rechts unten **Speichern** aus, um Ihre Änderungen zu speichern.

### <a name="step-6-bypass-consent-for-mobile-apps"></a>Schritt 6: Umgehen der Zustimmung für mobile Apps

Sie müssen ein Mandantenadministrator sein, um diesen Schritt auszuführen. Bevor Sie diesen Schritt ausführen, benötigen Sie außerdem die App-ID jeder mobilen App (Canvas-App).

Um die App-ID Ihrer App abzurufen, wählen Sie im linken Navigationsbereich in der Bereichsauswahl **Administration** und dann **Apps** aus. Dadurch werden alle mobilen Apps (Canvas-Apps) angezeigt. Wählen Sie eine mobile App aus, um ihre App-ID anzuzeigen. Kopieren Sie die App-ID jeder App in eine Editor-Datei.

> [!div class="mx-imgBorder"] 
> ![Abrufen der App-ID](media/conf-admin-get-app-id.png "Abrufen der App-ID")

Gehen Sie anschließend wie folgt vor:

1.  Öffnen Sie Editor, und kopieren Sie dieses PowerShell-Skript:

    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell
    
    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount
    
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppApisToBypassConsent -AppName APPGUIDHERE
    ```

2.  Ersetzen Sie den Wert `APPGUIDHERE` durch die tatsächliche App-ID einer Canvas-App.

3.  Speichern Sie die Datei als PS-Datei.

4.  Führen Sie PowerShell als Administrator und dann die soeben erstellte PS-Datei aus.

5.  Wiederholen Sie für jede Canvas-App die Schritte 2 bis 4.

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry"></a>Schritt 7: Hinzufügen des Azure Application Insights-Schlüssels zu mobilen Apps für Telemetriezwecke

Mit Azure Application Insights können Sie detaillierte Telemetriedaten für Ihre mobilen Apps (Canvas-Apps) sammeln, um Einblicke in die App-Nutzung zu erhalten. Ausführliche Informationen hierzu finden Sie unter [Analysieren von App-Telemetriedaten mithilfe von Application Insights](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights).

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>Schritt 8: Freigeben von Canvas-Apps für Benutzer in Ihrer Organisation

Damit Ihre Benutzer an vorderster Front Daten mithilfe der Canvas-Apps auf ihren mobilen Geräten nutzen können, müssen die Apps für sie freigegeben werden. Es wird empfohlen, Azure AD-Gruppen zu verwenden, um Apps einfach für Benutzergruppen freizugeben.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie im linken Navigationsbereich **Apps** aus, um eine Liste aller Apps anzuzeigen.

3.  Wählen Sie eine mobile App (Canvas-App) und dann im Banner **Freigeben** aus.

    > [!div class="mx-imgBorder"] 
    > ![Freigeben von Canvas-Apps](media/conf-share-canvas-apps.png "Freigeben von Canvas-Apps")

4.  Geben Sie die Azure AD-Gruppe oder Benutzer an, für die Sie diese App freigeben möchten. Da sich die App mit Common Data Service-Daten verbindet, müssen Sie auch Berechtigungen für die Entitäten erteilen. Im Freigabepanel werden Sie aufgefordert, die Sicherheit für die Entitäten zu verwalten. Weisen Sie den von dieser App verwendeten Entitäten die Sicherheitsrollen **Emergency Response User** (Notfallreaktionsbenutzer) und **Common Data Service User** (Common Data Service-Benutzer) zu, und klicken Sie auf **Share** (Freigeben).

    > [!div class="mx-imgBorder"] 
    > ![Freigeben einer App für Azure AD-Gruppe oder Benutzer](media/conf-share-app-groups-users.png "Freigeben einer App für Azure AD-Gruppe oder Benutzer")

5.  Wiederholen Sie für jede mobile App die Schritte 3 und 4.

Ausführliche Informationen zur Freigabe von Apps: [Freigeben einer Canvas-App](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

### <a name="step-9-set-your-mobile-app-as-hero-and-featured-app"></a>Schritt 9: Festlegen Ihrer mobilen App als herausragende und empfohlene App

In diesem Schritt können Sie Ihre mobile App als herausragende und empfohlene App innerhalb der mobilen **Power Apps**-App festlegen. Sie müssen ein Mandantenadministrator sein, um diesen Schritt auszuführen.

Bevor Sie diesen Schritt ausführen, benötigen Sie außerdem die App-ID jeder mobilen App (Canvas-App), die Sie als herausragende und empfohlene App festlegen möchten. Informationen zum Abrufen der App-ID einer Canvas-App finden Sie unter [Schritt 6: Umgehen der Zustimmung für mobile Apps](#step-6-bypass-consent-for-mobile-apps)

Gehen Sie anschließend wie folgt vor:

1.  Öffnen Sie Editor, und kopieren Sie dieses PowerShell-Skript:


    ```powershell
    # MUST BE A TENANT ADMIN TO RUN THIS
    Install-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber
    Import-Module -Name Microsoft.PowerApps.Administration.PowerShell
    Import-Module -Name Microsoft.PowerApps.PowerShell

    # This call opens prompt to collect credentials 
    # (Azure Active Directory account and password) 
    # used by the commands
    Add-PowerAppsAccount

    # Use the "Emergency Response App" App ID
    # To clear a featured app use Clear-AdminPowerAppAsFeatured

    #Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsFeatured -AppName APPGUIDHERE

    # To clear a hero app use Clear-AdminPowerAppAsHero
    # Change the App ID for each new app (APPGUIDHERE)
    Set-AdminPowerAppAsHero -AppName APPGUIDHERE
    ```

2.  Ersetzen Sie den Wert `APPGUIDHERE` im Skript durch die tatsächliche App-ID der App, die Sie als empfohlene oder herausragende App festlegen möchten.

3.  Speichern Sie die Datei als PS-Datei.

4.  Führen Sie PowerShell als Administrator und dann die soeben erstellte PS-Datei aus.
 

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>Schritt 10: Freigeben der modellgesteuerten App für Administratoren in Ihrer Organisation

Damit Ihre administrativen Benutzer die Admin-App (modellgesteuerte App) verwenden können, muss sie für sie freigegeben werden. Es wird empfohlen, Azure AD-Gruppen zu verwenden, um Apps einfach für Gruppen administrativer Benutzer freizugeben.

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2. Wählen Sie im linken Navigationsbereich „Apps“ aus, um eine Liste aller Apps anzuzeigen.

3. Wählen Sie die modellgesteuerte App (**Admin App – Emergency Response App)** und im Banner **Freigeben** aus.

4. Geben Sie die Azure AD-Gruppe oder administrativen Benutzer an, für die Sie diese Anwendung freigeben möchten. Weisen Sie die Sicherheitsrolle **Emergency Response Admin** (Notfallreaktions-Administrator) zu, und wählen Sie **Freigeben** aus.


## <a name="manually-configure-and-manage-master-data-for-your-organization"></a>Manuelles Konfigurieren und Verwalten von Stammdaten für Ihre Organisation

Administratoren können mit der modellgesteuerten App in [Power Apps](https://make.powerapps.com) Stammdaten für ihre Organisation erstellen und verwalten. Diese Daten werden benötigt, damit die Notfallreaktions-App funktionieren kann.

> [!NOTE]
> Sie können Ihre Organisationsdaten auch in Datendateien importieren, die im Bereitstellungspaket verfügbar sind, und sie anschließend in diese Entitäten importieren. Weitere Informationen: [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization)

Sie müssen Stammdaten in diesen Entitäten in der folgenden Reihenfolge hinzufügen:

1. [Systems (Systeme)](#systems-data)

1. [Regionen](#regions-data)

1. [Facilities (Einrichtungen)](#facilities-data)

1. [Speicherorte](#locations-data)

1. [Departments (Abteilungen)](#departments-data)

Die Stammdaten werden in der Admin-App im linken Navigationsbereich im Bereich **Locations** verwaltet:

> [!div class="mx-imgBorder"]
> ![Bereich „Locations“](media/locations-area.png)

Die Entitäten unter dem Bereich **Hierarchy** (Hierarchie) sind in der Reihenfolge aufgeführt, in der Sie die Daten auffüllen müssen.

### <a name="systems-data"></a>Daten zu Systemen

Mit der Entität **Systems** können Sie Einträge für Krankenhaussysteme erstellen und verwalten. Dies ermöglicht Ihnen die Verwaltung mehrerer Krankenhaussysteme innerhalb derselben Organisation.

So erstellen Sie einen Datensatz

1. Wählen Sie im linken Bereich **Systems** und dann **New** (Neu) aus:  
    > [!div class="mx-imgBorder"]
    > ![„Systems“->„New“ auswählen](media/select-systems-new.png)

2. Geben Sie auf der Seite **New System** (Neues System) die entsprechenden Werte an:  
   > [!div class="mx-imgBorder"]
   > ![Details zum neuen System eingeben](media/enter-details-new-system.png)

   | **Feld**            | **Beschreibung**                                    |
   |----------------------|----------------------------------------------------|
   | Systemname          | Geben Sie für Ihr Krankenhaus einen Namen ein.                     |
   | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
   | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für dieses Krankenhaussystem ein. |
   | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für dieses Krankenhaussystem ein.   |

3. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Systems** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

### <a name="regions-data"></a>Daten zu Regionen

Die Entität **Regions** ermöglicht Ihnen die Verwaltung der geografischen Regionen in Ihren Krankenhaussystemen.

So erstellen Sie einen Datensatz

1. Wählen Sie im linken Bereich **Regions** und dann **New** aus.

2. Geben Sie auf der Seite **New Region** (Neue Region) die entsprechenden Werte an:  

    > [!div class="mx-imgBorder"]
    > ![Details zu neuer Region eingeben](media/enter-details-new-region.png)

    | **Feld**            | **Beschreibung**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | System               | Wählen Sie ein Krankenhaussystem aus. Diese Liste wird auf Grundlage der Daten zu den **Systemen** aufgefüllt, die Sie zuvor erstellt haben. |
    | Name der Region          | Geben Sie den Namen der Region ein. Beispiel: Seattle.                                                              |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                            |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für dieses Krankenhaussystem ein.                                                       |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für dieses Krankenhaussystem ein.                                                         |

3. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Regions** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

### <a name="facilities-data"></a>Daten zu Einrichtungen

Mithilfe der Entität **Facilities** können Sie die Krankenhausstandorte innerhalb jeder Region verwalten. Beispielsweise die Einrichtungen **Redmond** und **Bellevue** in der Region **Seattle**.

So erstellen Sie einen Datensatz

1. Wählen Sie im linken Bereich **Facilities** und dann **New** aus.

2. Geben Sie auf der Seite **New Facility** (Neue Einrichtung) die entsprechenden Werte an: 

    > [!div class="mx-imgBorder"] 
    > ![Details zu neuer Einrichtung eingeben](media/enter-details-new-facility.png)

    | **Feld**            | **Beschreibung**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Region               | Wählen Sie eine Region aus. Diese Liste wird auf Grundlage der Daten zu den **Regionen** aufgefüllt, die Sie zuvor erstellt haben. |
    | Facility Name (Name der Einrichtung)        | Geben Sie den Namen der Einrichtung ein. Beispiel: Bellevue.                                                  |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                   |
    | Total Vents (Beatmungsgeräte insgesamt)          | Geben Sie die Gesamtanzahl der in der Einrichtung verfügbaren Beatmungsgeräte ein.                                  |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für diese Einrichtung ein.                                                     |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für diese Einrichtung ein.                                                       |

    Geben Sie bei Bedarf die Adresse der Einrichtung ein.

3. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Facilities** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

### <a name="locations-data"></a>Daten zu Standorten

Mithilfe der Entität **Locations** können Sie Standorte innerhalb jeder Krankenhauseinrichtung verwalten.

> [!NOTE]
> Bevor Sie einen Datensatz des Typs **Locations** erstellen, stellen Sie sicher, dass Sie die Pflegestufendaten mithilfe der Datei **00 - Acuities Import.xlsx** importiert haben. Weitere Informationen finden Sie weiter oben in [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization). Der Grund dafür ist, dass zur Erstellung eines Datensatzes des Typs **Location** Informationen zur Pflegestufe erforderlich sind.

So erstellen Sie einen Datensatz

1. Wählen Sie im linken Bereich **Locations** und dann **New** aus.

2. Geben Sie auf der Seite **New Location** (Neuer Standort) die entsprechenden Werte an:  
 
    > [!div class="mx-imgBorder"]
    > ![Details zu neuem Standort eingeben](media/enter-details-new-location.png)

    | **Feld**            | **Beschreibung**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Standortname        | Geben Sie den Namen des Standorts ein.                                                                       |
    | Facility             | Wählen Sie eine Einrichtung aus. Diese Liste wird auf Grundlage der Daten zu den **Einrichtungen** aufgefüllt, die Sie zuvor erstellt haben. |
    | Etage                | Geben Sie die Informationen zur Etage der Einrichtung ein.                                                         |
    | Einheit                 | Geben Sie die Informationen zur Einheit der Einrichtung ein.                                                           |
    | Location Acuity (Pflegestufe am Standort)      | Wählen Sie den Datensatz zur Pflegestufe aus, der mit diesem Standort verknüpft ist.                                                                                                     |
    | Total Beds (Betten insgesamt)           | Geben Sie die Gesamtanzahl der Betten in der Einrichtung ein.                                                       |
    | Blocked beds (Belegte Betten)         | Geben Sie die Anzahl der belegten Betten in der Einrichtung ein.                                                     |
    | Last Census (Letzte Volkszählung)          | Wird basierend auf dem zuletzt erstellten Volkszählungs-Datensatz aufgefüllt.                                             |
    | Occupancy Percentage (Belegungsprozentsatz) | Wird basierend auf der letzten Volkszählung und den insgesamt belegten Betten automatisch berechnet.                                         |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für dieses Krankenhaussystem ein.                                                   |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für dieses Krankenhaussystem ein.                                                     |
    | Location Order (Standortreihenfolge)       | Geben Sie eine Zahl zum Sortieren des Standorts in die Dropdownlisten für den Standort ein.                               |
    | Alternate Site Flag (Flag für alternatives Standort)  | Zur internen Verwendung                                                                                     |

3. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Locations** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

### <a name="departments-data"></a>Daten zu Abteilungen

Mithilfe der Entität **Departments** können Sie Abteilungsinformationen für ein Krankenhaus verwalten.

So erstellen Sie einen Datensatz

1. Wählen Sie im linken Bereich **Departments** und dann **New** aus.

2. Geben Sie auf der Seite **New Department** (Neue Abteilung) die entsprechenden Werte an:    

    > [!div class="mx-imgBorder"]
    > ![Details zu neuer Abteilung eingeben](media/enter-details-new-department.png)

    | **Feld**            | **Beschreibung**                                    |
    |----------------------|----------------------------------------------------|
    | Department Name      | Geben Sie einen Abteilungsnamen ein.                            |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
    | Effective Start Data (Tatsächliches Startdatum) | Geben Sie Startdatum und -uhrzeit für dieses Krankenhaussystem ein. |
    | Effective Start End (Tatsächliches Enddatum)   | Geben Sie Enddatum und -uhrzeit für dieses Krankenhaussystem ein.   |

3. Wählen Sie **Speichern und Schließen** aus. Der neu erstellte Datensatz ist in der Liste **Departments** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie ihn aus. Aktualisieren Sie die Werte wie gewünscht, und wählen Sie **Speichern und schließen** aus.

## <a name="get-insights-using-common-data-service-dashboards"></a>Gewinnen von Erkenntnissen mithilfe von Common Data Service-Dashboards

Die folgenden Dashboards sind in der modellgesteuerten Notfallreaktions-Admin-App standardmäßig verfügbar:

- **Bed Management** (Bettenmanagement)

   Zeigt die Verfügbarkeit von Betten, die prozentuale Belegung und die Gesamtanzahl der Betten in den verschiedenen Einrichtungen.

- **Equipment and Supply** (Geräte und Verbrauchsmaterial)

  Zeigt in verschiedenen Einrichtungen in Betrieb befindliche kritische Geräte und verfügbare Verbrauchsmaterialen.

- **Staff Management** (Personalverwaltung)

  Zeigt die Anzahl der in verschiedenen Einrichtungen beantragten, zugewiesenen und verfügbaren Mitarbeiter.

- **COVID Patients** (COVID-Patienten)

  Zeigt die Anzahl der Patienten, die in verschiedenen Einrichtungen untersucht wurden und einen positiven Befund auf COVID-19 haben.

- **Discharges** (Entlassungen)

  Zeigt die Anzahl von Patienten, die voraussichtlich entlassen werden, und die tatsächliche Entlassungen.

Zusätzlich zu den standardmäßig verfügbaren Dashboards können Sie auch eigene Dashboards erstellen.

### <a name="manage-dashboards"></a>Dashboards verwalten

So verwalten Sie Dashboards

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an, und navigieren Sie zu Ihrer Admin-App.

2. Wählen Sie im linken Navigationsbereich in der Bereichsauswahl **Dashboards** aus:

    > [!div class="mx-imgBorder"]
    > ![Dashboards auswählen](media/select-dashboards.png)

3. Wählen Sie im linken Navigationsbereich einen Dashboardnamen aus, um die Diagramme anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Diagramme anzeigen](media/view-charts.png)

    > [!NOTE]
    > Wenn Sie die Daten unten auf dem Bildschirm filtern, werden die Diagramme oben automatisch mit gefilterten Werten aktualisiert.

4. Wählen Sie die Option **Erweitern** aus, um ein Diagramm im Vollbildmodus anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![„Erweitern“ auswählen](media/select-expand.png)

### <a name="additional-analysis"></a>Zusätzliche Analyse

- **Drilldown**: Sie können einen Diagrammbereich auswählen, um weitere Attribute (Felder) für eine Entität genauer zu untersuchen:

    > [!div class="mx-imgBorder"]
    > ![Drilldown für Diagrammbereich auswählen](media/select-chart-area-drill-down.png)

- **Aktualisieren:** Sie können die Dashboards aktualisieren und dadurch auf den neuesten Stand bringen. Sie können entweder alle Diagramme auf einem bestimmten Dashboard mit **Alle aktualisieren** oder ein ausgewähltes Diagramm mit **Aktualisieren** aktualisieren:

    > [!div class="mx-imgBorder"]
    > ![Dashboards aktualisieren](media/refresh-dashboards.png)

- **Datensätze anzeigen**: Wählen Sie **Weitere Befehle** ( **...** ) und dann **Datensätze anzeigen** aus, um alle mit einem bestimmten Diagramm verknüpften Datensätze anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![„Weitere Befehle“ auswählen](media/select-more-commands.png)

    > [!NOTE] 
    > Wenn Sie **Datensätze anzeigen** auswählen, sehen Sie eine zwischen dem Diagramm und den Datensätzen aufgeteilte Ansicht der Entität. Jede Änderung der Filter für Datensätze auf der rechten Seite wird durch automatische Aktualisierungen des Diagramms auf der linken Seite des Bildschirms widergespiegelt.

Weitere Informationen zum Bearbeiten eines bestehenden Dashboards und Aktualisieren der Eigenschaften von Diagrammen finden Sie unter [Bearbeiten eines bestehenden Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Erstellen neuer Dashboards

Sie können auch Ihre eigenen Dashboards erstellen und an Ihre Anforderungen anpassen. Um ein neues Dashboard zu erstellen, wählen Sie **Neu** und danach **Dynamics 365-Dashboard** aus:

> [!div class="mx-imgBorder"]
> ![Neues Dynamics-Dashboard auswählen](media/select-new-dynamics-dashboard.png)

Weitere Informationen zum Erstellen eines neuen Dashboards finden Sie unter [Erstellen eines neuen Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="get-insights-using-power-bi-dashboards"></a>Gewinnen von Erkenntnissen mithilfe von Power BI-Dashboards

Veröffentlichen Sie das Power BI-Dashboard, und geben Sie es für Benutzer in Ihrer Organisation frei, damit diese anhand des Dashboards Erkenntnisse gewinnen und Entscheidungen treffen können.

### <a name="prerequisites"></a>Voraussetzungen

- Power BI Premium-Kapazität- oder Power BI Pro-Lizenzen, die Benutzern zugewiesen sind, die auf den Bericht zugreifen. 

- Erstellung eines Arbeitsbereichs in Power BI, in dem Sie den Bericht veröffentlichen. Melden Sie sich bei Power BI an, und erstellen Sie einen Arbeitsbereich. Weitere Informationen: [Erstellen der neuen Arbeitsbereiche in Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Installation von Power BI Desktop über den Microsoft Store: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Wenn Sie bisher Power BI durch direktes Herunterladen von der Power BI-Website als ausführbare Datei installiert haben, entfernen Sie es und, verwenden Sie die Version aus dem Microsoft Store. Die Microsoft Store-Version wird automatisch aktualisiert, sobald neue Releases verfügbar sind.

- Nachdem Sie Power BI Desktop über den Microsoft Store installiert haben, führen Sie es aus. Melden Sie sich mit einem Konto an, das die Berechtigung hat, Power BI-Anwendungen in Ihrer Organisation zu veröffentlichen.

### <a name="publish-the-power-bi-dashboard"></a>Veröffentlichen des Power BI-Dashboards

1. Wechseln Sie zum Speicherort, an dem Sie das Bereitstellungspaket extrahiert haben. Sie finden die Datei **Emergency Response App.pbit** im Ordner **Power BI Template**.

2. Öffnen Sie die Datei **Emergency Response App.pbit** in Power BI Desktop. Wenn diese Datei in Power BI Desktop geöffnet wird, sehen Sie das Dialogfeld **Aktualisieren**, das angibt, dass die Datenaktualisierung fehlgeschlagen ist. Der Grund dafür ist, dass wir die Details der Verbindung mit Ihrer Common Data Service-Umgebung noch nicht festgelegt haben.

3. Wählen Sie **Daten transformieren** aus, um die Verbindung mit Ihrer Common Data Service-Umgebung anzugeben.  
    
    > [!div class="mx-imgBorder"]
    > ![„Daten transformieren“ auswählen](media/select-transform-data.png)

4. Aktualisieren Sie im Abfrage-Editor den Parameter **CDSBaseURL** mit der URL Ihrer Common Data Service-Umgebung. Klicken Sie mit der rechten Maustaste auf **CDSBaseURL**, wählen Sie **Erweiterter Editor** aus, und geben Sie dann den entsprechenden Wert an.  

    > [!div class="mx-imgBorder"]
    > ![„Erweiterter Editor“ auswählen](media/select-advanced-editor.png)

5. Speichern Sie die Änderungen. Daraufhin wird eine Meldung angezeigt, in der Sie aufgefordert werden, ausstehende Änderungen an Ihrer Abfrage zu übernehmen. Klicken Sie auf **Übernehmen**.

6. Sie werden aufgefordert, Anmeldeinformationen einzugeben, um sich mit Ihrer Common Data Service-Umgebung zu verbinden. Wählen Sie **Organisationskonto** > **Anmelden** aus, um Ihre Common Data Service-Anmeldeinformationen anzugeben.  

    > [!div class="mx-imgBorder"]
    > ![Organisationskonto auswählen](media/select-organizational-account.png)

7. Wählen Sie **Verbinden** aus, um eine Verbindung herzustellen.

8. Bei erfolgreicher Verbindung werden Sie aufgefordert, die Datei als PBIX-Datei zusammen mit den Informationen zu Ihrer Common Data Service-Umgebung zu speichern. Geben Sie einen Namen an, und speichern Sie sie auf Ihrem Computer.

9. Wählen Sie auf der Registerkarte **Start** den Befehl **Schließen und übernehmen** aus.

10. Wählen Sie **Aktualisieren** aus, um die Daten in Ihrer Common Data Service-Umgebung zu aktualisieren. Wählen Sie **Veröffentlichen** aus, um Daten in Ihrem Power BI-Arbeitsbereich zu veröffentlichen.  
    
    > [!div class="mx-imgBorder"]
    > ![„Veröffentlichen“ auswählen](media/select-refresh-publish.png)

11. Wählen Sie auf der Seite **In Power BI veröffentlichen** den Arbeitsbereich aus, in dem die Veröffentlichung erfolgen soll.

12. Der Bericht wird in Ihrem Arbeitsbereich verfügbar. Nun konfigurieren wir die Datenaktualisierung für das Dataset. Wählen Sie das Dataset in Ihrem Arbeitsbereich und das Symbol **Zeitplan aktualisieren** aus.  
    
    > [!div class="mx-imgBorder"]
    > ![Zeitplan aktualisieren](media/schedule-refresh.png)

13. Erweitern Sie auf der Einstellungsseite für Ihren Datensatz **Anmeldeinformationen für die Datenquelle**. Wählen Sie **Anmeldeinformationen bearbeiten** aus, um sicherzustellen, dass die Details zur Herstellung der Verbindung mit Ihrer Datenquelle zutreffend sind.  

    > [!div class="mx-imgBorder"]
    > ![„Anmeldeinformationen bearbeiten“ auswählen](media/select-edit-credentials.png)

14. Erweitern Sie **Geplante Aktualisierung**, und geben Sie die erforderlichen Details für die Aktualisierung von Daten auf Grundlage eines Zeitplans an.

    > [!NOTE] 
    > Es gibt Beschränkungen, wie oft Daten aktualisiert werden können. Power BI begrenzt Datasets auf gemeinsam genutzter Kapazität auf acht tägliche Aktualisierungen. Wenn das Dataset sich auf einer Premium-Kapazität befindet, können Sie in den Dataseteinstellungen bis zu 48 Aktualisierungen pro Tag planen. Weitere Informationen: [Aktualisieren von Daten](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

15. Wählen Sie im linken Bereich den Namen Ihres Arbeitsbereichs und dann rechts oben **App erstellen** aus.  

    > [!div class="mx-imgBorder"]
    > ![„App erstellen“ auswählen](media/select-create-app.png)

16. Auf der Seite zum Veröffentlichen der App:

    1. Geben Sie auf der Registerkarte **Setup** den Namen und die Beschreibung Ihrer App an.

    2. Geben Sie auf der Registerkarte **Navigation** den Speicherort des Dashboards an, über den es veröffentlicht wird.

    3. Geben Sie auf der Registerkarte **Berechtigungen** Benutzer oder Gruppen an, die diese App anzeigen können. Stellen Sie sicher, dass Sie das Kontrollkästchen **Diese Anwendung automatisch installieren** aktivieren, um diese Anwendung automatisch für Endbenutzer zu installieren. Weitere Informationen: [Automatisches Installieren von Apps für Endbenutzer](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![„Apps automatisch installieren“ auswählen](media/select-install-apps-automatically.png)

17. Wählen Sie **App veröffentlichen** aus. Ausführliche Informationen zum Veröffentlichen von Apps in Power BI finden Sie unter [Veröffentlichen Ihrer App](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).

### <a name="view-the-power-bi-dashboard"></a>Anzeigen des Power BI-Dashboards

Melden Sie sich bei [Power BI](https://apps.powerbi.com) an, um auf das Power BI-Dashboard zuzugreifen und es anzuzeigen.

> [!div class="mx-imgBorder"]
> ![Power BI-Dashboard anzeigen](media/view-power-dashboard.png)

## <a name="view-and-manage-app-feedback"></a>Anzeigen und Verwalten von Feedback zur App

Das gesamte Feedback, das von Mitarbeitern an vorderster Front mithilfe von Canvas-Apps auf ihren mobilen Geräten gegeben wird, wird in der Entität **App-Feedback** gespeichert. Administratoren können es im linken Navigationsbereich der Admin-App im Bereich **Administration** einsehen und verwalten.

So wird Feedback zur App angezeigt und verwaltet

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an, und navigieren Sie zu Ihrer Admin-App.

2. Wählen Sie im linken Navigationsbereich in der Bereichsauswahl **Administration** aus:

3. Wählen Sie **App-Feedback** aus, um eine Liste des von Benutzern übermittelten Feedbacks zur App anzuzeigen. Sie können auf einen Datensatz klicken, um Details anzuzeigen und als überprüft zu markieren.  

    > [!div class="mx-imgBorder"]
    > ![„App-Feedback“ auswählen](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Issues und Feedback

- Wenn Sie ein Issue mit der Beispiel-App für die Notfallreaktion melden möchten, besuchen Sie <https://aka.ms/emergency-response-issues>.

- Wenn Sie Feedback zur Beispiel-App für die Notfallreaktion geben möchten, besuchen Sie <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Nächster Schritt

[Verwenden der Notfallreaktions-App](use.md)

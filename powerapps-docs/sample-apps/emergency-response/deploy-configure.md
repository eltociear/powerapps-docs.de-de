---
title: Bereitstellen der Notfallreaktions-App für Krankenhäuser | Microsoft-Dokumentation
description: Detaillierte Anweisungen für IT-Administratoren von Krankenhäusern für die Bereitstellung und Konfiguration der Beispielanwendung in ihrer Organisation.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/15/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 132276b88fe23e9ea4a69caeff330c10f7d32daf
ms.sourcegitcommit: 371fb08328f88f8bae7335db413d52b5c961c3e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544013"
---
# <a name="deploy-the-hospital-emergency-response-app"></a>Bereitstellen der Notfallreaktions-App für Krankenhäuser

Die Notfallreaktions-App für Krankenhäuser erfordert ein geringes Maß an Einrichtung, um sie an Ihre Anforderungen anzupassen. Dieser Artikel enthält detaillierte Anweisungen für IT-Administratoren von Krankenhäusern für die Bereitstellung und Konfiguration der Anwendung in ihrer Organisation.

Geschätzte Dauer: **35-40 Minuten**.

## <a name="demo-deploy-the-hospital-emergency-response-app"></a>Demo: Bereitstellen der Notfallreaktions-App für Krankenhäuser

Sehen Sie sich an, wie Sie die Notfallreaktions-App für Krankenhäuser bereitstellen und konfigurieren können.

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="service-urls-for-us-government-customers"></a>Dienst-URLs für Kunden in US-Regierungsbehörden

Die Notfallreaktionslösung für Krankenhäuser steht auch Kunden in US-Regierungsbehörden zur Verfügung. Es gibt eine andere Gruppe von URLs für den Zugriff auf Power Apps für US-Regierungsbehörden und Power BI als in der kommerziellen Version.

In diesem Artikel wird die kommerzielle Version der Dienst-URL verwendet. Wenn Sie Kunde in einer Kunden in einer US-Regierungsbehörde sind, verwenden Sie für Ihre Bereitstellung die entsprechende URL für Kunden in US-Regierungsbehörden, wie im Folgenden gezeigt:


| **URL der kommerziellen Version**                | **URL der Version für Kunden in US-Regierungsbehörden**  |
|-------------------------------------------|--------------------------------|
| https://make.powerapps.com                | https://make.gov.powerapps.us (GCC)<br/><br/>https://make.high.powerapps.us (GCC High)                |
| https://admin.powerplatform.microsoft.com | https://gcc.admin.powerplatform.microsoft.us (GCC)<br/><br/>https://high.admin.powerplatform.microsoft.us (GCC High) |
| https://app.powerbi.com/                  | <https://app.powerbigov.us> (GCC)<br/><br/>https://app.high.powerbigov.us (GCC High)                  |

Ausführliche Informationen zu den Plänen für Kunden in US-Regierungsbehörden für Power Apps und Power BI finden Sie unter:
- [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI für Angehörige von US-Behörden](https://docs.microsoft.com/power-bi/service-govus-overview)


## <a name="deploy-the-hospital-emergency-response-app"></a>Bereitstellen der Notfallreaktions-App für Krankenhäuser

Führen Sie die folgenden Schritte aus, um die Beispiel-App für die Notfallreaktion für Krankenhäuser in Ihrer Organisation bereitzustellen.

- [Schritt 1: Registrieren für Power Apps und Erstellen einer Umgebung](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [Schritt 2: Herunterladen des Bereitstellungspakets](#step-2-download-the-deployment-package)
- [Schritt 3: Importieren der Lösungsdatei in Ihre Umgebung](#step-3-import-the-solution-file-into-your-environment)
- [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization)
    - [Schritt 4.1: Laden obligatorischer Konfigurationsdaten](#step-41-load-mandatory-configuration-data)
    - [Schritt 4.2: Laden von Masterdaten](#step-42-load-master-data)
- [Schritt 5: Aktualisieren des Brandings der mobilen App](#step-5-update-the-mobile-app-branding)
- [Schritt 6: Umgehen der Zustimmung für mobile Apps](#step-6-bypass-consent-for-mobile-apps)
- [Schritt 7: Hinzufügen des Azure Application Insights-Schlüssels zu mobilen Apps für Telemetriezwecke (optional)](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional)
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

Laden Sie das neueste Bereitstellungspaket (.zip) von <https://aka.ms/emergency-response-solution> herunter, das die Lösungsdatei, Images und Datendateien enthält, um die Apps und Geschäftslogik für die Notfallreaktions-App für Krankenhäuser einzurichten.

> [!IMPORTANT]
> Stellen Sie vor dem Extrahieren des Bereitstellungspakets (ZIP-Datei) sicher, dass Sie die Datei entsperren. So erfolgt das Entsperren
> 1. Klicken Sie mit der rechten Maustaste auf die ZIP-Datei, und wählen Sie **Eigenschaften** aus.
> 2. Wählen Sie im Dialogfeld Eigenschaften **Blockierung aufheben** und dann nacheinander **Übernehmen** und **OK** aus.

<br/>

Nachdem Sie die Bereitstellungsdatei (ZIP-Datei) entsperrt haben, extrahieren Sie sie an einen Speicherort auf Ihrem Computer. Der extrahierte Ordner enthält die folgenden Ordner:

| **Ordner/Datei**       | **Beschreibung**  |
|-----------------------|------------------|
| **App Icons**         | Enthält die Standard-App-Symbole für die mobilen Apps (Canvas-Apps)|
| **Data Files**        | Enthält die Stamm- und Beispieldatendateien (. xlsx), damit die Lösung/App funktioniert. Sie können Daten aus diesen Dateien importieren, um mit der Arbeit in der App zu beginnen. Weitere Informationen finden Sie unter [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BI Template** | Enthält die Power BI-Berichtsvorlagendatei (.pbit), die Sie zum Konfigurieren der Berichterstellung für Ihre Organisation verwenden. Weitere Informationen: [Veröffentlichen des Power BI-Dashboards](#publish-the-power-bi-dashboard)|
| **PowerShell**        | Enthält Skripts, die Sie zum Konfigurieren Ihrer mobilen Apps (Canvas-Apps) nutzen. |
| **Solution File**     | Enthält die Common Data Service-Lösungsdatei, die die Apps und Metadaten erstellt, die für die Notfallreaktions-App für Krankenhäuser erforderlich sind.  |

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

Alle für die Notfallreaktions-App für Krankenhäuser erforderlichen Daten sind im Ordner **Data Files** unter Ihrem extrahierten Bereitstellungsordner verfügbar.

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
<br/>Durch Importieren von Daten in diese Entitäten werden Datensätze erstellt, die für das Funktionieren der Notfallreaktions-App für Krankenhäuser erforderlich sind.
<br/>
<br/>
<strong>Achtung:</strong> Stellen Sie sicher, dass Sie die Konfigurationswerte in diesen Entitäten nicht aktualisieren. Eine Ausnahme bilden die Entitäten <strong>Apps</strong> und <strong>App Config</strong>, die später erläutert werden.</td>
</tr>
<tr>
<td>Ordner <strong>Sample Data</strong></td>
<td><p>Der Ordner enthält die Beispieldatendateien (.xlsx), die Sie importieren können, um die Beispieldaten in Ihrer Anwendung aufzufüllen. Die Dateien sind so benannt, dass sie die Reihenfolge angeben, in der die Daten in Ihre App importiert werden sollen. </p>
<p>Importieren Sie Daten für die folgenden Entitäten, die die Beispielstammdaten für die Notfallreaktions-App für Krankenhäuser enthalten:
<ul>
<li>Systeme</li>
<li>Regionen</li>
<li>Facilities (Einrichtungen)</li>
<li>Standorte</li>
<li>Abteilungen</li>
</ul>
<p>Wenn Sie anstelle der Beispieldaten Ihre Organisationsdaten importieren möchten, können Sie die Beispieldaten in diesen Excel-Dateien durch Ihre Organisationsdaten ersetzen und dann die Daten in die App importieren.</p>
<p>Sie können Daten auch manuell in diese Entitäten eingeben. Informationen über all diese Entitäten und Felder in diesen Entitäten finden Sie unter <a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">Konfigurieren und Verwalten von Masterdaten für Ihre Organisation</a>.</p></td>
</tr>
<tr>
<td>Ordner <strong>Data Template File for Master Data</strong></td>
<td><p>Der Ordner enthält „leere“ Datendateien (.xlsx) für Stammentitäten, die Sie zum Auffüllen Ihrer Organisationsdaten und zum anschließenden Importieren in die App verwenden können.</p>
<p>Die Dateien sind so benannt, dass sie die Reihenfolge angeben, in der die Daten in Ihre App importiert werden sollen. Dabei handelt es sich um die gleiche Liste von Entitäten, die bereits für den Ordner <strong>Sample Data</strong> erwähnt wurde.</p>
<p>Sie können Daten auch manuell in diese Entitäten eingeben. Informationen über all diese Entitäten und Felder in diesen Entitäten finden Sie unter <a href="configure-data-reporting.md#configure-and-manage-master-data-for-your-organization">Konfigurieren und Verwalten von Masterdaten für Ihre Organisation</a>.</p>
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

Wenn Sie die Masterdaten manuell eingeben möchten, finden Sie weitere Informationen unter [Konfigurieren und Verwalten von Masterdaten für Ihre Organisation](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization).

#### <a name="step-42-load-master-data"></a>Schritt 4.2: Laden von Masterdaten

Wie bereits erläutert:
- Sie können die Beispieldatendateien für Masterdatenentitäten im Ordner **Data Files/Sample Data** (Datendateien/Beispieldaten) verwenden, um die Beispieldaten in die erforderlichen Entitäten zu importieren. 

- Sie können die leeren Datendateien für Masterentitäten im Ordner **Data Files/Data Template File for Master Data** (Datendateien/Datenvorlagendatei für Masterdaten) zum Befüllen mit Ihren Organisationsdaten verwenden und die Daten dann in die erforderlichen Entitäten importieren.

Sie können später auch manuell Masterdaten hinzufügen. Weitere Informationen: [Konfigurieren und Verwalten von Masterdaten für Ihre Organisation](configure-data-reporting.md#configure-and-manage-master-data-for-your-organization)

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

1.  Öffnen Sie einen der App-Datensätze, indem Sie ihn auswählen. Beachten Sie, dass das Feld **Power App ID** leer ist.

    > [!div class="mx-imgBorder"] 
    > ![Feld „Power App ID“](media/conf-powerapp-id-field.png "Aktualisieren der App-Informationen")

1.  Auf der Seite „App-Details“:

    1. Kopieren Sie die App-ID aus der Editor-Datei, in die Sie sie zuvor kopiert haben, in das Feld **Power App ID** (Power-App-ID).

    2. Doppelklicken Sie auf das App-Symbol, und wählen Sie aus dem Ordner **App-Symbole** eine Symboldatei für die App aus. Die Bilddateien werden intuitiv benannt, sodass Sie das richtige Symbol problemlos auswählen können. Wählen Sie z. B. die Datei „Emergency Response App.png“ für die **Notfallreaktions-App** aus. Sie können auch ein benutzerdefiniertes Bild auswählen, das zum Branding Ihrer Organisation passt.

    3. Aktualisieren Sie bei Bedarf die **Beschreibung** oder den **Anzeigenamen** der App.

    4. Aktualisieren Sie bei Bedarf den Wert **Hide App from Menu** (App im Menü ausblenden), mit dem Sie festlegen, ob die App in der App-Liste angezeigt werden soll. Da es sich bei der **Notfallreaktions-App** um eine Container-App handelt, ist der Standardwert **Nein**.

    5. Aktualisieren Sie bei Bedarf den Wert **App Display Rank** (App-Anzeigerang), mit dem Sie die Anzeigeposition der App in der App-Liste festlegen.

    6. Wählen Sie ggf. einen Wert im Feld **Tracking Level** (Nachverfolgungsebene) aus, um anzugeben, ob Sie Daten in dieser mobilen App auf Ebene eines **Standorts** oder einer **Einrichtung** nachverfolgen möchten. Weitere Informationen: [Verwalten der Nachverfolgungsebene für mobile Apps](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

    7. Wählen Sie **Speichern**.

1.  Wiederholen Sie für jeden Canvas-App-Eintrag unter **Apps** die Schritte 8 und 9.

1.  Wählen Sie im linken Bereich **App Config** aus.

1.  Wählen Sie den Datensatz **Emergency Response App** (Notfallreaktions-App) aus, um ihn zur Bearbeitung zu öffnen.

    1.  Aktualisieren Sie bei Bedarf die Farben Ihrer App.

    2.  Wählen Sie im Feld **Device Sharing Enabled** (Gerätefreigabe aktiviert) entweder **Yes** (Ja) oder **No** (Nein) aus, um anzugeben, ob in mobilen Apps die Option **Sign Out** (Abmelden) verfügbar sein soll oder nicht. Wenn Sie **Yes** (Ja) auswählen, ist die Option **Sign Out** (Abmelden) verfügbar. Weitere Informationen: [Abmelden bei Schichtende](use.md#end-shift---sign-out) im Benutzerhandbuch

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

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional"></a>Schritt 7: Hinzufügen des Azure Application Insights-Schlüssels zu mobilen Apps für Telemetriezwecke (optional)

Mit Azure Application Insights können Sie optional detaillierte Telemetriedaten für Ihre mobilen Apps (Canvas-Apps) sammeln, um Einblicke in die App-Nutzung zu erhalten. Ausführliche Informationen hierzu finden Sie unter [Analysieren von App-Telemetriedaten mithilfe von Application Insights](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights).

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>Schritt 8: Freigeben von Canvas-Apps für Benutzer in Ihrer Organisation

Damit Ihre Benutzer an vorderster Front Daten mithilfe der Canvas-Apps auf ihren mobilen Geräten nutzen können, müssen die Apps für sie freigegeben werden. Es wird empfohlen, Azure AD-Gruppen zu verwenden, um Apps einfach für Benutzergruppen freizugeben.

> [!IMPORTANT]
> Stellen Sie sicher, dass die Benutzer oder Gruppen, für die Sie die Apps freigeben möchten, *bereits* Zugriff auf Ihre Umgebung haben. In der Regel haben Sie bei der [Einrichtung der Umgebung](#step-1-sign-up-for-power-apps-and-create-an-environment) bereits Benutzer oder Gruppen hinzugefügt. Alternativ können Sie die hier beschriebenen Schritte befolgen, um Ihrer Umgebung Benutzer hinzuzufügen und diesen den entsprechenden Zugriff zu erteilen, bevor Sie Apps für sie freigeben: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

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

> [!IMPORTANT]
> Stellen Sie sicher, dass die Benutzer oder Gruppen, für die Sie die App freigeben möchten, *bereits* Zugriff auf Ihre Umgebung haben. In der Regel haben Sie bei der [Einrichtung der Umgebung](#step-1-sign-up-for-power-apps-and-create-an-environment) bereits Benutzer oder Gruppen hinzugefügt. Alternativ können Sie die hier beschriebenen Schritte befolgen, um Ihrer Umgebung Benutzer hinzuzufügen und diesen den entsprechenden Zugriff zu erteilen, bevor Sie eine App für sie freigeben: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2. Wählen Sie im linken Navigationsbereich „Apps“ aus, um eine Liste aller Apps anzuzeigen.

3. Wählen Sie die modellgesteuerte App (**Admin App – Emergency Response App)** und im Banner **Freigeben** aus.

4. Geben Sie die Azure AD-Gruppe oder administrativen Benutzer an, für die Sie diese Anwendung freigeben möchten. Weisen Sie die Sicherheitsrolle **Emergency Response Admin** (Notfallreaktions-Administrator) zu, und wählen Sie **Freigeben** aus.

## <a name="publish-the-power-bi-dashboard"></a>Veröffentlichen des Power BI-Dashboards

Veröffentlichen Sie das Power BI-Dashboard, und geben Sie es für Benutzer in Ihrer Organisation frei, damit diese anhand des Dashboards Erkenntnisse gewinnen und Entscheidungen treffen können.

Sie können das Power BI-Dashboard über eine der folgenden Optionen veröffentlichen: mit der Vorlagen-App aus AppSource *oder* mit der **PBIT**-Datei, die Sie im Bereitstellungspaket finden.

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>Option A: Veröffentlichen mithilfe der Vorlagen-App aus AppSource (bevorzugte Option)

Detaillierte Informationen zum Verwenden der Vorlagen-App aus AppSource finden Sie hier: [Herstellen einer Verbindung mit dem Supportdashboard für Notfalleinsätze im Krankenhaus](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-health-emergency-response)

> [!IMPORTANT]
> Dies ist eine einfachere Möglichkeit zum Veröffentlichen des Power BI-Dashboards als die Verwendung einer PBIT-Datei. Wir empfehlen Kunden, diese Option zu nutzen, anstatt die Veröffentlichung mit der PBIT-Option durchzuführen. 

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>Option B: Veröffentlichen mithilfe der PBIT-Datei im Bereitstellungspaket

Dieser Abschnitt bietet Informationen dazu, wie Sie die Datei **Emergency Response App.pbit** verwenden, die Sie im Bereitstellungspaket finden, um das Dashboard zu veröffentlichen.

#### <a name="prerequisites"></a>Voraussetzungen

- Power BI Premium-Kapazität- oder Power BI Pro-Lizenzen, die Benutzern zugewiesen sind, die auf den Bericht zugreifen. 

- Erstellung eines Arbeitsbereichs in Power BI, in dem Sie den Bericht veröffentlichen. Melden Sie sich bei Power BI an, und erstellen Sie einen Arbeitsbereich. Weitere Informationen: [Erstellen der neuen Arbeitsbereiche in Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Installation von Power BI Desktop über den Microsoft Store: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Wenn Sie Power BI Desktop bislang direkt von der Download-Center-Seite als ausführbare Datei heruntergeladen und installiert haben, entfernen Sie diese Datei, und verwenden Sie diejenige aus dem Microsoft Store. Die Microsoft Store-Version wird automatisch aktualisiert, sobald neue Releases verfügbar sind.
   >
   > Wenn die Installation nicht über den Microsoft Store möglich ist, installieren Sie die neueste Nicht-Microsoft Store-Version über die [Download Center-Seite](https://www.microsoft.com/download/details.aspx?id=58494).

- Nachdem Sie Power BI Desktop über den Microsoft Store installiert haben, führen Sie es aus. Melden Sie sich mit einem Konto an, das die Berechtigung hat, Power BI-Anwendungen in Ihrer Organisation zu veröffentlichen.

#### <a name="publish-the-dashboard-using-the-pbit-file"></a>Veröffentlichen des Dashboards mithilfe der PBIT-Datei

1. Wechseln Sie zum Speicherort, an dem Sie das Bereitstellungspaket extrahiert haben. Sie finden die Datei **Emergency Response App.pbit** im Ordner **Power BI Template**.

2. Öffnen Sie die Datei **Emergency Response App.pbit** in Power BI Desktop. Sie werden aufgefordert, die folgenden Informationen einzugeben:

    - **Organization_name**: Geben Sie den Namen Ihrer Organisation ein, der links oben auf jeder Berichtsseite angezeigt wird.
    - **CDS_base_solution_URL**: Geben Sie die URL Ihrer Common Data Service-Umgebungsinstanz ein. Beispiel: https:// *[myenv]* .crm.dynamics.com

    > [!div class="mx-imgBorder"]
    > ![Organisationsnamen und Basis-URL angeben](media/pbi-pub-rep1.png)

    Wählen Sie **Laden** aus.

3. Sie werden aufgefordert, Anmeldeinformationen einzugeben, um sich mit Ihrer Common Data Service-Umgebung zu verbinden. Wählen Sie **Organisationskonto** > **Anmelden** aus, um Ihre Common Data Service-Anmeldeinformationen anzugeben.  

    > [!div class="mx-imgBorder"]
    > ![Organisationskonto auswählen](media/select-organizational-account.png)

4. Wählen Sie nach der Anmeldung **Verbinden** aus, um eine Verbindung mit Ihren Daten in Common Data Service herzustellen.

5. Bei erfolgreichem Verbindungsaufbau werden Ihre Daten im Power BI-Bericht angezeigt. Sie werden aufgefordert, ausstehende Änderungen an Ihrer Abfrage zu übernehmen. Wählen Sie **Änderungen übernehmen** aus.

6. Wählen Sie **Veröffentlichen** aus, um Daten in Ihrem Power BI-Arbeitsbereich zu veröffentlichen. Sie werden aufgefordert, die Änderungen zu speichern. Wählen Sie **Speichern** aus.

    > [!div class="mx-imgBorder"]
    > ![„Veröffentlichen“ auswählen](media/select-refresh-publish.png)

7. Sie werden aufgefordert, die Datei als PBIX-Datei zusammen mit den Informationen zu Ihrer Common Data Service-Umgebung zu speichern. Geben Sie einen Namen an, und speichern Sie sie auf Ihrem Computer.

8. Nachdem Sie die PBIX-Datei gespeichert haben, werden Sie aufgefordert, den Bericht zu veröffentlichen. Wählen Sie auf der Seite **In Power BI veröffentlichen** den Arbeitsbereich aus, in dem die Veröffentlichung erfolgen soll, und klicken Sie auf **Auswählen**.

12. Der Bericht wird in Ihrem Arbeitsbereich verfügbar. Nun konfigurieren wir die Datenaktualisierungseinstellungen für das Dataset. Wählen Sie das Dataset in Ihrem Arbeitsbereich und das Symbol **Zeitplan aktualisieren** aus.  
    
    > [!div class="mx-imgBorder"]
    > ![Zeitplan aktualisieren](media/schedule-refresh.png)

13. Wenn Sie zum ersten Mal versuchen, die Datenaktualisierungseinstellung festzulegen, wird die Seite **Einstellungen** mit der Meldung angezeigt, dass Ihre Anmeldedaten ungültig sind. Wählen Sie unter **Anmeldeinformationen für die Datenquelle** die Option **Anmeldeinformationen bearbeiten** aus, um Ihre Anmeldeinformation anzugeben.  

    > [!div class="mx-imgBorder"]
    > ![„Anmeldeinformationen bearbeiten“ auswählen](media/select-edit-credentials.png)

14. Gehen Sie auf dem nächsten Bildschirm so vor:
    - Wählen Sie **OAuth2** als **Authentifizierungsmethode** aus.
    - Wählen Sie **Organisation** als **Datenschutzebene für diese Datenquelle** aus.
    - Wählen Sie **Anmelden**.

    Sie werden aufgefordert, Ihre Anmeldeinformationen anzugeben und sich anzumelden. Nach erfolgreicher Anmeldung gelangen Sie zurück zur Seite **Einstellungen**.

15. Erweitern Sie auf der Seite **Einstellung** den Eintrag **Geplante Aktualisierung**, und geben Sie die erforderlichen Details für die Aktualisierung von Daten auf Grundlage eines Zeitplans an. Klicken Sie auf **Übernehmen**.

    > [!div class="mx-imgBorder"]
    > ![Geplante Aktualisierung](media/refresh-schedule.png)

    > [!NOTE] 
    > Es gibt Beschränkungen, wie oft Daten aktualisiert werden können. Power BI begrenzt Datasets auf gemeinsam genutzter Kapazität auf acht tägliche Aktualisierungen. Wenn das Dataset sich auf einer Premium-Kapazität befindet, können Sie in den Dataseteinstellungen bis zu 48 Aktualisierungen pro Tag planen. Weitere Informationen: [Aktualisieren von Daten](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

16. Wählen Sie im linken Bereich den Namen Ihres Arbeitsbereichs und dann rechts oben **App erstellen** aus.  

    > [!div class="mx-imgBorder"]
    > ![„App erstellen“ auswählen](media/select-create-app.png)

17. Auf der Seite zum Veröffentlichen der App:

    1. Geben Sie auf der Registerkarte **Setup** den Namen und die Beschreibung Ihrer App an.

    2. Geben Sie auf der Registerkarte **Navigation** den Speicherort des Dashboards an, über den es veröffentlicht wird.

    3. Geben Sie auf der Registerkarte **Berechtigungen** Benutzer oder Gruppen an, die diese App anzeigen können. Stellen Sie sicher, dass Sie das Kontrollkästchen **Diese Anwendung automatisch installieren** aktivieren, um diese Anwendung automatisch für Endbenutzer zu installieren. Weitere Informationen: [Automatisches Installieren von Apps für Endbenutzer](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![„Apps automatisch installieren“ auswählen](media/select-install-apps-automatically.png)

18. Wählen Sie **App veröffentlichen** aus. Ausführliche Informationen zum Veröffentlichen von Apps in Power BI finden Sie unter [Veröffentlichen Ihrer App](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).

### <a name="after-publishing-the-dashboard"></a>Nach dem Veröffentlichen des Dashboards

Informationen zum Anzeigen des veröffentlichten Power BI-Dashboards finden Sie unter [Anzeigen des Power BI-Dashboards](configure-data-reporting.md#view-power-bi-dashboard).

## <a name="issues-and-feedback"></a>Issues und Feedback

- Wenn Sie ein Issue mit der Beispiel-App für die Notfallreaktion für Krankenhäuser melden möchten, besuchen Sie <https://aka.ms/emergency-response-issues>.

- Wenn Sie Feedback zur Beispiel-App für die Notfallreaktion für Krankenhäuser geben möchten, besuchen Sie <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Nächster Schritt

[Verwenden der Notfallreaktions-App für Krankenhäuser](use.md)

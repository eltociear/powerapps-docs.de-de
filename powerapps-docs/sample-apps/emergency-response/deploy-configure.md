---
title: Bereitstellen und Konfigurieren der Hospital Emergency Response-App | Microsoft-Dokumentation
description: Bietet detaillierte Anweisungen für IT-Administratoren in Krankenhäusern, um die Beispiel-App für ihre Organisation bereitzustellen und zu konfigurieren.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/05/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- GetStarted
- PowerApps
ms.openlocfilehash: 624c465ea812e4fe650dda3750259acf91476bb0
ms.sourcegitcommit: 83b35be5df4864e15be9122647b17465e050284c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2020
ms.locfileid: "3229063"
---
# <a name="deploy-and-configure-the-hospital-emergency-response-app"></a>Bereitstellen und Konfigurieren der Hospital Emergency Response-App

Die Hospital Emergency Response-App erfordert einen geringen Einrichtungsaufwand, um Ihre Anforderungen zu erfüllen. In diesem Artikel finden Sie schrittweise Anweisungen für IT-Administratoren in Krankenhäusern, um die Anwendung für ihre Organisation bereitzustellen und zu konfigurieren.

Geschätzte Zeit, um diese Schritte auszuführen: **35–40 Minuten**.

## <a name="demo-deploy-and-configure-the-hospital-emergency-response-app"></a>Demo: Bereitstellen und Konfigurieren der Hospital Emergency Response-App

Sehen Sie sich an, wie Sie die Hospital Emergency Response-App bereitstellen und konfigurieren.

<br/>

> [!VIDEO https://www.youtube.com/embed/-1g44wNiuWI]


## <a name="deploy-the-hospital-emergency-response-app"></a>Bereitstellen der Hospital Emergency Response-App

Führen Sie die folgenden Schritte aus, um die Hospital Emergency Response-Beispiel-App für Ihre Organisation bereitzustellen.

- [Schritt 1: Registrieren für Power Apps und Erstellen einer Umgebung](#step-1-sign-up-for-power-apps-and-create-an-environment)
- [Schritt 2: Herunterladen des Bereitstellungspakets](#step-2-download-the-deployment-package)
- [Schritt 3: Importieren der Lösungsdatei in Ihre Umgebung](#step-3-import-the-solution-file-into-your-environment)
- [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization)
    - [Schritt 4.1: Laden der obligatorischen Konfigurationsdaten](#step-41-load-mandatory-configuration-data)
    - [Schritt 4.2: Laden der Stammdaten](#step-42-load-master-data)
- [Schritt 5: Aktualisieren des Mobile App-Branding](#step-5-update-the-mobile-app-branding)
- [Schritt 6: Umgehen der Zustimmung für mobile Apps](#step-6-bypass-consent-for-mobile-apps)
- [Schritt 7: Hinzufügen des Azure Application Insights-Schlüssels zu mobilen Apps für die Telemetrie](#step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry)
- [Schritt 8: Freigeben der Canvas-Apps für Benutzer in Ihrer Organisation](#step-8-share-canvas-apps-with-users-in-your-organization)
- [Schritt 9: Festlegen Ihrer mobilen App als herausragende und ausgewählte App](#step-9-set-your-mobile-app-as-hero-and-featured-app)
- [Schritt 10: Freigeben der modellgesteuerten App für Administratoren in Ihrer Organisation](#step-10-share-model-driven-app-with-admins-in-your-organization)

### <a name="step-1-sign-up-for-power-apps-and-create-an-environment"></a>Schritt 1: Registrieren für Power Apps und Erstellen einer Umgebung

Wenn Sie noch nicht Power Apps verwenden, registrieren Sie sich für Power Apps und erwerben Sie eine entsprechende Lizenz.

Weitere Informationen:

-   [Power Apps-Preise](https://powerapps.microsoft.com/pricing/)
-   [Kauf von Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Nachdem Sie Power Apps gekauft haben, erstellen Sie eine Umgebung mit einer Common Data Service-Datenbank.

1.  Melden Sie sich beim [Power Platform-Admin Center](https://aka.ms/ppac) an.

2.  Erstellen Sie eine Common Data Service-Umgebung mit der Datenbank. Weitere Informationen: [Erstellen und Verwalten von Umgebungen](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT]
    > Wenn Sie beim Erstellen der Datenbank eine Sicherheitsgruppe für die Datenbank auswählen, können die Apps *nur* gemeinsam mit Benutzern genutzt werden, die Mitglieder der Sicherheitsgruppe sind.

3.  Erstellen Sie geeignete Benutzer in Ihrer Umgebung. Weitere Informationen: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

### <a name="step-2-download-the-deployment-package"></a>Schritt 2: Herunterladen des Bereitstellungspakets

Holen Sie sich das neueste Bereitstellungspaket (.zip) von <https://aka.ms/emergency-response-solution>. Dieses enthält die Lösungsdatei, Bilder und Datendateien zum Einrichten der Apps und der Geschäftslogik für die Hospital Emergency Response-App.

Extrahieren Sie die Bereitstellungsdatei (.zip) an einen Speicherort auf Ihrem Computer, um den Bereitstellungsprozess zu starten. Der extrahierte Ordner enthält die folgenden Ordner:

| **Ordner/Datei**       | **Beschreibung**  |
|-----------------------|------------------|
| **App-Symbole**         | Enthält die Standard-App-Symbole für die mobilen Apps (Canvas-Apps).|
| **Datendateien**        | Enthält die Stamm- und Beispieldatendateien (.xlsx), damit die Lösung/App funktioniert. Sie können Daten aus diesen Dateien importieren, um mit der Arbeit an der App zu beginnen. Weitere Informationen: [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization) |
| **Power BIVorlage** | Enthält die Power BI-Berichtsvorlagendatei (.pbit), mit der Sie die Berichterstellung für Ihre Organisation konfigurieren. Weitere Informationen: [Erkenntnisse durch Power BI-Dashboards](#get-insights-using-power-bi-dashboards)|
| **PowerShell**        | Enthält Skripte, mit denen Sie Ihre mobilen Apps (Canvas-Apps) konfigurieren. |
| **Lösungsdatei**     | Enthält die Common Data Service-Lösungsdatei, die die Apps und Metadaten erstellt, die für die Hospital Emergency Response-App erforderlich sind.  |

### <a name="step-3-import-the-solution-file-into-your-environment"></a>Schritt 3: Importieren der Lösungsdatei in Ihre Umgebung

1.  Navigieren Sie zu dem Speicherort, an dem Sie die Bereitstellungsdatei (.zip) extrahiert haben. Dort finden Sie den Ordner **Lösungsdatei**. Wir werden die Datei verwaltete Lösung (.zip) unter den Ordner **Lösungsdatei** in unsere Umgebung importieren.

2.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

3.  Wählen Sie Ihre Umgebung in der oberen rechten Ecke aus.

4.  Wählen Sie im linken Bereich **Lösungen** und dann **Importieren** aus.

    > [!div class="mx-imgBorder"] 
    > ![Lösung importieren](media/conf-import-solution.png "Lösung importieren")

5.  Wählen Sie im Dialogfeld **Lösung importieren** die in Schritt 1 erwähnte Lösungsdatei aus und befolgen Sie die Schritte im Assistenten, um die Lösung zu importieren.

6.  Nachdem die Lösung erfolgreich importiert wurde, wählen Sie **Schließen** im Importdialogfeld aus.

Jetzt sehen Sie neue Apps unter **Apps**:

> [!div class="mx-imgBorder"] 
> ![Neue Apps](media/conf-apps-new-apps.png "Neue Apps")

Wählen Sie die Option **Administrator-App** aus, um die modellgesteuerte App zu öffnen, mit der Sie den Rest der Bereitstellungseinstellungen konfigurieren können. Weitere Informationen: [Was sind modellgesteuerte Apps?](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

> [!div class="mx-imgBorder"] 
> ![Administrator-App öffnen](media/conf-admin-app-open.png "Administrator-App öffnen")

Die Administrator-App verfügt über eine Reihe von Entitäten, mit denen Sie Daten für Ihr Krankenhaussystem hinzufügen und verwalten können. Sie können die Bereichsauswahl im unteren Teil des linken Navigationsbereichs verwenden, um einen anderen Bereich auszuwählen.

### <a name="step-4-load-configuration-and-master-data-for-your-organization"></a>Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation

Alle für die Hospital Emergency Response-App erforderlichen Daten finden Sie im Ordner **Datendateien** unter Ihrem extrahierten Bereitstellungsordner.

Der Ordner **Datendateien** enthält die folgenden Dateien und Ordner:

<table style="width:100%">
<tr>
<th>Name</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>Am Stamm sind folgende Dateien verfügbar:
<ul>
<li>00 – Acuities Import.xlsx</li>
<li>00 – App Config Import.xlsx</li>
<li>00 – App Import.xlsx</li>
<li>00 – Request Roles Import.xlsx</li>
<li>00 – Supplies Import.xlsx</li>
</ul>
</td>
<td>Dies sind die Konfigurationsdatendateien, die mit der Administrator-App in die folgenden Entitäten importiert werden müssen:
<ul>
<li>Pflegekategorien</li>
<li>App-Konfiguration</li>
<li>Apps</li>
<li>Rollen anfordern</li>
<li>Bedarfsimport</li>
</ul>
<br/>Durch das Importieren von Daten in diese Entitäten werden Datensätze für diese Entitäten erstellt, die für die Funktion der Hospital Emergency Response-App erforderlich sind.
<br/>
<br/>
<strong>Achtung</strong>: Stellen Sie sicher, dass Sie die Konfigurationswerte in diesen Entitäten, mit Ausnahme der Entitäten <strong>Apps</strong> und <strong>App-Konfiguration</strong> wie später erklärt, nicht aktualisieren.</td>
</tr>
<tr>
<td>Ordner <strong>Beispieldaten</strong></td>
<td><p>Der Ordner enthält die Beispieldatendateien (.xlsx), die Sie importieren können, um die Beispieldaten in Ihrer Anwendung aufzufüllen. Die Dateien werden benannt, um die Reihenfolge anzugeben, in der die Daten in Ihre App importiert werden sollen. </p>
<p>Sie müssen Daten für die folgenden Entitäten importieren, die die Stammbeispieldaten für die Hospital Emergency Response-App enthalten:
<ul>
<li>Systeme</li>
<li>Regionen</li>
<li>Einrichtungen</li>
<li>Standorte</li>
<li>Abteilungen</li>
</ul>
<p>Wenn Sie Ihre Organisationsdaten anstelle der Beispieldaten importieren möchten, können Sie die Beispieldaten in diesen Excel-Dateien durch Ihre Organisationsdaten ersetzen und anschließend die Daten in die App importieren.</p>
<p>Sie können Daten für diese Entitäten auch manuell eingeben. Informationen zu allen Entitäten und Feldern in diesen Entitäten finden Sie unter: <a href="#manually-configure-and-manage-master-data-for-your-organization">Stammdaten für Ihre Organisation manuell konfigurieren und verwalten</a></p></td>
</tr>
<tr>
<td>Ordner <strong>Datenvorlagendatei für Stammdaten</strong></td>
<td><p>Der Ordner enthält „leere“ Datendateien (.xlsx) für Stammentitäten, mit denen Sie Ihre Organisationsdaten auffüllen und dann in die App importieren können.</p>
<p>Die Dateien werden benannt, um die Reihenfolge anzugeben, in der die Daten in Ihre App importiert werden sollen. Es ist die gleiche Liste von Entitäten, die zuvor für den Ordner <strong>Beispieldaten</strong> erwähnt wurde.</p>
<p>Sie können Daten für diese Entitäten auch manuell eingeben. Informationen zu allen Entitäten und Feldern in diesen Entitäten finden Sie unter: <a href="#manually-configure-and-manage-master-data-for-your-organization">Stammdaten für Ihre Organisation manuell konfigurieren und verwalten</a></p>
</td>
</tr>
</table>

#### <a name="step-41-load-mandatory-configuration-data"></a>Schritt 4.1: Laden der obligatorischen Konfigurationsdaten

Das Importieren der Konfigurationsdaten unter den folgenden Entitäten in die Administrator-App erfolgt **verpflichtend**, bevor Sie mit dem nächsten Schritt fortfahren:

| Bereichsname | Entitätsname| Dateiname
|-|-|-
| Standorte | Pflegekategorien | 00 – Acuities Import.xlsx
| Verwaltung | App-Konfiguration | 00 – App Config Import.xlsx
| Verwaltung | Apps | 00 – App Import.xlsx
| Personal | Rollen anfordern | 00 – Request Roles Import.xlsx
| Standorte | Bedarf | 00 – Supplies Import.xlsx

##### <a name="how-to-load-data-from-data-files"></a>Wie werden Daten aus Datendateien geladen?

So importieren Sie Daten aus einer der Datendateien in eine Entität:

1.  Wählen Sie im linken Navigationsbereich der Administrator-App eine Entität aus, für die Sie die Daten laden möchten. Wählen Sie zum Beispiel **Verwaltung** aus der Bereichsauswahl und dann **Pflegekategorien** aus.

2.  Wählen Sie **Aus Excel importieren** und dann die Datei **00 – Acuities Import.xlsx** aus dem Ordner **Datendateien** aus.

    > [!div class="mx-imgBorder"]
    > ![Aus Excel importieren](media/conf-import-from-excel.png "Aus Excel importieren")

3.  Fahren Sie mit den Schritten des Importassistenten fort, um die Daten zu importieren.

4.  Nachdem die Daten importiert wurden, wird der importierte Datensatz in der Entität angezeigt:

    > [!div class="mx-imgBorder"] 
    > ![Entitätsdatensatz](media/conf-entity-record.png "Nach dem Import in der Entität aufzeichnen")

Wiederholen Sie die obigen Schritte mit anderen Konfigurationsdatenentitäten.

Wenn Sie die Stammdaten manuell eingeben möchten, lesen Sie alternativ [Stammdaten für Ihre Organisation manuell konfigurieren und verwalten](#manually-configure-and-manage-master-data-for-your-organization).

#### <a name="step-42-load-master-data"></a>Schritt 4.2: Laden der Stammdaten

Wie bereits erläutert:
- Sie können die Beispieldatendateien für Stammdatenentitäten unter dem Ordner **Datendateien/Beispieldaten** verwenden, um die Beispieldaten in die erforderlichen Entitäten zu importieren. 

- Sie können die „leeren“ Datendateien für Stammentitäten unter dem Ordner **Datendateien/Datenvorlagendatei für Stammdaten** verwenden, mit dem Sie Ihre Organisationsdaten auffüllen und dann die Daten in die erforderlichen Entitäten importieren können.

Sie können Stammdaten auch später manuell hinzufügen. Weitere Informationen: [Stammdaten für Ihre Organisation manuell konfigurieren und verwalten](#manually-configure-and-manage-master-data-for-your-organization)

### <a name="step-5-update-the-mobile-app-branding"></a>Schritt 5: Aktualisieren des Mobile App-Branding

Sie können das App-Symbol, das Farbschema oder den Anzeigename der mobilen Apps ändern, um das Branding Ihres Unternehmens anzupassen.

Verwenden Sie hierfür die Entitäten **Apps** und **App-Konfiguration** im Bereich **Verwaltung**. Importieren Sie App- und App-Konfigurationsdaten aus den Excel-Dateien im Ordner **Datendateien** und aus den Symboldateien im Ordner **App-Symbole** unter dem Bereitstellungspaket, wie erläutert in [Schritt 2: Herunterladen des Bereitstellungspakets](#step-2-download-the-deployment-package).

> [!div class="mx-imgBorder"] 
> ![Apps- und App-Konfiguration-Entitäten](media/conf-app-app-config-entities.png "Apps- und App-Konfiguration-Entitäten")

1.  Stellen Sie sicher, dass Sie die Konfigurationsdaten für die Entitäten **Apps** und **App-Konfiguration** mit den entsprechenden Dateien **App Import.xlsx** und **App Config Import.xlsx** importiert haben.

1.  Jetzt kopieren wir die App-IDs der Canvas-Apps, damit wir sie in die **Apps**-Datensätze, die wir importiert haben, auffüllen können. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

1.  Wählen Sie Ihre Umgebung in der oberen rechten Ecke aus.

1.  Wählen Sie im linken Bereich die Option **Apps** und dann die Auslassungspunkte (…) für eine Canvas-App, gefolgt von **Details** aus.

    > [!div class="mx-imgBorder"] 
    > ![Apps-Details](media/conf-environments-apps-details.png "App-Details")

1.  Die App-ID wird unten im Bereich **Details** für die App angezeigt. Kopieren Sie die App-ID zusammen mit ihrem Namen in eine Editor-Datei.

    > [!div class="mx-imgBorder"] 
    > ![Details App-ID](media/conf-details-app-id.png "Details App-ID")

1.  Wiederholen Sie die Schritte 4 und 5 für jede Canvas-App.

1.  Öffnen Sie die Administrator-App und wählen Sie im linken Navigationsbereich der Administrator-App die Option **Verwaltung** aus der Bereichsauswahl und dann **Apps** aus. Dies zeigt alle Canvas-App-Datensätze an, die Sie aus der Datei **App Import.xlsx** importiert haben.

    > [!div class="mx-imgBorder"] 
    > ![Administrator-Apps](media/conf-admin-app-records.png "Administrator-Apps")

1.  Öffnen Sie einen der App-Datensätze, indem Sie ihn auswählen. Beachten Sie, dass das Feld **Power App-ID** leer ist.

    > [!div class="mx-imgBorder"] 
    > ![Power App-ID-Feld ](media/conf-powerapp-id-field.png "Power App-ID-Feld")

1.  Auf der App-Detailseite:

    1. Kopieren Sie die App-ID aus dem Editor (in den Sie sie zuvor kopiert haben) in das **Power App-ID**-Feld.

    2. Doppelklicken Sie auf das App-Symbol und wählen Sie eine Symboldatei für die App aus dem Ordner **App-Symbole** aus. Die Bilddateien werden intuitiv benannt, sodass Sie leicht das richtige Symbol auswählen können. Wählen Sie beispielsweise die Datei „Emergency Response App.png“ für die **Emergency Response App** aus. Sie können auch ein benutzerdefiniertes Bild gemäß dem Branding Ihres Unternehmens auswählen.

    3. Aktualisieren Sie gegebenenfalls die **Beschreibung** oder den **Anzeigename** der App.

    4. Aktualisieren Sie gegebenenfalls den Wert **App im Menü ausblenden**, mit dem festgelegt wird, ob die App in der App-Liste angezeigt werden soll. Da die **Emergency Response App** eine Container-App ist, wird der Wert standardmäßig auf **Nein** gesetzt.

    5. Aktualisieren Sie gegebenenfalls den Wert **App-Anzeigerang** zum Festlegen der Anzeigeposition der App in der App-Liste.

    6. Wählen Sie **Speichern** aus.

1.  Wiederholen Sie die Schritte 8 und 9 für jeden Canvas-App-Datensatz unter **Apps**.

1.  Wählen Sie im linken Bereich die Option **App-Konfiguration** aus.

1.  Wählen Sie den **Emergency Response App**-Datensatz aus, um ihn zur Bearbeitung zu öffnen.

    1.  Aktualisieren Sie gegebenenfalls die Farben für Ihre App.

    2.  Wählen Sie **Ja** oder **Nein** im Feld **Gerätefreigabe aktiviert** aus, um anzugeben, ob eine Option zum **Abmelden** in mobilen Apps verfügbar ist oder nicht. Durch die Auswahl von **Ja** ist die Option **Abmelden** verfügbar. Weitere Informationen finden Sie im Benutzerhandbuch [Schicht beenden – abmelden](use.md#end-shift---sign-out).

    > [!div class="mx-imgBorder"] 
    > ![Feld Gerätefreigabe aktiviert](media/conf-device-sharing-enabled-field.png "Feld Gerätefreigabe aktiviert")

1.  Wählen Sie **Speichern** in der unteren rechten Ecke aus, um Ihre Änderungen zu speichern.

### <a name="step-6-bypass-consent-for-mobile-apps"></a>Schritt 6: Umgehen der Zustimmung für mobile Apps

Sie müssen ein Mandantenadministrator sein, um diesen Schritt abzuschließen. Bevor Sie diesen Schritt ausführen, benötigen Sie außerdem die App-ID jeder mobilen App (Canvas-App).

Um die App-ID für Ihre App abzurufen, wählen Sie im linken Navigationsbereich der Administrator-App die Option **Verwaltung** aus der Bereichsauswahl und dann **Apps** aus. Dies zeigt alle mobilen Apps (Canvas-Apps) an. Wählen Sie eine mobile App aus, um ihre App-ID anzuzeigen. Kopieren Sie die App-ID für jede App in eine Editor-Datei.

> [!div class="mx-imgBorder"] 
> ![App-ID abrufen](media/conf-admin-get-app-id.png "App-ID abrufen")

Führen Sie als Nächstes folgende Schritte aus:

1.  Öffnen Sie den Editor und kopieren Sie dieses PowerShell-Skript:

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

2.  Ersetzen Sie den Wert `APPGUIDHERE` mit der tatsächlichen App-ID einer Canvas-App.

3.  Speichern Sie die Datei als PS-Datei.

4.  Führen Sie PowerShell als Administrator und die soeben erstellte PS-Datei aus.

5.  Wiederholen Sie die Schritte 2 bis 4 für jede Canvas-App.

### <a name="step-7-add-azure-application-insights-key-to-mobile-apps-for-telemetry"></a>Schritt 7: Hinzufügen des Azure Application Insights-Schlüssels zu mobilen Apps für die Telemetrie

Sie können Azure Application Insights verwenden, um detaillierte Telemetrie für Ihre mobilen Apps (Canvas-Apps) zu sammeln und so Einblicke in die App-Nutzung zu erhalten. Detaillierte Informationen hierzu finden Sie unter [Analysieren der App-Telemetrie mit Application Insights](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights).

### <a name="step-8-share-canvas-apps-with-users-in-your-organization"></a>Schritt 8: Freigeben der Canvas-Apps für Benutzer in Ihrer Organisation

Damit Ihre Benutzer an vorderster Front Daten mithilfe der Canvas-Apps auf ihren Mobilgeräten verwenden können, müssen die Apps für sie freigegeben werden. Es ist einfacher, Azure AD-Gruppen zu verwenden, um Apps einfach für Benutzergruppen freizugeben.

> [!IMPORTANT]
> Stellen Sie sicher, dass der Benutzer oder die Gruppe, für die Sie die Apps freigeben möchten, *bereits* Zugriff auf Ihre Umgebung hat. In der Regel haben Sie während des [Einrichtens Ihrer Umgebung](#step-1-sign-up-for-power-apps-and-create-an-environment) bereits Benutzer oder Gruppen hinzugefügt. Alternativ können Sie die folgenden Schritte ausführen, um Benutzer zu Ihrer Umgebung hinzuzufügen und einen entsprechenden Zugriff bereitzustellen, bevor Sie Apps für sie freigeben: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1.  Anmelden bei [Power Apps](https://make.powerapps.com)

2.  Wählen Sie im linken Navigationsbereich die Option **Apps** aus, um eine Liste aller Ihrer Apps anzuzeigen.

3.  Wählen Sie eine mobile App (Canvas-App) und dann **Freigeben** im Banner aus.

    > [!div class="mx-imgBorder"] 
    > ![Canvas-Apps freigeben](media/conf-share-canvas-apps.png "Canvas-Apps freigeben")

4.  Geben Sie die Azure AD-Gruppe oder -Benutzer an, für die Sie diese App freigeben möchten. Da sich die App mit Common Data Service-Daten verbindet, müssen Sie auch Berechtigungen für die Entitäten bereitstellen. Das Freigabefenster fordert Sie auf, die Sicherheit für die Entitäten zu verwalten. Weisen Sie die Sicherheitsrollen des **Emergency Response-Benutzers** und **Common Data Service-Benutzers** für die von dieser App verwendeten Entitäten zu und wählen Sie **Freigeben** aus.

    > [!div class="mx-imgBorder"] 
    > ![App für Azure AD-Gruppe oder -Benutzer freigeben](media/conf-share-app-groups-users.png "App für Azure AD-Gruppe oder -Benutzer freigeben")

5.  Wiederholen Sie die Schritte 3 und 4 für jede mobile App.

Detaillierte Informationen zum Freigeben Ihrer Apps: [Freigeben einer Canvas-App](https://docs.microsoft.com/powerapps/maker/canvas-apps/share-app)

### <a name="step-9-set-your-mobile-app-as-hero-and-featured-app"></a>Schritt 9: Festlegen Ihrer mobilen App als herausragende und ausgewählte App

In diesem Schritt können Sie Ihre mobile App als herausragende und ausgewählte App innerhalb der **Power Apps** Mobile App festlegen. Sie müssen ein Mandantenadministrator sein, um diesen Schritt abzuschließen.

Bevor Sie diesen Schritt ausführen, benötigen Sie die App-ID jeder mobilen App (Canvas-App), die Sie als herausragende und ausgewählte App festlegen möchten. Informationen zum Abrufen der App-ID für eine Canvas-App finden Sie unter [Schritt 6: Umgehen der Zustimmung für mobile Apps](#step-6-bypass-consent-for-mobile-apps).

Führen Sie als Nächstes folgende Schritte aus:

1.  Öffnen Sie den Editor und kopieren Sie dieses PowerShell-Skript:


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

2.  Ersetzen Sie den Wert `APPGUIDHERE` im Skript mit der tatsächlichen App-ID für die App, die Sie als ausgewählt und herausragend festlegen möchten.

3.  Speichern Sie die Datei als PS-Datei.

4.  Führen Sie PowerShell als Administrator und die soeben erstellte PS-Datei aus.
 

### <a name="step-10-share-model-driven-app-with-admins-in-your-organization"></a>Schritt 10: Freigeben der modellgesteuerten App für Administratoren in Ihrer Organisation

Damit Ihre Administratorbenutzer die Administrator-App (modellgesteuerte App) verwenden können, muss sie für sie freigegeben werden. Es ist einfacher, Azure AD-Gruppen zu verwenden, um Apps einfach für Administratorbenutzergruppen freizugeben.

> [!IMPORTANT]
> Stellen Sie sicher, dass der Benutzer oder die Gruppe, für die Sie die App freigeben möchten, *bereits* Zugriff auf Ihre Umgebung hat. In der Regel haben Sie während des [Einrichtens Ihrer Umgebung](#step-1-sign-up-for-power-apps-and-create-an-environment) bereits Benutzer oder Gruppen hinzugefügt. Alternativ können Sie die folgenden Schritte ausführen, um Benutzer zu Ihrer Umgebung hinzuzufügen und einen entsprechenden Zugriff bereitzustellen, bevor Sie die App für sie freigeben: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2. Wählen Sie im linken Navigationsbereich die Option Apps aus, um eine Liste aller Ihrer Apps anzuzeigen.

3. Wählen Sie die modellgesteuerte App (**Administrator-App – Emergency Response-App**) und dann **Freigeben** im Banner aus.

4. Geben Sie die Azure AD-Gruppen- oder -Administratorbenutzer, für die Sie diese App freigeben möchten, an, weisen Sie die Sicherheitsrolle **Emergency Response-Administrator** zu und wählen Sie **Freigeben** aus.


## <a name="manually-configure-and-manage-master-data-for-your-organization"></a>Stammdaten für Ihre Organisation manuell konfigurieren und verwalten

Administratoren können die modellgesteuerte App in [Power Apps](https://make.powerapps.com) verwenden, um die Stammdaten für ihre Organisation zu erstellen und zu verwalten. Diese Daten sind erforderlich, damit die Hospital Emergency Response-App funktioniert.

> [!NOTE]
> Sie können Ihre Organisationsdaten auch in Datendateien importieren, die im Bereitstellungspaket verfügbar sind, und diese dann in diese Entitäten importieren. Weitere Informationen: [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization)

Sie müssen Stammdaten zu diesen Entitäten in der folgenden Reihenfolge hinzufügen:

1. [Systeme](#systems-data)

1. [Regionen](#regions-data)

1. [Einrichtungen](#facilities-data)

1. [Standorte](#locations-data)

1. [Abteilungen](#departments-data)

Die Stammdaten werden vom Bereich **Standorte** in der linken Navigation in der Administrator-App verwaltet:

> [!div class="mx-imgBorder"]
> ![Standortbereich](media/locations-area.png)

Die Entitäten im Bereich **Hierarchie** werden in der Reihenfolge aufgelistet, in der Sie Daten auffüllen sollten.

### <a name="systems-data"></a>Systemdaten

Mit der Entität **Systeme** können Sie Einträge für Krankenhaussysteme erstellen und verwalten. Auf diese Weise können Sie mehrere Krankenhaussysteme innerhalb derselben Organisation verwalten.

So erstellen Sie einen Datensatz:

1. Wählen Sie im linken Bereich **Systeme** und dann **Neu** aus:  
    > [!div class="mx-imgBorder"]
    > ![Neue Systeme auswählen](media/select-systems-new.png)

2. Geben Sie auf der Seite **Neues System** die entsprechenden Werte an:  
   > [!div class="mx-imgBorder"]
   > ![Details für neues System eingeben](media/enter-details-new-system.png)

   | **Feld**            | **Beschreibung**                                    |
   |----------------------|----------------------------------------------------|
   | Systemname          | Geben Sie einen Namen für das Krankenhaus ein.                     |
   | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
   | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für dieses Krankenhaussystem ein. |
   | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für dieses Krankenhaussystem ein.   |

3. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Systeme** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

### <a name="regions-data"></a>Regionendaten

Mit der Entität **Regionen** können Sie die geografischen Regionen für Ihre Krankenhaussysteme verwalten.

So erstellen Sie einen Datensatz:

1. Wählen Sie im linken Bereich **Regionen** und dann **Neu** aus.

2. Geben Sie auf der Seite **Neue Region** die entsprechenden Werte an:  

    > [!div class="mx-imgBorder"]
    > ![Details für neue Region eingeben](media/enter-details-new-region.png)

    | **Feld**            | **Beschreibung**                                                                                          |
    |----------------------|----------------------------------------------------------------------------------------------------------|
    | System               | Wählen Sie ein Krankenhaussystem aus. Diese Liste wird basierend auf den **System**daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Regionenname          | Geben Sie den Regionennamen ein. Zum Beispiel Berlin.                                                              |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                            |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diese Region ein.                                                       |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diese Region ein.                                                         |

3. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Regionen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

### <a name="facilities-data"></a>Einrichtungsdaten

Mit der Entität **Einrichtungen** können Sie die Krankenhausstandorte in jeder Region verwalten. Zum Beispiel die Einrichtungen **Potsdam** und **Oranienburg** innerhalb der Region **Berlin**.

So erstellen Sie einen Datensatz:

1. Wählen Sie im linken Bereich die Option **Einrichtungen** und dann **Neu** aus.

2. Geben Sie auf der Seite **Neue Einrichtung** die entsprechenden Werte an: 

    > [!div class="mx-imgBorder"] 
    > ![Details für neue Einrichtung eingeben](media/enter-details-new-facility.png)

    | **Feld**            | **Beschreibung**                                                                                 |
    |----------------------|-------------------------------------------------------------------------------------------------|
    | Region               | Wählen Sie eine Region aus. Diese Liste wird basierend auf den **Regionen**daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Einrichtungsname        | Geben Sie den Einrichtungsnamen ein. Zum Beispiel Oranienburg.                                                  |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                                                                   |
    | Beatmungsgeräte insgesamt          | Geben Sie die Gesamtzahl der in der Einrichtung verfügbaren Beatmungsgeräte ein.                                  |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diese Einrichtung ein.                                                     |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diese Einrichtung ein.                                                       |

    Geben Sie bei Bedarf die Adresse der Einrichtung ein.

3. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Einrichtungen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

### <a name="locations-data"></a>Standortdaten

Mit der Entität **Standorte** können Sie bestimmte Standorte in jeder Krankenhauseinrichtung verwalten.

> [!NOTE]
> Stellen Sie vor dem Erstellen eines **Standorte**-Datensatzes sicher, dass Sie die Pflegekategoriedaten mit der Datei **00 – Acuities Import.xlsx** wie weiter oben erläutert in [Schritt 4: Laden der Konfigurations- und Stammdaten für Ihre Organisation](#step-4-load-configuration-and-master-data-for-your-organization) importiert haben. Dies liegt daran, dass Pflegekategoriedaten zur Erstellung eines **Standort**-Datensatzes erforderlich sind.

So erstellen Sie einen Datensatz:

1. Wählen Sie im linken Bereich die Option **Standorte** und dann **Neu** aus.

2. Geben Sie auf der Seite **Neuen Standort** die entsprechenden Werte an:  
 
    > [!div class="mx-imgBorder"]
    > ![Details für neuen Standort eingeben](media/enter-details-new-location.png)

    | **Feld**            | **Beschreibung**                                                                                      |
    |----------------------|------------------------------------------------------------------------------------------------------|
    | Standortname        | Geben Sie den Namen des Standortes ein.                                                                       |
    | Einrichtung             | Wählen Sie eine Einrichtung aus. Diese Liste wird basierend auf den **Einrichtungs**daten, die Sie zuvor erstellt haben, ausgefüllt. |
    | Etage                | Geben Sie die Etagedaten für die Einrichtung ein.                                                         |
    | Einheit                 | Geben Sie die Einheitsdaten für die Einrichtung ein.                                                           |
    | Pflegekategorie      | Wählen Sie den Pflegekategoriedatensatz aus, der diesem Standort zugewiesen ist.                                                                                                     |
    | COVID-Standort      | Wählen Sie aus, ob dieser Standort zur Behandlung von COVID-Patienten genutzt wird (**Ja** oder **Nein**).                                                                                                      |
    | Betten insgesamt           | Geben Sie die Gesamtzahl der Betten in der Einrichtung ein.                                                       |
    | Schwallbetten           | Geben Sie die Anzahl der Schwallbetten in der Einrichtung ein. Schwallbetten sind solche, die über die lizenzierte Bettenkapazität hinaus besetzt werden können, wenn Patienten aufgenommen werden müssen.                                                      |
    | Blockierte Betten         | Geben Sie die Anzahl blockierter Betten in der Einrichtung ein.                                                     |
    | Letzte Zählung          | Ausgefüllt basierend auf dem zuletzt erstellten Zählungsdatensatz.                                             |
    | Belegungsprozentsatz | Automatisch berechnet basierend auf der letzten Zählung und der Betten insgesamt.                                         |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diesen Standort ein.                                                   |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diesen Standort ein.                                                     |
    | Standortreihenfolge       | Geben Sie eine Zahl ein, die den Standort in den Dropdown-Standortlisten sortiert.                               |
    | Alternatives Site-Kennzeichen  | Nur zur internen Verwendung.                                                                                     |

3. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Standorte** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

### <a name="departments-data"></a>Abteilungsdaten

Mit der Entität **Abteilungen** können Sie Abteilungsdaten für ein Krankenhaus verwalten.

So erstellen Sie einen Datensatz:

1. Wählen Sie im linken Bereich die Option **Abteilungen** und dann **Neu** aus.

2. Geben Sie auf der Seite **Neue Abteilung** die entsprechenden Werte an:

    > [!div class="mx-imgBorder"]
    > ![Details für neue Abteilung eingeben](media/enter-details-new-department.png)

    | **Feld**            | **Beschreibung**                                    |
    |----------------------|----------------------------------------------------|
    | Abteilungsname      | Geben Sie einen Abteilungsnamen ein.                            |
    | Beschreibung          | Geben Sie eine optionale Beschreibung ein.                      |
    | Effektives Startdatum | Geben Sie Startdatum und -uhrzeit für diese Abteilung ein. |
    | Effektives Enddatum   | Geben Sie Enddatum und -uhrzeit für diese Abteilung ein.   |

3. Klicken Sie auf **Speichern und Schließen**. Der neu erstellte Datensatz ist in der Liste **Abteilungen** verfügbar.

Um den Datensatz zu bearbeiten, wählen Sie den Datensatz aus, aktualisieren Sie die Werte nach Bedarf und wählen Sie **Speichern und Schließen** aus.

## <a name="get-insights-using-common-data-service-dashboards"></a>Erkenntnisse durch Common Data Service-Dashboards

Die folgenden Dashboards sind standardmäßig in der (modellgesteuerten) Hospital Emergency Response-Administrator-App verfügbar:

- **Bettenverwaltung**

   Zeigt die Verfügbarkeit von Betten, den Belegungsprozentsatz und die Gesamtzahl der Betten in verschiedenen Einrichtungen an.

- **Arbeitsgeräte und Bedarf**

  Zeigt kritische Arbeitsgeräte in Gebrauch und verfügbaren Bedarf in verschiedenen Einrichtungen an.

- **Personalverwaltung**

  Zeigt die Anzahl der angeforderten, zugewiesenen und verfügbaren Mitarbeiter in verschiedenen Einrichtungen an.

- **COVID-Patienten**

  Zeigt die Anzahl der untersuchten und mit COVID-19 positiv getesteten Patienten in verschiedenen Einrichtungen an.

- **Entlassungen**

  Zeigt die Anzahl der Patienten, deren Entlassung erwartet wird, und tatsächlich entlassener Patienten an.

Sie können zusätzlich zu den standardmäßig verfügbaren Dashboards auch eigene Dashboards erstellen.

### <a name="manage-dashboards"></a>Verwalten von Dashboards

So verwalten Sie Dashboards:

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an und navigieren Sie zu Ihrer Administrator-App.

2. Wählen Sie im linken Navigationsbereich die Option **Dashboards** aus der Bereichsauswahl aus:

    > [!div class="mx-imgBorder"]
    > ![Dashboards auswählen](media/select-dashboards.png)

3. Wählen Sie in der linken Navigation einen Dashboard-Namen aus, um die Diagramme anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Diagramme anzeigen](media/view-charts.png)

    > [!NOTE]
    > Sie können Daten am unteren Bildschirmrand filtern und die Diagramme oben werden automatisch mit gefilterten Werten aktualisiert.

4. Wählen Sie die Option **Erweitern** aus, um ein Diagramm im Vollbildmodus anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Auswahl erweitern](media/select-expand.png)

### <a name="additional-analysis"></a>Zusätzliche Analyse

- **Drilldown ausführen**: Sie können den Diagrammbereich auswählen, um einen weiteren Drilldown mit zusätzlichen Attributen (Feldern) für eine Entität auszuführen:

    > [!div class="mx-imgBorder"]
    > ![Diagrammbereich auswählen und Drilldown ausführen](media/select-chart-area-drill-down.png)

- **Aktualisieren**: Sie können die Dashboards aktualisieren, um aktualisierte Daten wiederzugeben. Sie können entweder alle Diagramme in einem bestimmten Dashboard mit der Option **Alle aktualisieren** oder ein ausgewähltes Diagramm mit der Option **Aktualisieren** aktualisieren:

    > [!div class="mx-imgBorder"]
    > ![Dashboards aktualisieren](media/refresh-dashboards.png)

- **Datensätze anzeigen**: Wählen Sie **Weitere Befehle** (**…**) und dann **Datensätze anzeigen** aus, um alle Datensätze, die einem bestimmten Diagramm zugeordnet sind, anzuzeigen:

    > [!div class="mx-imgBorder"]
    > ![Weitere Befehle auswählen](media/select-more-commands.png)

    > [!NOTE] 
    > Wenn Sie die Option **Datensätze anzeigen** auswählen, sehen Sie die Ansicht der Entität, die zwischen Diagramm und Datensätzen aufgeteilt ist. Jede Änderung an Filtern für Datensätze auf der rechten Seite wird durch automatische Aktualisierungen des Diagramms auf der linken Seite des Bildschirms angezeigt.

Weitere Informationen zum Bearbeiten eines vorhandenen Dashboards und zum Aktualisieren der Eigenschaften von Diagrammen finden Sie unter [Bearbeiten eines vorhandenen Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#edit-an-existing-dashboard).

### <a name="create-new-dashboards"></a>Erstellen neuer Dashboards

Sie können auch Ihre eigenen Dashboards erstellen und an Ihre Bedürfnisse anpassen. Wählen Sie zum Erstellen eines neuen Dashboards die Option **Neu** und dann **Dynamics 365-Dashboard** aus:

> [!div class="mx-imgBorder"]
> ![Neues Dynamics-Dashboard auswählen](media/select-new-dynamics-dashboard.png)

Weitere Informationen zum Erstellen eines neuen Dashboards finden Sie unter [Erstellen eines neuen Dashboards](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-dashboards#create-a-new-dashboard).

## <a name="get-insights-using-power-bi-dashboards"></a>Erkenntnisse durch Power BI-Dashboards

Veröffentlichen Sie das Power BI-Dashboard und teilen Sie es mit Benutzern in Ihrer Organisation, damit diese das Dashboard für Einblicke und Entscheidungen verwenden können.

### <a name="prerequisites"></a>Voraussetzungen

- Power BI-Premium-Kapazität oder Power BI-Pro-Lizenzen für Benutzer, die auf den Bericht zugreifen. 

- Erstellen Sie einen Arbeitsbereich in Power BI, in dem Sie den Bericht veröffentlichen. Melden Sie sich bei Power BI an und erstellen Sie einen Arbeitsbereich. Weitere Informationen: [Erstellen neuer Arbeitsbereiche in Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Installieren Sie Power BI Desktop aus dem Windows-App-Store: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Wenn Sie Power BI durch direktes Herunterladen von der Power BI-Website als ausführbare Datei installiert haben, entfernen Sie es und verwenden Sie die Version aus dem App-Store. Die App-Store-Version wird automatisch aktualisiert, sobald neue Versionen verfügbar sind.

- Nachdem Sie Power BI Desktop aus dem App-Store installiert haben, führen Sie es aus und melden Sie sich mit einem Konto an, das zum Veröffentlichen von Power BI-Apps in Ihrer Organisation berechtigt ist.

### <a name="publish-the-power-bi-dashboard"></a>Veröffentlichen des Power BI-Dashboards

1. Navigieren Sie zum Speicherort, an dem Sie das Bereitstellungspaket extrahiert haben. Dort finden Sie die Datei **Emergency Response App.pbit** unter dem Ordner **Power BI-Vorlage**.

2. Öffnen Sie die Datei **Emergency Response App.pbit** in Power BI Desktop. Sie werden aufgefordert, die folgenden Werte einzugeben:

    - **Organization_name**: Geben Sie Ihren Organisationsnamen ein, der in der oberen linken Ecke jeder Berichtsseite angezeigt wird.
    - **CDS_base_solution_URL**: Geben Sie die URL Ihrer Common Data Service-Umgebungsinstanz ein. Zum Beispiel: https://*[myenv]*.crm.dynamics.com

    > [!div class="mx-imgBorder"]
    > ![Organisationsname und Basis-URL angeben](media/pbi-pub-rep1.png)

    Wählen Sie **Laden** aus.

3. Sie werden aufgefordert, Anmeldeinformationen einzugeben, um eine Verbindung zu Ihrer Common Data Service-Umgebung herzustellen. Wählen Sie **Organisationskonto** > **Anmelden** aus, um Ihre Common Data Service-Anmeldeinformationen anzugeben.  

    > [!div class="mx-imgBorder"]
    > ![Organisationskonto auswählen](media/select-organizational-account.png)

4. Wählen Sie nach dem Anmelden die Option **Verbinden** aus, um eine Verbindung zu Ihren Daten in Common Data Service herzustellen.

5. Bei erfolgreicher Verbindung werden Ihre Daten im Power BI-Bericht angezeigt. Sie werden aufgefordert, ausstehende Änderungen auf Ihre Abfrage anzuwenden. Wählen Sie dann **Änderungen übernehmen** aus.

6. Wählen Sie die Option **Veröffentlichen** aus, um Daten in Ihren Power BI-Arbeitsbereich zu veröffentlichen. Sie werden aufgefordert, Ihre Änderungen zu speichern. Wählen Sie **Speichern** aus.

    > [!div class="mx-imgBorder"]
    > ![Auswählen, aktualisieren, veröffentlichen](media/select-refresh-publish.png)

7. Sie werden aufgefordert, die Datei zusammen mit Ihren Common Data Service-Umgebungsdaten als PBIX-Datei zu speichern. Geben Sie einen Namen ein und speichern Sie sie auf Ihrem Computer.

8. Nach dem Speichern der PBIX-Datei werden Sie aufgefordert, den Bericht zu veröffentlichen. Wählen Sie auf der Seite **Veröffentlichen in Power BI** den Arbeitsbereich aus, in dem Sie veröffentlichen möchten, und klicken Sie dann auf **Auswählen**.

12. Der Bericht ist dann in Ihrem Arbeitsbereich verfügbar. Jetzt konfigurieren wir die Datenaktualisierungseinstellungen für DataSet. Wählen Sie das DataSet in Ihrem Arbeitsbereich und dann das Symbol für **Zeitplanaktualisierung** aus.  
    
    > [!div class="mx-imgBorder"]
    > ![Zeitplanaktualisierung](media/schedule-refresh.png)

13. Wenn Sie zum ersten Mal versuchen, die Datenaktualisierungseinstellungen festzulegen, wird die Seite **Einstellungen** mit der Meldung angezeigt, dass Ihre Anmeldeinformationen nicht gültig sind. Wählen Sie unter **Anmeldeinformationen für Datenquelle** die Option **Anmeldeinformationen bearbeiten** aus, um Ihre Anmeldeinformationen anzugeben.  

    > [!div class="mx-imgBorder"]
    > ![Anmeldeinformationen auswählen, bearbeiten](media/select-edit-credentials.png)

14. Im nächsten Bildschirm:
    - Wählen Sie **Authentifizierungsmethode** als **OAuth2** aus.
    - Wählen Sie **Datenschutzstufeneinstellungen für diese Datenquelle** als **Organisatorisch** aus.
    - Wählen Sie **Anmelden** aus.

    Sie werden aufgefordert, Ihre Anmeldeinformationen anzugeben und sich anzumelden. Nach erfolgreicher Anmeldung kehren Sie zur Seite **Einstellungen** zurück.

15. Erweitern Sie auf der Seite **Einstellungen** die Option **Geplante Aktualisierung** und geben Sie die erforderlichen Details zum Aktualisieren von Daten basierend auf einem Zeitplan an. Wählen Sie **Übernehmen** aus.

    > [!div class="mx-imgBorder"]
    > ![Geplante Aktualisierung](media/refresh-schedule.png)

    > [!NOTE] 
    > Es gibt Grenzen, wie oft Daten aktualisiert werden können. Power BI begrenzt DataSets für gemeinsam genutzte Kapazität auf acht tägliche Aktualisierungen. Wenn sich das DataSet auf einer Premium-Kapazität befindet, können Sie in den DataSet-Einstellungen bis zu 48 Aktualisierungen pro Tag planen. Weitere Informationen: [Daten aktualisieren](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)

16. Wählen Sie im linken Bereich den Namen Ihres Arbeitsbereichs aus und wählen Sie dann **App erstellen** in der oberen rechten Ecke aus.  

    > [!div class="mx-imgBorder"]
    > ![App auswählen, erstellen](media/select-create-app.png)

17. Auf der Seite zur App-Veröffentlichung:

    1. Geben Sie auf der Registerkarte **Einrichtung** den Namen und die Beschreibung Ihrer App an.

    2. Geben Sie auf der Registerkarte **Navigation** den Speicherort des Dashboards an, an dem Sie sie veröffentlichen möchten.

    3. Geben Sie auf der Registerkarte **Berechtigungen** die Benutzer oder Gruppen an, die diese App anzeigen können. Stellen Sie sicher, dass Sie das Kontrollkästchen **App automatisch installieren** aktivieren, um diese App automatisch für Endbenutzer zu installieren. Weitere Informationen: [Automatisches Installieren von Apps für Endbenutzer](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![Apps automatisch auswählen, installieren](media/select-install-apps-automatically.png)

18. Wählen Sie **App veröffentlichen** aus. Ausführliche Informationen zum Veröffentlichen von Apps in Power BI finden Sie unter [Veröffentlichen der App](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).

### <a name="view-the-power-bi-dashboard"></a>Anzeigen des Power BI-Dashboards

Melden Sie sich bei [Power BI](https://apps.powerbi.com) an, um das Power BI-Dashboard anzuzeigen und darauf zuzugreifen.

> [!div class="mx-imgBorder"]
> ![Power BI-Dashboard anzeigen](media/view-power-dashboard.png)

Sie können die Filter oben im Bericht verwenden, um Daten für Krankenhaussysteme, Regionen und Einrichtungen zu filtern. Sie können auch nach COVID-Standorten filtern.

> [!div class="mx-imgBorder"]
> ![Filter von Berichten](media/report-filters.png)

#### <a name="system-at-a-glance-page"></a>Systemüberblickseite 

Die **Systemüberblickseite** ist die Standardseite oder die Seite der obersten Ebene, die eine Gesamtansicht bietet.  

Auf der Seite wird eine zusammengefasste Ansicht der folgenden Elemente angezeigt: 

- **COVID-Patienten**: Zeigt die Gesamtzahl der COVID-Patienten, die Anzahl der mit COVID-19 positiv getesteten Patienten und die Anzahl der untersuchten Patienten an. 

- **Bettenverwaltung**: Zeigt die Verfügbarkeit von Betten, den Belegungsprozentsatz, die Anzahl der Schwallbetten und die Gesamtzahl der Betten an. Sie können auch das unten stehende Raster verwenden, um die Zahlen nach akuten Einheiten anzuzeigen. 

- **Personalverwaltung für Krankenschwestern**: Zeigt die Anzahl der Patienten auf der Intensivstation, die zugewiesenen Krankenschwestern und das Verhältnis von Krankenschwester zu Patient an.  

- **Entlassungen**: Zeigt die Anzahl der Patienten mit längerem Aufenthalt insgesamt, die Anzahl der Patienten, deren Entlassung erwartet wird, und die Anzahl tatsächlich entlassener Patienten an. 

- **Arbeitsgeräte**: Zeigt die Gesamtzahl der Beatmungsgeräte, die Anzahl der verwendeten Beatmungsgeräte und die verfügbaren Beatmungsgeräte an. 

- **Bedarf**: Zeigt die Anzahl des verfügbaren Bedarfs pro Tag an.

> [!NOTE]
> - Durch Auswahl des Informationssymbols (i) in einem der zusammengefassten Bereiche gelangen Sie zur entsprechenden Detailseite für den Bereich. 
> - Sie können auch andere Aktionen für Berichte ausführen, z. B. Daten filtern und sortieren, den Bericht in PDF und PowerPoint exportieren, einen Spotlight hinzufügen usw. Ausführliche Informationen zu Berichtsfunktionen in Power BI finden Sie unter [Berichte in Power BI](https://docs.microsoft.com/power-bi/consumer/end-user-reports).
> - Die letzten oder zuletzt aktualisierten Spalten in einigen dieser Berichte zeigen Datum und Uhrzeit der letzten Aktualisierung der Daten an. Es ist auch einfach, die Aktualität zu identifizieren, indem Sie die Farbe der Datums- und Uhrzeitwerte in diesen Spalten ansehen:
>    - Schwarz: Daten wurden vor weniger als 20 Stunden aktualisiert
>    - Grau: Daten wurden vor 20 bis 24 Stunden aktualisiert
>    - Rot: Daten wurden vor mehr als 24 Stunden aktualisiert 
 
#### <a name="system-view-page"></a>Systemansichtsseite

Auf der **Systemansichtsseite** werden Diagramme mit den folgenden Daten für ein Krankenhaussystem angezeigt:
- Beatmungsgeräte in Gebrauch und Beatmungsgeräte verfügbar
- Verfügbarkeit von Betten und Akutbetten und Belegungsprozentsatz
- Angefordertes Personal insgesamt, Anzahl der Patienten (Zählung), Verhältnis von Krankenschwester zu Patient.
- Verfügbarer Bedarf pro Tag

> [!div class="mx-imgBorder"]
> ![Systemansicht](media/report-system-view.png)

#### <a name="location-details-page"></a>Standortdetailseite 

Um einen Drilldown des Berichts nach Speicherort auszuführen, klicken Sie auf **Standortdetails** in der oberen rechten Ecke. Auf der Seite **Standortdetails** werden Daten nach Standort angezeigt, z. B. Gesamtzahl der Betten, verfügbare Betten, Schwallbetten, COVID-Patienten usw. 

> [!div class="mx-imgBorder"]
> ![Standortdetails](media/report-location-details.png) 

#### <a name="covid-patient-details-page"></a>COVID-Patientendetailseite 

Auf der Seite **COVID-Patientendetails** finden Sie detaillierte Informationen zu den COVID-Patienten, z. B. Patienten an jedem Standort, den Patiententrend im Zeitverlauf, der Maximal- und Mindestanzahl der untersuchten Patienten (PUI) anzeigt, die Anzahl der positiv getesteten Patienten sowie den Ort, wo Patienten im Krankenhaus untergebracht sind.

> [!div class="mx-imgBorder"]
> ![COVID-Patientendetails](media/report-covid-details.png)

#### <a name="bed-management-page"></a>Bettenverwaltungsseite 

Auf der Seite **Bettenverwaltung** finden Sie Detailinformationen nach Standort, z. B. insgesamt verfügbare Betten und Belegungsprozentsatz.

> [!div class="mx-imgBorder"]
> ![Bettenverwaltung](media/report-bed-details.png)

#### <a name="staff-details-page"></a>Personaldetailseite  

Auf der Seite **Personaldetails** finden Sie Details zum Personal nach Standort, Anzahl der zugewiesenen Krankenschwestern, Gesamtzahl der Patienten und Anzahl der COVID-Patienten. Es zeigt auch das Verhältnis von Krankenschwester zu Patient und das Verhältnis von Krankenschwester zu Patient auf der Intensivstation über einen bestimmten Zeitraum an.

> [!div class="mx-imgBorder"]
> ![Personaldetails](media/report-staff-details.png)

#### <a name="equipment-details-page"></a>Arbeitsgerätedetailseite 

Auf der Seite **Arbeitsgerätedetails** finden Sie Details zu den Arbeitsgeräten nach Standort, zur Gesamtzahl der verwendeten Beatmungsgeräte, überlagert mit der Anzahl der COVID-Patienten und zu anderen Arbeitsgeräten wie Gürteln, Ladegeräten und Hauben, die verwendet werden.

> [!div class="mx-imgBorder"]
> ![Arbeitsgerätedetails](media/report-equipment-details.png)

#### <a name="discharge-details-page"></a>Entlassungsdetailseite 

Auf der Seite **Entlassungsdetails** finden Sie Details zu Langzeitpatienten, Entlassungsbarrieren über einen bestimmten Zeitraum und Abweichungen in Bezug auf tatsächliche und erwartete Entlassungen.

> [!div class="mx-imgBorder"]
> ![Arbeitsgerätedetails](media/report-discharge-details.png)

#### <a name="supplies-on-hand-details-page"></a>Detailseite zum verfügbaren Bedarf 

Die Seite **Details zum verfügbaren Bedarf** enthält Details zum Bedarf nach Standort und Bedarf. Sie bietet auch Daten über den Bedarf, der über einen bestimmten Zeitraum verfügbar ist.

> [!div class="mx-imgBorder"]
> ![Arbeitsgerätedetails](media/report-discharge-details.png)

## <a name="view-and-manage-app-feedback"></a>Anzeigen und Verwalten von App-Feedback

Alle Rückmeldungen von Mitarbeitern an vorderster Front, die Canvas-Apps auf ihren Mobilgeräten verwenden, werden in der Entität **App-Feedback** gespeichert. Administratoren können dies mithilfe des Bereichs **Verwaltung** im linken Navigationsbereich in der Administrator-App anzeigen und verwalten.

So erfolgt das Anzeigen und Verwalten von App-Feedback:

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an und navigieren Sie zu Ihrer Administrator-App.

2. Wählen Sie im linken Navigationsbereich die Option **Administration** aus der Bereichsauswahl aus.

3. Wählen Sie **App-Feedback** aus, um eine Liste der von Benutzern eingereichten App-Rückmeldungen anzuzeigen. Sie können auf einen Datensatz klicken, um Details anzuzeigen und als überprüft oder nicht überprüft zu markieren.  

    > [!div class="mx-imgBorder"]
    > ![App-Feedback auswählen](media/select-app-feedback.png)

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Hospital Emergency Response-Beispiel-App zu melden, navigieren Sie zu <https://aka.ms/emergency-response-issues>.

- Feedback zur Hospital Emergency Response-Beispiel-App finden Sie unter <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Nächster Schritt

[Verwenden der Hospital Emergency Response-App](use.md)

---
title: Die App für Notfallmaßnahmen im Krankenhaus bereitstellen | Microsoft Docs
description: Bietet detaillierte Anweisungen für IT-Administratoren in Krankenhäusern, um die Beispiel-App für ihre Organisation bereitzustellen und zu konfigurieren.
author: pankajarora-msft
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 04/29/2020
ms.author: pankar
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 40cd65d4017573689e98381269a50cfcc4000cb0
ms.sourcegitcommit: 4c7c213dd1d10523c84013ab78f02c260e6b6388
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "3324823"
---
# <a name="deploy-the-hospital-emergency-response-app"></a>Bereitstellen der Hospital Emergency Response-App

Die Hospital Emergency Response-App erfordert einen geringen Einrichtungsaufwand, um Ihre Anforderungen zu erfüllen. In diesem Artikel finden Sie schrittweise Anweisungen für IT-Administratoren in Krankenhäusern, um die Anwendung für ihre Organisation bereitzustellen und zu konfigurieren.

Geschätzte Zeit, um diese Schritte auszuführen: **35–40 Minuten**.

## <a name="service-urls-for-us-government-customers"></a>Service-URLs für Kunden der US-Regierung

Die Lösung für Notfallmaßnahmen im Krankenhaus ist auch für Kunden der US-Regierung verfügbar. Der Zugriff auf Power Apps-Umgebungen der US-Regierung und Power BI findet über andere URLs statt als bei der kommerziellen Version.

Die kommerzielle Version der Service-URL wird in diesem Artikel verwendet. Wenn Sie ein Kunde der US-Regierung sind, verwenden Sie die entsprechende URL der US-Regierung für Ihre Bereitstellung wie folgt:


| **URl zur kommerziellen Version**                | **URL für Version für US-Regierungsbehörden**  |
|-------------------------------------------|--------------------------------|
| [https://make.powerapps.com](https://make.powerapps.com)                | [https://make.gov.powerapps.us](https://make.gov.powerapps.us) (GCC) <br/><br/>[https://make.high.powerapps.us](https://make.high.powerapps.us) (GCC hoch)                |
| [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) | [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us) (GCC)<br/><br/>[https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us) (GCC Hoch)|
| [https://app.powerbi.com/](https://app.powerbi.com/)                  | [https://app.powerbigov.us](https://app.powerbigov.us) (GCC)<br/><br/>[https://app.high.powerbigov.us](https://app.high.powerbigov.us) (GCC hoch)                 |

Detaillierte Informationen über die Pläne der US-Regierung für Power Apps und Power BI finden Sie unter:
- [Power Apps für US-Regierungsbehörden](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI für US-Regierungsbehörden](https://docs.microsoft.com/power-bi/service-govus-overview)


## <a name="step-1-download-the-deployment-package"></a>Schritt 1: Herunterladen des Bereitstellungspakets

> [!IMPORTANT]
> Wenn Sie die kommerzielle Version verwenden, können Sie diesen Schritt überspringen und stattdessen die Option AppSource verwenden, um die App und Power BI Dashboard zu installieren. 

Laden Sie das neueste Bereitstellungspaket (.zip) von <https://aka.ms/emergency-response-solution> herunter.

Bevor Sie die .zip-Datei extrahieren, stellen Sie sicher, dass Sie die Blockierung aufheben.

1.  Klicken Sie mit der rechten Maustaste auf die .zip-Datei und wählen Sie **Eigenschaften**.

2.  Wählen Sie im Dialogfeld „Eigenschaften“ die Option **Entsperren** aus und wählen Sie dann **Anwenden**, gefolgt von **OK** aus.

Wenn Sie die .zip-Datei extrahieren, sehen Sie in dem extrahierten Ordner Folgendes

|**Ordner**  |**Beschreibung**  |
|---------|---------|
|**Paket**     |  Enthält das Package Deployer Tool und das Paket, das Sie später bereitstellen werden, um die Lösung in Ihrer Umgebung einzurichten. Weitere Informationen: [Option C: Installieren der App aus dem Bereitstellungspaket](#option-c-install-the-app-from-the-deployment-package)     |
|**Power BIVorlage**     | Enthält die Power BI-Berichtsvorlagendatei (.pbit), die Sie zur Konfiguration der Berichterstattung verwenden werden. Weitere Informationen: [Schritt 10: Veröffentlichen Sie das Power BI Dashboard](#step-10-publish-the-power-bi-dashboard)        |

## <a name="step-2-sign-up-for-power-apps-and-create-an-environment"></a>Schritt 2: Registrieren für Power Apps und Erstellen einer Umgebung

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

## <a name="step-3-install-the-app"></a>Schritt 3: Installieren Sie die App

Befolgen Sie die folgenden Schritte, um die App Hospital Emergency Response zusammen mit der Konfiguration und den Beispieldaten zu installieren.

> [!NOTE]
> Die Konfigurations- und Beispieldaten werden nur bei einer Neuinstallation installiert. Wenn Sie eine vorherige Installation dieser App in Ihrer Umgebung haben, werden die Konfigurations- und Beispieldaten während der Installation nicht installiert, um sicherzustellen, dass Ihre vorhandenen Daten nicht überschrieben werden.

Sie können die App installieren, indem Sie eine der folgenden 3 Optionen verwenden:

- Microsoft AppSource (nur für Power Apps US Govt-Kunden). Siehe [Option A: Installieren Sie die App von Microsoft AppSource (US Govt Kunden)](#option-a-install-the-app-from-microsoft-appsource-us-govt-customers)

- Microsoft AppSource (für Power Apps Kunden der kommerziellen Version). Siehe [Option B: Installieren der Apps von Microsoft AppSource](#option-b-install-the-app-from-microsoft-appsource)

- Bereitstellungspaket, das Sie zuvor heruntergeladen haben. Siehe [Option C: Installieren der App aus dem Bereitstellungspaket](#option-c-install-the-app-from-the-deployment-package)

### <a name="option-a-install-the-app-from-microsoft-appsource-us-govt-customers"></a>Option A: Installieren der App von Microsoft AppSource (US Govt Kunden)

1.  Melden Sie sich beim Power Platform Admin-Zentrum an. Verwenden Sie die entsprechende URL zur Anmeldung:
    - **GCC**: [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us)
    - **GCC Hoch**: [https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us)

2.  Wählen Sie im linken Fensterbereich **Umgebungen** und wählen Sie dann den Namen der Umgebung, die Sie im vorherigen Schritt erstellt haben.

3. Wählen Sie auf der Detailseite der Umgebung **Dynamics 365 Apps verwalten**.

    > [!div class="mx-imgBorder"] 
    > ![Umgebungseinstellungen](media/ppac-env-setting.png "Umgebungseinstellungen")

3.  Wählen Sie auf der Seite Dynamics 365 Apps **Anwendung installieren**. Wählen Sie als nächstes **Power Platform Emergency Response App** im rechten Fensterbereich und wählen Sie **Weiter**.

    > [!div class="mx-imgBorder"] 
    > ![App installieren](media/ppac-install-app.png "App installieren")

4.  Stimmen Sie auf der nächsten Seite den Bedingungen zu und wählen Sie **Installieren**.

5.  Die Installation wird gestartet, und Sie können den Fortschritt der Installation Ihrer App auf der Seite Dynamics 365 Apps verfolgen.

    > [!div class="mx-imgBorder"] 
    > ![Installationsfortschritt der App überwachen](media/ppac-app-install-progress.png "Überwachen Sie den Fortschritt der Installation von Apps")

    > [!IMPORTANT]
    > Es kann eine Weile dauern, bis die App installiert ist.

6.  Nachdem die App installiert ist, navigieren Sie zu [Power Apps](https://make.powerapps.com) und wählen Sie Ihre Umgebung oben rechts aus. Sie finden neue Apps unter **Apps**:

    > [!div class="mx-imgBorder"] 
    > ![Neue Apps](media/conf-apps-new-apps.png "Neue Apps")

    Die Installation fügt auch die Konfigurations- und Beispieldaten für die App App Hospital Emergency Response hinzu.

### <a name="option-b-install-the-app-from-microsoft-appsource"></a>Option B: Installieren der Apps von Microsoft AppSource aus

1.  Navigieren Sie zu [AppSource](https://appsource.microsoft.com/), und suchen Sie nach der App "Hospital Emergency Response Apps".<br/>Alternativ können Sie über diesen Link direkt zur App auf AppSource navigieren: <https://appsource.microsoft.com/product/dynamics-365/mscrm.pphersapp>

2.  Wählen Sie auf der Seite Hospital Emergency Response Apps **Jetzt abrufen**.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/appsource-01.png "App auf AppSource")

3.  Sie werden aufgefordert, die Bedingungen der AppSource-Vereinbarung zu überprüfen. Das Dialogfeld zeigt auch das Konto an, das zur Anmeldung verwendet wird. Wählen Sie **Fortsetzen** aus. Möglicherweise werden Sie aufgefordert, Ihre Anmeldedaten zu überprüfen.

4.  Wählen Sie auf der nächsten Seite die Umgebung aus, in der Sie die Apps installieren möchten. Markieren Sie die Kontrollkästchen Rechtliche Bestimmungen und Datenschutzerklärungen und wählen Sie **Vereinbarung**.

    > [!div class="mx-imgBorder"] 
    > ![Eine Umgebung auswählen](media/appsource-02.png "Eine Umgebung auswählen")

5.  Sie werden zum Dynamics 365 Admin Center weitergeleitet, wo Sie den Fortschritt der Installation Ihrer Apps verfolgen können.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/appsource-03.png "Überwachen Sie den Fortschritt der Installation von Apps")

    > [!IMPORTANT]
    > Es kann eine Weile dauern, bis die App installiert ist.

6.  Nachdem die App installiert ist, navigieren Sie zu [Power Apps](https://make.powerapps.com) und wählen Sie Ihre Umgebung oben rechts aus. Sie finden neue Apps unter **Apps**:

    > [!div class="mx-imgBorder"] 
    > ![Neue Apps](media/conf-apps-new-apps.png "Neue Apps")

    Die Installation fügt auch die Konfigurations- und Beispieldaten für die App App Hospital Emergency Response hinzu.

### <a name="option-c-install-the-app-from-the-deployment-package"></a>Option C: Installieren der App aus dem Bereitstellungspaket

1.  Navigieren Sie zu dem Ort, an dem Sie das Paket [Bereitstellungspaket](#step-1-download-the-deployment-package) (.zip) extrahiert haben; Sie finden einen Ordner **Paket**. Führen Sie im Ordner **Package** die Datei **PackageDeployer.exe** aus, um das Tool zur Bereitstellung des Pakets zu starten.

2.  Wählen Sie auf dem nächsten Bildschirm **Fortfahren**.

3.  Sie werden aufgefordert, eine Verbindung zu Ihrer Umgebung herzustellen. Wählen Sie **Office 365** als **Bereitstellungsart**, wählen Sie **Erweitert anzeigen** und geben Sie dann Ihre Zugangsdaten ein, um sich mit Ihrer Umgebung zu verbinden.

    > [!div class="mx-imgBorder"] 
    > ![Paket bereitstellen](media/deploy-connect-to-environment.png "Paket bereitstellen"): Typ der abhängigen Komponente

4.  Wählen Sie **Anmelden**, um fortzufahren.

5.  Wenn Sie Zugriff auf mehr als eine Common Data Service-Umgebung haben, werden Sie im nächsten Bildschirm aufgefordert, die Umgebung auszuwählen, in der Sie das Paket installieren möchten. Wählen Sie eine Umgebung und wählen Sie **Anmelden**.

    > [!div class="mx-imgBorder"] 
    > ![Eine Umgebung auswählen](media/deploy-select-environment.png "Eine Umgebung auswählen")

6.  Wählen Sie auf dem nächsten Bildschirm **Weiter**

7.  Der nächste Bildschirm zeigt Ihnen den Namen der Umgebung an, in der das Paket installiert wird. Prüfen Sie die Informationen und wählen Sie **Weiter**.

8.  Auf dem nächsten Bildschirm wird überprüft, ob das Paket in Ihrer Umgebung installiert werden kann. Wählen Sie **Weiter**, um mit der Installation fortzufahren.

    > [!div class="mx-imgBorder"] 
    > ![Umgebung validieren](media/conf-validate-env.png "Umgebung validieren")

9.  Der nächste Bildschirm zeigt den Installationsstatus des Pakets an. Nachdem die Installation abgeschlossen ist, wählen Sie **Weiter**.

    > [!div class="mx-imgBorder"] 
    > ![Status der Installation](media/conf-package-install.png "Status der Installation")

    > [!NOTE]
    > Es kann eine Weile dauern, bis die Paketinstallation abgeschlossen ist. 

10.  Wählen Sie auf dem nächsten Bildschirm **Beenden**, um das Setup abzuschließen und zu schließen.

11.  Nachdem die App installiert ist, navigieren Sie zu [Power Apps](https://make.powerapps.com) und wählen Sie Ihre Umgebung oben rechts aus. Sie finden neue Apps unter **Apps**:

        > [!div class="mx-imgBorder"] 
        > ![Neue Apps](media/conf-apps-new-apps.png "Neue Apps")

        Die Installation fügt auch die Konfigurations- und Beispieldaten für die App App Hospital Emergency Response hinzu.

Wählen Sie die Option **Administrator-App** aus, um die modellgesteuerte App zu öffnen, mit der Sie den Rest der Bereitstellungseinstellungen konfigurieren können. Die Administrator-App verfügt über eine Reihe von Entitäten, mit denen Sie Daten für Ihr Krankenhaussystem hinzufügen und verwalten können. Sie können die Bereichsauswahl im unteren Teil des linken Navigationsbereichs verwenden, um einen anderen Bereich auszuwählen.

> [!div class="mx-imgBorder"] 
> ![Administrator-App öffnen](media/conf-admin-app-open.png "Administrator-App öffnen")

## <a name="step-4-update-the-mobile-app-branding-and-tracking-level"></a>Schritt 4: Aktualisieren Sie das Branding und die Verfolgungsebene der mobilen Apps

Sie können das App-Symbol, das Farbschema oder den Anzeigename der mobilen Apps ändern, um das Branding Ihres Unternehmens anzupassen. Sie können auch angeben, ob Frontline-Mitarbeiter mit Hilfe der mobilen Apps Informationen nach Standort oder Einrichtung verfolgen können. Sie verwenden dafür die Entitäten **App** und **App-Konfiguration** unter **Verwaltung**.

1.  Öffnen Sie die Administrator-App und wählen Sie im linken Navigationsbereich der Administrator-App die Option **Verwaltung** aus der Bereichsauswahl und dann **Apps** aus. Dies zeigt alle Canvas-App-Datensätze an, die Sie aus der Datei **App Import.xlsx** importiert haben.

    > [!div class="mx-imgBorder"] 
    > ![Administrator-Apps](media/conf-admin-app-records.png "Administrator-Apps")

1.  Öffnen Sie einen der App-Datensätze, indem Sie ihn auswählen. 

    > [!div class="mx-imgBorder"] 
    > ![Power App-ID-Feld ](media/conf-powerapp-id-field.png "App-Informationen aktualisieren")

1.  Auf der App-Detailseite:
 
    1. Doppelklicken Sie auf das App-Symbol und wählen Sie eine Symboldatei für die App aus dem Ordner **App-Symbole** aus. Die Bilddateien werden intuitiv benannt, sodass Sie leicht das richtige Symbol auswählen können. Wählen Sie beispielsweise die Datei „Emergency Response App.png“ für die **Emergency Response App** aus. Sie können auch ein benutzerdefiniertes Bild gemäß dem Branding Ihres Unternehmens auswählen.

    3. Aktualisieren Sie gegebenenfalls die **Beschreibung** oder den **Anzeigename** der App.

    4. Aktualisieren Sie gegebenenfalls den Wert **App im Menü ausblenden**, mit dem festgelegt wird, ob die App in der App-Liste angezeigt werden soll. Da die **Emergency Response App** eine Container-App ist, wird der Wert standardmäßig auf **Nein** gesetzt.

    5. Aktualisieren Sie gegebenenfalls den Wert **App-Anzeigerang** zum Festlegen der Anzeigeposition der App in der App-Liste.

    6. Wählen Sie bei Bedarf einen Wert im Feld **Nachverfolgungsebene** aus, um festzulegen, ob Sie Daten in dieser mobilen App auf der Ebene **Standort** oder **Einrichtung** nachverfolgen möchten. Weitere Informationen: [Verwalten der Nachverfolgungsebene für mobile Apps](configure-data-reporting.md#manage-tracking-level-for-mobile-apps)

    7. Wählen Sie **Speichern** aus.

1.  Wiederholen Sie die Schritte 2 und 3 für jeden Canvas-App-Datensatz unter **Apps**.

1.  Wählen Sie im linken Bereich die Option **App-Konfiguration** aus.

1.  Wählen Sie den **Emergency Response App**-Datensatz aus, um ihn zur Bearbeitung zu öffnen.

    1.  Aktualisieren Sie gegebenenfalls die Farben für Ihre App.

    2.  Wählen Sie **Ja** oder **Nein** im Feld **Gerätefreigabe aktiviert** aus, um anzugeben, ob eine Option zum **Abmelden** in mobilen Apps verfügbar ist oder nicht. Durch die Auswahl von **Ja** ist die Option **Abmelden** verfügbar. Weitere Informationen finden Sie im Benutzerhandbuch [Schicht beenden – abmelden](use.md#end-shift---sign-out).

    > [!div class="mx-imgBorder"] 
    > ![Feld Gerätefreigabe aktiviert](media/conf-device-sharing-enabled-field.png "Feld Gerätefreigabe aktiviert")

1.  Wählen Sie **Speichern** in der unteren rechten Ecke aus, um Ihre Änderungen zu speichern.

## <a name="step-5-bypass-consent-for-mobile-apps-optional"></a>Schritt 5: Zustimmung für mobile Apps umgehen (optional)

Optional können Sie konfigurieren, dass die Benutzerzustimmung für Ihre mobilen Apps umgangen wird, so dass Benutzer nicht für Standortberechtigungen zugelassen werden. Sie müssen ein Mandantenadministrator sein, um diesen Schritt abzuschließen. Bevor Sie diesen Schritt ausführen, benötigen Sie außerdem die App-ID jeder mobilen App (Canvas-App).

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

## <a name="step-6-add-azure-application-insights-key-to-mobile-apps-for-telemetry-optional"></a>Schritt 6: Azure Application Insights-Schlüssel zu mobilen Apps für Telemetrie hinzufügen (optional)

Optional können Sie Azure Application Insights zum Sammeln detaillierter Telemetrie für Ihre mobilen Apps (Canvas-Apps) verwenden, um Einblicke in die App-Nutzung zu erhalten. Detaillierte Informationen hierzu finden Sie unter [Analysieren der App-Telemetrie mit Application Insights](https://docs.microsoft.com/powerapps/maker/canvas-apps/application-insights).

## <a name="step-7-share-canvas-apps-with-users-in-your-organization"></a>Schritt 7: Freigeben der Canvas-Apps für Benutzer in Ihrer Organisation

Damit Ihre Benutzer an vorderster Front Daten mithilfe der Canvas-Apps auf ihren Mobilgeräten verwenden können, müssen die Apps für sie freigegeben werden. Es ist einfacher, Azure AD-Gruppen zu verwenden, um Apps einfach für Benutzergruppen freizugeben.

> [!IMPORTANT]
> Stellen Sie sicher, dass der Benutzer oder die Gruppe, für die Sie die Apps freigeben möchten, *bereits* Zugriff auf Ihre Umgebung hat. In der Regel haben Sie während des [Einrichtens Ihrer Umgebung](#step-2-sign-up-for-power-apps-and-create-an-environment) bereits Benutzer oder Gruppen hinzugefügt. Alternativ können Sie die folgenden Schritte ausführen, um Benutzer zu Ihrer Umgebung hinzuzufügen und einen entsprechenden Zugriff bereitzustellen, bevor Sie Apps für sie freigeben: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

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

## <a name="step-8-set-your-mobile-app-as-hero-and-featured-app-optional"></a>Schritt 8: Legen Sie Ihre mobile App als Hero- und Featured-App fest (optional)

Optional können Sie Ihre mobile App als Helden- und Featured App innerhalb der **Power Apps** mobilen App festlegen. Sie müssen ein Mandantenadministrator sein, um diesen Schritt abzuschließen.

Bevor Sie diesen Schritt ausführen, benötigen Sie die App-ID jeder mobilen App (Canvas-App), die Sie als herausragende und ausgewählte App festlegen möchten. Informationen über das Erhalten der App-ID für eine Canvas App finden Sie unter 

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
 

## <a name="step-9-share-model-driven-app-with-admins-in-your-organization"></a>Schritt 9: Freigeben der modellgesteuerten App für Administratoren in Ihrer Organisation

Damit Ihre Administratorbenutzer die Administrator-App (modellgesteuerte App) verwenden können, muss sie für sie freigegeben werden. Es ist einfacher, Azure AD-Gruppen zu verwenden, um Apps einfach für Administratorbenutzergruppen freizugeben.

> [!IMPORTANT]
> Stellen Sie sicher, dass der Benutzer oder die Gruppe, für die Sie die App freigeben möchten, *bereits* Zugriff auf Ihre Umgebung hat. In der Regel haben Sie während des [Einrichtens Ihrer Umgebung](#step-2-sign-up-for-power-apps-and-create-an-environment) bereits Benutzer oder Gruppen hinzugefügt. Alternativ können Sie die folgenden Schritte ausführen, um Benutzer zu Ihrer Umgebung hinzuzufügen und einen entsprechenden Zugriff bereitzustellen, bevor Sie die App für sie freigeben: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2. Wählen Sie im linken Navigationsbereich die Option Apps aus, um eine Liste aller Ihrer Apps anzuzeigen.

3. Wählen Sie die modellgesteuerte App (**Administrator-App – Emergency Response-App**) und dann **Freigeben** im Banner aus.

4. Geben Sie die Azure AD-Gruppen- oder -Administratorbenutzer, für die Sie diese App freigeben möchten, an, weisen Sie die Sicherheitsrolle **Emergency Response-Administrator** zu und wählen Sie **Freigeben** aus.

## <a name="step-10-publish-the-power-bi-dashboard"></a>Schritt 10: Veröffentlichen Sie das Power BI-Dashboard

Veröffentlichen Sie das Power BI-Dashboard und teilen Sie es mit Benutzern in Ihrer Organisation, damit diese das Dashboard für Einblicke und Entscheidungen verwenden können.

Sie können das Power BI-Dashboard mit einer der folgenden Optionen veröffentlichen: Verwenden der Vorlagen-App aus dem AppSource *oder* Verwendung der **.pbit**-Datei im Bereitstellungspaket.

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>Option A: Veröffentlichen mit der Vorlagen-App von AppSource (Bevorzugte Option)

Detaillierte Informationen zur Verwendung der Vorlagen-App aus AppSource ist hier verfügbar: [Dashboard zur Unterstützung von Notfallentscheidungen im Krankenhaus herstellen](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-health-emergency-response)

> [!IMPORTANT]
> Dies ist eine einfachere Möglichkeit zur Veröffentlichung des Power BI-Dashboards als die Verwendung der Option „.pbit-Datei“ zum Veröffentlichen. Wir empfehlen Kunden, diese Option zu verwenden, anstatt sie mit der Option „.pbit file“ zu veröffentlichen. 

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>Option B: Veröffentlichen mit der „.pbit-Datei“ im Bereitstellungspaket

Dieser Abschnitt enthält Informationen darüber, wie Sie die im Deployment-Paket verfügbare Datei **Emergency Response App.pbit** verwenden können, um das Dashboard bereitzustellen.

#### <a name="prerequisites"></a>Voraussetzungen

- Laden Sie das Bereitstellungspaket (.zip-Datei) von <https://aka.ms/emergency-response-solution> herunter. Nach dem Herunterladen extrahieren Sie die .zip-Datei auf Ihren Computer. Die .pbit-Datei ist im Ordner **Power BI-Vorlage** verfügbar

- Power BI-Premium-Kapazität oder Power BI-Pro-Lizenzen für Benutzer, die auf den Bericht zugreifen. 

- Erstellen Sie einen Arbeitsbereich in Power BI, in dem Sie den Bericht veröffentlichen. Melden Sie sich bei Power BI an und erstellen Sie einen Arbeitsbereich. Weitere Informationen: [Erstellen neuer Arbeitsbereiche in Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

- Installieren Sie Power BI Desktop aus dem Windows-App-Store: <https://aka.ms/pbidesktop>

   > [!NOTE] 
   > Wenn Sie Power BI Desktop installiert haben, indem Sie es in der Vergangenheit direkt von der Download Center-Seite als ausführbare Datei heruntergeladen haben, entfernen Sie es und verwenden Sie die aus dem Microsoft Store. Die Microsoft Store-Version wird automatisch aktualisiert, sobald neue Versionen verfügbar sind.
   >
   > Wenn Sie nicht aus dem Microsoft Store installieren können, installieren Sie die neueste Nicht-Microsoft Store-Version von der [Download Center-Webseite](https://www.microsoft.com/download/details.aspx?id=58494).

- Nachdem Sie Power BI Desktop aus dem App-Store installiert haben, führen Sie es aus und melden Sie sich mit einem Konto an, das zum Veröffentlichen von Power BI-Apps in Ihrer Organisation berechtigt ist.

#### <a name="publish-the-dashboard-using-the-pbit-file"></a>Dashboard mit der .pbit-Datei veröffentlichen

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

### <a name="after-publishing-the-dashboard"></a>Nach dem Veröffentlichen des Dashboards

Zum Anzeigen des veröffentlichten Power BI-Dashboards, siehe [Power BI-Dashboard anzeigen](configure-data-reporting.md#view-power-bi-dashboard)

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Hospital Emergency Response-Beispiel-App zu melden, navigieren Sie zu <https://aka.ms/emergency-response-issues>.

- Feedback zur Hospital Emergency Response-Beispiel-App finden Sie unter <https://aka.ms/emergency-response-feedback>.

## <a name="next-step"></a>Nächster Schritt

[Verwenden der Hospital Emergency Response-App](use.md)

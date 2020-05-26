---
title: Bereitstellen der Regional Government Emergency Response and Monitoring Lösung | Microsoft Docs
description: Enthält detaillierte Anweisungen für regionale IT-Admins zur Bereitstellung der Emergency Response and Monitoring-Lösung für Regional Government Emergency Response and Monitoring für ihre Organisation.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: 7c2d72201e9ae45e6d8957434aa9d4014cb593a6
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342065"
---
# <a name="deploy-the-regional-governmentemergency-response-and-monitoring-solution"></a>Stellen Sie die Lösung Regional Government Emergency Response and Monitoring bereit

IT-Administratoren regionaler Organisationen können diesen Artikel nutzen, um die Lösung Regional Government Emergency Response and Monitoring bereitzustellen. Am Ende dieses Bereitstellungsprozesses werden Sie über Folgendes verfügen:

- Eine Admin App (modellbasierte App), mit der Sie Stammdaten für übergeordnete Organisationen und deren Krankenhaussysteme konfigurieren und anzeigen sowie Admin-Benutzer von übergeordneten Organisationen hinzufügen und verwalten können, so dass diese das Portal zur Meldung von Daten für ihre Krankenhaussysteme nutzen können.

- Ein Webportal, das es einzelnen übergeordneten Organisationen ermöglicht, Daten in Bezug auf ihre Benutzer, Krankenhaussysteme, Regionen, Einrichtungen, Patienten, Materialien und Mitarbeiter hinzuzufügen und zu verwalten.

- Ein Power BI-Dashboard, auf das Ihre regionalen Admins in Ihrem Power BI-Mandanten zugreifen können, um Schlüsseldaten und Einblicke für alle übergeordneten Organisationen anzuzeigen, die Daten an Ihre regionale Organisation berichten. Dasselbe Dashboard ist in das Portal eingebettet, damit Admins von übergeordneten Organisationen Schlüsseldaten und Einblicke nur für ihre übergeordneten Organisationen und Krankenhaussysteme anzeigen können.

Führen Sie die folgenden Schritte aus, um die Regional Government Emergency Response and Monitoring-Lösung für Ihre Organisation bereitzustellen.

Geschätzte Zeit, um diese Schritte auszuführen: 35–40 Minuten.

> [!IMPORTANT]
> Wenn Sie diese Lösung bereits installiert haben, führen Sie stattdessen die folgenden Schritte aus, um auf die neueste Version zu aktualisieren: [Aktualisieren der Lösung](upgrade.md)

## <a name="service-urls-for-us-government-customers"></a>Service-URLs für Kunden der US-Regierung

Es gibt einen anderen Satz von URLs für den Zugriff auf Power Apps US Government-Umgebungen und Power BI US Government-Mandanten als die kommerzielle Version. In diesem Artikel wird die kommerzielle Version der Service-URLs verwendet. Wenn Sie eine Organisation der US-Regierung sind, verwenden Sie die entsprechende URL der US-Regierung für Ihre Bereitstellung, wie hier erwähnt:

| **URl zur kommerziellen Version**                | **URL für Version für US-Regierungsbehörden**  |
|-------------------------------------------|--------------------------------|
| [https://make.powerapps.com](https://make.powerapps.com)                | [https://make.gov.powerapps.us](https://make.gov.powerapps.us) (GCC)<br/><br/>[https://make.high.powerapps.us](https://make.high.powerapps.us) (GCC hoch)                |
| [https://admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) | [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us) (GCC)<br/><br/>[https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us) (GCC hoch) |
| [https://app.powerbi.com/](https://app.powerbi.com/)                  | [https://app.powerbigov.us](https://app.powerbigov.us) (GCC)<br/><br/>[https://app.high.powerbigov.us](https://app.high.powerbigov.us) (GCC hoch)                 |

Detaillierte Informationen über die Pläne der US-Regierung für Power Apps und Power BI finden Sie unter:

- [Power Apps für US-Regierungsbehörden](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI für US-Regierungsbehörden](https://docs.microsoft.com/power-bi/service-govus-overview)

## <a name="step-1-download-the-deployment-package"></a>Schritt 1: Herunterladen des Bereitstellungspakets

> [!IMPORTANT]
> Wenn Sie die kommerzielle Version verwenden, können Sie statt des Bereitstellungspakets die Option AppSource verwenden, um die App und das Power BI Dashboard zu installieren. Sie müssen noch das Bereitstellungspaket herunterladen, um die [Beispieldaten](configure.md##add-and-manage-master-data) zu verwenden.

Laden Sie das neueste Bereitstellungspaket (.zip) von <https://aka.ms/rer-solution> herunter.

Bevor Sie die .zip-Datei extrahieren, stellen Sie sicher, dass Sie die Blockierung aufheben.

1.  Klicken Sie mit der rechten Maustaste auf die .zip-Datei, wählen Sie **Eigenschaften**.

2.  Wählen Sie im Dialogfeld „Eigenschaften“ die Option **Entsperren** aus und wählen Sie dann **Anwenden**, gefolgt von **OK** aus.

    > [!div class="mx-imgBorder"] 
    > ![Lösungspaket-Eigenschaften](media/deploy-deployment-package.png "Eigenschaften des Lösungspakets")

Wenn Sie die .zip-Datei extrahieren, sehen Sie in dem extrahierten Ordner Folgendes

|**Ordner**  |**Beschreibung**  |
|---------|---------|
|**Paket**     |  Der Ordner enthält das Package Deployer-Tool und das Paket, das Sie später importieren, um die Lösung in Ihrer Umgebung einzurichten.       |
|**Power BIVorlage**     | Enthält die Power BI-Berichtsvorlagendatei (.pbit), die Sie zur Konfiguration der Berichterstattung verwenden werden. Weitere Informationen: [Schritt 5: Konfigurieren und Publizieren von Power BI Dashboard](#step-5-configure-and-publish-power-bi-dashboard)        |
|**SampleData**     |   Enthält die Beispielstammdatendateien (.xlsx), mit denen Sie Beispieldaten importieren können. Weitere Informationen: [Daten mit Beispieldateien importieren](configure.md#import-data-using-sample-files)      |

## <a name="step-2-sign-up-for-power-apps-and-create-an-environment"></a>Schritt 2: Registrieren für Power Apps und Erstellen einer Umgebung

Wenn Sie noch nicht Power Apps verwenden, registrieren Sie sich für Power Apps und erwerben Sie eine entsprechende Lizenz.
Weitere Informationen:

- [Power Apps-Preise](https://powerapps.microsoft.com/pricing/)

- [Kauf von Power Apps](https://docs.microsoft.com/power-platform/admin/signup-for-powerapps-admin)

Nachdem Sie Power Apps gekauft haben, erstellen Sie eine Umgebung mit einer Common Data Service-Datenbank.

1.  Melden Sie sich beim [Power Platform-Admin Center](https://aka.ms/ppac) an.

2.  Erstellen Sie eine Common Data Service-Umgebung mit der Datenbank. Weitere Informationen: [Erstellen und Verwalten von Umgebungen](https://docs.microsoft.com/power-platform/admin/create-environment)

    > [!IMPORTANT] 
    > Wenn Sie beim Erstellen der Datenbank eine Sicherheitsgruppe für die Datenbank auswählen, können die Apps nur gemeinsam mit Benutzern genutzt werden, die Mitglieder der Sicherheitsgruppe sind.

3.  Erstellen Sie geeignete Benutzer in Ihrer Umgebung. Weitere Informationen: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles)

Nachdem Sie Ihre Umgebung erstellt haben, können Sie über die folgende URL darauf zugreifen: https://[myenv].crm.dynamics.com, wobei [myenv] der Name Ihrer Umgebung ist. Notieren Sie sich die URL dieser Umgebung.

## <a name="step-3-create-a-power-apps-portal-in-your-environment"></a>Schritt 3: Erstellen Sie ein Power Apps-Portal in Ihrer Umgebung

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Stellen Sie sicher, dass Ihre neu erstellte Umgebung in der oberen rechten Ecke ausgewählt ist.

3.  Wählen Sie im linken Fensterbereich **Apps** und wählen Sie dann **Neue App** \> **Portal**.

    > [!div class="mx-imgBorder"] 
    > ![Power Apps Portal erstellen](media/deploy-create-powerapps-portal.png "Power Apps Portal erstellen")

4.  Geben Sie auf der Seite **Portal ohne Vorlage** die entsprechenden Werte an und wählen Sie dann **Erstellen**.

    > [!div class="mx-imgBorder"] 
    > ![Portal komplett neu erstellen](media/deploy-portal-from-blank.png "Portal komplett neu erstellen")

Power Apps beginnt mit der Bereitstellung des Portals für Sie, und die Fortschrittsmeldung wird in der oberen rechten Ecke der Seite angezeigt.

> [!NOTE]
> Es kann eine Weile dauern, bis Ihr Portal bereitgestellt ist.

Nachdem das Portal bereitgestellt wurde, erscheint es in Ihrer **Apps** Liste unter Power Apps. Sie können die Ellipsen (...) für Ihren Ausschnittdatensatz auswählen und **Durchsuchen** wählen, um das Starter-Portal anzuzeigen.

> [!div class="mx-imgBorder"] 
> ![Starter-Portal anzeigen](media/deploy-view-starter-portal.png "Starter-Portal anzeigen")

  > [!IMPORTANT]
  > Warten Sie, bis das Portal bereitgestellt ist, bevor Sie mit dem nächsten Schritt fortfahren.

## <a name="step-4-install-the-app"></a>Schritt 4: Installieren Sie die App

Installieren Sie nach der Bereitstellung Ihres Portals die Regional Government Emergency Response and Monitoring-App, um das zuvor erstellte Portal zu konfigurieren und die Admin-App (modellbasierte App) zu installieren.

Sie können die App installieren, indem Sie eine der folgenden 3 Optionen verwenden:

- Microsoft AppSource (nur für Power Apps US Govt-Kunden). Siehe [Option A: Installieren Sie die App von Microsoft AppSource (US Govt Kunden)](#option-a-install-the-app-from-microsoft-appsource-us-govt-customers)

- Microsoft AppSource (für Power Apps Kunden der kommerziellen Version). Siehe [Option B: Installieren der Apps von Microsoft AppSource](#option-b-install-the-app-from-microsoft-appsource)

- Bereitstellungspaket, das Sie zuvor heruntergeladen haben. Siehe [Option C: Installieren der App aus dem Bereitstellungspaket](#option-c-install-the-app-from-the-deployment-package)

### <a name="option-a-install-the-app-from-microsoft-appsource-us-govt-customers"></a>Option A: Installieren der App von Microsoft AppSource (US Govt Kunden)

1.  Melden Sie sich beim Power Platform Admin-Zentrum an. Verwenden Sie die entsprechende URL zur Anmeldung:
    - **GCC**: [https://gcc.admin.powerplatform.microsoft.us](https://gcc.admin.powerplatform.microsoft.us)
    - **GCC Hoch**: [https://high.admin.powerplatform.microsoft.us](https://high.admin.powerplatform.microsoft.us).

2.  Wählen Sie im linken Fensterbereich **Umgebungen** und wählen Sie dann den Namen der Umgebung, die Sie zuvor erstellt haben.

3. Wählen Sie auf der Detailseite der Umgebung **Dynamics 365 Apps verwalten**.

    > [!div class="mx-imgBorder"] 
    > ![Umgebungseinstellungen](media/ppac-env-setting.png "Umgebungseinstellungen")

3.  Wählen Sie auf der Seite Dynamics 365 Apps **Anwendung installieren**. Wählen Sie als danach rechts **Notfallmaßnahmen und Überwachung der regionalen Behörden** und danach **Weiter**.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/ppac-install-app.png "App installieren")

4.  Stimmen Sie auf der nächsten Seite den Bedingungen zu und wählen Sie **Installieren**.

5.  Die Installation wird gestartet, und Sie können den Fortschritt der Installation Ihrer App auf der Seite Dynamics 365 Apps verfolgen.

    > [!div class="mx-imgBorder"] 
    > ![Installationsfortschritt der App überwachen](media/ppac-app-install-progress.png "Überwachen Sie den Fortschritt der Installation von Apps")

    > [!IMPORTANT]
    > Es kann eine Weile dauern, bis die App installiert ist.

6.  Nachdem die App installiert ist, navigieren Sie zu [Power Apps](https://make.powerapps.com) und wählen Sie Ihre Umgebung oben rechts aus. Sie finden eine neue Admin-App in Ihrer Liste **Apps**.

    > [!div class="mx-imgBorder"] 
    > ![Neue Admin-App in der Apps-Liste](media/deploy-new-admin-app.png "Neue Admin-App in der Liste der Apps")

### <a name="option-b-install-the-app-from-microsoft-appsource"></a>Option B: Installieren der Apps von Microsoft AppSource aus

1.  Navigieren Sie zu [AppSource](https://appsource.microsoft.com/), und suchen Sie nach "Regional Govt Emergency Response".<br/>Alternativ können Sie über diesen Link direkt zur App auf AppSource navigieren: <https://appsource.microsoft.com/product/dynamics-365/mscrm.pprersapp>

2.  Wählen Sie auf der Seite Emergency Response and Monitoring der Regionalregierung **Jetzt abrufen**.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/deploy-appsource-01.png "App auf AppSource")

3.  Sie werden aufgefordert, die Bedingungen der AppSource-Vereinbarung zu überprüfen. Das Dialogfeld zeigt auch das Konto an, das zur Anmeldung verwendet wird. Wählen Sie **Fortsetzen** aus. Möglicherweise werden Sie aufgefordert, Ihre Anmeldedaten zu überprüfen.

4.  Wählen Sie auf der nächsten Seite die Umgebung aus, in der Sie die Apps installieren möchten. Markieren Sie die Kontrollkästchen Rechtliche Bestimmungen und Datenschutzerklärungen und wählen Sie **Vereinbarung**.

    > [!div class="mx-imgBorder"] 
    > ![Eine Umgebung auswählen](media/deploy-appsource-02.png "Eine Umgebung auswählen")

5.  Sie werden zum Dynamics 365 Admin Center weitergeleitet, wo Sie den Fortschritt der Installation Ihrer Apps verfolgen können.

    > [!div class="mx-imgBorder"] 
    > ![AppSource](media/deploy-appsource-03.png "Überwachen Sie den Fortschritt der Installation von Apps")

    > [!IMPORTANT]
    > Es kann eine Weile dauern, bis die App installiert ist.

6. Nachdem die App installiert ist, navigieren Sie zu [Power Apps](https://make.powerapps.com) und wählen Sie Ihre Umgebung oben rechts aus. Sie finden eine neue Admin-App in Ihrer Liste **Apps**.

    > [!div class="mx-imgBorder"] 
    > ![Neue Admin-App in der Apps-Liste](media/deploy-new-admin-app.png "Neue Admin-App in der Liste der Apps")

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

8.  Auf dem nächsten Bildschirm wird überprüft, ob ein Starterportal in Ihrer Umgebung verfügbar ist. Wählen Sie **Weiter**, um mit der Installation fortzufahren.

    > [!div class="mx-imgBorder"] 
    > ![Starterportal validieren](media/deploy-validate-starter-portal.png "Starter-Portal validieren")

9.  Der nächste Bildschirm zeigt den Installationsstatus des Pakets an. Bitte beachten Sie, dass es eine Weile dauern kann, bis die Paketinstallation abgeschlossen ist.

10. Nachdem die Installation abgeschlossen ist, wählen Sie **Weiter**.

11.  Wählen Sie auf dem nächsten Bildschirm **Beenden**, um das Setup abzuschließen und zu schließen.

12. Nachdem die App installiert ist, navigieren Sie zu [Power Apps](https://make.powerapps.com) und wählen Sie Ihre Umgebung oben rechts aus. Sie finden eine neue Admin-App in Ihrer Liste **Apps**.

    > [!div class="mx-imgBorder"] 
    > ![Neue Admin-App in der Apps-Liste](media/deploy-new-admin-app.png "Neue Admin-App in der Liste der Apps")

## <a name="step-5-configure-and-publish-power-bi-dashboard"></a>Schritt 5: Konfigurieren und Veröffentlichen von Power BI Dashboard

In diesem Schritt konfigurieren und veröffentlichen wir das Power BI Dashboard, damit es in das Portal eingebettet werden kann. Am Ende dieses Schritts verfügen Sie über eine Bericht-URL, die zum Einbetten des Berichts in das Portal verwendet wird.

Sie können das Power BI Dashboard mit einer der folgenden Optionen veröffentlichen: mit der Vorlage-App aus der AppSource oder mit der im Bereitstellungspaket verfügbaren .pbit-Datei.

### <a name="option-a-publish-using-the-template-app-from-appsource-preferred-option"></a>Option A: Veröffentlichen mit der Vorlagen-App von AppSource (Bevorzugte Option)

Ausführliche Informationen zur Verwendung der Vorlagen-App aus der AppSource finden Sie hier: [Verbinden Sie sich mit dem regionalen Dashboard für Notfallmaßnahmen](https://docs.microsoft.com/power-bi/connect-data/service-connect-to-regional-emergency-response)

### <a name="option-b-publish-using-the-pbit-file-in-the-deployment-package"></a>Option B: Veröffentlichen mit der „.pbit-Datei“ im Bereitstellungspaket

Dieser Abschnitt enthält Informationen darüber, wie Sie die Datei **Regional Emergency Response App.pbit**, die im Deployment-Paket zur Verfügung steht, zur Veröffentlichung des Dashboards verwenden können.

#### <a name="prerequisites"></a>Voraussetzungen

-   Sie müssen ein Global Admin sein und eine Power BI Pro-Lizenz besitzen, um Berichte konfigurieren und veröffentlichen zu können.

-   Erstellen Sie in Power BI einen Arbeitsbereich, in dem Sie den Bericht veröffentlichen werden. Melden Sie sich bei Power BI an und erstellen Sie einen Arbeitsbereich. Weitere Informationen:  [Erstellen neuer Arbeitsbereiche in Power BI](https://docs.microsoft.com/power-bi/service-create-the-new-workspaces)

-   Installieren Sie Power BI Desktop aus dem Microsoft Store: <https://aka.ms/pbidesktop>

    > [!NOTE]
    > Wenn Sie Power BI Desktop installiert haben, indem Sie es in der Vergangenheit direkt von der Download Center-Seite als ausführbare Datei heruntergeladen haben, entfernen Sie es und verwenden Sie die aus dem Microsoft Store. Die Microsoft Store-Version wird automatisch aktualisiert, sobald neue Versionen verfügbar sind.
    >
    > Wenn Sie nicht aus dem Microsoft Store installieren können, installieren Sie die neueste Nicht-Microsoft Store-Version von der Seite [Download Center](https://www.microsoft.com/download/details.aspx?id=58494).

#### <a name="the-process"></a>Das Verfahren

1.  Führen Sie Power BI Desktop aus und melden Sie sich mit Ihrem Konto an.

2.  Navigieren Sie zu dem Ort, an dem Sie das Paket [Bereitstellungspaket](#step-1-download-the-deployment-package) (.zip) extrahiert haben. Unter dem Power BI Vorlagenordner finden Sie die Datei **Regional Emergency Response App.pbit**.

3.  Öffnen Sie die **Regional Emergency Response App.pbit** -Datei in Power BI Desktop. Sie werden aufgefordert, den folgenden Wert einzugeben: **CDS_base_solution_URL**. Geben Sie die URL Ihrer Common Data Service Umgebung ein. Zum Beispiel, https://*[myenv]*.crm.dynamics.com, wobei *[myenv]* der Name Ihrer Umgebung ist. Wählen Sie **Laden.**

    > [!div class="mx-imgBorder"] 
    > ![Konfigurieren Sie das Power BI Dashboard](media/deploy-config-dashboard.png "Konfigurieren Sie Power BI Dashboard")

4.  Sie werden aufgefordert, Anmeldeinformationen einzugeben, um eine Verbindung zu Ihrer Common Data Service-Umgebung herzustellen. Wählen Sie **Organisationskonto** \> **Anmelden** , um Ihre Common Data Service-Anmeldeinformationen anzugeben.

    > [!div class="mx-imgBorder"] 
    > ![Verbinden mit Common Data Service Umgebung](media/deploy-connect-cds.png "Verbindung zu Common Data Service Umgebung")

5.  Nachdem Sie sich angemeldet haben, wählen Sie **Verbinden**, um eine Verbindung zu Ihren Daten in Common Data Service herzustellen.

6.  Bei erfolgreicher Verbindung wird der Bericht Power BI angezeigt. Sie werden aufgefordert, ausstehende Änderungen an Ihrer Anfrage vorzunehmen; wählen Sie **Änderungen vornehmen**.

    > [!NOTE]
    > Der Bericht ist leer, da Sie noch keine Daten in das System eingegeben haben.

7.  Wählen Sie **Veröffentlichen** um Daten in Ihrem Power BI Arbeitsbereich zu veröffentlichen. Sie werden aufgefordert, Ihre Änderungen zu speichern; wählen Sie **Speichern**.

     > [!div class="mx-imgBorder"] 
     > ![Arbeitsbereich von Power BI speichern](media/deploy-save-workspace.png "Power BI Arbeitsbereich speichern")

8.  Sie werden aufgefordert, die Datei zusammen mit Ihren Common Data Service-Umgebungsdaten als PBIX-Datei zu speichern. Geben Sie einen Namen ein und speichern Sie sie auf Ihrem Computer.

9.  Nach dem Speichern der PBIX-Datei werden Sie aufgefordert, den Bericht zu veröffentlichen. Wählen Sie auf der Seite **Veröffentlichen in Power BI** den Arbeitsbereich aus, in dem Sie veröffentlichen möchten, und klicken Sie dann auf **Auswählen**.

    > [!div class="mx-imgBorder"] 
    > ![Veröffentlichung an Power BI](media/deploy-publish-workspace.png "Veröffentlichen zu Power BI")

10.  Der Bericht ist dann in Ihrem Arbeitsbereich verfügbar. Jetzt konfigurieren wir die Datenaktualisierungseinstellungen für DataSet. Wählen Sie in Ihrem Arbeitsbereich unter **Datensätze** das Symbol **Aktualisierung planen** für den Datensatz Ihres soeben veröffentlichten Berichts.

      > [!div class="mx-imgBorder"] 
      > ![Bericht im Arbeitsbereich verfügbar](media/deploy-report-workspace.png "Bericht im Arbeitsbereich verfügbar")

11.  Wenn Sie zum ersten Mal versuchen, die Einstellung für die Datenaktualisierung festzulegen, sehen Sie die Seite **Einstellungen** mit einer Meldung, die besagt, dass Ihre Anmeldedaten nicht gültig sind. Wählen Sie unter **Datenquellen-Zugangsdaten** **Zugangsdaten bearbeiten**, um Ihre Zugangsdaten anzugeben.

      > [!div class="mx-imgBorder"] 
      > ![Anmeldeinformationen zur Datenquelle](media/deploy-datasource-credentials.png "Datenquellen-Anmeldeinformationen")

12.  Im nächsten Bildschirm:

      1.  Wählen Sie **Authentifizierung** Methode als **OAuth2**.

      2.  Wählen Sie **Datenschutzstufeneinstellungen für diese Datenquelle** als **Organisatorisch** aus.

      3.  Wählen Sie **Anmelden** aus.

13.  Sie werden aufgefordert, Ihre Anmeldeinformationen anzugeben und sich anzumelden. Nach erfolgreicher Anmeldung kehren Sie zur Seite **Einstellungen** zurück.

14.  Erweitern Sie auf der Seite **Einstellungen** die Option **Geplante Aktualisierung** und geben Sie die erforderlichen Details zum Aktualisieren von Daten basierend auf einem Zeitplan an. Wählen Sie **Übernehmen** aus.

      > [!div class="mx-imgBorder"] 
      > ![Aktualisierung der Daten planen](media/deploy-schedule-refresh-data.png "Planen Sie die Datenaktualisierung")

      > [!NOTE]
      > - Es gibt Grenzen, wie oft Daten aktualisiert werden können. Power BI begrenzt DataSets für gemeinsam genutzte Kapazität auf acht tägliche Aktualisierungen. Wenn sich das DataSet auf einer Premium-Kapazität befindet, können Sie in den DataSet-Einstellungen bis zu 48 Aktualisierungen pro Tag planen. Weitere Informationen:  [Daten aktualisieren](https://docs.microsoft.com/power-bi/refresh-data#data-refresh)
      >- Wir empfehlen, die Daten so einzustellen, dass sie alle 30 Minuten aktualisiert werden.

15.  Gehen Sie dann zurück zu Ihrem Arbeitsbereich, wählen Sie das Register **Berichte** und wählen Sie dann den Bericht, um ihn im Browser zu öffnen.

        > [!div class="mx-imgBorder"] 
        > ![Bericht im Browser öffnen](media/deploy-open-report.png "Bericht im Browser öffnen")

16.  Die URL hat das folgende Format: https://app.powerbi.com/groups/3d6db5d0-22c7-4674-b957-0605c021511d/reports/bf9cd5a1-c176-4786-9c4e-684a79678575/ReportSection?redirectedFromSignup=1<br/>
    Kopieren Sie die Power BI-Berichts-URL in Notepad, wie Sie sie im nächsten Abschnitt benötigen, um sie in das Portal einzubetten.

17. Wenn Sie möchten, dass dieser Power BI-Bericht anderen Benutzern innerhalb Ihres Power BI-Mandanten zur Verfügung steht, ziehen Sie in Betracht, den Bericht als App zu veröffentlichen. Wählen Sie im linken Bereich den Namen Ihres Arbeitsbereichs aus und wählen Sie dann **App erstellen** in der oberen rechten Ecke aus.  

18. Auf der Seite zur App-Veröffentlichung:

    1. Geben Sie auf der Registerkarte **Einrichtung** den Namen und die Beschreibung Ihrer App an.

    2. Geben Sie auf der Registerkarte **Navigation** den Ort an, an dem Sie es veröffentlichen möchten.

    3. Geben Sie auf der Registerkarte **Berechtigungen** die Benutzer oder Gruppen an, die diese App anzeigen können. Stellen Sie sicher, dass Sie das Kontrollkästchen **App automatisch installieren** aktivieren, um diese App automatisch für Endbenutzer zu installieren. Weitere Informationen: [Automatisches Installieren von Apps für Endbenutzer](https://docs.microsoft.com/power-bi/service-create-distribute-apps#automatically-install-apps-for-end-users)  

        > [!div class="mx-imgBorder"]
        > ![Apps automatisch auswählen, installieren](media/select-install-apps-automatically.png)

18. Wählen Sie **App veröffentlichen** aus. Ausführliche Informationen zum Veröffentlichen von Apps in Power BI finden Sie unter [Veröffentlichen der App](https://docs.microsoft.com/power-bi/service-create-distribute-apps#publish-your-app).


## <a name="step-6-embed-power-bi-report-in-portal"></a>Schritt 6: Power BI Bericht im Portal einbetten

In diesem Schritt werden wir den (im vorherigen Schritt veröffentlichten) Power BI-Bericht in Ihr Portal einbetten.

### <a name="prerequisites"></a>Voraussetzungen

- Sie müssen die Rolle von Global Admin haben, um diesen Schritt ausführen zu können.

- Bevor Sie einen Power BI-Bericht in ein Power Apps-Portal einbetten können, müssen **Power BI-Visualisierung** und **Power BI embedded-Dienst** für Ihr Portal über das [Power Apps-Portal-Admin-Center](https://docs.microsoft.com/powerapps/maker/portals/admin/admin-overview) aktiviert werden.

  > [!div class="mx-imgBorder"] 
  > ![Admin-Center für Power Apps-Portale](media/deploy-admin-center.png "Admin Center für Power Apps-Portale")

Eine Schritt-für-Schritt-Anleitung finden Sie in den folgenden Dokumenten des Power Apps-Portals:

-   [Power BI-Visualisierung aktivieren](https://docs.microsoft.com/powerapps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-visualization)

-   [Power BI embedded Dienst aktivieren](https://docs.microsoft.com/powerapps/maker/portals/admin/set-up-power-bi-integration#enable-power-bi-embedded-service)

### <a name="the-process"></a>Das Verfahren

Nachdem Sie nun sowohl die Power BI-Visualisierung als auch den Power BI Embedded-Dienst aktiviert haben, fügen wir nun die Berichts-URL zum Einbetten in Ihr Portal hinzu. Vergewissern Sie sich, dass Sie die URL des Power BI Berichts aus dem vorherigen Schritt zur Hand haben.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie im linken Fensterbereich **Apps**, und wählen Sie die App **Portalmanagement**, um sie zu öffnen.

    > [!div class="mx-imgBorder"] 
    > ![Portal-Management-App öffnen](media/deploy-open-mgmt-app.png "Portal Management App öffnen")

3.  Wählen Sie im linken Fensterbereich **Site-Einstellungen**, wählen Sie **Neu**:

    > [!div class="mx-imgBorder"] 
    > ![Neue Website-Einstellungen](media/deploy-site-settings.png "Neue Website-Einstellungen")

4.  Geben Sie auf der Seite **Neue Website-Einstellung** die folgenden Werte an:

    1.  **Name**: PowerBI Path

    2.  **Website**: Wählen Sie **Startportal**

    3.  **Wert**: Kopieren Sie die Power BI Berichts-URL aus dem vorherigen Schritt.

        > [!div class="mx-imgBorder"] 
        > ![Site-Einstellungswerte](media/deploy-site-setting-values.png "Website-Einstellwerte")

5.  Wählen Sie **Speichern und schließen**, um den Datensatz zu speichern.

### <a name="restart-the-portal"></a>Portal neu starten

Nun werden wir das Portal neu starten, damit die Änderungen wirksam werden.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie im linken Fensterbereich **Apps**, wählen Sie das Ellipsenmenü (...) für Ihr Portal und wählen Sie **Einstellungen**.

    > [!div class="mx-imgBorder"] 
    > ![Portalmenü Anwendungen](media/deploy-portal-menu.png "Menü des Apps-Portals")

3.  Wählen Sie im Fensterbereich **Portaleinstellungen** **Verwaltung**.

    > [!div class="mx-imgBorder"] 
    > ![Verwaltung der Portaleinstellungen](media/deploy-settings-admin.png "[Verwaltung der Portaleinstellungen")

4.  Wählen Sie im Power Apps Portale Admin-Center **Portal-Aktionen** \> **Neustart**.

    > [!div class="mx-imgBorder"] 
    > ![Neustart von Portal-Aktionen](media/deploy-portal-restart.png "Neustart von Portal-Aktionen")

5.  Wählen Sie **Neustart** in der Bestätigungsnachricht, um das Portal neu zu starten.

  > [!NOTE]
  > Optional können Sie auch eine Eitelkeits-URL für Ihr Portal einrichten, indem Sie einen benutzerdefinierten Domänennamen verwenden. Eine benutzerdefinierte Domäne kann Ihren Kunden helfen, die Supportressource einfacher zu finden und Ihre Marke sichtbarer zu machen. Ausführliche Informationen hierzu finden Sie unter [Eine benutzerdefinierte Domäne hinzufügen](https://docs.microsoft.com/powerapps/maker/portals/admin/add-custom-domain) in den Dokumenten zu Portalen.

## <a name="step-7-add-a-custom-title-and-logo-for-your-portal"></a>Schritt 7: Fügen Sie einen benutzerdefinierten Titel und ein Logo für Ihr Portal hinzu

Sie können ein benutzerdefiniertes Logo und einen benutzerdefinierten Titel zu Ihrem Portal hinzufügen, um es an die Marke Ihrer Organisation anzupassen.

> [!NOTE]
> Für das benutzerdefinierte Logobild wird als Farbe weiß-transparent mit einer Symbolrahmengröße von 40x40px und einer Symbolgröße von 24x24px mit 8px Füllung im SVG-Format empfohlen. Wenn Sie das PNG/JPG-Format für das Logo verwenden, verwenden Sie eine Symbolrahmengröße von 80x80px und eine Symbolgröße von 48x48px mit 16px Füllung.

### <a name="the-process"></a>Das Verfahren

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Öffnen Sie in der Liste Ihrer Apps die App **Portalverwaltung**.

3.  Wählen Sie links **Site-Einstellungen** und dann **Neu.**

4.  Geben Sie auf der Seite **Neue Website-Einstellung** die folgenden Werte an:

    1.  **Name**: SiteTitle

    2.  **Website**: Wählen Sie **Startportal**

    3.  **Wert**: Zeichenfolge, die in der linken oberen Ecke Ihres Portals erscheinen soll.

        > [!div class="mx-imgBorder"] 
        > ![Portal-Management-Website-Einstellungen](media/deploy-portal-site-settings.png "Portal-Management-Website-Einstellungen")
        
5.  Wählen Sie **Speichern**, um den Site Setting-Datensatz zu speichern.

6.  Wählen Sie **Neu**, um einen weiteren Site Setting-Datensatz zu erstellen.

7.  Geben Sie auf der Seite **Neue Website-Einstellung** die folgenden Werte an:

    1.  **Name**: SiteLogoPath

    2.  **Website**: Wählen Sie **Startportal**

    3.  **Wert**: Name Ihrer Logo-Bilddatei. Wenn Sie z.B. mylogo.png angeben, sucht das Portal nach dieser Datei im Stammverzeichnis des Portals. Wir werden die Logodatei später auf unser Portal hochladen.

        > [!div class="mx-imgBorder"] 
        > ![Neuen Datensatz für Website-Einstellungen erstellen](media/deploy-create-new-settings.png "[Neuen Datensatz für die Standort-Einstellungen erstellen")       

8.  Wählen Sie **Speichern und schließen**, um diesen Datensatz zu speichern und die Seite zu schließen.

9.  Jetzt werden wir die Logo-Bilddatei hochladen. Wählen Sie im linken Fensterbereich **Webdateien** und wählen Sie dann **Neu**.

10. Geben Sie auf dem Bildschirm **Neue Webdatei** die folgenden Werte an:

    1.  **Name**: mylogo.png

    2.  **Website**: Wählen Sie **Startportal**

    3.  **Übergeordnete Seite:** Wählen Sie **Einrichtung wählen**

    4.  **Teil-URL:** mylogo.png

        > [!IMPORTANT]
        > Stellen Sie sicher, dass dieser Wert mit dem Wert übereinstimmt, den Sie zuvor für die Einstellung **SiteLogoPfad** für die Suche nach weiteren Entitäten angegeben haben.

    5.  **Veröffentlichungsstatus**: Wählen Sie **Veröffentlicht**

        > [!div class="mx-imgBorder"] 
        > ![Neue Web-Datei](media/deploy-new-web-file.png "Neue Web-Datei")

11.  Wählen Sie **Speichern** aus, um den Datensatz zu speichern.

12.  Wählen Sie die Registerkarte **Notizen** und wählen Sie dann **+** gefolgt von **Notiz.**

      > [!div class="mx-imgBorder"] 
      >  ![Web Datei Anmerkungen](media/deploy-web-file-notes.png "Web-Datei-Notizen")

13.  Geben Sie in das Feld **Titel** mylogo.png ein. Wählen Sie das Symbol für die Anlage, um die Logo-Bilddatei von Ihrem Computer auszuwählen.

      > [!div class="mx-imgBorder"] 
      > ![Logo-Bild zuweisen](media/deploy-attach-logo.png "Logo-Bild anhängen")

14.  Wählen Sie das entsprechende Logo-Bild von Ihrem Computer aus (im .PNG-Format).
    Das ausgewählte Bild erscheint auf der Seite.

15.  Wählen Sie **Notiz hinzufügen**.

16.  Wählen Sie Speichern in der unteren rechten Ecke der Seite, um den Datensatz zu speichern.

Sie sind fertig. Es kann eine Weile dauern, bis der neueste Titel und das neueste Logo auf Ihrem Portal erscheinen. Aktualisieren Sie Ihr Portal in den nächsten 5-10 Minuten, um Ihren neuesten Titel und Ihr Logo zu sehen.

## <a name="step-8-add-a-custom-about-page-in-your-portal"></a>Schritt 8: Fügen Sie eine benutzerdefinierte Info-Seite in Ihrem Portal hinzu

Sie können eine benutzerdefinierte Info-Seite in Ihrem Portal hinzufügen, um Informationen oder Ressourcen für Ihre Benutzer hinzuzufügen/zu präsentieren.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie im linken Fensterbereich **Apps**, wählen Sie das Ellipsenmenü (...) für Ihr Portal und wählen Sie dann **Bearbeiten**. Dadurch wird die Portal-Konfigurationsseite geöffnet.

3.  Wählen Sie **Neue Seite** \> **Feste Layouts** \> **Über uns Seitenvorlage.**

    > [!div class="mx-imgBorder"] 
    > ![Über uns Seite](media/deploy-aboutus-page.png "Über uns Seite")
    

4.  Stellen Sie sicher, dass Sie auf der neuen Webseite **Über** im Feld **Teil-URL** im rechten Fensterbereich verwenden. Sie können einen Namen Ihrer Wahl im Feld **Name** verwenden; wir verwenden **Über Contoso**.

    > [!div class="mx-imgBorder"] 
    > ![Benutzen Sie in der Teil-URL](media/deploy-partial-url.png "Verwendung über in der Teil-URL")    

5.  Klicken Sie auf den linken Bereich, um den Inhalt zu bearbeiten. Sie können entweder den Standard-Editor verwenden oder **\</\>** in der rechten unteren Ecke wählen, um den HTML-Editor zu öffnen.

    > [!div class="mx-imgBorder"] 
    > !["Über uns" Seite bearbeiten](media/deploy-edit-aboutus.png "Seite "Über uns" bearbeiten")    

6.  Nachdem Sie die erforderlichen Änderungen an der Seite Info vorgenommen haben, speichern Sie sie und wählen Sie **Konfiguration synchronisieren** in der oberen rechten Ecke.

Die neu erstellte Seite "Info" kann von Ihren Portalbenutzern über den Link **Info** in der Kopfzeile des Portals aufgerufen werden.

## <a name="step-9-set-up-server-side-synchronization-of-emails"></a>Schritt 9: Einrichten der serverseitigen Synchronisierung von E-Mails

Die serverseitige Synchronisierung ermöglicht Ihnen die Synchronisierung von E-Mails in Common Data Service mit Microsoft Exchange Online, Microsoft Exchange Server (lokal) und POP3-E-Mail-Servern für im Web gehostete E-Mails wie Google Mail oder Outlook.com.

> [!div class="mx-imgBorder"] 
> ![E-Mail-Synchronisierung einrichten](media/deploy-email-synchronization.png "Einrichten der E-Mail-Synchronisation")

Detaillierte Schritte zur Einstellung der serverseitigen Synchronisierung finden Sie in den folgenden Ressourcen:

-   [Einrichten serverseitiger Synchronisierung](https://docs.microsoft.com/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks)

-   [Verbinden mit Exchange Online](https://docs.microsoft.com/power-platform/admin/connect-exchange-online)

-   [Verbindung zu Exchange Server (lokal)](https://docs.microsoft.com/power-platform/admin/connect-exchange-server-on-premises)

    > [!WARNING]
    > Stellen Sie sicher, dass dieser Benutzer nicht für die serverseitige Synchronisierung in einer anderen Common Data Service- oder Dynamics 365-Umgebung konfiguriert ist. Wenn Sie eine serverseitige Synchronisierung in einer anderen Umgebung eingestellt haben, deaktiviert die Aktivierung der serverseitigen Synchronisierung hier diese in der zuvor verwendeten Umgebung.

## <a name="step-10-fix-the-send-invitation-process"></a>Schritt 10: Fixieren Sie den Einladungsversand-Prozess

In diesem Schritt werden wir den Prozess **Einladung senden** festlegen, um die E-Mail-Adresse, von der die Portal-Einladung an die einzelnen Admins des Krankenhauses verschickt wird, und die Einladungs-URL, die in der Einladungs-E-Mail verschickt wird, zu spezifizieren.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie das Zahnrad für die Einstellungen in der oberen rechten Ecke und wählen Sie dann **Erweiterte Einstellungen.**

3.  Wählen Sie auf der Seite Einstellungen den Dropdown-Pfeil neben **Einstellungen** und wählen Sie **Prozesse**.

    > [!div class="mx-imgBorder"] 
    > ![Fix Einladungsvorgang senden](media/deploy-settings-processes.png "Fix Einladungsversand-Prozess")
    

4.  Suchen Sie auf der Seite **Prozesse** nach "Einladung senden" und wählen Sie den Prozess **Einladung senden**, um ihn zu öffnen.

5.  Auf der Seite zur Prozessdefinition:

    1.  Wählen Sie **Deaktivieren** in der Befehlsleiste, um den Prozess zu deaktivieren. Bestätigen Sie die Deaktivierung.

    2.  Unter dem Bereich Schritte wählen Sie **Eigenschaften festlegen** für den Schritt **E-Mail erstellen**:

        > [!div class="mx-imgBorder"] 
        > ![Eigenschaften für E-Mail erstellen festlegen](media/deploy-email-properties.png "Eigenschaften für E-Mail erstellen festlegen")

6.  Auf der Seite **E-Mail erstellen** Schrittdefinition:

    1.  Wählen Sie die E-Mail-ID im Feld **Ab**, die für den Versand der Portal-Einladungslinks verwendet wird. Für das hier angegebene Benutzerkonto muss die serverseitige Synchronisierung aktiviert sein, damit die E-Mail versendet werden kann.

        > [!TIP]
        >  Vielleicht möchten Sie ein Konto in Ihrer Umgebung mit aktivierter serverseitiger Synchronisierung und einer E-Mail-Adresse wie no-reply\@[*customerdomain*].com für den Versand von Portal-Einladungs-E-Mails einrichten.

    2.  Aktualisieren Sie die "https://**regionaldev**.powerappsportals.com" Zeichenfolge im E-Mail-Text mit der tatsächlichen URL Ihres Portals. Achten Sie auch darauf, dass Sie nicht den **Einladungscode kodieren** gelb markierten Inhalt ändern.

        Sie können bei Bedarf weitere Änderungen im E-Mail-Text vornehmen, um ihn an das Branding Ihrer Organisation anzupassen.

    3.  Wählen Sie **Speichern und schließen**, um Ihre Änderungen zu speichern.

        > [!div class="mx-imgBorder"] 
        > ![Aktualisierungs-URL Ihres Portals](media/deploy-update-url.png "Aktualisieren Sie die URL Ihres Portals")
        

3.  Sie kehren zur Prozessdefinitionsseite zurück. Speichern Sie die Änderungen und **Aktivieren** den Prozess.

    > [!div class="mx-imgBorder"] 
    > ![Aktivieren Sie den Prozess](media/deploy-activate-process.png "Aktivieren Sie den Prozess")    

## <a name="step-11-fix-the-send-password-reset-to-contact-process"></a>Schritt 11: Korrigieren Sie den Prozess zum Zurücksetzen des Sendekennworts an den Kontakt

In diesem Schritt werden wir den Prozess **Passwortrücksetzung an Kontakt senden** festlegen, um die E-Mail-Adresse anzugeben, von der die E-Mail zum Zurücksetzen des Portalpassworts an den Portalbenutzer gesendet wird, wenn er/sie beantragt, das Passwort über den Link **Passwort vergessen** im Portal zurückzusetzen.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie das Zahnrad für die Einstellungen in der oberen rechten Ecke und wählen Sie dann **Erweiterte Einstellungen.**

3.  Wählen Sie auf der Seite Einstellungen den Dropdown-Pfeil neben **Einstellungen** und wählen Sie **Prozesse**.

    > [!div class="mx-imgBorder"] 
    > ![Passwortzurücksetzung an Kontakt senden](media/deploy-password-reset.png "Kennwortzurücksetzung an Kontakt senden")
    <!-- ![](media/2ff3f6344a7ea9aa564592a15833fcb3.png) -->

4.  Suchen Sie auf der Seite **Prozesse** nach "Passwortrücksetzung an Kontakt senden" und wählen Sie im Suchergebnis den Prozess **Passwortrücksetzung an Kontakt senden**, um ihn zu öffnen.

5.  Auf der Seite zur Prozessdefinition:

    1.  Wählen Sie **Deaktivieren** in der Befehlsleiste, um den Prozess zu deaktivieren.
        Bestätigen Sie die Deaktivierung.

    2.  Wählen Sie unter dem Schrittbereich **Eigenschaften festlegen** für den Schritt **E-Mail senden**:

        > [!div class="mx-imgBorder"] 
        > ![Eigenschaften für E-Mail-Versand festlegen](media/deploy-set-email-properties.png "[Eigenschaften für E-Mail-Versand festlegen")
        <!-- ![](media/4a3c0bbf3785cdb7bad4c671964f0220.png) -->

6.  Entfernen Sie auf der Seite **E-Mail senden** für Schrittdefinition den dynamischen Wert (gelb markiert) im Feld **Von**.

    > [!div class="mx-imgBorder"] 
    > ![E-Mail-Schrittdefinition senden](media/deploy-email-step-definition.png "E-Mail-Schrittdefinition senden")
    <!-- ![](media/8838a0341e240cfe49741d64e761555d.png) -->

7.  Wählen Sie die E-Mail-ID im Feld **Ab**, die für den Versand der Portal-Einladungslinks verwendet wird. Für das hier angegebene Benutzerkonto muss die serverseitige Synchronisierung aktiviert sein, damit die E-Mail versendet werden kann.

    > [!TIP]
    > Möglicherweise möchten Sie in Ihrer Umgebung ein Konto mit aktivierter serverseitiger Synchronisierung und einer E-Mail-Adresse wie no-reply\@[*customerdomain*].com einrichten, um E-Mails mit Kennwortrücksetzung zu versenden.
    > Stellen Sie sicher, dass Sie die gelb markierten dynamischen Werte nicht aktualisieren. Optional können Sie den Inhalt des E-Mail-Textkörpers je nach Bedarf Ihrer Organisation im E-Mail-Textkörper aktualisieren.

    > [!div class="mx-imgBorder"] 
    > ![Dynamische Werte nicht aktualisieren](media/deploy-dynamic-values.png "Aktualisieren Sie keine dynamischen Werte")
    <!-- ![](media/35a0f7a386b2e5345158def083c62402.png) -->

8.  Wählen Sie **Speichern und schließen**, um Ihre Änderungen zu speichern.

9.  Sie kehren zur Prozessdefinitionsseite zurück. Speichern Sie die Änderungen und **Aktivieren** den Prozess.

    > [!div class="mx-imgBorder"] 
    > ![Änderungen speichern und Prozess aktivieren](media/deploy-save-activate-process.png "Änderungen speichern und Prozess aktivieren")    

## <a name="step-12-verify-assign-web-roles-to-new-users-process-is-enabled"></a>Schritt 12: Überprüfen Sie, ob der Prozess Webrollen an neue Benutzer zuweisen aktiviert ist

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie das Zahnrad für die Einstellungen in der oberen rechten Ecke und wählen Sie dann **Erweiterte Einstellungen.**

3.  Wählen Sie auf der Seite Einstellungen den Dropdown-Pfeil neben **Einstellungen** und wählen Sie **Prozesse**.

    > [!div class="mx-imgBorder"] 
    > ![Neuen Benutzern Webrollen zuweisen](media/deploy-assign-webroles.png "Weisen Sie neuen Benutzern Webrollen zu")    

4.  Suchen Sie auf der Seite **Prozesse** nach "Web zuweisen" und stellen Sie sicher, dass der Prozess **Neuen Benutzern Web-Rollen zuweisen** aktiviert ist.

    > [!div class="mx-imgBorder"] 
    > ![Sicherstellen, dass der Prozess aktiviert ist](media/deploy-process-enabled.png "Stellen Sie sicher, dass der Prozess aktiviert ist")    

5.  Wenn sie nicht aktiviert ist, wählen Sie den Prozessnamen, um den Datensatz zu öffnen, und wählen Sie dann **Aktivieren**. Bestätigen Sie, um den Prozess zu aktivieren.

## <a name="step-13-enable-the-flow-supply-tracking-flow"></a>Schritt 13: Aktivieren Sie den Nachverfolgungsfluss der Flow-Versorgung

1.  Melden Sie sich beim [Power Automate](https://flow.microsoft.com/) Admin-Zentrum an.

2.  Wählen Sie im linken Fensterbereich **Lösungen.** Wählen Sie aus der Lösungsliste **Regionale Notfallreaktionslösung**, um die Lösung zu öffnen.

    > [!div class="mx-imgBorder"] 
    > ![Öffnen Sie die Lösung](media/deploy-open-solution.png "Öffnen Sie die Lösung")

3.  Filtern Sie in der Lösung auf **Flüsse**, um den Datensatz **Nachverfolgung des Flusses** zu finden.

    > [!div class="mx-imgBorder"] 
    > ![Finden Sie den Datensatz zur Verfolgung der Flüsse im Flussangebot](media/deploy-find-record.png "Finden Sie den Datensatz zur Verfolgung von Flüssen")

4.  Wählen Sie den Namen des Flusses, um die Flussdefinition zu öffnen. Wählen Sie in der Flussdefinition **Bearbeiten** in der Symbolleiste.

5.  Reparieren Sie die Verbindung, die mit Common Data Service verbunden werden soll, und speichern Sie die Verbindungsinformationen.

6. Wählen Sie in der Flussdefinition **Einschalten**.

## <a name="step-14-update-the-details-of-flows-for-sending-emails"></a>Schritt 14: Aktualisieren Sie die Details der Flüsse für den E-Mail-Versand

In diesem Schritt werden wir Folgendes tun:

|Name des Flusses|Änderungen|
|--|--|
|**Portalbenutzeranforderung: E-Mail an Administratoren bei Ablehnung der Anforderung senden**|Aktualisieren Sie die Verbindung, mit der eine Verbindung zu Common Data Service hergestellt wird, und legen Sie dann ein Benutzerkonto zum Senden von E-Mails fest.|
|**Portalbenutzeranforderung: E-Mail an Administratoren bei Erstellung der Anforderung senden**|Aktualisieren Sie die Verbindung, mit der eine Verbindung zu Common Data Service hergestellt wird, und legen Sie dann ein Benutzerkonto zum Senden von E-Mails fest. Aktualisieren Sie außerdem die Portal-URL im E-Mail-Text gemäß Ihrer Portal-URL.| 

1.  Melden Sie sich beim [Power Automate](https://flow.microsoft.com/) Admin-Zentrum an.

2.  Wählen Sie im linken Fensterbereich **Lösungen.** Wählen Sie aus der Lösungsliste **Regionale Notfallreaktionslösung**, um die Lösung zu öffnen.

    > [!div class="mx-imgBorder"] 
    > ![Öffnen Sie die Lösung](media/deploy-open-solution.png "Öffnen Sie die Lösung")

3.  Filtern Sie in der Lösung auf **Fluss**, um die Flüsse zu finden. 

    > [!div class="mx-imgBorder"] 
    > ![Finden Sie den Datensatz zur Verfolgung der Flüsse im Flussangebot](media/deploy-find-record1.png "Finden Sie die Flüsse")

4.  Wählen Sie **Portal-Benutzeranfrage: E-Mail bei Ablehnungsanfrage senden** Name, um die Flussdefinition zu öffnen. Wählen Sie **Bearbeiten** in der Symbolleiste.

5.  Geben Sie die Verbindung an, die mit Common Data Service verbunden werden soll, indem Sie **Verbindungen** wählen und dann entweder die bestehende Verbindung verwenden oder einen neuen Berechtigungsnachweis verwenden, indem Sie **Neue Verbindung hinzufügen** wählen.  

    > [!div class="mx-imgBorder"] 
    > ![Berechtigungsnachweis fixieren](media/deploy-specify-cred.png "Zugangsdaten fixieren")

6.  Nachdem Sie die Verbindung für die Verbindung zu Common Data Service hergestellt haben, wählen Sie **IfRequestState ==** und geben Sie das Benutzerkonto an, das über ein Postfach-aktiviertes Konto zum Senden von E-Mails verfügt.

    > [!div class="mx-imgBorder"] 
    > ![Anmeldeinformationen angeben](media/deploy-fix-cred2.png "Angeben der Outlook-Zugangsdaten")

7. Wählen Sie **Speichern**, um die Änderungen zu speichern, und wählen Sie dann **Einschalten**.

8.  Gehen Sie als Nächstes zur Liste der Flüsse und wählen Sie **Portalbenutzeranforderung: E-Mail an Admins auf Anfrage senden Erstellung** Name, um die Flussdefinition zu öffnen. Wählen Sie **Bearbeiten** in der Befehlsleiste.

9.  Legen Sie die zu verbindende Verbindung auf Common Data Service fest, indem Sie **Verbindungen** wählen und dann entweder die bestehende Verbindung verwenden oder einen neuen Berechtigungsnachweis verwenden, indem Sie **Neue Verbindung hinzufügen** wählen.

10. Nachdem Sie die Verbindung für die Verbindung mit Common Data Service repariert haben:
     1. Wählen Sie **IfRequestState ==**
     2. Wählen Sie **Verbindungen**, um die Verbindung festzulegen, die mit Common Data Service verbunden werden soll 
     3. Wählen Sie **Verbindungen**, um die Anmeldedaten des Benutzerkontos anzugeben, für das ein Postfachkonto zum Senden von E-Mails aktiviert ist

    > [!div class="mx-imgBorder"] 
    > ![Anmeldeinformationen angeben](media/deploy-fix-cred3.png "Angeben der Outlook-Zugangsdaten")

11. Stellen Sie in **E-Mail senden** sicher, dass Sie die URL entsprechend der URL Ihres Portals festlegen. Ändern Sie in diesem Fall z.B. rer6 in Ihren URL-Wert.

    > [!div class="mx-imgBorder"] 
    > ![Anmeldeinformationen angeben](media/deploy-fix-cred4.png "Angeben der Outlook-Zugangsdaten")

12. Wählen Sie **Speichern**, um die Änderungen zu speichern, und wählen Sie dann **Einschalten**.

## <a name="step-15-share-admin-app-with-other-admin-users"></a>Schritt 15: Admin App mit anderen Admin-Benutzern teilen

Damit Ihre Admin-Benutzer die Admin-App (modellbasierte App) zur Eingabe und Verwaltung von Daten verwenden können, muss sie für sie freigegeben werden. Es ist einfacher, Azure AD-Gruppen zu verwenden, um Apps einfach für Administratorbenutzergruppen freizugeben.

> [!IMPORTANT]
> Stellen Sie sicher, dass der Benutzer oder die Gruppe, für die Sie die App freigeben möchten, bereits Zugriff auf Ihre Umgebung hat. In der Regel haben Sie während des Einrichtens Ihrer Umgebung bereits Benutzer oder Gruppen hinzugefügt. Alternativ können Sie die folgenden Schritte ausführen, um Benutzer zu Ihrer Umgebung hinzuzufügen und einen entsprechenden Zugriff bereitzustellen, bevor Sie die App für sie freigeben: [Erstellen von Benutzern und Zuweisen von Sicherheitsrollen](https://docs.microsoft.com/power-platform/admin/create-users-assign-online-security-roles).

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com) an.

2.  Wählen Sie im linken Navigationsbereich **Anwendungen**, wählen Sie die modellbasierte App (**Admin App - Regionale Notfallreaktions-App**) und wählen Sie **Freigeben** im Banner.

    > [!div class="mx-imgBorder"] 
    > ![Admin-App teilen](media/deploy-share-admin-app.png "Admin Apps freigeben")

3.  Geben Sie die Azure AD Gruppe oder Admin-Benutzer an, für die Sie diese App gemeinsam nutzen möchten, weisen Sie die Rolle **Regional Emergency Response Admin**Sicherheit zu und wählen Sie **Freigeben**.

    > [!div class="mx-imgBorder"] 
    > ![Azure AD Gruppe oder Admin-Benutzer angeben](media/deploy-specify-share.png "Geben Sie Azure AD-Gruppe oder Admin-Benutzer an")

## <a name="next-steps"></a>Nächste Schritte

Die Schritte zur Bereitstellung sind jetzt abgeschlossen. Business-Admins können sich auf das Thema [Konfiguration](configure.md) beziehen, um die folgenden Schritte durchzuführen:

-  Konfigurieren und Verwalten der Master-Daten

-   Erstellen Sie Portalbenutzer, um Admin-Benutzer aus einzelnen Krankenhäusern einzuladen, damit diese Portale zum Hinzufügen und Verwalten von Daten und Benutzern verwenden können.

- Zeigen Sie das Power BI-Dashboard in Ihrem Mandant an.

## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Lösung Regional Government Emergency Response and Monitoring zu melden, besuchen Sie <https://aka.ms/rer-issues>.

- Rückmeldungen über die Lösung Regional Government Emergency Response and Monitoring finden Sie unter <https://aka.ms/rer-feedback>.

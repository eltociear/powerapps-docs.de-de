---
title: Verwenden von Power BI mit modellgesteuerten Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/14/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- admin
search.app:
- D365CE
- Powerplatform
ms.openlocfilehash: a05a163e8f946f35f0b3b52d8978b1bf9be4fe8b
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755946"
---
# <a name="use-power-bi"></a>Verwenden von Power BI

Der Power BI-Clouddienst arbeitet mit Common Data Service-Apps, um eine Self-Service-Analyselösung bereitzustellen. Power BI aktualisiert automatisch die angezeigten Daten der App. Mit Power BI Desktop oder Microsoft Excel, Power Query für die Erstellung von Berichten und Power BI für die Freigabe von Dashboards und die Aktualisierung von Daten aus modellgetriebenen Anwendungen haben Ihre Benutzer eine leistungsstarke Möglichkeit, mit den Daten Ihrer App zu arbeiten.  
  
<a name="PowerBIGetstarted"></a>   
## <a name="get-started-using-power-bi-with-model-driven-apps"></a>Erste Schritte mit Power BI mit modellgesteuerten Apps  
 
Die Inhaltspakete der Dynamics 365-Apps für Power BI ermöglichen Ihnen einen einfachen Zugriff auf Ihre Daten in modellgesteuerten Apps in Dynamics 365 (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 Field Service, Dynamics 365 Marketing, Dynamics 365 Project Service Automation) und deren Analyse.  
  
 Um ein Power BI-Dashboard mit einem Content Pack zu erstellen, gehen Sie wie folgt vor.  
  
1. Wenn Sie es nicht bereits getan haben, [registrieren Sie sich für Power BI](https://powerbi.com/).  
  
2. Nachdem Sie sich bei Power BI angemeldet haben, wählen Sie im Bereich **Datensätze** **Daten holen**, unter **Dienste** **Abrufen**, und wählen Sie dann aus den folgenden Content-Packs.  
  
   - **Vertriebsanalyse für Dynamics 365**  
  
   - **Kundenserviceanalyse für Dynamics 365**  
  
   - **Microsoft Dynamics 365 – Social Engagement**  
  
3. Geben Sie für die Inhaltspakete Sales Analytics und Service Analytics die URL Ihrer Instanz ein, z.B. *<https://OrganizationName.crm.dynamics.com>*, wobei *OrganisationsName* der Organisationsname Ihrer Instanz ist, und wählen Sie **Weiter**.  
  
   > [!NOTE]
   >  Wenn sich Ihr Rechenzentrum außerhalb Nordamerikas befindet, kann der Domänenname crm.dynamics.com unterschiedlich sein, z.B. crm2.dynamics.com, crm3.dynamics.com, crm4.dynamics.com, etc. Um den Domainnamen zu finden, gehen Sie in der Apps Web App zu **Einstellungen** > **Anpassungen** > **Entwicklerressourcen**. Die aufgeführten URLs zeigen den richtigen Domänennamen an.  
  
    Geben Sie für das Marketing Content Pack die URL als *<https://OrganizationName.marketing.dynamics.com/analytics>* ein, wobei *OrganisationName* der Organisationsname Ihrer Instanz von Dynamics 365 ist, und wählen Sie **Next**.  
  
4. Wählen Sie unter **Authentifizierungsmethode** **oAuth2** aus.  
  
5. Ihre Instanzdaten werden importiert und mehrere Visualisierungen werden verfügbar.  
  
> [!TIP]
>  Wenn das Inhaltspaket, das Sie auswählen, nicht in Ihrem Webbrowser geöffnet wird, klicken Sie im linken Bereich Ihres Power BI-Arbeitsbereichs auf das Inhaltspaket unter **Dashboards**.  
  
### <a name="content-packs-available-for-download"></a>Inhaltspakete als Download verfügbar.  
 Die Inhaltspakete von Dynamics 365 unterstützen die standardmäßigen Out-of-Box-Elemente der App. Sie können die folgenden Inhaltspakete jedoch anpassen, indem Sie die .PBIX-Datei herunterladen und dann Power BI Desktop verwenden, um das Inhaltspaket anzupassen, bevor sie es zum Power BI-Service hochladen.  
  
- [Laden Sie die .PBIX-Datei für den Dynamics CRM Online-Vertriebsleiter herunter](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Sales%20Manager.pbix)  
  
- [Laden Sie Dynamics 365 for Customer Engagement-Apps (online) Servicemanager .PBIX herunter](https://download.microsoft.com/download/9/2/B/92BCBDCE-CE01-4BC9-A306-2A92653B683E/Customer%20Service%20Manager.pbix)  
  
  Die Power BI Berichtsvorlage für Connected Field Service ermöglicht es Benutzern, einen Power BI Bericht zu veröffentlichen, der den live Heart Beat der angeschlossenen Geräte anzeigt.  
  
- [Laden Sie das Power BI Report Template for Connected Field Service for Dynamics 365 for Customer Engagement herunter](https://download.microsoft.com/download/E/B/5/EB5ED97A-A36A-4CAE-8C04-333A1E463B4F/PowerBI%20Report%20Template%20for%20Connected%20Field%20Service%20for%20Microsoft%20Dynamics%20365.pbix)  
  
 Informationen dazu, wie die Inhaltspakete angepasst werden, finden Sie unter [Anpassen von Power BI-Inhaltspaketen](customize-power-bi-content-packs.md). 
  
<a name="BPI_embed"></a>   
## <a name="embed-power-bi-visualizations-on-personal-dashboards"></a>Integrieren von Power BI-Visualisierungen in persönliche Dashboards  
 Ehe Benutzer Power BI-Visualisierungen in persönliche Dashboards einbetten können, muss die organisationsweite Einstellung aktiviert werden.  
  
> [!NOTE]
>  Standardmäßig ist das Einbetten von Power BI-Visualisierungen deaktiviert und muss aktiviert werden, ehe Benutzer sie in ihre persönlichen Dashboards einbetten können.  
  
### <a name="enable-power-bi-visualizations-in-the-organization"></a>Aktivieren von Power BI-Visualisierungen in der Organisation  
  
1. Melden Sie sich bei Dynamics 365 als Benutzer mit der Sicherheitsrolle des Systemadministrators an.  
  
2. Gehen Sie zu **Einstellungen** > **Verwaltung** > **Systemeinstellungen**.  
  
3. Auf der Registerkarte **Berichterstellung** der Option**Einbettung von Power BI-Visualisierung zulassen** wählen Sie **Ja** für eine Aktivierung und **Nein** für eine Deaktivierung aus.  
  
4. Wählen Sie **OK** aus.  
  
Um mehr darüber zu erfahren, wie Sie Power BI-Kacheln zu persönlichen Dashboards hinzufügen können, siehe [Einbetten von Power BI-Kacheln in Ihr persönliches Dashboard](/powerapps/user/add-powerbi-dashboards#embed--power-bi-tiles-on-your-personal-dashboard).  
  
Weitere Informationen darüber, wie Sie Power BI-Dashboards zu persönlichen Dashboards hinzufügen können, finden Sie unter [Hinzufügen oder Bearbeiten von Power BI-Visualisierungen in Ihrem Dashboard](/powerapps/user/add-powerbi-dashboards).  
  
<a name="CRMOnline_PBIDesktop"></a>   
## <a name="use-power-bi-desktop-to-connect-directly-to-your-instance"></a>Verwenden Sie Power BI Desktop, um sich direkt mit Ihrer Instanz zu verbinden.  
 Sie können sich mit Power BI Desktop mit Ihrer Instanz verbinden, um benutzerdefinierte Berichte und Dashboards für den Dienst Power BI zu erstellen.  
  
### <a name="requirements"></a>Anforderungen  
  
- Power BI-Serviceregistrierung  
  
- Power BI Desktop  
  
- Dynamics 365-Instanz  
  
### <a name="connect"></a>Verbinden  
  
1. Starten Sie Power BI Desktop.  
  
2. Wählen Sie auf der Registerkarte Start **Daten abrufen**, und wählen Sie dann **Mehr**.  
  
3. Wählen Sie in der Liste "Daten abrufen" die Option **Dynamics 365 Online** aus.  
  
4. Geben Sie die URL des Dynamics 365 OData-Endpunkts ein. Es sollte ähnlich wie diese URL aussehen, wobei *OrganizationName* der Name Ihrer Organisation und **v9.0** die Version ist. Wählen Sie **OK** aus.  
  
    https://<em>OrganizationName</em>.api.crm.dynamics.com/api/data/*v9.0*  
  
> [!IMPORTANT]
> Weitere Informationen zu den unterschiedlichen Endpunktversionen finden sie unter [Web-API-URL und Versionen](/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#web-api-url-and-versions)
 
> [!TIP]
>  Sie können Ihre OData-Endpunkt-URL finden. Wechseln Sie zu **Einstellungen**  >  **Anpassungen**  >  **Entwicklerressourcen** und suchen Sie nach der URL unter **Instanz-Web-API**.  
  
5. Wählen Sie im Dialogfeld Zugriff auf einen ODaten-Feed **Organisationskonto**, und wählen Sie dann **Verbindung**.  
  
   > [!NOTE]
   >  Wenn Sie nicht in Ihrer Instanz angemeldet sind, wählen Sie **Anmeldung** im Dialogfeld OData-Feed aufrufen, bevor Sie Verbinden wählen.  
  
6. Die Organisationsdatenbankentitätstabellen werden im Power BI Desktop-Navigator angezeigt. Sie können Standard und benutzerdefinierte Entitäten auswählen. Weitere Informationen zum Erstellen von Berichten mit Power BI Desktop finden Sie unter [Power BI-Support: Berichtsansicht in Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-report-view/).  
  
   ![Entitätstabelle auswählen](media/pbi-select-entity-table.PNG "Entitätstabelle auswählen")  
  
   > [!TIP]
   >  Sie können ähnliche Schritte verwenden, um eine Verbindung zu Dynamics 365 mit Excel Power Query herzustellen, indem Sie **Aus anderen Quellen** auf der Registerkarte **Power Query** in Excel auswählen.  
  


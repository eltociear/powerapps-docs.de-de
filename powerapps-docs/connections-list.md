---
title: "Connectorübersicht | Microsoft-Dokumentation"
description: "Übersicht über die verfügbaren Verbindungen, die Sie verwenden können, um Apps zu erstellen"
services: 
suite: powerapps
documentationcenter: 
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 08/28/2017
ms.author: archanan
ms.openlocfilehash: e78cf64217d65ee90e9e463452ea62d7ee63df88
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="overview-of-connectors-for-powerapps"></a>Übersicht über die Connectors für PowerApps
Daten bilden das Herzstück der meisten Apps, u.a. bei denen, die Sie in PowerApps erstellen. Daten werden in einer *Datenquelle* gespeichert, und Sie übergeben diese Daten an Ihre App, indem Sie eine *Verbindung* erstellen. Die Verbindung verwendet einen bestimmten *Connector* für die Kommunikation mit der Datenquelle. PowerApps verfügt über Connectors für viele gängige Dienste und lokale Datenquellen, u.a. SharePoint, SQL Server, Office 365, Salesforce, Twitter und viele mehr. Die ersten Schritte zum Hinzufügen von Daten zu einer App werden unter [Hinzufügen einer Datenverbindung in PowerApps](add-data-connection.md) beschrieben.

Die folgende Tabelle enthält Links zu weiteren Informationen zu den am häufigsten verwendeten Connectors. Eine vollständige Liste der Connectors finden Sie unter [Alle Connectors](#all-connectors).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive for Business](./media/connections-list/onedrive.png) |[**OneDrive for Business**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Office 365-Benutzer](./media/connections-list/office365.png) |[**Office 365-Benutzer**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="types-of-connectors"></a>Connectortypen
PowerApps verfügt über zwei Arten von Connectors: *Standardconnectors* wie oben aufgeführt und *benutzerdefinierte Connectors*. Wenn Sie eine Verbindung mit einer Datenquelle herstellen, die von PowerApps mit einem Standardconnector unterstützt wird, verwenden Sie diesen Connector. Wenn Sie eine Verbindung mit einer anderen Quelle herstellen möchten, z.B. mit einem von Ihnen erstellten Dienst, finden Sie weitere Informationen unter [Registrieren und Verwenden von benutzerdefinierten Connectors](register-custom-api.md).

Standardconnectors verhalten sich unterschiedlich, abhängig vom Typ der verbundenen Datenquelle und davon, wie Daten von der Datenquelle zurückgegeben werden:

* Einige-Connectors funktionieren mit tabellarischen Datenquellen, z.B. SharePoint, SQL Server und Excel. Beim Arbeiten mit diesen Datenquellen werden Daten als Tabelle an PowerApps zurückgegeben. PowerApps verwendet eigene Funktionen, z.B. [Patch()](functions/function-patch.md), [Collect()](functions/function-clear-collect-clearcollect.md), [Update()](functions/function-update-updateif.md) usw. für die Interaktion mit den Daten. Tabellarische Daten können auch einfach in Formularen und Katalogen verwendet werden, in denen ein Feld in einer Tabelle als Feld in einem Katalog oder Formular angezeigt wird. Weitere Informationen finden Sie in den folgenden Artikeln:
  
    [Grundlegendes zu Datenquellen in PowerApps](working-with-data-sources.md)
  
    [Generieren einer App aus Excel-Daten](get-started-create-from-data.md)
  
    [App von Grund auf neu erstellen](get-started-create-from-blank.md)
  
    **Hinweis:** Zum Herstellen einer Verbindung mit Daten in Excel muss die Arbeitsmappe in einem Cloudspeicherdienst wie OneDrive gehostet werden. Weitere Informationen finden Sie im Artikel zum [Verbinden mit Cloudspeicher aus PowerApps](connections/cloud-storage-blob-connections.md).
* Andere Connectors funktionieren mit funktionsbasierten Datenquellen, z.B. Twitter, Facebook und Office 365 Outlook. Beim Arbeiten mit diesen Datenquellen werden Daten durch Aufrufen bestimmter Funktionen im zugrunde liegenden Dienst an PowerApps zurückgegeben. Mit dem Twitter-Connector können Sie z.B. `Twitter.MyFollowers()` aufrufen, um eine Liste Ihrer Follower zurückzugeben. Sie können diese Daten ebenfalls in einem Formular oder Katalog verwenden, dies ist jedoch etwas komplizierter als bei Tabellendaten. Weitere Informationen finden Sie im Artikel zum [Verbinden mit Twitter aus PowerApps](connections/connection-twitter.md).

## <a name="all-connectors"></a>Alle Connectors
Die folgende Tabelle enthält alle Connectors. Weitere Informationen zu den einzelnen Connectors finden Sie in der [Microsoft-Referenz zu Connectors](https://docs.microsoft.com/connectors/). Für Premium-Connectors ist PowerApps-Plan 1 oder 2 erforderlich. Weitere Informationen finden Sie auf der [Seite mit den PowerApps-Plänen](https://powerapps.microsoft.com/pricing/).

| &nbsp; | &nbsp; |
| --- | --- |
| 10to8 Appointment Scheduling<br>Act!<br>Adobe Creative Cloud ![Premium-Connector](./media/connections-list/premium.png)<br>Adobe Sign<br>Amazon Redshift ![Premium-Connector](./media/connections-list/premium.png)<br>Apache Impala ![Premium-Connector](./media/connections-list/premium.png)<br>AppFigures<br>Genehmigungen<br>Asana<br>AWeber ![Premium-Connector](./media/connections-list/premium.png)<br>Azure AD<br>Azure Application Insights<br>Azure Automation<br>Azure Blob Storage<br>Azure Cosmos DB<br>Azure Data Lake<br>Azure Event Grid<br>Azure Event Grid Publish<br>Azure File Storage<br>Azure Log Analytics<br>Azure Log Analytics-Datensammler<br>Azure-Warteschlangen<br>Azure Resource Manager<br>Azure Table Storage<br>Basecamp 2<br>Basecamp 3<br>Benchmark Email ![Premium-Connector](./media/connections-list/premium.png)<br>Bing Karten<br>Bing-Suche<br>Bitbucket ![Premium-Connector](./media/connections-list/premium.png)<br>Bitly<br>Bizzy (H3 Solutions, Inc.)<br>Blogger<br>Box<br>bttn<br>Buffer<br>Calendly ![Premium-Connector](./media/connections-list/premium.png)<br>Campfire<br>Capsule CRM ![Premium-Connector](./media/connections-list/premium.png)<br>Chatter ![Premium-Connector](./media/connections-list/premium.png)<br>Cognito Forms<br>Common Data Service ![Premium-Connector](./media/connections-list/premium.png)<br>Maschinelles Sehen-API<br>Inhaltskonvertierung<br>Content Moderator<br>DB2 ![Premium-Connector](./media/connections-list/premium.png)<br>Disqus<br>DocFusion365 – SP ![Premium-Connector](./media/connections-list/premium.png)<br>DocuSign ![Premium-Connector](./media/connections-list/premium.png)<br>Dropbox<br>Dynamics 365<br>Dynamics 365 for Financials<br>Dynamics for Operations<br>Dynamics NAV<br>Easy Redmine ![Premium-Connector](./media/connections-list/premium.png)<br>Elastic Forms<br>Event Hubs<br>Eventbrite ![Premium-Connector](./media/connections-list/premium.png)<br>Excel<br>Gesichtserkennungs-API<br>Facebook<br>Dateisystem<br>Flic<br>FlowForma ![Premium-Connector](./media/connections-list/premium.png)<br>FreshBooks ![Premium-Connector](./media/connections-list/premium.png)<br>Freshdesk<br>Freshservice ![Premium-Connector](./media/connections-list/premium.png)<br>FTP<br>GitHub<br>Gmail<br>Google Kalender<br>Google Kontakte<br>Google Drive<br>Google Tabellen<br>Google Tasks<br>GoToMeeting ![Premium-Connector](./media/connections-list/premium.png)<br>GoToTraining ![Premium-Connector](./media/connections-list/premium.png)<br>GoToWebinar ![Premium-Connector](./media/connections-list/premium.png)<br>Harvest ![Premium-Connector](./media/connections-list/premium.png)<br>HelloSign ![Premium-Connector](./media/connections-list/premium.png)<br>HipChat<br>HTTP mit Azure AD ![Premium-Connector](./media/connections-list/premium.png)<br>Informix ![Premium-Connector](./media/connections-list/premium.png)<br>Infusionsoft ![Premium-Connector](./media/connections-list/premium.png) |Inoreader<br>Insightly<br>Instagram<br>Instapaper<br>Intercom<br>JIRA ![Premium-Connector](./media/connections-list/premium.png)<br>JotForm ![Premium-Connector](./media/connections-list/premium.png)<br>LeanKit ![Premium-Connector](./media/connections-list/premium.png)<br>LinkedIn<br>LiveChat ![Premium-Connector](./media/connections-list/premium.png)<br>LUIS<br>Mail<br>MailChimp ![Premium-Connector](./media/connections-list/premium.png)<br>Mandrill ![Premium-Connector](./media/connections-list/premium.png)<br>Mittel<br>Microsoft Forms<br>Microsoft StaffHub<br>Microsoft Teams<br>Microsoft Translator<br>MSN Wetter<br>Muhimbi PDF<br>MySQL ![Premium-Connector](./media/connections-list/premium.png)<br>Nexmo ![Premium-Connector](./media/connections-list/premium.png)<br>Benachrichtigungen<br>Office 365 Buchungen<br>Office 365-Gruppen<br>Office 365 Outlook<br>Office 365-Benutzer<br>Office 365 Video<br>OneDrive<br>OneDrive for Business<br>OneNote (Business)<br>Oracle Database ![Premium-Connector](./media/connections-list/premium.png)<br>Outlook Customer Manager<br>Outlook-Aufgaben<br>Outlook.com<br>PagerDuty<br>Parserr<br>Paylocity ![Premium-Connector](./media/connections-list/premium.png)<br>Pinterest<br>Pipedrive ![Premium-Connector](./media/connections-list/premium.png)<br>Pitney Bowes Data Validation ![Premium-Connector](./media/connections-list/premium.png)<br>Pivotal Tracker<br>Planner<br>Plivo ![Premium-Connector](./media/connections-list/premium.png)<br>PostgreSQL ![Premium-Connector](./media/connections-list/premium.png)<br>Power BI<br>PowerApps-Benachrichtigung ![Premium-Connector](./media/connections-list/premium.png)<br>Project Online<br>Redmine<br>RSS<br>Salesforce ![Premium-Connector](./media/connections-list/premium.png)<br>SendGrid<br>Service Bus<br>SFTP<br>SharePoint<br>Skype for Business<br>Slack<br>SmartSheet<br>SMTP<br>SparkPost<br>SQL Server<br>Stripe ![Premium-Connector](./media/connections-list/premium.png)<br>SurveyMonkey ![Premium-Connector](./media/connections-list/premium.png)<br>Teamwork Projects ![Premium-Connector](./media/connections-list/premium.png)<br>Teradata ![Premium-Connector](./media/connections-list/premium.png)<br>Textanalysen<br>Todoist<br>Toodledo<br>Trello<br>Twilio<br>Twitter<br>TypeForm<br>UserVoice ![Premium-Connector](./media/connections-list/premium.png)<br>Videoindizierung<br>Vimeo<br>Visual Studio Team Services<br>WebMerge<br>WordPress<br>Wunderlist<br>Yammer<br>YouTube<br>Zendesk ![Premium-Connector](./media/connections-list/premium.png) |

Wenn Sie Fragen zu einem bestimmten Connector haben, lesen Sie die [PowerApps-Foren](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1). Wenn Sie eine Idee für einen neuen Connector oder Verbesserungsvorschläge haben, schreiben Sie uns unter [PowerApps Ideas](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).


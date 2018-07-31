---
title: Connectorübersicht | Microsoft-Dokumentation
description: Übersicht über die verfügbaren Verbindungen, die Sie verwenden können, um Apps zu erstellen
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 08/28/2017
ms.author: lanced
ms.openlocfilehash: 15da6ed2ce6b44c17645ac11d1b049b95e157703
ms.sourcegitcommit: 47be38a23c96ba7478fd777065f5db41181af40b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39164746"
---
# <a name="overview-of-connectors-for-powerapps"></a>Übersicht über die Connectors für PowerApps
Daten bilden das Herzstück der meisten Apps, u.a. bei denen, die Sie in PowerApps erstellen. Daten werden in einer *Datenquelle* gespeichert, und Sie übergeben diese Daten an Ihre App, indem Sie eine *Verbindung* erstellen. Die Verbindung verwendet einen bestimmten *Connector* für die Kommunikation mit der Datenquelle. PowerApps verfügt über Connectors für viele gängige Dienste und lokale Datenquellen, u.a. SharePoint, SQL Server, Office 365, Salesforce, Twitter und viele mehr. Die ersten Schritte zum Hinzufügen von Daten zu einer App werden unter [Hinzufügen einer Datenverbindung in PowerApps](add-data-connection.md) beschrieben.

Die folgende Tabelle enthält Links zu weiteren Informationen zu den am häufigsten verwendeten Connectors. Eine vollständige Liste der Connectors finden Sie unter [Alle Connectors](#all-connectors).

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive for Business](./media/connections-list/onedrive.png) |[**OneDrive for Business**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Office 365-Benutzer](./media/connections-list/office365.png) |[**Office 365-Benutzer**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="types-of-connectors"></a>Connectortypen
PowerApps verfügt über zwei Arten von Connectors: *Standardconnectors* wie oben aufgeführt und *benutzerdefinierte Connectors*. Wenn Sie eine Verbindung mit einer Datenquelle herstellen, die von PowerApps mit einem Standardconnector unterstützt wird, verwenden Sie diesen Connector. Wenn Sie eine Verbindung mit einer anderen Quelle herstellen möchten, z.B. mit einem von Ihnen erstellten Dienst, finden Sie weitere Informationen unter [Registrieren und Verwenden von benutzerdefinierten Connectors](../canvas-apps/register-custom-api.md).

Standardconnectors verhalten sich unterschiedlich, abhängig vom Typ der verbundenen Datenquelle und davon, wie Daten von der Datenquelle zurückgegeben werden:

* Einige-Connectors funktionieren mit tabellarischen Datenquellen, z.B. SharePoint, SQL Server und Excel. Beim Arbeiten mit diesen Datenquellen werden Daten als Tabelle an PowerApps zurückgegeben. PowerApps verwendet eigene Funktionen, z.B. [Patch()](functions/function-patch.md), [Collect()](functions/function-clear-collect-clearcollect.md), [Update()](functions/function-update-updateif.md) usw. für die Interaktion mit den Daten. Tabellarische Daten können auch einfach in Formularen und Katalogen verwendet werden, in denen ein Feld in einer Tabelle als Feld in einem Katalog oder Formular angezeigt wird. Weitere Informationen finden Sie in den folgenden Artikeln:

    [Grundlegendes zu Datenquellen in PowerApps](working-with-data-sources.md)

    [Generieren einer App aus Excel-Daten](get-started-create-from-data.md)

    [App von Grund auf neu erstellen](get-started-create-from-blank.md)

    > [!NOTE]
  > Zum Herstellen einer Verbindung mit Daten in Excel muss die Arbeitsmappe in einem Cloudspeicherdienst wie OneDrive gehostet werden. Weitere Informationen finden Sie im Artikel zum [Verbinden mit Cloudspeicher aus PowerApps](connections/cloud-storage-blob-connections.md).

* Andere Connectors funktionieren mit funktionsbasierten Datenquellen, z.B. Twitter, Facebook und Office 365 Outlook. Beim Arbeiten mit diesen Datenquellen werden Daten durch Aufrufen bestimmter Funktionen im zugrunde liegenden Dienst an PowerApps zurückgegeben. Mit dem Twitter-Connector können Sie z.B. `Twitter.MyFollowers()` aufrufen, um eine Liste Ihrer Follower zurückzugeben. Sie können diese Daten ebenfalls in einem Formular oder Katalog verwenden, dies ist jedoch etwas komplizierter als bei Tabellendaten. Weitere Informationen finden Sie im Artikel zum [Verbinden mit Twitter aus PowerApps](connections/connection-twitter.md).

## <a name="all-connectors"></a>Alle Connectors
Eine vollständige Liste der Connectors finden Sie in der [Microsoft-Referenz zu Connectors](https://docs.microsoft.com/connectors/). Für Premium-Connectors ist PowerApps-Plan 1 oder 2 erforderlich. Weitere Informationen finden Sie auf der [Seite mit den PowerApps-Plänen](https://powerapps.microsoft.com/pricing/).


Wenn Sie Fragen zu einem bestimmten Connector haben, lesen Sie die [PowerApps-Foren](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1). Wenn Sie eine Idee für einen neuen Connector oder Verbesserungsvorschläge haben, schreiben Sie uns unter [PowerApps Ideas](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas).

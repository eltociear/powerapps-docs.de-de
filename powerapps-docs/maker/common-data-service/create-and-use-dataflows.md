---
title: Erstellen und Verwenden von Dataflows in PowerApps | MicrosoftDocs
description: Informationen zum Erstellen und Verwenden von Dataflows in PowerApps
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5ad261f668c36e623b35e619e4d573401f3b547a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2705797"
---
# <a name="create-and-use-dataflows-in-powerapps"></a>Erstellen und Verwenden von Dataflows in PowerApps
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Mit der erweiterten Datenaufbereitung, die in PowerApps verfügbar ist, können Sie eine Datensammlung erstellen, Dataflow genannt, die Sie verwenden können, um eine Verbindung mit Geschäftsdaten aus verschiedenen Quellen herzustellen, die Daten zu bereinigen, sie zu transformieren und sie dann in Common Data Service oder das Azure Data Lake Gen2-Speicherkonto Ihrer Organisation zu laden.

Ein Dataflow ist eine Sammlung von Entitäten (Entitäten sind ähnlich wie Tabellen), die in Umgebungen im PowerApps-Service erstellt und verwaltet werden. Sie können Entitäten in Ihrem Dataflow hinzufügen und bearbeiten sowie Datenaktualisierungszeitpläne verwalten, und zwar direkt über die Umgebung, in der Ihr Dataflow erstellt wurde.

Nachdem Sie einen Dataflow im PowerApps-Portal erstellt haben, können Sie Daten darüber erhalten, indem Sie den Common Data Service-Konnektor oder den Power BI Desktop-Dataflow-Konnektor verwenden, je nachdem, welches Ziel Sie beim Erstellen des Dataflows ausgewählt haben.

Es gibt drei wesentliche Schritte zur Verwendung eines Dataflows:

1.  Erstellen Sie den Dataflow im PowerApps-Portal. Wählen Sie das Ziel aus, in das die Ausgangsdaten geladen werden sollen, die Quelle, von der die Daten abgerufen werden, und die Power Query-Schritte, um die Daten mithilfe von Microsoft-Tools zu transformieren, die eigens dafür ausgelegt sind.

2.  Zeitplan-Dataflow wird ausgeführt. Dies ist die Frequenz, mit der Power Platform-Dataflow die Daten aktualisieren soll, die in Ihrem Dataflow geladen und transformiert werden.

3.  Verwenden Sie die Daten, die Sie in den Zielspeicher geladen haben. Sie können Apps, Flows, Power BI-Berichte und Dashboards erstellen oder sie direkt mithilfe der Azure-Datendienste wie Azure Data Factory, Azure Databricks oder jedem anderen Dienst, bei dem der Common Data Model-Ordnerstandard unterstützt wird, mit dem Common Data Model-Ordner des Dataflows im Lake Ihrer Organisation verbinden.

In den folgenden Abschnitten werden die einzelnen Schritte genauer betrachtet, damit Sie sich mit den bereitgestellten Tools vertraut machen können, um die einzelnen Schritte ausführen zu können. 

## <a name="create-a-dataflow"></a>Erstellen eines Dataflows
Dataflows werden in einer Umgebung erstellt. Daher können Sie sie nur in dieser Umgebung sehen und verwalten. Darüber hinaus müssen Einzelpersonen, die Daten aus Ihrem Dataflow abrufen möchten, Zugriff auf die Umgebung haben, in der Sie diese erstellt haben.

> [!NOTE]
> Das Erstellen von Dataflows, bei denen Daten in Azure Data Lake Storage Gen2 in die Standardumgebung geladen werden, wird derzeit nicht unterstützt.

1.  Melden Sie sich in PowerApps an, überprüfen Sie, in welcher Umgebung Sie sich befinden, und suchen Sie nach dem Umgebungs-Schnellzugriff auf der rechten Seite der Befehlsleiste.

    ![Umgebungs-Schnellzugriff](media/environment-switcher.png)

2.  Wählen Sie im linken Navigationsbereich den Abwärtspfeil neben **Daten** aus.

    ![Datenauswahl](media/data-select.png)

3.  Wählen Sie in der Liste **Daten** die Option **Dataflows** und dann **Neuer Dataflow** aus.

    ![Erstellen eines Dataflows](media/create-a-dataflow.png)

4.  Wählen Sie auf der Seite **Ladeziel auswählen** den Zielspeicher aus, in dem die Entitäten gespeichert werden sollen. Dataflows können Entitäten in Common Data Service oder im Azure Data Lake Storage-Konto Ihrer Organisation speichern. Wenn Sie ein Ziel auswählen, in das die Daten geladen werden sollen, geben Sie einen **Namen** für den Dataflow ein, und wählen Sie dann **Erstellen** aus.

    ![Ladeziel auswählen](media/select-load-target.png)

     > [!IMPORTANT]
     > Es gibt nur einen Besitzer für einen jeweiligen Dataflow – und zwar die Person, die ihn erstellt hat. Nur der Besitzer kann den Dataflow bearbeiten. Die Autorisierung und der Zugriff auf Daten, die vom Dataflow erstellt werden, hängen vom Ziel ab, in das Sie die Daten geladen haben. Daten, die in Common Data Service geladen werden, sind über den Common Data Service-Konnector verfügbar und erfordern, dass die Person, die auf die Daten zugreift, für Common Data Service autorisiert wird.
     > Daten, die in das Azure Data Lake Gen2-Speicherkonto Ihrer Organisation geladen werden, sind über die Power Platform-Dataflow-Konnektor zugänglich. Der Zugriff darauf erfordert eine Mitgliedschaft innerhalb der Umgebung, in der sie erstellt wurden.

5. Wählen Sie auf der Seite **Datenquelle auswählen** die Datenquelle aus, in der die Entitäten gespeichert werden, und wählen Sie dann **Erstellen** aus. Durch die Auswahl der angezeigten Datenquellen können Sie Dataflow-Entitäten erstellen. 

    ![Auswählen einer Datenquelle](media/choose-data-source.png)

6. Wenn Sie eine Datenquelle ausgewählt haben, werden Sie aufgefordert, die Verbindungseinstellungen anzugeben, darunter das Konto, das Sie beim Verbinden mit der Datenquelle verwenden.

    ![Verbindung mit Datenquelle herstellen](media/data-source-provide-cred.png)

7. Sobald eine Verbindung hergestellt wurde, wählen Sie die Daten aus, die für Ihre Entität verwendet werden soll. Wenn Sie Daten und eine Quelle auswählen, verbindet sich der Power Platform-Dataflow-Service daraufhin wieder mit der Datenquelle, um die Daten in Ihrem Dataflow aktuell zu halten, und zwar in der Frequenz, die Sie später im Einrichtungsprozess auswählen.


    ![Auswählen von Daten](media/choose-data.png)

Sie haben nun die Daten ausgewählt, die bei der Entität verwendet werden sollen. Sie können den Dataflow-Editor verwenden, um diese Daten in das erforderliche Format für Ihren Dataflow zu formen oder zu transformieren.

## <a name="use-the-dataflow-editor-to-shape-or-transform-data"></a>Verwenden des Dataflow-Editors zum Formen oder Transformieren von Daten
Sie können Ihre Datenauswahl in eine Form bringen, die für Ihre Entität am besten funktioniert, und zwar mithilfe eines Power Query-Bearbeitungstools, ähnlich des Power Query-Editors in Power BI Desktop. Weitere Informationen über Power Query finden Sie unter [Abfrageübersicht in Power BI Desktop](/power-bi/desktop-query-overview).

Wenn Sie den Code sehen möchten, den der Abfrage-Editor mit jedem einzelnen Schritt erstellt, oder wenn Sie Ihren eigenen Formcode erstellen möchten, können Sie den erweiterten Editor verwenden.

![Erweiterter Editor](media/advanced-editor.png)

## <a name="dataflows-and-the-common-data-model"></a>Dataflows und das Common Data Model 
Dataflows-Entitäten enthalten neue Tools, mit denen Sie Ihre Geschäftsdaten ganz einfach dem Common Data Model zuordnen, sie mit Microsoft- und Drittanbieterdaten anreichern und einen vereinfachten Zugriff auf maschinelles Lernen erzielen können. Diese neuen Funktionen können genutzt werden, um intelligente und aktionsfähige Erkenntnisse in Ihre Geschäftsdaten bereitzustellen. Wenn Sie alle Transformationen im unten beschriebenen Schritt "Abfragen bearbeiten" abgeschlossen haben, können Sie Spalten aus Ihren Tabellen mit Datenquellen zu standardmäßigen Entitätsfeldern zuordnen, wie im Common Data Model beschrieben. Standardmäßige Entitäten haben ein bekanntes Schema, das vom Common Data Model definiert wird.

Weitere Informationen zu dieser Herangehensweise und zum Common Data Model finden Sie unter [Das Common Data Model](/powerapps/common-data-model/overview).

Um das Common Data Model mit Ihrem Dataflow zu nutzen, wählen Sie die Transformation **Dem Standard zuordnen** im Dialog **Abfragen bearbeiten** aus. Wählen Sie in dem daraufhin angezeigten Bildschrim **Entitäten zuordnen** die standardmäßige Entität aus, die Sie zuordnen möchten.

![Zuordnung zur standardmäßigen Entität](media/map-to-standard-entity.png)

Wenn Sie einer Quellspalte einem Standardfeld zuordnen, geschieht Folgendes:

1.  Die Quellspalte übernimmt den Namen des Standardfelds (die Spalte wird umbenannt, wenn die Namen unterschiedlich sind). 

2.  Die Quellspalte ruft den Datentyp des Standardfelds ab. 

Um die Standardentität von Common Data Model zu behalten, erhalten alle Standardfelder, die nicht zugeordnet sind, *Null*-Werte.

Alle Quellspalten, die nicht zugeordnet sind, bleiben unverändert, um sicherzustellen, dass das Ergebnis des Mappings eine Standardentität mit benutzerdefinierten Feldern ist.

Wenn Sie Ihre Auswahl abgeschlossen haben und Ihre Entität und deren Dateneinstellungen vollständig sind, sind Sie bereit für den nächsten Schritt. Dieser besteht darin, die Aktualisierungsfrequenz Ihres Dataflows auszuwählen.

## <a name="set-the-refresh-frequency"></a>Festlegen der Aktualisierungsfrequenz
Sobald die Entitäten definiert wurden, müssen Sie die Aktualisierungsfrequenz für jede Ihrer verbundenen Datenquellen planen.

1. Dataflows verwenden einen Datenaktualisierungsprozess, um die Daten aktuell zu halten. Im **Power Platform-Dataflow-Dokumenterstellungstool** können Sie Ihren Dataflow manuell oder automatisch in einem geplanten Intervall Ihrer Wahl aktualisieren. Um die Aktualisierung automatisch zu planen, wählen Sie **Automatisch aktualisieren** aus.

   ![Automatisch aktualisieren](media/refresh-automatically.png)

2. Geben Sie die Dataflow-Aktualisierungsfrequenz, das Startdatum und die Startzeit in UTC ein.

3. Wählen Sie **Erstellen** aus.
<!-- 
## Connect to your dataflow in Power BI Desktop
Once you’ve created your dataflow and you have scheduled the refresh frequency
for each data source that will populate the model, you’re ready for the final task, which is connecting to your dataflow from within Power BI Desktop.

To connect to the dataflow, in Power BI Desktop select **Get Data** > **Power Platform** > **Power Platform dataflows** > **Connect**.

![Connect to the dataflow](media/get-data.png)

Navigate to the environment where you saved your dataflow, select
the dataflow, and then select the entities that you created from the list.

You can also use the search bar, near the top of the window, to quickly find the
name of your dataflow or entities from among many dataflow entities.

When you select the entity and then select the **Load** button, the entities
appear in the **Fields** pane in Power BI Desktop, and appear and behave just
like tables from any other dataset. -->

## <a name="using-dataflows-stored-in-azure-data-lake-storage-gen2"></a>Verwenden von Dataflows in Azure Data Lake Storage Gen2
Einige Organisationen möchten unter Umständen ihren eigenen Speicher für das Erstellen und Verwalten von Dataflows verwenden. Sie können Dataflows in Azure Data Lake Storage Gen2 integrieren, wenn Sie die Anforderungen zum korrekten Einrichten des Speicherkontos einhalten. Weitere Informationen: [Verbinden von Azure Data Lake Storage Gen2 für den Dataflow-Speicher](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2) 

## <a name="troubleshooting-data-connections"></a>Problembehandlung bei Datenverbindungen
Es gibt Fälle, in dem beim Verbinden von Datenquellen für Dataflows Probleme auftreten. Dieser Abschnitt enthält Problembehandlungstipps.

-   **Salesforce-Konnektor.** Die Verwendung eines Testkontos für Salesforce bei Dataflows führt zu einem Verbindungsfehler ohne weitere Informationen. Um dieses Problem zu beheben, verwenden Sie ein Salesforce-Produktionskonto oder -Entwicklerkonto zum Testen.

-   **SharePoint-Konnektor.** Stellen Sie sicher, dass Sie die Stammadresse der SharePoint-Website angeben, ohne Unterordner oder Dokumente. Verwenden Sie beispielsweise einen ähnlichen Link wie *https://microsoft.sharepoint.com/teams/ObjectModel*.


-   **JSON-Dateikonnektor.** Derzeit können Sie eine JSON-Datei nur mithilfe einer Standardauthentifizierung verbinden. Beispielsweise wird eine ähnliche URL wie *https://XXXXX.blob.core.windows.net/path/file.json?sv=2019-01-01&si=something&sr=c&sig=123456abcdefg* nicht unterstützt.

-   **Azure SQL Data Warehouse.** Dataflows unterstützen derzeit nicht die Azure Active Directory-Authentifizierung für Azure SQL Data Warehouse. Verwenden Sie die Standardauthentifizierung für dieses Szenario.

## <a name="next-steps"></a>Nächste Schritte
Dei folgenden Artikel sind hilfreich für weitere Informationen und Szenarios zur Verwendung von Dataflows:

-   [Hinzufügen von Daten zu einer Entität in Common Data Service](data-platform-cds-newentity-pq.md)

-   [Verwenden von Dataflows mit lokalen Datenquellen](using-dataflows-with-on-premises-data.md)

-   [Verbinden von Azure Data Lake Storage Gen2 für Dataflow-Speicher](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)

Weitere Informationen zum Common Data Model:

-   [Common Data Model – Übersicht](/powerapps/common-data-model/overview)

-   [Weitere Informationen zum Common Data Model-Schema und zu Common Data Model-Entitäten bei GitHub](https://github.com/Microsoft/CDM)

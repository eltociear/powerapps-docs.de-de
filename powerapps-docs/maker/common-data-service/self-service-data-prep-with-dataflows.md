---
title: Self-Service Datenvorbereitung mit Dataflows in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Sie die Dataflows in PowerApps zur Aufbereitung Ihrer Daten verwenden können.'
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
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---


<!--note from editor: I think "dataflows" should be lowercase based on this entry in the Microsoft style guide (scroll down to find dataflows): https://styleguides.azurewebsites.net/Styleguide/Read?id=2696&topicid=42299 -->



# <a name="self-service-data-prep-with-dataflows"></a>Self-Service Datenaufbereitung mit Dataflows
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Mit dem wachsenden Datenvolumen wächst auch die Herausforderung, diese Daten in gut strukturierte, umsetzbare Informationen zu verwandeln. Sie benötigen Daten, die für Apps, KI-Workloads oder Analysen vorbereitet sind, damit Sie Datenmengen schnell in umsetzbare Erkenntnisse umwandeln können. Mit der Self-Service-Datenvorbereitung im PowerApps Portal können Sie Daten mit wenigen Klicks in Common Data Service oder das Azure Data Lake Storage Gen2-Konto Ihres Unternehmens transformieren und laden.

Dataflows wurden eingeführt, um Unternehmen dabei zu unterstützen, Daten aus unterschiedlichen Quellen zu vereinheitlichen und für den Verbrauch vorzubereiten. Sie können Dataflows mit vertrauten Self-Service-Tools erstellen, um große Datenmengen aufzunehmen, zu transformieren, zu integrieren und anzureichern. Beim Erstellen eines Dataflows definieren Sie Datenquellenverbindungen, ETL (Extrahieren, Transformieren, Laden) Logik und Ziel, in das die resultierenden Daten geladen werden sollen. Nach der Erstellung können Sie den Aktualisierungsplan eines Dataflows so konfigurieren, dass er angibt, wie oft er ausgeführt werden soll. Darüber hinaus macht die neue modellgetriebene Rechen-Engine den Prozess der Datenaufbereitung überschaubarer, deterministischer und für Dataflow-Kunden weniger schwerfällig. Mit Dataflows können Aufgaben, die früher von einer Daten-IT-Organisation erstellt und überwacht wurden (und viele Stunden oder Tage), nun mit wenigen Klicks von Personen erledigt werden, die nicht einmal Datenwissenschaftler sind, wie z.B. App-Ersteller, Business-Analysten und Reportgeneratoren.


Dataflows speichern Daten in Entitäten. Eine Entität ist eine Datensatzgruppe, in der Daten gespeichert werden, ähnlich zur Speicherung von Daten in einer Tabelle einer Datenbank. Kunden können benutzerdefinierte Entity-Schemata definieren oder die Standard-Entitäten des Common Data Model nutzen.
Das Common Data Model ist eine gemeinsame Datensprache, die von Geschäfts- und Analyseanwendungen verwendet wird. Das Metadatensystem des Common Data Model ermöglicht die Konsistenz von Daten und deren Bedeutung über Anwendungen und Geschäftsprozesse hinweg, wie beispielsweise PowerApps, Power BI, einige Dynamics 365-Anwendungen (modellgetriebene Anwendungen) und Azure, die Daten in Übereinstimmung mit dem Common Data Model speichern. Die resultierenden Entitäten eines Dataflows können dann in einer der folgenden Varianten gespeichert werden:

-   **Common Data Service.** Ermöglicht die sichere Speicherung und Verwaltung von Daten, die von Geschäftsanwendungen verwendet werden, die mit PowerApps und Microsoft Flow erstellt wurden.

-   **Azure Data Lake Storage Gen2.** Ermöglicht die Zusammenarbeit mit Personen in Ihrem Unternehmen über Power BI, Azure Data und AI-Dienste oder speziell entwickelte Branchenanwendungen, die Daten aus dem Lake lesen. Dataflows, die Daten in ein Azure Data Lake Storage Gen2-Konto laden, speichern Daten in [Common Data Model-Ordnern](https://go.microsoft.com/fwlink/?linkid=2045304). **Common Data Model Ordner** enthalten schematisierte Daten und Metadaten in einem standardisierten Format, um den Datenaustausch zu erleichtern und die volle Interoperabilität über Dienste hinweg zu ermöglichen, die Daten produzieren oder verbrauchen, die im Azure Data Lake Storage-Konto eines Unternehmens als gemeinsame Speicherschicht gespeichert sind.

Sie können Dataflows verwenden, um Daten aus einer großen und wachsenden Anzahl von unterstützten lokalen und Cloud-basierten Datenquellen wie Excel, Azure SQL Database, SharePoint, Azure Data Explorer, Salesforce, Oracle-Datenbank und mehr aufzunehmen.

Nach der Auswahl der Datenquelle können Sie die Power Query Low-Code/No-Code-Erfahrung nutzen, um die Daten zu transformieren und auf Standard-Entitäten im Common Data Model abzubilden oder eigene Entitäten zu erstellen. Fortgeschrittene Benutzer können die M-Sprache eines Dataflows direkt bearbeiten, um Dataflows vollständig anzupassen, ähnlich wie bei der Power Query, die Millionen von Power BI Desktop- und Excel-Benutzern bereits kennen.

Nachdem Sie einen Dataflow erstellt und gespeichert haben, müssen Sie ihn in der Cloud ausführen.
Sie können wählen, ob Sie einen Dataflow manuell auslösen oder die Häufigkeit für den Power Platform Dataflow Dienst für Sie planen möchten. Wenn ein Dataflow einen Lauf beendet, stehen seine Daten zur Verfügung. Um Dataflowdaten in Common Data Service zu laden, kann der Common Data Service-Konnektor in PowerApps, Microsoft Flow, Excel und allen anderen Anwendungen verwendet werden, die den Common Data Service-Konnektor unterstützen. Um von Dataflows zu profitieren, die im Azure Data Lake Storage Gen2-Konto Ihres Unternehmens gespeichert sind, können Sie den Power Platform Dataflow-Konnektor in Power BI Desktop verwenden oder direkt auf die Dateien im Lake zugreifen.

## <a name="how-to-use-dataflows"></a>Wie man Dataflows verwendet
Der vorherige Abschnitt lieferte Hintergrundinformationen zur Dataflow-Technologie. In diesem Abschnitt erhalten Sie einen Überblick darüber, wie Dataflows in einem Unternehmen verwendet werden können.

> [!NOTE]
> Sie müssen einen kostenpflichtigen PowerApps-Plan haben, um Dataflows zu verwenden, aber Sie werden nicht separat für die Verwendung von Dataflows berechnet. 

### <a name="load-data-to-common-data-service"></a>Daten auf Common Data Service laden
Dataflows können verwendet werden, um Entitäten in den [Common Data Service](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro) zu füllen, die dann in PowerApps Anwendungen verwendet werden. Mit wenigen Klicks können Sie Daten aus Online- und lokalen Datenquellen integrieren.

<!--from editor: In the last sentence above, should it change to "...on-premises data sources." ? -->


### <a name="extend-the-common-data-model-for-your-business-needs"></a>Erweiterung des gemeinsamen Datenmodells für Ihre Geschäftsanforderungen
Für Unternehmen, die das Common Data Model erweitern und darauf aufbauen wollen, ermöglichen Dataflows Business Intelligence-Experten, die Standard-Entitäten anzupassen oder neue zu erstellen. Dieser Self-Service-Ansatz zur Anpassung des Datenmodells kann dann zusammen mit Dataflows verwendet werden, um Power BI-Dashboards zu erstellen, die auf ein Unternehmen zugeschnitten sind.

### <a name="extend-your-capabilities-with-azure-data-and-ai-services"></a>Erweitern Sie Ihre Fähigkeiten mit Azure Data und AI Services.
Die Power Platform-Dataflows können so konfiguriert werden, dass sie Dataflow-Daten im Azure Data Lake Storage-Gen2-Konto Ihres Unternehmens speichern. Wenn eine Umgebung mit dem Data Lake Ihres Unternehmens verbunden ist, können Datenwissenschaftler und Entwickler leistungsstarke Azure-Produkte wie Azure Machine Learning, Azure Databricks, Azure Data Factory und mehr nutzen.

Weitere Informationen über die Azure Data Lake Storage Gen2- und Dataflowintegration, einschließlich der Erstellung von Dataflows, die sich im Azure Data Lake Ihrer Organisation befinden, finden Sie unter [Dataflows und Azure Data Lake-Integration (Vorschau)](/power-bi/service-dataflows-azure-data-lake-integration).

## <a name="summary-of-self-service-data-prep-for-big-data-in-powerapps"></a>Zusammenfassung der Self-Service Datenvorbereitung für Big Data in PowerApps.
Es gibt mehrere Szenarien und Beispiele, in denen Dataflows es Ihnen ermöglichen, eine bessere Kontrolle - und schnellere Einblicke - über Ihre Geschäftsdaten zu erhalten. Andere Personen in Ihrem Unternehmen können Dataflows entweder über Common Data Service, den Power Platform Dataflow-Konnektor in Power BI oder über den direkten Zugriff auf den Ordner **Common Data Service** von Dataflow im Azure Data Lake Storage Gen2-Konto Ihres Unternehmens nutzen. Unter Verwendung eines durch das Common Data Model definierten Standard-Datenmodells (Schema) können Geschäftsanwendungen vom Schema einer Entität abhängen und von der Art und Weise, wie die Daten erstellt wurden oder von welcher Datenquelle abstrahiert werden. Wenn ein Dataflow einen geplanten Lauf beendet, sind die Daten bereit für die Modellierung und Erstellung von Apps, Flows oder BI-Insights in sehr kurzer Zeit (was früher Monate oder länger gedauert hat).

Das standardisierte Format des Common Data Model ermöglicht es den Mitarbeitern in Ihrem Unternehmen, Anwendungen zu erstellen, die schnell, einfach und automatisch Visualisierungen und Berichte generieren. Diese beinhalten, sind aber nicht beschränkt auf:

-   Abbildung Ihrer Daten aus verschiedenen Quellen auf Standard-Entitäten im Common Data Model, um Daten zu vereinheitlichen und das bekannte Schema zu nutzen, um Out-of-the-Box-Anwendungen zu betreiben.

-   Erstellen Sie Ihre eigenen benutzerdefinierten Entitäten, um Daten in Ihrem Unternehmen zu vereinheitlichen.

-   Erstellung von Power BI-Berichten und Dashboards zur Nutzung von Dataflowdaten.

-   Erstellen der Integration mit Azure Data und AI-Services über das Azure Data Lake Storage Gen2-Konto Ihres Unternehmens.

## <a name="next-steps"></a>Nächste Schritte

Dieser Artikel gab einen Überblick über die Vorbereitung von Self-Service-Daten im PowerApps Portal und darüber, wie Sie diese nutzen können. In den folgenden Themen werden die üblichen Nutzungsszenarien für Dataflows näher erläutert:

-   [Erstellen und Verwenden von Dataflows in PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)

-   [Daten zu einer Entität in Common Data Service hinzufügen](https://go.microsoft.com/fwlink/?linkid=2100075)

-   [Verbinden Sie Azure Data Lake Storage Gen2 für die Dataflowspeicherung](https://go.microsoft.com/fwlink/?linkid=2099973)

-   [Dataflows mit lokalen Datenquellen verwenden](https://go.microsoft.com/fwlink/?linkid=2100077)

Weitere Informationen zu Power Query und geplanter Aktualisierung finden Sie in diesen Artikeln:

-   [Abfrageübersicht in Power BI Desktop](/power-bi/desktop-query-overview)

-   [Konfiguration der geplanten Aktualisierung ](/power-bi/refresh-scheduled-refresh)

Weitere Informationen zum Common Data Model finden Sie in seinem Übersichtsartikel:

-   [Common Data Model – Übersicht](/powerapps/common-data-model/overview)


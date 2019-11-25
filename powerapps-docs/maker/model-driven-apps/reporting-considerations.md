---
title: Überlegungen zur Berichterstattung | MicrosoftDocs
ms.custom: ''
ms.date: 09/27/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
- powerapps
ms.assetid: cb1bb002-8300-43bb-ab75-99e7a9c9c35d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: d3600ad3c1f0953ff3aef5786c62afebca43b4c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755045"
---
# <a name="reporting-considerations"></a>Berichterstellungsüberlegungen

Modellbasierte Anwendungen verfügen über eine Reihe von Funktionen, die es Kunden ermöglichen, Geschäftsdaten zu erfassen, die ihnen helfen, Entscheidungen zu treffen und effektiver mit ihren Kunden zu interagieren.  Zu den verfügbaren Funktionen gehören Ansichten, Diagramme, Dashboards und SQL Server Reporting Services-Berichte. Ebenfalls enthalten ist die Microsoft Excel-Integration, die es Benutzern ermöglicht, mit den Power BI-Funktionen [PowerView](https://support.office.com/article/power-view-overview-and-learning-5380e429-3ee0-4be2-97b7-64d7930020b6), [PowerPivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed) und [PowerQuery](https://support.office.com/article/power-query-overview-and-learning-ed614c81-4b00-4291-bd3a-55d80767f81d) einfach einen Self-Service Report zu erstellen. Mit zunehmendem Datenvolumen in der Datenbank der App wird es immer wichtiger, über Ihre BI-Strategie nachzudenken und die effektivsten Mechanismen für das Reporting und die Visualisierung großer Datensätze zu ermitteln.  
  
 In einer Umgebung wird die Berichtsinfrastruktur gemeinsam genutzt und von der Datenbank getrennt. In dieser Architektur wird jeder Bericht, auch wenn Kunden die zum Ausführen des Berichts erforderlichen Ressourcen teilen, für die einzelnen Datenbankinstanzen der Kunden ausgeführt.  Darüber hinaus können Benutzer beliebig viele Berichte ausführen, wann immer sie diese zur Erreichung der Geschäftsziele ausführen möchten.  Wir legen keine Zeiteinschränkungen für Berichte fest.  
  
 Die Berichterstellungsfunktionen, die in Common Data Service integriert sind, sind so konzipiert, dass Benutzer Berichte zu Datasets ausführen können, die kürzere Zeiträume beinhalten. Beachten Sie in diesem Zusammenhang die folgenden festen Einstellungen:  
  
- Berichte und für Abfragen können bis zu fünf Minuten ausgeführt werden. Wenn der Maximalzeitraum erreicht ist, gibt es einen Berichts-Timeout und eine Nachricht wird an den Benutzer zurückgegeben. Innerhalb der Dauer von fünf Minuten können Abfragen und Berichte große Datasets beinhalten mit über 50.000 Datensätzen, was eine erhebliche Flexibilität bedeutet, um die meisten Betriebsberichterstellungsanforderungen zu erfüllen.  
  
- Um die Abfrageantwort zu verbessern, ist es empfehlenswert, dass ausführliche Berichte die Anzeige vieler Datensätze minimieren. Wenden Sie hierzu eine passende Filterung an, um die Anzahl der Datensätze zu reduzieren, die zurückgegeben werden. Wenn Sie aggregierte oder zusammengefasste Berichte erstellen, sollten Abfragen die Aggregation an die Abfrage übertragen statt detaillierte Datensätze abzurufen, um eine Aggregation im Bericht auszuführen.  Dies kann ausgeführt werden, indem Sie eine FetchXML-Aggregation verwenden. <!-- More information: [Use FetchXML aggregation](../developer/use-fetchxml-aggregation.md)  -->
  
- Für Diagramme und Gitter, die in Dashboards angezeigt werden, ermöglichen Ihre Anwendungen Benutzern, Abfragen auszuführen, die einen Datensatz mit weniger als 50.000 Zeilen enthalten. Führt ein Benutzer eine Dashboardabfrage aus, die einen Datensatz von 50.000 oder mehr Zeilen umfasst, wird die Meldung "Die maximale Datensatzgrenze wird überschritten. Reduzieren Sie die Anzahl der Datensätze" wird zurückgegeben.  Die praktische Einstellung des Datensatzes hilft, eine optimale Leistung der App zu gewährleisten.  
 
  
<a name="BKMK_ReportTips"></a>   
## <a name="tips-and-solutions-for-reporting"></a>Tipps und Lösungen für die Berichterstellung  
 Diese Einstellungen sind für die meisten Berichterstellungsanforderungen der Organisationen normalerweise ausreichend. Damit die Benutzer diese Einstellungen nicht überschreiten und um die Berichtsabfrageleistung im Allgemeinen zu verbessern, sollten Sie die folgenden bewährten Methoden bedenken.  
  
- Wenn Sie benutzerdefinierte Berichte oder Dashboards erstellen, gestalten Sie sie so, dass sie kleinere Datasets über kürzere Zeiträume abfragen, indem Sie einen zeitbasierten Filter im Bericht hinzuzufügen, um die Ergebnisse einzuschränken, wie z. B. aktuellen Monat oder Quartal.  
  
- Es wird empfohlen, die Anzahl von Entitäten zu beschränken, die nötig sind, um das Ergebnis zurückzugeben. Dies erleichtert die Reduzierung der Zeit, die erforderlich ist, um die Abfrage auszuführen und den Ergebnissatz zurückzugeben.  
  
- Es wird empfohlen, die Anzahl der Datensätze zu verringern, die in den ausführlichen Berichten angezeigt werden. Passende Filterung kann verwendet werden, um die Anzahl der Datensätze zu verringern, die von der Abfrage zurückgegeben werden, um Timeouts zu reduzieren.  
  
- Für aggregierte oder zusammengefasste Berichte müssen Abfragen verwendet werden, um die Aggregation auf die Datenbank zu verschieben und nicht um detaillierte Datensätze zu holen und die Aggregation im SQL Server Reporting Services-Bericht durchzuführen.  
  
- Wenn es in Ihrem Unternehmen angemessen ist, sollten Benutzer die Standardberichte und -Dashboards ausführen. Diese Berichte und Dashboards sind in der Regel so konzipiert, dass sie Abfragen pro Benutzerdatasets ausführen, sodass sie die Datasetgrenze in den meisten Fällen nicht überschreiten.  
  
  Wenn Benutzer Berichte ausführen müssen, die diese Einstellungen überschreiten, empfehlen wir Ihnen, die folgenden Optionen zur Unterstützung bei komplexen Berichtsanforderungen zu überprüfen. Beide Optionen entlasten Berichts-Workloads effektiv von Common Data Service in einen anderen Datenspeicher, indem sie eine Datenintegrationslösung verwenden.  
  
- [Adapter](reporting-considerations.md#BKMK_ThirdPartyAdapt) werden in Verbindung mit SQL Server Integration Services (SSIS) verwendet, um die Möglichkeiten der Integration mit Ihren Apps-Daten zu erweitern.  
  
- [ETL-Tools](reporting-considerations.md#BKMK_ETL) bieten einen neuen Werkzeugsatz zur Erstellung von Datenanalysen durch Kombination mehrerer Datenquellen oder Extraktion von Daten in die Data-Warehouse-Lösung, wenn SSIS nicht verwendet wird. ETL-Tools bieten umfassende Lösungen für die Verbindung mit einem common data service zum Verschieben von Daten.  
  
> [!IMPORTANT]
>  Beachten Sie, dass Sie, wenn Sie diese Tools verwenden, Daten am besten außerhalb der Betriebszeiten verschieben oder synchronisieren.  
  
 Bei Bedarf gibt es viele Microsoft-Partner, die Ihnen helfen können, eine Lösung für Ihre spezifischen Berichtsanforderungen bereitzustellen, z.B. die Erstellung einer Offline-Kopie der Daten, die speziell für die Ausführung großer Berichte verwendet werden.  Diese Partner sind mit den verfügbaren Datenintegrationstools vertraut. Mehr Informationen: [Finden Sie einen Dynamics 365 Partner](https://dynamics.microsoft.com/partners/find-a-partner/)  
  
<a name="BKMK_ThirdPartyAdapt"></a>   
## <a name="third-party-adapters-for-ssis"></a>Adapter von Drittanbietern für SSIS  
  
-   [CozyRoc SSIS+ Komponente für Dynamics 365/CRM](https://www.cozyroc.com/ssis/dynamics-crm)  
  
-   [KingswaySoft SSIS Integration Toolkit für Dynamics 365](https://www.kingswaysoft.com/products/ssis-integration-toolkit-for-microsoft-dynamics-365)  
  
-   [CData SSIS-Komponenten für Dynamics 365](https://www.cdata.com/ssis/components/)  
  
-   [Team4 SSIS Connector für Dynamics 365](https://www.team4.de/microsoft-dynamics-365-crm/)  
  
<!--    [PragmaticWorks TaskFactory SSIS Source/Destination for Dynamics CRM](https://pragmaticworks.com/Products/Task-Factory/Features/DynamicsCRMSource.aspx)  -->
  
<a name="BKMK_ETL"></a>   
## <a name="etl-tools"></a>ETL-Tools  
  
-   [TIBCO Dynamics 365 Integration](https://www.tibco.com/solutions/microsoft-dynamics-365-integration)  <br />
  
<!--   [Productivity tools from Informatica](https://community.informatica.com/community/search.jspa?peopleEnabled=true&userID=&containerType=14&container=2002&spotlight=true&resultTypes=solution&q=dynamics+CRM)  -->
  
### <a name="see-also"></a>Siehe auch  
 [Berichterstellungserweiterung (mit SQL Server Data Tools-Unterstützung)](https://www.microsoft.com/download/details.aspx?id=45013) <br />
  
 [Einführung in Microsoft Power Query für Excel](https://office.microsoft.com/en-ca/excel-help/introduction-to-microsoft-power-query-for-excel-HA104003940.aspx?CTT=5&origin=HA104003813)   <br />
 [Dynamics 365 for Customer Engagement OData Feeds und Power Query: Was ist der [Datensatz]?](https://community.dynamics.com/crm/b/survivingcrm/archive/2014/02/16/dynamics-crm-odata-feeds-and-power-query-what-s-the-record.aspx)   <br />
 


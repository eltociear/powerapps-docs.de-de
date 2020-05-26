---
title: Anzeigen von Daten mit Visualisierungen (Diagrammen) (modellgesteuerte Apps) | Microsoft Docs
description: Mit Visualisierungen können Sie Ihre Geschäftsdaten grafisch anzeigen. Eine Visualisierung wird einer Entität in Common Data Service angefügt. Sie können mehrere Visualisierungen an eine Entität anfügen, jedoch kann jeweils nur eine Visualisierung neben einem Raster gleichzeitig angezeigt werden. Sie können gleichzeitig mehrere Visualisierungen anzeigen, indem Sie ein Dashboard verwenden.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: KumarVivek
ms.author: kvivek
manager: shilpas
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ea600e7ea7e9201c0bc5006eb2eb7cde32c4e2a4
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275802"
---
# <a name="view-data-with-visualizations-charts"></a>Daten mit Visualisierungen (Diagramme) anzeigen

Mit Visualisierungen können Sie Ihre Geschäftsdaten grafisch anzeigen. Eine Visualisierung wird einer Entität in Common Data Service angefügt. Sie können mehrere Visualisierungen an eine Entität anfügen, jedoch kann jeweils nur eine Visualisierung neben einem Raster gleichzeitig angezeigt werden. Sie können gleichzeitig mehrere Visualisierungen anzeigen, indem Sie ein Dashboard verwenden. Weitere Informationen: [Analyisieren von Daten mit Dashboards](analyze-data-with-dashboards.md)  
  
 Sie können ein Diagramm oder eine Webressource als Visualisierung in Common Data Service verwenden. Für Diagramme können Sie den Diagrammdesigner in „Modellgesteuerte Apps“ verwenden. Um jedoch eine Webressource in einer Visualisierung zu verwenden, müssen Sie entweder das SDK verwenden oder eine benutzerdefinierte Visualisierungs-XML in „Modellgesteuerte Apps“ importieren.
  
<a name="VisualizationTypes"></a> 

## <a name="visualization-ownership"></a>Visualisierungsbesitz  

In „Modellgesteuerte Apps“ stehen zwei Arten von Visualisierungsbesitz zur Verfügung: Besitz der Organisation und Besitz des Benutzers.  
  
- Eine Visualisierung im Besitz einer Organisation gehört einer Organisation und kann nicht zugewiesen oder freigegeben werden. Die `SavedQueryVisualization`-Entität stellt die Visualisierung im Besitz einer Organisation dar. Diese Visualisierungen sind lösungsbewusste Entitäten in „Modellgesteuerte Apps“. Wenn Sie eine gespeicherte Abfragenvisualisierung aktualisieren, müssen die Änderungen veröffentlicht werden, damit die Updates in der Organisation verfügbar sind, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.PublishAllXmlRequest>-Meldung verwenden. Diese Entität wird als *Systemdiagramm* in der „Modellgesteuerte Apps“-Webanwendung bezeichnet.  
  
- Eine Visualisierung im Besitz des Benutzers gehört einem einzelnen Benutzer und kann für andere Benutzer und Teams freigegeben und diesen zugewiesen werden. Die `UserQueryVisualization`-Entität stellt die Visualisierung im Besitz eines Benutzers dar. Diese Entität wird als ein *Benutzerdiagramm* in der „Modellgesteuerte Apps“-Webanwendung bezeichnet und unter **Meine Diagramme** in der Diagrammdropdownliste angezeigt.  
  
  Eine Benutzeranfragevisualisierung wird nicht einer Benutzeranfrage (Ansicht) zugeordnet, trotz des Entitätsnamens. Der Ansichtsaspekt dieser Entität wird nur zum Festlegen der Filterungskriterien verwendet.  
  
<a name="Charts"></a> 

## <a name="chart-visualizations"></a>Diagrammvisualisierungen 

Mit Diagrammen können Sie Zusammenfassungen von Rasterdaten anzeigen. Die Diagramme werden mithilfe von Microsoft Chart Controls für Microsoft .NET Framework 3.5 erstellt. Weitere Informationen zu Microsoft Chart Controls finden Sie unter [Download: Diagrammsteuerelemente für .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=128852).  
  
Diese Diagramme werden in die Rastern in der Webanwendung integriert. Falls Sie einen Filter (Abfrage) für die Daten in einem Raster anwenden, wird der Filter auch für das Diagramm angewendet, und das Diagramm entsprechend aktualisiert. Auch wenn Sie Vorgänge zum Anzeigen von Detailinformationen in einem Diagramm ausführen, werden die Rasterdaten automatisch aktualisiert.  
  
Ein Diagramm, das einer Entität angefügt wird, ist für alle Ansichten für die Entität verfügbar. Ein Diagramm zeigt Daten gemäß der derzeit ausgewählten (oder angezeigten) Ansicht einer Entität an. Ein Diagramm kann Daten aus einer gespeicherten Abfrage (Ansicht im Besitz der Organisation) und einer Benutzerabfrage (Ansicht im Besitz des Benutzers) anzeigen.  
  
Diagramme zeigen Daten nur für gespeicherte Abfragen (Ansichten im Besitz der Organisation) an, die FetchXML `SavedQuery.FetchXml`-Attribut) verwenden, um die Datensätze zu filtern. Wenn eine gespeicherte Abfrage die Abfrage-API (`SavedQuery.QueryAPI`-Attribut) zum Filtern der Datensätze verwendet, wird das Diagramm nicht für diese gespeicherte Abfrage angezeigt. Diese Beschränkung gilt nicht für Benutzerabfragen (Ansichten im Besitz des Benutzers), weil die Benutzerabfrageentität nicht das `QueryAPI`-Attribut zum Filtern der Datensätze verwendet.  
  
Weitere Informationen zum Arbeiten mit Diagrammen finden Sie unter [Diagramme: Zugrunde liegende Daten und Diagrammpräsentation](understand-charts-underlying-data-chart-representation.md).  
  
<a name="ChartTypes"></a>

### <a name="chart-types-in-microsoft-chart-controls"></a>Diagrammtypen in Microsoft-Diagrammsteuerelementen  

Microsoft Chart Controls wird verwendet, um Diagramme in modellgesteuerten Apps zu erstellen. Microsoft Chart Controls ermöglichen es Ihnen, verschiedene Diagrammtypen zu erstellen, wie z. B. Spalten, Balken, Bereich, gestapelt, Zeilen, Blasen und Kreis.  
  
Die folgenden Diagrammtypen werden standardmäßig in Common Data Service unterstützt: *Spalte*, *Bereich*, *Balken*, *Zeile*, *Kreis*, und*Trichter*. Sie können die Funktionalität aber erweitern, indem Sie weitere unterstützte Microsoft Chart Controls-Diagrammtypen wie Mehrfachdiagramme, gestapelte Diagramme und 100 % gestapelte (Vergleichs-) Diagramme erstellen, indem Sie entsprechende Inhalte in den Datenbeschreibungs- und den Darstellungsbeschreibungs-XML-Zeichenfolgen für ein Diagramm angeben. Weitere Informationen: [Angeben der Diagrammdaten](understand-charts-underlying-data-chart-representation.md)  
  
<a name="WebResources"></a>   
## <a name="web-resource-visualizations"></a>Webressourcenvisualisierungen  
 Webressourcen sind virtuelle Dateien, die in der Datenbank für „Modellgesteuerte Apps“ gespeichert sind und die Sie mithilfe einer eindeutigen URL-Adresse abrufen können. Sie können eine vorhandene Webressource als Visualisierung anzeigen und sie im Bereich **Diagramme** in „Modellgesteuerte Apps“ zusammen mit anderen Diagrammen für eine Entität anzeigen. Weitere Informationen zu Webressourcen finden Sie unter [Webressourcen für modellgesteuerte Apps](web-resources.md).  
  
 Die folgenden Typen von Webressourcen können in einer Visualisierung verwendet werden: [Webressourcen der Webseite (HTML)](webpage-html-web-resources.md) und [Bild (JPG, PNG, GIF, ICO)-Webressourcen](image-web-resources.md). Weitere Informationen zum Erstellen einer Visualisierung mit einer Webressource finden Sie unter [Erstellen einer Webressourcen-Visualisierung](create-visualization-chart.md#create-a-web-resource-visualization).  
  
<a name="SupportedVisualizationEntities"></a>  

## <a name="entities-supported-for-visualizations"></a>Für Visualisierungen unterstützte Entitäten 

Sie können Visualisierungen erstellen und diese nur an die Entitäten in Common Data Service anfügen, die die neue Menübandschnittstelle unterstützen. Dies ist darauf zurückzuführen, dass Diagrammsteuerelemente nur in der Menübandschnittstelle von Common Data Service verfügbar sind. Benutzerdefinierte Entitäten werden ebenfalls für Visualisierungen unterstützt. Sie können für benutzerdefinierte Entitäten die Visualisierungsunterstützung deaktivieren, wenn Sie dies wünschen. Allerdings können Sie die Visualisierungsunterstützung nicht für standardmäßige Entitäten deaktivieren.  
  
 Nachfolgend werden die standardmäßigen Entitäten aufgeführt, die für Visualisierungen unterstützt werden.  
  
 Konto  
ActivityPointer  
Termin  
BulkOperation  
Kampagne  
CampaignActivity  
CampaignResponse  
Mitbewerber  
Verbindung  
Kontakt  
Vertrag  
Per E-Mail senden  
Berechtigung  
EntitlementChannel  
EntitlementTemplateChannel  
Faxnummer  
Ziel  
GoalRollupQuery  
Vorfall  
Rechnung  
InvoiceDetail  
KbArticle  
Lead  
Brief  
Liste  
Postfach  
Metrik  
Verkaufschance  
Verkaufschance (Produkt)  
PhoneCall  
Position  
PriceLevel  
Produkt  
ProductAssociation  
ProductSubstitute  
QueueItem  
Angebot  
QuoteDetail  
RecurringAppointmentMaster  
Bericht  
SalesLiterature  
Vertriebsauftrag  
SalesOrderDetail  
Dienst  
ServiceAppointment  
SLAKPIInstance  
Social Media-Aktivitäten  
SocialProfile  
SystemUser  
Aufgabe  
Teams  
Gebiet  
UoMSchedule  
  
### <a name="see-also"></a>Siehe auch  
 [Diagramm und Analysieren von Daten](customize-visualizations-dashboards.md)   
 [Angeben von Diagrammdaten](understand-charts-underlying-data-chart-representation.md)   
 [Aktionenen im Diagramm](actions-visualizations-charts.md)   
 [Erstellen eines Diagramms](create-visualization-chart.md)   
 [Beispieldiagramme](sample-charts.md)   
 [SavedQueryVisualization-Entität](../common-data-service/reference/entities/savedqueryvisualization.md)   
 [UserQueryVisualizations-Entität](../common-data-service/reference/entities/userqueryvisualization.md) [Download: Diagramm-Steuerelemente für .NET Framework Language Pack](https://www.microsoft.com/downloads/details.aspx?FamilyId=581FF4E3-749F-4454-A5E3-DE4C463143BD&displaylang=en)   
 [Download: Grafiksteuerungs-Add-On für Visual Studio](https://www.microsoft.com/downloads/details.aspx?FamilyId=1D69CE13-E1E5-4315-825C-F14D33A303E9&displaylang=en)   
 [Download: Chart Controls für .NET Framework – Dokumentation](https://go.microsoft.com/fwlink/p/?LinkId=128301)   
 [Beispielumgebung für Microsoft Chart Controls](https://code.msdn.microsoft.com/mschart)   
 [Chart Controls-Forum](https://go.microsoft.com/fwlink/p/?LinkId=128713)

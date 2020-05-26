---
title: Erstellen einer Visualisierung (Diagramm) (modellgesteuerte Apps) | Microsoft Docs
description: In diesem Thema wird gezeigt, wie Sie eine Diagrammvisualisierung und eine Webressourcenvisualisierung erstellen.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 9dbed5ee-21a4-ab86-fc4c-08c3838e42f2
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ef9bb60a64b4b7b88d252fcfbbc99e74307eb298
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275838"
---
# <a name="create-a-visualization-chart"></a>Erstellen einer Visualisierung (Diagramm)

Wenn Sie eine Visualisierung programmgesteuert erstellen möchten, müssen Sie einen Datensatz für die [SavedQueryVisualization Entity](../common-data-service/reference/entities/savedqueryvisualization.md)- oder [UserQueryVisualization Entity](../common-data-service/reference/entities/userqueryvisualization.md)-Entität erstellen, um ein Diagramm im Besitz der Organisation bzw. im Besitz des Benutzers zu erstellen. In diesem Thema wird gezeigt, wie Sie eine Diagrammvisualisierung und eine Webressourcenvisualisierung erstellen.  
  
<a name="Before"></a>   

## <a name="before-you-create-a-visualization"></a>Bevor Sie eine Visualisierung erstellen  

 Bevor Sie eine Visualisierung erstellen, stellen Sie sicher, dass Folgendes berücksichtigt wird:  
  
- **Typ der Visualisierung**: Wenn die Visualisierungen in der gesamten Organisation verfügbar sein sollen und Sie die Zugriffsebenen nicht genauer verwalten möchten, sollten Sie eine Visualisierung im Besitz einer Organisation erstellen. Wenn Sie sich jedoch über die Zugriffsrechte und die Sicherheit Ihrer Visualisierung Gedanken machen, sollten Sie überlegen, eine Visualisierung im Besitz eines Benutzers zu erstellen, bei der Sie eine größere Kontrolle darüber haben, wer darauf zugreifen kann.  
  
    > [!NOTE]
    >  Organisationseigene Visualisierungen können nur von den Benutzern erstellt werden, die die Sicherheitsrolle "Systemadministrator" oder "Systemanpasser" haben.  
  
- **Zugeordnete Entität**: Visualisierungen sind an Entitäten angefügt. Weitere Informationen: [Für Visualisierungen unterstützte Entitäten](view-data-with-visualizations-charts.md#SupportedVisualizationEntities). Sie können ein Diagramm zu einer unterstützten Entität mithilfe des Attributs [SavedQueryVisualization.PrimaryEntityTypeCode](../common-data-service/reference/entities/savedqueryvisualization.md#BKMK_PrimaryEntityTypeCode) oder [UserQueryVisualization.PrimaryEntityTypeCode](../common-data-service/reference/entities/userqueryvisualization.md#BKMK_PrimaryEntityTypeCode) anfügen.  
  
<a name="CreateChart"></a>   

## <a name="create-a-chart-visualization"></a>Erstellen einer Diagrammvisualisierung  

 Bei Diagrammen müssen Sie die zugrundeliegenden Daten für die Diagramme und die Darstellung der Diagramme in Form von XML-Zeichenfolgen für die *Datenbeschreibung* und *Präsentationsbeschreibung* angeben. Weitere Infromationen: [Angeben der Diagrammdaten](understand-charts-underlying-data-chart-representation.md) und [Beispieldiagramme](sample-charts.md).  
  
 Ein vollständiges Beispiel dazu, wie ein organisationseigenes Diagramm erstellt wird, siehe [Beispiel: Erstellen, Aktualisieren und Löschen (CRUD) eines Diagramms](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-chart).  <!-- TODO need to replace the link with powerapps -->
  
### <a name="create-a-multi-series-chart"></a>Erstellen eines Mehrfachdiagramms  

 Mehrfachdiagramme ordnen mehrere Werte der (vertikalen) Reihenachse einem einzelnen Wert der (horizontalen) Kategorieachse zu. Der einzige Unterschied zu einem einfachen Seriendiagramm ist, dass in diesen Diagrammen mehrere `<measurecollection>`- und entsprechende `<series>`-Elemente vorhanden sind, die in den XML-Zeichenfolgen angegeben werden. Jedes `<measurecollection>`-Element enthält ein untergeordnetes Element mit der Bezeichnung `<measure>`, das einen Wert auf der (vertikalen) Reihenachse für denselben Wert der (horizontalen) Kategorieachse definiert. Weitere Informationen: [Diagramme verstehen: Zugrunde liegende Daten und Diagrammdarstellung](understand-charts-underlying-data-chart-representation.md).  
  
 Ein Beispiel für Mehrfachdiagramm und die entsprechenden Datenbeschreibungs- und Präsentationsbeschreibungs-XML-Zeichenfolgen finden Sie unter [Mehrfachseriendiagramm](sample-charts.md#multi-series-chart).
  
<a name="CreateWRVisualization"></a>   

## <a name="create-a-web-resource-visualization"></a>Erstellen einer Webressourcenvisualisierung  

 Für Visualisierungen, die Webressourcen enthalten, müssen Sie keine Datenbeschreibungs- und Präsentationsbeschreibungs-XML-Zeichenfolgen angeben. Im folgenden Beispiel wird gezeigt, wie Sie mithilfe des SDK eine Visualisierung im Besitz der Organisation erstellen, die eine Webressource enthält.  
  
```csharp  
SavedQueryVisualization newWebResourceVisualization = new SavedQueryVisualization()  
{  
   Name = "Sample Dashboard Visualization",  
   Description = "Sample organization-owned visualization",  
                           PrimaryEntityTypeCode = Account.EntityLogicalName,  
   WebResourceId = new EntityReference(WebResource.EntityLogicalName, _webResourceId))  
  
};  
_orgOwnedVisualizationId = _serviceProxy.Create(newWebResourceVisualization);  
  
```  
  
 Wenn Sie eine Webressourcen-Visualisierung unter Verwendung der Common Data Service erstellen möchten, müssen Sie eine XML-Datei im folgenden Format erstellen und dann **Diagramm importieren** im Menüband verwenden, um die Visualisierung zu importieren.  
  
```xml  
<visualization>  
  <name>Visualization_Name</name>  
  <description>Description</description>  
  <webresourcename>Name_Of_An_Existing_Web_Resource</webresourcename>  
  <primaryentitytypecode>Entity_Logical_Name</primaryentitytypecode>  
  <isdefault>Value: true or false</isdefault>  
</visualization>  
```  
  
 Wenn Sie z. B. eine *Beispielvisualisierung* erstellen möchten, die eine vorhandene Webressource mit der Bezeichnung *new_TestWebResource* anzeigt, und die Visualisierung an die *Firma*-Entität angefügt werden sollte, sollte die XML wie folgt aussehen.  
  
```xml  
<visualization>  
  <name>Sample Visualization</name>  
  <description>Sample Web Resource Visualization.</description>  
  <webresourcename>new_TestWebResource</webresourcename>  
  <primaryentitytypecode>account</primaryentitytypecode>  
  <isdefault>false</isdefault>  
</visualization>  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Diagramme](view-data-with-visualizations-charts.md)   
 [Angeben von Diagrammdaten](understand-charts-underlying-data-chart-representation.md)   
 [Aktionenen im Diagramm](actions-visualizations-charts.md)   
 [Beispieldiagramme](sample-charts.md)   
 [Datenvisualisierung und Analysen](customize-visualizations-dashboards.md)   
 [Beispiel: Erstellen, Abrufen, Aktualisieren und Löschen (CRUD) eines Diagramms](/dynamics365/customer-engagement/developer/customize-dev/sample-create-retrieve-update-delete-chart)  <!-- TODO need to replace the link with powerapps -->
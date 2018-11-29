---
title: 'Diagramme verstehen: Zugrunde liegende Daten und Diagrammdarstellung (modellgestützte Apps) | Microsoft Docs'
description: 'Diagramme zeigen Daten visuell durch Zuordnen von Textwerten auf Achsen: horizontal (X) und vertikal (Y). Die x-Achse wird als Kategorieachse bezeichnet und die y-Achse wird als Reihenachse bezeichnet.'
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
---
# <a name="understand-charts-underlying-data-and-chart-representation"></a>Diagramme verstehen: Zugrunde liegende Daten und Diagrammdarstellung

<!-- https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/customize-dev/understand-charts-underlying-data-chart-representation -->

Diagramme zeigen Daten visuell durch Zuordnen von Textwerten auf Achsen: horizontal (X) und vertikal (Y). Die x-Achse wird als *Kategorieachse* bezeichnet und die y-Achse wird als *Reihenachse* bezeichnet. Die Kategorieachse kann numerische und nicht-numerischen Werte anzeigen, während die Reihenachse nur numerische Werte anzeigt.  
  
 Diagramme in modellgestützten Apps können weiter in Folgende klassifiziert werden:  
  
- **Einzel-Seriendiagramme**: Diagramme, die Daten mit einem Serienwert (Y) anzeigen, der einem Kategorienwert (X) zugeordnet ist.  
  
- **Mehrseriendiagramme**: Diagramme, die Daten mit mehreren Serienwerten anzeigen, die einem einzelnen Kategorienwert zugeordnet sind. Multi-Seriendiagramme enthalten gestaplete Säulendiagramme, die den Beitrag der einzelnen Serie zu einer Summe Kategorien übergreifend anzeigen, und 100 % gestapelte Säulendiagramme, die den Prozentwert vergleichen, den jede einzelne Serie zu der Summe Kategorien übergreifend beiträgt. Sie können verschiedene kompatible Diagrammtypen zu Multi-Seriendiagrammen kombinieren, z. B. Zeile und Spalte, Balken und Zeile usw.  
  
> [!NOTE]
>  Multi-Kategoriendiagramme können erstellt werden über die Webanwendung oder durch Modifizieren der XML-Zeichenfolgen, die hier beschrieben werden.  
  
 Beim Erstellen eines Diagramms in modellgestützten Apps mithilfe des SDK müssen Sie die folgenden zwei wichtigen Punkte berücksichtigen:  
  
- **Zugrunde liegenden Daten für das Diagramm**: Angegeben mithilfe der XML-Zeichenfolge *Datenbeschreibung*.  
  
- **Datendarstellung (Erscheinung)**: Angegeben mithilfe der XML-Zeichenfolge *Präsentationsbeschreibung*.  
  
> [!NOTE]
> Mit Microsoft Chart Controls können Sie verschiedene Arten von Diagrammen, z. B. Spalten, Balken, Bereiche, Zeilen, Säulen, Linien, Torten, Blasen und Radare erstellen. Mit dem Diagrammdesigner in modellgestützten Apps können Sie nur bestimmte Typen von Diagrammen erstellen. Mithilfe des SDK können Sie jedoch die meisten Diagrammtypen erstellen, die von Microsoft Chart Controls unterstützt werden.  
  
## <a name="use-the-data-description-xml-string-to-specify-chart-data"></a>Verwenden Sie die Datenbeschreibungs-XML-Zeichenfolge, um Diagrammdaten anzugeben.  
 Die Datenbeschreibungs-XML-Zeichenfolge definiert die Daten, die im Diagramm angezeigt werden. Die Inhalte der XML-Zeichenfolge werden im Vergleich zum Visualisierungsdaten-Beschreibungsschema überprüft. Weitere Informationen über das Schema finden Sie unter [Visualisierungsdaten-Beschreibungsschema](visualization-data-description-schema.md).  
  
 Sie können die Datenbeschreibungs-XML-Zeichenfolge angeben, wenn Sie ein Diagramm mit dem `SavedQueryVisualization.DataDescription`- oder `UserQueryVisualization.DataDescription`-Attribut für das im Besitz der Organisation bzw. im Besitz des Benutzers befindliche Diagramm erstellen.  
  
 Die Datenbeschreibungs-XML-Zeichenfolge enthält die folgenden zwei Elemente: `<FetchCollection>` und `<CategoryCollection>`.  
  
### <a name="the-fetchcollection-element"></a>Das Element \<FetchCollection> 
 
 Das Element `<FetchCollection>` verwendet FetchXML, um Daten für das Diagramm abzurufen. Die FetchXML-Abfrage enthält Informationen zu den Entitätsattributen, Aggregatfunktionen und der Gruppe nach Klauseln, damit die Daten in einem Diagramm angezeigt werden können. Alle FetchXML-Aggregatfunktionen werden für Diagramme unterstützt. Weitere Informationen über FetchXML-Aggregatfunktionen finden Sie unter [FetchXML-Aggregation verwenden](../common-data-service/use-fetchxml-aggregation.md).  
  
 Durch die FetchXML-Abfrage wird es Ihnen ermöglicht, die Daten zu filtern. Außerdem werden Filter auf Ansichten von Diagrammen angewendet. Wenn eine in Filterbedingung bereits in der FetchXML-Abfrage im `<FetchCollection>`-Element angegeben ist, und außerdem ein Filter durch eine Ansicht angewendet wird, zeigt das Diagramm Daten an, die zurückgegeben werden, nachdem es alle Filter angewendet hat. Weitere Informationen dazu, wie die FetchXML-Abfrage verwendet wird, um Daten zu filtern, finden Sie unter [Verwenden von FetchXML zum Erstellen einer Abfrage](../common-data-service/use-fetchxml-construct-query.md).  
  
> [!NOTE]
>  Obwohl die Datenbeschreibungs-XML-Zeichenfolge gegen das Visualisierungsdaten-Beschreibungsschema überprüft wird, gilt dies nicht für die FetchXML-Abfrage innerhalb des `<FetchCollection>`-Elements. Die FetchXML-Abfrage wird anhand des FetchXML-Schemas überprüft. Weitere Informationen finden Sie unter [FetchXML-Schema](../common-data-service/fetchxml-schema.md).  
  
 Wenn das Diagramm ein Vergleichsdiagramm ist, enthält das `<FetchCollection>`-Element zwei *Gruppieren nach*-Klauseln.  
  
### <a name="the-categorycollection-element"></a>Das Element \<CategoryCollection>  
 Das Element `<CategoryCollection>` enthält Informationen zur Kategorien- (horizontal) und Serien- (vertikal) Achse in einem Diagramm.  
  
-   Jedes `<Category>`-Unterelement hat ein untergeordnetes Element namens `<MeasureCollection>`, das dem `<Series>`-Element in der Präsentationsbeschreibungs-XML zugeordnet ist. Ein Einzelseriendiagramm hat ein einzelnes untergeordnetes `<MeasureCollection>`-Element, während ein Mehrseriendiagramm über mehrere untergeordnete `<MeasureCollection>`-Elemente verfügt, wobei jedes dem jeweiligen `<Series>`-Element in der Präsentationsbeschreibungs-XML zugeordnet ist.  
  
-   Jedes untergeordnete `<MeasureCollection>`-Element ist hat ein Element namens `<Measure>`, das dem Achsenwert der Serie (vertikal) entspricht, entsprechend jedem Wert auf der der Kategorienachse (horizontal).  
  
### <a name="example"></a>Beispiel  
 Das folgende ist eine Beispieldatenbeschreibungs-XML-Zeichenfolge:  
  
```xml  
<datadefinition>  
  <fetchcollection>  
    <fetch mapping="logical" count="10">  
      <entity name="opportunity">  
        <attribute name="estimatedvalue" />  
        <order attribute="estimatedvalue" descending="true" />  
      </entity>  
    </fetch>  
  </fetchcollection>  
  <categorycollection>  
    <category>  
      <measurecollection>  
        <measure alias="estimatedvalue" />  
      </measurecollection>  
    </category>  
  </categorycollection></datadefinition>  
```  
  
 Weitere Beispieldatenbeschreibung-XML-Zeichenfolgen finden Sie unter [Beispieldiagramme](sample-charts.md).  
  
## <a name="use-the-presentation-description-xml-string-to-specify-data-representation"></a>Verwenden Sie die Präsentationsbeschreibungs-XML-Zeichenfolge, um die Datenrepräsentation festzulegen.  
 Die Präsentationsbeschreibungs-XML-Zeichenfolge enthält Informationen zur Darstellung des Diagramms, wie Diagrammfarbe, Diagrammtitel und Diagrammtyp (Balken, Spalte, Zeile usw.). Es gibt keine Schemadefinition für diese XML-Zeichenfolge. XML ist jedoch eine Serialisierung der [Diagramm](https://msdn.microsoft.com/library/system.web.ui.datavisualization.charting.chart.aspx)-Klasse in Microsoft Chart Controls. Weitere Informationen: [Chart Controls](http://go.microsoft.com/fwlink/p/?LinkId=128301)  
  
 Sie können die Präsentationsbeschreibungs-XML-Zeichenfolge angeben, wenn Sie ein Diagramm mit dem `SavedQueryVisualization.PresentationDescription`- oder `UserQueryVisualization.PresentationDescription`-Attribut für das im Besitz der Organisation bzw. im Besitz des Benutzers befindliche Diagramm erstellen.  
  
### <a name="example"></a>Beispiel  
 Das folgende ist eine Beispiel-Präsentationsbeschreibungs-XML-Zeichenfolge:  
  
```xml  
<Chart Palette="BrightPastel">  
  <Series>  
    <Series _Template_="All" Color="153, 204, 255" BorderColor="164, 164, 164" BorderDashStyle="Solid" BorderWidth="1" ShadowColor="128, 128, 128, 128" ShadowOffset="1" IsValueShownAsLabel="true" Font="{0}, 6.75pt" BackGradientStyle="TopBottom" BackSecondaryColor="0, 102, 153" LabelForeColor="100, 100, 100" ChartType="Column">  
      <SmartLabelStyle Enabled="True" />  
      <Points />  
    </Series>  
  </Series>  
  <ChartAreas>  
    <ChartArea _Template_="All" BackColor="White" BorderColor="26, 59, 105" BorderWidth="0" BorderDashStyle="Solid">      <AxisY LineColor="204, 204, 204" TitleFont="{0}, 8pt, GdiCharSet=0" TitleForeColor="100, 100, 100" LabelAutoFitMaxFontSize="7" LabelAutoFitMinFontSize="7">  
        <MajorTickMark LineColor="Gray" />  
        <MajorGrid Enabled="false" />  
        <LabelStyle Font="{0}, 6.75pt, GdiCharSet=0" ForeColor="100, 100, 100" />  
      </AxisY>  
      <AxisX LineColor="204, 204, 204" TitleFont="{0}, 8pt, GdiCharSet=0" TitleForeColor="100, 100, 100" LabelAutoFitMaxFontSize="7" LabelAutoFitMinFontSize="7">        <MajorTickMark LineColor="Gray" />        <MajorGrid Enabled="false" />  
        <LabelStyle Font="{0}, 6.75pt, GdiCharSet=0" ForeColor="100, 100, 100" />  
      </AxisX>  
    </ChartArea>  
  </ChartAreas>  
  <Titles>  
    <Title _Template_="All" Font="{0}, 9pt, style=Bold, GdiCharSet=0" ForeColor="100, 100, 100"></Title>  
  </Titles>  
  <BorderSkin PageColor="Control" BackColor="CornflowerBlue" BackSecondaryColor="CornflowerBlue" />  
</Chart>  
```  
  
 Weitere Beispiel-Präsentationsbeschreibungs-XML-Zeichenfolgen finden Sie unter [Beispieldiagramme](sample-charts.md).  
  
### <a name="see-also"></a>Siehe auch  
 [Visualisierungen (Diagramme)](view-data-with-visualizations-charts.md)   
 [Aktionen für Visualisierungen (Diagramme)](actions-visualizations-charts.md)   
 [Erstellen eines Diagramms](create-visualization-chart.md)   
 [Verwenden von FetchXML zum Erstellen einerAbfrage](../common-data-service/use-fetchxml-construct-query.md)   
 [FetchXML-Schema](../common-data-service/fetchxml-schema.md) [Visualisierungsdaten-Beschreibungsschema](visualization-data-description-schema.md)   
 [Beispieldiagramme](sample-charts.md)   
 [Diagrammklasse (Microsoft Chart Controls)](https://msdn.microsoft.com/library/system.web.ui.datavisualization.charting.chart.aspx)

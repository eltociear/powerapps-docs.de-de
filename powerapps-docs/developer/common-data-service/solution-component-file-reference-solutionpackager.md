---
title: Dateireferenz der Lösungskomponente (Common Data Service für Apps) | Microsoft Docs
description: 'In diesem Thema werden die Ordnerstruktur- und Datei-Benennungsschema beschrieben, die durch SolutionPackager-Tool verwendet werden. Dieses Tool wird verwendet, um Dynamics 365-Lösungsdateien in XML-Dateien zu zerlegen (entpacken), die durch ein Quellcodeverwaltungssystem verwaltet werden können.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: shmcarth
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="solution-component-file-reference-solutionpackager"></a>Dateireferenz von Lösungskomponenten (SolutionPackager)

In diesem Thema werden die Ordnerstruktur- und Datei-Benennungsschema beschrieben, die durch SolutionPackager-Tool verwendet werden. Dieses Tool wird verwendet, um Common Data Service for Apps -Lösungsdateien in XML-Dateien zu zerlegen (entpacken), die durch ein Quellcodeverwaltungssystem verwaltet werden können. Das Tool kann auch die einzelnen XML-Dateien in eine Lösungsdatei kompilieren (verpacken), die in CDS for Apps importiert werden können. Weitere Informationen zum SolutionPackager-Tool, siehe [SolutionPackager-Tool](compress-extract-solution-file-solutionpackager.md).  
  
 In den folgenden Abschnitten werden die Dateien beschrieben, die für jeden Lösungskomponententyp erstellt werden und welche von diesen Dateien zur Inklusion im Quellsteuerelement weniger geeignet sind. Die Ordner, in den Abschnitten angegeben sind, sind alle relativ zu dem Ordner, der im Parameter `/folder` des **SolutionPackager**-Befehls angegeben sind.  
  
<a name="entity_bm"></a>   
## <a name="entity"></a>Entity  
 Unterscheidet sich in verwalteten Lösungen: Ja  
  
### <a name="notes"></a>Notizen  
  
1.  Jede Entität besitzt einen speziellen Ordner.  
  
2.  Für jedes Formular, Ansicht und Visualisierung wird eine eigene Datei im entsprechenden Unterordner erstellt.  
  
3.  Die Formulardateinamen variieren nach verwalteten oder nicht verwalteten Lösungs-Typen.  
  
4.  Direkte Bearbeitung von RibbonDiff.xml, um bestimmte Menübänder der Entität anzupassen. wird unterstützt.  
  
5.  Manuelle Aufbereitung von XML-Dateien die unter den Ordner FormXml und SavedQueries wird jedoch unterstützt, aber optional.  
  
### <a name="files"></a>Dateien  
 \Entities\\<Entitäts-Schemaname\>\  
  
 Entity.xml  
RibbonDiff.xml  
  
 FormXml\Main\  
  
 {guid 1}.xml  
{guid 1_managed}.xml  
{guid n}.xml  
{guid n_managed}.xml  
  
 FormXml\Mobile\  
  
 {guid 1}.xml  
{guid 1_managed}.xml  
{guid n}.xml  
{guid n_managed}.xml  
  
 SavedQueries\  
  
 {guid 1}.xml  
{guid n}.xml  
  
 Visualizations\  
  
 {guid 1}.xml  
{guid n}.xml  
  
<a name="optionset_bm"></a>   
## <a name="option-set"></a>Optionssatz  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Jeder Optionssatz ist in einer eigenen Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \OptionSets\  
  
 \<schema name 1>.xml  
\<schema name n>.xml  
  
<a name="relationship_bm"></a>   
## <a name="entity-relationship"></a>Entitätsbeziehung  
 Unterscheidet sich in verwalteten Lösungen: Ja  
  
### <a name="notes"></a>Notizen  
  
1.  Jede Entität besitzt eine eigene Datei, die alle Beziehungen enthält für:  
  
    1.  N:N ist die erste aufgeführte Entität  
  
    2.  1:N ist die referenzierte Entität  
  
### <a name="files"></a>Dateien  
 \Other\Relationships\  
  
 \<Entitätsschemaname 1>.xml  
\<Entitätsschemaname n>.xml  
  
<a name="ribbon_bm"></a>   
## <a name="ribbon-customization"></a>Menübandanpassung  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  Alle entitätsspezifischen Menüband-XML können im entsprechenden Ordner für diese Entität gefunden werden. Alle weiteren Menüband-XML sind in dieser Datei.  
  
2.  Direkte Bearbeitung von RibbonCustomizations.xml zum Anpassen der globalen Multifunktionsleiste wird unterstützt.  
  
### <a name="files"></a>Dateien  
 \Other\RibbonCustomizations.xml  
  
<a name="sitemap_bm"></a>   
## <a name="site-map"></a>Siteübersicht  
 Unterscheidet sich in verwalteten Lösungen: Ja  
  
### <a name="notes"></a>Notizen  
 Siteübersicht XML-Format ist verschieden für nicht verwaltete und verwaltete Lösungen. Erwarten Sie, dass die Datei so gezeigt wird,l wie hier gezeigt. Wenn sie beide für Pakettypen extrahieren, sind beide Dateien vorhanden.  
  
### <a name="files"></a>Dateien  
 \Other\  
  
 SiteMap.xml  
SiteMap_managed.xml  
  
<a name="resource_bm"></a>   
## <a name="web-resources"></a>Webressourcen  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  Die roh- Webressource wird als distinkte Datei gespeichert. Das Schrägstrich-Zeichen (/) wird verwendet, um Ordner zu erstellen.  
  
2.  Die Webressourcemetadaten werden mit einem ähnlichen Dateinamenende in .data.xml gespeichert.  
  
3.  Es wird empfohlen, dass der Name einer Webressource die natürliche Dateinamenerweiterung enthält.  
  
4.  Das Hinzufügen der Rohdatendateien zum Quellsteuerelement kann zu Verdopplung führen.  
  
### <a name="files"></a>Dateien  
 \WebResources\  
  
 \<name 1>  
\<name 1>.data.xml  
\<name n>  
\<name n>.data.xml  
  
<a name="role_bm"></a>   
## <a name="role"></a>Rolle  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Jede Rolle ist in einer eigenen Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \Roles\  
  
 \<schema name>.xml  
  
<a name="connectionrole_bm"></a>   
## <a name="connection-role"></a>Verbindungsrolle  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Alle Verbindungsrollen werden gemeinsam in einer Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \Other\ConnectionRoles.xml  
  
<a name="dashboard_bm"></a>   
## <a name="dashboard"></a>Informationsleiste  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Jedes Dashboard ist in einer eigenen Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \Dashboards\  
  
 {guid 1}.xml  
{guid n}.xml  
  
<a name="workflow_bm"></a>   
## <a name="workflow"></a>Workflow  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  XAML für jeden Workflow wird in einer eindeutigen Datei gespeichert.  
  
2.  Metadaten für jeden Workflows befinden sich in einer auf ähnliche Weise benannten Datei in .data.xml.  
  
### <a name="files"></a>Dateien  
 \Workflows\  
  
 \<XamlFileName 1>.xaml  
\<XamlFileName 1>.xaml.data.xml  
\<XamlFileName n>.xaml  
\<XamlFileName n>.xaml.data.xml  
  
<a name="emailtemplate_bm"></a>   
## <a name="email-template"></a>E-Mail-Vorlage  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  Alle E-Mail-Vorlagenmetadaten werden in eine einzelne Datei gespeichert.  
  
2.  Jede E-Mail-Vorlage verwendet eindeutige vier Dateien pro Sprache.  
  
### <a name="files"></a>Dateien  
 \Templates\  
  
 EmailTemplates.xml  
  
 EmailDocuments\  
  
 \<LCID 1>\\{guid 1}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
 \<LCID 1>\\{guid n}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
 \<LCID n>\\{guid 1}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
 \<LCID n>\\{guid n}\  
  
 Body.xsl  
Presentation.xml  
Subject.xsl  
Subjectpresentation.xml  
  
<a name="contracttemplate_bm"></a>   
## <a name="contract-template"></a>Vertragsvorlage  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Alle Vertragsvorlagenmetadaten werden in eine einzelne Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \Templates\ContractTemplates.xml  
  
<a name="kbarticle_bm"></a>   
## <a name="kb-article-template"></a>Vorlage für Wissensdatenbankartikel  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  Alle Vertragsvorlagenmetadaten werden in eine einzelne Datei gespeichert.  
  
2.  JedeVertragsvorlage verwendet eindeutige zwei Dateien pro Sprache.  
  
### <a name="files"></a>Dateien  
 \Templates\  
  
 KBArticleTemplates.xml  
  
 KBArticleTemplates\  
  
 \<LCID 1>\\{guid 1}\  
  
 formatxml.xsl  
Structurexml.xml  
  
 \<LCID 1>\\{guid n}\  
  
 formatxml.xsl  
Structurexml.xml  
  
 \<LCID n>\\{guid 1}\  
  
 formatxml.xsl  
Structurexml.xml  
  
 \<LCID n>\\{guid n}\  
  
 formatxml.xsl  
Structurexml.xml  
  
<a name="mailmerge_bm"></a>   
## <a name="mail-merge-template"></a>Seriendruckvorlage  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  Alle Seriendruckvorlagenmetadaten werden in eine einzelne Datei gespeichert.  
  
2.  Jede Seriendruckvorlage verwendet eindeutige zwei Dateien pro Sprache.  
  
3.  Dokumente, die über mehrere Vorlagen verwendet werden, sind in einer einzelnen Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \Templates\  
  
 MailMergeTemplates.xml  
  
 MailMergeDocuments\  
  
 \<LCID 1>\\{guid 1}\\<document name 1>.xml  
\<LCID 1>\\{guid n}\\<document name n\>.xml  
\<LCID n>\\{guid 1}\\<document name 1>.xml  
\<LCID n>\\{guid n}\\<document name n\>.xml  
  
<a name="pluginassembly_bm"></a>   
## <a name="pluginassembly"></a>PluginAssembly  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  Jede Plug-In-Assembly besitzt eine eigene Datei für die rohen Assemblybytes.  
  
2.  Plug-In-Assemblymetadaten werden in einer ähnlich benannten Dateiendung in .data.xml gespeichert.  
  
3.  Das Einschließen der rohen Assembly im Quellsteuerelement wird nicht empfohlen.  
  
### <a name="files"></a>Dateien  
 \PluginAssemblies\  
  
 \<Assembly Name 1>-{guid 1}\  
  
 \<Assembly Name 1>.dll  
\<Assemblyname 1>.dll.data.xml  
  
 \<Assembly Name n>-{guid n}\  
  
 \<Assembly Name n>.dll  
\<Assembly Name n>.dll.data.xml  
  
<a name="step_bm"></a>   
## <a name="sdkmessageprocessingstep"></a>SdkMessageProcessingStep  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Jeder SDK-Meldungsverarbeitungsschritt wird in einer eindeutigen Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \SdkMessageProcessingSteps\  
  
 {guid 1}.xml  
{guid n}.xml  
  
<a name="serviceendpoint_bm"></a>   
## <a name="serviceendpoint"></a>ServiceEndpoint  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Alle Serviceendpunktmetadaten werden zusammen in einer Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \PluginAssemblies\ServiceEndpoints.xml  
  
<a name="reports_bm"></a>   
## <a name="reports"></a>Berichte  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
  
1.  Berichte werden in einem eindeutigen Unterordner pro Sprache gespeichert.  
  
2.  Jeder Bericht hat eine eindeutige Datei auf dieser Ordner.  
  
3.  Metadaten für jeden Bericht werden in einer ähnlich benannten Dateiendung in .data.xml gespeichert.  
  
### <a name="files"></a>Dateien  
 \Reports\  
  
 ReportSignatureIdMappings.xml  
  
 ReportLinks.xml  
  
 \<LCID 1>\\{guid 1}\  
  
 \<Report Name 1>.rdl  
\<Report Name 1>.rdl.data.xml  
  
 \<LCID 1>\\{guid n}\  
  
 \<Report Name n>.rdl  
\<Report Name n>.rdl.data.xml  
  
 \<LCID n>\\{guid 1}\  
  
 \<Report Name 1>.rdl  
\<Report Name 1>.rdl.data.xml  
  
 \<LCID n>\\{guid n}\  
  
 \<Report Name n>.rdl  
\<Report Name n>.rdl.data.xml  
  
<a name="entitymap_bm"></a>   
## <a name="entitymap"></a>EntityMap  
 Unterscheidet sich in verwalteten Lösungen: Nein  
  
### <a name="notes"></a>Notizen  
 Alle Entitätszuordnungen werden in eine einzelne Datei gespeichert.  
  
### <a name="files"></a>Dateien  
 \Other\EntityMaps.xml  
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden des SolutionPackager-Tools, um eine Lösungsdatei zu komprimieren und zu extrahieren](compress-extract-solution-file-solutionpackager.md)   

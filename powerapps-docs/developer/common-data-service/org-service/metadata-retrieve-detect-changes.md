---
title: Abrufen und Erkennen von Änderungen bei Metadaten (Common Data Service) | Microsoft-Dokumentation
description: Die Klassen im Abfrage-Namespace und die RetrieveMetadataChangesRequest und RetrieveMetadataChangesResponse-Klassen erlauben Ihnen, effiziente Metadatenabfragen aufzubauen und Änderungen an den Metadaten, die im Laufe der Zeit auftreten, zu erfassen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8723f629b38df58bbc44ec294f84e7d006555e62
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156022"
---
# <a name="retrieve-and-detect-changes-to-metadata"></a>Abrufen und Erkennen von Änderungen bei Metadaten

Die Klassen im <xref:Microsoft.Xrm.Sdk.Metadata.Query>-Namespace und die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>- und <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest>-Klassen erlauben Ihnen, effiziente Metadatenabfragen aufzubauen und Änderungen an den Metadaten, die im Laufe der Zeit auftreten, zu erfassen.  
  
 Alle Codebeispiele, auf die in diesem Dokument aus verwiesen wird, werden gefunden in [Beispiel: Abfragen von Metadaten und Ermitteln von Änderungen](/dynamics365/customer-engagement/developer/org-service/sample-query-metadata-detect-changes).  
  
 Der technische Artikel [Abfragemetadaten mit JavaScript](https://msdn.microsoft.com/library/jj919080.aspx) stellt eine JavaScript-Bibliothek für die Verwendung der Objekte und Nachrichten in clientseitigem Code bereit.  
  
<a name="BKMK_MetadataStrategies"></a> 
  
## <a name="strategies-for-using-metadata"></a>Strategien für die Verwendung von Metadaten  

 Mithilfe von Metadaten können Sie Anwendungen erstellen, die sich anpassen, während das Common Data Service-Datenmodell sich ändert. Metadaten sind für die folgenden Typen von Anwendungen wichtig:  
  
-   UI für-Client-Anwendungen  
  
-   Integrationstools, die Dynamics 365-Daten externen Systemen zuordnen müssen  
  
-   Entwicklungstools  
  
 Bei Verwenden der Klassen im <xref:Microsoft.Xrm.Sdk.Metadata.Query>-Namespace können Sie Entwürfe implementieren, die irgendwo zwischen einer Abfrage mit geringem Umfang und einem permanenten Metadatencache liegen.  
  
### <a name="lightweight-query"></a>Einfache Abfrage
  
 Ein Beispiel für eine einfache Abfrage ist es, wenn Sie eine benutzerdefinierte Webressourcen-Benutzeroberfläche haben, die ein Auswahlsteuerelement bereitstellt, um die aktuellen Optionen in einem Dynamics 365-Optionssatzattribut (Auswahllistenattribut) anzuzeigen. Sie möchten diese Optionen nicht hartcodiert festlegen, da Sie diesen Code aktualisieren müssten, wenn die verfügbaren Optionen jemals geändert werden. Stattdessen können Sie eine Abfrage erstellen, um nur diese Optionswerte und Beschriftungen aus den Metadaten abzurufen.  
  
 Sie müssen diese Daten nicht zwischenspeichern, da Sie die <xref:Microsoft.Xrm.Sdk.Metadata.Query>-Klassen verwenden können, um diese Daten direkt aus dem Dynamics 365-Anwendungscache abzurufen.  
  
### <a name="persistent-metadata-cache"></a>Dauerhafter Metadatencache
  
 Wenn Sie eine Anwendung haben, die arbeiten können muss, während sie vom Dynamics 365 Server getrennt ist, oder die durch eine beschränkte Netzwerk-Bandbreite zwischen dem Client und dem Server leicht beeinträchtigt wird, wie etwa eine mobile Anwendung, müssen Sie einen dauerhaften Metadatencache implementieren.  
  
 Mit einem dauerhaften Metadatencache muss Ihre Anwendung alle notwendigen Metadaten abfragen, wenn sie zum ersten Mal eine Verbindung herstellen. Anschließend speichern Sie diese Daten in der Anwendung. Das nächste Mal, wenn die Anwendung eine Verbindung mit dem Server herstellt, können Sie einfach Unterschied abfragen, was sehr viel weniger zu übertragende Daten bedeuten sollte, und dann die Änderungen mit den Metadatencache zusammenführen, wenn die Anwendung geladen wird.  
  
 Wie häufig Sie nach Metadatenänderungen abfragen sollten, hängt von der erwarteten Volatillität der Metadaten für die Anwendung ab, und wie lange die Anwendung weiterhin ausgeführt wird. Es ist kein Ereignis verfügbar, das Sie verwenden können, um zu ermitteln, wann Metadatenänderungen eintreten. Es gibt eine Begrenzung für die Anzahl der Tage, die Metadatenänderungen gespeichert werden, und eine Anforderungen von Änderungen, die jenseits dieser Beschränkung auftritt, erfordert eine vollständige Reinitialisierung des Metadatencache. Weitere Informationen finden Sie unter [Ablauf gelöschter Metadaten](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata#BKMK_DeletedMetadataExpiration).  
  
 Sind keine Änderungen vorhanden, sollte die Abfrage schnell reagieren, und es sind keine Daten vorhanden, die zurückzugeben sind. Falls jedoch Änderungen vorhanden sind, insbesondere wenn es gelöschte Metadatenelemente gibt, die aus dem Cache entfernt werden müssen, können Sie damit rechnen, dass die Anforderung einige Zeit in Anspruch nehmen kann. Weitere Informationen: [Leistung beim Abrufen gelöschter Metadaten](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata#BKMK_PerformanceRetrievingDeletedMetadata)  
  
<a name="BKMK_RetrieveJusttheMetadataYouNeed"></a>
   
## <a name="retrieve-only-the-metadata-you-need"></a>Rufen Sie nur die Metadaten ab, die Sie benötigen.  

 Metadaten werden häufig abgerufen oder synchronisiert, wenn eine Anwendung gestartet wird und sich auf die Zeit auswirken kann, die die Anwendung zum Laden benötigt. Dies gilt besonders für mobile Anwendungen, die zum ersten Mal Metadaten abrufen. Nur die Metadaten abzurufen, die Sie benötigen, ist sehr wichtig, um eine Anwendung zu erstellen, die gute Leistung bringt.  
  
 Die <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>-Klasse bietet eine Struktur, die mit der <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Klasse konsistent ist, die Sie verwenden, um komplexe Abfragen zu erstellen, um Entitätsdaten abzurufen. Anders als die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest>, <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest>,  <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>, oder <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>-Klassen enthält <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest> einen `Query`-Parameter, der eine <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>-Instanz akzeptiert, die Sie verwenden können, um spezifische Kriterien für die zurückzugebenden Daten festzulegen, zusätzlich zu den Eigenschaften, die Sie wünschen. Sie können <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest> verwenden, um den ganzen Satz von Metadaten zurückzugeben, die Sie erhalten, wenn Sie <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest> verwenden, oder nur eine Beschriftung für ein bestimmtes Attribut.  
  
### <a name="specify-your-filter-criteria"></a>Angeben der Filterkriterien  

 Im <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> Die -Eigenschaft akzeptiert einen <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression>, der eine Sammlung von <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionExpression>-Objekte enthält, die das Festlegen von Bedingungen zum Filtern von Entitätseigenschaften auf der Grundlage ihres Wertes zulassen. Diese Anforderungen verwenden einen <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>, der folgende Operatoren zulässt:  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.Equals  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.NotEquals  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.In  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.NotIn  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.GreaterThan  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataConditionOperator>.LessThan  
  
 Der <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> enthält außerdem einen <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator>, um darzustellen, ob  `And` oder `Or`-Logik angewendet wird, wenn Sie die Bedingungen auswerten.  
  
 Nicht alle Eigenschaften können als Filterkriterien verwendet werden. Nur Eigenschaften, die einfache Datentypen, Aufzählen, <xref:Microsoft.Xrm.Sdk.BooleanManagedProperty> oder <xref:Microsoft.Xrm.Sdk.Metadata.AttributeRequiredLevelManagedProperty>-Typen darstellen, können in einer <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> verwendet werden. Wenn eine <xref:Microsoft.Xrm.Sdk.BooleanManagedProperty> oder <xref:Microsoft.Xrm.Sdk.Metadata.AttributeRequiredLevelManagedProperty> angegeben ist, kann nur die Eigenschaft `Value` ausgewertet werden.  
  
 In der folgenden Tabelle werden <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>-Eigenschaften aufgeführt, die in nicht in einem <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> verwendet werden können:  
  
|||||  
|-|-|-|-|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Attributes>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Description>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DisplayCollectionName>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DisplayName>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToManyRelationships>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToOneRelationships>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OneToManyRelationships>|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Privileges>|  
  
 Im folgenden Beispiel wird ein <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> angezeigt, der einen Satz von nicht sich überschneiden Entitäten im Besitz des Benutzers zurückgibt, die nicht in einer Liste von Entitäten enthalten sind, die ausgeschlossen sind:  
  
 ```csharp
   // An array SchemaName values for non-intersect, user-owned entities that should not be returned.
     String[] excludedEntities = {
"WorkflowLog",
"Template",
"CustomerOpportunityRole",
"Import",
"UserQueryVisualization",
"UserEntityInstanceData",
"ImportLog",
"RecurrenceRule",
"QuoteClose",
"UserForm",
"SharePointDocumentLocation",
"Queue",
"DuplicateRule",
"OpportunityClose",
"Workflow",
"RecurringAppointmentMaster",
"CustomerRelationship",
"Annotation",
"SharePointSite",
"ImportData",
"ImportFile",
"OrderClose",
"Contract",
"BulkOperation",
"CampaignResponse",
"Connection",
"Report",
"CampaignActivity",
"UserEntityUISettings",
"IncidentResolution",
"GoalRollupQuery",
"MailMergeTemplate",
"Campaign",
"PostFollow",
"ImportMap",
"Goal",
"AsyncOperation",
"ProcessSession",
"UserQuery",
"ActivityPointer",
"List",
"ServiceAppointment"};

     //A filter expression to limit entities returned to non-intersect, user-owned entities not found in the list of excluded entities.
     MetadataFilterExpression EntityFilter = new MetadataFilterExpression(LogicalOperator.And);
     EntityFilter.Conditions.Add(new MetadataConditionExpression("IsIntersect", MetadataConditionOperator.Equals, false));
     EntityFilter.Conditions.Add(new MetadataConditionExpression("OwnershipType", MetadataConditionOperator.Equals, OwnershipTypes.UserOwned));
     EntityFilter.Conditions.Add(new MetadataConditionExpression("SchemaName", MetadataConditionOperator.NotIn, excludedEntities));
     MetadataConditionExpression isVisibileInMobileTrue = new MetadataConditionExpression("IsVisibleInMobile", MetadataConditionOperator.Equals, true);
     EntityFilter.Conditions.Add(isVisibileInMobileTrue);
```
  
### <a name="specify-the-properties-you-want"></a>Erstellen der Eigenschaften, die Sie wünschen
  
 Die <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties>-Eigenschaft akzeptiert einen <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression>. Sie können auch <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression.AllProperties> ffestlegen zu `true`, wenn Sie alle Eigenschaften zurückgeben bzw. Sie können eine Sammlung von Zeichenfolgen zu <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataPropertiesExpression.PropertyNames> ggewähren. um zu definieren, welche Eigenschaften Sie in Abfrageergebnissen einschließen möchten.  
  
 Die zurückgegebenen stark typisierten Objekte enthalten alle Eigenschaften, aber nur die, die Sie benötigen, enthalten Daten. Alle anderen Eigenschaften sind Null, mit den folgenden wenigen Ausnahmen: jedes Metadatenelement enthält die <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId> ,`LogicalName` und <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged>-Werte, wenn sie für dieses Element vorhanden sind. Sie müssen sie nicht in den <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> angeben, die Sie benötigen.  
  
 Wenn Sie nicht verwalteten Code verwenden, und das `responseXML` analysieren, das von derXMLHttpRequest zurückgegeben wurde, erhalten Sie Elemente für jede Eigenschaft, aber nur die, die Sie benötigen, enthalten Daten. Das folgende XML zeigt die Kontaktentitätsmetadaten-XML, die zurückgegeben wird, wenn `IsVisibleInMobile` die einzige angeforderte Eigenschaft ist.  
  
```xml  
<a:EntityMetadata>  
 <c:MetadataId>608861bc-50a4-4c5f-a02c-21fe1943e2cf</c:MetadataId>  
 <c:HasChanged i:nil="true"/>  
 <c:ActivityTypeMask i:nil="true"/>  
 <c:Attributes i:nil="true"/>  
 <c:AutoRouteToOwnerQueue i:nil="true"/>  
 <c:CanBeInManyToMany i:nil="true"/>  
 <c:CanBePrimaryEntityInRelationship i:nil="true"/>  
 <c:CanBeRelatedEntityInRelationship i:nil="true"/>  
 <c:CanCreateAttributes i:nil="true"/>  
 <c:CanCreateCharts i:nil="true"/>  
 <c:CanCreateForms i:nil="true"/>  
 <c:CanCreateViews i:nil="true"/>  
 <c:CanModifyAdditionalSettings i:nil="true"/>  
 <c:CanTriggerWorkflow i:nil="true"/>  
 <c:Description i:nil="true"/>  
 <c:DisplayCollectionName i:nil="true"/>  
 <c:DisplayName i:nil="true"/>  
 <c:IconLargeName i:nil="true"/>  
 <c:IconMediumName i:nil="true"/>  
 <c:IconSmallName i:nil="true"/>  
 <c:IsActivity i:nil="true"/>  
 <c:IsActivityParty i:nil="true"/>  
 <c:IsAuditEnabled i:nil="true"/>  
 <c:IsAvailableOffline i:nil="true"/>  
 <c:IsChildEntity i:nil="true"/>  
 <c:IsConnectionsEnabled i:nil="true"/>  
 <c:IsCustomEntity i:nil="true"/>  
 <c:IsCustomizable i:nil="true"/>  
 <c:IsDocumentManagementEnabled i:nil="true"/>  
 <c:IsDuplicateDetectionEnabled i:nil="true"/>  
 <c:IsEnabledForCharts i:nil="true"/>  
 <c:IsImportable i:nil="true"/>  
 <c:IsIntersect i:nil="true"/>  
 <c:IsMailMergeEnabled i:nil="true"/>  
 <c:IsManaged i:nil="true"/>  
 <c:IsMappable i:nil="true"/>  
 <c:IsReadingPaneEnabled i:nil="true"/>  
 <c:IsRenameable i:nil="true"/>  
 <c:IsValidForAdvancedFind i:nil="true"/>  
 <c:IsValidForQueue i:nil="true"/>  
 <c:IsVisibleInMobile>  
  <a:CanBeChanged>false</a:CanBeChanged>  
  <a:ManagedPropertyLogicalName>canmodifymobilevisibility</a:ManagedPropertyLogicalName>  
  <a:Value>false</a:Value>  
 </c:IsVisibleInMobile>  
 <c:LogicalName>contact</c:LogicalName>  
 <c:ManyToManyRelationships i:nil="true"/>  
 <c:ManyToOneRelationships i:nil="true"/>  
 <c:ObjectTypeCode i:nil="true"/>  
 <c:OneToManyRelationships i:nil="true"/>  
 <c:OwnershipType i:nil="true"/>  
 <c:PrimaryIdAttribute i:nil="true"/>  
 <c:PrimaryNameAttribute i:nil="true"/>  
 <c:Privileges i:nil="true"/>  
 <c:RecurrenceBaseEntityLogicalName i:nil="true"/>  
 <c:ReportViewName i:nil="true"/>  
 <c:SchemaName i:nil="true"/>  
</a:EntityMetadata>  
  
```  
  
 In einer zukünftigen Version wird möglicherweise mehr Effizienz erreicht, indem Elementen mit leeren Werten für Eigenschaften , die nicht angefordert wurden, nicht zurückgegeben werden. Wenn Sie Code schreiben, um diese XML zu analysieren, sollten Sie erwarten, dass die XML-Datei, die für dieselbe Abfrage zurückgegeben wurde, zu der folgenden XML-Datei reduziert werden könnte.  
  
```xml  
<a:EntityMetadata>  
 <c:MetadataId>608861bc-50a4-4c5f-a02c-21fe1943e2cf</c:MetadataId>  
 <c:IsVisibleInMobile>  
  <a:CanBeChanged>false</a:CanBeChanged>  
  <a:ManagedPropertyLogicalName>canmodifymobilevisibility</a:ManagedPropertyLogicalName>  
  <a:Value>false</a:Value>  
 </c:IsVisibleInMobile>  
 <c:LogicalName>contact</c:LogicalName>  
</a:EntityMetadata>  
```  
  
 Metadaten werden in einer Baumstruktur zurückgegeben, wie sie die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAllEntitiesRequest> verwendet. Um auf ein ein bestimmtes Attribut oder eine Beziehung zuzugreifen, müssen Sie eine Abfrage erstellen, die die Entität zurückgibt, von der sie ein Teil ist. Wenn Sie Daten über ein bestimmtes Attribut abrufen möchten, müssen Sie die <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata><xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Attributes>Eigenschaft einschließen. Eigenschaft in der <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression><xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties>. Damit Entitätsbeziehungen zurückgegeben werden, müssen Sie mindestens eine der folgenden Eigenschaften <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata> enthalten: <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToManyRelationships>,  <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ManyToOneRelationships> oder <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OneToManyRelationships>.  
  
 Das folgende Bespiel wird die `Attributes`-Eigenschaft für die angeforderte Entitäten zurückgeben:  
  
```csharp
//A properties expression to limit the properties to be included with entities
MetadataPropertiesExpression EntityProperties = new MetadataPropertiesExpression()
{
 AllProperties = false
};
EntityProperties.PropertyNames.AddRange(new string[] { "Attributes" });
```

### <a name="retrieve-attribute-metadata"></a>Attribut-Metadaten abrufen 
 
 Im <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.AttributeQuery> -Eigenschaft übernimmt eine <xref:Microsoft.Xrm.Sdk.Metadata.Query.AttributeQueryExpression>, die <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> und <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> für Attribute übernimmt, die für die Entitäten zurückgegeben werden sollen, die mit <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> und <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria><xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> übereinstimmen.  
  
 In der folgenden Tabelle werden <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>-Eigenschaften aufgeführt, die nicht in einer <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataFilterExpression> verwendet werden können.  
  
|||  
|-|-|  
|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.Description>|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.DisplayName>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EnumAttributeMetadata.OptionSet>|<xref:Microsoft.Xrm.Sdk.Metadata.LookupAttributeMetadata.Targets>|  
  
 Das folgende Bespiel beschränkt die zurückgegebenen Attribute nur auf solche, die ein `OptionSet` haben und nur die <xref:Microsoft.Xrm.Sdk.Metadata.EnumAttributeMetadata.OptionSet>- und <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.AttributeType>-Eigenschaften für diese Attribute zurückgegeben:  
  
```csharp
//A condition expresson to return optionset attributes
MetadataConditionExpression[] optionsetAttributeTypes = new MetadataConditionExpression[] { 
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.Picklist),
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.State),
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.Status),
new MetadataConditionExpression("AttributeType", MetadataConditionOperator.Equals, AttributeTypeCode.Boolean)
};

//A filter expression to apply the optionsetAttributeTypes condition expression
MetadataFilterExpression AttributeFilter = new MetadataFilterExpression(LogicalOperator.Or);
AttributeFilter.Conditions.AddRange(optionsetAttributeTypes);

//A Properties expression to limit the properties to be included with attributes
MetadataPropertiesExpression AttributeProperties = new MetadataPropertiesExpression() { AllProperties = false };
AttributeProperties.PropertyNames.Add("OptionSet");
AttributeProperties.PropertyNames.Add("AttributeType");
```
  
### <a name="retrieve-relationship-metadata"></a>Beziehungsmetadaten abrufen
  
 Im <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.RelationshipQuery> -Eigenschaft übernimmt eine <xref:Microsoft.Xrm.Sdk.Metadata.Query.RelationshipQueryExpression>, um die Entitätsbeziehung <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria> und <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> anzugeben, die Sie für die Entitäten wünschen, die mit <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> und <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Criteria><xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> übereinstimmen.  
  
 Verwenden Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.RelationshipType> in den Kriterien, um anzugeben, dass Sie ManyToMany-Beziehungen oder OneToMany-Beziehungen zurückgeben möchten.  
  
 In der folgenden Tabelle werden Beziehungsmetadateneigenschaften aufgeführt, die in einer MetadataFilterExpression nicht verwendet werden können.  
  
||  
|-|  
|<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata.AssociatedMenuConfiguration>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata.CascadeConfiguration>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata.Entity1AssociatedMenuConfiguration>|  
|<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.ManyToManyRelationshipMetadata.Entity2AssociatedMenuConfiguration>|  
  
### <a name="retrieve-labels"></a>Abrufen von Beschriftungen
  
 Schließlich <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression>.<xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.LabelQuery> Schließlich akzeptiert die Eigenschaft eine <xref:Microsoft.Xrm.Sdk.Metadata.Query.LabelQueryExpression> mit der Sie einen oder mehrere ganzzahlige `LCID`-Werte angeben können, um zu bestimmen, welche lokalisierten Beschriftungen zurückgegeben werden sollen. Gültige Gebietsschema-ID-Werte finden Sie unter [Gebietsschema-ID-Diagramm (LCID)](https://go.microsoft.com/fwlink/?LinkId=122128). Wenn eine Organisation viele Sprachpakete installiert hat, werden die Beschriftungen für alle Sprachen zurückgegeben, es sei denn, Sie legen eine <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression.LabelQuery> fest.  
  
 Das folgende Bespiel definiert eine <xref:Microsoft.Xrm.Sdk.Metadata.Query.LabelQueryExpression>, die Beschriftungen auf solche beschränkt, die die bevorzugte Sprache des Benutzers darstellen.  
  
```csharp

private Guid _userId;
private int _languageCode;
```

```csharp

_userId = ((WhoAmIResponse)_service.Execute(new WhoAmIRequest())).UserId;
_languageCode = RetrieveUserUILanguageCode(_userId);
```

```csharp

protected int RetrieveUserUILanguageCode(Guid userId)
{
 QueryExpression userSettingsQuery = new QueryExpression("usersettings");
 userSettingsQuery.ColumnSet.AddColumns("uilanguageid", "systemuserid");
 userSettingsQuery.Criteria.AddCondition("systemuserid", ConditionOperator.Equal, userId);
 EntityCollection userSettings = _service.RetrieveMultiple(userSettingsQuery);
 if (userSettings.Entities.Count > 0)
 {
  return (int)userSettings.Entities[0]["uilanguageid"];
 }
 return 0;
}
```

```csharp

//A label query expression to limit the labels returned to only those for the user's preferred language
LabelQueryExpression labelQuery = new LabelQueryExpression();
labelQuery.FilterLanguages.Add(_languageCode);
```
  
<a name="BKMK_RetrievingNeworChangedMetadata"></a> 
  
## <a name="retrieve-new-or-changed-metadata"></a>Abrufen von neuen oder geänderten Metadaten

 Die Klasse <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse> gibt eine stark typisierte <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadataCollection> zurück, die die nachgefragten Daten enthält. Die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>-Klasse bietet auch einen <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.ServerVersionStamp>-Wert, den Sie an die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp>-Eigenschaft in späteren Abfragen übergeben können. Eigenschaft in späteren Anforderungen. Wenn ein Wert für die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp>-Eigenschaft eingeschlossen wird, werden nur Daten zurückgegeben, die der <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> entsprechen, und die sich geändert haben, seit der `ClientVersionStamp` abgerufen wurde. Die einzige Ausnahme davon ist, wenn <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> die <xref:Microsoft.Xrm.Sdk.Metadata.Query.MetadataQueryExpression.Properties> enthält. umfasst <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata><xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.Privileges> Rechte werden immer zurückgegeben, unabhängig vom <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp>. Dadurch kann die Anwendung bestimmen, ob wichtige Änderungen eingetreten sind, seit Sie zuletzt die Metadaten abgerufen haben. Sie können dann neue oder geänderte Metadaten im dauerhaften Metadatencache zusammenführen, sodass die Anwendung in der Lage ist, Leistungsprobleme durch das Herunterladen von Metadaten zu vermeiden, die möglicherweise nicht erforderlich sind.  
  
 Die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged> bietet eine Möglichkeit, festzustellen, welche untergeordneten Elemente in einem Metadatenelement sich geändert haben. Da alle Metadaten im Rahmen des Metadatenelements zurückgegeben werden, wenn die Beschriftung eines <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata> sich geändert hat, werden die enthaltende <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>, <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> und <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata>-Eigenschaft zurückgegeben. Die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged> ist jedoch falsch für solche, die Metadatenelemente enthalten. Nur <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.HasChanged> Eigenschaft  ist TRUE.  
  
 Das folgende Beispiel enthält eine anfängliche Abfrage durch Definieren einer <xref:Microsoft.Xrm.Sdk.Metadata.Query.EntityQueryExpression> und Durchführen einer Abfrage, bei der <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> auf Null gesetzt ist.  
  
```csharp
//An entity query expression to combine the filter expressions and property expressions for the query.
EntityQueryExpression entityQueryExpression = new EntityQueryExpression()
{

 Criteria = EntityFilter,
 Properties = EntityProperties,
 AttributeQuery = new AttributeQueryExpression()
 {
  Criteria = AttributeFilter,
  Properties = AttributeProperties
 },
 LabelQuery = labelQuery

};

//Retrieve the metadata for the query without a ClientVersionStamp
RetrieveMetadataChangesResponse initialRequest = getMetadataChanges(entityQueryExpression, null, DeletedMetadataFilters.OptionSet);

```

```csharp
protected RetrieveMetadataChangesResponse getMetadataChanges(
 EntityQueryExpression entityQueryExpression,
 String clientVersionStamp,
 DeletedMetadataFilters deletedMetadataFilter)
{
 RetrieveMetadataChangesRequest retrieveMetadataChangesRequest = new RetrieveMetadataChangesRequest()
 {
  Query = entityQueryExpression,
  ClientVersionStamp = clientVersionStamp,
  DeletedMetadataFilters = deletedMetadataFilter
 };

 return (RetrieveMetadataChangesResponse)_service.Execute(retrieveMetadataChangesRequest);

}
```

<a name="BKMK_RetrieveInformationaboutDeletedMetadata"></a>
   
## <a name="retrieve-information-about-deleted-metadata"></a>Abrufen von Informationen zu gelöschten Metadaten  

 Im <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.DeletedMetadata> Eigenschaft gibt eine <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataCollection> zurück, wenn die Eigenschaften <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> und <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.DeletedMetadataFilters> in der <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest> festgelegt sind. Die <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataCollection> enthält die <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId>-Werte von <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>,  <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> or <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase>-Objekten, die in einem Zeitlimit vom System gelöscht wurden. Weitere Informationen finden Sie unter [Ablauf gelöschter Metadaten](/dynamics365/customer-engagement/developer/retrieve-detect-changes-metadata#BKMK_DeletedMetadataExpiration).  
  
 Nutzen Sie die<xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters> Ennumeration mit der <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.DeletedMetadataFilters> um die Informationen auf die Typen von Metadaten zu beschränken, an denen Sie interessiert sind. Die <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>-Aufzählung bietet folgende Optionen:  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Entity (Standard)  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Attribute  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Relationship  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.Label  
  
-   <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>.OptionSet  
  
 Sie verwenden auch <xref:Microsoft.Xrm.Sdk.Metadata.Query.DeletedMetadataFilters>-Enumeration als Schlüssel <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.DeletedMetadata> zum Filtern der `GUID` Werte, die man im<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesResponse.DeletedMetadata> ffindet. -Eigenschaft verfügbar.  
  
 Wenn Sie einen Metadatencache entwickeln, verwenden Sie die <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId> für jedes Element, sodass Sie die gelöschten Metadatenelemente identifizieren und entfernen können.  
  
<a name="BKMK_DeletedMetadataExpiration"></a>
   
### <a name="deleted-metadata-expiration"></a>Ablauf gelöschter Metadaten  

 Metadatenelemente, der gelöscht wurden, werden für einen beschränkten Zeitraum nachverfolgt, der durch den `Organization.ExpireSubscriptionsInDays`-Wert angegeben wird. Der Standardwert ist 90 Tage. Wenn das <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest><xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> Wert zeigt an, dass die letzte Metadatenabfrage vor dem Ablaufdatum lag, wirft der Service einen `ExpiredVersionStamp`-Fehler (0x80044352) aus. Wenn Sie Daten abrufen, um einen vorhandenen Metadatencache zu aktualisieren, sollten Sie immer versuchen, diesen Fehler abzufangen und bereit sein, den Metatadatencache mit den Ergebnissen einer zweiten Abfrage zu re-initialisieren, die ohne <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> übergeben wurde. Der Fehler wird `ExpiredVersionStamp` wird auch ausgegeben, wenn Änderungen auf dem Server, wie Änderungen am `ExpireSubscriptionsInDays`-Wert, sich auf die exakte Nachverfolgung der gelöschte Metadaten auswirken.  
  
 Das folgenden Beispiel übergibt einen <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp> und fängt den `ExpiredVersionStamp` ab. Wenn der Fehler abgefangen wird, wird der Cache reintialisert, indem eine neue Abfrage mit dem <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMetadataChangesRequest.ClientVersionStamp>-Set auf `null` eingereicht wird.  
  
```csharp

protected String updateOptionLabelList(EntityQueryExpression entityQueryExpression, String clientVersionStamp)
{
 //Retrieve metadata changes and add them to the cache
 RetrieveMetadataChangesResponse updateResponse;
 try
 {
  updateResponse = getMetadataChanges(entityQueryExpression, clientVersionStamp, DeletedMetadataFilters.OptionSet);
  addOptionLabelsToCache(updateResponse.EntityMetadata, true);
  removeOptionLabelsFromCache(updateResponse.DeletedMetadata, true);

 }
 catch (FaultException<Microsoft.Xrm.Sdk.OrganizationServiceFault> ex)
 {
  // Check for ErrorCodes.ExpiredVersionStamp (0x80044352)
  // Will occur when the timestamp exceeds the Organization.ExpireSubscriptionsInDays value, which is 90 by default.
  if (ex.Detail.ErrorCode == unchecked((int)0x80044352))
  {
   //reinitialize cache
   _optionLabelList.Clear();

   updateResponse = getMetadataChanges(entityQueryExpression, null, DeletedMetadataFilters.OptionSet);
   //Add them to the cache and display the changes
   addOptionLabelsToCache(updateResponse.EntityMetadata, true);

  }
  else
  {
   throw ex;
  }

 }
 return updateResponse.ServerVersionStamp;
}
```

  
<a name="BKMK_PerformanceRetrievingDeletedMetadata"></a>
   
### <a name="performance-when-retrieving-deleted-metadata"></a>Leistung beim Abrufen gelöschter Metadaten 
 
 Wenn ein Metadatenelement gelöscht wird, wird es in der Datenbank gespeichert, und nicht im Dynamics 365-Metadatencache. Obwohl die gelöschte Metadaten nur auf die <xref:Microsoft.Xrm.Sdk.Metadata.MetadataBase.MetadataId> und den Typ des Metadatenelements beschränkt sind, ist der Zugriff auf die Datenbank ein Vorgang, der mehr Serverressourcen erfordert als nur die Abfrage nach Änderungen.  
  
### <a name="see-also"></a>Siehe auch  
 [Schreiben von Anwendungen und Servererweiterungen](/dynamics365/customer-engagement/developer/extend-dynamics-365-server)   
 [Offline-Verwendung der Dynamics 365-Services](/dynamics365/customer-engagement/developer/org-service/offline-use-services)   
 [Beispiel: Abfragen von Metadaten und Erkennen von Änderungen](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/MetadataQuery)   
 [Erweitern Sie das Metadatenmodell für Dynamics 365](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)   
 [Anpassen von Entitätsmetadaten](/dynamics365/customer-engagement/developer/customize-entity-metadata)   
 [Anpassen von Entitätsattributmetadaten](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)   
 [Anpassen von Entitätsbeziehungsmetadaten](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)   
 [Abfragemetadaten mit JavaScript](https://msdn.microsoft.com/library/jj919080.aspx)

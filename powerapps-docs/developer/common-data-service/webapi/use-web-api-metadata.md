---
title: Nutzen der Web-API mit Metadaten (Common Data Service) | Microsoft Docs
description: 'Dieser Abschnitt enthält Anweisungen dazu, wie die Web-API mit Entitätstypen verwendet wird, die in der WEB-API-Metadaten-EntityType-Referenz enthalten sind.'
ms.custom: ''
ms.date: 11/04/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: a0edc029-c6db-48ac-9538-b0270fe94440
caps.latest.revision: 10
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-web-api-with-metadata"></a>Verwenden der Web-API mit Metadaten

Sie können die Metadatenvorgänge mit der Web-API ausführen, die Sie mithilfe des Organisationsservice ausführen können. Dieser Abschnitt enthält Anweisungen dazu, wie die Web-API mit Entitätstypen, die in der <xref:Microsoft.Dynamics.CRM.MetadataEntityTypeIndex> enthalten sind, verwendet werden.  
  
 Es gibt vier festgelegte Pfade der Entität, die verfügbar gemacht werden, um Vorgänge mit Metadatenentitäten auszuführen (siehe folgende Tabelle).  
  
|Festgelegter Pfad der Entität|Beschreibung|  
|---------------------|-----------------|  
|*[Organisations-URI]*/api/data/v9.0/EntityDefinitions|Enthält <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" />-Entitäten.|  
|*[Organisations-URI]*/api/data/v9.0/RelationshipDefinitions|Enthält <xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" /> und <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" />, da beide von <xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" /> erben.|  
|*[Organisations-URI]*/api/data/v9.0/GlobalOptionSetDefinitions|Enthält den global definierten <xref href="Microsoft.Dynamics.CRM.BooleanOptionSetMetadata?text=BooleanOptionSetMetadata EntityType" /> und <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" />, da beide von <xref href="Microsoft.Dynamics.CRM.OptionSetMetadata?text=OptionSetMetadata EntityType" /> erben.|  
|*[Organisations-URI]*/api/data/v9.0/ManagedPropertyDefinitions|Nur zur internen Verwendung.|  
  
Jeder Metadatenentitätstyp verwendet `MetadataId` als eindeutigen Bezeichnereigenschaft, die vom, <xref href="Microsoft.Dynamics.CRM.MetadataBase?text=MetadataBase EntityType" /> erbt. Wenn alle Metadatenentitäten eine `MetadataId`besitzen, können Sie nicht alle direkt abrufen. Beispielsweise können Sie Vorgänge für Attribute nur im Rahmen der `EntityMetadata`-Entität abfragen und ausführen, die sie enthält.  
  
Für einige Entitäten gelten erhebliche Unterschiede hinsichtlich der Entitäten, die Unternehmens- und Anwendungsdaten speichern, z.B.:  
  
- Die Eigenschaften für Metadatenentitäten verwenden viele der Komplex- und Enumerationstypen, die in <xref:Microsoft.Dynamics.CRM.ComplexTypeIndex> und <xref:Microsoft.Dynamics.CRM.EnumTypeIndex> definiert sind, anstelle de der primitiven Datentypen, die für Eigenschaften in Entitäten verwendet werden, die von <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" /> erben.  
  
- Metadatenentitäten folgen einer anderen Namenskonvention und verwenden die Pascal-Schreibung, die in den Assemblys des Organisationsservice verwendet wird.  
  
- Metadatenentitäten nutzen die Vererbung intensiver. Deshalb müssen Sie möglicherweise Umwandlungen ausführen, um die Daten abzurufen, die Sie verwenden möchten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt 

[Metadatenabfrage mit Web-API](query-metadata-web-api.md)<br />
Sie können die Web-API verwenden, um Metadaten mithilfe des Abfragestils RESTful abzufragen.  

[Abrufen von Metadaten über den Namen oder die MetadataId](retrieve-metadata-name-metadataid.md)<br />
Ihre Anwendungen können durch Abrufen von Metadaten an Konfigurationsänderungen anpassen. Wenn Sie eine der Schlüsseleigenschaften eines Metadatenelements kennen, können Sie Metadatendefinitionen mit der Web-API abrufen.  

[Erstellen und Aktualisieren von Entitätsdefinitionen mit der Web-API](create-update-entity-definitions-using-web-api.md)<br />
Sie können die Entitäten und Attribute mit der Web-API erstellen und aktualisieren, um die gleichen Ergebnisse zu erzielen, die Sie mit dem Organisationsservice <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> und <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest> erhalten.  

[Erstellen und Aktualisieren von Entitätsbeziehungen mit der Web-API](create-update-entity-relationships-using-web-api.md)<br />
Sie können feststellen, ob Entitäten sich für die Teilnahme an einer Beziehung mit anderen Entitäten eignen, und anschließend diese Beziehungen mit der Web-API erstellen oder aktualisieren.  

### <a name="see-also"></a>Siehe auch


<!-- TODO [Metadata and data models](../metadata-data-models.md)<br /> -->
[Durchsuchen Sie Metadaten für die Organisation](../browse-your-metadata.md)<br />
<!--  TODO [Use the Organization service with Common Data Service metadata](../org-service/use-organization-service-metadata.md)<br /> -->
[Common Data Service-Web-API verwenden](overview.md)

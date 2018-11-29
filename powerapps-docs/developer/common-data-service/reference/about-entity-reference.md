---
title: Über die Entitätsreferenz (Common Data Service for Apps)| Microsoft Docs
description: 'Verwenden Sie diese Referenz, um die verfügbaren Vorgänge, die für bestimmte Entitäten, die Standardattributattribute, Attribute jeder Entität und Beziehungen zwischen Entitäten ausgeführt werden können, zu verstehen.'
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="about-the-entity-reference"></a>Über die Entitätsreferenz

Verwenden Sie diese Referenz, um die verfügbaren Vorgänge, die für bestimmte Entitäten, die Standardattributattribute jeder Entität und Beziehungen zwischen Entitäten ausgeführt werden können, zu verstehen.

> [!NOTE]
> Diese Referenz enthält nur Entitäten, bei denen:
>
> -  **IsPrivate** ist `false`
>    - Außer den Entitäten, bei denen keine externen Anwendungsfälle vorhanden sein.
> - **IsIntersect** ist `false`
>    - Außer den Entitäten, die zur Bestimmung der N:n-Beziehungen verwendet werden.
> - Die Entität unterstützt eine Art direkten Datenmodifikationsvorgang.
>    - Dies schließt Entitäten aus, mit denen Sie nicht direkt arbeiten können. 
>
> Alle Entitätsmetadateninformationen für Ihre Umgebung finden Sie unter: [CDS for Apps-Entwicklerhandbuch: Metadaten für Ihr Unternehmen durchsuchen](/dynamics365/customer-engagement/developer/browse-your-metadata).


## <a name="entity-properties"></a>Entitätseigenschaften

Zu diesem Abschnitt zählen eher ausgewählte Entitätseigenschaften als alle davon. Nur Eigenschaften, die für Entwickler am hilfreichsten sein sollen, werden eingeschlossen. Einige Entitätseigenschaftswerte können geändert werden.

## <a name="attributes"></a>Attribute
Attribute werden in zwei unterschiedlichen Abschnitten aufgeführt: **Druckattribute** und **Schreibschutzattribute**. Das Ziel dieser Trennung ist sich auf den Attributen zu konzentrieren, die einer Entwickler festlegen kann, wenn eine Entitätsinstanz erstellt oder aktualisiert wird. Diese Attribute verstanden zu haben kann einem Entwickler helfen, zu verstehen, was er mit der Entität außer der bloßen Übersicht der Werte machen kann. 

Die Attribute im Abschnitt **Druckattribute** setzen „true” *entweder* für die Eigenschaft **IsValidForCreate** oder für die Eigenschaft **IsValidForUpdate**, (in der Regel die beiden). Wenn eine dieser Eigenschaften als „false” gesetzt wird, wird das angegeben.

**Schreibgeschützte Attribute** geben für die Eigenschaften **IsValidForCreate** *und* **IsValidForUpdate** immer false zurück.

## <a name="relationships"></a>Beziehungen

Die Klasse [EntityMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata) enthält drei Eigenschaften zur Darstellung von Beziehungen:

|Eigenschaft| Typ  |Beschreibung  |
|---------|---------|---------|
|[OneToManyRelationships](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.onetomanyrelationships#Microsoft_Xrm_Sdk_Metadata_EntityMetadata_OneToManyRelationships)|[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)[]|Ruft das Array von 1:n-Beziehungen für die Entität aus.|
|[EntityMetadata.ManyToOneRelationships](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.manytoonerelationships#Microsoft_Xrm_Sdk_Metadata_EntityMetadata_ManyToOneRelationships)|[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)[]|Ruft das Array von N:1-Beziehungen für die Entität aus.|
|[EntityMetadata.ManyToManyRelationships](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata.manytomanyrelationships#Microsoft_Xrm_Sdk_Metadata_EntityMetadata_ManyToManyRelationships)|[ManyToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata)[]|Ruft das Array von N:n-Beziehungen für die Entität aus.|

> [!NOTE]
> Es ist wichtig zu beachten, dass jede Entität zwar die Beziehungen auflistet, die für sie gelten, aber jede Beziehung von beiden Entitäten geteilt wird. Die Beziehungen bestehen *zwischen* den Entitäten. Wenn die 1:n-Beziehungen existieren, sind die *N:1*-Beziehungen eine bloße Übersicht einer 1:n-Beziehung von der Referenzentität.

### <a name="one-to-many-relationships"></a>Eins-zu-viele-Beziehungen
Um darzustellen, dass es keine tatsächlichen *N:1*-Beziehungen mit einer minimalen Verwechslungschance gibt, werden die Details jeder Beziehung nur einmal dokumentiert. Jede 1:n-Beziehung ist in der referenzierten Entität aufgelistet und enthält ausgewählte Beziehungsdetails und einen Link zu der entsprechenden *N:1*-Beziehung. Jede *N:1* aufgeführte Beziehung enthält nur einen Link zur entsprechenden 1:n-Beziehung.

Für jede 1: n-Beziehung sind folgende Eigenschaften enthalten:

|Eigenschaft|Beschreibung|
|---------|---------|
|`ReferencingEntity`|Der logische Name der zugehörigen Entität.|
|`ReferencingAttribute`|Der logische Name des Attributs in der zugehörigen Entität, das einen Verweis auf den Primärschlüssel der primären Entität enthält.|
|`IsHierarchical`|Ob die Beziehung eine auf sich selbst verweisende hierarchische Beziehung darstellt|
|`IsCustomizable`|Ob die Eigenschaften der Beziehung geändert werden können.|
|`ReferencedEntityNavigationPropertyName`|Der Name der von der Web-API-Sammlung bewerteten Navigationseigenschaft für diese Beziehung.<br />Weitere Informationen:[Common Data Service for Apps Entwicklerhandbuch Navigationseigenschaften](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#navigation-properties)|
|`AssociatedMenuConfiguration`|Daten, die von modellgesteuerten Apps verwendet werden, um zu steuern, ob und wie auf die zugehörigen Entitätsdaten in der Benutzeroberfläche von der primären Entität aus zugegriffen werden kann.|
|`CascadeConfiguration`|Daten, die beschreiben, welche Vorgänge an der übergeordneten Entität ausgeführt werden, die bis zu den verknüpften Entitäten kaskadiert werden.<br />Weitere Informationen: [Konfiguration kaskadieren](../entity-relationship-metadata.md#cascade-configuration)|


### <a name="many-to-many-relationships"></a>Viele-zu-viele-Beziehungen
Jede n: n-Beziehung enthält [Entity1LogicalName](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata.entity1logicalname) und [Entity2LogicalName](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata.entity2logicalname). Weitere Details zu dieser Dokumentationsbeziehung sind nur im Thema *Entity1* enthalten. Jede N:n-Beziehung, in der die Entität *Entity2* ist, enthält nur einen Link zu den Details, die im Thema *Entity1* gefunden wurden.

Für jede n: n-Beziehung sind folgende Eigenschaften enthalten:

|Eigenschaft|Beschreibung|
|---------|---------|
|`IntersectEntityName`|Der logische Name der überschneidenden Entität , die diese n: n-Beziehung unterstützt|
|`Entity1LogicalName`|Der logische Name der ersten Entität in der Beziehung.|
|`Entity1IntersectAttribute`|Der logische Name des Attributs der sich überschneidenden Entität, das eine Referenz auf den Primärschlüssel der ersten Entität enthält.|
|`Entity1NavigationPropertyName`|Der Name der von der Web-API-Sammlung bewerteten Navigationseigenschaft für diese Beziehung.<br />Weitere Informationen: [Common Data Service for Apps Entwicklerhandbuch Navigationseigenschaften](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations#navigation-properties)|
|`Entity1AssociatedMenuConfiguration`|Daten, die von modellgesteuerten App verwendet werden, um zu steuern, ob und wie auf die ersten Entitätsdaten in der Benutzeroberfläche von der zweiten Entität aus zugegriffen werden kann.|
|`Entity2LogicalName`|Der logische Name der zweiten Entität in der Beziehung.|
|`Entity2IntersectAttribute`|Der logische Name des Attributs der sich überschneidenden Entität, das eine Referenz auf den Primärschlüssel der zweiten Entität enthält.|
|`Entity2NavigationPropertyName`|Hierbei handelt es sich in der Regel um denselben Wert wie bei dem `Entity1NavigationPropertyName`|
|`Entity2AssociatedMenuConfiguration`|Daten, die von modellgesteuerten Apps verwendet werden, um zu steuern, ob und wie auf die zweiten Entitätsdaten in der Benutzeroberfläche von der ersten Entität aus zugegriffen werden kann.|
|`IsCustomizable`|Ob die Eigenschaften der Beziehung geändert werden können.|


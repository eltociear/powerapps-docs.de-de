---
title: API-Überlegungen virtueller Entitäten (Common Data Service) | Microsoft-Dokumentation
description: Beschreibt API-Überlegungen von virtuellen Einheiten.
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: d329dade-16c5-46e9-8dec-4b8efb996dea
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cbd3da97fcf4e2f8d21f5475221eb39455c09050
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748507"
---
# <a name="api-considerations-of-virtual-entities"></a>API-Rücksichten auf virtuelle Entitäten

Es gibt zwei breite Kategorien der Änderungen, die mit der Einführung der virtuellen Entitäten in Common Data Service verbunden sind, am Metadatensystem:

- Hinzufügung eines neuen Assemblys, der Namespaces, Klassen und anderer Typen, um die Entwicklung der virtuellen Entitätsdatenanbieter zu unterstützen
- Änderungen an der Kernplattform einschließlich einige zusätzliche Eigenschaften, um die externe Datenquellenzuordnung und Modifizierung des Verhaltens der vorhandenen Entitäts- und Attributeigenschaften, die die Beschränkungen der ursprünglichen Implementierung dieser Funktion widerspiegeln, zu unterstützen

## <a name="dynamics-365-data-sdk-assembly"></a>Dynamics 365 Data SDK-Assembly

Das Dynamics 365 Data SDK-Assembly, `Microsoft.Xrm.Sdk.Data.dll`, enthält Typen, die bei der Erstellung der benutzerdefinierten virtuellen Entitätsdatenanbieter hilfreich sind. Es ist in den folgenden Namespaces enthalten:

|Namespace|Beschreibung|
|---------|---------|
|<xref:Microsoft.Xrm.Sdk.Data>|Basis-Namespace, der einige allgemeine Typen enthält wie z.B. **AllowedQueryOptions**-Enumeration.|
|<xref:Microsoft.Xrm.Sdk.Data.CodeGen>|Enthält Klassen und Schnittstellen, die die dynamische Reflektion, den Typenabgleich und die Codegenerierung unterstützen.  Hauptsächlich wird von der internen Anbieterengine genutzt.|
|<xref:Microsoft.Xrm.Sdk.Data.Converters>|Einer Satz der Klassen, um Standard-XRM-Typen in ihre entsprechenden .NETs-Basistypen zu konvertieren.|
|<xref:Microsoft.Xrm.Sdk.Data.Exceptions>|Einer Satz der Ausnahmeklassen, die Fehler darstellen, die während der Ablaufwertlösung auftreten können.  Alle resultieren aus Microsoft.Xrm.Sdk.SdkExceptionBase.|
|<xref:Microsoft.Xrm.Sdk.Data.Expressions>|Klassen, um bei der Implementierung der unterstützten Abfragentransformationen wie FILTER, JOIN und ORDER zu helfen.|
|<xref:Microsoft.Xrm.Sdk.Data.Infra>|Einige andere Klassen, die die zentrale Abfrageverarbeitung unterstützen.|
|<xref:Microsoft.Xrm.Sdk.Data.Mappings>|Klassen und Schnittstellen, die die Zuordnung von den Entitätsmetadatentypen zu den externen Typen aufbaut.|
|Microsoft.Xrm.Sdk.Data.Visitors|Klassen, die die [Besuchermuster](https://en.wikipedia.org/wiki/Visitor_pattern) implementieren, um bestimmte Operationen für den **QueryExpression**-Parameter, übergaben an den Datenanbieter über **RetrieveMultiple**-Anfragen, auszuführen. Gewährt bestimmte Unterstützung für Verarbeitung allgemeiner und LINQ-basierten Abfragen. Diese Klassen resultieren aus Microsoft.Xrm.Sdk.Query.QueryExpressionVisitorBase.|

Diese Assembly wird als NuGet-Paket verteilt: [Microsoft.CrmSdk.Daten](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

## <a name="changes-to-the-core-platform"></a>Änderungen an der Kernplattform

Die folgenden Änderungen an den Standardreferenztypen Common Data Service wurden eingeführt, um virtuelle Entitäten zu unterstützen.

### <a name="new-entities"></a>Neue Entitäten

Das Common Data Service stellt virtuelle Entitätsdatenanbieter und -quellen als die folgenden neuen Entitäten dar: [EntityDataProvider](../reference/entities/entitydataprovider.md) [und EntityDataSource](../reference/entities/entitydatasource.md). 

### <a name="new-metadata-properties"></a>Neue Metadateneigenschaften

Vier neue Eigenschaften wurden zur Klasse <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata> hinzugefügt:

|Eigenschaft|Beschreibung|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataProviderId>|GUID, die den zugehörigen virtuellen Entitätsdatenanbieter identifiziert.|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataSourceId>|GUID, das die zugewiesene virtuelle Entitätsdatenquelle bestimmt.|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ExternalName>|Name für diesen Typ in der externen Datenquelle|
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ExternalCollectionName>|Pluralname für diesen Typ, der in der UI und zur Unterstützung des OData-Zugriffs verwendet wird.|

Zwei neue Eigenschaften wurden zur Klasse <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> hinzugefügt:

|Eigenschaft|Beschreibung|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.ExternalName>|Name für diesen Typ in der externen Datenquelle|
|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsDataSourceSecret>|Bestimmt, ob das Feld vertrauliche Informationen enthält.|

Die `ExternalName`-Eigenschaft wurde ebenfalls den Klassen <xref:Microsoft.Xrm.Sdk.Metadata.OptionMetadata> und <xref:Microsoft.Xrm.Sdk.Metadata.OptionSetMetadata> übergeben. Diese externe Namen helfen bei der externen Datenquellenzuordnung, indem der Name des verbundenen Typs in der externen Datenquelle bestimmt wird. Diese Eigenschaften werden nur für virtuelle Entitäten verwendet; für einen eingebauten oder Standardtyp der benutzerdefinierten Entität müssen diese externen Namen `null` sein.


### <a name="virtual-entity-creation"></a>Erstellung einer virtuellen Entität

Die Vorgehensweise der programmgesteuerten Erstellung eines virtuellen Entitätstyps unterscheidet sich etwas von einer Erstellung der benutzerdefinierten Entitätstypen wie folgt:

- Wenn der verbundene Datenanbieter (und Datenquelle optional) am Erstellungszeitpunkt bekannt ist, dann werden diese bestimmt.
- Wenn der Datenanbieter für den Typ unbekannt ist, dann wird <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataProviderId> auf zumindest auf `7015A531-CC0D-4537-B5F2-C882A1EB65AD` festgelegt, und die <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.DataSourceId> wird auf `null` festgelegt. Bevor Instanzen dieses Typs zur Laufzeit verwendet werden, müssen diesen Eigenschaften entsprechende Werten zugewiesen werden.

Zwei neue Entitäten, [EntityDataProvider](../reference/entities/entitydataprovider.md) und optional [EntityDataSource](../reference/entities/entitydatasource.md), werden erstellt, wenn Sie ein Plug-In registrieren und die jeweiligen IDs, `entitydataproviderid` und `entitydatasourceid`, die erforderlichen GUIDs darstellen. (Andernfalls müssen die Entwickler manchmal diese benutzerdefinierten Typen direkt aufrufen.) Beachten Sie, dass diese Datenquelle die Eigenschaft `entitydataproviderid`, die mit dem entsprechenden Datenanbietertyp übereinstimmen muss, enthält, oder eine Ablaufausnahme wird ausgelöst.

> [!WARNING]
> (Nicht virtuelle) Standard-Entitäten müssen die Werte derer verbundenen `DataProviderId` und `DataSourceId`, die für deren Standardwerte (`null`)festgelegt sind, besitzen; andernfalls wird eine Ablaufausnahme ausgelöst.  Sobald es erstellt wurde, können Sie nicht von einem nicht virtuellen Typ in einen virtuellen Typ oder zurück konvertieren. 

### <a name="entity-metadata-property-behavior-changes"></a>Entitätsmetadateneigenschaften-Verhaltensänderungen

Die folgenden Tabellendetails darüber, wie das Verhalten von [EntityMetadata-Eigenschaften](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata?view=dynamics-general-ce-9#properties) geändert wird, wenn diese zu den virtuellen Entitäten angewendet werden. Einige Eigenschaften sind für virtuelle Entitäten ungültig, während andere im Umfang oder im Wert beschränkt sind.

|**Metadateneigenschaft**|**Anwendbar?**|**Notizen**|
|---------------------|------------|---------|
|ActivityTypeMask|_ungültig_|Immer 0|
|Attribute|Gültig||
|AutoCreateAccessTeams|_ungültig_|Immer false|
|AutoRouteToOwnerQueue|_ungültig_|Immer false, Abfragen werden nicht unterstützt.|
|CanBeInManyToMany|Gültig||
|CanBePrimaryEntityInRelationship|Gültig||
|CanBeRelatedEntityInRelationship|Gültig||
|CanChangeHierarchicalRelationship|_ungültig_|Immer false, hierarchische Beziehungen werden nicht unterstützt.|
|CanChangeTrackingBeEnabled|_ungültig_|Immer false, die Änderungsnachverfolgung und -überwachung werden nicht unterstützt.|
|CanCreateAttributes|Gültig||
|CanCreateCharts|_ungültig_|Immer false|
|CanCreateForms|Gültig||
|CanCreateViews|Gültig||
|CanEnableSyncToExternalSearchIndex|_ungültig_|Immer false|
|CanModifyAdditionalSettings|Gültig||
|CanTriggerWorkflow|_ungültig_|Immer false, Workflows können nicht gestartet werden.
|ChangeTrackingEnabled|_ungültig_|Immer false|
|CollectionSchemaName|Gültig||
|DaysSinceRecordLastModified|_ungültig_|Immer null oder 0|
|Beschreibung|Gültig||
|DisplayCollectionName|Gültig||
|DisplayName|Gültig||
|EnforceStateTransitions|_ungültig_|StateCode und Status werden nicht unterstützt.|
|EntityColor|Gültig||
|EntityHelpUrl|Gültig||
|EntityHelpUrlEnabled|Gültig||
|EntitySetName|Gültig||
|ExtensionData|_ungültig_|Veraltete Eigenschaft|
|HasChanged|Gültig||
|IconLargeName|Gültig||
|IconMediumName|Gültig||
|IconSmallName|Gültig||
|IntroducedVersion|Gültig||
|IsActivity|_ungültig_|Immer false, Aktivitäten werden nicht unterstützt.|
|IsActivityParty|_ungültig_|Immer false|
|IsAIRUpdated|_ungültig_|Veraltet|
|IsAuditEnabled|_ungültig_|Immer false, die Überwachung wird nicht unterstützt.|
|IsAvailableOffline|_ungültig_|Immer false, Offline-Nutzung wird nicht unterstützt.|
|IsBusinessProcessEnabled|_ungültig_|Immer false, Geschäftsprozesse werden nicht unterstützt.|
|IsChildEntity|_ungültig_|Immer false, alle virtuellen Entitäten sind im Besitz einer Organisation.|
|IsConnectionsEnabled|Gültig|<!-- TODO: Connection support is still TBD for Potassium -->|
|IsCustomEntity|Gültig||
|IsCustomizable|Gültig||
|IsDocumentManagementEnabled|Gültig||
|IsDocumentRecommendationsEnabled|_ungültig_|Immer false, die neue Funktion wird nicht unterstützt.|
|IsDuplicateDetectionEnabled|_ungültig_|Immer false, aber Duplikaterkennung kann an der Datenquelle ausgeführt werden.|
|IsEnabledForCharts|_begrenzt_|Nur für unterstützte Fetch-Klassen.|
|IsEnabledForTrace|Gültig||
|IsImportable|Gültig|<!--TODO: May have limitations. -->|
|IsInteractionCentricEnabled|Gültig||
|IsIntersect|Gültig||
|IsKnowledgeManagementEnabled|_ungültig_|Immer false, Wissensmanagement-Integration wird nicht unterstützt.|
|IsMailMergeEnabled|Gültig||
|IsManaged|Gültig||
|IsMappable|Gültig||
|IsOfflineInMobileClient|_ungültig_|Immer false, virtuelle Entitätswerte werden für Offline-Nutzung nicht zwischengespeichert.|
|IsOneNoteIntegrationEnabled|Gültig||
|IsOptimisticConcurrencyEnabled|_ungültig_|Immer false, Parallelität muss in der Datenquelle implementiert werden.|
|IsPrivate|Gültig||
|IsQuickCreateEnabled|Gültig||
|IsReadOnlyInMobileClient|Gültig||
|IsRenameable|Gültig||
|IsSLAEnabled|_ungültig_|Immer false|
|IsStateModelAware|_ungültig_|<!-- TODO: TBD? -->|
|IsValidForAdvancedFind|Gültig||
|IsValidForQueue|Gültig||
|IsVisibleInMobile|Gültig||
|IsVisibleInMobileClient|Gültig||
|Schlüssel|_ungültig_|Alternativschlüssel werden nicht unterstützt.|
|LogicalCollectionName|Gültig||
|LogicalName|Gültig||
|ManyToManyRelationships|Gültig||
|ManyToOneRelationships|Gültig| Nicht unterstützt zwischen zwei virtuellen Entitäten. |
|MetadataId|Gültig||
|MobileOfflineFilters|_ungültig_|Immer false, Offline-Nutzung wird nicht unterstützt.|
|ObjectTypeCode|Gültig||
|OneToManyRelationships|Gültig||
|OwnershipType|_ungültig_|Immer **OrganizationOwned**|
|PrimaryIdAttribute|Gültig||
|PrimaryImageAttribute|Gültig||
|PrimaryNameAttribute|Gültig||
|Rechte|_ungültig_|<!-- TODO: TBD? -->|
|RecurrenceBaseEntityLogicalName|_ungültig_||
|ReportViewName|_ungültig_||
|SchemaName|Gültig||
|SyncToExternalSearchIndex|_ungültig_||

<!-- TODO: Add links to reference properties in first column. -->


### <a name="attribute-metadata-property-behavior-changes"></a>Attributmetadateneigenschaften-Verhaltensänderungen

Die folgende Tabellen zeigt, wie das Verhalten von [AttributeMetadata-Eigenschaften](/dotnet/api/microsoft.xrm.sdk.metadata.attributemetadata?view=dynamics-general-ce-9#properties) geändert wird, wenn diese zu den virtuellen Entitäten angewendet werden. Einige Eigenschaften sind für virtuelle Entitäten ungültig, während andere im Umfang oder im Wert beschränkt sind.

|**Metadateneigenschaft**|**Anwendbar?**|**Notizen**|
|---------------------|------------|---------|
|ColumnNumber|_ungültig_||
|DeprecatedVersion|Gültig||
|Beschreibung|Gültig||
|DisplayName|Gültig||
|EntityLogicalName|Gültig||
|ExtensionData|_ungültig_|<!-- TODO: TBD? -->|
|HasChanged|Gültig||
|InheritsFrom|Gültig||
|IntroducedVersion|Gültig||
|IsAuditEnabled|_ungültig_|Immer false, die Überwachung wird nicht unterstützt.|
|IsCustomAttribute|Gültig||
|IsCustomizable|Gültig||
|IsFilterable|Gültig||
|IsGlobalFilterEnabled|Gültig||
|IsLogical|Gültig||
|IsManaged|Gültig||
|IsPrimaryId|Gültig||
|IsPrimaryName|Gültig||
|IsRenameable|Gültig||
|IsSearchable|Gültig||
|IsSecured|_ungültig_|Immer false, die Sicherheit auf der Feldebene wird nicht unterstützt.|
|IsSortableEnabled|Gültig||
|IsValidForAdvancedFind|Gültig||
|IsValidForCreate|Gültig||
|IsValidForRead|Gültig||
|IsValidForUpdate|Gültig||
|LinkedAttributeId|Gültig||
|LogicalName|Gültig||
|MetadataId|Gültig||
|RequiredLevel|Gültig||
|SchemaName|Gültig||
|SourceType|_ungültig_|Immer 0, berechnet oder Rollupwerte werden nicht unterstützt.|

### <a name="see-also"></a>Siehe auch

[Erste Schritte mit virtuellen Entitäten](get-started-ve.md)<br />
[Benutzerdefinierte virtuelle Entitätsdatenanbieter](custom-ve-data-providers.md)<br />
[Beispiel: Generisches virtuelles Entitätsdatenanbieter-Plug-In](sample-generic-ve-plugin.md)


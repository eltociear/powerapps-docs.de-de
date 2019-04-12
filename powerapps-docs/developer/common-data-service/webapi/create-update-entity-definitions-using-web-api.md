---
title: Erstellen und Aktualisieren Sie Entitätsdefinitionen mithilfe von Web-API (Common Data Service) | Microsoft Docs
description: Informationen zum Erstellen und Aktualisieren von Entitätsdefinitionen mit Internet-API.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 1f430d2d-e829-4ffa-922e-dfcfb7c9e86e
caps.latest.revision: 24
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-update-entity-definitions-using-the-web-api"></a>Erstellen und Aktualisieren von Entitätsdefinitionen mit der Web-API



Sie können die gleichen Vorgänge für Modellentitäten ausführen wie beim Organisationsservice. Der Schwerpunkt dieses Themas liegt auf der Arbeit mit Metadatenentitäten mithilfe der Web-API. Details zu Entitäts-Metadateneigenschaften finden Sie unter [Anpassen von Entitätsmetadaten](../customize-entity-metadata.md) and <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" />.  

<a name="bkmk_createEntities"></a>

## <a name="create-entities"></a>Entitäten erstellen

Zum Erstellen einer Entität POST die JSON-Darstellung der Entitätsdaten für den `EntityDefinitions`-Entitätspfad. Die Entität muss über die Definition für das primäre Namensattribut für die Entität verfügen. Sie müssen nicht Werte für alle Eigenschaften festlegen. Die Elemente in der Liste mit Ausnahme von Beschreibung sind erforderlich, obwohl die Festlegung einer Beschreibung eine empfohlene bewährte Methode ist. Eigenschaftswerte, die Sie nicht angeben, werden auf Standardwerte festgelegt. Zum Kennenlernen von Standardwerten siehe das Beispiel im Abschnitt [Aktualisieren von Entitäten](create-update-entity-definitions-using-web-api.md#bkmk_updateEntities). Das Beispiel in diesem Thema verwendet die folgenden Entitätseigenschaften.  
  
|Entitätseigenschaft|Value|  
|---------------------|-----------|  
|SchemaName|new_BankAccount **Hinweis:** Sie sollten das Anpassungspräfix einschließen, das dem Lösungsherausgeber entspricht. Hier wird der Standardwert „new_” verwendet, aber sie sollten das Präfix auswählen, das für die Lösung funktioniert.|  
|DisplayName|Bankkonto|  
|DisplayCollectionName|Bankkonten|  
|Beschreibung|Eine Entität, um Informationen zu Kundenbankkonten zu speichern.|  
|OwnershipType|UserOwned **Hinweis:** Werte, die Sie hier festlegen können, finden Sie unter <xref href="Microsoft.Dynamics.CRM.OwnershipTypes?text=OwnershipTypes EnumType" />.|  
|IsActivity|false|  
|HasActivities|false|  
|HasNotes|false|  
  
 Zusätzlich zu den zuvor aufgelisteten Eigenschaften muss die `EntityMetadataAttributes`-Eigenschaft ein Array enthalten, das einen <xref href="Microsoft.Dynamics.CRM.StringAttributeMetadata?text=StringAttributeMetadata EntityType" /> enthält, um das primäre Namensattribut darzustellen für die Entität. Die Attributeigenschaft IsPrimaryName muss „true” sein. Die folgende Tabelle beschreibt die im Beispiel festgelegten Eigenschaften.  
  
|Primäre Attributeigenschaft|Value|  
|--------------------------------|-----------|  
|SchemaName|new_AccountName|  
|RequiredLevel|Keine <br />**Hinweis:** Werte, die Sie hier festlegen können, finden Sie unter <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevelManagedProperty?text=AttributeRequiredLevelManagedProperty ComplexType" /> und <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevel?text=AttributeRequiredLevel EnumType" />.|  
|MaxLength|100|  
|FormatName|Text <br />**Hinweis:** Das primäre Namensattribut muss das Text-Format verwenden. Formatoptionen für andere Zeichenfolgenattribute finden Sie unter [String-Formate](../entity-attribute-metadata.md#string-formats).|  
|DisplayName|Firmenname|  
|Beschreibung|Geben Sie den Namen des Bankkontos ein.|  
|IsPrimaryName|true|  
  
> [!NOTE]
>  Wenn Sie Etiketten mit <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> erstellen oder aktualisieren, müssen Sie nur die Eigenschaft `LocalizedLabels` festlegen. Der `UserLocalizedLabel`-Wert, der zurückgegeben wird, basiert auf der Spracheinstellung des Benutzers und ist schreibgeschützt.  
  
Im folgenden Beispiel wird das Erstellen einer benutzerdefinierten Entität mit den festgelegten Eigenschaften angezeigt. Die Sprache ist Englisch mit der Gebietsschema-ID (LCID) 1033. [!INCLUDE [lcid](../../../includes/lcid.md)]  
  
 **Anforderung**  
```http 
POST [Organization URI]/api/data/v9.0/EntityDefinitions HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
  "@odata.type": "Microsoft.Dynamics.CRM.EntityMetadata",  
 "Attributes": [  
  {  
   "AttributeType": "String",  
   "AttributeTypeName": {  
    "Value": "StringType"  
   },  
   "Description": {  
     "@odata.type": "Microsoft.Dynamics.CRM.Label",  
    "LocalizedLabels": [  
     {  
       "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
      "Label": "Type the name of the bank account",  
      "LanguageCode": 1033  
     }  
    ]  
   },  
   "DisplayName": {  
     "@odata.type": "Microsoft.Dynamics.CRM.Label",  
    "LocalizedLabels": [  
     {  
       "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
      "Label": "Account Name",  
      "LanguageCode": 1033  
     }  
    ]  
   },  
   "IsPrimaryName": true,  
   "RequiredLevel": {  
    "Value": "None",  
    "CanBeChanged": true,  
    "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
   },  
   "SchemaName": "new_AccountName",  
    "@odata.type": "Microsoft.Dynamics.CRM.StringAttributeMetadata",  
   "FormatName": {  
    "Value": "Text"  
   },  
   "MaxLength": 100  
  }  
 ],  
 "Description": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "An entity to store information about customer bank accounts",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayCollectionName": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Accounts",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Account",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "HasActivities": false,  
 "HasNotes": false,  
 "IsActivity": false,  
 "OwnershipType": "UserOwned",  
 "SchemaName": "new_BankAccount"  
}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(417129e1-207c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_updateEntities"></a>
 
## <a name="update-entities"></a>Aktualisieren von Entitäten
  
> [!IMPORTANT]
>  Sie können nicht die Methode HTTP PATCH verwenden, um Modellentitäten zu aktualisieren. Die Metadatenentitäten haben Parität mit dem Organisationsservice <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, der die Entitätsdefinition durch die eingeschlossene ersetzt. Daher müssen Sie die Methode HTTP PUT verwenden, wenn Sie Modellentitäten aktualisieren, und darauf achten, dass alle vorhandenen Eigenschaften eingeschlossen werden, die Sie nicht ändern möchten. Sie können keine einzelnen Eigenschaften aktualisieren.  
  
 Wenn Sie Metadatenentitäten mit Etiketten aktualisieren, sollten Sie eine benutzerdefinierte `MSCRM.MergeLabels`-Überschrift einschließen, um zu steuern, wie Bezeichnungen im Update bearbeitet werden sollen. Wenn eine Beschriftung für ein Element bereits Bezeichnungen für weitere Sprachen enthält und Sie sie mit einer Beschriftung aktualisieren, die nur eine Beschriftung für eine bestimmte Sprache enthält, steuert die `MSCRM.MergeLabels`-Kopfzeile, ob die vorhandenen Bezeichnungen überschrieben oder die neuen Bezeichnungen mit den vorhandenen Sprachbeschriftungen zusammengeführt werden sollen. Wenn `MSCRM.MergeLabels` auf `true` festgelegt ist, überschreiben alle neuen definierten Beschriftungen nur dann vorhandene Bezeichnungen, wenn der Sprachcode übereinstimmt. Wenn Sie die vorhandenen Bezeichnungen überschreiben möchten, damit Sie nur die von Ihnen eingeschlossenen Bezeichnungen einschließen, legen Sie `MSCRM.MergeLabels` auf `false` fest.  
  
> [!IMPORTANT]
>  Wenn Sie keine `MSCRM.MergeLabels`-Kopfzeile einschließen, ist das standardmäßige Verhalten so, als ob der Wert `false` wäre, und alle lokalisierten Bezeichnungen, die nicht in dem Update enthalten sind, gehen verloren.  
  
 Wenn Sie eine Entität bzw. ein Attribut aktualisieren, müssen Sie <xref href="Microsoft.Dynamics.CRM.PublishXml?text=PublishXml Action" /> oder <xref href="Microsoft.Dynamics.CRM.PublishAllXml?text=PublishAllXml Action" /> verwenden, damit die Änderungen, die Sie vornehmen, für die Anwendung angewendet werden. Weitere Informationen: [Veröffentlichen von Anpassungen](../../model-driven-apps/publish-customizations.md)  
  
 In der Regel rufen Sie die JSON-Definition des Attributs ab und ändern die Eigenschaften, bevor Sie sie zurücksenden. Das folgende Beispiel enthält alle Metadateneigenschaften der Entität, die in [Entitäten erstellen](create-update-entity-definitions-using-web-api.md#bkmk_createEntities) erstellt wurde, wobei aber DisplayName changed zu “Bankunternehmensname” geändert wurde. Bedenken Sie jedoch ggf., dass das JSON hier die Standardwerte für Eigenschaften verfügbar macht, die im [Entitäten erstellen](create-update-entity-definitions-using-web-api.md#bkmk_createEntities)-Beispiel nicht festgelegt werden.  
  
 **Anforderung**  
```http 
PUT [Organization URI]/api/data/v9.0/EntityDefinitions(417129e1-207c-e511-80d2-00155d2a68d2) HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
MSCRM.MergeLabels: true  
  
{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions/$entity",  
 "ActivityTypeMask": 0,  
 "AutoRouteToOwnerQueue": false,  
 "CanTriggerWorkflow": true,  
 "Description": {  
  "LocalizedLabels": [  
   {  
    "Label": "An entity to store information about customer bank accounts",  
    "LanguageCode": 1033,  
    "IsManaged": false,  
    "MetadataId": "edc3abd7-c5ae-4822-a3ed-51734fdd0469",  
    "HasChanged": null  
   }  
  ]  
 },  
 "DisplayCollectionName": {  
  "LocalizedLabels": [  
   {  
    "Label": "Bank Accounts",  
    "LanguageCode": 1033,  
    "IsManaged": false,  
    "MetadataId": "7c758e0c-e9cf-4947-93b0-50ec30b20f60",  
    "HasChanged": null  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Business Name",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "EntityHelpUrlEnabled": false,  
 "EntityHelpUrl": null,  
 "IsDocumentManagementEnabled": false,  
 "IsOneNoteIntegrationEnabled": false,  
 "IsInteractionCentricEnabled": false,  
 "IsKnowledgeManagementEnabled": false,  
 "AutoCreateAccessTeams": false,  
 "IsActivity": false,  
 "IsActivityParty": false,  
 "IsAuditEnabled": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyauditsettings"  
 },  
 "IsAvailableOffline": false,  
 "IsChildEntity": false,  
 "IsAIRUpdated": false,  
 "IsValidForQueue": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyqueuesettings"  
 },  
 "IsConnectionsEnabled": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyconnectionsettings"  
 },  
 "IconLargeName": null,  
 "IconMediumName": null,  
 "IconSmallName": null,  
 "IsCustomEntity": true,  
 "IsBusinessProcessEnabled": false,  
 "IsCustomizable": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "iscustomizable"  
 },  
 "IsRenameable": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "isrenameable"  
 },  
 "IsMappable": {  
  "Value": true,  
  "CanBeChanged": false,  
  "ManagedPropertyLogicalName": "ismappable"  
 },  
 "IsDuplicateDetectionEnabled": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyduplicatedetectionsettings"  
 },  
 "CanCreateAttributes": {  
  "Value": true,  
  "CanBeChanged": false,  
  "ManagedPropertyLogicalName": "cancreateattributes"  
 },  
 "CanCreateForms": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "cancreateforms"  
 },  
 "CanCreateViews": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "cancreateviews"  
 },  
 "CanCreateCharts": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "cancreatecharts"  
 },  
 "CanBeRelatedEntityInRelationship": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canberelatedentityinrelationship"  
 },  
 "CanBePrimaryEntityInRelationship": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canbeprimaryentityinrelationship"  
 },  
 "CanBeInManyToMany": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canbeinmanytomany"  
 },  
 "CanEnableSyncToExternalSearchIndex": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canenablesynctoexternalsearchindex"  
 },  
 "SyncToExternalSearchIndex": false,  
 "CanModifyAdditionalSettings": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyadditionalsettings"  
 },  
 "CanChangeHierarchicalRelationship": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canchangehierarchicalrelationship"  
 },  
 "IsOptimisticConcurrencyEnabled": true,  
 "ChangeTrackingEnabled": false,  
 "IsImportable": true,  
 "IsIntersect": false,  
 "IsMailMergeEnabled": {  
  "Value": true,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymailmergesettings"  
 },  
 "IsManaged": false,  
 "IsEnabledForCharts": true,  
 "IsEnabledForTrace": false,  
 "IsValidForAdvancedFind": true,  
 "IsVisibleInMobile": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobilevisibility"  
 },  
 "IsVisibleInMobileClient": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobileclientvisibility"  
 },  
 "IsReadOnlyInMobileClient": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobileclientreadonly"  
 },  
 "IsOfflineInMobileClient": {  
  "Value": false,  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifymobileclientoffline"  
 },  
 "DaysSinceRecordLastModified": 0,  
 "IsReadingPaneEnabled": true,  
 "IsQuickCreateEnabled": false,  
 "LogicalName": "new_bankaccount",  
 "ObjectTypeCode": 10009,  
 "OwnershipType": "UserOwned",  
 "PrimaryNameAttribute": "new_accountname",  
 "PrimaryImageAttribute": null,  
 "PrimaryIdAttribute": "new_bankaccountid",  
 "Privileges": [  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvCreatenew_BankAccount",  
   "PrivilegeId": "d1a8de4b-27df-42e1-bc5c-b863e002b37f",  
   "PrivilegeType": "Create"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvReadnew_BankAccount",  
   "PrivilegeId": "726043b1-de2c-487e-9d6d-5629fca2bf22",  
   "PrivilegeType": "Read"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvWritenew_BankAccount",  
   "PrivilegeId": "fa50c539-b6c7-4eaf-bd49-fd8224bc51b6",  
   "PrivilegeType": "Write"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvDeletenew_BankAccount",  
   "PrivilegeId": "17c1fd6e-f856-45e7-b563-796f53108b85",  
   "PrivilegeType": "Delete"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvAssignnew_BankAccount",  
   "PrivilegeId": "133ca81d-668e-4c19-a71e-10c6dfe099cd",  
   "PrivilegeType": "Assign"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvSharenew_BankAccount",  
   "PrivilegeId": "15f27df4-9c67-47c9-b1f1-274e1c44f24a",  
   "PrivilegeType": "Share"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvAppendnew_BankAccount",  
   "PrivilegeId": "ac8b1920-8f93-4e9d-94e3-c680e2a2f228",  
   "PrivilegeType": "Append"  
  },  
  {  
   "CanBeBasic": true,  
   "CanBeDeep": true,  
   "CanBeGlobal": true,  
   "CanBeLocal": true,  
   "CanBeEntityReference": false,  
   "CanBeParentEntityReference": false,  
   "Name": "prvAppendTonew_BankAccount",  
   "PrivilegeId": "f63a5f46-3bc7-4eac-81d0-7f77f566ef46",  
   "PrivilegeType": "AppendTo"  
  }  
 ],  
 "RecurrenceBaseEntityLogicalName": null,  
 "ReportViewName": "Filterednew_BankAccount",  
 "SchemaName": "new_BankAccount",  
 "IntroducedVersion": "1.0",  
 "IsStateModelAware": true,  
 "EnforceStateTransitions": false,  
 "EntityColor": null,  
 "LogicalCollectionName": "new_bankaccounts",  
 "CollectionSchemaName": "new_BankAccounts",  
 "EntitySetName": "new_bankaccounts",  
 "IsEnabledForExternalChannels": false,  
 "IsPrivate": false,  
 "MetadataId": "417129e1-207c-e511-80d2-00155d2a68d2",  
 "HasChanged": null  
}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  
  
<a name="bkmk_CreateAttributes"></a>

## <a name="create-attributes"></a>Erstellen von Attributen

Attribute können gleichzeitig mit der Entität erstellt werden, indem Sie die JSON-Definition der Attribute im `Attributes`-Array für die Entität einschließen, die Sie zusätzlich zum Zeichenfolgenattribut veröffentlichen, das als das primäre Namensattribut dient. Wenn Sie Attribute zu einer Entität hinzufügen möchten, die bereits erstellt wurde, können Sie eine POST-Anforderung einschließlich der zugehörigen JSON-Definition zur sammlungswertigen `Attributes`-Navigationseigenschaft der Entität senden.  
  
<a name="bkmk_CreateString"></a>

### <a name="create-a-string-attribute"></a>Erstellen eines Zeichenfolgenattributs

Das folgende Beispiel verwendet diese Eigenschaften, um ein Zeichenfolgenattribut zu erstellen.  
  
|Zeichenfolgenattributeigenschaften|Werte|  
|---------------------------------|------------|  
|SchemaName|new_BankName|  
|DisplayName|Bankname|  
|Beschreibung|Geben Sie den Namen der Bank ein.|  
|RequiredLevel|Keiner|  
|MaxLength|100|  
|FormatName|Text|  
  
Das folgende Bespiel erstellt ein Zeichenfolgenattribut mithilfe der Eigenschaften und fügt sie der Entität mit dem MetadataId-Wert 402fa40f-287c-e511-80d2-00155d2a68d2 hinzu.

Der URI für das Attribut wird in der Antwort zurückgegeben.  
  
 **Anforderung**

```http 
POST [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "AttributeType": "String",  
 "AttributeTypeName": {  
  "Value": "StringType"  
 },  
 "Description": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Type the name of the bank",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Name",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "RequiredLevel": {  
  "Value": "None",  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
 },  
 "SchemaName": "new_BankName",  
 "@odata.type": "Microsoft.Dynamics.CRM.StringAttributeMetadata",  
 "FormatName": {  
  "Value": "Text"  
 },  
 "MaxLength": 100  
}  
  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(f01bef16-287c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_createMoney"></a>

### <a name="create-a-money-attribute"></a>Erstellen eines Money-Attributs

Das folgende Beispiel verwendet diese Eigenschaften, um ein money-Attribut zu erstellen.  
  
|Money-Attributeigenschaften|Werte|  
|--------------------------------|------------|  
|SchemaName|new_Balance|  
|DisplayName|Saldo|  
|Beschreibung|Geben Sie den Saldobetrag ein.|  
|RequiredLevel|Keiner|  
|PrecisionSource|2 <br />**Hinweis:** Informationen zu den gültigen Werten für PrecisionSource finden Sie unter [MoneyType](../entity-attribute-metadata.md#money_type). Der Wert „2” bedeutet, dass die Ebene der Dezimalgenauigkeit TransactionCurrency.CurrencyPrecision entspricht, der dem aktuellen Datensatz zugeordnet ist.|  


  
Das folgende Bespiel erstellt ein money-Attribut mithilfe der Eigenschaften und fügt sie der Entität mit dem MetadataId-Wert 402fa40f-287c-e511-80d2-00155d2a68d2 hinzu. Der URI für das Attribut wird in der Antwort zurückgegeben.  
  
 **Anforderung**  
```http   
POST [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "AttributeType": "Money",  
 "AttributeTypeName": {  
  "Value": "MoneyType"  
 },  
 "Description": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Enter the balance amount",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Balance",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "RequiredLevel": {  
  "Value": "None",  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
 },  
 "SchemaName": "new_Balance",  
 "@odata.type": "Microsoft.Dynamics.CRM.MoneyAttributeMetadata",  
 "PrecisionSource": 2  
}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(f11bef16-287c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_createDateTime"></a>

### <a name="create-a-datetime-attribute"></a>Erstellen eines datetime-Attributs

Das folgende Beispiel verwendet diese Eigenschaften, um ein datetime-Attribut zu erstellen.  
  
|Datetime-Attributeigenschaften|Werte|  
|-----------------------------------|------------|  
|SchemaName|new_Checkeddate|  
|DisplayName|Datum|  
|Beschreibung|Das Datum, an dem der Kontosaldo zuletzt bestätigt wurde.|  
|RequiredLevel|Keiner|  
|Format|DateOnly **Hinweis:** Die gültigen Optionen für diese Eigenschaft finden Sie unter <xref href="Microsoft.Dynamics.CRM.DateTimeFormat?text=DateTimeFormat EnumType" />.|  
  
Das folgende Bespiel erstellt ein datetime-Attribut mithilfe der Eigenschaften und fügt sie der Entität mit dem MetadataId-Wert 402fa40f-287c-e511-80d2-00155d2a68d2 hinzu. Der URI für das Attribut wird in der Antwort zurückgegeben.  
  
 **Anforderung**

```http 
POST [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "AttributeType": "DateTime",  
 "AttributeTypeName": {  
  "Value": "DateTimeType"  
 },  
 "Description": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "The date the account balance was last confirmed",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "DisplayName": {  
  "@odata.type": "Microsoft.Dynamics.CRM.Label",  
  "LocalizedLabels": [  
   {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Date",  
    "LanguageCode": 1033  
   }  
  ]  
 },  
 "RequiredLevel": {  
  "Value": "None",  
  "CanBeChanged": true,  
  "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
 },  
 "SchemaName": "new_Checkeddate",  
 "@odata.type": "Microsoft.Dynamics.CRM.DateTimeAttributeMetadata",  
 "Format": "DateOnly"  
}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/EntityDefinitions(402fa40f-287c-e511-80d2-00155d2a68d2)/Attributes(fe1bef16-287c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_CreateCustomerLookup"></a>

### <a name="create-a-customer-lookup-attribute"></a>Erstellen eines Kundesuchattributs

Anders als andere Attribute wird ein Kundensuchattribut erstellt mithilfe von <xref href="Microsoft.Dynamics.CRM.CreateCustomerRelationships?text=CreateCustomerRelationships Action" />. 

Die Parameter für diese Aktion erfordern die Definition des Suchattributs und ein Paar 1: n-Beziehungen. Ein Kundensuchattribut hat zwei 1:n-Beziehungen: eine für die Firmenentität und das andere für die Kontaktentität.  
  
 Das folgende Beispiel verwendet diese Eigenschaften, um ein Kundensuchattribut zu erstellen.  
  
|Kundesuchattributeigenschaften|Werte|  
|------------------------------------------|------------|  
|SchemaName|new_CustomerId|  
|DisplayName|Kundin/Kunde|  
|Beschreibung|Beispiel-Kundesuchattribut|  
  
Das Beispiel erstellt ein Kundensuchattribut, `new_CustomerId`, und fügt es der benutzerdefinierten Entität hinzu: `new_bankaccount`. Der Response-Typ ist ein <xref href="Microsoft.Dynamics.CRM.CreateCustomerRelationshipsResponse?text=CreateCustomerRelationshipsResponse ComplexType" />.  
  
 **Anforderung**

```http 
POST [Organization URI]/api/data/v9.0/CreateCustomerRelationships HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
  
{  
    "OneToManyRelationships": [{  
        "SchemaName": "new_bankaccount_customer_account",  
        "ReferencedEntity": "account",  
        "ReferencingEntity": "new_bankaccount"  
    }, {  
        "SchemaName": "new_bankaccount_customer_contact",  
        "ReferencedEntity": "contact",  
        "ReferencingEntity": "new_bankaccount"  
    }],  
    "Lookup": {  
        "AttributeType": "Lookup",  
        "AttributeTypeName": {  
            "Value": "LookupType"  
        },  
        "Description": {  
            "@odata.type": "Microsoft.Dynamics.CRM.Label",  
            "LocalizedLabels": [{  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Sample Customer Lookup Attribute",  
                "LanguageCode": 1033  
            }],  
            "UserLocalizedLabel": {  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Sample Customer Lookup Attribute",  
                "LanguageCode": 1033  
            }  
        },  
        "DisplayName": {  
            "@odata.type": "Microsoft.Dynamics.CRM.Label",  
            "LocalizedLabels": [{  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Customer",  
                "LanguageCode": 1033  
            }],  
            "UserLocalizedLabel": {  
                "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
                "Label": "Customer",  
                "LanguageCode": 1033  
            }  
        },  
        "SchemaName": "new_CustomerId",  
        "@odata.type": "Microsoft.Dynamics.CRM.ComplexLookupAttributeMetadata"  
    }  
}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.CreateCustomerRelationshipsResponse",  
    "RelationshipIds": [  
        "a7d261bc-3580-e611-80d7-00155d2a68de", "aed261bc-3580-e611-80d7-00155d2a68de"  
    ],  
    "AttributeId": "39a5d94c-e8a2-4a41-acc0-8487242d455e"  
}  
  
```  
  
<a name="bkmk_updateAttribute"></a>
 
## <a name="update-an-attribute"></a>Aktualisieren eines Attributs

Wie in [Aktualisieren von Entitäten](create-update-entity-definitions-using-web-api.md#bkmk_updateEntities) beschrieben, werden Modellentitäten mithilfe der HTTP PUT-Methode mit der gesamten JSON-Definition des aktuellen Elements aktualisiert. Dies gilt für Attribute und für Entitäten. Wie bei Entitäten haben Sie die Möglichkeit zum Überschreiben von Beschriftungen mithilfe der `MSCRM.MergeLabels`-Kopfzeile mit dem auf `false` festgelegten Wert, und Sie müssen Ihre Anpassungen veröffentlichen, bevor sie im System aktiv sind.  
  
### <a name="see-also"></a>Siehe auch

[Nutzen der Web-API mit Common Data Service-Metadaten](use-web-api-metadata.md)<br />
[Metadatenabfrage mit Web-API](query-metadata-web-api.md)<br />
[Abrufen von Metadaten über den Namen oder die MetadataId](retrieve-metadata-name-metadataid.md)<br />
[Entitätsbeziehungen modellieren mit Web-API](create-update-entity-relationships-using-web-api.md)<br />

[Arbeiten mit Metadaten mithilfe des Organisationsdiensts](../org-service/work-with-metadata.md)<br />
[Attribut-Metadaten](../entity-attribute-metadata.md)

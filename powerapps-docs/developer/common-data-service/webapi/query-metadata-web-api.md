---
title: Abfragen von Metadaten mit der Web-API (Common Data Service) | Microsoft Docs
description: 'Die Funktion, Systemmetadaten abzufragen, ist mit der Web-API und dem Organisationsservice verfügbar, indem RetrieveMetadataChangesRequest verwendet wird.'
ms.custom: ''
ms.date: 11/04/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3ad4a332-a304-421f-a9fa-82ea3e0503fe
caps.latest.revision: 18
author: brandonsimons
ms.author: jdaly
ms.reviewer: susikka
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="query-metadata-using-the-web-api"></a>Metadaten mit Web-API abfragen

Da Common Data Service eine metadatengesteuerte Anwendung ist, müssen Entwickler unter Umständen die Systemmetadaten zur Laufzeit abfragen, um die Konfiguration der Organisation anzupassen. Dieses Feature verwendet einen RESTful-Abfragenstil.

> [!NOTE]
> Sie können auch eine Abfrage mithilfe eines objektbasierten Stils unter Verwendung des <xref href="Microsoft.Dynamics.CRM.EntityQueryExpression?text=EntityQueryExpression ComplexType" /> mit der <xref href="Microsoft.Dynamics.CRM.RetrieveMetadataChanges?text=RetrieveMetadataChanges Function" /> erstellen. Diese Funktion ermöglicht die Ablaufverfolgung von Änderungen an den Metadaten zwischen zwei Zeiträumen sowie das Zurückgeben einer begrenzten Anzahl für Metadaten, die von einer Abfrage definiert werden, die Sie angeben.

<a name="bkmk_QueryingEntityMetadata"></a>

## <a name="querying-the-entitymetadata-entity-type"></a>Abfragen des EntityMetadata-Entitätstyps

Sie verwenden die gleichen Techniken wie beschrieben in [Datenabfrage mit Web-API](query-data-web-api.md), wenn Sie EntityMetadata abfragen, mit wenigen Variationen. Über den festgelegten Pfad der `EntityDefinitions`-Entität können Sie Informationen zu <xref href="Microsoft.Dynamics.CRM.EntityMetadata?text=EntityMetadata EntityType" /> abrufen. EntityMetadata-Entitäten enthalten viele Daten, sodass Sie sicher darauf achten möchten, dass Sie nur die Daten abrufen, die Sie benötigen. Im folgenden Beispiel werden die Daten angezeigt, die nur für die DisplayName, IsKnowledgeManagementEnabled und EntitySetName-Eigenschaften der Metadaten für die `Account`-Entität zurückgegeben werden. Der `MetadataId`-Eigenschaftswert wird immer zurückgegeben.  
  
 **Anforderung**

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')?$select=DisplayName,IsKnowledgeManagementEnabled,EntitySetName HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```

 **Antwort**
```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  

{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(DisplayName,IsKnowledgeManagementEnabled,EntitySetName)",  
 "value": [  
  {  
   "DisplayName": {  
    "LocalizedLabels": [  
     {  
      "Label": "Account",  
      "LanguageCode": 1033,  
      "IsManaged": true,  
      "MetadataId": "2a4901bf-2241-db11-898a-0007e9e17ebd",  
      "HasChanged": null  
     }  
    ],  
    "UserLocalizedLabel": {  
     "Label": "Account",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "2a4901bf-2241-db11-898a-0007e9e17ebd",  
     "HasChanged": null  
    }  
   },  
   "IsKnowledgeManagementEnabled": false,  
   "EntitySetName": "accounts",  
   "MetadataId": "70816501-edb9-4740-a16c-6a5efbc05d84"  
  }  
 ]  
}  
  
```

Sie können jede der `EntityMetadata`-Eigenschaften mit den `$select`-Systemabfrageoptionen verwenden und Sie können `$filter` für alle Eigenschaften verwenden, die einfache oder Enumerationswerte verwenden.  

Es gibt keine Beschränkungen zur Anzahl der Metadatenentitäten, die in einer Abfrage zurückgegeben werden. Es gibt kein Auslagern. Alle entsprechenden Ressourcen werden mit der ersten Antwort zurückgegeben.  

<a name="bkmk_filterEnumTypes"></a>

## <a name="use-enum-types-in-filter-operations"></a>Verwendung von Enumerationstypen in $filter-Vorgängen

Wenn Sie Metadatenentitäten auf Grundlage des Werts einer Eigenschaft filtern müssen, die eine Enumeration verwendet, muss zudem der Namespace der Enumeration vor dem Zeichenfolgenwert enthalten sein. Enumerationstypen werden als Eigenschaftswerte nur in den Metadatenentitäten und komplexen Arten verwendet. Wenn Sie z. B. Entitäten filtern müssen basierend auf der `OwnershipType`-Eigenschaft, die <xref href="Microsoft.Dynamics.CRM.OwnershipTypes?text=OwnershipTypes EnumType" /> verwendet, können Sie folgende `$filter` verwenden, um nur die Entitäten zurückzugeben, die UserOwned sind.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions?$select=LogicalName&$filter=OwnershipType eq Microsoft.Dynamics.CRM.OwnershipTypes'UserOwned'  
```

<a name="bkmk_complexTypesAsFilters"></a>

## <a name="use-complex-types-in-filter-operations"></a>Verwendung von komplexen Typen in $filter-Vorgängen

Wenn Sie Metadatenentitäten auf Grundlage des Werts einer Eigenschaft filtern müssen, die einen komplexen Typen verwendet, muss zudem der Pfad zum zugrundeliegenden einfachen Typen enthalten sein. Komplexe Typen werden als Eigenschaftswerte nur in den Metadatenentitäten verwendet. Wenn Sie z. B. Entitäten filtern müssen auf Basis der CanCreateAttributes-Eigenschaft, die <xref href="Microsoft.Dynamics.CRM.BooleanManagedProperty?text=BooleanManagedProperty ComplexType" /> verwendet,. können Sie folgende `$filter` verwenden, die einen `Value` von `true` aufweisen.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions?$select=LogicalName&$filter=CanCreateAttributes/Value eq true  
```

Dieses Muster verwendet <xref href="Microsoft.Dynamics.CRM.BooleanManagedProperty?text=BooleanManagedProperty ComplexType" />, da der einfache zu prüfende Wert eine Ebene tief ist. Allerdings funktioniert dies nicht für Eigenschaften von <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" />.  

<a name="bkmk_queryAttributes"></a>

## <a name="querying-entitymetadata-attributes"></a>Abfragen von EntityMetadata-Attributen

Entitätsattribute können Sie im Rahmen einer Entität abfragen, indem Sie die sammlungswertige `Attributes`-Navigationseigenschaft erweitern. Dies enthält jedoch nur die allgemeinen Eigenschaften, die in <xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" /> verfügbar sind, das alle Attribute gemeinsam haben. So gibt die folgende Abfrage den `LogicalName` der Entität zurück, und alle erweiterten Attribute, die einen `AttributeType`-Wert besitzen, der dem <xref href="Microsoft.Dynamics.CRM.AttributeTypeCode?text=AttributeTypeCode EnumType" />-Wert von `Picklist` entspricht.

<a name="bkmk_queryAttributesexample"></a>

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')?$select=LogicalName&$expand=Attributes($select=LogicalName;$filter=AttributeType eq Microsoft.Dynamics.CRM.AttributeTypeCode'Picklist')  
```

Sie können jedoch nicht die sammlungswertigen `OptionSet`- oder `GlobalOptionSet`-Navigationseigenschaften einschließen, die <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" />-Attribute im `$select`-Filter dieser Abfrage enthalten.  

Um die Eigenschaften eines bestimmten Typs eines Attributs abzurufen, müssen Sie die sammlungswertige `Attributes`-Navigationseigenschaft in den gewünschten Typ umwandeln. Die folgende Abfrage gibt nur die <xref href="Microsoft.Dynamics.CRM.PicklistAttributeMetadata?text=PicklistAttributeMetadata EntityType" />-Attribute zurück und enthält den `LogicalName` und erweitert die sammlungswertigen `OptionSet`- und `GlobalOptionSet`-Navigationseigenschaften  

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet,GlobalOptionSet  
```

> [!NOTE]
> Obwohl die sammlungswertigen `OptionSet`- und `GlobalOptionSet`-Navigationseigenschaften in <xref href="Microsoft.Dynamics.CRM.EnumAttributeMetadata?text=EnumAttributeMetadata EntityType" /> definiert werden, können Sie die Attribute nicht in diesen Typ umwandeln. Das bedeutet, dass wenn Sie nach anderen Typen filtern möchten, die ebenfalls diese Eigenschaften erben (siehe [Entitätstypen, die von EnumAttributeMetadata erben](/dynamics365/customer-engagement/web-api/enumattributemetadata?view=dynamics-ce-odata-9#Derived_Types)), müssen Sie separate Abfragen zum Filtern für jeden Typ ausführen.

Ein anderes Beispiel hierfür ist der Zugriff auf die `Precision`-Eigenschaft, die in <xref href="Microsoft.Dynamics.CRM.MoneyAttributeMetadata?text=MoneyAttributeMetadata EntityType" />- und <xref href="Microsoft.Dynamics.CRM.DecimalAttributeMetadata?text=DecimalAttributeMetadata EntityType" />-Attributen verfügbar ist. Damit Sie auf diese Eigenschaft zugreifen können, müssen Sie die Attributsammlung entweder als <xref href="Microsoft.Dynamics.CRM.MoneyAttributeMetadata?text=MoneyAttributeMetadata EntityType" /> oder als <xref href="Microsoft.Dynamics.CRM.DecimalAttributeMetadata?text=DecimalAttributeMetadata EntityType" /> umwandeln. Ein Beispiel, das das Umwandeln zu `MoneyAttributeMetadata` veranschaulicht, wird hier angezeigt.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes/Microsoft.Dynamics.CRM.MoneyAttributeMetadata?$select=LogicalName,Precision
```

### <a name="filtering-by-required-level"></a>Filtern nach erforderlicher Ebene

Die <xref href="Microsoft.Dynamics.CRM.AttributeMetadata?text=AttributeMetadata EntityType" /> `RequiredLevel`-Eigenschaft verwendet einen speziellen <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevelManagedProperty?text=AttributeRequiredLevelManagedProperty ComplexType" />, wobei die `Value`-Eigenschaft ein <xref href="Microsoft.Dynamics.CRM.AttributeRequiredLevel?text=AttributeRequiredLevel EnumType" /> ist. In diesem Fall müssen die Muster kombinieren, die in [Verwenden komplexer Typen in $filter operations](query-metadata-web-api.md#bkmk_complexTypesAsFilters) und [Enumerationstypen in $filter-Operationen verwenden](query-metadata-web-api.md#bkmk_filterEnumTypes), um diese spezielle Eigenschaft zu verwenden. In der folgenden Abfrage werden solche Attribute in der Firmenentität gefiltert, die ApplicationRequired sind.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes?$select=SchemaName&$filter=RequiredLevel/Value eq Microsoft.Dynamics.CRM.AttributeRequiredLevel'ApplicationRequired'  
```

<a name="bkmk_retrieveAttributes"></a>

## <a name="retrieving-attributes"></a>Abrufen von Attributen

Wenn Sie die MetadataId für EntityMetadata und AttributeMetadata kennen, können Sie ein einzelnes Attribut abrufen und auf die Eigenschaftswerte zugreifen, indem Sie eine Abfrage wie die folgende verwenden. Diese Abfrage ruft die LogicalName-Eigenschaft des Attributs ab und erweitert die sammlungswertige OptionSet-Navigationseigenschaft. Beachten Sie, dass Sie das Attribut als Microsoft.Dynamics.CRM.PicklistAttributeMetadata umwandeln müssen, um auf die sammlungswertige OptionSet-Navigationseigenschaft zuzugreifen.  

 **Anforderung**
 ```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata?$select=LogicalName&$expand=OptionSet HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```

 **Antwort**
 ```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes/Microsoft.Dynamics.CRM.PicklistAttributeMetadata(LogicalName,OptionSet)/$entity",  
 "LogicalName": "preferredappointmentdaycode",  
 "MetadataId": "5967e7cc-afbb-4c10-bf7e-e7ef430c52be",  
 "OptionSet@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions(70816501-edb9-4740-a16c-6a5efbc05d84)/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet/$entity",  
 "OptionSet": {  
  "Options": [  
   {  
    "Value": 0,  
    "Label": {  
     "LocalizedLabels": [  
      {  
       "Label": "Sunday",  
       "LanguageCode": 1033,  
       "IsManaged": true,  
       "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
       "HasChanged": null  
      }  
     ],  
     "UserLocalizedLabel": {  
      "Label": "Sunday",  
      "LanguageCode": 1033,  
      "IsManaged": true,  
      "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
      "HasChanged": null  
     }  
    },  
    "Description": {  
     "LocalizedLabels": [],  
     "UserLocalizedLabel": null  
    },  
    "Color": null,  
    "IsManaged": true,  
    "MetadataId": null,  
    "HasChanged": null  
   }  
Additional options removed for brevity  
  ],  
  "Description": {  
   "LocalizedLabels": [  
    {  
     "Label": "Day of the week that the account prefers for scheduling service activities.",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "1b67144d-ece0-4e83-a38b-b4d48e3f35d5",  
     "HasChanged": null  
    }  
   ],  
   "UserLocalizedLabel": {  
    "Label": "Day of the week that the account prefers for scheduling service activities.",  
    "LanguageCode": 1033,  
    "IsManaged": true,  
    "MetadataId": "1b67144d-ece0-4e83-a38b-b4d48e3f35d5",  
    "HasChanged": null  
   }  
  },  
  "DisplayName": {  
   "LocalizedLabels": [  
    {  
     "Label": "Preferred Day",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "ebb7e979-f9e3-40cd-a86d-50b479b1c5a4",  
     "HasChanged": null  
    }  
   ],  
   "UserLocalizedLabel": {  
    "Label": "Preferred Day",  
    "LanguageCode": 1033,  
    "IsManaged": true,  
    "MetadataId": "ebb7e979-f9e3-40cd-a86d-50b479b1c5a4",  
    "HasChanged": null  
   }  
  },  
  "IsCustomOptionSet": false,  
  "IsGlobal": false,  
  "IsManaged": true,  
  "IsCustomizable": {  
   "Value": true,  
   "CanBeChanged": false,  
   "ManagedPropertyLogicalName": "iscustomizable"  
  },  
  "Name": "account_preferredappointmentdaycode",  
  "OptionSetType": "Picklist",  
  "IntroducedVersion": null,  
  "MetadataId": "53f9933c-18a0-40a6-b4a5-b9610a101735",  
  "HasChanged": null  
 }  
}  
```

Sofern Sie keine Eigenschaften des Attributs benötigen und nur die Werte einer sammlungswertigen Navigationseigenschaft wie OptionsSet benötigen, können Sie diese in die URL einschließen und die Eigenschaften mit einer `$select`-Systemabfrageoption für eine etwas effizientere Abfrage beschränken. Im folgenden Beispiel wird nur die Options-Eigenschaft von OptionSet einbezogen.  

 **Anforderung**
 ```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet?$select=Options HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```

 **Antwort**
 ```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  

{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#EntityDefinitions('account')/Attributes(5967e7cc-afbb-4c10-bf7e-e7ef430c52be)/Microsoft.Dynamics.CRM.PicklistAttributeMetadata/OptionSet(Options)/$entity",  
 "Options": [{  
   "Value": 0,  
   "Label": {  
    "LocalizedLabels": [{  
     "Label": "Sunday",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
     "HasChanged": null  
    }],  
    "UserLocalizedLabel": {  
     "Label": "Sunday",  
     "LanguageCode": 1033,  
     "IsManaged": true,  
     "MetadataId": "21d6a218-2341-db11-898a-0007e9e17ebd",  
     "HasChanged": null  
    }  
   },  
   "Description": {  
    "LocalizedLabels": [],  
    "UserLocalizedLabel": null  
   },  
   "Color": null,  
   "IsManaged": true,  
   "MetadataId": null,  
   "HasChanged": null  
  }  
Additional options removed for brevity  
 ],  
 "MetadataId": "53f9933c-18a0-40a6-b4a5-b9610a101735"  
}  
```

<a name="bkmk_queryRelationshipMetadata"></a>

## <a name="querying-relationship-metadata"></a>Abfragen von Beziehungsmetadaten

Sie können Beziehungsmetadaten im Kontext einer bestimmten Entität ganz ähnlich abrufen wie Sie Attribute abfragen können. Die sammlungswertigen `ManyToManyRelationships`-, `ManyToOneRelationships`- und `OneToManyRelationships`-Navigationseigenschaften können genauso abgefragt werden wie die sammlungswertige `Attributes`-Navigationseigenschaft. Weitere Informationen: [Abfragen von EntityMetadata-Attributen](query-metadata-web-api.md#bkmk_queryAttributes)  

Entitätsbeziehungen können jedoch auch mit dem `RelationshipDefinitions`-Entitätssatz abgefragt werden. Sie können eine Abfrage wie die folgende verwenden, um die `SchemaName`-Eigenschaft für jede Beziehung abzurufen.

```http
GET [Organization URI]/api/data/v9.0/RelationshipDefinitions?$select=SchemaName  
```

Die Eigenschaften, die verfügbar sind, wenn dieser Entitätssatz abgefragt wird, werden auf die im <xref href="Microsoft.Dynamics.CRM.RelationshipMetadataBase?text=RelationshipMetadataBase EntityType" /> beschränkt. Um auf Eigenschaften von Entitätstypen zuzugreifen, die von `RelationshipMetadataBase` erben, müssen Sie eine Umwandlung in der Abfrage einschließen wie die folgende, um nur <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> zurückzugeben.  

```http
GET [Organization URI]/api/data/v9.0/RelationshipDefinitions/Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?$select=SchemaName  
```

Da die zurückgegebenen Entitäten als `OneToManyRelationshipMetadata` eingegeben werden, können Sie nach den Eigenschaften wie `ReferencedEntity` filtern, um eine Abfrage zu erstellen, die nur 1: n-Entitätsbeziehungen für eine bestimmte Entität zurückgibt, wie die Firmenentität, siehe folgende Abfrage:  

```http
GET [Organization URI]/api/data/v9.0/RelationshipDefinitions/Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?$select=SchemaName&$filter=ReferencedEntity eq 'account' 
```

Diese Abfrage gibt im Wesentlichen die gleichen Ergebnisse wie die folgende Abfrage zurück, die gefiltert wird, da sie in der sammlungswertigen `EntityMetadataOneToManyRelationships`-Navigationseigenschaft der Firmenentität enthalten ist. Der Unterschied ist, dass Sie für die vorherige Abfrage nicht die `MetadataId` für die Firmenentität kennen müssen.  

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='account')/OneToManyRelationships?$select=SchemaName  
```

<a name="bkmk_GlobalOptionSets"></a>

## <a name="querying-global-optionsets"></a>Abfragen von globalen OptionSets

Sie können den festgelegten `GlobalOptionSetDefinitions`-Entitätspfad verwenden, um Informationen zu globalen Optionssätzen abzurufen, aber der Pfad unterstützt nicht die Verwendung der `$filter`-Systemabfrageoption. Sofern Sie also nicht die `MetadataId` für einen bestimmten globalen Optionssatz kennen, können Sie nur alle von ihnen abrufen. Sie können auch auf die Definition eines globalen Optionssatzes in der einzelwertigen `GlobalOptionSet`-Navigationseigenschaft für jedes Attribut, das diese verwendet, zugreifen. Dies ist verfügbar für alle [Abgeleitete Typen EnumAttributeMetadata EntityType](/dynamics365/customer-engagement/web-api/enumattributemetadata?view=dynamics-ce-odata-9#Derived_Types). Weitere Informationen [Abrufen von Attributen](query-metadata-web-api.md#bkmk_retrieveAttributes)  

### <a name="see-also"></a>Siehe auch

[Nutzen der Web-API mit Common Data Service-Metadaten](use-web-api-metadata.md)<br />
[Abrufen von Metadaten über den Namen oder die MetadataId](retrieve-metadata-name-metadataid.md)<br />
[Metadaten-Entitäten und Attribute unter Verwendung der Web-API](create-update-entity-definitions-using-web-api.md)<br />
[Metadaten-Entitätsbeziehungen modellieren mit Internet-API](create-update-entity-relationships-using-web-api.md)

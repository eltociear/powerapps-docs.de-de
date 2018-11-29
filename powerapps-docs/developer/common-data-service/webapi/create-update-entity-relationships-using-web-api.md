---
title: Erstellen und Aktualisieren Sie Entitätsbeziehungen mithilfe von Web-API (Common Data Service for Apps) | Microsoft Docs
description: 'Informationen zum Erstellen und Aktualisieren einer Common Data Service for Apps verwendet eine metadatengetriebene Architektur, um die Flexibilität zu bieten, benutzerdefinierte Entitäten und zusätzliche Systementitätsattribute zu erstellen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 923538e2-15fe-4718-8eae-d939c5d200cd
caps.latest.revision: 15
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-update-entity-relationships-using-the-web-api"></a>Erstellen und Aktualisieren von Entitätsbeziehungen mit der Web-API


Die Web-API unterstützt die Arbeit mit Beziehungsmetadaten. Die Konzepte, die in [Entitätsbeziehungs-Metadaten](../entity-relationship-metadata.md) beschriebenen werden, gelten auch für die Web-API.  

<a name="bkmk_RelationshipEligibility"></a>

## <a name="eligibility-for-relationships"></a>Eignung für Beziehungen


Bevor Sie eine Entitätsbeziehung erstellen, müssen Sie bestätigen, ob die Entität geeignet ist, um an der Beziehung teilzunehmen. Sie können die Aktionen verwenden, die in der folgenden Tabelle aufgeführt sind, um die Eignung zu bestimmen. Diese Aktionen entsprechen den Organisationsservicemeldungen, die unter [Entitätsbeziehungseignung](../entity-relationship-eligibility.md) beschrieben werden.  


  
|Aktion|Beschreibung|  
|------------|-----------------|  
|<xref href="Microsoft.Dynamics.CRM.CanBeReferenced?text=CanBeReferenced Action" />|Überprüft, ob die angegebene Entität als primäre Entität (eins) in einer 1:n-Beziehung verwendet werden kann.|  
|<xref href="Microsoft.Dynamics.CRM.CanBeReferencing?text=CanBeReferencing Action" />|Überprüft, ob die angegebene Entität als verweisende Entität (viele) in einer 1:n-Beziehung verwendet werden kann.|  
|<xref href="Microsoft.Dynamics.CRM.CanManyToMany?text=CanManyToMany Action" />|Überprüft, ob die Entität an einer n:n-Beziehung teilnehmen kann.|  
|<xref href="Microsoft.Dynamics.CRM.GetValidManyToMany?text=GetValidManyToMany Function" />|Gibt den Satz von Entitäten zurück, die an einer n:n-Beziehung teilnehmen können.|  
|<xref href="Microsoft.Dynamics.CRM.GetValidReferencedEntities?text=GetValidReferencedEntities Function" />|Gibt den Satz von Entitäten zurück, der als die primäre Entität (eins) von der angegebenen Entität in einer 1: n-Beziehung gültig ist.|  
|<xref href="Microsoft.Dynamics.CRM.GetValidReferencingEntities?text=GetValidReferencingEntities Function" />|Gibt den Satz von Entitäten zurück, der als die verknüpfte Entität (viele) mit der angegebenen Entität in einer 1:n-Beziehung gültig ist.|  
  
<a name="bkmk_createOnetoMany"></a>

## <a name="create-a-one-to-many-relationship"></a>Erstellen einer 1:n-Beziehung

Wenn Sie eine 1:n-Beziehung erstellen, definieren Sie sie, indem Sie den <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> verwenden. Die Definition umfasst das Suchattribut, da mit dem <xref href="Microsoft.Dynamics.CRM.LookupAttributeMetadata?text=LookupAttributeMetadata EntityType" /> definiert wird, und erfordert auch komplexe Eigenschaften unter Verwendung von <xref href="Microsoft.Dynamics.CRM.AssociatedMenuConfiguration?text=AssociatedMenuConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.CascadeConfiguration?text=CascadeConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> und <xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" />. Das Suchattribut wird auf die einzelwertige Navigationseigenschaft des `OneToManyRelationshipMetadata`-Objekts festgelegt und wird gleichzeitig mit der *tiefen Einfügung* erstellt. Weitere Informationen: [Erstellen von verknüpften Entitäten in einem Vorgang](create-entity-web-api.md#bkmk_CreateRelated) und [Entitätsbeziehungsmetadaten](../entity-relationship-metadata.md)
  
Wenn Sie einen benutzerdefinierten Navigationseigenschaftennamen für eine 1:n-Beziehung anwenden, können Sie Werte für die Eigenschaften `ReferencingEntityNavigationPropertyName` und `ReferencedEntityNavigationPropertyName` festlegen.  
  
Nachdem Sie das erforderliche JSON generiert haben, um die Beziehung und das Suchattribut zu definieren, wird `POST` das JSON an den RelationshipDefinitions-Entitätssatz. Sie müssen den `@odata.type`-Eigenschaftswert von Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata aufnehmen, um den Typ der Beziehung zu verdeutlichen, den Sie erstellen, da der gleiche Entitätssatz verwendet wird, um n:n-Beziehungen zu erstellen. Der URI für die resultierende Beziehung wird in der Antwort zurückgegeben.  
  
 **Anforderung**  
```http 
POST [Organization URI]/api/data/v9.0/RelationshipDefinitions HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "SchemaName": "new_contact_new_bankaccount",  
 "@odata.type": "Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata",  
 "AssociatedMenuConfiguration": {  
  "Behavior": "UseCollectionName",  
  "Group": "Details",  
  "Label": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Bank Accounts",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Bank Accounts",  
    "LanguageCode": 1033  
   }  
  },  
  "Order": 10000  
 },  
 "CascadeConfiguration": {  
  "Assign": "Cascade",  
  "Delete": "Cascade",  
  "Merge": "Cascade",  
  "Reparent": "Cascade",  
  "Share": "Cascade",  
  "Unshare": "Cascade"  
 },  
 "ReferencedAttribute": "contactid",  
 "ReferencedEntity": "contact",  
 "ReferencingEntity": "new_bankaccount",  
 "Lookup": {  
  "AttributeType": "Lookup",  
  "AttributeTypeName": {  
   "Value": "LookupType"  
  },  
  "Description": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "The owner of the account",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "The owner of the account",  
    "LanguageCode": 1033  
   }  
  },  
  "DisplayName": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Account Owner",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Account Owner",  
    "LanguageCode": 1033  
   }  
  },  
  "RequiredLevel": {  
   "Value": "ApplicationRequired",  
   "CanBeChanged": true,  
   "ManagedPropertyLogicalName": "canmodifyrequirementlevelsettings"  
  },  
  "SchemaName": "new_AccountOwner",  
  "@odata.type": "Microsoft.Dynamics.CRM.LookupAttributeMetadata"  
 }  
}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/RelationshipDefinitions(d475020f-5d7c-e511-80d2-00155d2a68d2)  
```  
  
<a name="bkmk_CreateManyToMany"></a>
  
## <a name="create-a-many-to-many-relationship"></a>Erstellen einer n:n-Beziehung

<!-- TODO:
When you create a many-to-many relationship, you must the relationship by using the <xref href="Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata?text=ManyToManyRelationshipMetadata EntityType" />. This definition includes the name of the intersect entity to be created as well as how the relationship should be displayed in the application by using <xref href="Microsoft.Dynamics.CRM.AssociatedMenuConfiguration?text=AssociatedMenuConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> and <xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" />. More information:[Many-to-many relationships](../customize-entity-relationship-metadata.md#BKMK_ManyToManyRelationships)   -->
  
 Wenn Sie einen benutzerdefinierten Navigationseigenschaftennamen für eine n:n-Beziehung anwenden, können Sie Werte für die Eigenschaften `Entity1NavigationPropertyName` und `Entity2NavigationPropertyName` festlegen.  
  
 Nachdem Sie das erforderliche JSON generiert haben, um die Beziehung zu definieren, `POST` das JSON an den RelationshipDefinitions-Entitätssatz. Sie müssen den `@odata.type`-Eigenschaftswert von Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata aufnehmen, um den Typ der Beziehung zu verdeutlichen, den Sie erstellen, da der gleiche Entitätssatz verwendet wird, um 1:n-Beziehungen zu erstellen. Der URI für die resultierende Beziehung wird in der Antwort zurückgegeben.  
  
 **Anforderung**
  
```http 
POST [Organization URI]/api/data/v9.0/RelationshipDefinitions HTTP/1.1  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
 "SchemaName": "new_accounts_campaigns",  
 "@odata.type": "Microsoft.Dynamics.CRM.ManyToManyRelationshipMetadata",  
 "Entity1AssociatedMenuConfiguration": {  
  "Behavior": "UseLabel",  
  "Group": "Details",  
  "Label": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Account",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Account",  
    "LanguageCode": 1033  
   }  
  },  
  "Order": 10000  
 },  
 "Entity1LogicalName": "account",  
 "Entity2AssociatedMenuConfiguration": {  
  "Behavior": "UseLabel",  
  "Group": "Details",  
  "Label": {  
   "@odata.type": "Microsoft.Dynamics.CRM.Label",  
   "LocalizedLabels": [  
    {  
     "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
     "Label": "Campaign",  
     "LanguageCode": 1033  
    }  
   ],  
   "UserLocalizedLabel": {  
    "@odata.type": "Microsoft.Dynamics.CRM.LocalizedLabel",  
    "Label": "Campaign",  
    "LanguageCode": 1033  
   }  
  },  
  "Order": 10000  
 },  
 "Entity2LogicalName": "campaign",  
 "IntersectEntityName": "new_accounts_campaigns"  
}  
```  
  
 **Antwort**  
```http 
HTTP/1.1 204 No Content  
OData-Version: 4.0  
OData-EntityId: [Organization URI]/api/data/v9.0/RelationshipDefinitions(420245fa-c77c-e511-80d2-00155d2a68d2)    
```  
  
<a name="bkmk_updateRelationships"></a>

## <a name="update-relationships"></a>Aktualisieren von Beziehungen

Wie in [Aktualisieren von Entitäten](create-update-entity-definitions-using-web-api.md#bkmk_updateEntities) erläutert, aktualisieren Sie Beziehungen mit der HTTP PUT-Methode, um die vorhandene Definition von Änderungen zu ersetzen, die Sie anwenden möchten. Sie können einzelne Eigenschaften nicht mithilfe der HTTP PATCH-Methode bearbeiten, wie Sie es mit Geschäftsdatenentitäten können. Wie mit Entitäten und Attributen können Sie eine `MSCRM.MergeLabels`-Kopfzeile mit dem auf `true` gesetzten Wertsatz aufnehmen, um das Überschreiben von lokalisierten Beschriftungen zu vermeiden, die in dem Update enthalten sind, und Sie müssen die Anpassungen veröffentlichen, damit sie im System aktiv sind.  
  
<a name="bkmk_deleteRelationship"></a>
 
## <a name="delete-relationships"></a>Beziehungen löschen

Wenn Sie eine Beziehung mit der Web-API löschen möchten, können Sie die HTTP DELETE-Methode mit dem URI für die Beziehung verwenden.  
  
### <a name="see-also"></a>Siehe auch

<!-- TODO:
[Customize entity relationship metadata](../customize-entity-relationship-metadata.md)<br /> -->
[Nutzen der Web-API mit Common Data Service for Apps-Metadaten](use-web-api-metadata.md)<br />
[Metadatenabfrage mit Web-API](query-metadata-web-api.md)<br />
[Abrufen von Metadaten über den Namen oder die MetadataId](retrieve-metadata-name-metadataid.md)<br />
[Entitäten und Attribute modellieren mit Internet-API](create-update-entity-definitions-using-web-api.md)

---
title: Erstellen einer benutzerdefinierten Entität (Common Data Service) | Microsoft-Dokumentation
description: Zeigt, wie Sie programmgesteuert eine benutzerdefinierte Entität Common Data Service erstellen.
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
ms.openlocfilehash: 127317260eb873e3565cfa7de5a24569263b4522
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156082"
---
# <a name="create-custom-entity"></a>Benutzerdefinierte Entität erstellen

In diesem Thema wird erläutert, wie Sie eine benutzerdefinierte Entität mit der Bezeichnung **Bankkonto** programmgesteuert erstellen und dieser vier verschiedene Arten von Attributen hinzufügen.  
  
Sie können auch unternehmenseigene benutzerdefinierte Entitäten erstellen. Weitere Informationen finden Sie unter [Entitätsbesitz](/dynamics365/customer-engagement/developer/introduction-entities#entity-ownership).  
  
> [!NOTE]
>  Sie sehen diese Entität in der Anwendungsnavigation nur, wenn die Entitätseigenschaften so bearbeitet werden, dass ein Wert für **Bereiche, in denen diese Entität angezeigt wird** festgelegt ist.  
  
<a name="BKMK_CreateCustomEntity"></a>   

## <a name="create-a-custom-entity"></a>Erstellen einer benutzerdefinierten Entität.  

 Das folgende Beispiel verwendet <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest> zum Erstellen der Entität und von <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata><xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.PrimaryAttribute>.  
  
 Der `_customEntityName`-Wert ist “new_bankaccount”.  
  
```csharp
CreateEntityRequest createrequest = new CreateEntityRequest
{

 //Define the entity
 Entity = new EntityMetadata
 {
  SchemaName = _customEntityName,
  DisplayName = new Label("Bank Account", 1033),
  DisplayCollectionName = new Label("Bank Accounts", 1033),
  Description = new Label("An entity to store information about customer bank accounts", 1033),
  OwnershipType = OwnershipTypes.UserOwned,
  IsActivity = false,

 },

 // Define the primary attribute for the entity
 PrimaryAttribute = new StringAttributeMetadata
 {
  SchemaName = "new_accountname",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  MaxLength = 100,
  FormatName = StringFormatName.Text,
  DisplayName = new Label("Account Name", 1033),
  Description = new Label("The primary attribute for the Bank Account entity.", 1033)
 }

};
_serviceProxy.Execute(createrequest);
Console.WriteLine("The bank account entity has been created.");
```  
  
<a name="BKMK_AddStringAttribute"></a>   

## <a name="add-a-string-attribute-to-the-custom-entity"></a>Hinzufügen eines Zeichenfolgenattributs zur benutzerdefinierten Entität  

Das folgende Bespiel fügt ein <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata>-Attribut der `Bank Account`-Entität hinzu.  
  
```csharp
CreateAttributeRequest createBankNameAttributeRequest = new CreateAttributeRequest
{
 EntityName = _customEntityName,
 Attribute = new StringAttributeMetadata
 {
  SchemaName = "new_bankname",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  MaxLength = 100,
  FormatName = StringFormatName.Text,
  DisplayName = new Label("Bank Name", 1033),
  Description = new Label("The name of the bank.", 1033)
 }
};

_serviceProxy.Execute(createBankNameAttributeRequest);
```
  
<a name="BKMK_AddMoneyAttribute"></a>   

## <a name="add-a-money-attribute-to-the-custom-entity"></a>Hinzufügen eines Money-Attributs zur benutzerdefinierten Entität  

 Das folgende Bespiel fügt ein <xref:Microsoft.Xrm.Sdk.Metadata.MoneyAttributeMetadata>-Attribut der `Bank Account`-Entität hinzu.  
  
```csharp
CreateAttributeRequest createBalanceAttributeRequest = new CreateAttributeRequest
{
 EntityName = _customEntityName,
 Attribute = new MoneyAttributeMetadata
 {
  SchemaName = "new_balance",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  PrecisionSource = 2,
  DisplayName = new Label("Balance", 1033),
  Description = new Label("Account Balance at the last known date", 1033),

 }
};

_serviceProxy.Execute(createBalanceAttributeRequest);

```  
  
<a name="BKMK_AddDateTimeAttribute"></a>   

## <a name="add-a-datetime-attribute-to-the-custom-entity"></a>Hinzufügen eines Datum/Uhrzeit-Attributs zur benutzerdefinierten Entität  

Das folgende Bespiel fügt ein <xref:Microsoft.Xrm.Sdk.Metadata.DateTimeAttributeMetadata>-Attribut der `Bank Account`-Entität hinzu.  
  
```csharp
CreateAttributeRequest createCheckedDateRequest = new CreateAttributeRequest
{
 EntityName = _customEntityName,
 Attribute = new DateTimeAttributeMetadata
 {
  SchemaName = "new_checkeddate",
  RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
  Format = DateTimeFormat.DateOnly,
  DisplayName = new Label("Date", 1033),
  Description = new Label("The date the account balance was last confirmed", 1033)

 }
};

_serviceProxy.Execute(createCheckedDateRequest);
Console.WriteLine("An date attribute has been added to the bank account entity.");
```
  
<a name="BKMK_AddLookupAttribute"></a>
   
## <a name="add-a-lookup-attribute-to-the-custom-entity"></a>Hinzufügen eines Suche-Attributs zur benutzerdefinierten Entität 
 
 Das folfende Beispiel verwendet <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest> zum Erstellen einer 1:n-Beziehung mit der `Contact`-Entität, so dass ein <xref:Microsoft.Xrm.Sdk.Metadata.LookupAttributeMetadata>-Attribut der `Bank Account`-Entität hinzugefügt wird.  
  
```csharp
CreateOneToManyRequest req = new CreateOneToManyRequest()
{
    Lookup = new LookupAttributeMetadata()
    {
        Description = new Label("The referral (lead) from the bank account owner", 1033),
        DisplayName = new Label("Referral", 1033),
        LogicalName = "new_parent_leadid",
        SchemaName = "New_Parent_leadId",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.Recommended)
    },
    OneToManyRelationship = new OneToManyRelationshipMetadata()
    {
        AssociatedMenuConfiguration = new AssociatedMenuConfiguration()
        {
            Behavior = AssociatedMenuBehavior.UseCollectionName,
            Group = AssociatedMenuGroup.Details,
            Label = new Label("Bank Accounts", 1033),
            Order = 10000
        },
        CascadeConfiguration = new CascadeConfiguration()
        {
            Assign = CascadeType.Cascade,
            Delete = CascadeType.Cascade,
            Merge = CascadeType.Cascade,
            Reparent = CascadeType.Cascade,
            Share = CascadeType.Cascade,
            Unshare = CascadeType.Cascade
        },
        ReferencedEntity = "lead",
        ReferencedAttribute = "leadid",
        ReferencingEntity = _customEntityName,
        SchemaName = "new_lead_new_bankaccount"
    }
};
_serviceProxy.Execute(req);
```
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden Sie den IOrganizationService und Hilfscode](/dynamics365/customer-engagement/developer/use-sample-helper-code)   
 <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>   
 [Anpassen von Entitätsmetadaten](../customize-entity-metadata.md)   
 [Welche Entitäten sind anpassbar?](/dynamics365/customer-engagement/developer/which-entities-are-customizable)   
 [Abrufen, Aktualisieren und Löschen von Entitäten](/dynamics365/customer-engagement/developer/retrieve-update-delete-entities)   
 [Entität, die per E-Mail gesendet werden kann, erstellen und aktualisieren](/dynamics365/customer-engagement/developer/create-update-entity-emailed)   
 [Erstellen einer benutzerdefinierten Aktivitätsentität](/dynamics365/customer-engagement/developer/create-custom-activity-entity)   
 [Ändern von Entitätssymbolen](/dynamics365/customer-engagement/developer/modify-icons-entity)   
 [Ändern von Entitätsmeldungen](/dynamics365/customer-engagement/developer/modify-messages-entity)

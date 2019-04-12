---
title: Erstellen und Abrufen der Entitätsbeziehung (Common Data Service) | Microsoft Docs
description: Zeigt Codebeispiele zum Erstellen und Abrufen von Entitätsbeziehungen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-and-retrieve-entity-relationships"></a>Erstellen und Abrufen von Entitätsbeziehungen

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/create-retrieve-entity-relationships -->

Dieses Thema zeigt, wie Entitätsbeziehungen erstellt und abgerufen werden.  
  
<a name="BKMK_Create1NEntityRelationship"></a>   
## <a name="create-a-1n-entity-relationship"></a>Erstellen einer 1:n-Entitätsbeziehung  
 Im folgenden Beispiel wird die [EligibleCreateOneToManyRelationship](#eligiblecreateonetomanyrelationship) -Methode verwendet, um sicherzustellen, dass die Entitäten `Account` und `Campaign` an einer 1:n-Entitätsbeziehung beteiligt sein können, und anschließend die Entitätsbeziehung erstellt, indem <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest> verwendet wird.  
  
```csharp
bool eligibleCreateOneToManyRelationship =
    EligibleCreateOneToManyRelationship("account", "campaign");

if (eligibleCreateOneToManyRelationship)
{
    CreateOneToManyRequest createOneToManyRelationshipRequest =
        new CreateOneToManyRequest
    {
        OneToManyRelationship =
        new OneToManyRelationshipMetadata
        {
            ReferencedEntity = "account",
            ReferencingEntity = "campaign",
            SchemaName = "new_account_campaign",
            AssociatedMenuConfiguration = new AssociatedMenuConfiguration
            {
                Behavior = AssociatedMenuBehavior.UseLabel,
                Group = AssociatedMenuGroup.Details,
                Label = new Label("Account", 1033),
                Order = 10000
            },
            CascadeConfiguration = new CascadeConfiguration
            {
                Assign = CascadeType.NoCascade,
                Delete = CascadeType.RemoveLink,
                Merge = CascadeType.NoCascade,
                Reparent = CascadeType.NoCascade,
                Share = CascadeType.NoCascade,
                Unshare = CascadeType.NoCascade
            }
        },
        Lookup = new LookupAttributeMetadata
        {
            SchemaName = "new_parent_accountid",
            DisplayName = new Label("Account Lookup", 1033),
            RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
            Description = new Label("Sample Lookup", 1033)
        }
    };


    CreateOneToManyResponse createOneToManyRelationshipResponse =
        (CreateOneToManyResponse)_serviceProxy.Execute(
        createOneToManyRelationshipRequest);

    _oneToManyRelationshipId =
        createOneToManyRelationshipResponse.RelationshipId;
    _oneToManyRelationshipName = 
        createOneToManyRelationshipRequest.OneToManyRelationship.SchemaName;

    Console.WriteLine(
        "The one-to-many relationship has been created between {0} and {1}.",
        "account", "campaign");
}
```
  
<a name="BKMK_EligibleCreateOneToManyRelationship"></a>   

### <a name="eligiblecreateonetomanyrelationship"></a>EligibleCreateOneToManyRelationship  

 Das folgende Beispiel erstellt eine `EligibleCreateOneToManyRelationship`-Methode, die <xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencedRequest> und <xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencingRequest> verwendet, um sicherzustellen, dass zwei Entitäten an einer 1:n-Entitätsbeziehung beteiligt sein können.  
  
```csharp
/// <summary>
/// Determines whether two entities are eligible to participate in a relationship
/// </summary>
/// <param name="referencedEntity">Primary Entity</param>
/// <param name="referencingEntity">Referencing Entity</param>
/// <returns></returns>
public bool EligibleCreateOneToManyRelationship(string referencedEntity, 
    string referencingEntity)
{
    //Checks whether the specified entity can be the primary entity in one-to-many
    //relationship.
    CanBeReferencedRequest canBeReferencedRequest = new CanBeReferencedRequest
    {
        EntityName = referencedEntity
    };

    CanBeReferencedResponse canBeReferencedResponse =
        (CanBeReferencedResponse)_serviceProxy.Execute(canBeReferencedRequest);

    if (!canBeReferencedResponse.CanBeReferenced)
    {
        Console.WriteLine(
            "Entity {0} can't be the primary entity in this one-to-many relationship", 
            referencedEntity);
    }

    //Checks whether the specified entity can be the referencing entity in one-to-many
    //relationship.
    CanBeReferencingRequest canBereferencingRequest = new CanBeReferencingRequest
    {
        EntityName = referencingEntity
    };

    CanBeReferencingResponse canBeReferencingResponse =
        (CanBeReferencingResponse)_serviceProxy.Execute(canBereferencingRequest);

    if (!canBeReferencingResponse.CanBeReferencing)
    {
        Console.WriteLine(
            "Entity {0} can't be the referencing entity in this one-to-many relationship", 
            referencingEntity);
    }


    if (canBeReferencedResponse.CanBeReferenced == true
        && canBeReferencingResponse.CanBeReferencing == true)
    {
        return true;
    }
    else
    {
        return false;
    }
}
```
  
<a name="BKMK_CreateNNEntityRelationship"></a>   

## <a name="create-an-nn-entity-relationship"></a>Erstellen einer n:n-Entitätsbeziehung  

 Im folgenden Beispiel wird eine [EligibleCreateManyToManyRelationship](#EligibleCreateManyToManyRelationship)-Methode verwendet, um sicherzustellen, dass die `Account` und `Campaign` Entitäten an einer n:n-Entitätsbeziehung beteiligt sein können, und anschließend die Entitätsbeziehung erstellt, indem <xref:Microsoft.Xrm.Sdk.Messages.CreateManyToManyRequest> verwendet wird.  
  
```csharp
bool accountEligibleParticipate =
    EligibleCreateManyToManyRelationship("account");
bool campaignEligibleParticipate =
    EligibleCreateManyToManyRelationship("campaign");

if (accountEligibleParticipate && campaignEligibleParticipate)
{

    CreateManyToManyRequest createManyToManyRelationshipRequest =
        new CreateManyToManyRequest
    {
        IntersectEntitySchemaName = "new_accounts_campaigns",
        ManyToManyRelationship = new ManyToManyRelationshipMetadata
        {
            SchemaName = "new_accounts_campaigns",
            Entity1LogicalName = "account",
            Entity1AssociatedMenuConfiguration =
            new AssociatedMenuConfiguration
            {
                Behavior = AssociatedMenuBehavior.UseLabel,
                Group = AssociatedMenuGroup.Details,
                Label = new Label("Account", 1033),
                Order = 10000
            },
            Entity2LogicalName = "campaign",
            Entity2AssociatedMenuConfiguration =
            new AssociatedMenuConfiguration
            {
                Behavior = AssociatedMenuBehavior.UseLabel,
                Group = AssociatedMenuGroup.Details,
                Label = new Label("Campaign", 1033),
                Order = 10000
            }
        }
    };

    CreateManyToManyResponse createManytoManyRelationshipResponse =
        (CreateManyToManyResponse)_serviceProxy.Execute(
        createManyToManyRelationshipRequest);


    _manyToManyRelationshipId =
        createManytoManyRelationshipResponse.ManyToManyRelationshipId;
    _manyToManyRelationshipName =
        createManyToManyRelationshipRequest.ManyToManyRelationship.SchemaName;

    Console.WriteLine(
        "The many-to-many relationship has been created between {0} and {1}.",
        "account", "campaign");
}
```
  
<a name="BKMK_EligibleCreateManyToManyRelationship"></a>   

### <a name="eligiblecreatemanytomanyrelationship"></a>EligibleCreateManyToManyRelationship  

 Das folgende Beispiel erstellt eine `EligibleCreateManyToManyRelationship`-Methode, die <xref:Microsoft.Xrm.Sdk.Messages.CanManyToManyRequest> verwendet, um sicherzustellen, dass eine Entität an einer n:n-Entitätsbeziehung beteiligt sein kann.  
  
```csharp
/// <summary>
/// Determines whether the entity can participate in a many-to-many relationship.
/// </summary>
/// <param name="entity">Entity</param>
/// <returns></returns>
public bool EligibleCreateManyToManyRelationship(string entity)
{
    CanManyToManyRequest canManyToManyRequest = new CanManyToManyRequest
    {
        EntityName = entity
    };

    CanManyToManyResponse canManyToManyResponse =
        (CanManyToManyResponse)_serviceProxy.Execute(canManyToManyRequest);

    if (!canManyToManyResponse.CanManyToMany)
    {
        Console.WriteLine(
            "Entity {0} can't participate in a many-to-many relationship.", 
            entity);
    }

    return canManyToManyResponse.CanManyToMany;
}
```
  
<a name="BKMK_RetrieveEntityRelationships"></a>   
## <a name="retrieve-entity-relationships"></a>Abrufen von Entitätsbeziehungen  
 Das folgende Beispiel ruft die beiden Entitätsbeziehungen ab, die mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest> zuvor erstellt werden. Das erste Beispiel verwendet `MetadataId`, das zweite `Name`.  
  
```csharp
//You can use either the Name or the MetadataId of the relationship.

//Retrieve the One-to-many relationship using the MetadataId.
RetrieveRelationshipRequest retrieveOneToManyRequest =
    new RetrieveRelationshipRequest { MetadataId = _oneToManyRelationshipId };
RetrieveRelationshipResponse retrieveOneToManyResponse =
    (RetrieveRelationshipResponse)_serviceProxy.Execute(retrieveOneToManyRequest);

Console.WriteLine("Retrieved {0} One-to-many relationship by id", retrieveOneToManyResponse.RelationshipMetadata.SchemaName);

//Retrieve the Many-to-many relationship using the Name.
RetrieveRelationshipRequest retrieveManyToManyRequest =
    new RetrieveRelationshipRequest { Name = _manyToManyRelationshipName};
RetrieveRelationshipResponse retrieveManyToManyResponse =
    (RetrieveRelationshipResponse)_serviceProxy.Execute(retrieveManyToManyRequest);

Console.WriteLine("Retrieved {0} Many-to-Many relationship by Name", retrieveManyToManyResponse.RelationshipMetadata.MetadataId);
```
  
### <a name="see-also"></a>Siehe auch  
 
 [Entitätsbeziehungsmetadatennachrichten](../entity-relationship-metadata-messages.md)   

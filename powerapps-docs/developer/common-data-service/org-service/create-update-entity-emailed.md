---
title: 'Erstellen und Upgraden einer Entität, um E-Mail-Aktivitäten an Datensätze zu senden (Common Data Service) | Microsoft Docs'
description: 'Sie können eine Entität erstellen, die eine E-Mail-Adresse enthält, die Sie verwenden können, um E-Mail-Aktivitäten an Datensätze für diese Entität zu senden.'
ms.custom: ''
ms.date: 04/05/2019
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
# <a name="create-and-update-an-entity-to-send-email-activities-to-records"></a>Erstellen und Upgraden einer Entität, um E-Mail-Aktivitäten an Datensätze zu senden

Sie können eine Entität erstellen, die eine E-Mail-Adresse enthält, die Sie verwenden können, um E-Mail-Aktivitäten an Datensätze für diese Entität zu senden.  
  
 Der folgende Beispielcode erstellt eine benutzerdefinierte Entität und legt die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsActivityParty> auf `true` fest. Es erstellt außerdem ein <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata>-Attribut mit <xref:Microsoft.Xrm.Sdk.Metadata.StringFormatName>.`Email` um eine E-Mail-Adresse zur Verwendung zur Verfügung zu stellen.  
  
 Selbst wenn Sie andere <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata>-Attribute hinzufügen, die als E-Mail-Adresse formatiert sind, wird nur das zuerst angegebene Attribut verwendet.  

```csharp
// Create the custom entity.
CreateEntityRequest createrequest = new CreateEntityRequest
{
    // Define an entity to enable for emailing. In order to do so,
    // IsActivityParty must be set.
    Entity = new EntityMetadata
    {
        SchemaName = _customEntityName,
        DisplayName = new Label("Agent", 1033),
        DisplayCollectionName = new Label("Agents", 1033),
        Description = new Label("Insurance Agents", 1033),
        OwnershipType = OwnershipTypes.UserOwned,
        IsActivity = false,

        // Unless this flag is set, this entity cannot be party to an
        // activity.
        IsActivityParty = true
    },

    // As with built-in emailable entities, the Primary Attribute will
    // be used in the activity party screens. Be sure to choose descriptive
    // attributes.
    PrimaryAttribute = new StringAttributeMetadata
    {
        SchemaName = "new_fullname",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        FormatName = StringFormatName.Text,
        DisplayName = new Label("Agent Name", 1033),
        Description = new Label("Agent Name", 1033)
    }
};

_serviceProxy.Execute(createrequest);
Console.WriteLine("The emailable entity has been created.");

// The entity will not be selectable as an activity party until its customizations
// have been published. Otherwise, the e-mail activity dialog cannot find
// a correct default view.
PublishAllXmlRequest publishRequest = new PublishAllXmlRequest();
_serviceProxy.Execute(publishRequest);

// Before any emails can be created for this entity, an Email attribute
// must be defined.
CreateAttributeRequest createFirstEmailAttributeRequest = new CreateAttributeRequest
{
    EntityName = _customEntityName,
    Attribute = new StringAttributeMetadata
    {
        SchemaName = "new_emailaddress",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        FormatName = StringFormatName.Email,
        DisplayName = new Label("Email Address", 1033),
        Description = new Label("Email Address", 1033)
    }
};

_serviceProxy.Execute(createFirstEmailAttributeRequest);
Console.WriteLine("An email attribute has been added to the emailable entity.");

// Create a second, alternate email address. Since there is already one 
// email attribute on the entity, this will never be used for emailing
// even if the first one is not populated.
CreateAttributeRequest createSecondEmailAttributeRequest = new CreateAttributeRequest
{
    EntityName = _customEntityName,
    Attribute = new StringAttributeMetadata
    {
        SchemaName = "new_secondaryaddress",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        FormatName = StringFormatName.Email,
        DisplayName = new Label("Secondary Email Address", 1033),
        Description = new Label("Secondary Email Address", 1033)
    }
};

_serviceProxy.Execute(createSecondEmailAttributeRequest);

Console.WriteLine("A second email attribute has been added to the emailable entity.");
```

### <a name="see-also"></a>Siehe auch

[Erstellen von Entitäten mit dem Organisationsservice](entity-operations-create.md)  
[Aktualisieren und Löschen von Entitäten mit dem Organisationsservice](entity-operations-update-delete.md)

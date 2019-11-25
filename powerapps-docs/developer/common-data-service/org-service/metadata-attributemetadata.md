---
title: Verwenden von Attributmetadaten (Common Data Service) | Microsoft-Dokumentation
description: Beschreibt allgemeine Vorgänge mit Attributmetadaten.
ms.custom: ''
ms.date: 04/05/2019
ms.reviewer: ''
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
ms.openlocfilehash: 069e8723ebdbb99d02c16b3d734d8bc5f76f9560
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748408"
---
# <a name="work-with-attribute-metadata"></a>Verwenden von Attributmetadaten

In diesem Thema werden einige allgemeine Vorgänge beschrieben, die bei Attributmetadaten angewendet werden können.

<a name="BKMK_CreateAttributes"></a>   
## <a name="create-attributes"></a>Erstellen von Attributen

 Sie erstellen Attribute, indem Sie einen der <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>-Typen definieren und ihn anschließend der Meldung <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> übergeben.  
  
 Das folgende Beispiel definiert die <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> für eine Reihe von unterschiedlichen Typen von Attributen und fügt sie zu `List<AttributeMetadata>` hinzu. Am Ende des Codes werden die Attributdefinitionen einer Instanz der Klasse <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> übergeben, und das Attribut wird mithilfe der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode.  
  
 Im folgenden Beispielcode wird angenommen, dass das aktuelle Anpassungspräfix "Neu" ist, da dies das standardmäßige Anpassungspräfix für den Organisationslösungsherausgeber ist. Sie sollten das Anpassungspräfix für den Lösungsherausgeber verwenden, das für den Lösungskontext sinnvoll ist.  

```csharp
// Create storage for new attributes being created
addedAttributes = new List<AttributeMetadata>();

// Create a boolean attribute
BooleanAttributeMetadata boolAttribute = new BooleanAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Boolean",
    LogicalName = "new_boolean",
    DisplayName = new Label("Sample Boolean", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Boolean Attribute", _languageCode),
    // Set extended properties
    OptionSet = new BooleanOptionSetMetadata(
        new OptionMetadata(new Label("True", _languageCode), 1),
        new OptionMetadata(new Label("False", _languageCode), 0)
        )
};

// Add to list
addedAttributes.Add(boolAttribute);

// Create a date time attribute
DateTimeAttributeMetadata dtAttribute = new DateTimeAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Datetime",
    LogicalName = "new_datetime",
    DisplayName = new Label("Sample DateTime", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("DateTime Attribute", _languageCode),
    // Set extended properties
    Format = DateTimeFormat.DateOnly,
    ImeMode = ImeMode.Disabled
};

// Add to list
addedAttributes.Add(dtAttribute);

// Create a decimal attribute   
DecimalAttributeMetadata decimalAttribute = new DecimalAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Decimal",
    LogicalName = "new_decimal",
    DisplayName = new Label("Sample Decimal", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Decimal Attribute", _languageCode),
    // Set extended properties
    MaxValue = 100,
    MinValue = 0,
    Precision = 1
};

// Add to list
addedAttributes.Add(decimalAttribute);

// Create a integer attribute   
IntegerAttributeMetadata integerAttribute = new IntegerAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Integer",
    LogicalName = "new_integer",
    DisplayName = new Label("Sample Integer", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Integer Attribute", _languageCode),
    // Set extended properties
    Format = IntegerFormat.None,
    MaxValue = 100,
    MinValue = 0
};

// Add to list
addedAttributes.Add(integerAttribute);

// Create a memo attribute 
MemoAttributeMetadata memoAttribute = new MemoAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Memo",
    LogicalName = "new_memo",
    DisplayName = new Label("Sample Memo", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Memo Attribute", _languageCode),
    // Set extended properties
    Format = StringFormat.TextArea,
    ImeMode = ImeMode.Disabled,
    MaxLength = 500
};

// Add to list
addedAttributes.Add(memoAttribute);

// Create a money attribute 
MoneyAttributeMetadata moneyAttribute = new MoneyAttributeMetadata
{
    // Set base properties
    SchemaName = "new_Money",
    LogicalName = "new_money",
    DisplayName = new Label("Money Picklist", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("Money Attribue", _languageCode),
    // Set extended properties
    MaxValue = 1000.00,
    MinValue = 0.00,
    Precision = 1,
    PrecisionSource = 1,
    ImeMode = ImeMode.Disabled
};

// Add to list
addedAttributes.Add(moneyAttribute);

// Create a picklist attribute  
PicklistAttributeMetadata pickListAttribute =
    new PicklistAttributeMetadata
    {
        // Set base properties
        SchemaName = "new_Picklist",
        LogicalName = "new_picklist",
        DisplayName = new Label("Sample Picklist", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        Description = new Label("Picklist Attribute", _languageCode),
        // Set extended properties
        // Build local picklist options
        OptionSet = new OptionSetMetadata
        {
            IsGlobal = false,
            OptionSetType = OptionSetType.Picklist,
            Options =
        {
            new OptionMetadata(
                new Label("Created", _languageCode), null),
            new OptionMetadata(
                new Label("Updated", _languageCode), null),
            new OptionMetadata(
                new Label("Deleted", _languageCode), null)
        }
        }
    };

// Add to list
addedAttributes.Add(pickListAttribute);

// Create a string attribute
StringAttributeMetadata stringAttribute = new StringAttributeMetadata
{
    // Set base properties
    SchemaName = "new_String",
    LogicalName = "new_string",

    DisplayName = new Label("Sample String", _languageCode),
    RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
    Description = new Label("String Attribute", _languageCode),
    // Set extended properties
    MaxLength = 100
};

// Add to list
addedAttributes.Add(stringAttribute);

//Multi-select attribute requires version 9.0 or higher.
if (_productVersion > new Version("9.0"))
{

    // Create a multi-select optionset
    MultiSelectPicklistAttributeMetadata multiSelectOptionSetAttribute = new MultiSelectPicklistAttributeMetadata()
    {
        SchemaName = "new_MultiSelectOptionSet",
        LogicalName = "new_multiselectoptionset",
        DisplayName = new Label("Multi-Select OptionSet", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        Description = new Label("Multi-Select OptionSet description", _languageCode),
        OptionSet = new OptionSetMetadata()
        {
            IsGlobal = false,
            OptionSetType = OptionSetType.Picklist,
            Options = {
        new OptionMetadata(new Label("First Option",_languageCode),null),
        new OptionMetadata(new Label("Second Option",_languageCode),null),
        new OptionMetadata(new Label("Third Option",_languageCode),null)
        }
        }
    };
    // Add to list
    addedAttributes.Add(multiSelectOptionSetAttribute);
}

// NOTE: LookupAttributeMetadata cannot be created outside the context of a relationship.
// Refer to the WorkWithRelationships.cs reference SDK sample for an example of this attribute type.

// NOTE: StateAttributeMetadata and StatusAttributeMetadata cannot be created via the SDK.

foreach (AttributeMetadata anAttribute in addedAttributes)
{
    // Create the request.
    CreateAttributeRequest createAttributeRequest = new CreateAttributeRequest
    {
        EntityName = Contact.EntityLogicalName,
        Attribute = anAttribute
    };

    // Execute the request.
    _serviceProxy.Execute(createAttributeRequest);

    Console.WriteLine("Created the attribute {0}.", anAttribute.SchemaName);
}
```

<a name="BKMK_RetrieveAttribute"></a>

## <a name="retrieve-an-attribute"></a>Abrufen eines Attributs

 Dieses Beispiel veranschaulicht, wie die <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> für ein Attribut mithilfe der <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest> abgerufen werden. In diesem Beispiel werden die Metadaten für ein benutzerdefiniertes Attribut <xref:Microsoft.Xrm.Sdk.Metadata.StringAttributeMetadata>, das als "new_string" bezeichnet wird, aus der in [Attribute erstellen](#BKMK_CreateAttributes) erstellten Kontaktentität abgerufen.
  
> [!NOTE]
> Da für <xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest.RetrieveAsIfPublished> "true" gilt, gibt diese Anforderung die aktuelle unveröffentlichte Definition dieses Attributs zurück. Sie können dies verwenden, wenn Sie einen Attribut-Editor erstellen und die unveröffentlichte Definition des Attributs abrufen möchten. Andernfalls sollten Sie `RetrieveAsIfPublished` nicht angeben. Weitere Informationen: [Vorbereiten von nicht veröffentlichten Metadaten](/dynamics365/customer-engagement/developer/customize-dev/publish-customizations#retrieving-unpublished-metadata).  

```csharp
// Create the request
RetrieveAttributeRequest attributeRequest = new RetrieveAttributeRequest
{
    EntityLogicalName = Contact.EntityLogicalName,
    LogicalName = "new_string",
    RetrieveAsIfPublished = true
};

// Execute the request
RetrieveAttributeResponse attributeResponse =
    (RetrieveAttributeResponse)_serviceProxy.Execute(attributeRequest);

Console.WriteLine("Retrieved the attribute {0}.",
    attributeResponse.AttributeMetadata.SchemaName);
```

<a name="BKMK_UpdateAttribute"></a>

## <a name="update-an-attribute"></a>Aktualisieren eines Attributs

 Dieser Beispielcode zeigt, wie ein Attribut aktualisiert wird. In diesem Beispiel wird <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest> zur Änderung der <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.DisplayName> Eigenschaft eines zuvor abgerufenen benutzerdefinierten Attributs für die `Contact` Entität verwendet.  

```csharp
// Modify the retrieved attribute
AttributeMetadata retrievedAttributeMetadata =
    attributeResponse.AttributeMetadata;
retrievedAttributeMetadata.DisplayName =
    new Label("Update String Attribute", _languageCode);

// Update an attribute retrieved via RetrieveAttributeRequest
UpdateAttributeRequest updateRequest = new UpdateAttributeRequest
{
    Attribute = retrievedAttributeMetadata,
    EntityName = Contact.EntityLogicalName,
    MergeLabels = false
};

// Execute the request
_serviceProxy.Execute(updateRequest);

Console.WriteLine("Updated the attribute {0}.",
    retrievedAttributeMetadata.SchemaName);
```

<a name="BKMK_CreateLookupAttribute"></a>

## <a name="create-a-lookup-attribute"></a>Erstellen eines Suchattributs

 Ein Suchattribut wird mithilfe der <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest> erstellt.  

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

<a name="BKMK_createcustlookup"></a>

## <a name="create-a-customer-lookup-attribute"></a>Erstellen eines Kundesuchattributs

 Im Gegensatz zu einem Suchattribut wird ein Kundensuchattribut mit der <xref:Microsoft.Xrm.Sdk.Messages.CreateCustomerRelationshipsRequest>-Meldung erstellt, die zwei Beziehungen zum Suchattribut hinzufügt: eine zur `Account`-Entität und die andere zur `Contact`-Entität. Sie können Beziehungen zu keinen anderen Entitäten als `Account` und `Contact` für ein Kundensuchattribut hinzufügen.  

```csharp
CreateCustomerRelationshipsRequest createCustomerReq = new CreateCustomerRelationshipsRequest
{
    Lookup = new LookupAttributeMetadata
    {
        Description = new Label("The owner of the bank account", 1033),
        DisplayName = new Label("Account owner", 1033),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.ApplicationRequired),
        SchemaName = "new_customerid"
    },
    OneToManyRelationships = new OneToManyRelationshipMetadata[]
    {
        new OneToManyRelationshipMetadata()
        {
            ReferencedEntity = "account",
            ReferencingEntity = _customEntityName,
            SchemaName = "new_bankaccount_customer_account",
        },
        new OneToManyRelationshipMetadata()
        {
            ReferencedEntity = "contact",
            ReferencingEntity = _customEntityName,
            SchemaName = "new_bankaccount_customer_contact",
        }
    },
};
_serviceProxy.Execute(createCustomerReq);
```

<a name="BKMK_CreatePicklistGlobalOptionSet"></a>

## <a name="create-a-picklist-that-uses-a-global-option-set"></a>Erstellen einer Auswahlliste, die einen globalen Optionssatz verwendet

 Dieser Beispielcode zeigt, wie ein <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>-Attribut erstellt wird, dem ein globaler Optionssatz zugeordnet ist.  
  
 Im folgenden Beispiel wird <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest> verwendet, um die Optionen für ein <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>-Attribut festzulegen, das einen globalen Optionssatz mit einem Namen verwenden soll, der durch die Zeichenfolgenvariable `_globalOptionSetName` dargestellt wird. Weitere Informationen: [Anpassen von Optionssätzen](metadata-option-sets.md)  
 
```csharp
// Create a Picklist linked to the option set.
// Specify which entity will own the picklist, and create it.
CreateAttributeRequest createRequest = new CreateAttributeRequest
{
    EntityName = Contact.EntityLogicalName,
    Attribute = new PicklistAttributeMetadata
    {
        SchemaName = "sample_examplepicklist",
        LogicalName = "sample_examplepicklist",
        DisplayName = new Label("Example Picklist", _languageCode),
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),

        // In order to relate the picklist to the global option set, be sure
        // to specify the two attributes below appropriately.
        // Failing to do so will lead to errors.
        OptionSet = new OptionSetMetadata
        {
            IsGlobal = true,
            Name = _globalOptionSetName
        }
    }
};

_serviceProxy.Execute(createRequest);
```

<a name="BKMK_InsertNewStatusValue"></a>

## <a name="insert-a-new-status-value"></a>Einfügen eines neuen Statuswerts

 Dieser Beispielcode zeigt, wie eine neue Option **Statusgrund** für das Attribut <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata> eingefügt wird.  
  
 Im folgenden Beispielcode wird die <xref:Microsoft.Xrm.Sdk.Messages.InsertStatusValueRequest> verwendet, um eine neue Option für das zur Entität `Contact` gehörende Attribut `Contact.StatusCode` festzulegen, das gültig ist, wenn der `Contact.StateCode` 0 (Aktiv) ist. Im <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode verarbeitet die Anforderung.  
  
 Der folgende Beispielcode erlaubt zwei gültige Optionen **Statusgrund** für aktive Kontakte: **Aktiv** und **Inaktiv**.  
  
```csharp
// Use InsertStatusValueRequest message to insert a new status 
// in an existing status attribute. 
// Create the request.
InsertStatusValueRequest insertStatusValueRequest =
    new InsertStatusValueRequest
{
    AttributeLogicalName = "statuscode",
    EntityLogicalName = Contact.EntityLogicalName,
    Label = new Label("Dormant", _languageCode),
    StateCode = 0
};

// Execute the request and store newly inserted value 
// for cleanup, used later part of this sample. 
_insertedStatusValue = ((InsertStatusValueResponse)_serviceProxy.Execute(
    insertStatusValueRequest)).NewOptionValue;

Console.WriteLine("Created {0} with the value of {1}.",
    insertStatusValueRequest.Label.LocalizedLabels[0].Label,
    _insertedStatusValue);
```

<a name="BKMK_UpdateStateValue"></a>

## <a name="update-a-state-value"></a>Aktualisieren eines Statuswerts

 Dieser Beispielcode zeigt, wie die Beschriftung für eine Option in einem <xref:Microsoft.Xrm.Sdk.Metadata.StateAttributeMetadata>-Attribut geändert wird.  
  
 Im folgenden Beispielcode wird <xref:Microsoft.Xrm.Sdk.Messages.UpdateStateValueRequest> verwendet, um die Optionsbeschriftung `Contact.StateCode` von **Aktiv** in **Öffnen** zu ändern.  

```csharp
// Modify the state value label from Active to Open.
// Create the request.
UpdateStateValueRequest updateStateValue = new UpdateStateValueRequest
{
    AttributeLogicalName = "statecode",
    EntityLogicalName = Contact.EntityLogicalName,
    Value = 1,
    Label = new Label("Open", _languageCode)
};

// Execute the request.
_serviceProxy.Execute(updateStateValue);

Console.WriteLine(
    "Updated {0} state attribute of {1} entity from 'Active' to '{2}'.",
    updateStateValue.AttributeLogicalName,
    updateStateValue.EntityLogicalName,
    updateStateValue.Label.LocalizedLabels[0].Label
    );
```

 Sie können `StateCode`-Optionen nicht hinzufügen oder entfernen, aber Sie können die Beschriftungen der Optionen ändern.  
  
<a name="BKMK_InsertNewOptionLocalOptionSet"></a>

## <a name="insert-a-new-option-in-a-local-option-set"></a>Fügen Sie eine neue Option in einen lokalen Optionssatz ein.

 Dieser Beispielcode zeigt, wie Sie eine neue Option zu einem lokalen Optionssatz hinzufügen. Im folgenden Beispiel wird <xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest> verwendet, um eine neue Option zu einem benutzerdefinierten Attribut <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> für die Entität `Contact` hinzuzufügen.  

```csharp
// Create a request.
InsertOptionValueRequest insertOptionValueRequest =
    new InsertOptionValueRequest
{
    AttributeLogicalName = "new_picklist",
    EntityLogicalName = Contact.EntityLogicalName,
    Label = new Label("New Picklist Label", _languageCode)
};

// Execute the request.
int insertOptionValue = ((InsertOptionValueResponse)_serviceProxy.Execute(
    insertOptionValueRequest)).NewOptionValue;

Console.WriteLine("Created {0} with the value of {1}.",
    insertOptionValueRequest.Label.LocalizedLabels[0].Label,
    insertOptionValue);
```

<a name="BKMK_ChangeOrderOptionLocalOptionSet"></a>

## <a name="change-the-order-of-options-in-a-local-option-set"></a>Ändern der Reihenfolge von Optionen in einem lokalen Optionssatz

 Dieser Beispielcode zeigt, wie die Reihenfolge der Optionen in einem lokalen Optionssatz geändert wird. Das folgende Beispiel ruft ein benutzerdefiniertes <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata>-Attribut ab und ändert die Reihenfolge der ursprünglichen Optionen mithilfe der Funktion [OrderBy](https://msdn.microsoft.com/library/system.linq.enumerable.orderby.aspx)**LINQ** zum Sortieren von Elementen in aufsteigender Reihenfolge nach dem Beschriftungstext. Anschließend wird mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest> die neue Reihenfolge der Optionen für das Attribut festgelegt.  
  
 Verwenden Sie die LINQ-Funktion [OrderByDecending](https://msdn.microsoft.com/library/system.linq.enumerable.orderbydescending.aspx), um die Elemente in absteigender Reihenfolge zu sortieren.  

```csharp
// Use the RetrieveAttributeRequest message to retrieve  
// a attribute by it's logical name.
RetrieveAttributeRequest retrieveAttributeRequest =
    new RetrieveAttributeRequest
{
    EntityLogicalName = Contact.EntityLogicalName,
    LogicalName = "new_picklist",
    RetrieveAsIfPublished = true
};

// Execute the request.
RetrieveAttributeResponse retrieveAttributeResponse =
    (RetrieveAttributeResponse)_serviceProxy.Execute(
    retrieveAttributeRequest);

// Access the retrieved attribute.
PicklistAttributeMetadata retrievedPicklistAttributeMetadata =
    (PicklistAttributeMetadata)
    retrieveAttributeResponse.AttributeMetadata;

// Get the current options list for the retrieved attribute.
OptionMetadata[] optionList =
    retrievedPicklistAttributeMetadata.OptionSet.Options.ToArray();

// Change the order of the original option's list.
// Use the OrderBy (OrderByDescending) linq function to sort options in  
// ascending (descending) order according to label text.
// For ascending order use this:
var updateOptionList =
    optionList.OrderBy(x => x.Label.LocalizedLabels[0].Label).ToList();

// For descending order use this:
// var updateOptionList =
//      optionList.OrderByDescending(
//      x => x.Label.LocalizedLabels[0].Label).ToList();

// Create the request.
OrderOptionRequest orderOptionRequest = new OrderOptionRequest
{
    // Set the properties for the request.
    AttributeLogicalName = "new_picklist",
    EntityLogicalName = Contact.EntityLogicalName,
    // Set the changed order using Select linq function 
    // to get only values in an array from the changed option list.
    Values = updateOptionList.Select(x => x.Value.Value).ToArray()
};

// Execute the request
_serviceProxy.Execute(orderOptionRequest);

Console.WriteLine("Option Set option order changed");
```

<a name="BKMK_DeleteAttribute"></a>

## <a name="delete-an-attribute"></a>Löschen eines Attributs

 Dieses Beispiel zeigt, wie Sie in einer `List<`<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>`>` gespeicherte Attribute löschen, die für die `Contact`-Entität in [Attribute erstellen](#BKMK_CreateAttributes) erstellt wurden. Für jedes <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> wird von <xref:Microsoft.Xrm.Sdk.Messages.DeleteAttributeRequest> die Anforderung vorbereitet, die mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> verarbeitet wird.  

```csharp
// Delete all attributes created for this sample.
foreach (AttributeMetadata anAttribute in addedAttributes)
{
    // Create the request object
    DeleteAttributeRequest deleteAttribute = new DeleteAttributeRequest
    {
        // Set the request properties 
        EntityLogicalName = Contact.EntityLogicalName,
        LogicalName = anAttribute.SchemaName
    };
    // Execute the request
    _serviceProxy.Execute(deleteAttribute);
}
```

---
title: Entitäten erstellen mithilfe des Organisationsservices (Common Data Service für Apps)| Microsoft Docs
description: <Description>
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
# <a name="create-entities-using-the-organization-service"></a>Erstellen von Entitäten mit dem Organisationsservice

Dieses Thema enthält Beispiele zu später und früherer gebundenen Programmierungsstile. Weitere Informationen: 
- [Programmierung mit später und früher Bindung mithilfe des Organisationsservices](early-bound-programming.md)
- [Generieren von Klassen mit früher Bindung für den Organisationsdienst](generate-early-bound-classes.md)

## <a name="basic-create"></a>Grundlegende Erstellung

Die folgenden Beispiele veranschaulichen, wie einem Entitätsdatensatz mithilfe des späten und frühen Generierung Stils erstellt wird

<!-- TODO make this an include? -->Jedes der Beispiele verwendet eine `svc`-Variable, die eine Instanz einer Klasse darstellt, die Sie auf der Benutzeroberfläche der <xref:Microsoft.Xrm.Sdk.IOrganizationService> implementieren. Weitere Informationen zu Klassen finden Sie unter [Organisationsservice-Benutzeroberfläche](iorganizationservice-interface.md).

> [!NOTE]
> Jede Entität besitzt ein Attribut mit eindeutigem Bezeichnerwert, den Sie angeben können, wenn Sie eine Entität erstellen. In den meisten Fällen empfiehlt das System, dass Sie diese Option festlegen, da die Werte, die vom System generiert werden, für eine bestmögliche Leistung optimiert werden.


### <a name="late-bound-example"></a>Spät gebundenes Beispiel

Das folgende Bespiel mithilfe <xref:Microsoft.Xrm.Sdk.Entity> einer Klasse dar, um einen Firmendatensatz mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> zu erstellen Methode. 

```csharp
//Use Entity class with entity logical name
var account = new Entity("account");

// set attribute values
    // string primary name
    account["name"] = "Contoso";
    // Boolean (Two option)
    account["creditonhold"] = false;
    // DateTime
    account["lastonholdtime"] = new DateTime(2017, 1, 1);
    // Double
    account["address1_latitude"] = 47.642311;
    account["address1_longitude"] = -122.136841;
    // Int
    account["numberofemployees"] = 500;
    // Money
    account["revenue"] = new Money(new decimal(5000000.00));
    // Picklist (Option set)
    account["accountcategorycode"] = new OptionSetValue(1); //Preferred customer

//Create the account
Guid accountid = svc.Create(account);
```

### <a name="early-bound-example"></a>Früh gebundenes Beispiel

Das folgende Bespiel stellt eine erzielte `Account`  Klasse dar, um einen Firmendatensatz mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> zu erstellen Methode.

Die `Account`-Klasse wird von der <xref:Microsoft.Xrm.Sdk.Entity>-Klasse abgeleitet.

```csharp
var account = new Account();
// set attribute values
    // string primary name
    account.Name = "Contoso";
    // Boolean (Two option)
    account.CreditOnHold = false;
    // DateTime
    account.LastOnHoldTime = new DateTime(2017, 1, 1);
    // Double
    account.Address1_Latitude = 47.642311;
    account.Address1_Longitude = -122.136841;
    // Int
    account.NumberOfEmployees = 500;
    // Money
    account.Revenue = new Money(new decimal(5000000.00));
    // Picklist (Option set)
    account.AccountCategoryCode = new OptionSetValue(1); //Preferred customer

//Create the account
Guid accountid = svc.Create(account);
```

## <a name="use-the-createrequest-class"></a>Die CreateRequest-Klasse nutzen

Statt  <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> zu verwenden. Methode, können Sie die spät gebundene Klasse <xref:Microsoft.Xrm.Sdk.Entity> oder früher generierte Entitätsklassen mit Klasse<xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> verwenden, indem die Eigenschaft<xref:Microsoft.Xrm.Sdk.Messages.CreateRequest.Target> Entitätsinstanz auf die und dann mithilfe <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> festlegen Methode, um einem.<xref:Microsoft.Xrm.Sdk.Messages.CreateResponse> Die ID des Datensatzes ist Eigenschaftswert im <xref:Microsoft.Xrm.Sdk.Messages.CreateResponse.id>.

```csharp
var request = new CreateRequest() { Target = account };
var response  = (CreateResponse)svc.Execute(request);
Guid accountid = response.id;
```

### <a name="when-to-use-the-createrequest-class"></a>Wenn die CreateRequest-Klasse verwendet werden soll

Sie müssen die <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> Klasse verwenden, wenn Sie optionale Parameter behalten möchten. Es gibt zwei Fälle, in denen Sie möglicherweise bestimmte Parameter brauchen.
 - Geben Sie den Zeitpunkt an, zu dem der Duplikaterkennungsauftrag gestartet werden soll. Weitere Informationen:  [Suchen nach Duplikaten](#check-for-duplicate-records)
 - Wenn Sie einen Entitätsdatensatz erstellen, der einer Lösungskomponente darstellt, wie [WebResource](../reference/entities/webresource.md) und diese einer bestimmten Lösung zuordnen möchten. In diesem Fall überprüfen Sie den Wert der mithilfe [Solution.UniqueName](../reference/entities/solution.md#BKMK_UniqueName) des Parameters `SolutionUniqueName` einschließen möchten. Weitere Informationen: [Verwenden von Meldungen mit dem Organisationsservice](use-messages.md)

## <a name="create-related-entities-in-one-operation"></a>Erstellen verknüpfter Entitäten in einem Vorgang

Wenn Sie eine neue Entität erstellen, können Sie einen Satz verknüpfter Entitätsdatensätze ebenfalls definieren, um im gleichen Vorgang zu erstellen.

Die folgenden Beispiele später und früher Bindungen erstellen eine [Firma](../reference/entities/account.md) und einen [Kointakt](../reference/entities/contact.md) der  [Kontakt, Firma, primärer Kontakt](../reference/entities/contact.md#BKMK_account_primary_contact)1: n-Beziehung, in der die [Firma primarycontactid](../reference/entities/account.md#BKMK_PrimaryContactId) und Suche `ReferencingAttribute` ist.

Die Beispiele erstellen auch drei verknüpfte [Aufgabe](../reference/entities/task.md) Entitätsdatensätze mithilfe [Firma Account_Tasks](../reference/entities/account.md#BKMK_Account_Tasks) der 1: n-Beziehung, in der die [Aufgabe regardingobjectid](../reference/entities/task.md#BKMK_RegardingObjectId) der Suche `ReferencingAttribute`ist.

### <a name="late-bound-example"></a>Spät gebundenes Beispiel

Im spät gebundenen Stil müssen Sie die verknüpfte Entität (en) explizit hinzufügen <xref:Microsoft.Xrm.Sdk.EntityCollection> und dann die<xref:Microsoft.Xrm.Sdk.Relationship>- Klasse verwenden, um die Beziehung mithilfe`SchemaName` der Beziehung angeben, damit sie hinzugefügt<xref:Microsoft.Xrm.Sdk.Entity><xref:Microsoft.Xrm.Sdk.Entity.RelatedEntities> werden. -Eigenschaft verfügbar.

```csharp
// Use Entity class with entity logical name
var account = new Entity("account");

// Set attribute values
    // string primary name
    account["name"] = "Sample Account";

// Create Primary contact
var primaryContact = new Entity("contact");
primaryContact["firstname"] = "John";
primaryContact["lastname"] = "Smith";

// Add the contact to an EntityCollection
EntityCollection primaryContactCollection = new EntityCollection();
primaryContactCollection.Entities.Add(primaryContact);

// Set the value to the relationship
account.RelatedEntities[new Relationship("account_primary_contact")] = primaryContactCollection;

// Add related tasks to create
var taskList = new List<Entity>() {
            new Entity("task") { ["subject"] = "Task 1" },
            new Entity("task") { ["subject"] = "Task 2" },
            new Entity("task") { ["subject"] = "Task 3" }
        };

// Add the tasks to an EntityCollection
EntityCollection tasks = new EntityCollection(taskList);

// Set the value to the relationship
account.RelatedEntities[new Relationship("Account_Tasks")] = tasks;

// Create the account
Guid accountid = svc.Create(account);
```

### <a name="early-bound-example"></a>Früh gebundenes Beispiel

Mit früher Bindungs-Klassen können Sie weniger Code schreiben, da Klassen die Definition der Geschäftsbeziehungen enthalten.

```csharp
var account = new Account();
// set attribute values
    // string primary name
    account.Name = "Sample Account";

    // Set the account primary contact
    account.account_primary_contact = new Contact()
    { FirstName = "John", LastName = "Smith" };

// Set a list of Tasks to create
account.Account_Tasks = new List<Task>() {
        new Task() { Subject = "Task 1" },
        new Task() { Subject = "Task 2" },
        new Task() { Subject = "Task 3" }
    };

// Create the account
Guid accountid = svc.Create(account);
```

## <a name="associate-entities-on-create"></a>Entitäten bei Erstellung zuordnen

Sie können einen neuen Datensatz einem vorhandenen Datensatz zuordnen, wenn Sie ihn gleich erstellen wie wenn Sie ihn updaten würden. Sie müssen die <xref:Microsoft.Xrm.Sdk.EntityReference> verwenden, um den Wert eines Suchattributs festzulegen.

Diese Suchattribut-Zuweisung ist dann für frühe und spät gebundene Stile gleich.

```csharp
//Use Entity class with entity logical name
var account = new Entity("account");

// set attribute values
    //string primary name
    account["name"] = "Sample Account";

Guid primarycontactid = new Guid("e6fa5509-2582-e811-a95e-000d3af40ae7");

account["primarycontactid"] = new EntityReference("contact", primarycontactid);

//Create the account
Guid accountid = svc.Create(account);
```

### <a name="use-alternate-keys"></a>Alternativschlüssel verwenden

Wenn Sie die ID der Entität nicht kennen und die folgenden Bedingungen erfüllt sind:
- Sie haben Alternativschlüssel für die Entität konfiguriert
- Sie kennen die Schlüsselwerte

Sie können die anderen Konstruktoren <xref:Microsoft.Xrm.Sdk.EntityReference> mit und`keyName` der Parameter`keyValue` verwenden.
```csharp
account["primarycontactid"] = new EntityReference("contact", "sample_username", "john.smith123");
```
> [!NOTE]
> Alternativschlüssel werden in der Regel nur für Datenenintegrationsszenarien verwendet

Weitere Informationen: 
- [Definieren von Alternativschlüsseln für den Verweis auf Datensätze](../../../maker/common-data-service/define-alternate-keys-reference-records.md)
- [Verwenden Sie einen Alternativschlüssel, um Datensätze zu erstellen](../use-alternate-key-create-record.md)
- [Arbeiten mit Alternativschlüsseln](../define-alternate-keys-entity.md)


## <a name="check-for-duplicate-records"></a>Nach doppelten Datensätzen suchen

Weitere Informationen: [DoppelteAbfdra Daten mit dem Organisationsdienst erkennen](detect-duplicate-data.md).

## <a name="set-default-values-from-the-primary-entity"></a>Legen Sie den Standardwerte der primären Entität fest

Wenn Benutzer neue Datensätze in der Anwendung erstellen, sind sie im Rahmen eines anderen Datensatzes erstellt. So erstellen Sie möglicherweise einen neuen Kontaktdatensatz im Kontext einer Firma. Wenn dies geschieht, werden bestimmte Attributwerte von der Firmaenentität im Kontaktformular kopiert. Dies beschleunigt die Erstellung des neuen verknüpften Datensatzes, da der neue Datensatz einige Standardwerte hat, die festgelegt werden, so dass die Person, die den Datensatz erstellt, diesen nicht bearbeitet muss, um den Wert einzugeben. Sie können die Werte ändern, wenn Sie dies möchten, vor dem Speichern.

Die Werte, die kopiert werden, wenn ein neuer Datensatz erstellt wird, wird gleich erstellt und ist von der verknüpften Konfiguration mit der CDS für Apps-Umgebung gesteuert, sodass sie zwischen den Umgebungen wechseln können. 

Weitere Informationen: 
- [Entitätsfelder zuordnen](../../../maker/common-data-service/map-entity-fields.md)
- [Anpassen von Entitäts- und Attributzuordnungen](../customize-entity-attribute-mappings.md)

Als Entwickler können Sie die <xref:Microsoft.Crm.Sdk.Messages.InitializeFromRequest> Klasse verwenden, um eine Entität mit diesen Standardwerten zu generieren.

Der folgende Code erstellt einen neuen Kontakt, der einer vorhandenen Firma zugeordnet ist. Die Kontaktentität wird mit der angegebenen Firma zugeordnet und bestimmte Attributwerte, wie `Telephone1` und die verschiedenen Adressenwerte, die zwischen einer Firma und der Kontaktentität freigegeben werden, sind standardmäßig festgelegt.

```csharp
//The account that the contact will be associated with:
var parentAccount = new EntityReference("account", new Guid("a976763a-ba1c-e811-a954-000d3af451d6"));

// Initialize a new contact entity with default values from the account.
var request = new InitializeFromRequest()
{
    EntityMoniker = parentAccount,
    TargetEntityName = "contact"

};

var response = (InitializeFromResponse)svc.Execute(request);
//Get the Entity from the response
Entity contact = response.Entity;

// Set values that are not from the account
contact["firstname"] = "Joe";
contact["lastname"] = "Smith";

// Create the contact
Guid contactid = svc.Create(contact);
```

## <a name="use-upsert"></a>Verwendung von Upsert

Eine weitere Methode, eine Entität zu erstellen ist, die <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> Klasse zu verwenden. Ein Upsert erstellt eine neue Entität, wenn kein Datensatz vorhanden ist, der einen eindeutigen Bezeichner hat, inklusive in der Entität,  die mit der Anfrage übergeben werden.

Weitere Informationen: [Upsert verwenden](entity-operations-update-delete.md#use-upsert)


### <a name="see-also"></a>Siehe auch

[Abrufen einer Entität mithilfe des Organisationsdienstes](entity-operations-retrieve.md)<br />
[Aktualisieren und Löschen von Entitäten mit dem Organisationsservice](entity-operations-update-delete.md)<br />
[Entitäten mithilfe des Organisations-Service zuordnen oder trennen](entity-operations-associate-disassociate.md)<br />


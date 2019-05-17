---
title: Entitäten mithilfe des Organisationsservices aktualisieren und löschen (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie, wie Sie mithilfe des Organisations-Service Entitäten updaten und trennen'
ms.custom: ''
ms.date: 04/21/2019
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
# <a name="update-and-delete-entities-using-the-organization-service"></a>Aktualisieren und Löschen von Entitäten mit dem Organisationsservice

Dieses Thema enthält Beispiele zu später und früherer gebundenen Programmierungsstile. Weitere Informationen: [Programmierung mit später und früher Bindung mithilfe des Organisationsservices](early-bound-programming.md)

Jedes der Beispiele verwendet eine `svc`-Variable, die eine Instanz einer Klasse darstellt, die Sie auf<xref:Microsoft.Xrm.Sdk.IOrganizationService> der Benutzeroberfläche implementieren. Weitere Informationen zu Klassen finden Sie unter [Organisationsservice-Benutzeroberfläche](iorganizationservice-interface.md).

> [!IMPORTANT]
>  Wenn Sie eine Entität durchführen, schließen Sie die Attribute aus, die Sie ändern. Aktualisieren Sie einfach die Attribute einer Entität, die Sie bereits abgerufen haben und aktualisieren das Attribut, obwohl der Wert unverändert ist. Dies kann Systemereignisse verursachen, die Geschäftslogik starten können, da angenommen wird, dass die Werte geändert haben. Dieses kann bewirken, dass Eigenschaften so aussehen, als seien sie beim Daten-Bearbeiten aktualisiert worden, wenn tatsächlich sie sich nicht wirklich geändert haben. 
>
> Sie sollten eine Entitätsinstanz neu erstellen, das ID-Attribut sowie alle Attributwerte festlegen, die Sie ändern und diese Entitätsinstanz verwenden, um den Datensatz zu aktualisieren.

> [!NOTE]
> Metadaten für Attribute enthält eine `RequiredLevel`-Eigenschaft. Falls das auf `SystemRequired` festgelegt ist, können Sie dieser Attribute auf einen NULL-Wert nicht festlegen. Wenn Sie dies versuchen, erhalten Sie Fehlercode `-2147220989` mit der Meldung`Attribute: <attribute name> cannot be set to NULL`.
> 
> Weitere Informationen: [Attributerforderlichkeitsstufe](../entity-attribute-metadata.md#attribute-requirement-level)

## <a name="basic-update"></a>Grundlegende Aktualisierung

Beide der folgenden Beispiele verwendeten<xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> Methode, um Attributwerte für eine Entität festzulegen, die zuvor erhalten wurde.

Verwenden Sie die <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Id> Eigenschaft, um den eindeutigen Bezeichnerwert der Entität zur Entitätsinstanz zu übertragen, die verwendet wird, um den Vorgang upzudaten.

> [!NOTE]
> Wenn Sie versuchen, einen Datensatz ohne einen Primärschlüsselwert zu aktualisieren, wird der Fehler: `Entity Id must be specified for Update` angezeigt.
> 
> Falls Sie keinen Primärschlüsselwert haben, können Sie Datensätze auch mithilfe der Alternativschlüssel ausführen. Weitere Informationen: [Update mit Alternativschlüssel](#update-with-alternate-key)

### <a name="late-bound-example"></a>Spät gebundenes Beispiel

Das folgende Bespiel mithilfe <xref:Microsoft.Xrm.Sdk.Entity> einer Klasse dar, um einen Firmendatensatz mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> zu erstellen Methode. 

```csharp
var retrievedAccount = new Entity("account", new Guid("a976763a-ba1c-e811-a954-000d3af451d6"));

//Use Entity class with entity logical name
var account = new Entity("account");
account.Id = retrievedAccount.Id;
// set attribute values
// Boolean (Two option)
account["creditonhold"] = true;
// DateTime
account["lastonholdtime"] = DateTime.Now;
// Double
account["address1_latitude"] = 47.642311;
account["address1_longitude"] = -122.136841;
// Int
account["numberofemployees"] = 400;
// Money
account["revenue"] = new Money(new Decimal(2000000.00));
// Picklist (Option set)
account["accountcategorycode"] = new OptionSetValue(2); //Standard customer

//Update the account
svc.Update(account);
```

### <a name="early-bound-example"></a>Früh gebundenes Beispiel

Das folgende Bespiel stellt eine erzielte `Account`  Klasse dar, um einen Firmendatensatz mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> zu erstellen Methode.

```csharp
var retrievedAccount = new Account()
{ Id = new Guid("a976763a-ba1c-e811-a954-000d3af451d6") };

var account = new Account();
account.Id = retrievedAccount.Id;
// set attribute values
// Boolean (Two option)
account.CreditOnHold = true;
// DateTime
account.LastOnHoldTime = DateTime.Now;
// Double
account.Address1_Latitude = 47.642311;
account.Address1_Longitude = -122.136841;
// Int
account.NumberOfEmployees = 400;
// Money
account.Revenue = new Money(new Decimal(2000000.00));
// Picklist (Option set)
account.AccountCategoryCode = new OptionSetValue(2); //Standard customer

//Update the account
svc.Update(account);
```

## <a name="use-the-updaterequest-class"></a>Die UpdateRequest-Klasse

Statt  <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> zu verwenden. Methode, können Sie die spät gebundene Klasse <xref:Microsoft.Xrm.Sdk.Entity> oder früher generierte Entitätsklassen mit Klasse<xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> verwenden, indem die Eigenschaft<xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest.Target> Entitätsinstanz auf die und dann mithilfe festlegen<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode.

> [!NOTE]
> Sie hat keine<xref:Microsoft.Xrm.Sdk.Messages.UpdateResponse> Eigenschaften. Während sie mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode zurückgegeben wird, ist es nicht nötig, darauf zu referenzieren.
 
```csharp
var request = new UpdateRequest()
{ Target = account };
svc.Execute(request);
```
### <a name="when-to-use-the-updaterequest-class"></a>Wedd ie UpdateRequest-Klasse verwendet werden soll

Sie müssen die <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> Klasse verwenden, wenn Sie optionale Parameter behalten möchten. Es gibt zwei Fälle, in denen Sie möglicherweise bestimmte Parameter brauchen.
 - Geben Sie den Zeitpunkt an, zu dem der Duplikaterkennungsauftrag gestartet werden soll. Weitere Informationen:  [Suchen nach Duplikaten](entity-operations-create.md#check-for-duplicate-records)
 - Wenn Sie einem Entitätsdatensatz erstellen, der einer Lösungskomponente darstellt, wie [WebResource](../reference/entities/webresource.md) und diese einer bestimmten Lösung zuordnen möchten. In diesem Fall überprüfen Sie den Wert der mithilfe [Solution.UniqueName](../reference/entities/solution.md#BKMK_UniqueName) des Parameters `SolutionUniqueName` einschließen möchten. Weitere Informationen: [Verwenden von Meldungen mit dem Organisationsservice](use-messages.md)

Sie müssen die verwenden Klasse auch <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> nutzen, wenn Sie einem Verhalten eine optimistische Parallelität angeben möchten. Weitere Informationen: [Optimistische Parallelität Verhalten](#optimistic-concurrency-behavior).

## <a name="update-related-entities-in-one-operation"></a>Updaten verknüpfter Entitäten in einem Vorgang

In ähnlicher Weise können Sie [Verknüpfte Entitäten in einen Vorgang erstellen](entity-operations-create.md#create-related-entities-in-one-operation), Sie können auch verknüpfte Entitäten updaten.

Führen Sie hierzu die Schritte aus, müssen Sie die Entität mit den verknüpften Datensätzen zu sodass die nachzuverfolgenden GUID-ID-Werten zugreifen können. Weitere Informationen: [Abrufen von verknüpften Datensätzen](entity-operations-retrieve.md#retrieve-with-related-records)

> [!IMPORTANT]
> Aktualisierungen an den Datensätzen werden in einer bestimmten Reihenfolge ausgeführt. Zunächst werden primäre Entitäten verarbeitet, und anschließend werden verknüpfte Entitäten verarbeitet. Wenn eine Änderung von der primären Entität für ein Such- oder verknüpftes Entitätsattribut vorgenommen wird und dann eine verknüpfte Entität das gleiche Attribut aktualisiert, wird der Wert der verknüpften Entität beibehalten. Im Allgemeinen sollte ein Suchattributwert und die Entsprechung in<xref:Microsoft.Xrm.Sdk.Entity><xref:Microsoft.Xrm.Sdk.Entity.RelatedEntities> für dieselbe Beziehung sollte nicht gleichzeitig verwendet werden.

### <a name="late-bound-example"></a>Spät gebundenes Beispiel


```csharp
var account = new Entity("account");
account.Id = retrievedAccount.Id;

//Define relationships
var primaryContactRelationship = new Relationship("account_primary_contact");
var AccountTasksRelationship = new Relationship("Account_Tasks");

//Update the account name
account["name"] = "New Account name";

//Update the email address for the primary contact of the account
var contact = new Entity("contact");
contact.Id = retrievedAccount.RelatedEntities[primaryContactRelationship]
.Entities.FirstOrDefault().Id;
contact["emailaddress1"] = "someone_a@example.com";

List<Entity> primaryContacts = new List<Entity>();
primaryContacts.Add(contact);  
account.RelatedEntities.Add(primaryContactRelationship, new EntityCollection(primaryContacts));

// Find related Tasks that need to be updated
List<Entity> tasksToUpdate = retrievedAccount
.RelatedEntities[AccountTasksRelationship].Entities
.Where(t => t["subject"].Equals("Example Task")).ToList();

// A list to put the updated tasks
List<Entity> updatedTasks = new List<Entity>();

//Fill the list of updated tasks based on the tasks that need to but updated
tasksToUpdate.ForEach(t => {
var updatedTask = new Entity("task");
updatedTask.Id = t.Id;
updatedTask["subject"] = "Updated Subject";

updatedTasks.Add(updatedTask);
});

//Set the updated tasks to the collection
account.RelatedEntities.Add(AccountTasksRelationship, new EntityCollection(updatedTasks));

//Update the account and related contact and tasks
svc.Update(account);
```


### <a name="early-bound-example"></a>Früh gebundenes Beispiel

```csharp
var account = new Account();
account.Id = retrievedAccount.Id;

//Update the account
account.Name = "New Account name";

//Update the email address for the primary contact of the account
account.account_primary_contact = new Contact
{ Id = retrievedAccount.PrimaryContactId.Id, EMailAddress1 = "someone_a@example.com" };

// Find related Tasks that need to be updated
List<Task> tasksToUpdate = retrievedAccount.Account_Tasks
    .Where(t => t.Subject.Equals("Example Task")).ToList();

// A list to put the updated tasks
List<Task> updatedTasks = new List<Task>();

//Fill the list of updated tasks based on the tasks that need to but updated
tasksToUpdate.ForEach(t =>
{
    updatedTasks
    .Add(new Task() {
        ActivityId = t.ActivityId,
        Subject = "Updated Subject"
    });

});

//Set the updated tasks to the collection
account.Account_Tasks = updatedTasks;

//Update the account and related contact and tasks
svc.Update(account);
```

## <a name="check-for-duplicate-records"></a>Nach doppelten Datensätzen suchen

Wenn Sie eine Entität aktualisieren, können Sie die Werte änder, damit der Datensatz ein Duplikat für einen anderen Datensatz darstellt. Weitere Informationen: [DoppelteAbfdra Daten mit dem Organisationsdienst erkennen](detect-duplicate-data.md).

## <a name="update-with-alternate-key"></a>Aktualisierung mit Alternativschlüsseln

Wenn Sie über einen Alternativschlüssel verfügen, der für eine Entität definiert wurde, können Sie diesen anstelle des Primärschlüssels verwenden, um einen Datensatz zu aktualisieren. Sie können die früh gebundene Klasse nicht verwendet, um den Alternativschlüssel anzugeben. Sie müssen den Konstruktor [Entity(String, KeyAttributeCollection)](/dotnet/api/microsoft.xrm.sdk.entity.-ctor#Microsoft_Xrm_Sdk_Entity__ctor_System_String_Microsoft_Xrm_Sdk_KeyAttributeCollection_) verwenden, um den Alternativschlüssel anzugeben.

Bei Nutzung von Typen mit früher Bindung können Sie <xref:Microsoft.Xrm.Sdk.Entity> mittels der <xref:Microsoft.Xrm.Sdk.Entity.ToEntity``1>-Methode in eine früh gebundene Klasse konvertieren.

Im folgenden Beispiel wird veranschaulicht, wie Sie eine `Account`-Entität mit einem Alternativschlüssel aktualisieren, der für das Attribut `accountnumber` definiert wurde.

> [!IMPORTANT]
> Standardmäßig sind keine Alternativschlüssel für Entitäten definiert. Diese Methode kann nur verwendet werden, wenn für die Umgebung konfiguriert wird, um einen Alternativschlüssel für eine Entität zu definieren.

```csharp
var accountNumberKey = new KeyAttributeCollection();
accountNumberKey.Add(new KeyValuePair<string, object>("accountnumber", "123456"));

Account exampleAccount = new Entity("account", accountNumberKey).ToEntity<Account>();
exampleAccount.Name = "New Account Name";
svc.Update(exampleAccount);
```

Weitere Informationen: 
- [Arbeiten mit Alternativschlüsseln](../define-alternate-keys-entity.md)
- [Verwenden Sie einen Alternativschlüssel, um Datensätze zu erstellen](../use-alternate-key-create-record.md)

## <a name="use-upsert"></a>Verwendung von Upsert

In der Regel müssen Sie in den Datenenintegrationsszenarien Daten in Common Data Service aus anderen Quellen erstellen oder aktualisieren. Common Data Service verfügt ggf. bereits über Datensätze mit dem gleichen eindeutigen Bezeichner, die möglicherweise ein Alternativschlüssel sind. Wenn ein Entitätsdatensatz vorhanden ist,  möchten Sie diesen aktualisieren. Sollte er nicht vorhanden sein, erstellen Sie ihn, damit die Daten, die hinzugefügt werden, mit den Quelldaten synchronisiert werden. Dies ist erforderlich, wenn Sie upsert verwenden möchten.

Das folgende Beispiel nutzt ein <xref:Microsoft.Xrm.Sdk.Messages.UpsertRequest> zweimal. Das erste Mal, wenn ein Firmaenentitätsdatensatz erstellt wird und im zweiten Importvorgang der Anwendung aktualisiert wird, da er ein Wert `accountnumber` ist und es sich um einen Alternativschlüssel mithilfe dieses Attribut ist.

Bei beiden Anrufe gibt die <xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse>.<xref:Microsoft.Xrm.Sdk.Messages.UpsertResponse.RecordCreated> Eigenschaft an, ob der Vorgang einen Datensatz erstellt oder nicht.

```csharp
// This environment has an alternate key set for the accountnumber attribute.

//Instantiate account entity with accountnumber value
var account = new Entity("account", "accountnumber", "0003");
account["name"] = "New Account";

//Use Upsert the first time
UpsertRequest request1 = new UpsertRequest() {
Target = account
};

//The new entity is created
var response1 = (UpsertResponse)svc.Execute(request1);
Console.WriteLine("Record Created: {0}",response1.RecordCreated); //true

//Update the name of the existing account entity
account["name"] = "Updated Account";

//Use Upsert for the second time
UpsertRequest request2 = new UpsertRequest()
{
Target = account
};

//The existing entity is updated.
var response2 = (UpsertResponse)svc.Execute(request1);
Console.WriteLine("Record Created: {0}", response2.RecordCreated); //false
```
Weitere Informationen: [Einen Datensatz mit Upsert einfügen oder aktualisieren](../use-upsert-insert-update-record.md)

## <a name="delete"></a>Löschen

Im <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> Methode erfordert lediglich den logischen Namen und den eindeutigen Bezeichnerwert und die Entität. Unabhängig davon, ob Sie eine spät gebundene <xref:Microsoft.Xrm.Sdk.Entity> Klasse oder eine früh gebundene Entitätsklasse verwenden, können Sie die folgenden Syntax für einen Löschvorgang verwenden, indem Sie die <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.LogicalName> übergeben und <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Id> Eigenschaften definiert.

```csharp
svc.Delete(retrievedEntity.LogicalName, retrievedEntity.Id);
```
Alternativ können Sie auch dynamische Werte verwenden:
```csharp
svc.Delete("account", new Guid("e5fa5509-2582-e811-a95e-000d3af40ae7"));
```
> [!IMPORTANT]
> Löschen von Vorgängen können untergeordnete Datensätze veranlassen, untergeordnete Datensätze zu löschen, die Datenintegrität abhängig von der für die Beziehungen in Umgebungen definieren. Weitere Informationen: [Verhalten von Entitätsbeziehungen](../../../maker/common-data-service/entity-relationship-behavior.md)

## <a name="use-the-deleterequest-class"></a>Die DeleteRequest-Klasse nutzen

Sie können die <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> anstelle der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> nutzen Methode, aber sie sind nur erforderlich, wenn Sie das optimistischen Parallelität Verhalten angeben möchten.

```csharp
var retrievedEntity = new Entity("account")
{
    Id = new Guid("c81ffd82-cd82-e811-a95c-000d3af49bf8"),
    RowVersion = "986335"

};

var request = new DeleteRequest()
{
    Target = retrievedEntity.ToEntityReference(),
    ConcurrencyBehavior = ConcurrencyBehavior.IfRowVersionMatches
};

svc.Execute(request);
```

## <a name="optimistic-concurrency-behavior"></a> Optimistisches Parallelität Verhalten

Sie können das Verhalten der optimistischen Parallelität für den Vorgang angeben, indem Sie die `ConcurrencyBehavior` angezeigten aus oder <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> aus Klassen<xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> festlegen.

Die Logik, den Datensatzes zu aktualisieren oder zu löschen kann auf veralteten Daten basieren. Wenn die aktuellen Daten sich unterscheiden, da sie geändert wurden, seit sie abgerufen wurden, enthält die optimistische Parallelität eine Möglichkeit, ein Update oder einen Löschvorgang abzubrechen, sodass möglicherweise die Anfrage wiederholt werden kann, um die aktuellen Daten zu nutzen.

Um zu bestimmen ob die Entität geändert wurde, müssen Sie die Werte vergleichen. Sie können die angezeigten <xref:Microsoft.Xrm.Sdk.Entity.RowVersion> verwenden um festzustellen wenn sie geändert wurde.

Das folgende Beispiel wird nur erfolgreich ausgeführt, wenn Folgendes zutrifft:
- Die `RowVersion` In der Entität in den Datenbank ist gleich `986323`
- Die Kontoentität ist für die optimistische Parallelität aktiviert (<xref href="Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsOptimisticConcurrencyEnabled?text=EntityMetadata.IsOptimisticConcurrencyEnabled" /> ist `true`).
- Die `RowVersion`-Eigenschaft wird auf der Entität festgelegt, die der Anfrage übergeben werden.

Wenn `RowVersion` nicht übereinstimmt, tritt ein Fehler mit der `The version of the existing record doesn't match the RowVersion property provided.` Meldung auf.

```csharp
var retrievedAccount = new Account()
{   
    Id = new Guid("a976763a-ba1c-e811-a954-000d3af451d6"), 
    RowVersion = "986323" 
};

var account = new Account();
account.Id = retrievedAccount.Id;
account.RowVersion = retrievedAccount.RowVersion;

// set attribute values
account.CreditOnHold = true;

//Update the account
var request = new UpdateRequest()
{ 
    Target = account,
    ConcurrencyBehavior = ConcurrencyBehavior.IfRowVersionMatches 
};

try
{
    svc.Execute(request);
}
catch (FaultException<OrganizationServiceFault> ex)
{
    switch (ex.Detail.ErrorCode)
    {
        case -2147088254: // ConcurrencyVersionMismatch 
        case -2147088253: // OptimisticConcurrencyNotEnabled 
            throw new InvalidOperationException(ex.Detail.Message);
        case -2147088243: // ConcurrencyVersionNotProvided
            throw new ArgumentNullException(ex.Detail.Message);
        default:
            throw ex;
    }
}
```

Weitere Informationen: 
- [Optimistische Parallelität](../optimistic-concurrency.md)
- <xref href="Microsoft.Xrm.Sdk.ConcurrencyBehavior?text=ConcurrencyBehavior Enum"  />

## <a name="legacy-update-messages"></a>Vorgängerupdatenachrichten

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update -->

Es gibt mehrere veraltete spezialisierte Nachrichten, die Aktualisierungsvorgänge ausführen. In früheren Versionen wurde es erforderlich, um die Nachrichten zu verwenden, aber jetzt können dieselben Vorgänge mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService> <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> ausgeführt werden. oder <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> Klasse  mit<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

[!INCLUDE [cc-legacy-update-messages](../includes/cc-legacy-update-messages.md)]

Weitere Informationen: [Verhalten spezieller Vorgänge mithilfe Update](../special-update-operation-behavior.md)

### <a name="see-also"></a>Siehe auch

[Erstellen von Entitäten mit dem Organisationsservice](entity-operations-create.md)<br />
[Abrufen einer Entität mithilfe des Organisationsdienstes](entity-operations-retrieve.md)<br />
[Entitäten mithilfe des Organisations-Service zuordnen oder trennen](entity-operations-associate-disassociate.md)<br />
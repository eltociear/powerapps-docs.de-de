---
title: Rufen Sie eine Entität ab mithilfe des Organisationsservices (Common Data Service für Apps)| Microsoft Docs
description: 'Beschreibt die Optionen, die verfügbar sind, wenn Sie einen Datensatz programmgesteuert abrufen'
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
# <a name="retrieve-an-entity-using-the-organization-service"></a>Abrufen einer Entität mithilfe des Organisationsdienstes

Sie rufen in der Regel einen Datensatz anhand der Ergebnisse einer Abfrage ab und die Abfrageergebnisse sollten einen eindeutigen Bezeichner für den Entitätsdatensatz enthalten.

> [!NOTE]
> In den folgenden Beispielen steht die `accountid` Variable für den <xref:System.Guid> Bezeichner für einen Firmaenentitätsdatensatz.

Sie haben einige, um die Daten zu definieren, die zurückgegeben werden, wenn Sie einen Entitätsdatensatz abrufen. Sie verwenden die <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>-Klasse, um zu definieren, welche Attributwerte Sie benötigen.


> [!IMPORTANT]
> Wenn Sie Entitätsdatensätze abrufen, sollten Sie die Attributwerte abrufen, die Sie benötigen, um bestimmte Attribute mithilfe von <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> Klassenkonstruktor zu nutzen. Obwohl <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>-Klassenkonstruktor eine Überladung bietet, die einem Booleschen Parameter`allColumns` annimmt, sollten Sie dies im Produktionscode nicht verwenden. Weitere Informationen: [Rufen Sie nicht alle Spalten einer Entität zur Abfrage von APIs ab](/dynamics365/customer-engagement/guidance/data/retrieve-specific-columns-entity-via-query-apis)

Wenn Sie verknüpfte Entitäten zurückgebenmüssen, können Sie eine Abfrage mit Ihre abgerufenen Anforderung definieren, die die verknüpften Datensätze zurückgeben.


## <a name="basic-retrieve"></a>Grundlegende Abfragen

Sie können einzelne Datensätze mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> abrufen Methode bzw. indem Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.Target>-Klasse<xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> auf einen Bezugsdatensatz festlegen und verwenden<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode.

Dies wird im folgenden Beispiel verdeutlicht <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*> Methode.

```csharp
Entity entity = svc.Retrieve("account", accountid, new ColumnSet("name"));
Console.WriteLine("account name: {0}", entity["name"]);
```

Dieses Beispiel zeigt Nutzung der <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> und<xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> Klasse mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode.

```csharp
RetrieveRequest request = new RetrieveRequest()
{
  ColumnSet = new ColumnSet("name"),
  Target = new EntityReference("account", accountid)
};
var response = (RetrieveResponse)svc.Execute(request);
Entity entity = response.Entity;
Console.WriteLine("account name: {0}", entity["name"]);
```

> [!NOTE]
> Meistens verwenden Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService> <xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>  Methode.
>
> Verwenden Sie die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>-Methode. Methode für spezielle Umstände, wie unten beschrieben. 
> Weitere Informationen: 
> - [Abrufen von verknüpften Datensätzen aus](#retrieve-with-related-records)
> - [Abruf mit einem Alternativschlüssel](#retrieve-with-an-alternate-key)


## <a name="retrieve-with-related-records"></a>Abrufen von verknüpften Datensätzen aus

Wenn Sie einen einzelnen Datensatz anzeigen, können Sie auch eine Abfrage darin aufnehmen, um verknüpfte Datensätze einzuschließen, indem Sie die angezeigten <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.RelatedEntitiesQuery> Eigenschaften von <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> festlegen.

Sie können auch eine Abfrage mit der der Klassen definieren, die von erfolgt <xref:Microsoft.Xrm.Sdk.Query.QueryBase> und sie einer bestimmten Entitätsbeziehung zuordnen. Fügen Sie eine Sammlungvon Abfragen und Beziehungen der <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.RelatedEntitiesQuery>-Eigenschaft mithilfe einer <xref:Microsoft.Xrm.Sdk.RelationshipQueryCollection> hinzu.

Das folgende Beispiel enthält `task` und `contact`Datensätze, die sich auf den Entitätsdatensatz `account` beziehen, der abgerufen wird.

```csharp

var relationshipQueryCollection = new RelationshipQueryCollection();

var relatedTasks = new QueryExpression("task");
relatedTasks.ColumnSet = new ColumnSet("subject", "description");
var taskRelationship = new Relationship("Account_Tasks");
relationshipQueryCollection.Add(taskRelationship, relatedTasks);


var relatedContacts = new QueryExpression("contact");
relatedContacts.ColumnSet = new ColumnSet("fullname", "emailaddress1");
var contactRelationship = new Relationship("account_primary_contact");
relationshipQueryCollection.Add(contactRelationship, relatedContacts);

var request = new RetrieveRequest()
{
  ColumnSet = new ColumnSet(true),
  RelatedEntitiesQuery = relationshipQueryCollection,
  Target = new EntityReference("account", accountid)
};

RetrieveResponse response = (RetrieveResponse)svc.Execute(request);

Entity retrievedAccount = response.Entity;

Console.WriteLine("Account Name: {0}",retrievedAccount["name"]);

var tasks = retrievedAccount.RelatedEntities[new Relationship("Account_Tasks")];

Console.WriteLine("Tasks:");
tasks.Entities.ToList().ForEach(x => {
  Console.WriteLine(" Task Subject: {0}",x["subject"]);
});

Entity primaryContact = retrievedAccount
  .RelatedEntities[new Relationship("account_primary_contact")]
  .Entities.FirstOrDefault();

Console.WriteLine("Primary Contact Fullname: {0}",primaryContact["fullname"]);
```
Das Ergebnis des Beispiels könnte wie folgt aussehen:

```
Account Name: City Power & Light (sample)
Tasks:
 Task Subject: Task 1
 Task Subject: Task 2
Primary Contact Fullname: Scott Konersmann (sample)
```

Weitere Informationen: [Abfdragedaten mit dem Organisationsdienst](entity-operations-query-data.md).


## <a name="retrieve-with-an-alternate-key"></a>Abruf mit einem Alternativschlüssel

Wenn Sie eine Entität konfiguriert haben, um einen Alternativschlüssel zu verwenden, können Sie diesen Alternativschlüssel verwenden, um einen zu<xref:Microsoft.Xrm.Sdk.EntityReference> definieren und diesen Wert als <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest> den <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.Target> zu verabschieden. -Eigenschaft verfügbar.

Wenn Sie zum Beispiel das Attribut `account``accountnumber`definieren, um ein Alternativschlüssel zu erhalten, können Sie ein Konto mithilfe des Werts dieses Attributs abrufen.


```csharp
RetrieveRequest request = new RetrieveRequest()
{
ColumnSet = new ColumnSet("name"),
Target = new EntityReference("account", "accountnumber", "0001")
};
var response = (RetrieveResponse)svc.Execute(request);
Entity entity = response.Entity;

Console.WriteLine(entity["name"]);
```

Wenn der Alternativschlüssel eine Zusammensetzung einiger Attribute ist, müssen Sie eine <xref:Microsoft.Xrm.Sdk.KeyAttributeCollection> definieren. Das folgende Beispiel ist für eine Firmaenentität, die üer einen Alternativschlüssel verfügt, der sowohl `accountnumber` und `sic` Attribute enthält.

```csharp
var keyCollection = new KeyAttributeCollection();
keyCollection.Add("accountnumber", "0001");
keyCollection.Add("sic", "7372");

RetrieveRequest request = new RetrieveRequest()
{
ColumnSet = new ColumnSet("name"),
Target = new EntityReference("account", keyCollection)
};
var response = (RetrieveResponse)svc.Execute(request);
Entity entity = response.Entity;

Console.WriteLine(entity["name"]);
```
> [!NOTE]
> Alternativschlüssel werden in der Regel nur für Datenenintegrationsszenarien verwendet


## <a name="access-formatted-values"></a>Zugriff formatierte Werte

Die Methode, um formattierte Werte in einem Abrufensvorgang abzurufen ist gleich, wie wenn Sie auf die Ergebnisse in einer Abfrage zugreifen. Weitere Informationen:[Zugriff auf formattierte Werte](entity-operations-query-data.md#access-formatted-values)

<!-- TODO Move the information about accessing formatted values here, where the topic is shorter rather than the query topic which is longer -->

### <a name="see-also"></a>Siehe auch

[Erstellen von Entitäten mit dem Organisationsservice](entity-operations-create.md)<br />
[Aktualisieren und Löschen von Entitäten mit dem Organisationsservice](entity-operations-update-delete.md)<br />
[Entitäten mithilfe des Organisations-Service zuordnen oder trennen](entity-operations-associate-disassociate.md)<br />

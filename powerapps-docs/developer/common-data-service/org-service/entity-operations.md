---
title: Entitätsvorgänge mithilfe des Organisationsservices (Common Data Service für Apps)| Microsoft Docs
description: 'Lernen Sie die Entitätsklasse, die für Datenenvorgänge verwendet wird, die mithilfe der CDS für App-Organisationsservice verwendet wird'
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
# <a name="entity-operations-using-the-organization-service"></a>Entitäts-Vorgänge mithilfe des Organisationsservice

Wenn Sie mit Common Data Service for Apps Daten mithilfe des Organisationsservice arbeiten,  verwenden Sie die -<xref:Microsoft.Xrm.Sdk.Entity>-Klasse mit später Bindung oder mit erstellten Entitätsklassen mithilfe früher Bindung. Die erstellten Entitätsklassen erben von der <xref:Microsoft.Xrm.Sdk.Entity> Klasse, deshalb ist das Verstehen der <xref:Microsoft.Xrm.Sdk.Entity> Klasse für jeden Stil wichtig.

In diesem Kapitel werden einige der am häufigsten verwendeten Eigenschaften und Methoden der <xref:Microsoft.Xrm.Sdk.Entity>-Klasse beschrieben.

## <a name="entitylogicalname"></a>Logischer Entitätsname

Wenn Sie eine neue Instanz <xref:Microsoft.Xrm.Sdk.Entity> mithilfe der späten Bindung erstellen, legen Sie einen gültigen Zeichenfolgenwert bereit, um anzuzeigen, welcher Typ die Entität ist. Der `LogicalName` ist in den Entitätsmetadaten definiert.

Wenn Sie die frühe Bindung verwenden, ist dieser Wert vom Konstruktor der Webressourcen generierten Klasse festgelegt. Beispiel: `var account = new Entity("account");`

In Ihrem Code wenn Sie später den Zeichenfolgenwert abrufen möchten, der den Entitätstyp beschreibt, können Sie die <xref:Microsoft.Xrm.Sdk.Entity.LogicalName> Eigenschaft verwenden. Dies ist für die vielen APIs hilfreich, die einen logischen Entitätsnamen als Parameter erfordern.

## <a name="entityid"></a>Entitäts.ID

Wenn Sie eine Entitätsinstanz instanziieren, ob mithilfe einer späten oder frühen Bindung, gibt es keine eindeutige festgelegte ID. Wenn Sie eine Entität erstellen, möchten Sie sie nicht festlegen, können jedoch vom System festgelegt werden beim Erstellen (Speichern).

Wenn Sie eine Entität abrufen, ist ein Primärschlüsselattributwert enthalten, ob sie diesen angefordert haben oder nicht. Der Primärschlüsselattributname ist für jeden Entitätstyp unterschiedlich. Generell ist der Name des Primärschlüsselattributs die Entität `logicalname` + `id`. Für eine Firmaenentität ist es `accountid` und für einen Kontakt ist es `contactid`.

Wenn Sie den Primärschlüsselwert mithilfe des Primärschlüsselattributs abrufen oder festlegen, kann die  <xref:Microsoft.Xrm.Sdk.Entity.Id> Eigenschaft auch verwendet werden, um auf den Wert zuzugreifen, ohne dass Sie sich an den Namen des Primärschlüsselattributs erinnern müssen.

## <a name="early-bound-access-to-attributes"></a>Früh gebundener Zugriff zu Attributen

Wenn Sie die frühe Bindung verwenden, um Klassen zu erstellen, finden Sie typisierte Eigenschaften für jedes Attribut in der Klasse. Die Eigenschaften für die Attribute verwenden <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> und sie können direkt auf der Entitätsinstanz zugegriffen werden.
Beispiel: 


```csharp
//Using the early-bound Account entity class
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
```

## <a name="late-bound-access-to-attributes"></a>Späte gebundener Zugriff zu Attributen

Die Daten, die in einer einzelnen Entität enthalten sind in <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Attributes> -Eigenschaft verfügbar. Diese Eigenschaft ist ein <xref:Microsoft.Xrm.Sdk.AttributeCollection>, die einen ganzen Satz Methoden bereitstellt, um neue Attribute hinzuzufügen und zu überprüfen, ob ein Attribut vorhanden ist ode zum Entfernen von Attributen.

### <a name="discover-attribute-names-and-data-types"></a>Erkunden Sie Attributnamen und Datentypen

Bei späten Bindunghen müssen Sie die <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LogicalName><xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata> kkennen für Attribute und Datentyp. Der `LogicalName` Ist die kleingeschriebene Version von `SchemaName`. Sie erkunden und tippen `LogicalName` für Attribute auf unterschiedliche Arten ein:

- Zeigen Sie die Definition des Attributs in den Anpassungstools an
- Für Systementitäten können Sie die [Entitätsreferenz](../reference/about-entity-reference.md) überprüfen
- Nutzen Sie ein Tool, umd die Metadaten nach Entitäten zu durchsuchen, wie Metadaten-Browser, beschrieben in [Durchsuchen der Metadaten für Ihre Organisation](../browse-your-metadata.md)

Attributtypen können die folgenden sein:

|Typ|Beschreibung|
|--|--|
|<xref:Microsoft.Xrm.Sdk.EntityReference>|Ein **Such**-Aztribut. Ein Link zu einem anderen Datensatz.|
|<xref:Microsoft.Xrm.Sdk.BooleanManagedProperty>|Verwendet nur für Entitäten, die Lösungskomponenten sind, wie [WebResource-Entität](../reference/entities/webresource.md). Weitere Informationen: [Bearbeiten von verwalteten Eigenschaften](../use-managed-properties.md)|
|<xref:Microsoft.Xrm.Sdk.Money>|Ein Attribut **Währung**.|
|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|Ein Attribut **Optionssatz** **Status**- und **Status**-Attribute verwenden auch diesen Typ. |
|<xref:System.Boolean>|Ein Attribut **Zwei Option**.|
|<xref:System.Byte>[]|Ein Attribut **Bild**. Jede Entität kann über ein Bildattribut verfügen und das Attribut nennt sich `entityimage`. Eine URL, um das Bilds herunterzuladen. kann in einem Begleitattribut abgerufen werden namens `entityimage_url`. Weitere Informationen [Bildattribute](../image-attributes.md) |
|<xref:System.DateTime>|Ein Attribut **Datum und Uhrzeit** verwendet UTC-Wert. Weitere Informationen: [Verhalten und Format des Datums- und Uhrzeitattributs](../behavior-format-date-time-attribute.md)|
|<xref:System.Decimal>|Ein **Dezimalzahl** Attribut.|
|<xref:System.Double>|Ein Attribut **Gleitkommazahl**.|
|<xref:System.Guid>|Normalerweise wird der eindeutige Bezeichner für die Entität verwendet. |
|<xref:System.Int32>|Ein **Ganzzahl** Attribut.|
|<xref:System.String>|**Mehrere Textzeilen** und **Einzelne Textzeile** Attribute verwenden Sie diesen Typ.|



Es gibt drei unterschiedliche Arten, mit Entitätsattributen mithilfe der späten Bindung zu interagieren:
- Verwenden Sie den Index der Entität.
- Verwenden Sie den Index in der `Attributes` Sammlung
- Verwenden Sie die vorhandenen Entitätsmethoden

### <a name="use-the-indexer-on-the-entity"></a>Verwenden Sie den Index der Entität.

In den meisten Fällen können Sie mithilfe der späten Bindung mit der Sammlung interagieren, indem Sie den Indexer verwenden, um den Wert eines Attributs mithilfe des `LogicalName` für das Attribut festzulegen. Beispielsweise um das Namensattribut einer Firma festzulegen:

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
```

### <a name="use-the-indexer-on-the-attributes-collection"></a>Verwenden Sie den Index in der Attribut-Sammlung

Gelich wie Sie dies für die Entität tun würden, können Sie auch auf einen Wert zugreifen, indem Sie den Index in der Attributsammlung verwenden.

```csharp
string accountName = account.Attributes["name"];
```

### <a name="use-the-entity-methods"></a>Verwenden Sie die vorhandenen Entitätsmethoden

Sie können auch <xref:Microsoft.Xrm.Sdk.Entity> Methoden verwenden, um den Attributwerte festzulegen oder abzurufen.

|Methode|Beschreibung|
|--|--|
|<xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)>|Verwenden Sie diesen Antworttyp, um einen typisierten Attributwert zurückzugeben|
|<xref:Microsoft.Xrm.Sdk.Entity.SetAttributeValue(System.String,System.Object)>|Verwenden Sie dies,  um einen typisierten Attributwert zurückzugeben|

Beispiel:

```csharp
account.SetAttributeValue("name", "Account Name");
var accountName = account.GetAttributeValue<string>("name");
```



## <a name="entityformattedvalues"></a>Entity.FormattedValues

Jeder Entitätsattributwert, der in der Benutzeroberfläche angezeigt wird und keine Zeichenfolgen ist, hat einen Zeichenfolge formatierten Wert, der verwendet werden kann, um den Wert auf der Benutzeroberfläche anzuzeigen. Beispiel:

- Geldbeträge haben Zeichenfolgenwert mit der entsprechenden Genauigkeits- und Währungsformatierung.
- Datumswerte haben Formatierungen, die festgelegt sind abhängig davon, wie das System konfiguriert wird
- OptionSet-Werte zeigen die lokalisierte Beschriftung an, die den ganzzahligen Wert darstellt

> [!NOTE]
> Formatierte Werte werden ausschließlich auf Entitäten angewendet, die abgerufen wurden. Nachdem Sie den Wert festgelegt haben, wird kein neuer WErt kalkuliert, bis Sie die Entität speichern und die Entität erneut abrufen. Der formatierte Wert wird auf dem Server erstellt.

Sie können auf die Werte mithilfe der Sammlung <xref:Microsoft.Xrm.Sdk.Entity.FormattedValues> mithilfe eines Indexers oder mit der Entitätsmethode zugreifen<xref:Microsoft.Xrm.Sdk.Entity.GetFormattedAttributeValue(System.String)>.

Beispielsweise haben beide denselben formatierten Wert:

```csharp
var formattedRevenueString1 = account.FormattedValues["revenue"];
var formattedRevenueString2 = account.GetFormattedAttributeValue("revenue");
```

Weitere Informationen:[Zugriff auf formattierte Werte](entity-operations-query-data.md#access-formatted-values)

## <a name="entityrelatedentities"></a>Entity.RelatedEntities 

Wenn Sie eine Entität erstellen, können Sie einen Satz verknüpfte Entitätsdatensätze ebenfalls definieren, um im gleichen Vorgang zu erstellen. Weitere Informationen: [Erstellen verknüpfter Entitäten in einem Vorgang](entity-operations-create.md#create-related-entities-in-one-operation)

Wenn Sie eine Entität abrufen, können Sie die Verwendung verfassen, die wird <xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest>, indem Sie eine<xref:Microsoft.Xrm.Sdk.Messages.RetrieveRequest.RelatedEntitiesQuery>-Abfrage einrichten, um verknüpfte Entitäten in Abfrageergebnissen einzuschließen. Weitere Informationen: [Abrufen von verknüpften Datensätzen](entity-operations-retrieve.md#retrieve-with-related-records)

Wenn Sie verknüpfte Entitäten in Abfrageergebnissen einschließen, können Sie diese Werte in verknüpften Entitäten aktualisieren und sie auch schließen, wenn Sie die Entität aktualisieren. Weitere Informationen: [Aktualisieren verknüpfter Entitäten in einem Vorgang](entity-operations-update-delete.md#update-related-entities-in-one-operation)

## <a name="convert-to-an-entityreference"></a>In eine EntityReference konvertieren

Viele Nachrichteneigenschaften benötigen nur eine <xref:Microsoft.Xrm.Sdk.EntityReference> Verwenden Sie die <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.ToEntityReference> Methode, um einer Entität zu einer Entitätsreferenz zu konvertieren.

## <a name="convert-to-an-entity-class"></a>In eine Entitätklasse konvertieren

Wenn Sie eine frühe Bindung verwenden, müssen Sie die Instanz <xref:Microsoft.Xrm.Sdk.Entity> in den Typ der generierten Entitätsklasse konvertieren, die Sie verwenden. Dies kann in der Regel mit einer Schnittstelle erfolgen, aber Sie können auch die <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.ToEntity``1> verwenden Methode.

```csharp
Account account1 = (Account)retrievedEntity;
Account account2 = retrievedEntity.ToEntity<Account>();
```

> [!NOTE]
> Diese Methode kann nicht verwendet werden, um eine generierte Entitätsinstanz in eine andere Klasse oder <xref:Microsoft.Xrm.Sdk.Entity> zu konvertieren. Sie können nur verwendet werden, um eine Instanz <xref:Microsoft.Xrm.Sdk.Entity> zu einer der Webressourcen generierte Klassen zu konvertieren, die von diesen erben. Wenn die <xref:Microsoft.Xrm.Sdk.Entity>-Instanz nicht wirklich eine Instanz der Webressourcen generierte Klasse ist, löst diese Nachricht ein Fehler aus.

## <a name="next-steps"></a>Nächste Schritte

Diese Themen erklären mehr über das Arbeiten mit CDS für App-Entitäten.

[Schnellstart: Organisationsservicebeispiel C#](quick-start-org-service-console-app.md)
[Abfragedaten](entity-operations-query-data.md)<br />
[Entitäten erstellen](entity-operations-create.md)<br />
[Eine Entität abrufen](entity-operations-retrieve.md)<br />
[Entitäten aktualisieren und löschen](entity-operations-update-delete.md)<br />
[Entitäten zuordnen und ihre Zuordnung aufheben](entity-operations-associate-disassociate.md)<br />
[Generieren Sie Klassen für früh gebundene Programmierung](generate-early-bound-classes.md)<br />
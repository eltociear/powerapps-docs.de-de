---
title: Abfragen von Daten mit dem Organisationsdienst (Common Data Service) | Microsoft-Dokumentation
description: Stellt die verschiedenen Arten vor, Daten mithilfe von Common Data Service-SDK-Assemblies abzufragen.
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 2fd09284e99a11ad55625d63a30975c36164a7bd
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748546"
---
# <a name="query-data-using-the-organization-service"></a>Daten abfragen mithilfe des Organisation-Service

Die SDK-Assemblys für den Organisationsservice stellt einige Stile zum Abfragen von Daten bereit. Jede hat verschiedene Vorteile.

|Formatvorlage|Vorteile|
|--|--|
|[FetchExpression](#use-fetchxml-with-fetchexpression)|Verwenden Sie cie Eigenschaft FetchXML zur Erstellung von Abfragen, die Aggregate zurückgeben, wie etwa die Summe eines Wertes für alle zurückgegebenen Datensätze. Sie können mit FetchXML auch Gruppierungsvorgänge ausführen. Können Daten aus verknüpften Entitäten umfassen.|
|[QueryExpression](#use-queryexpression)|Sie haben ein stark typisiertes Objektmodell, um komplexer Abfragen zu erstellen. Unterstützt alle FetchXML-Funktionen, ausgenommen Aggregate und Gruppierung. Können Daten aus verknüpften Entitäten umfassen.|
|[QueryByAttribute](#use-querybyattribute)|Ein einfacheres Objektmodel als`QueryExpression` Verwendung von `QueryByAttribute` für Abfragen, in denen Sie testen, ob die Attributwertkriterien in Ihrer Abfrage eine Übereinstimmung haben. Können Daten von der Entität nur zurückgeben.|
|[LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq)|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.QueryProvider> vverwenden. zum Abfragen mithilfe der gängigen LINQ-Syntax verfassen. Alle LINQ-Abfragen werden konvertiert werden,<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> um die von Ihnen verwendeten Funktionen zu beschränken, die verfügbar sind `QueryExpression` <br /> In diesem Artikel stehen die Stile von Abfragen im Mittelpunkt, die zu SDK-Assemblyklassen verfügbar sind. Weitere Informationen: [Erstellen von Abfragen mit LINQ (.NET Sprache integrierte Abfrage)](build-queries-with-linq-net-language-integrated-query.md)|


<xref:Microsoft.Xrm.Sdk.Query.FetchExpression>, <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, znd <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> stammen von <xref:Microsoft.Xrm.Sdk.Query.QueryBase> abstrakten Klassen. Es gibt zwei Möglichkeiten, um Ergebnisse einer Abfrage anzuzeigen, die mit dieser Klassen definiert wird:

- Sie können eine dieser Instanz Klassen als `query` Parameter für <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> nutzen Methode.
- Sie können die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query> Eigenschaft der  <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> Klasse und die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> nutzen Methode.

> [!NOTE]
> Im <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> Methode wird grundsätzlich bevorzugt. Es sind keine speziellen Funktionen, für die die Verwendung von  <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> Klassen ist.

Beide Möglichkeiten geben <xref:Microsoft.Xrm.Sdk.EntityCollection> zurück, das die Ergebnisse der Abfrage in der Sammlung<xref:Microsoft.Xrm.Sdk.EntityCollection.Entities> und in den Eigenschaften enthält, um zusätzliche Abfragen zu verwenden, um ausgelagerte Ergebnisse zu erhalten. 

> [!NOTE]
> Um eine bestmögliche Leistung sicherzustellen, kann jede Abfragenanforderung ein Maximum von 5000 Entitäten führen. Um zum größeren Resultatset zurückzugeben müssen Sie weitere Seiten anfordern.

### <a name="null-attribute-values-are-not-returned"></a>Ungültige Attributwerte werden nicht zurückgegeben

Wenn ein Attribut einem NULL-Wert enthält, oder wenn das Attribut vom FetchXml-Attributen enthalten war <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>, das<xref:Microsoft.Xrm.Sdk.Entity> <xref:Microsoft.Xrm.Sdk.Entity.Attributes> Sammlung enthält nicht das Attribut. Es gibt keinen Schlüssel, um darauf zuzugreifen oder zurückzugeben. Das Fehlen des Attributs gibt an, dass es Null ist. Wenn die frühe Biondung verwendet wird, verwaltet die generierte Entitätsklasseneigenschaften dies und gibt einen Null-Wert zurück.

Wenn die späte Bindung verwendet wird, wenn Sie versuchen, den Wert mit einem Indexers auf <xref:Microsoft.Xrm.Sdk.Entity.Attributes> oder<xref:Microsoft.Xrm.Sdk.Entity.FormattedValues> zuzugreifen, erhalten Sie eine `The given key was not present in the dictionary`mit der Message <xref:System.Collections.Generic.KeyNotFoundException> angezeigt.

Um dieses Problem zu vermeiden, wenn Sie die späte Bindung nutzen, können Sie zwei Strategien verwenden:

1. Ein Attribut, das nicht zulässig sein kann, verwenden den<xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.Contains(System.String)> Methode, um zu überprüfen, ob das Attribut, das mit einem Indexer zuzugreift, ungültig ist. Beispiel:

    `Money revenue = (entity.Contains("revenue")? entity["revenue"] : null);`

1. <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)> vverwenden. um auf den Wert zuzugreifen. Beispiel:

    `Money revenue = entity.GetAttributeValue<Money>();`

  > [!NOTE]
  > Wenn der Typ, der angegeben ist in <xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)>ein Werttyp ist, der nicht gültig sein kann, wie <xref:System.Boolean> oder <xref:System.DateTime> Wert, der zurückgesendet wird, der  Standardwert ist, wie `false` oder`1/1/0001 12:00:00 AM` eher als Null.




## <a name="use-fetchxml-with-fetchexpression"></a>Verwendung von FetchXML mit FetchExpression

FetchXml ist eine proprietäre XML-basiert Abfragesprache, die mit SDK Assemblyabfragen mithilfe von <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> und durch die WEB API mithilfe einer Abfragezeichenfolge `fetchXml` verwendet werden kann. Weitere Informationen: [WEB API: Abrufen von vordefinierte Abfragen > Benutzerdefiniertes FetchXML verwenden](../webapi/retrieve-and-execute-predefined-queries.md#use-custom-fetchxml)

Das folgende Beispiel veranschaulicht eine einfache Abfrage, um bis zu 50 passenden Firmaenentitäten  zurückzugeben, wenn der `address1_city` Wert `Redmond` entspricht, bestellte von `name`.

```csharp
string fetchXml = @"
<fetch top='50' >
  <entity name='account' >
    <attribute name='name' />
    <filter>
      <condition 
        attribute='address1_city' 
        operator='eq' 
        value='Redmond' />
    </filter>
    <order attribute='name' />
  </entity>
</fetch>";

var query = new FetchExpression(fetchXml);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x => {
  Console.WriteLine(x.Attributes["name"]);
});
```

> [!IMPORTANT]
> Wenn Sie Entitätsdatensätze abrufen, sollten Sie nur die Attributwerte abrufen, die Sie benötigen, indem Sie die einzelnen Attributen mit den `attribute` Elementen und nicht mit den `all-attributes` Elementen nutzen, um alle Attribute zurückzugeben.


Weitere Informationen:
- [Verwenden von FetchXML zum Erstellen einerAbfrage](../use-fetchxml-construct-query.md)
- [FetchXML-Schema](../fetchxml-schema.md)
- [Auslagern von umfangreichen Ergebnissätzen mit FetchXML](page-large-result-sets-with-fetchxml.md)
- [FetchXML-Aggregation verwenden](../use-fetchxml-aggregation.md)
- [Steuerdatum und "älter als"-Datums-/Zeit-Abfrageoperatoren in FetchXML](../use-fetchxml-fiscal-date-older-datetime-query-operators.md)
- [Verwenden einer linken äußeren Verknüpfung in FetchXML für Abfragen nach Datensätzen, die „nicht in“ sind.](../use-fetchxml-left-outer-join-query-records-not-in.md)
- [Beispiel: Verwendung von Aggregation in FetchXML](samples/use-aggregation-fetchxml.md)
- [Beispiel: Verwenden von FetchXML mit einem Auslagerungscookie](samples/use-fetchxml-paging-cookie.md)

## <a name="use-queryexpression"></a>QueryExpression nutzen

Diese <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Klasse stellt einen Satz stark typisierter Objekte dar, die für Ablaufmanipulation von Abfragen optimiert wird.

Das folgende Beispiel veranschaulicht eine einfache Abfrage, um bis zu 50 passenden Firmaenentitäten  zurückzugeben, wenn der `address1_city` Wert `Redmond` entspricht, bestellte von `name`.

```csharp
var query = new QueryExpression("account")
{
  ColumnSet = new ColumnSet("name"),
  Criteria = new FilterExpression(LogicalOperator.And),
  TopCount = 50
};
query.Criteria.AddCondition("address1_city", ConditionOperator.Equal, "Redmond");
query.AddOrder("name", OrderType.Ascending);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x =>
{
  Console.WriteLine(x.Attributes["name"]);
});
```

> [!IMPORTANT]
> Wenn Sie Entitätsdatensätze abrufen, sollten Sie die Attributwerte abrufen, die Sie benötigen, um bestimmte Attribute mithilfe von <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> Klassenkonstruktor zu nutzen. Obwohl <xref:Microsoft.Xrm.Sdk.Query.ColumnSet>-Klassenkonstruktor eine Überladung bietet, die einem Booleschen Parameter`allColumns` annimmt, sollten Sie dies im Produktionscode nicht verwenden.


Weitere Informationen:
- [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)
- [Auslagern von umfangreichen Ergebnissätzen mit QueryExpression](page-large-result-sets-with-queryexpression.md)
- [Verwenden der QueryExpression-Klasse](use-queryexpression-class.md)
- [Verwenden der ConditionExpression-Klasse](use-conditionexpression-class.md)
- [Verwenden der ColumnSet-Klasse](use-the-columnset-class.md)
- [Die FilterExpression-Klasse verwenden](use-filterexpression-class.md)
- [Beispiel: Rufen Sie mit der QueryExpressions-Klasse Vielfaches ab](samples/retrieve-multiple-queryexpression-class.md)
- [Beispiel: Verwenden von QueryExpression mit einem Auslagerungscookie](samples/use-queryexpression-with-a-paging-cookie.md)

## <a name="use-querybyattribute"></a>QueryByAttribute nutzen

Diese <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>-Klasse stellt einen Satz stark typisierter Objekte dar, die für Ablaufmanipulation von einfachen Abfragen einer Enität optimiert wird. Anders als FetchXML und `QueryExpression`, `QueryByAttribute` können Daten nur in der Entität zurückgegeben werden. Dies aktiviert nicht das Abrufen von Daten aus verknüpften Entitäten oder von komplexen Abfragekriterien.

Das folgende Beispiel veranschaulicht eine einfache Abfrage, um bis zu 50 passenden Firmaenentitäten  zurückzugeben, wenn der `address1_city` Wert `Redmond` entspricht, bestellte von `name`.

```csharp
var query = new QueryByAttribute("account")
{
  TopCount = 50,
  ColumnSet = new ColumnSet("name")
};
query.AddAttributeValue("address1_city", "Redmond");
query.AddOrder("name", OrderType.Ascending);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x =>
{
  Console.WriteLine(x.Attributes["name"]);
});
```

Weitere Informationen:
- [Verwenden der QueryByAttribute-Klasse](use-querybyattribute-class.md)
- [Beispiel: Abruf von Vielfachen mit der QueryByAttribute-Klasse](samples/retrieve-multiple-querybyattribute-class.md)


## <a name="access-formatted-values"></a>Zugriff auf formatierte Werte

Unabhängig von der Datenpräsentation, die Sie verwenden, um die Daten abzufragen, werden die Daten als <xref:Microsoft.Xrm.Sdk.EntityCollection> <xref:Microsoft.Xrm.Sdk.EntityCollection.Entities> zurückgegeben werden. Sie können auf die Attributdatenwerte mit <xref:Microsoft.Xrm.Sdk.Entity><xref:Microsoft.Xrm.Sdk.Entity.Attributes> zugreifen. Sammlung Aber diese Werte können vom Typ als Zeichenfolge, die Sie bearbeiten möchten abhängen, um Zeichenfolgenwerte abzurufen, die Sie in der Anwendung anzeigen möchten.

Sie können auf eichenfolgenwerte zugreifen, die die Umgebungseinstellungen zum Formatieren verwenden, da Werte im <xref:Microsoft.Xrm.Sdk.Entity>.<xref:Microsoft.Xrm.Sdk.Entity.FormattedValues> verwendet werden Sammlung

Im folgenden Beispiel wird gezeigt, wie Sie auf die gesammelten formatierten Zeichenfolgenwerte für die folgenden Firmaenattribute zugreifen:

|Logischer Name des Attributs|Typ|
|--|--|
|`primarycontactid`|<xref:Microsoft.Xrm.Sdk.EntityReference>|
|`createdon`|<xref:System.DateTime>|
|`revenue`|<xref:Microsoft.Xrm.Sdk.Money>|
|`statecode`|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|

```csharp
var query = new QueryByAttribute("account")
{
TopCount = 50,
ColumnSet = new ColumnSet("name", "primarycontactid", "createdon", "revenue", "statecode")
};
query.AddAttributeValue("address1_city", "Redmond");
query.AddOrder("name", OrderType.Ascending);

EntityCollection results = svc.RetrieveMultiple(query);

results.Entities.ToList().ForEach(x =>
{
Console.WriteLine(@"
name:{0}
primary contact: {1}
created on: {2}
revenue: {3}
status: {4}",
  x.Attributes["name"],
  (x.Contains("primarycontactid")? x.FormattedValues["primarycontactid"]:string.Empty),
  x.FormattedValues["createdon"],
  (x.Contains("revenue") ? x.FormattedValues["revenue"] : string.Empty),
  x.FormattedValues["statecode"]
  );
});
```

> [!NOTE]
> Attribute, die Null-Werte enthalten, werden nicht in `Attributes` oder `FormattedValues` Sammlungen zurückgegben. Wenn ein Attribut einen NULL-Wert enthält, sollten Sie mit <xref:Microsoft.Xrm.Sdk.Entity.Contains*> dier Funktionsweise überprüfen, bevor Sie auf den Wert zugreifen.

Die formattierten Ergebnisse werden wie folgt angezeigt:

```
name:A Datum (sample)
  primary contact: Rene Valdes (sample)
  created on: 2/28/2018 11:04 AM
  revenue: $10,000.000
  status: Active

name:City Power & Light (sample)
  primary contact: Scott Konersmann (sample)
  created on: 2/28/2018 11:04 AM
  revenue: $100,000.000
  status: Active

name:Contoso Pharmaceuticals (sample)
  primary contact: Robert Lyon (sample)
  created on: 2/28/2018 11:04 AM
  revenue: $60,000.000
  status: Active
```


## <a name="convert-queries-between-fetchxml-and-queryexpression"></a>Konvertieren von Abfragen zwischen FetchXML und QueryExpression

Sie können <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> Abfrage zu FetchXml und FetchXml Abfragen zu  QueryExpression konvertieren mithilfe der <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> und <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest> Klassen.

Die [SavedQuery](../reference/entities/savedquery.md) Entität enthält Systemansichten für eine Entität und die [UserQuery](../reference/entities/userquery.md) Entität speichert Benutzeranfragen. Andere Entitäten können auch eine Abfrage als FetchXml-Zeichenfolge speicher. Diese Methoden aktivieren das Konvertieren einer FetchXml-Zeichenfolge zu,<xref:Microsoft.Xrm.Sdk.Query.QueryExpression> um sie kann mithilfe des Objektmodells bearbeitet werden und dann wieder in FetchXml konvertiert werden, um als Zeichenfolge kann sie gespeichert werden.


Weitere Informationen: [Beispiel: Konvertieren von Abfragen zwischen Fetch und QueryExpression](samples/convert-queries-fetch-queryexpression.md)



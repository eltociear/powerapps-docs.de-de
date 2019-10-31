---
title: 'Beispiel: Abfrage in der Vorbereitungsphase ändern (Common Data Service) | Microsoft Docs'
description: 'Dieses Beispiel zeigt, wie man ein Plug-in schreibt, das eine Abfrage ändert, die im PreOperation-Stadium einer RetrieveMultiple-Anfrage definiert ist.'
ms.custom: ''
ms.date: 09/23/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: samples
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="sample-modify-query-in-preoperation-stage"></a>Beispiel: Abfrage in der Phase PreOperation ändern

Dieses Beispiel zeigt, wie man ein Plug-in schreibt, das eine Abfrage ändert, die innerhalb der `PreOperation`-Phase einer `RetrieveMultiple`-Abfrage definiert ist.

Die Datenfilterung in einem Plug-in erfolgt in der Regel in der Phase `PostOperation`. Die <xref:Microsoft.Xrm.Sdk.EntityCollection.Entities>-Daten können untersucht werden und Entitäten, die nicht zurückgegeben werden sollen, werden aus der Sammlung entfernt. Dieses Beispiel führt jedoch zu Problemen, bei denen die Anzahl der auf einer Seite zurückgegebenen Datensätze möglicherweise nicht mit der erwarteten Seitengröße übereinstimmt.

Der in diesem Beispiel beschriebene Ansatz ist anders. Anstatt Objekte nach dem Abruf zu filtern, übernimmt dieses Plug-in Änderungen an der Abfrage im Schritt `PreOperation`, bevor sie ausgeführt wird. 

Ein wichtiger Punkt, der durch dieses Beispiel demonstriert wird, ist, dass die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest.Query> einer von drei verschiedenen Typen sein kann, die von der <xref:Microsoft.Xrm.Sdk.Query.QueryBase> abgeleitet sind. Um Abfragen jeglicher Art zu ermöglichen, muss der Plugin-Code die Art der Abfrage erkennen und den entsprechenden Filtertyp implementieren.

Sie können das Beispiel von [hier](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/orgsvc/C%23/RetrieveMultipleAccountPreOperation) herunterladen.

## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

1. Um eine lokale Kopie zu erhalten, laden Sie den [Beispielbericht](https://github.com/Microsoft/PowerApps-Samples) herunter, oder klonen Sie ihn. Dieses Beispiel befindet sich unter PowerApps-Samples-master\cds\orgsvc\C#\RetrieveMultipleAccountPreOperation.
1. Öffnen Sie die Beispiellösung in Visual Studio, navigieren Sie zu den Eigenschaften des Projekts und vergewissern Sie sich, dass die Assembly während des Builds signiert wird. Drücken Sie F6, um die Assembly des Beispiels zu erstellen (RetrieveMultipleAccountPreOperation.dll).
1. Führen Sie das Plug-in-Registrierungstool aus und registrieren Sie die Baugruppe in der Sandbox und Datenbank des Servers Common Data Service für die Phase `PreOperation` der Nachricht `RetrieveMultiple` für die Entität `Account`. 
1. Verwenden Sie eine App oder einen Schreibcode, um Konten abzurufen, um das Plug-in zu aktivieren. Siehe [Code, um dieses Beispiel zu testen](#code-to-test-this-sample) unten für ein Beispiel.
1. Wenn Sie mit dem Testen fertig sind, heben Sie die Registrierung der Assembly auf und gehen Sie wie folgt vor.

## <a name="what-this-sample-does"></a>Funktionsweise:

Nach der Ausführung stellt das Plug-in sicher, dass inaktive Kontendatensätze für die gängigsten Abfragetypen nicht zurückgegeben werden: <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> und <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>.

<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> ist eine dritte Art von Abfrage, die ebenfalls verwendet werden kann. Es unterstützt keine komplexen Abfragen und daher kann mit dieser Methode keine komplexe Filterung angewendet werden. Glücklicherweise wird diese Art der Abfrage nicht häufig verwendet. Sie können solche Anfragen ablehnen, indem Sie in der Stufe `PreValidation` eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> werfen.

## <a name="how-this-sample-works"></a>Wie dieses Beispiel funktioniert

Um das unter [Was macht dieses Beispiel](#what-this-sample-does), beschriebene Szenario zu simulieren, geht das Beispiel wie folgt vor:

1. Sicherstellen, dass die Eingabeparameter einen Parameter mit dem Namen `Query` enthalten.
1. Testen Sie den Typ der Abfrage, indem Sie versuchen, sie als einen der drei erwarteten Typen zu behandeln.
1. Je nach Art der Abfrage wird die Abfrage wie folgt geändert:

### <a name="fetchexpression"></a>FetchExpression

1. Parsen Sie den Wert <xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query>, der die FetchXml enthält, in eine <xref:System.Xml.Linq.XDocument>.
1. Stellen Sie sicher, dass das `entity` Element `attribute` Attribut die Entität `account` angibt.
1. Untersuchen Sie alle `filter`-Elemente in der Abfrage auf Bedingungen, die das Attribut `statecode` testen.
1. Entfernen Sie alle vorhandenen Bedingungen, die auf diesem Attribut basieren.
1. Fügen Sie der Abfrage eine neue `filter` hinzu, die verlangt, dass nur Konten zurückgegeben werden, bei denen die `statecode` ungleich 1 (inaktiv) ist.
1. Setzen Sie die modifizierte Abfrage auf den Wert <xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query>.

```csharp
if (fetchExpressionQuery != null)
{
    tracingService.Trace("Found FetchExpression Query");

    XDocument fetchXmlDoc = XDocument.Parse(fetchExpressionQuery.Query);
    //The required entity element
    var entityElement = fetchXmlDoc.Descendants("entity").FirstOrDefault();
    var entityName = entityElement.Attributes("name").FirstOrDefault().Value;

    //Only applying to the account entity
    if (entityName == "account")
    {
        tracingService.Trace("Query on Account confirmed");

        //Get all filter elements
        var filterElements = entityElement.Descendants("filter");

        //Find any existing statecode conditions
        var stateCodeConditions = from c in filterElements.Descendants("condition")
                                    where c.Attribute("attribute").Value.Equals("statecode")
                                    select c;

        if (stateCodeConditions.Count() > 0)
        {
            tracingService.Trace("Removing existing statecode filter conditions.");
        }
        //Remove statecode conditions
        stateCodeConditions.ToList().ForEach(x => x.Remove());


        //Add the condition you want in a new filter
        entityElement.Add(
            new XElement("filter",
                new XElement("condition",
                    new XAttribute("attribute", "statecode"),
                    new XAttribute("operator", "neq"), //not equal
                    new XAttribute("value", "1") //Inactive
                    )
                )
            );
    }


    fetchExpressionQuery.Query = fetchXmlDoc.ToString();

}
```

### <a name="queryexpression"></a>QueryExpression

1. Stellen Sie sicher, dass die <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.EntityName> die `account` Entität ist.
1. Schleife durch die <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>.<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters> Sammlung
1. Verwenden Sie die rekursive Methode `RemoveAttributeConditions`, um nach allen <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>-Instanzen zu suchen, die das Statecode-Attribut testen, und diese zu entfernen.
1. Fügem Sie der <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria> eine neue <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> hinzu.<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters> Sammlung, die verlangt, dass nur Konten zurückgegeben werden, bei denen die `statecode` nicht gleich 1 (inaktiv) ist.

```csharp
if (queryExpressionQuery != null)
{
    tracingService.Trace("Found Query Expression Query");
    if (queryExpressionQuery.EntityName.Equals("account"))
    {
        tracingService.Trace("Query on Account confirmed");

        //Recursively remove any conditions referring to the statecode attribute
        foreach (FilterExpression fe in queryExpressionQuery.Criteria.Filters)
        {
            //Remove any existing criteria based on statecode attribute
            RemoveAttributeConditions(fe, "statecode", tracingService);
        }

        //Define the filter
        var stateCodeFilter = new FilterExpression();
        stateCodeFilter.AddCondition("statecode", ConditionOperator.NotEqual, 1);
        //Add it to the Criteria
        queryExpressionQuery.Criteria.AddFilter(stateCodeFilter);
    }

}
```

#### <a name="removeattributeconditions-method"></a>RemoveAttributeConditions-Methode

Ein rekursives Verfahren, das alle Bedingungen für ein bestimmtes benanntes Attribut entfernt.

```csharp
/// <summary>
/// Removes any conditions using a specific named attribute
/// </summary>
/// <param name="filter">The filter that may have a condition using the attribute</param>
/// <param name="attributeName">The name of the attribute that should not be used in a condition</param>
/// <param name="tracingService">The tracing service to use</param>
private void RemoveAttributeConditions(FilterExpression filter, string attributeName, ITracingService tracingService)
{

    List<ConditionExpression> conditionsToRemove = new List<ConditionExpression>();

    foreach (ConditionExpression ce in filter.Conditions)
    {
        if (ce.AttributeName.Equals(attributeName))
        {
            conditionsToRemove.Add(ce);
        }
    }

    conditionsToRemove.ForEach(x =>
    {
        filter.Conditions.Remove(x);
        tracingService.Trace("Removed existing statecode filter conditions.");
    });

    foreach (FilterExpression fe in filter.Filters)
    {
        RemoveAttributeConditions(fe, attributeName, tracingService);
    }
}
```

### <a name="querybyattribute"></a>QueryByAttribute

Da <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> keine komplexen Filter unterstützt, schreiben Sie nur eine Meldung in das Plug-in-Trace-Log. 

Wenn Sie nicht möchten, dass diese Art von Abfrage überhaupt verwendet wird, können Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> werfen, um die Operation zu verhindern, aber dies wäre besser während der Phase `PreValidation` anzuwenden.

```csharp
if (queryByAttributeQuery != null)
{
    tracingService.Trace("Found Query By Attribute Query");
    //Query by attribute doesn't provide a complex query model that 
    // can be manipulated
}
```

## <a name="code-to-test-this-sample"></a>Code zum Testen dieses Beispiels

Der folgende Code zeigt 5 verschiedene Möglichkeiten, die gleiche Abfrage durchzuführen, die das Plug-in auslöst. 

Durch die Angabe eines bestimmten Kriteriums, in diesem Fall des Attributwertes `address1_city`, mit dem nur ein aktiver Datensatz übereinstimmt, geben diese Abfragen genau diesen Datensatz zurück.

Deaktivieren Sie dann diesen Datensatz und führen Sie diesen Code ein zweites Mal aus. Es werden keine Datensätze zurückgegeben.

```csharp
try
{
    string account_city_value = "ValueForTesting";

    //QueryByAttribute
    var queryByAttribute = new QueryByAttribute("account")
    {
        TopCount = 1,
        ColumnSet = new ColumnSet("accountid", "name")
    };
    queryByAttribute.AddAttributeValue("address1_city", account_city_value);
    queryByAttribute.AddOrder("name", OrderType.Descending);

    //QueryExpression
    var queryExpression = new QueryExpression("account")
    { ColumnSet = new ColumnSet("accountid", "name"), TopCount = 1 };
    queryExpression.Orders.Add(new OrderExpression("name", OrderType.Descending));
    var qeFilter = new FilterExpression(LogicalOperator.And);
    qeFilter.AddCondition(new ConditionExpression("address1_city", ConditionOperator.Equal, account_city_value));
    queryExpression.Criteria = qeFilter;

    //Fetch
    var fetchXml = $@"<fetch mapping='logical' count='1'>
                <entity name='account'>  
                    <attribute name='accountid'/>
                    <attribute name='name'/>
                    <order attribute='name' descending='true' />
                    <filter>
                    <condition attribute='address1_city' operator='eq' value='{account_city_value}' />
                    </filter>
                </entity>  
            </fetch>";

    var fetchExpression = new FetchExpression(fetchXml);

    //Get results:
    var queryByAttributeResults = service.RetrieveMultiple(queryByAttribute);
    var queryExpressionResults = service.RetrieveMultiple(queryExpression);
    var fetchExpressionResults = service.RetrieveMultiple(fetchExpression);

    //WebAPI
    string WebAPIAccountName = string.Empty;

    Dictionary<string, List<string>> ODataHeaders = new Dictionary<string, List<string>>() {
    {"Accept", new List<string>(){"application/json" } },
    {"OData-MaxVersion", new List<string>(){ "4.0" } },
    {"OData-Version", new List<string>(){ "4.0" } }};


    HttpResponseMessage response = service.ExecuteCrmWebRequest(HttpMethod.Get,
        $"accounts?$select=accountid,name&$top=1&$orderby=name desc&$filter=address1_city eq '{account_city_value}'",
        string.Empty,
        ODataHeaders);
    if (response.IsSuccessStatusCode)
    {
        var results = response.Content.ReadAsStringAsync().Result;
        var jsonResults = JObject.Parse(results);
        var accounts = (JArray)jsonResults.GetValue("value");
        if (accounts.Count > 0)
        {
            var account = accounts.First();
            WebAPIAccountName = account.Value<string>("name");
        }

    }

    else
    {
        Console.WriteLine(response.ReasonPhrase);
    }

    //Using Fetch with Web API
    string FetchWebAPIAccountName = string.Empty;
    HttpResponseMessage fetchResponse = service.ExecuteCrmWebRequest(HttpMethod.Get,
    $"accounts?fetchXml=" + Uri.EscapeDataString(fetchXml),
    string.Empty,
    ODataHeaders);
    if (fetchResponse.IsSuccessStatusCode)
    {

        var results = fetchResponse.Content.ReadAsStringAsync().Result;
        var jsonResults = JObject.Parse(results);
        var accounts = (JArray)jsonResults.GetValue("value");
        if (accounts.Count > 0)
        {
            var account = accounts.First();
            FetchWebAPIAccountName = account.Value<string>("name");
        }
    }

    else
    {
        Console.WriteLine(fetchResponse.ReasonPhrase);
    }

    string no_records_message = "No records returned";

    Console.WriteLine("QueryByAttribute Account Returned: {0}", queryByAttributeResults.Entities.Count > 0 ?
        queryByAttributeResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("QueryExpression Account Returned: {0}", queryExpressionResults.Entities.Count > 0 ?
        queryExpressionResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("Fetch Account Returned: {0}", fetchExpressionResults.Entities.Count > 0 ?
        fetchExpressionResults.Entities[0]["name"] : no_records_message);
    Console.WriteLine("WebAPI Account Returned: {0}", WebAPIAccountName != string.Empty ?
        WebAPIAccountName : no_records_message);
    Console.WriteLine("WebAPI Fetch Account Returned: {0}", FetchWebAPIAccountName != string.Empty ?
        FetchWebAPIAccountName : no_records_message);

}
catch (Exception ex)
{

    throw ex;
}
```

### <a name="see-also"></a>Siehe auch

[Implementieren aller Arten von Abfragen bei der Filterung von Ergebnissen mit PreOperation RetrieveMultiple](../../best-practices/business-logic/implement-all-types-of-queries-when-filtering-preoperation-retrievemultiple.md)
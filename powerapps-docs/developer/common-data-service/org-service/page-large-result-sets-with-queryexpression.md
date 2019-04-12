---
title: Auslagern von umfangreichen Ergebnissätzen mit QueryExpression (Common Data Service) | Microsoft Docs
description: 'In Dynamics 365 (Online) Customer Engagement können Sie die Auslagerungscookiefunktion verwenden, um Auslagerung in einer einzelnen Anwendung für umfangreiche Datasets schneller auszuführen. Die Funktion ist in FetchXML und QueryExpression-Abfragen verfügbar.'
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
# <a name="page-large-result-sets-with-queryexpression"></a>Auslagern von umfangreichen Ergebnissätzen mit QueryExpression

In Common Data Service können Sie die Auslagerungscookiefunktion verwenden, damit die Auslagerung in einer Anwendung für umfangreiche Datasets schneller ausgeführt werden kann. Die Funktion ist in FetchXML und <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Abfragen verfügbar. Wenn Sie die Auslagerungscookiefunktion bei der Abfrage einer Datensatzgruppe verwenden, enthält das Ergebnis einen Wert für das Auslagerungscookie. Um eine höhere Systemleistung zu erzielen, können Sie diesen Wert dann übergeben, wenn Sie die folgende Datensatzgruppe abrufen.  
  
 FetchXML und <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> und FetchXML verwenden unterschiedliche Formate für die Auslagerungscookies. Wenn Sie eine Konvertierung von einem Abfrageformat in anderes durchführen, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest>- oder die <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>-Meldung verwenden, wird der Auslagerungscookiewert ignoriert. Wenn Sie nicht aufeinanderfolgende Seiten abfragen, wird der Auslagerungscookiewert außerdem ignoriert.  
  
<a name="QueryExpression"></a>   
## <a name="using-a-paging-cookie-with-queryexpression"></a>Verwenden eines Auslagerungscookies mit QueryExpression  
 Im folgenden Beispiel wird gezeigt, wie das Auslagerungscookie mit einem Abfrageausdruck verwendet wird. Den vollständigen Beispielcode finden Sie unter [Beispiel: Verwendung von QueryExpression mit einem Auslagerungs-Cookie](../org-service/samples/use-queryexpression-with-a-paging-cookie.md).  
  
```csharp
// Query using the paging cookie.
// Define the paging attributes.
// The number of records per page to retrieve.
int queryCount = 3;

// Initialize the page number.
int pageNumber = 1;

// Initialize the number of records.
int recordCount = 0;

// Define the condition expression for retrieving records.
ConditionExpression pagecondition = new ConditionExpression();
pagecondition.AttributeName = "parentaccountid";
pagecondition.Operator = ConditionOperator.Equal;
pagecondition.Values.Add(_parentAccountId);

// Define the order expression to retrieve the records.
OrderExpression order = new OrderExpression();
order.AttributeName = "name";
order.OrderType = OrderType.Ascending;

// Create the query expression and add condition.
QueryExpression pagequery = new QueryExpression();
pagequery.EntityName = "account";
pagequery.Criteria.AddCondition(pagecondition);
pagequery.Orders.Add(order);
pagequery.ColumnSet.AddColumns("name", "emailaddress1");                   

// Assign the pageinfo properties to the query expression.
pagequery.PageInfo = new PagingInfo();
pagequery.PageInfo.Count = queryCount;
pagequery.PageInfo.PageNumber = pageNumber;

// The current paging cookie. When retrieving the first page, 
// pagingCookie should be null.
pagequery.PageInfo.PagingCookie = null;
Console.WriteLine("Retrieving sample account records in pages...\n");
Console.WriteLine("#\tAccount Name\t\tEmail Address"); 

while (true)
{
    // Retrieve the page.
    EntityCollection results = _serviceProxy.RetrieveMultiple(pagequery);
    if (results.Entities != null)
    {
        // Retrieve all records from the result set.
        foreach (Account acct in results.Entities)
        {
            Console.WriteLine("{0}.\t{1}\t{2}", ++recordCount, acct.Name,
                               acct.EMailAddress1);
        }
    }

    // Check for more records, if it returns true.
    if (results.MoreRecords)
    {
        Console.WriteLine("\n****************\nPage number {0}\n****************", pagequery.PageInfo.PageNumber);
        Console.WriteLine("#\tAccount Name\t\tEmail Address");

        // Increment the page number to retrieve the next page.
        pagequery.PageInfo.PageNumber++;
        
        // Set the paging cookie to the paging cookie returned from current results.
        pagequery.PageInfo.PagingCookie = results.PagingCookie;
    }
    else
    {
        // If no more records are in the result nodes, exit the loop.
        break;
    }
}
```

### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 [Beispiel: Verwenden von QueryExpression mit einem Auslagerungscookie](samples/use-queryexpression-with-a-paging-cookie.md)   
 [Beispiel: Abrufen bei 1: n-Beziehung](/dynamics365/customer-engagement/developer/retrieve-with-one-to-many-relationship)   
 [Verwenden der QueryExpression-Klasse](use-queryexpression-class.md)   
 [Auslagern von umfangreichen Ergebnissätzen mit FetchXML](page-large-result-sets-with-fetchxml.md)
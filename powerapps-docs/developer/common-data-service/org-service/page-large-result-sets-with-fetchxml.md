---
title: Auslagern von umfangreichen Ergebnissätzen mit FetchXML (Common Data Service) | Microsoft Docs
description: 'Sie können die Ergebnisse einer FetchXML-Abfrage auslagern, indem Sie das Auslagerungscookie verwenden.'
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
# <a name="page-large-result-sets-with-fetchxml"></a>Auslagern von umfangreichen Ergebnissätzen mit FetchXML

Sie können die Ergebnisse einer FetchXML-Abfrage auslagern, indem Sie das Auslagerungscookie verwenden. Das Auslagerungscookie ist eine Leistungsfunktion, durch die das Auslagern in der Anwendung für sehr große Datasets schneller ausgeführt wird. Wenn Sie eine Datensatzgruppe abfragen, enthält das Ergebnis einen Wert für das Auslagerungscookie. Um eine höhere Leistung zu erzielen, können Sie diesen Wert übergeben, wenn Sie die folgende Datensatzgruppe abrufen.  
  
 FetchXML und <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> verwenden unterschiedliche Formate für die Auslagerungscookies. Wenn Sie eine Konvertierung von einem Abfrageformat in anderes durchführen, indem Sie die <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>- oder die <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest>-Meldung verwenden, wird der Auslagerungscookiewert ignoriert. Wenn Sie nicht aufeinanderfolgende Seiten abfragen, wird der Auslagerungscookiewert außerdem ignoriert.  
  
 Wenn Sie das Auslagerungscookie mit FetchXML verwenden, stellen Sie sicher, dass Sie die korrekte Codierung verwenden. Das folgende Beispiel zeigt die richtige Codierung für die Verwendung des Auslagerungscookies mit FetchXML:  
  
```csharp  
strQueryXML = @"  
<fetch mapping='logical' paging-cookie='&lt;cookie page=&quot;1&quot;&gt;&lt;accountid last=&quot;{E062B974-7F8D-DC11-9048-0003FF27AC3B}&quot; first=&quot;{60B934EF-798D-DC11-9048-0003FF27AC3B}&quot;/&gt;&lt;/cookie&gt;' page='2' count='2'>  
 <entity name='account'>  
  <all-attributes/>  
 </entity>  
</fetch>";  
```  
  
## <a name="fetchxml-and-the-paging-cookie-example"></a>FetchXML und das Auslagerungscookie-Beispiel  
 Im folgenden Beispiel wird gezeigt, wie das Auslagerungscookie mit einer FetchXML-Abfrage verwendet wird. Den vollständigen Beispielcode finden Sie unter [Beispiel: Verwendung von FetchXML mit einem Auslagerungs-Cookie](samples/use-fetchxml-paging-cookie.md).  
  
```csharp
// Define the fetch attributes.
// Set the number of records per page to retrieve.
int fetchCount = 3;
// Initialize the page number.
int pageNumber = 1;
// Initialize the number of records.
int recordCount = 0;
// Specify the current paging cookie. For retrieving the first page, 
// pagingCookie should be null.
string pagingCookie = null;

// Create the FetchXml string for retrieving all child accounts to a parent account.
// This fetch query is using 1 placeholder to specify the parent account id 
// for filtering out required accounts. Filter query is optional.
// Fetch query also includes optional order criteria that, in this case, is used 
// to order the results in ascending order on the name data column.
string fetchXml = string.Format(@"<fetch version='1.0' 
                                mapping='logical' 
                                output-format='xml-platform'>
                                <entity name='account'>
                                    <attribute name='name' />
                                    <attribute name='emailaddress1' />
                                    <order attribute='name' descending='false'/>
                                    <filter type='and'>
                            <condition attribute='parentaccountid' 
                                            operator='eq' value='{0}' uiname='' uitype='' />
                                    </filter>
                                </entity>
                            </fetch>",
                                _parentAccountId);

Console.WriteLine("Retrieving data in pages\n"); 
Console.WriteLine("#\tAccount Name\t\t\tEmail Address");

while (true)
{
    // Build fetchXml string with the placeholders.
    string xml = CreateXml(fetchXml, pagingCookie, pageNumber, fetchCount);

    // Excute the fetch query and get the xml result.
    RetrieveMultipleRequest fetchRequest1 = new RetrieveMultipleRequest
    {
        Query = new FetchExpression(xml)
    };

    EntityCollection returnCollection = ((RetrieveMultipleResponse)_service.Execute(fetchRequest1)).EntityCollection;
    
    foreach (var c in returnCollection.Entities)
    {
        System.Console.WriteLine("{0}.\t{1}\t\t{2}", ++recordCount, c.Attributes["name"], c.Attributes["emailaddress1"] );
    }                        
    
    // Check for morerecords, if it returns 1.
    if (returnCollection.MoreRecords)
    {
        Console.WriteLine("\n****************\nPage number {0}\n****************", pageNumber);
        Console.WriteLine("#\tAccount Name\t\t\tEmail Address");
        
        // Increment the page number to retrieve the next page.
        pageNumber++;

        // Set the paging cookie to the paging cookie returned from current results.                            
        pagingCookie = returnCollection.PagingCookie;
    }
    else
    {
        // If no more records in the result nodes, exit the loop.
        break;
    }
}
```
  
### <a name="see-also"></a>Siehe auch  
 [Beispiel: Verwenden von FetchXML mit einem Auslagerungscookie](samples/use-fetchxml-paging-cookie.md)   
 [Abfragen erstellen mit FetchXML](/dynamics365/customer-engagement/developer/org-service/build-queries-fetchxml)   
 [Steuerdatum und "älter als"-Datums-/Zeit-Abfrageoperatoren in FetchXML](../use-fetchxml-fiscal-date-older-datetime-query-operators.md)   
 [Verwenden von FetchXml.](../use-fetchxml-construct-query.md)   
 [Auslagern von umfangreichen Ergebnissätzen mit QueryExpression](page-large-result-sets-with-queryexpression.md)

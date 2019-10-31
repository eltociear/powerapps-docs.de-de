---
title: Verwenden der Klasse QueryExpression (Common Data Service) | Microsoft Docs
description: 'Verwenden Sie die Klasse QueryExpression, um komplexe Abfragen für die Verwendung mit der Methode IOrganizationService.QueryBase oder der Nachricht RetrieveMultipleRequest zu erstellen.'
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
# <a name="use-the-queryexpression-class"></a>Verwenden der QueryExpression-Klasse

In Common Data Service können Sie mit der Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> komplexe Abfragen für die Verwendung mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>. <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> erstellen. Methode die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> Meldung verwenden. Sie können Abfrageparameter für <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, einrichten, indem Sie die Klassen <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>,i <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> und <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> verwenden.  
  
 Die <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Klasse ermöglicht Ihnen, komplexe Abfragen zu erstellen. Die Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> ist eine einfache Möglichkeit, um nach Entitäten zu suchen, bei denen Attribute mit angegebenen Werten übereinstimmen.  
  
 In der folgenden Tabelle sind die Eigenschaften aufgelistet, die Sie festlegen können, um einen Abfrageausdruck zu erstellen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.EntityName>|Gibt an, welcher Typ von Entität abgerufen wird. Ein Abfrageausdruck kann nur eine Sammlung eines Entitätstyps abrufen.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.ColumnSet>|Gibt den Satz von Attributen (Spalten) für den Abruf an.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Criteria>|Gibt komplexe bedingte und logische Filterausdrücke an, oder legt diese fest, die die Ergebnisse der Abfrage filtern.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Distinct>|Gibt an, ob die Suchergebnisse der Abfrage doppelte Datensätze enthalten.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.LinkEntities>|Gibt die Links zwischen mehreren Entitätstypen an.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.Orders>|Gibt die Reihenfolge an, in der die Datensätze von der Abfrage zurückgegeben werden.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryExpression.PageInfo>|Gibt die Anzahl von Seiten und die Anzahl der Datensätze pro Seite an, die von der Abfrage zurückgegeben werden.|  
  
<a name="record_count"></a>   
## <a name="record-count"></a>Anzahl der Datensätze  
 Um festzustellen wie viele Datensätze eine Abfrage zurückgab legen Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Query.PagingInfo.ReturnTotalRecordCount> auf "true" fest, bevor Sie die Abfrage ausführen. Daraufhin wird <xref:Microsoft.Xrm.Sdk.EntityCollection.TotalRecordCount> festgelegt. Andernfalls ist dieser Wert -1.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie die <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Klasse verwendet wird.  
  
```csharp  
//  Query using ConditionExpression and FilterExpression  
ConditionExpression condition1 = new ConditionExpression();  
condition1.AttributeName = "lastname";  
condition1.Operator = ConditionOperator.Equal;  
condition1.Values.Add("Brown");              
  
FilterExpression filter1 = new FilterExpression();  
filter1.Conditions.Add(condition1);  
  
QueryExpression query = new QueryExpression("contact");  
query.ColumnSet.AddColumns("firstname", "lastname");  
query.Criteria.AddFilter(filter1);  
  
EntityCollection result1 = _serviceProxy.RetrieveMultiple(query);  
Console.WriteLine();Console.WriteLine("Query using Query Expression with ConditionExpression and FilterExpression");  
Console.WriteLine("---------------------------------------");  
foreach (var a in result1.Entities)  
{  
    Console.WriteLine("Name: " + a.Attributes["firstname"] + " " + a.Attributes["lastname"]);  
}  
Console.WriteLine("---------------------------------------");  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 [Verwenden der ColumnSet-Klasse](use-the-columnset-class.md)   
 [Verwenden der ConditionExpression-Klasse](use-conditionexpression-class.md)   
 [Verwenden der FilterExpression-Klasse](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>
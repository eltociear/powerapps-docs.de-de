---
title: Verwenden der Klasse QueryExpression (Common Data Service) | Microsoft Docs
description: Verwenden Sie die Klasse QueryExpression, um komplexe Abfragen für die Verwendung mit der Methode IOrganizationService.QueryBase oder der Nachricht RetrieveMultipleRequest zu erstellen.
ms.custom: ''
ms.date: 04/17/2020
ms.reviewer: pehecke
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
ms.openlocfilehash: 0b405e76323300522e01956ea3eacbe7b2596f50
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275782"
---
# <a name="use-the-queryexpression-class"></a>Verwenden der QueryExpression-Klasse

In Common Data Service können Sie mit der Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> komplexe Abfragen für die Verwendung mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService>. <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> erstellen. Methode die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> Meldung verwenden. Sie können Abfrageparameter für <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>, einrichten, indem Sie die Klassen <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>,i <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> und <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> verwenden.  
  
 Die <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Klasse ermöglicht Ihnen, komplexe Abfragen zu erstellen. Die Klasse <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute> ist eine einfache Möglichkeit, um nach Entitäten zu suchen, bei denen Attribute mit angegebenen Werten übereinstimmen.  
  
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
## <a name="use-sql-hints-in-a-query"></a>Verwenden von SQL-Hinweisen in einer Abfrage

Die <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Klasse enthält eine Eigenschaft namens <xref:Microsoft.Xrm.Sdk.Query.QueryExpression.QueryHints>. Indem Sie diese Eigenschaft auf einen der unten gezeigten unterstützten Zeichenfolgenwerte setzen, können Sie einen Hinweis für generierten SQL-Text bereitstellen, der sich auf die Ausführung der Abfrage auswirkt.

|QueryHint-Wert | SQL-Abfrageoption und -hinweis |
|---------|---------|
|OptimizeForUnknown | Für unbekannt optimieren|
|ForceOrder | Befehl durchsetzen |
|Neu kompilieren | Neu kompilieren |
|DisableRowGoal | Hinweis benutzen ('Disable_Optimizer_RowGoal') |
|EnableOptimizerHotfixes | Hinweis benutzen ('ENABLE_QUERY_OPTIMIZER_HOTFIXES') |
|LoopJoin | Loop verbinden |
|MergeJoin | Zusammenführen |
|HashJoin | Hash Join |
|NO_PERFORMANCE_SPOOL | NO_PERFORMANCE_SPOOL |
|MaxRecursion | MAXRECURSION-Nummer |

Weitere Informationen: [Hinweise (Transact-SQL) – Abfrage](https://docs.microsoft.com/sql/t-sql/queries/hints-transact-sql-query)

### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 [Verwenden der ColumnSet-Klasse](use-the-columnset-class.md)   
 [Verwenden der ConditionExpression-Klasse](use-conditionexpression-class.md)   
 [Verwenden der FilterExpression-Klasse](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>
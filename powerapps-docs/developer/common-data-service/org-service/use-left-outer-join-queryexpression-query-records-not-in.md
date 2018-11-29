---
title: 'Verwenden einer linken äußeren Verknüpfung in QueryExpression für Abfragen nach Datensätzen, die &quot;nicht in&quot; sind (Common Data Service für Apps) | Microsoft Docs'
description: 'Erfahren Sie, wie eine linke äußere Verknüpfung mithilfe der QueryExpression-Klasse verwendet wird, um eine Abfrage auszuführen, die die Verknüpfungstabelle filtert, und eine Abfrage zu erstellen, die Datensätze des Typs &quot;nicht in&quot; in einer Gruppe findet'
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
# <a name="use-a-left-outer-join-in-queryexpression-to-query-for-records-not-in"></a>Verwenden einer linken äußeren Verknüpfung in QueryExpression für Abfragen nach Datensätzen, die „nicht in“ sind.

Sei können eine linke äußere Verknüpfung verwenden, indem Sie mit der <xref:Microsoft.Crm.Sdk.Messages.SearchByKeywordsKbArticleRequest.QueryExpression>-Klasse eine Abfrage ausführen, in der die Verknüpfungstabelle gefiltert wird, z. B. zum Suchen aller Kontakte, die in den letzten beiden Monaten keine Kampagnenaktivität hatten. Eine weitere allgemeine Verwendung dieses Abfragetyps ist das Suchen von Datensätzen, die „nicht in“ sind, wie in folgenden Fällen:  
  
- Suchen aller Leads, die über keine Tasks verfügen.  
  
- Suchen aller Firmen, die über keine Kontakte verfügen  
  
- Suchen aller Leads, die mindestens eine Task verfügen.  
  
  Eine linke äußere Verknüpfung gibt jede Zeile zurück, die der Verknüpfung der ersten Eingabe mit der zweiten Eingabe entspricht. Es werden auch alle Zeilen aus der ersten Eingabe zurückgegeben, die in der zweiten Eingabe keine Übereinstimmung haben. Die nicht übereinstimmenden Zeilen in der zweiten Eingabe werden als Nullwerte zurückgegeben.  
  
  Sie können eine linke äußere Verknüpfung in `QueryExpression` ausführen, indem Sie das Attribut `entityname` als Bedingungsoperator verwenden. Das Attribut `entityname` ist auch für die Bedingungen, Filter und geschachtelte Filter gültig.  
  
## <a name="find-all-leads-that-have-no-tasks-using-an-alias"></a>Suchen aller Leads, die keine Aufgaben haben, mithilfe eines Alias  

Im folgenden Beispiel wird gezeigt, wie diese Abfrage aufgebaut ist:  
  
```csharp
QueryExpression qx = new QueryExpression("lead");  
qx.ColumnSet.AddColumn("subject");  
  
LinkEntity link = qx.AddLink("task", "leadid", "regardingobjectid", JoinOperator.LeftOuter);  
link.Columns.AddColumn("subject");  
link.EntityAlias = "tsk";  
  
qx.Criteria = new FilterExpression();  
qx.Criteria.AddCondition("tsk", "activityid", ConditionOperator.Null);
```  
  
Dies ist äquivalent zu folgendem SQL:  
  
```sql
SELECT lead.FullName  
FROM Leads as lead  
LEFT OUTER JOIN Tasks as ab  
ON (lead.leadId  =  ab.RegardingObjectId)  
WHERE ab.RegardingObjectId is null
```  
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 [Test auf einen Nullwert](/dynamics365/customer-engagement/developer/test-null-value)   
 [Verwenden der QueryExpression-Klasse](use-queryexpression-class.md)   
 [Verwenden der QueryByAttribute-Klasse](use-querybyattribute-class.md)
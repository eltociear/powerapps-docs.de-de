---
title: Verwenden der FilterExpression-Klasse (Common Data Service) | Microsoft Docs
description: 'Lesen Sie, wie Sie die FilterExpression-Klasse dazu verwenden, eine Abfrage zu erstellen, die Mehrfachbedingungen ausdrückt'
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
# <a name="use-the-filterexpression-class"></a>Die FilterExpression-Klasse verwenden

In Common Data Service können Sie die <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>-Klasse verwenden, eine Abfrage zu erstellen, die Mehrfachbedingungen ausdrückt. Beispielsweise können Sie einen Abfrageausdruck erstellen, der die Entsprechung einer SQL-Anweisung, wie `([FirstName] = 'Joe' OR [FirstName] = 'John') AND [City] = 'Redmond'` ist.  
  
 In der folgenden Tabelle werden die Eigenschaften der <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>-Klasse aufgeführt:  
  
|||  
|-|-|  
|Eigenschaft|Beschreibung|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Conditions>|Ruft Bedingungsausdrücke ab oder legt sie fest, die Attribute, Zustandsoperatoren und Attributwerte enthalten.|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.FilterOperator>|Ruft logische `AND/OR`-Filteroperatoren ab oder legt sie fest. Dies wird mit der <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator>-Enumeration festgelegt.|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters>|Ruft eine Hierarchie von Bedingung und logischen Filterausdrücken ab oder legt diese fest, die die Ergebnisse der Abfrage filtern.|  
|<xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter>|Ruft einen Wert ab oder legt diesen fest, der angibt, ob der Ausdruck Teil einer Schnellsuchabfrage ist.|  
  
 Die <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>-Klasse beinhaltet auch mehrere Hilfsmethoden, mit denen Abfragen leichter erstellt werden können. Im <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression> fügt der <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Conditions>-Eigenschaft für <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> ein <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>-Element hinzu und verringert die Codemenge, die zur Erstellung des Bedingungsausdrucks benötigt wird. Im <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.AddFilter*>.<xref:Microsoft.Xrm.Sdk.Query.LogicalOperator> Methode fügt der <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.Filters>-Eigenschaft der <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>-Klasse einen neuen Filter hinzu.  
  
<a name="example"></a>   

## <a name="filter-expression-example"></a>Filterausdruckbeispiel  

 Im folgenden Code wird gezeigt, wie die <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>-Klasse verwendet wird.  
  
```csharp  
QueryExpression query = new QueryExpression("contact");   
query.ColumnSet.AddColumns("firstname", "lastname", "address1_city");   
  
query.Criteria = new FilterExpression();   
query.Criteria.AddCondition("address1_city", ConditionOperator.Equal, "Redmond");   
  
FilterExpression childFilter = query.Criteria.AddFilter(LogicalOperator.Or);   
childFilter.AddCondition("lastname", ConditionOperator.Equal, "Tharpe");   
childFilter.AddCondition("lastname", ConditionOperator.Equal, "Brown");   
  
// Pass query to service proxy   
EntityCollection results = _serviceProxy.RetrieveMultiple(query);   
Console.WriteLine();   
Console.WriteLine("Query using QE with multiple conditions and filters");   
Console.WriteLine("---------------------------------------");   
  
// Print results   
foreach (var a in results.Entities)   
{   
Console.WriteLine("Name: {0} {1}", a.GetAttributeValue<string>("firstname"), a.GetAttributeValue<string>("lastname"));   
Console.WriteLine("City: {0}", a.GetAttributeValue<string>("address1_city"));   
}   
Console.WriteLine("---------------------------------------");  
```  
  
<a name="quickfindfilter"></a> 
  
## <a name="about-the-isquickfindfilter-property"></a>Informationen zur IsQuickFindFilter-Eigenschaft  

 In <xref:Microsoft.Xrm.Sdk.Query.FilterExpression> können Sie die Methoden <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> verwenden. Eigenschaft verwenden, die analog ist zum `isquickfindfields`-Attribut, das auf dem `filter`-Knoten in Fetch-XML vorhanden ist. Wenn eine Fetch-Abfrage gespeichert wird, wird diese in den `IsQuickFind`-Eigenschaften der Entitäten `SavedQuery` und `UserQuery` gespeichert. Die <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter>-Eigenschaft wurde hinzugefügt, um zwischen Abfrageausdruck und und Fetch-XML-Abfragen Konsistenz zu erreichen.  
  
 Die folgenden Regeln gelten für die <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter>-Eigenschaft:  
  
-   Dieses Feld kann nur für Filterausdrücke mit einem logischen Operator des Typs <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator>.`Or` auf `true` festgelegt werden. Falls es für Ausdrücke mit dem logischen Operator vom Typ <xref:Microsoft.Xrm.Sdk.Query.LogicalOperator>.`And` festgelegt wird, wird die <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter>-Eigenschaft ignoriert.  
  
-   Nur ein Filterausdruck in einer Filterausdruckhierarchie kann auf <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> = **true** festgelegt werden. Wird mehr als eine gefunden, wird eine Ausnahme ausgelöst.  
  
-   Wenn ein Filterausdruck <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> auf **true** festgelegt ist, kann sie keine untergeordneten Filterausdruckeigenschaften haben. Sie kann nur <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>-Eigenschaften haben. Wenn Sie einen untergeordneten Filterausdruck hinzufügen, wird eine Ausnahme ausgelöst.  
  
-   Alle Bedingungsausdrücke, die sich auf einen Filterausdruck beziehen, bei dem <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.IsQuickFindFilter> auf **true** festgelegt ist, müssen einzelne, nicht Nullwertbedingungen sein. Mit anderen Worten, da eine Bedingung aus Attribut, Operator und Wert besteht, werden nur Bedingungen unterstützt, bei denen die Wertseigenschaft ein einzelner Wert ist, der nicht **Null** ist. Außerdem sind die einzigen Bedingungsoperatoren, die auf diesen Bedingungsausdrücken unterstützt werden, solche, die einem Einzelwert verwenden, der nicht NULL ist. Wenn ein **Null**-Wert oder mehrere Werte erkannt werden, wird eine Ausnahme ausgelöst.  
  
### <a name="see-also"></a>Siehe auch  

 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 [Verwenden einer linken äußeren Verknüpfung in QueryExpression für Abfragen nach Datensätzen, die „nicht in“ sind.](use-left-outer-join-queryexpression-query-records-not-in.md)   
 [Verwenden der ConditionExpression-Klasse](use-conditionexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>
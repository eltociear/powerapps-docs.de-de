---
title: Verwenden von FetchXML-Aggregation (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie mehr über die Gruppierungs- und Aggregationsfunktionen von FetchXML, mit denen Sie die Summe, das durchschnittliche Minimum, das durchschnittliche Maximum und die Anzahl berechnen können.'
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

# <a name="use-fetchxml-aggregation"></a>FetchXML-Aggregation verwenden

In Common Data Service enthält `FetchXML` Gruppierungs- und Aggregationsfunktionen, mit denen Sie die Summe, das durchschnittliche Minimum, das durchschnittliche Maximum und die Anzahl berechnen können.  
  
 Die folgenden Aggregatfunktionen werden unterstützt:  
  
-   sum  
  
-   avg  
  
-   Min.  
  
-   max  
  
-   count(*)  
  
-   count(*attribute name*)  
  
<a name="Aggregation"></a>

## <a name="about-aggregation"></a>Über Aggregation
 
 Um ein Aggregatattribut zu erstellen, legen Sie das Schlüsselwort `aggregate` auf `true` fest, und geben Sie dann einen gültigen *Entitätsnamen*, *Attributnamen* und *Alias* (Variablennamen) an. Sie müssen auch den Typ der Aggregation angeben, den Sie ausführen möchten.  
  
 Das folgende Beispiel zeigt ein einfaches Aggregatattribut in `FetchXML`.  
  
```xml  
<fetch distinct='false' mapping='logical' aggregate='true'>   
   <entity name='entity name'>   
      <attribute name='attribute name' aggregate='count' alias='alias name'/>   
   </entity>   
</fetch>
```  
  
 Das Ergebnis einer Abfrage mit einem Aggregatattribut unterscheidet sich von den Ergebnissen einer Standardabfrage. Der Aliaswert wird als der Tagbezeichner für das Aggregatergebnis verwendet.  
  
 Im folgenden Beispiel wird das Format von dem Ergebnis einer Aggregatabfrage gezeigt.  
  
```xml
<resultset morerecords="0"'>   
   <result>  
      <alias>aggregate value</alias>  
   </result>  
</resultset>
```  
  
 Das folgende Beispiel zeigt die Ergebnisse einer Abfrage, wenn die zu Aliasvariable auf `account_count` festgelegt ist.  
  
```xml
<resultset morerecords="0"'>   
   <result>  
      <account_count>20</account_count>  
   </result>  
</resultset>
```  
  
<a name="AVG"></a>

## <a name="avg"></a>Durchschnitt

 Im folgenden Beispiel wird gezeigt, wie das `avg``aggregate`-Attribut verwendet wird.  
  
 ```csharp
// Fetch the average of estimatedvalue for all opportunities.  This is the equivalent of 
// SELECT AVG(estimatedvalue) AS estimatedvalue_avg ... in SQL.
System.Console.WriteLine("===============================");
string estimatedvalue_avg = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg' /> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_avg_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_avg));

foreach (var c in estimatedvalue_avg_result.Entities)
{
    decimal aggregate1 = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average estimated value: " + aggregate1);

}
System.Console.WriteLine("===============================");
```
  
### <a name="limitation-with-null-values-while-computing-average"></a>Beschränkung mit Nullwerten beim Berechnen des Durchschnitts  
 **Null**-Werte werden nicht berücksichtigt, wenn Common Data Service den Durchschnitt von Daten berechnet. NULL (0) wird jedoch verwendet.  
  
 Im folgenden Beispiel wird mit den folgenden Daten als Durchschnittswert für Firma 1 (zwei Einträge) 250 angezeigt, während als Durchschnittswert für Firma 2 (zwei Einträge) 125 angezeigt wird.  
  
|Thema|Potenz. Kunde|Erwarteter Wert|  
|-----|------------------|---------------|  
|Verkaufschance 1|Firma 1|Null|  
|Verkaufschance 2|Firma 1|250|  
|Verkaufschance 3|Firma 2|0|  
|Verkaufschance 4|Firma 2|250|  
  
<a name="count"></a>

## <a name="count"></a>Anzahl

 Im folgenden Beispiel wird gezeigt, wie das `count``aggregate`-Attribut verwendet wird.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      opportunity_count   Aggregate 2
// *****************************************************************************************************************
// Fetch the count of all opportunities.  This is the equivalent of
// SELECT COUNT(*) AS opportunity_count ... in SQL.
string opportunity_count = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_count' aggregate='count'/> 
    </entity> 
</fetch>";

EntityCollection opportunity_count_result = _serviceProxy.RetrieveMultiple(new FetchExpression(opportunity_count));

foreach (var c in opportunity_count_result.Entities)
{
    Int32 aggregate2 = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate2); 

}
System.Console.WriteLine("===============================");
```
  
<a name="count_column"></a>

### <a name="countcolumn"></a>CountColumn

 Im folgenden Beispiel wird veranschaulicht, wie Sie das `countcolumn``aggregate`-Attribut verwenden, um Spalten zu zählen.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      opportunity_colcount   Aggregate 3
// *****************************************************************************************************************
// Fetch the count of all opportunities.  This is the equivalent of 
// SELECT COUNT(name) AS opportunity_count ... in SQL.
string opportunity_colcount = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_colcount' aggregate='countcolumn'/> 
    </entity> 
</fetch>";

EntityCollection opportunity_colcount_result = _serviceProxy.RetrieveMultiple(new FetchExpression(opportunity_colcount));

foreach (var c in opportunity_colcount_result.Entities)
{
    Int32 aggregate3 = (Int32)((AliasedValue)c["opportunity_colcount"]).Value;
    System.Console.WriteLine("Column count of all opportunities: " + aggregate3);

}
System.Console.WriteLine("===============================");
```
  
<a name="count_distinct"></a>
 
### <a name="count-distinct-columns"></a>Eindeutige Spalten zählen

 Im folgenden Beispiel wird veranschaulicht, wie Sie das `countcolumn``aggregate`-Attribut mit dem `distinct`-Attribut verwenden, um distinkte Spalten zu zählen.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      opportunity_distcount   Aggregate 4
// *****************************************************************************************************************
// Fetch the count of distinct names for opportunities.  This is the equivalent of 
// SELECT COUNT(DISTINCT name) AS opportunity_count ... in SQL.
string opportunity_distcount = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_distcount' aggregate='countcolumn' distinct='true'/> 
    </entity> 
</fetch>";

EntityCollection opportunity_distcount_result = _serviceProxy.RetrieveMultiple(new FetchExpression(opportunity_distcount));

foreach (var c in opportunity_distcount_result.Entities)
{
    Int32 aggregate4 = (Int32)((AliasedValue)c["opportunity_distcount"]).Value;
    System.Console.WriteLine("Distinct name count of all opportunities: " + aggregate4);

}
System.Console.WriteLine("===============================");
```
  
<a name="max"></a>

## <a name="max"></a>Max

 **Null**-Werte werden nicht berücksichtigt, wenn Common Data Service das Maximum von Daten berechnet. NULL (0) wird jedoch verwendet.  
  
 Im folgenden Beispiel wird gezeigt, wie das `max``aggregate`-Attribut verwendet wird.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      opportunity_distcount   Aggregate 4
// *****************************************************************************************************************
// Fetch the count of distinct names for opportunities.  This is the equivalent of 
// SELECT COUNT(DISTINCT name) AS opportunity_count ... in SQL.
string opportunity_distcount = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_distcount' aggregate='countcolumn' distinct='true'/> 
    </entity> 
</fetch>";

EntityCollection opportunity_distcount_result = _serviceProxy.RetrieveMultiple(new FetchExpression(opportunity_distcount));

foreach (var c in opportunity_distcount_result.Entities)
{
    Int32 aggregate4 = (Int32)((AliasedValue)c["opportunity_distcount"]).Value;
    System.Console.WriteLine("Distinct name count of all opportunities: " + aggregate4);

}
System.Console.WriteLine("===============================");
```
  
<a name="min"></a>
 
## <a name="min"></a>Min

 **Null**-Werte werden nicht berücksichtigt, wenn Common Data Service das Minimum von Daten berechnet. NULL (0) wird jedoch verwendet.  
  
 Im folgenden Beispiel wird gezeigt, wie das `min``aggregate`-Attribut verwendet wird.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      estimatedvalue_min   Aggregate 6
// *****************************************************************************************************************
// Fetch the minimum estimatedvalue of all opportunities.  This is the equivalent of 
// SELECT MIN(estimatedvalue) AS estimatedvalue_min ... in SQL.
string estimatedvalue_min = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='estimatedvalue' alias='estimatedvalue_min' aggregate='min' /> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_min_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_min));

foreach (var c in estimatedvalue_min_result.Entities)
{
    decimal aggregate6 = ((Money)((AliasedValue)c["estimatedvalue_min"]).Value).Value;
    System.Console.WriteLine("Minimum estimated value of all opportunities: " + aggregate6);

}
System.Console.WriteLine("===============================");
```
  
<a name="sum"></a>

## <a name="sum"></a>Summe

 Im folgenden Beispiel wird gezeigt, wie das `sum``aggregate`-Attribut verwendet wird.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      estimatedvalue_sum   Aggregate 7
// *****************************************************************************************************************
// Fetch the sum of estimatedvalue for all opportunities.  This is the equivalent of 
// SELECT SUM(estimatedvalue) AS estimatedvalue_sum ... in SQL.
string estimatedvalue_sum = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum' /> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_sum_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_sum));

foreach (var c in estimatedvalue_sum_result.Entities)
{
    decimal aggregate7 = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate7);

}
System.Console.WriteLine("===============================");
```
  
<a name="mult_agg"></a>
 
## <a name="multiple-aggregates"></a>Mehrere Aggregate

 Im folgenden Beispiel wird veranschaulicht, wie Sie mehrere `aggregate`-Attribute verwenden, um ein Minimum und ein Maximum festzulegen.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      estimatedvalue_avg, estimatedvalue_sum   Aggregate 8
// *****************************************************************************************************************
// Fetch multiple aggregate values within a single query.
string estimatedvalue_avg2 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
    </entity> 
</fetch>";

EntityCollection estimatedvalue_avg2_result = _serviceProxy.RetrieveMultiple(new FetchExpression(estimatedvalue_avg2));

foreach (var c in estimatedvalue_avg2_result.Entities)
{
    Int32 aggregate8a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate8a);
    decimal aggregate8b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate8b);
    decimal aggregate8c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate8c);

}
System.Console.WriteLine("===============================");
```
  
<a name="groupby"></a>
 
## <a name="group-by"></a>Gruppieren nach

 Im folgenden Beispiel wird veranschaulicht, wie Sie mehrere `aggregate`-Attribute und ein verknüpftes `groupby`-Attribut verwenden.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      groupby1   Aggregate 9
// *****************************************************************************************************************
// Fetch a list of users with a count of all the opportunities they own using groupby.
string groupby1 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_count' aggregate='countcolumn' /> 
       <attribute name='ownerid' alias='ownerid' groupby='true' /> 
    </entity> 
</fetch>";

EntityCollection groupby1_result = _serviceProxy.RetrieveMultiple(new FetchExpression(groupby1));

foreach (var c in groupby1_result.Entities)
{
    Int32 aggregate9a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate9a + "\n");
    string aggregate9b = ((EntityReference)((AliasedValue)c["ownerid"]).Value).Name;
    System.Console.WriteLine("Owner: " + aggregate9b);
    string aggregate9c = (string)((AliasedValue)c["ownerid_owneridyominame"]).Value;
    System.Console.WriteLine("Owner: " + aggregate9c);
    string aggregate9d = (string)((AliasedValue)c["ownerid_owneridyominame"]).Value;
    System.Console.WriteLine("Owner: " + aggregate9d);
}
System.Console.WriteLine("===============================");
```
  
 Die unteren Beispiele zeigen die folgende Gruppe nach Beispielen:  
  
 [Gruppieren nach mit verknüpfter Entität](use-fetchxml-aggregation.md#groupby_linked)  
  
 [Gruppieren nach Jahr](use-fetchxml-aggregation.md#groupby_year)  
  
 [Gruppieren nach Quartal](use-fetchxml-aggregation.md#groupby_quarter)  
  
 [Gruppieren nach Monat](use-fetchxml-aggregation.md#groupby_month)  
  
 [Gruppieren nach Woche](use-fetchxml-aggregation.md#groupby_week)  
  
 [Gruppieren nach Tag](use-fetchxml-aggregation.md#groupby_day)  
  
 [Mehrere "Gruppieren nach"](use-fetchxml-aggregation.md#Multiple_GroupBy)  
  
<a name="groupby_linked"></a>

### <a name="group-by-with-linked-entity"></a>Gruppieren nach mit verknüpfter Entität

 Im folgenden Beispiel wird veranschaulicht, wie Sie das `sum``aggregate`-Attribut verwenden, um verknüpfte Entitätswerte zu summieren.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      groupby2   Aggregate 10
// *****************************************************************************************************************
// Fetch the number of opportunities each manager's direct reports 
// own using a groupby within a link-entity.
string groupby2 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='name' alias='opportunity_count' aggregate='countcolumn' /> 
       <link-entity name='systemuser' from='systemuserid' to='ownerid'>
           <attribute name='parentsystemuserid' alias='managerid' groupby='true' />
       </link-entity> 
    </entity> 
</fetch>";

EntityCollection groupby2_result = _serviceProxy.RetrieveMultiple(new FetchExpression(groupby2));

foreach (var c in groupby2_result.Entities)
{

      int? aggregate10a = (int?)((AliasedValue)c["opportunity_count"]).Value;
      System.Console.WriteLine("Count of all opportunities: " + aggregate10a + "\n");
}
System.Console.WriteLine("===============================");
```
  
<a name="groupby_year"></a>

### <a name="group-by-year"></a>Gruppieren nach Jahr

 "Gruppieren nach" für Datumsangaben verwenden den Wert für Tag, Woche, Monat, Quartal oder Jahr. Im folgenden Beispiel wird gezeigt, wie Sie das `aggregate`-Attribut und das `groupby`-Attribut verwenden, um die Ergebnisse nach Jahr zu gruppieren.  
  
 ```csharp

// *****************************************************************************************************************
//                FetchXML      byyear   Aggregate 11           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by year.
string byyear = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='year' alias='year' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byyear_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byyear));

foreach (var c in byyear_result.Entities)
{
    Int32 aggregate11 = (Int32)((AliasedValue)c["year"]).Value;
    System.Console.WriteLine("Year: " + aggregate11);                      
    Int32 aggregate11a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate11a);
    decimal aggregate11b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate11b);
    decimal aggregate11c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate11c);
    System.Console.WriteLine("----------------------------------------------");
}
System.Console.WriteLine("===============================");
```
  
<a name="groupby_quarter"></a>
 
### <a name="group-by-quarter"></a>Gruppieren nach Quartal

 Im folgenden Beispiel wird gezeigt, wie Sie das `aggregate`-Attribut und das `groupby`-Attribut verwenden, um die Ergebnisse nach Quartal zu gruppieren.  
  
 ```csharp
 // *****************************************************************************************************************
 //                FetchXML      byquarter   Aggregate 12           
 // *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
 // been won by quarter.(returns 1-4)
 string byquarter = @" 
 <fetch distinct='false' mapping='logical' aggregate='true'> 
     <entity name='opportunity'> 
        <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
        <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
        <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
        <attribute name='actualclosedate' groupby='true' dategrouping='quarter' alias='quarter' />
        <filter type='and'>
            <condition attribute='statecode' operator='eq' value='Won' />
        </filter>
     </entity> 
 </fetch>";

 EntityCollection byquarter_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byquarter));

 foreach (var c in byquarter_result.Entities)
 {
     Int32 aggregate12 = (Int32)((AliasedValue)c["quarter"]).Value;
     System.Console.WriteLine("Quarter: " + aggregate12);
     Int32 aggregate12a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
     System.Console.WriteLine("Count of all opportunities: " + aggregate12a);
     decimal aggregate12b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
     System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate12b);
     decimal aggregate12c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
     System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate12c);
     System.Console.WriteLine("----------------------------------------------");
 }
 System.Console.WriteLine("===============================");
```
  
<a name="groupby_month"></a>

### <a name="group-by-month"></a>Gruppieren nach Monat

 Im folgenden Beispiel wird gezeigt, wie Sie das `aggregate`-Attribut und das `groupby`-Attribut verwenden, um die Ergebnisse nach Monat zu gruppieren.  
  
```csharp
// *****************************************************************************************************************
//                FetchXML      bymonth   Aggregate 13           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by month. (returns 1-12)
string bymonth = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='month' alias='month' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection bymonth_result = _serviceProxy.RetrieveMultiple(new FetchExpression(bymonth));

foreach (var c in bymonth_result.Entities)
{
    Int32 aggregate13 = (Int32)((AliasedValue)c["month"]).Value;
    System.Console.WriteLine("Month: " + aggregate13);
    Int32 aggregate13a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate13a);
    decimal aggregate13b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate13b);
    decimal aggregate13c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate13c);
    System.Console.WriteLine("----------------------------------------------");
}
System.Console.WriteLine("===============================");
``` 
<a name="groupby_week"></a>

### <a name="group-by-week"></a>Gruppieren nach Woche

 Im folgenden Beispiel wird gezeigt, wie Sie das `aggregate`-Attribut und das `groupby`-Attribut verwenden, um die Ergebnisse nach Woche zu gruppieren.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byweek   Aggregate 14           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by week. (Returns 1-52)
string byweek = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='week' alias='week' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byweek_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byweek));

foreach (var c in byweek_result.Entities)
{
    Int32 aggregate14 = (Int32)((AliasedValue)c["week"]).Value;
    System.Console.WriteLine("Week: " + aggregate14);
    Int32 aggregate14a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate14a);
    decimal aggregate14b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate14b);
    decimal aggregate14c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate14c);
    System.Console.WriteLine("----------------------------------------------");
}
System.Console.WriteLine("===============================");
```
  
<a name="groupby_day"></a>

### <a name="group-by-day"></a>Gruppieren nach Tag

 Im folgenden Beispiel wird gezeigt, wie Sie das `aggregate`-Attribut und das `groupby`-Attribut verwenden, um die Ergebnisse nach Tag zu gruppieren.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byday   Aggregate 15           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by day. (Returns 1-31)
string byday = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='day' alias='day' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byday_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byday));

foreach (var c in byday_result.Entities)
{
    Int32 aggregate15 = (Int32)((AliasedValue)c["day"]).Value;
    System.Console.WriteLine("Day: " + aggregate15);
    Int32 aggregate15a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate15a);
    decimal aggregate15b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate15b);
    decimal aggregate15c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate15c);
    System.Console.WriteLine("----------------------------------------------");
}
System.Console.WriteLine("===============================");
```
  
<a name="Multiple_GroupBy"></a>
 
### <a name="multiple-group-by"></a>Mehrere "Gruppieren nach"

 Im folgenden Beispiel wird veranschaulicht, wie Sie das `aggregate`-Attribut und mehrere `groupby`-Klauseln verwenden.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byyrqtr   Aggregate 16           
// *****************************************************************************************************************
// Fetch aggregate information about the opportunities that have 
// been won by year and quarter.
string byyrqtr = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='quarter' alias='quarter' />
       <attribute name='actualclosedate' groupby='true' dategrouping='year' alias='year' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byyrqtr_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byyrqtr));

foreach (var c in byyrqtr_result.Entities)
{
    Int32 aggregate16d = (Int32)((AliasedValue)c["year"]).Value;
    System.Console.WriteLine("Year: " + aggregate16d);
    Int32 aggregate16 = (Int32)((AliasedValue)c["quarter"]).Value;
    System.Console.WriteLine("Quarter: " + aggregate16);
    Int32 aggregate16a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate16a);
    decimal aggregate16b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate16b);
    decimal aggregate16c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate16c);
    System.Console.WriteLine("----------------------------------------------");
}
System.Console.WriteLine("===============================");
```
  
<a name="orderby_aggregate"></a>

## <a name="order-by"></a>Ordnen nach

 Im folgenden Beispiel wird veranschaulicht, wie Sie das `aggregate`-Attribut und mehrere `orderby`-Klauseln verwenden.  
  
 ```csharp
// *****************************************************************************************************************
//                FetchXML      byyrqtr2   Aggregate 17           
// *****************************************************************************************************************
// Specify the result order for the previous sample.  Order by year, then quarter.
string byyrqtr2 = @" 
<fetch distinct='false' mapping='logical' aggregate='true'> 
    <entity name='opportunity'> 
       <attribute name='opportunityid' alias='opportunity_count' aggregate='count'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_sum' aggregate='sum'/> 
       <attribute name='estimatedvalue' alias='estimatedvalue_avg' aggregate='avg'/> 
       <attribute name='actualclosedate' groupby='true' dategrouping='quarter' alias='quarter' />
       <attribute name='actualclosedate' groupby='true' dategrouping='year' alias='year' />
       <order alias='year' descending='false' />
       <order alias='quarter' descending='false' />
       <filter type='and'>
           <condition attribute='statecode' operator='eq' value='Won' />
       </filter>
    </entity> 
</fetch>";

EntityCollection byyrqtr2_result = _serviceProxy.RetrieveMultiple(new FetchExpression(byyrqtr2));

foreach (var c in byyrqtr2_result.Entities)
{
    Int32 aggregate17 = (Int32)((AliasedValue)c["quarter"]).Value;
    System.Console.WriteLine("Quarter: " + aggregate17);
    Int32 aggregate17d = (Int32)((AliasedValue)c["year"]).Value;
    System.Console.WriteLine("Year: " + aggregate17d);
    Int32 aggregate17a = (Int32)((AliasedValue)c["opportunity_count"]).Value;
    System.Console.WriteLine("Count of all opportunities: " + aggregate17a);
    decimal aggregate17b = ((Money)((AliasedValue)c["estimatedvalue_sum"]).Value).Value;
    System.Console.WriteLine("Sum of estimated value of all opportunities: " + aggregate17b);
    decimal aggregate17c = ((Money)((AliasedValue)c["estimatedvalue_avg"]).Value).Value;
    System.Console.WriteLine("Average of estimated value of all opportunities: " + aggregate17c);
    System.Console.WriteLine("----------------------------------------------");
}
System.Console.WriteLine("===============================");
```
  
### <a name="see-also"></a>Siehe auch  
 [Abfragen erstellen mit FetchXML](/dynamics365/customer-engagement/developer/build-queries-fetchxml)   
 [Auslagern von umfangreichen Ergebnissätzen mit FetchXML](org-service/page-large-result-sets-with-fetchxml.md)   
 [Fetch-XML-Schema](fetchxml-schema.md)   
 <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>   
 <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>   
 <xref:Microsoft.Xrm.Sdk.Query.FetchExpression>
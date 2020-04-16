---
title: Die ConditionExpression-Klasse verwenden (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie mehr dazu, wie Sie die ConditionExpression-Klasse verwenden können, um ein Attribut mit einem Wert oder einer Wertemenge zu vergleichen, indem Sie einen Operator verwenden, wie beispielsweise &quot;Ist gleich&quot; oder &quot;Größer als&quot;
ms.custom: ''
ms.date: 10/31/2018
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
ms.openlocfilehash: 84ac9bf64031fcf27e8b7602db36d35025aff7bd
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155462"
---
# <a name="use-the-conditionexpression-class"></a>Verwenden der ConditionExpression-Klasse

In Common Data Service können Sie die <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>-Klasse verwenden, um ein Attribut mit einem Wert oder einer Wertemenge zu vergleichen, indem Sie einen Operator verwenden, wie beispielsweise "Ist gleich" oder "Größer als". Bei der `ConditionExpression`-Klasse können Sie Bedingungsausdrücke als Parameter an andere Klassen übergeben, wie beispielsweise <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> und <xref:Microsoft.Xrm.Sdk.Query.FilterExpression>.  
  
 In der folgenden Tabelle sind die Eigenschaften aufgelistet, die Sie festlegen können, um eine Bedingung mithilfe der `ConditionExpression`-Klasse zu erstellen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression.AttributeName>|Gibt den logischen Namen des Attributs im Bedingungsausdruck an.|  
|<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression.Operator>|Gibt den Bedingungsoperator an. Dies wird mit der <xref:Microsoft.Xrm.Sdk.Query.ConditionOperator>-Enumeration festgelegt.|  
|<xref:Microsoft.Xrm.Sdk.Query.ConditionExpression.Values>|Gibt den Wert des Attributs an.|  
  
 Wenn Sie die Methode <xref:Microsoft.Xrm.Sdk.Query.FilterExpression.AddCondition(Microsoft.Xrm.Sdk.Query.ConditionExpression)> (oder den Konstruktor für <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>) verwenden, ist es wichtig zu wissen, ob das Array als mehrere Werte oder als Array hinzugefügt wird.  
  
 Das folgende Codebeispiel zeigt zwei unterschiedliche Ergebnisse, abhängig davon, wie das Array verwendet wird.  
  
```csharp  
string[] values = new string[] { "Value1", "Value2" };  
ConditionExpression c = new ConditionExpression("name", ConditionOperator.In, values);  
Console.WriteLine(c.Values.Count); //This will output 2   
string[] values = new string[] { "Value1", "Value2" }object value = values;  
ConditionExpression c = new ConditionExpression("name", ConditionOperator.In, value);  
Console.WriteLine(c.Values.Count); //This will output 1  
  
```  
  
 In einigen Fällen ist erforderlich, entweder in `object[]` oder `object` umzuwandeln, je nach dem gewünschten Verhalten.  
  
 Wenn Sie eine Bedingung erstellen, die einen Attributwert mit einer Enumeration vergleicht, wie beispielsweise ein Statuscode, müssen Sie die Methode `ToString` verwenden, um den Wert in eine Zeichenfolge zu konvertieren.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird gezeigt, wie die `ConditionExpression`-Klasse verwendet wird.  
  
```csharp  
  
//  Query using ConditionExpression    
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
Console.WriteLine();    
Console.WriteLine("Query using Query Expression with ConditionExpression and FilterExpression");    
Console.WriteLine("---------------------------------------");    
foreach (var a in result1.Entities)    
{  
      Console.WriteLine("Name: " + a.Attributes["firstname"] + " " + a.Attributes["lastname"]);    
}    
Console.WriteLine("---------------------------------------");  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt, wie die `ConditionExpression`-Klasse verwendet wird, um auf den Status "Inaktiv" zu testen.  
  
```csharp  
  
ConditionExpression condition3 = new ConditionExpression();  
condition3.AttributeName = "statecode";  
condition3.Operator = ConditionOperator.Equal;  
condition3.Values.Add(AccountState.Active);  
  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen](build-queries-with-queryexpression.md)   
 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 [Die FilterExpression-Klasse verwenden](use-filterexpression-class.md)   
 <xref:Microsoft.Xrm.Sdk.Query.ConditionExpression>
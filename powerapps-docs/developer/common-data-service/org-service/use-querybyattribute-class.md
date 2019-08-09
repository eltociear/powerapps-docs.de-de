---
title: Verwenden Sie die QueryByAttribute-Klasse (Common Data Service) | Microsoft Docs
description: 'Sie können die QueryByAttribute-Klasse zum Erstellen von Abfragen verwenden, die eine Gruppe von Attributen hinsichtlich einer Gruppe von Werten testen.'
ms.custom: ''
ms.date: 05/03/2019
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

# <a name="use-the-querybyattribute-class"></a>Verwenden der QueryByAttribute-Klasse

Sie können die <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>-Klasse zum Erstellen von Abfragen verwenden, die eine Gruppe von Attributen hinsichtlich einer Gruppe von Werten testen. Verwenden Sie diese Klasse mit der <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>-Methode oder der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest> Methode.
  
 In der folgenden Tabelle sind die Eigenschaften aufgelistet, die Sie festlegen können, um einen Abfrageausdruck mithilfe der <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>-Klasse zu erstellen.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.EntityName>|Gibt an, welcher Typ der Entität abgerufen wird. Ein Abfrageausdruck kann nur eine Sammlung eines Entitätstyps abrufen. Sie können diesen Wert über den <xref:Microsoft.Xrm.Sdk.Query.QueryExpression>-Konstruktor weitergeben.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.ColumnSet>|Gibt den Satz von Attributen (Spalten) für den Abruf an.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.Attributes>|Gibt den Satz von Attributen an, die in der Abfrage ausgewählt werden.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.Values>|Gibt die Attributwerte an, nach denen gesucht wird, wenn die Abfrage ausgeführt wird.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.Orders>|Gibt die Reihenfolge an, in der die Datensätze von der Abfrage zurückgegeben werden.|  
|<xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute.PageInfo>|Gibt die Anzahl von Seiten und die Anzahl der Datensätze pro Seite an, die von der Abfrage zurückgegeben werden.|  
  
 Im folgenden Code wird gezeigt, wie die `QueryByAttribute`-Klasse verwendet wird.  
  
```csharp  
//  Create query using querybyattribute      
QueryByAttribute querybyexpression = new QueryByAttribute("account");      
querybyexpression.ColumnSet = new ColumnSet("name", "address1_city", "emailaddress1");  
  
//  Attribute to query      
querybyexpression.Attributes.AddRange("address1_city");  
  
//  Value of queried attribute to return      
querybyexpression.Values.AddRange("Detroit");      
  
//  Query passed to the service proxy      
EntityCollection retrieved = _serviceProxy.RetrieveMultiple(querybyexpression);     
  
//  Iterate through returned collection      
foreach (var c in retrieved.Entities)      
{  
      System.Console.WriteLine("Name: " + c.Attributes["name"]);  
      System.Console.WriteLine("Address: " + c.Attributes["address1_city"]);        
      System.Console.WriteLine("E-mail: " + c.Attributes["emailaddress1"]);      
}  
  
```  
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit QueryExpression](build-queries-with-queryexpression.md)   
 <xref:Microsoft.Xrm.Sdk.Query.QueryByAttribute>
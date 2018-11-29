---
title: Bestellergebnisse mithilfe von Entitätsattributen mit LINQ (Common Data Service für Apps) | Microsoft Docs
description: 'Infos zu Such- oder Optionen (Auswahlliste)-Attributen, um Ergebnisse innerhalb der LINQ-Abfrage zu finden.'
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
# <a name="order-results-using-entity-attributes-with-linq"></a>Bestellergebnisse mithilfe von LINQ der Entitätsattributen

In Common Data Service(CDS) für Apps können Sie Such- oder OptionSet (Auswahlliste)-Attribute verwenden, um Ergebnisse innerhalb der LINQ-Abfrage zu sortieren. Dieses Thema zeigt verschiedene Beispiele dieser Art von Abfragen an.  
  
## <a name="using-a-lookup-value-to-order-by"></a>Verwenden eines Suchwerts für Bestellt durch  

Das folgende Beispiel zeigt das Suchattribut `PrimaryContactId` in einer `Order By` Klausel.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_orderbylookup = from a in svcContext.AccountSet
                           where a.Address1_Name == "Contoso Pharmaceuticals"
                           orderby a.PrimaryContactId
                           select new
                           {
                            a.Name,
                            a.Address1_City
                           };
 foreach (var a in query_orderbylookup)
 {
  System.Console.WriteLine(a.Name + " " + a.Address1_City);
 }
}

```
  
## <a name="using-a-picklist-to-order-by"></a>Verwendung einer Auswahlliste für Bestellt durch  

Das folgende Beispiel zeigt uns die Verwendung des Suchwerts für Bestellt durch.  
  
```csharp

using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_orderbypicklist = from c in svcContext.ContactSet
                             where c.LastName != "Parker" &&
                             c.AccountRoleCode != null
                             orderby c.AccountRoleCode, c.FirstName
                             select new
                             {
                              AccountRole = c.FormattedValues["accountrolecode"],
                              c.FirstName,
                              c.LastName
                             };
 foreach (var c in query_orderbypicklist)
 {
  System.Console.WriteLine(c.AccountRole + " " +
   c.FirstName + " " + c.LastName);
 }
}
```
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit LINQ (.NET Language-integrierte Abfrage)](build-queries-with-linq-net-language-integrated-query.md)   
 [Auslagern von umfangreichen Ergebnissätzen mit LINQ](page-large-result-sets-linq.md)
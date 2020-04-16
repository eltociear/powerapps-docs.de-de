---
title: Anordnen von Ergebnissen mit Hilfe von Entitätsattributen mit LINQ (Common Data Service) | Microsoft-Dokumentation
description: Infos zu Such- oder Optionen (Auswahlliste)-Attributen, um Ergebnisse innerhalb der LINQ-Abfrage zu finden.
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
ms.openlocfilehash: e665e66b4ec138532dd5476561b6cc0c7becc330
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156026"
---
# <a name="order-results-using-entity-attributes-with-linq"></a>Bestellergebnisse mithilfe von LINQ der Entitätsattributen

In Common Data Service (Common Data Service) für Apps können Sie Such- oder Optionssatz (Auswahlliste)-Attribute verwenden, um Ergebnisse innerhalb einer LINQ-Abfrage anzuordnen. Dieses Thema zeigt verschiedene Beispiele dieser Art von Abfragen an.  
  
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
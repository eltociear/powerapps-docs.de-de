---
title: Auslagern von umfangreichen Ergebnissätzen mit LINQ (Common Data Service) | Microsoft Docs
description: 'Lesen Sie, wie Sie Ergebnisse einer großen .NET-sprachintegrierten Abfrage (LINQ), Language-Integrated Query auslagern können, indem Sie die Nehmen- und Überspringen-Operatoren verwenden'
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
# <a name="page-large-result-sets-with-linq"></a>Auslagern von umfangreichen Ergebnissätzen mit LINQ

In Common Data Service können Sie die Ergebnisse einer großen .NET-sprachintegrierten Abfrage (LINQ, Language-Integrated Query) auslagern, indem Sie die Operatoren `Take` und `Skip` verwenden. Der `Take`-Operator ruft eine angegebene Anzahl von Ergebnisse ab, und der `Skip`-Operator überspringt eine angegebene Anzahl von Ergebnissen.  
  
## <a name="linq-paging-example"></a>LINQ-Beispiel  

Im folgenden Beispiel wird veranschaulicht, wie Ergebnisse einer LINQ-Abfrage mithilfe der Operatoren `Take` und `Skip` auslagern:  
  
```csharp
int pageSize = 5;

var accountsByPage = (from a in svcContext.AccountSet
                      select new Account
                      {
                       Name = a.Name,
                      });
System.Console.WriteLine("Skip 10 accounts, then Take 5 accounts");
System.Console.WriteLine("======================================");
foreach (var a in accountsByPage.Skip(2 * pageSize).Take(pageSize))
{
 System.Console.WriteLine(a.Name);
}

```
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit LINQ (.NET Language-integrierte Abfrage)](build-queries-with-linq-net-language-integrated-query.md)   
 [LINQ-Abfragebeispiele](linq-query-examples.md)
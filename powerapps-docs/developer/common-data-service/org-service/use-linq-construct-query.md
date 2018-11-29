---
title: Verwenden von LINQ zum Erstellen einer Abfrage (Common Data Service für Apps) | Microsoft Docs
description: 'Hier wird beschrieben, wie der Abfrageanbieter .NET Language-Integrated Query(LINQ) in Dynamics 365 zum Erstellen einer Abfrage verwendet wird'
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
# <a name="use-linq-to-construct-a-query"></a>Verwenden von LINQ zum Erstellen einerAbfrage

Der Abfrageanbieter .NET Language-Integrated Query(LINQ) in Common Data Service für Apps verwendet eine Standard-LINQ-Syntax. Der erste Schritt zum Erstellen einer LINQ-Abfrage besteht darin, die relevanten Entitätstypen und die Beziehungen zwischen diesen zu identifizieren. Sie können dann die Datenquelle und die anderen Abfrageparameter angeben.  

 Die `from`-Klausel wird verwendet, um eine einzelne „Stamm“-Entität zurückzugeben. Der Abfragenanbieter kann nur Entitäten eines einzigen Entitätstyps zurückgeben. `orderby` und `select`-Klauseln müssen auf diese Stammentität verweisen. Mit `join`-Klauseln können Sie Entitäten einer Beziehung zur „Stamm“-Entität hinzuzufügen.  

<a name="bkmk_operators"></a>   

## <a name="linq-operators"></a>LINQ-Operatoren  
 Alle LINQ-Abfrageausdrücke haben ein ähnliches Format. In der folgenden Tabelle sind die häufigsten Klauseln in einem LINQ-Abfrageausdruck aufgeführt, wenn der LINQ-Abfragenanbieter von CDS für Apps verwendet wird.  

### <a name="from"></a>von  
 Wenn Sie den generierten Dienstkontext und ältere Bindung verwenden, verwenden Sie den Entitätssatz, wie z. B. `IQueryable` `AccountSet`, im generierten Kontext.  

 Wenn Sie keinen generierten Kontext verwenden, können Sie mit der `CreateQuery`-Methode im Servicekontext der Organisation auf CDS für Apps-Entitäten zugreifen.  

 Beispiel:  

 Verwenden des generierten Servicekontexts:  

```csharp  
var query1 = from c in context.ContactSet  
select c;  
```  

 Verwenden der `CreateQuery`-Methode:  

```csharp  
var query1 = from c in context.CreateQuery<Contact>()  
select c;  
```  

### <a name="join"></a>join  
 Die `join`-Klausel stellt eine innere Verknüpfung dar. Verwenden Sie die Klausel, um mit zwei oder mehreren Entitäten zu arbeiten, die mit einem gemeinsamen Attributwert verknüpft werden können.  

 Beispiel:  

```csharp  
from c in context.ContactSet  
join a in context.AccountSet on c.ContactId equals a.PrimaryContactId.Id  
```  

### <a name="where"></a>Dabei gilt Folgendes:  
 Die `where`-Klausel wendet einen Filter auf die Ergebnisse an. Dazu wird häufig ein Boolescher Ausdruck verwendet. Der Filter gibt an, welche Elemente von der Quellreihenfolge auszuschließen sind. Jede `where`-Klausel kann nur Bedingungen für einen einzelnen Entitätstyp enthalten. Eine zusammengesetzte Bedingung, die mehrere Entitäten mit einbezieht, ist ungültig. Stattdessen sollte jede Entität in separaten `where`-Klauseln gefiltert werden.  

 Beispiel:  

```csharp  
from a in context.AccountSet  
where (a.Name.StartsWith("Contoso") && a.Address1_StateOrProvince == "WA")  
```  

### <a name="orderby"></a>orderby  
 Der `orderby`-Operator stellt die zurückgegebenen Abfragenattribute in eine bestimmte Reihenfolge.  

 Beispiel:  

```csharp  
var query1 = from c in context.CreateQuery<Contact>()     
    orderby c.FullName ascending     
    select c;  
foreach ( var q in query1)     
{  
    Console.WriteLine(q.FirstName + " " + q.LastName);     
}  
```  

### <a name="select"></a>Auswählen  
 Die `select`-Klausel definiert die Form der zurückgegebenen Daten. Die Klausel erstellt einen Spaltensatz auf der Grundlage der Abfrageausdruckergebnisse. Sie können auch eine Instanz eines neuen Objekts definieren, mit dem gearbeitet werden soll. Das neu mit der `select`-Klausel erstellte Objekt wird nicht auf dem Server erstellt, sondern ist eine lokale Instanz.  

 Beispiel:  

```csharp  
select new Contact     
{  
    ContactId = c.ContactId,  
    FirstName = c.FirstName,  
    LastName = c.LastName,  
    Address1_Telephone1 = c.Address1_Telephone1     
};  
```  

<a name="limitations"></a>   

## <a name="linq-limitations"></a>LINQ-Einschränkungen  

 Der LINQ-Abfragenanbieter unterstützt eine Teilmenge der LINQ-Operatoren. Nicht alle Bedingungen, die in LINQ ausgedrückt werden können, werden unterstützt. In der folgenden Tabelle sind einige Einschränkungen für die grundlegenden LINQ-Operatoren aufgeführt.  


|   LINQ-Operator   |                                                                                                                                              Einschränkungen                                                                                                                                              |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      `join`       |                                                                                                                Stellt eine innere oder äußere Verknüpfung dar. Nur linke äußere Verknüpfungen werden unterstützt.                                                                                                                |
|      `from`       |                                                                                                                                 Unterstützt eine einzige `from`-Klausel pro Abfrage.                                                                                                                                 |
|      `where`      | Auf der linken Seite der Klausel muss ein Attributname und auf der rechten Seite der Klausel muss ein Wert stehen. Sie können die linke Seite nicht auf eine Konstante festlegen. Es dürfen keine Konstanten auf beiden Klauselseiten stehen.<br /><br /> Unterstützt die `String`-Funktionen `Contains`, `StartsWith`, `EndsWith` und `Equals`. |
|     `groupBy`     |                               Nicht unterstützt. FetchXML unterstützt das Gruppieren von Optionen, die nicht mithilfe des LINQ-Abfragenanbieter verfügbar sind. Weitere Informationen: [FetchXML-Aggregation verwenden](/dynamics365/customer-engagement/developer/use-fetchxml-aggregation)                               |
|     `orderBy`     |                                                                                                                  Unterstützt die Sortierung nach Entitätsattributen, wie `Contact.FullName`.                                                                                                                  |
|     `select`      |                                                                                                                       Unterstützt anonyme Typen, Konstruktoren und Initialisierer.                                                                                                                       |
|      `last`       |                                                                                                                                 Der `last`-Operator wird nicht unterstützt.                                                                                                                                 |
| `skip` und `take` |                                                                                       Unterstützt `skip` und `take` mit serverseitigem Paging. Der Wert `skip` muss größer oder gleich dem Wert `take` sein.                                                                                        |
|    `aggregate`    |                             Nicht unterstützt. FetchXML unterstützt die Aggregation von Optionen, die nicht mithilfe des LINQ-Abfragenanbieter verfügbar sind. Weitere Informationen: [FetchXML-Aggregation verwenden](/dynamics365/customer-engagement/developer/use-fetchxml-aggregation)                              |

<a name="filter"></a>   

## <a name="filter-multiple-entities"></a>Filtern mehrerer Entitäten  

 Sie können komplexe .NET-sprachintegrierte Abfrage(LINQ)-Abfragen in CDS für Apps erstellen. Sie können mehrere `Join`-Klauseln mit Filterklauseln verwenden, um ein Ergebnis zu erhalten, das nach Attributen aus mehreren Entitäten gefiltert ist.  

 Das folgende Beispiel zeigt, wie Sie eine LINQ-Abfrage erstellen, die mit zwei Entitäten arbeitet und das Ergebnis anhand von Werten aus den einzelnen Entitäten filtert.  

 ```csharp
 using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_where3 = from c in svcContext.ContactSet
                    join a in svcContext.AccountSet
                    on c.ContactId equals a.PrimaryContactId.Id
                    where a.Name.Contains("Contoso")
                    where c.LastName.Contains("Smith")
                    select new
                    {
                     account_name = a.Name,
                     contact_name = c.LastName
                    };

 foreach (var c in query_where3)
 {
  System.Console.WriteLine("acct: " +
   c.account_name +
   "\t\t\t" +
   "contact: " +
   c.contact_name);
 }
}
 ```
### <a name="see-also"></a>Siehe auch  
 [Beispiel: Erstellen einer LINQ-Abfrage](/dynamics365/customer-engagement/developer/org-service/sample-create-linq-query.md)   
 [Beispiel: LINQ-Abfragenbeispiele](/dynamics365/customer-engagement/developer/org-service/sample-complex-linq-queries.md)   
 [Erstellen von Abfragen mit LINQ (.NET Language-integrierte Abfrage)](/dynamics365/customer-engagement/developer/org-service/build-queries-with-linq-net-language-integrated-query.md)   
 [Verwenden von spät gebundenen Entitätsklassen mit einer LINQ-Abfrage](/dynamics365/customer-engagement/developer/org-service/use-late-bound-entity-class-linq-query.md)   
 [Blog: LINQPad 4 Driver für Dynamics CRM REST/Web API sind verfügbar auf CodePlex](http://blogs.msdn.com/b/crminthefield/archive/2015/06/11/linqpad-4-driver-for-dynamics-crm-rest-webapi-are-available-on-codeplex.aspx)
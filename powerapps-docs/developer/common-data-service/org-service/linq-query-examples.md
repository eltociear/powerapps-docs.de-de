---
title: <Topic Title> (Common Data Service for Apps) | Microsoft Docs
description: <Description>
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
# <a name="linq-query-examples-using-organizationservicecontext-with-common-data-service-for-apps"></a>LINQ-Abfragenbeispiele mithilfe von OrganizationServiceContext mit Common Data Service für Apps

Dieses Thema enthält viele Code-Beispiele für INQ-Abfragen.  
  
<a name="SimpleWhereClause"></a>   
## <a name="simple-where-clause"></a>Einfache Wobei-Klausel  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Konten abrufen, wobei der Name "Contoso" enthält.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_where1 = from a in svcContext.AccountSet
        where a.Name.Contains("Contoso")
        select a;
    foreach (var a in query_where1)
    {
        System.Console.WriteLine(a.Name + " " + a.Address1_City);
    }
}
```  
  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Konten abrufen, wobei der Na,e "Contoso" und Address1_City "Redmond" ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_where2 = from a in svcContext.AccountSet
                    where a.Name.Contains("Contoso")
                    where a.Address1_City == "Redmond"
                    select a;

    foreach (var a in query_where2)
    {
        System.Console.WriteLine(a.Name + " " + a.Address1_City);
    }
}
``` 
  
<a name="JoinandSimpleWhereClause"></a>   
## <a name="join-and-simple-where-clause"></a>Verknüpfung und einfache und Wobei-Klausel  
 Das folgende Beispiel zeigt, wie der Firma-Name und der Kontakt LastName abgerufen werden, wobei der Firma-Name "Contoso" enthält, und der Kontakt LastName "Smith" enthält, und der Kontakt der primäre Kontakt für die Firma ist.  
  
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
  
<a name="UsingtheDistinctOperator"></a>   
## <a name="use-the-distinct-operator"></a>Verwenden des eindeutigen Operators  
 Das folgende Beispiel zeigt, wie Sie eine eindeutige Liste von Kontaktnachnamen abrufen. Obwohl es möglicherweise viele Duplikate gibt, wird jeder Name nur einmal aufgelistet.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_distinct = (from c in svcContext.ContactSet
                       select c.LastName).Distinct();
    foreach (var c in query_distinct)
    {
        System.Console.WriteLine(c);
    }
}
```
  
<a name="SimpleInnerJoin"></a>   
## <a name="simple-inner-join"></a>Einfache innere Verknüpfung  
Das folgende Beispiel zeigt, wie Informationen zu einer Firma und dem Kontakt, der als primärer Kontakt für die Firma aufgelistet ist, abgerufen werden.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join1 = from c in svcContext.ContactSet
                   join a in svcContext.AccountSet
                  on c.ContactId equals a.PrimaryContactId.Id
                   select new
                   {
                    c.FullName,
                    c.Address1_City,
                    a.Name,
                    a.Address1_Name
                   };
    foreach (var c in query_join1)
    {
        System.Console.WriteLine("acct: " +
        c.Name +
        "\t\t\t" +
        "contact: " +
        c.FullName);
    }
}
```  
  
<a name="SelfJoin"></a>   
## <a name="self-join"></a>Selbstverknüpfung  
 Das folgende Beispiel zeigt, wie Informationen zu Firmen abgerufen werden, wobei eine Firma die übergeordnete Firma für eine Firma ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join5 = from a in svcContext.AccountSet
                   join a2 in svcContext.AccountSet
                   on a.ParentAccountId.Id equals a2.AccountId

                   select new
                   {
                    account_name = a.Name,
                    account_city = a.Address1_City
                   };
    foreach (var c in query_join5)
    {
        System.Console.WriteLine(c.account_name + "  " + c.account_city);
    }
}
```
  
<a name="DoubleJoin"></a>   
## <a name="double-and-multiple-joins"></a>Doppelte und mehrere Verknüpfungen  
 Das folgende Beispiel zeigt, wie die Informationen von Firma, Kontakt und Lead abgerufen werden, wobei der Kontakt der primäre Kontakt für die Firma ist und der Lead der Ursprungslead für die firma war.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join4 = from a in svcContext.AccountSet
                   join c in svcContext.ContactSet
                   on a.PrimaryContactId.Id equals c.ContactId
                   join l in svcContext.LeadSet
                   on a.OriginatingLeadId.Id equals l.LeadId
                   select new
                   {
                    contact_name = c.FullName,
                    account_name = a.Name,
                    lead_name = l.FullName
                   };
    foreach (var c in query_join4)
    {
        System.Console.WriteLine(c.contact_name +
        "  " +
        c.account_name +
        "  " +
        c.lead_name);
    }
}
```  
  
 Das folgende Beispiel zeigt, wie die Informationen Firmen- und Kontaktinformationen abgerufen werden, wobei die Firma die übergeordnete Firma einer Firma ist und der Kontakt der primäre Kontakt für die Firma ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join6 = from c in svcContext.ContactSet
                   join a in svcContext.AccountSet
                   on c.ContactId equals a.PrimaryContactId.Id
                   join a2 in svcContext.AccountSet
                   on a.ParentAccountId.Id equals a2.AccountId
                   select new
                   {
                    contact_name = c.FullName,
                    account_name = a.Name
                   };
    foreach (var c in query_join6)
    {
        System.Console.WriteLine(c.contact_name + "  " + c.account_name);
    }
}
```
  
<a name="JoinUsingEntityFields"></a>   
## <a name="join-using-entity-fields"></a>Verknüpfen unter Verwendung von Entitätsfeldern  
 Das folgende Beispiel zeigt, wie Sie Informationen über Firmen aus einer Liste abrufen.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var list_join = (from a in svcContext.AccountSet
                  join c in svcContext.ContactSet
                  on a.PrimaryContactId.Id equals c.ContactId
                  where a.Name == "Contoso Ltd" &&
                  a.Address1_Name == "Contoso Pharmaceuticals"
                  select a).ToList();
    foreach (var c in list_join)
    {
        System.Console.WriteLine("Account " + list_join[0].Name
        + " and it's primary contact "
        + list_join[0].PrimaryContactId.Id);
    }
}
```  
  
<a name="LeftJoin"></a>   
## <a name="late-binding-left-join"></a>Links-Verknüpfung mit später Bindung  
 Das folgende Beispiel zeigt eine Linksverknüpfung. Eine Linksverknüpfung ist so ausgelegt, dass übergeordnete Elemente mit und ohne untergeordnete Elemente von zwei Quellen zurückgegeben werden. Es gibt eine Korrelation zwischen übergeordnetem und untergeordnetem Element, aber ein untergeordnetes Element kann nicht vorhanden sein.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_join8 = from a in svcContext.AccountSet
                   join c in svcContext.ContactSet
                   on a.PrimaryContactId.Id equals c.ContactId
                   into gr
                   from c_joined in gr.DefaultIfEmpty()
                   select new
                   {
                    contact_name = c_joined.FullName,
                    account_name = a.Name
                   };
    foreach (var c in query_join8)
    {
        System.Console.WriteLine(c.contact_name + "  " + c.account_name);
    }
}
``` 
  
<a name="UsingtheEqualsOperator"></a>   
## <a name="use-the-equals-operator"></a>Verwenden des Gleich-Operators  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten abrufen, wobei FirstName "Colin" ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_equals1 = from c in svcContext.ContactSet
                     where c.FirstName.Equals("Colin")
                     select new
                     {
                      c.FirstName,
                      c.LastName,
                      c.Address1_City
                     };
    foreach (var c in query_equals1)
    {
        System.Console.WriteLine(c.FirstName +
        " " + c.LastName +
        " " + c.Address1_City);
    }
}
``` 
  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten abrufen, wobei FamilyStatusCode „3” ist. Dieses entspricht der **Familienstand**-Option **Geschieden**.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_equals2 = from c in svcContext.ContactSet
                     where c.FamilyStatusCode.Equals(3)
                     select new
                     {
                      c.FirstName,
                      c.LastName,
                      c.Address1_City
                     };
    foreach (var c in query_equals2)
    {
        System.Console.WriteLine(c.FirstName +
        " " + c.LastName +
        " " + c.Address1_City);
    }
}
``` 
  
<a name="UsingtheNotEqualsOperator"></a>   
## <a name="use-the-not-equals-operator"></a>Verwenden des Ungleich-Operators  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten abrufen, wobei Address1_City nicht "Redmond" ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_ne1 = from c in svcContext.ContactSet
                 where c.Address1_City != "Redmond"
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };
    foreach (var c in query_ne1)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
```  
  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten abrufen, wobei FirstName nicht "Colin" ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_ne2 = from c in svcContext.ContactSet
                 where !c.FirstName.Equals("Colin")
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };

    foreach (var c in query_ne2)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
```  
  
<a name="BKMK_UsingMethodBasedLINQQueryWithWhereClause"></a>   
## <a name="use-a-method-based-linq-query-with-a-where-clause"></a>Verwenden einer methodenbasierten LINQ-Abfrage mit einer Wobei-Klausel  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten abrufen, wobei LastName "Smith" ist oder "Colin" enthält.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var methodResults = svcContext.ContactSet
    .Where(a => a.LastName == "Smith");
    var methodResults2 = svcContext.ContactSet
    .Where(a => a.LastName.StartsWith("Smi"));
    Console.WriteLine();
    Console.WriteLine("Method query using Lambda expression");
    Console.WriteLine("---------------------------------------");
    foreach (var a in methodResults)
    {
        Console.WriteLine("Name: " + a.FirstName + " " + a.LastName);
    }
    Console.WriteLine("---------------------------------------");
    Console.WriteLine("Method query 2 using Lambda expression");
    Console.WriteLine("---------------------------------------");
    foreach (var a in methodResults2)
    {
        Console.WriteLine("Name: " + a.Attributes["firstname"] +
        " " + a.Attributes["lastname"]);
    }
}
``` 
  
<a name="BKMK_UsingGreaterThanOperator"></a>   
## <a name="use-the-greater-than-operator"></a>Verwenden des Größer-als-Operators  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten mit einem Geburtstags-Datum später als 5. Februar 2010 abrufen.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_gt1 = from c in svcContext.ContactSet
                 where c.Anniversary > new DateTime(2010, 2, 5)
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };

    foreach (var c in query_gt1)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
``` 
  
 Das folgende Beispiel zeigt, wie Sie Kontakte mit einem CreditLimit von mehr als $20.000 abrufen.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_gt2 = from c in svcContext.ContactSet
                 where c.CreditLimit.Value > 20000
                 select new
                 {
                  c.FirstName,
                  c.LastName,
                  c.Address1_City
                 };
    foreach (var c in query_gt2)
    {
        System.Console.WriteLine(c.FirstName + " " +
        c.LastName + " " + c.Address1_City);
    }
}
``` 
  
<a name="BKMK_UsingGreaterThanOrEqualsAndLessThanOrEqualsOperators"></a>   
## <a name="use-the-greater-than-or-equals-and-less-than-or-equals-operators"></a>Verwenden der Größer als- oder Gleich- oder Kleiner als-Operatoren  
 Das folgende Beispiel zeigt, wie Sie Kontakte mit einem CreditLimit von mehr als $200 und weniger als $400 abrufen.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
 var query_gele1 = from c in svcContext.ContactSet
                   where c.CreditLimit.Value >= 200 &&
                   c.CreditLimit.Value <= 400
                   select new
                   {
                    c.FirstName,
                    c.LastName
                   };
 foreach (var c in query_gele1)
 {
  System.Console.WriteLine(c.FirstName + " " + c.LastName);
 }
}
``` 
  
<a name="BKMK_UsingContainsOperator"></a>   
## <a name="use-the-contains-operator"></a>Verwenden des Enthält-Operators  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten abrufen, wobei Description "Alpine" enhält.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_contains1 = from c in svcContext.ContactSet
                       where c.Description.Contains("Alpine")
                       select new
                       {
                        c.FirstName,
                        c.LastName
                       };
    foreach (var c in query_contains1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```
  
<a name="BKMK_UsingDoesNotContainOperator"></a>   
## <a name="use-the-does-not-contain-operator"></a>Verwenden des Enthält nicht-Operators  
 Das folgende Beispiel zeigt, wie Sie eine Liste von Kontakten abrufen, wobei Description "Coho" nicht enhält.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_contains2 = from c in svcContext.ContactSet
                       where !c.Description.Contains("Coho")
                       select new
                       {
                        c.FirstName,
                        c.LastName
                       };
    foreach (var c in query_contains2)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  
  
<a name="BKMK_UsingEndsWithOperator"></a>   
## <a name="use-the-startswith-and-endswith-operators"></a>Verwenden der StartsWith- und EndsWith-Operatoren  
 Das folgende Beispiel zeigt, wie Sie Kontakte abrufen, wobei FirstName mit "Bri" beginnt.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_startswith1 = from c in svcContext.ContactSet
                         where c.FirstName.StartsWith("Bri")
                         select new
                         {
                          c.FirstName,
                          c.LastName
                         };
    foreach (var c in query_startswith1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
 Das folgende Beispiel zeigt, wie Sie Kontakte abrufen, wobei LastName mit "cox" endet.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_endswith1 = from c in svcContext.ContactSet
                       where c.LastName.EndsWith("cox")
                       select new
                       {
                        c.FirstName,
                        c.LastName
                       };
    foreach (var c in query_endswith1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
<a name="BKMK_UsingAndOrOperators"></a>   
## <a name="use-the-and-and-or-operators"></a>Verwenden der Und- und Oder-Operatoren  
 Das folgende Beispiel zeigt, wie Sie Kontakte abrufen, wobei Address1_City "Redmond" oder "Bellevue" ist, und ein CreditLimit, das größer als $200 ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_andor1 = from c in svcContext.ContactSet
                    where ((c.Address1_City == "Redmond" ||
                    c.Address1_City == "Bellevue") &&
                    (c.CreditLimit.Value != null &&
                    c.CreditLimit.Value >= 200))
                    select c;

    foreach (var c in query_andor1)
    {
        System.Console.WriteLine(c.LastName + ", " + c.FirstName + " " +
        c.Address1_City + " " + c.CreditLimit.Value);
    }
}
```  

  
<a name="BKMKUsingOrderByOperator"></a>   
## <a name="use-the-orderby-operator"></a>Verwenden des OrderBy-Operators  
 Das folgende Beispiel zeigt, wie die Kontakte abgerufen werden, die in absteigender Reihenfolge nach CreditLimit angeordnet sind.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_orderby1 = from c in svcContext.ContactSet
                      where !c.CreditLimit.Equals(null)
                      orderby c.CreditLimit descending
                      select new
                      {
                       limit = c.CreditLimit,
                       first = c.FirstName,
                       last = c.LastName
                      };
    foreach (var c in query_orderby1)
    {
        System.Console.WriteLine(c.limit.Value + " " +
        c.last + ", " + c.first);
    }
}
```   

  
 Das folgende Beispiel zeigt, wie die Kontakte abgerufen werden, die in absteigender Reihenfolge nach LastName und in aufsteigender Reihenfolge nach FirstName angeordnet sind.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_orderby2 = from c in svcContext.ContactSet
                      orderby c.LastName descending,
                      c.FirstName ascending
                      select new
                      {
                       first = c.FirstName,
                       last = c.LastName
                      };

    foreach (var c in query_orderby2)
    {
        System.Console.WriteLine(c.last + ", " + c.first);
    }
}
```  

  
<a name="BKMK_UsingFirstAndSingleOperators"></a>   
## <a name="use-the-first-and-single-operators"></a>Verwenden der Erster- und Einziger-Operatoren  
 Das folgende Beispiel zeigt, wie Sie nur den ersten zurückgegebenen Kontaktdatensatz abrufen, und nur einen Kontaktdatensatz abrufen, der mit dem Kriterium übereinstimmt.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    Contact firstcontact = svcContext.ContactSet.First();

    Contact singlecontact = svcContext.ContactSet.Single(c => c.ContactId == _contactId1);
    System.Console.WriteLine(firstcontact.LastName + ", " +
    firstcontact.FirstName + " is the first contact");
    System.Console.WriteLine("==========================");
    System.Console.WriteLine(singlecontact.LastName + ", " +
    singlecontact.FirstName + " is the single contact");
}
```  

  
<a name="BKMK_RetrievingFormattedValues"></a>   
## <a name="retrieving-formatted-values"></a>Abrufen von formatierten Werten  
 Das folgende Beispiel zeigt, wie Sie eine Beschriftung für eine Optionssatz-Option abrufen, in diesem Fall den Wert für aktuellen Status des Datensatzes.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var list_retrieve1 = from c in svcContext.ContactSet
                      where c.ContactId == _contactId1
                      select new { StatusReason = c.FormattedValues["statuscode"] };
    foreach (var c in list_retrieve1)
    {
        System.Console.WriteLine("Status: " + c.StatusReason);
    }
}
```  

  
<a name="BKMK_UsingTheSkipAndTakeOperatorsWithoutPaging"></a>   
## <a name="use-the-skip-and-take-operators-without-paging"></a>Verwenden der Operatoren Auslassen und Nehmen ohne Paging 

 Das folgende Beispiel zeigt, wie nur zwei Datensätze abgerufen werden, nachdem zwei Datensätze übersprungen wurden, in denen LastName nicht "Parker" ist, mithilfe der Operatoren [Überspringen](https://msdn.microsoft.com/library/bb358985.aspx) und [Nehmen](https://msdn.microsoft.com/library/bb503062.aspx).  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{

    var query_skip = (from c in svcContext.ContactSet
                   where c.LastName != "Parker"
                   orderby c.FirstName
                   select new
                       {
                        last = c.LastName,
                        first = c.FirstName
                       }).Skip(2).Take(2);
    foreach (var c in query_skip)
    {
        System.Console.WriteLine(c.first + " " + c.last);
    }
}
```  

  
<a name="BKMK_UsingTheFirstOrDefaultAndSingleOrDefaultOperators"></a>   
## <a name="use-the-firstordefault-and-singleordefault-operators"></a>Verwenden der Operatoren FirstOrDefault und SingleOrDefault  
 Der [FirstOrDefault](https://msdn.microsoft.com/library/system.linq.enumerable.firstordefault.aspx)-Operator gibt das erste Element einer Sequenz zurück, oder einen Standardwert, wenn kein Element gefunden wird. Der [SingleOrDefault](https://msdn.microsoft.com/library/system.linq.enumerable.singleordefault.aspx)-Operator gibt ein einzelnes, spezifisches Element einer Sequenz zurück, oder einen Standardwert, wenn dieses Element nicht gefunden wird. Im folgenden Beispiel wird gezeigt, wie diese Operatoren verwendet werden.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{

    Contact firstorcontact = svcContext.ContactSet.FirstOrDefault();

    Contact singleorcontact = svcContext.ContactSet
        .SingleOrDefault(c => c.ContactId == _contactId1);


    System.Console.WriteLine(firstorcontact.FullName +
        " is the first contact");
    System.Console.WriteLine("==========================");
    System.Console.WriteLine(singleorcontact.FullName +
        " is the single contact");
}
```  

  
<a name="BKMK_UsingASelfJoinWithConditionOnLinkedEntity"></a>   
## <a name="use-a-self-join-with-a-condition-on-the-linked-entity"></a>Verwenden einer Selbstverknüpfung mit einer Bedingung für die verknüpfte Entität  
 Das folgende Beispiel zeigt, wie die Namen von zwei Firmen abgerufen werden, wobei eine Firma die übergeordnete Firma der anderen ist.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_joincond = from a1 in svcContext.AccountSet
                      join a2 in svcContext.AccountSet
                      on a1.ParentAccountId.Id equals a2.AccountId
                      where a2.AccountId == _accountId1
                      select new { Account = a1, Parent = a2 };
    foreach (var a in query_joincond)
    {
        System.Console.WriteLine(a.Account.Name + " " + a.Parent.Name);
    }
}
```  

  
<a name="BKMK_UsingTransformationInTheWhereClause"></a>   
## <a name="use-a-transformation-in-the-where-clause"></a>Verwenden von Transformationen in der Wobei-Klausel  
 Das folgende Beispiel zeigt, wie Sie einen bestimmten Kontakt abrufen, bei dem das Jahrestagsdatum später ist als der 1. Januar 2010.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_wheretrans = from c in svcContext.ContactSet
                        where c.ContactId == _contactId1 &&
                        c.Anniversary > DateTime.Parse("1/1/2010")
                        select new
                        {
                         c.FirstName,
                         c.LastName
                        };
    foreach (var c in query_wheretrans)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
<a name="BKMK_UsingAPagingSort"></a>   
## <a name="use-a-paging-sort"></a>Verwenden einer Paging-Sortierung  
 Das folgende Beispiel zeigt eine mehrspaltige Sortierung mit einer Sonderbedingung.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_pagingsort1 = (from c in svcContext.ContactSet
                          where c.LastName != "Parker"
                          orderby c.LastName ascending,
                          c.FirstName descending
                          select new { c.FirstName, c.LastName })
                          .Skip(2).Take(2);
    foreach (var c in query_pagingsort1)
    {
        System.Console.WriteLine(c.FirstName + " " + c.LastName);
    }
}
```  

  
 Das folgende Beispiel eine Paging-Sortierung, wobei die Spalte, die sortiert wird, sich von der Spalte unterscheidet, die abgerufen wird.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_pagingsort2 = (from c in svcContext.ContactSet
                          where c.LastName != "Parker"
                          orderby c.FirstName descending
                          select new { c.FirstName }).Skip(2).Take(2);
    foreach (var c in query_pagingsort2)
    {
        System.Console.WriteLine(c.FirstName);
    }
}
```  

  
 Das folgende Beispiel zeigt, wie Sie nur die ersten 10 Datensätze abrufen.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_pagingsort3 = (from c in svcContext.ContactSet
                          where c.LastName.StartsWith("W")
                          orderby c.MiddleName ascending,
                          c.FirstName descending
                          select new
                          {
                           c.FirstName,
                           c.MiddleName,
                           c.LastName
                          }).Take(10);
    foreach (var c in query_pagingsort3)
    {
        System.Console.WriteLine(c.FirstName + " " +
            c.MiddleName + " " + c.LastName);
    }
}
```  

  
<a name="BKMK_RetrievingRelatedEntityColumns"></a>   
## <a name="retrieve-related-entity-columns-for-1-to-n-relationships"></a>Abrufen von verknüpften Entitätsspalten für 1:N-Beziehungen  
 Das folgende Beispiel zeigt, wie Spalten von verknüpften Firmen- und Kontaktdatensätzen abgerufen werden.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
     var query_retrieve1 = from c in svcContext.ContactSet
                       join a in svcContext.AccountSet
                       on c.ContactId equals a.PrimaryContactId.Id
                       where c.ContactId != _contactId1
                       select new { Contact = c, Account = a };
     foreach (var c in query_retrieve1)
    {
          System.Console.WriteLine("Acct: " + c.Account.Name +
           "\t\t" + "Contact: " + c.Contact.FullName);
     }
}
```  
  
<a name="BKMK_UsingValueToRetrieveTheValueOfAnAttribute"></a>   
## <a name="use-value-to-retrieve-the-value-of-an-attribute"></a>Verwendung von Wert, um den Wert eines Attributs abzufen  
 Im folgenden Beispiel wird das Verwenden eines Werts zum Zugriff auf den Wert eines Attributs gezeigt.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{

     var query_value = from c in svcContext.ContactSet
                   where c.ContactId != _contactId2
                   select new
                   {
                    ContactId = c.ContactId != null ?
                     c.ContactId.Value : Guid.Empty,
                    NumberOfChildren = c.NumberOfChildren != null ?
                     c.NumberOfChildren.Value : default(int),
                    CreditOnHold = c.CreditOnHold != null ?
                     c.CreditOnHold.Value : default(bool),
                    Anniversary = c.Anniversary != null ?
                     c.Anniversary.Value : default(DateTime)
                   };

     foreach (var c in query_value)
     {
      System.Console.WriteLine(c.ContactId + " " + c.NumberOfChildren + 
           " " + c.CreditOnHold + " " + c.Anniversary);
     }
}
```  
  
<a name="BKMK_MultipleProjectionsNewDataTypeCastingToDifferentTypes"></a>   
## <a name="multiple-projections-new-data-type-casting-to-different-types"></a>Mehrere Projektionen, Neuer Datentyp, der zu verschiedenen Typen umgewandelt wird  
 Das folgende Beispiel zeigt mehrere Projektionen, und wie Werte in einen anderen Typ umgewandelt werden.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
     var query_projections = from c in svcContext.ContactSet
                         where c.ContactId == _contactId1
                         && c.NumberOfChildren != null && 
                         c.Anniversary.Value != null
                         select new
                         {
                          Contact = new Contact { 
                           LastName = c.LastName, 
                           NumberOfChildren = c.NumberOfChildren 
                          },
                          NumberOfChildren = (double)c.NumberOfChildren,
                          Anniversary = c.Anniversary.Value.AddYears(1),
                         };
     foreach (var c in query_projections)
     {
          System.Console.WriteLine(c.Contact.LastName + " " + 
               c.NumberOfChildren + " " + c.Anniversary);
     }
}
```  
  
<a name="BKMK_UsingTheGetAttributeValueMethod"></a>   
## <a name="use-the-getattributevalue-method"></a>Verwenden der GetAttributeValue-Methode  
 Im folgenden Beispiel wird gezeigt, wie die <xref:Microsoft.Xrm.Sdk.Entity.GetAttributeValue``1(System.String)>-Methode verwendet wird.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_getattrib = from c in svcContext.ContactSet
                       where c.GetAttributeValue<Guid>("contactid") != _contactId1
                       select new
                       {
                        ContactId = c.GetAttributeValue<Guid?>("contactid"),
                        NumberOfChildren = c.GetAttributeValue<int?>("numberofchildren"),
                        CreditOnHold = c.GetAttributeValue<bool?>("creditonhold"),
                        Anniversary = c.GetAttributeValue<DateTime?>("anniversary"),
                       };

    foreach (var c in query_getattrib)
    {
        System.Console.WriteLine(c.ContactId + " " + c.NumberOfChildren + 
            " " + c.CreditOnHold + " " + c.Anniversary);
    }
}
```  
  
<a name="mathoperators"></a>   
## <a name="use-math-methods"></a>Verwendung von mathematischen Methoden  
 Im folgenden Beispiel wird gezeigt, wie verschiedene [Mathematische](https://msdn.microsoft.com/library/system.math.aspx) Methoden verwendet werden.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_math = from c in svcContext.ContactSet
                  where c.ContactId != _contactId2
                  && c.Address1_Latitude != null && 
                  c.Address1_Longitude != null
                  select new
                  {
                   Round = Math.Round(c.Address1_Latitude.Value),
                   Floor = Math.Floor(c.Address1_Latitude.Value),
                   Ceiling = Math.Ceiling(c.Address1_Latitude.Value),
                   Abs = Math.Abs(c.Address1_Latitude.Value),
                  };
    foreach (var c in query_math)
    {
        System.Console.WriteLine(c.Round + " " + c.Floor + 
            " " + c.Ceiling + " " + c.Abs);
    }
}
```  
  
<a name="BKMK_UsingMultipleSelectAndWhereClauses"></a>   
## <a name="use-multiple-select-and-where-clauses"></a>Verwendung von Mehrfachauswahl- und Wobei-Klauseln  
 Das folgende Beispiel zeigt Mehrfachauswahl- und Wobei-Klauseln unter Verwendung einer methodenbasierten Abfragensyntax.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_multiselect = svcContext.IncidentSet
                        .Where(i => i.IncidentId != _incidentId1)
                        .Select(i => i.incident_customer_accounts)
                        .Where(a => a.AccountId != _accountId2)
                        .Select(a => a.account_primary_contact)
                        .OrderBy(c => c.FirstName)
                        .Select(c => c.ContactId);
    foreach (var c in query_multiselect)
    {
        System.Console.WriteLine(c.GetValueOrDefault());
    }
}
```  
  
<a name="BKMK_UsingSelectMany"></a>   
## <a name="use-selectmany"></a>Verwendung von SelectMany  
 Im folgenden Beispiel wird gezeigt, wie die [SelectMany-Methode](https://msdn.microsoft.com/library/system.linq.enumerable.selectmany.aspx) verwendet wird.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_selectmany = svcContext.ContactSet
                        .Where(c => c.ContactId != _contactId2)
                        .SelectMany(c => c.account_primary_contact)
                        .OrderBy(a => a.Name);
    foreach (var c in query_selectmany)
    {
        System.Console.WriteLine(c.AccountId + " " + c.Name);    
    }
}
```
  
<a name="BKMK_UsingStringOperations"></a>   
## <a name="use-string-operations"></a>Verwendung von Zeichenfolgenoperationen  
 Im folgenden Beispiel wird gezeigt, wie verschiedene Zeichenfolge-Methoden verwendet werden.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_string = from c in svcContext.ContactSet
                    where c.ContactId == _contactId2
                    select new
                    {
                     IndexOf = c.FirstName.IndexOf("contact"),
                     Insert = c.FirstName.Insert(1, "Insert"),
                     Remove = c.FirstName.Remove(1, 1),
                     Substring = c.FirstName.Substring(1, 1),
                     ToUpper = c.FirstName.ToUpper(),
                     ToLower = c.FirstName.ToLower(),
                     TrimStart = c.FirstName.TrimStart(),
                     TrimEnd = c.FirstName.TrimEnd(),
                    };

    foreach (var c in query_string)
    {
        System.Console.WriteLine(c.IndexOf + "\n" + c.Insert + "\n" + 
            c.Remove + "\n" + c.Substring + "\n"
            + c.ToUpper + "\n" + c.ToLower + 
            "\n" + c.TrimStart + " " + c.TrimEnd);
    }
}
```
  
<a name="BKMK_UsingTwoWhereClauses"></a>   
## <a name="use-two-where-clauses"></a>Verwendung von zwei Wobei-Klauseln  
 Im folgenden Beispiel wird gezeigt, wie zwei Wobei-Klauseln verwendet werden.  
  
```csharp
using (ServiceContext svcContext = new ServiceContext(_serviceProxy))
{
    var query_twowhere = from a in svcContext.AccountSet
                      join c in svcContext.ContactSet 
                      on a.PrimaryContactId.Id equals c.ContactId
                      where c.LastName == "Smith" && c.CreditOnHold != null
                      where a.Name == "Contoso Ltd"
                      orderby a.Name
                      select a;
    foreach (var c in query_twowhere)
    {
         System.Console.WriteLine(c.AccountId + " " + c.Name);
    }
}
``` 
  
<a name="BKMK_UseLoadProperty"></a>   
## <a name="use-loadproperty-to-retrieve-related-records"></a>Verwendung von LoadProperty, um verwandte Datensätze abzurufen  
 Das folgende Beispiel zeigt, wie [Beziehung]<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.LoadProperty(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship)> verwendet wird, um auf verwandte Datensätze zuzugreifen.  
  
```csharp
Contact benAndrews = svcContext.ContactSet.Where(c => c.FullName == "Ben Andrews").FirstOrDefault();
if (benAndrews != null)
{
     //benAndrews.Contact_Tasks is null until LoadProperty is used.
     svcContext.LoadProperty(benAndrews, "Contact_Tasks");
     Task benAndrewsFirstTask = benAndrews.Contact_Tasks.FirstOrDefault();
     if (benAndrewsFirstTask != null)
     {
          Console.WriteLine("Ben Andrews first task with Subject: '{0}' retrieved.", benAndrewsFirstTask.Subject);
     }
}
```
  

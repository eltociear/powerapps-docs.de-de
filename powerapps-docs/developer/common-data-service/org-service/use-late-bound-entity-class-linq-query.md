---
title: Verwenden von spät gebundenen Entitätsklassen mit einer LINQ-Abfrage (Common Data Service für Apps) | Microsoft Docs
description: 'Erfahren Sie, wie Sie die späte Bindung mit .NET Language-Integrated Query (LINQ)-Abfragen verwenden können'
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
# <a name="use-late-bound-entity-class-with-a-linq-query"></a>Verwenden von spät gebundenen Entitätsklassen mit einer LINQ-Abfrage

In Common Data Service für Apps können Sie die späte Bindung mit .NET Language-Integrated Query (LINQ)-Abfragen verwenden. Späte Bindung verwendet den logischen Namen des Attributs und wird zur Laufzeit aufgehoben.  
  
<a name="usinglatebindingjoin"></a>   

## <a name="using-late-binding-in-a-join-clause"></a>Verwenden von später Bindung in einer Verknüpfungsklausel  

 Die folgenden Beispiele veranschaulichen, wie Sie späte Bindung in der `join`-Klausel einer LINQ-Abfrage verwenden.  
  
 Rufen Sie den vollständigen Namen des Kontakts ab, der den primären Kontakt für eine Firma und den Firmennamen darstellt.  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_join2 = from c in orgSvcContext.CreateQuery("contact")
                   join a in orgSvcContext.CreateQuery("account")
                   on c["contactid"] equals a["primarycontactid"]
                   select new
                   {
                    contact_name = c["fullname"],
                    account_name = a["name"]
                   };
 foreach (var c in query_join2)
 {
  System.Console.WriteLine(c.contact_name + "  " + c.account_name);
 }
}
 ```
 Abrufen von Kontakt-, Firmen- und Leaddaten, bei denen der Lead der Ursprungslead war und der Nachname des Kontakts nicht "Parker" ist  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_dejoin = from c in orgSvcContext.CreateQuery("contact")
                    join a in orgSvcContext.CreateQuery("account") 
                    on c["contactid"] equals a["primarycontactid"]
                    join l in orgSvcContext.CreateQuery("lead") 
                    on a["originatingleadid"] equals l["leadid"]
                    where (string)c["lastname"] != "Parker"
                    select new { Contact = c, Account = a, Lead = l };
 foreach (var c in query_dejoin)
 {
  System.Console.WriteLine(c.Account.Attributes["name"] + " " + 
   c.Contact.Attributes["fullname"] + " " + c.Lead.Attributes["leadid"]);
 }
}
 ```
<a name="Usinglatebindingleft"></a>   

## <a name="using-late-binding-in-a-left-join"></a>Verwenden von später Bindung in einer Linksverknüpfung  

 Das folgende Beispiel zeigt, wie Sie eine Liste mit Kontakt- und Firmeninformationen mithilfe einer Linksverknüpfung abrufen. Eine Linksverknüpfung ist so ausgelegt, dass übergeordnete Elemente mit und ohne untergeordnete Elemente von zwei Quellen zurückgegeben werden. Es gibt eine Korrelation zwischen übergeordnetem und untergeordnetem Element, aber ein untergeordnetes Element kann nicht vorhanden sein.  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_join9 = from a in orgSvcContext.CreateQuery("account")
                   join c in orgSvcContext.CreateQuery("contact") 
                   on a["primarycontactid"] equals c["contactid"] into gr
                   from c_joined in gr.DefaultIfEmpty()
                   select new
                   {
                    account_name = a.Attributes["name"]
                   };
 foreach (var c in query_join9)
 {
  System.Console.WriteLine(c.account_name);
 }
}
 ```
<a name="contains"></a>   

## <a name="using-late-binding-and-the-contains-method"></a>Verwenden von später Bindung und der Contains-Methode  

 Das folgende Beispiel veranschaulicht, wie Sie späte Bindung mit der `Contains`-Methode in einer LINQ-Abfrage verwenden.  
  
 ```csharp
 using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_contains3 = from c in orgSvcContext.CreateQuery("contact")
                       where ((string)c["description"]).Contains("Coho")
                       select new
                       {
                        firstname = c.Attributes["firstname"],
                        lastname = c.Attributes["lastname"]
                       };
 foreach (var c in query_contains3)
 {
  System.Console.WriteLine(c.firstname + " " + c.lastname);
 }
}
 ```
 <a name="notequals"></a>   

## <a name="using-late-binding-and-not-equals-operator"></a>Verwenden von später Bindung und des Nicht-Gleich-Operators  

 Die folgende Beispiel zeigt die Verwendung des Nicht-Gleich-Operators.  
  
 ```csharp
using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{
 var query_ne3 = from c in orgSvcContext.CreateQuery("contact")
                 where !c["address1_city"].Equals(null)
                 select new
                 {
                  FirstName = c["firstname"],
                  LastName = c["lastname"],
                  Address1_City = c["address1_city"]
                 };
 foreach (var c in query_ne3)
 {
  System.Console.WriteLine(c.FirstName + " " + 
   c.LastName + " " + c.Address1_City);
 }
}
```

 <a name="getattribute"></a>   

## <a name="using-the-getattributevalue-method"></a>Verwenden der GetAttributeValue-Methode  

 Das folgende Beispiel zeigt, wie Sie Kontaktinformationen mithilfe der `GetAttributeValue`-Methode abrufen.  
  
 ```csharp
using (OrganizationServiceContext orgSvcContext = new OrganizationServiceContext(_serviceProxy))
{

 var list_getattrib1 = (from c in orgSvcContext.CreateQuery("contact")
                        where c.GetAttributeValue<Guid?>("contactid") != _contactId1
                        select new { 
                         FirstName = c.GetAttributeValue<string>("firstname"), 
                         LastName = c.GetAttributeValue<string>("lastname") 
                        }).ToList();
 foreach (var c in list_getattrib1)
 {
  System.Console.WriteLine(c.FirstName + " " + c.LastName);
 }
}
```
  
### <a name="see-also"></a>Siehe auch  
 [Erstellen von Abfragen mit LINQ (.NET Language-integrierte Abfrage)](build-queries-with-linq-net-language-integrated-query.md)   
 [Bestellergebnisse mithilfe von LINQ der Entitätsattributen](order-results-entity-attributes-linq.md)   
 <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.CreateQuery``1>
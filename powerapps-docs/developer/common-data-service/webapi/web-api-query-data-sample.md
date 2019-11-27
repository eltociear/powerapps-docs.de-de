---
title: Web-API-Abfragedatenbeispiel (Common Data Service) | Microsoft-Dokumentation
description: Diese Gruppe von Beispielen zeigt, wie Daten mit der Web-API abgefragt werden. Diese werden mithilfe clientseitigen JavaScripts und C# implementiert.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 9457ce4f-0ef6-4085-8346-fe3134ec7106
caps.latest.revision: 18
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a305f1676275c8b6f72d70e4e416a798933b476c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753630"
---
# <a name="web-api-query-data-sample"></a>Web API-Abfragedatenbeispiel

Diese Gruppe von Beispielen zeigt, wie Daten mit dem Common Data Service Web-API abgefragt werden. Dieses Beispiel wurde als ein separates Projekt für die folgenden Sprachen implementiert:

- [Web API-Abfragedatenbeispiele (clientseitiges JavaScript)](samples/query-data-client-side-javascript.md)

- [Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)

Dieses Thema berschreibt einen allgemeinen Satz von Vorgängen, die von jedem Beispiel in dieser Gruppe implementiert wurden. Dieses Thema beschreibt HTTP-Anforderungen, -Antworten und Textausgaben, die von jedem Beispiel dieser Gruppe ohne sprachspezifischen Details ausgeführt wird. Weitere Informationen zum Ausführen dieser Vorgänge, finden Sie in den sprachspezifischen Beschreibungen und den individuellen Beispielen.

## <a name="demonstrates"></a>Demonstriert

Dieses Beispiel wird in die folgenden Hauptabschnitte unterteilt und enthält Web-API-Datenabfragen, die in den entsprechenden Themenabschnitten detailliert behandelt werden.

|Themenabschnitt|Zugeordnete Themen|
|-------------------|---------------------------|
|[Auswählen von spezifischen Eigenschaften](#bkmk_selectproperties)|[Spezifische Eigenschaften abrufen](retrieve-entity-using-web-api.md#bkmk_requestProperties)<br /><br /> [Formatierte Werte einschließen](query-data-web-api.md#bkmk_includeFormattedValues)|
|[Abfragefunktionen verwenden](#bkmk_queryfunctions)|[Ergebnisse filtern](query-data-web-api.md#bkmk_filter)<br /><br /> [Standardabfragenfunktionen](query-data-web-api.md#bkmk_buildInQueryFunctions)<br /><br /> [Verfassen Sie Sie eine Abfrage mit Funktionen](use-web-api-functions.md#bkmk_composeQueryWithFunctions)<br /><br /> <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>|
|[Operatoren verwenden](#bkmk_operators)|[Standardfilteroperatoren](query-data-web-api.md#bkmk_buildInFilterOperators)|
|[Festlegen der Reihenfolge](#bkmk_prededence)|[Standardfilteroperatoren](query-data-web-api.md#bkmk_buildInFilterOperators)|
|[Reihenfolge von Ergebnissen](#bkmk_orderresults)|[Reihenfolge von Ergebnissen](query-data-web-api.md#bkmk_order)<br /><br /> [Ergebnisse filtern](query-data-web-api.md#bkmk_filter)|
|[Parameteralias](#bkmk_parameteralias)|[Verwendung von Parameteraliasen mit Systemabfrageoptionen](query-data-web-api.md#bkmk_useParameterAliases)|
|[Ergebnisse eingrenzen](#bkmk_limitresults)|[Ergebnisse eingrenzen](query-data-web-api.md#bkmk_limitResults)<br /><br /> [Beschränkungen der Zahl der zurückgegebenen Entitäten](query-data-web-api.md#bkmk_limits)|
|[Ergebnisse erweitern](#bkmk_expandresults)|[Abrufen verwandter Entitäten durch Erweitern der Navigationseigenschaften](query-data-web-api.md#bkmk_expandRelated)|
<!-- TODO:
|[FetchXML queries](#bkmk_fetchxml)|[FetchXML schema](../org-service/fetchxml-schema.md)<br /><br /> [Page large result sets with FetchXML](../org-service/page-large-result-sets-with-fetchxml.md)<br /><br /> [Use custom FetchXML](retrieve-and-execute-predefined-queries.md#bkmk_useFetchXML)| -->
|[Vordefinierte Abfragen](#bkmk_predefinedqueries)|[Vordefinierte Abfragen abrufen und ausführen](retrieve-and-execute-predefined-queries.md)<br /><br /> <xref href="Microsoft.Dynamics.CRM.userquery?text=userquery EntityType" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.savedquery?text=savedquery EntityType" />|

Die folgenden Abschnitte enthalten eine kurze Diskussion zu den ausgeführten Common Data Service Web-API-Vorgängen, sowie den entsprechenden HTTP-Nachrichten und den Ausgaben, die der Konsolen zugeordnet sind.

<a name="bkmk_sampleData"></a>

## <a name="sample-data"></a>Beispieldaten

Um sicherzustellen, dass die Abfragen des vorliegenden Beispiels ordnungsgemäß ausgeführt werden, wird ein Standardsatz von Beispieldatensätzen durch dieses Beispiel erstellt. Diese Beispieldatensätze werden gelöscht, es sei denn, der Benutzer entscheidet sich, sie nicht zu löschen. Dies sind die Daten, die das Beispiel abfragen wird. Sie erhalten möglicherweise unterschiedliche Ergebnisse, abhängig von sämtlichen vorhandenen Daten in Ihrer Umgebung.  
  
Die Daten werden mithilfe von *Deep-Insert* in einer einzelnen `POST`-Anfrage hinzugefügt und entsprechen der folgenden Struktur:  
  
```json  
  
 {  
        "name": "Contoso, Ltd. (sample)",  
        "primarycontactid": {  
            "firstname": "Yvonne", "lastname": "McKay (sample)", "jobtitle": "Coffee Master",  
            "annualincome": 45000, "Contact_Tasks": [  
            { "subject": "Task 1", "description": "Task 1 description" },  
            { "subject": "Task 2", "description": "Task 2 description" },  
            { "subject": "Task 3", "description": "Task 3 description" }  
            ]  
        },   
                            "Account_Tasks": [  
        { "subject": "Task 1", "description": "Task 1 description" },  
        { "subject": "Task 2", "description": "Task 2 description" },  
        { "subject": "Task 3", "description": "Task 3 description" }  
        ],  
        "contact_customer_accounts": [  
            {  
                "firstname": "Susanna", "lastname": "Stubberod (sample)", "jobtitle": "Senior Purchaser",  
                "annualincome": 52000, "Contact_Tasks": [  
            { "subject": "Task 1", "description": "Task 1 description" },  
            { "subject": "Task 2", "description": "Task 2 description" },  
            { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Nancy", "lastname": "Anderson (sample)", "jobtitle": "Activities Manager",  
                "annualincome": 55500, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Maria", "lastname": "Cambell (sample)", "jobtitle": "Accounts Manager",  
                "annualincome": 31000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Nancy", "lastname": "Anderson (sample)", "jobtitle": "Logistics Specialist",  
                "annualincome": 63500, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Scott", "lastname": "Konersmann (sample)", "jobtitle": "Accounts Manager",  
                "annualincome": 38000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Robert", "lastname": "Lyon (sample)", "jobtitle": "Senior Technician",  
                "annualincome": 78000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Paul", "lastname": "Cannon (sample)", "jobtitle": "Ski Instructor",  
                "annualincome": 68500, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Rene", "lastname": "Valdes (sample)", "jobtitle": "Data Analyst III",  
                "annualincome": 86000, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            },  
            {  
                "firstname": "Jim", "lastname": "Glynn (sample)", "jobtitle": "Senior International Sales Manager",  
                "annualincome": 81400, "Contact_Tasks": [  
                { "subject": "Task 1", "description": "Task 1 description" },  
                { "subject": "Task 2", "description": "Task 2 description" },  
                { "subject": "Task 3", "description": "Task 3 description" }  
                ]  
            }  
        ]  
    }  
```  
  
<a name="bkmk_selectproperties"></a>
   
## <a name="selecting-specific-properties"></a>Auswählen von spezifischen Eigenschaften
  
Erstellen Sie Abfragen immer mithilfe der `$select`-Abfrageoption; andernfalls wird der Server alle Eigenschaften jeder einzelnen Entität zurückgeben und somit die Leitung reduzieren. Dieses Beispiel veranschaulicht, wie eine grundlegende Abfrage durch Auswählen von drei Eigenschaften eines <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> erstellt wird. Die Eigenschaften sind `fullname`, `jobtitle`, `annualincome`. Der Abschnitt stellt auch die Unterschiede zwischen formatierten und nicht formatierten Werten dar, wie in den Ergebnissen der Eigenschaft `annualincome` des Kontakts angezeigt. Weitere Informationen: [Anforderungsspezifische Eigenschaften](query-data-web-api.md#bkmk_requestProperties), [Formatierte Werte einschließen](query-data-web-api.md#bkmk_includeFormattedValues).  
  
In diesem Beispiel stellen wir Anfragen für einen bestimmten Kontakt. In diesem Fall ist es der primäre Kontakt der Firma, `Yvonne McKay (sample)`.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts(b848fdee-c143-e611-80d5-00155da84802)?$select=fullname,jobtitle,annualincome HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 517  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)/$entity",  
   "@odata.etag":"W/\"619718\"",  
   "fullname":"Yvonne McKay (sample)",  
   "jobtitle":"Coffee Master",  
   "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
   "annualincome":45000.0000,  
   "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
   "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
   "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contact basic info:  
    Fullname: 'Yvonne McKay (sample)'  
    Jobtitle: 'Coffee Master'  
    Annualincome: '45000' (unformatted)  
    Annualincome: $45,000.00 (formatted)  
  
```  
  
<a name="bkmk_queryfunctions"></a>
  
## <a name="using-query-functions"></a>Abfragefunktionen verwenden
 
Filteroptionen verwenden, um Kriterien für die gewünschten Ergebnisse festzulegen. Sie können sowohl einfache als auch komplexen Filter mithilfe einer Kombination aus Abfragenfunktionen, Vergleichsoperatoren und logischen Operatoren erstellen. Weitere Informationen: [Filterergebnisse](query-data-web-api.md#bkmk_filter).  
  
Abfragefunktionen sind Funktionen, die als Filterkriterium in einer Abfrage verwendet werden. Es gibt Standardabfragenfunktionen und Common Data Service-spezifische Abfragenfunktionen. Diese Funktionen nehmen Parameter an und geben einen `Boolean`-Wert zurück. Dieses Beispiel veranschaulicht, wie eine Abfrage für jeden Typ erstellt wird.  
  
### <a name="standard-query-functions"></a>Standardabfragenfunktionen

Common Data Service unterstützt kleine Teilmenge von OData-Abfragenfunktionen, insbesondere: `contains`, `endswith`und `startswith`. Zum Beispiel erlaubt uns die `contains`-Standardabfragenfunktion nach Eigenschaften, die einer Zeichenfolge entsprechen, zu filtern. In diesem Vorgang fragen wir nach allen Kontakten mit `fullname` ab, die die Zeichenfolge `(sample)` enthalten. Weitere Informationen: [Standardabfragenfunktionen](query-data-web-api.md#bkmk_buildInQueryFunctions).  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)') HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts filtered by fullname containing '(sample)':  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
    5) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    6) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    7) Robert Lyon (sample), Senior Technician, $78,000.00  
    8) Paul Cannon (sample), Ski Instructor, $68,500.00  
    9) Rene Valdes (sample), Data Analyst III, $86,000.00  
    10) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
  
```  
  
### <a name="common-data-service-query-functions"></a>Common Data Service-Abfragefunktionen

Common Data Service-Abfragenfunktionen bieten zahlreiche Optionen zum Erstellen von Abfragen, die für Common Data Service relevant sind. Eine komplette Liste dieser Funktionen finden Sie unter <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex>. Weitere Informationen: [Verfassen Sie eine Abfrage mit Funktionen](use-web-api-functions.md#bkmk_composeQueryWithFunctions)  
  
Sie werden diese Abfragenfunktionen in ähnlicher Weise wie die Standardabfragenfunktionen verwenden. Der Hauptunterschied ist, dass bei der Verwendung der Common Data Service-Abfragenfunktionen der vollständige Name der Funktion sowie der/die Parametername/n angeben werden müssen. Wenn Sie beispielsweise einer Liste von Kontakten erhalten wollen, die in der letzten Stunde erstellt wurden, können Sie eine Abfrage unter Verwendung der <xref href="Microsoft.Dynamics.CRM.LastXHours?text=LastXHours Function" /> erstellen.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=Microsoft.Dynamics.CRM.LastXHours(PropertyName='createdon',PropertyValue='1') HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts that were created within the last 1hr:  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
    5) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    6) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    7) Robert Lyon (sample), Senior Technician, $78,000.00  
    8) Paul Cannon (sample), Ski Instructor, $68,500.00  
    9) Rene Valdes (sample), Data Analyst III, $86,000.00  
    10) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_operators"></a>
 
## <a name="using-operators"></a>Operatoren verwenden

Verwenden Sie [Standardfilteroperatoren](query-data-web-api.md#bkmk_buildInFilterOperators) (`eq`,`ne`,`gt`,`ge`,`lt`,`le`,`and`,`or`,`not`), um unsere Ergebnisse weiter zu verfeinern. In diesem Beispiel stellen wir eine Anfrage für eine Liste mit allen Kontakten mit `fullname`, die `(sample)` enthalten und deren Jahreseinkommen größer als `55000` ist.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')%20and%20annualincome%20gt%2055000 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 2629  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts filtered by fullname and annualincome (<$55,000):  
    1) Nancy Anderson (sample), Activities Manager, $55,500.00  
    2) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    3) Robert Lyon (sample), Senior Technician, $78,000.00  
    4) Paul Cannon (sample), Ski Instructor, $68,500.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_prededence"></a>
   
## <a name="setting-precedence"></a>Festlegen der Reihenfolge
 
Verwenden Sie Klammern, um die Reihenfolge, in der die Bedingungen ausgewertet werden, festzulegen.  
  
 In diesem Beispiel stellen wir eine Anfrage für eine Liste mit allen Kontakten mit `fullname`, die `(sample)`, `jobtitle` enthalten und entweder `senior` oder `specialist` sind und deren `annualincome` größer als `55000` ist. Um die gewünschten Ergebnisse zu erhalten, werden Klammern zum Gruppieren der `jobtitle`-Filter verwendet. Da alle Operatoren die gleiche Rangfolge haben, erhält der `or`-Operator durch das Weglassen der Klammern dieselbe Rangfolge wie die `and`-Operatoren.  Filter werden von links nach rechts angewendet. Die Reihenfolge, in der diese Anweisungen im Filter angezeigt werden, kann die Ergebnisse beeinflussen. So sieht die Abfrage in diesem Beispiel aus: `$filter=contains(fullname,'(sample)') and (contains(jobtitle,'senior') or contains(jobtitle,'specialist')) and annualincome gt 55000`.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')%20and%20(contains(jobtitle,'senior')%20or%20contains(jobtitle,'specialist'))%20and%20annualincome%20gt%2055000 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 1393  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts filtered by fullname, annualincome and jobtitle (Senior or Specialist):  
    1) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    2) Robert Lyon (sample), Senior Technician, $78,000.00  
    3) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_orderresults"></a>

## <a name="ordering-results"></a>Reihenfolge von Ergebnissen

Sie können entweder eine auf- oder absteigende Reihenfolge der Ergebnisse festlegen, indem Sie die `$orderby` Filteroption verwenden. In diesem Beispiel erstellen wir eine Abfrage für alle Kontakten mit `fullname`, die `(sample)` beinhalten und fragen die Daten in aufsteigender Reihenfolge basierend auf dem `jobtitle`-Eigenschaftswert ab und danach in absteigender Reihenfolge basierend auf dem `annualincome` Eigenschaftswert, indem wir diese Syntax verwenden: `$orderby=jobtitle asc, annualincome desc`. Weitere Informationen: [Auftragsergebnisse](query-data-web-api.md#bkmk_order).  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')%20&$orderby=jobtitle%20asc,%20annualincome%20desc HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts ordered by jobtitle (ascending) and annualincome (descending):  
    1) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    2) Maria Cambell (sample), Accounts Manager, $31,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Yvonne McKay (sample), Coffee Master, $45,000.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    7) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
    8) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    9) Robert Lyon (sample), Senior Technician, $78,000.00  
    10) Paul Cannon (sample), Ski Instructor, $68,500.00  
```  
  
<a name="bkmk_parameteralias"></a>

## <a name="parameter-alias"></a>Parameteralias

Verwenden Sie Parameteraliase, um Parameter in Ihren Filtern einfacher wiederzuverwenden. Parametrisierte Aliase können in `$filter`- und `$orderby`-Optionen verwendet werden. Wenn dem Alias kein Wert zugeordnet wurde, wird angenommen, dass er NULL ist. Sie können auch Parameteraliase verwenden, wenn Sie Funktionen aufrufen. Weitere Informationen: [Verwenden von Web-API-Funktionen](use-web-api-functions.md), [Verwendung von Parameteraliasen mit Systemabfrageoptionen](query-data-web-api.md#bkmk_useParameterAliases). Mit der Orderby-Option beispielsweise können wir diese Abfrage mit Parametern erneut schreiben und würden die gleichen Ausgabeergebnisse erhalten.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(@p1,'(sample)')%20&$orderby=@p2%20asc,%20@p3%20desc&@p1=fullname&@p2=jobtitle&@p3=annualincome HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4284  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619847\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"2cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619853\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"38c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619855\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"3cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619849\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"30c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619851\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"34c364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts list using parameterized aliases:  
    1) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    2) Maria Cambell (sample), Accounts Manager, $31,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Yvonne McKay (sample), Coffee Master, $45,000.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    7) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
    8) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    9) Robert Lyon (sample), Senior Technician, $78,000.00  
    10) Paul Cannon (sample), Ski Instructor, $68,500.00  
```  
  
<a name="bkmk_limitresults"></a>

## <a name="limit-results"></a>Ergebnisse eingrenzen

Wenn mehr Daten als benötigt zurückgeben werden, wirkt es sich negativ auf die Leistung aus. Der Server wird ein Maximum von 5000 Entitäten pro Anfrage zurückgeben. Sie können die Anzahl der zurückgegebenen Ergebnisse beschränken, indem Sie die `$top`-Abfrageoption verwenden oder indem Sie `odata.maxpagesize` im Anforderungsheader hinzufügen. Die `$top`-Abfrageoption gibt nur die oberste Anzahl der Entitäten aus der Ergebnismenge zurück und ignoriert den Rest. Der `odata.maxpagesize` Anforderungsheader gibt die Anzahl der zurückgegebenen Entitäten pro Seite mit einer `@odata.nextLink`-Eigenschaft an, um Ergebnisse der nächsten Seite zu erhalten. Weitere Informationen zu `odata.maxpagesize` finden Sie im Abschnitt in [Paginierung](#bkmk_filterPagination) und auch in [Beschränkungen der Zahl der zurückgegebenen Entitäten](query-data-web-api.md#bkmk_limits).  
  
<a name="bkmk_topResults"></a>
 
### <a name="top-results"></a>Beste Ergebnisse

Wir können die `$top`-Abfrageoption anwenden, um die grundlegenden Abfrageoperation auf die ersten fünf Kontakte mit `fullname` zu beschränken, die `(sample)`enthalten. In diesem Fall wird die tatsächliche Anforderung mindestens 10 Ergebnisse liefern, aber nur die ersten 5 Einträge werden in der Antwort zurückgegeben.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$top=5 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 2209  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "value":[  
      {  
         "@odata.etag":"W/\"619718\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"15c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619839\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"1cc364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619841\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"20c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619843\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"24c364b2-bf43-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"619845\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"28c364b2-bf43-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts top 5 results:  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
    5) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
  
```  
  
<a name="bkmk_resultCount"></a>

### <a name="result-count"></a>Ergebniszähler

Sie können lediglich die Anzahl der Datensätze aus einer als Sammlung bewerteten Eigenschaft oder eine Anzahl entsprechender Entitäten in einem Filter abrufen. Das Abrufen der Anzahl zeigt uns die Anzahl der möglichen Einträge in unserem Ergebnis. Der Common Data Service-Server gibt jedoch nicht mehr als eine maximale Anzahl von 5000 zurück, auch wenn das Ergebnis möglicherweise höher ist. In diesem Beispiel erstellen wir einen Filter mit `jobtitle`, der entweder `Senior` oder `Manager` enthält und fordern ebenfalls eine `$count` des Ergebnisses an. Die Antwort enthält die Anzahl der `@odata.count`-Eigenschaft sowie die Ergebnisse der Abfrage. Weitere Informationen: [Abrufen einer Anzahl von Entitäten](query-data-web-api.md#bkmk_retrieveCount).  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(jobtitle,'senior')%20or%20contains(jobtitle,%20'manager')&$count=true HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 2654  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "@odata.count":6,  
   "value":[  
      {  
         "@odata.etag":"W/\"620258\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"bf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620260\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620262\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c748fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620266\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"cf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620268\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"d348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620274\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"df48fdee-c143-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
6 contacts have either 'Manager' or 'Senior' designation in their jobtitle.  
Manager or Senior:  
    1) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
    3) Maria Cambell (sample), Accounts Manager, $31,000.00  
    4) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    5) Robert Lyon (sample), Senior Technician, $78,000.00  
    6) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
  
```  
  
<a name="bkmk_filterPagination"></a>

### <a name="pagination"></a>Paginierung

Um eine sequenzielle Teilmenge der Ergebnisse einer Abfrage zu erhalten, die eine große Anzahl an Entitäten zurückgibt, verwenden Sie `odata.maxpagesize` statt `$top`. Weitere Informationen: [Anzahl der auf einer Seite zurückzugebenden Entitäten angeben](query-data-web-api.md#bkmk_specifyNumber).  
  
In diesem Beispiel fordern wir eine `$count` an und wir legen `odata.maxpagesize` auf `4`fest. Diese Filter entspricht 10 Kontakten, aber wir rufen nur jeweils 4 auf einmal ab. Wir verwenden die Anzahl und die maximale Seitengröße auch, um herauszufinden, wie viele Seiten insgesamt vorhanden sind. Das Ergebnis der ersten Seite wird in dieser Anfrage zurückgegeben.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=4, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=4  
Content-Length: 2294  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "@odata.count":10,  
   "value":[  
      {  
         "@odata.etag":"W/\"620138\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b848fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620258\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"bf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620260\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620262\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"c748fdee-c143-e611-80d5-00155da84802"  
      }  
   ],  
   "@odata.nextLink":"https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253ccontactid%2520last%253d%2522%257bC748FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520first%253d%2522%257bB848FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E"  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts total: 10  Contacts per page: 4.  
Page 1 of 3:  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Nancy Anderson (sample), Activities Manager, $55,500.00  
    4) Maria Cambell (sample), Accounts Manager, $31,000.00  
  
```  
  
 Um Seite 2 zu erhalten, verwenden Sie eine `GET`-Anforderung mit dem Wert der  `@odata.nextLink`-Eigenschaft.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253ccontactid%2520last%253d%2522%257bC748FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520first%253d%2522%257bB848FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=4, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=4  
Content-Length: 2294  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome)",  
   "@odata.count":10,  
   "value":[  
      {  
         "@odata.etag":"W/\"620264\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"cb48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620266\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"cf48fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620268\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"d348fdee-c143-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620270\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"d748fdee-c143-e611-80d5-00155da84802"  
      }  
   ],  
   "@odata.nextLink":"https://[Organization URI]/api/data/v9.0/contacts?$select=fullname,jobtitle,annualincome&$filter=contains(fullname,'(sample)')&$count=true&$skiptoken=%3Ccookie%20pagenumber=%223%22%20pagingcookie=%22%253ccookie%2520page%253d%25222%2522%253e%253ccontactid%2520last%253d%2522%257bD748FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520first%253d%2522%257bCB48FDEE-C143-E611-80D5-00155DA84802%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E"  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Page 2 of 3:  
    1) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    2) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    3) Robert Lyon (sample), Senior Technician, $78,000.00  
    4) Paul Cannon (sample), Ski Instructor, $68,500.00  
```  
  
<a name="bkmk_expandresults"></a>

## <a name="expanding-results"></a>Ergebnisse erweitern

Um Informationen von zugeordneten Entitäten zu erhalten, verwenden Sie die `$expand`-Abfrageoption der Navigationseigenschaften. Weitere Informationen: [Abrufen verwandter Entitäten durch Erweitern der Navigationseigenschaften](query-data-web-api.md#bkmk_expandRelated).  
  
### <a name="expand-on-single-valued-navigation-property"></a>Auf einzelwertige Navigationseigenschaften erweitern

Eine einzelwertige Navigationseigenschaft stellt eine n:1-Beziehungen dar. In unseren Beispieldaten weist die Firma eine Beziehung mit einem Kontakt über das `primarycontactid`-Attribut auf. Für diese Beziehung kann die Firma über nur einen primären Kontakt verfügen.  Mithilfe von <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> können Sie eine Abfrage erstellen, um Informationen über die Firma und erweiterte Informationen über den primären Kontakt zu erhalten.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts(b2546951-c543-e611-80d5-00155da84802)?$select=name&$expand=primarycontactid($select=fullname,jobtitle,annualincome) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 700  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(fullname,jobtitle,annualincome))/$entity",  
   "@odata.etag":"W/\"620641\"",  
   "name":"Contoso, Ltd. (sample)",  
   "accountid":"b2546951-c543-e611-80d5-00155da84802",  
   "primarycontactid":{  
      "@odata.etag":"W/\"620534\"",  
      "fullname":"Yvonne McKay (sample)",  
      "jobtitle":"Coffee Master",  
      "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
      "annualincome":45000.0000,  
      "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
      "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
      "contactid":"b3546951-c543-e611-80d5-00155da84802"  
   }  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Account 'Contoso, Ltd. (sample)' has the following primary contact person:  
    Fullname: 'Yvonne McKay (sample)'   
    Jobtitle: 'Coffee Master'   
    Annualincome: '45000'  
```  
  
### <a name="expand-on-partner-property"></a>Auf Partnereigenschaften erweitern

Jede Navigationseigenschaft besitzt eine entsprechende "Partner"-Eigenschaft. Wenn erst einmal eine Zuordnung erstellt ist, können wir Informationen über diese Zuordnung erhalten. Welches Attribut wir verwenden, hängt von der Basisentität ab, gegen die die Abfrage gestellt wird. Im vorherigen Vorgang haben wir beispielsweise eine Abfrage gegen den <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> gestellt und wir möchten weitere Informationen über den primären Kontakt erhalten. Dies ist über das `primarycontactid`-Attribut erfolgt. Im Abschnitt <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> unter [Einzelwertige Navigationseigenschaften](/dynamics365/customer-engagement/web-api/account?view=dynamics-ce-odata-9#Single-valued_navigation_properties) sehen wir, dass die Partnereigenschaft, die `primarycontactid` entspricht, die `account_primary_contact` sammlungswertige Navigationseigenschaft ist, die im <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> angezeigt wird.  
  
Um eine Abfrage gegen einen Kontakt zu schreiben, können Sie das `account_primary_contact`-Attribut erweitern, um Informationen über Firmen zu erhalten, bei denen dieser Kontakt der primäre Kontakt ist. In den Beispieldaten ist `Yvonne McKay (sample)` die primäre Kontaktperson für nur eine Firma. Allerdings kann sie potentiell anderen Firmen als primärer Kontakt zugewiesen werden. Da die `account_primary_contact`-Eigenschaft eine n: 1-Beziehung ist, wird das Ergebnis als Array von Firmenentitäten zurückgegeben.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts(b3546951-c543-e611-80d5-00155da84802)?$select=fullname,jobtitle,annualincome&$expand=account_primary_contact($select=name) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 737  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome,account_primary_contact,account_primary_contact(name))/$entity",  
   "@odata.etag":"W/\"620534\"",  
   "fullname":"Yvonne McKay (sample)",  
   "jobtitle":"Coffee Master",  
   "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
   "annualincome":45000.0000,  
   "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
   "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
   "contactid":"b3546951-c543-e611-80d5-00155da84802",  
   "account_primary_contact":[  
      {  
         "@odata.etag":"W/\"620919\"",  
         "name":"Contoso, Ltd. (sample)",  
         "accountid":"b2546951-c543-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contact 'Yvonne McKay (sample)' is the primary contact for the following accounts:  
    1) Contoso, Ltd. (sample)  
```  
  
### <a name="expand-on-collection-valued-navigation-property"></a>Auf sammlungswertige Navigationseigenschaften erweitern

Sammlungswertige Navigationseigenschaften unterstützen 1:n- oder n:n-Beziehungen. In unseren Beispieldaten weist die Firma eine Beziehung mit vielen Kontakten über das `contact_customer_accounts`-Attribut auf.  
  
Mithilfe von <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" /> können Sie eine Abfrage erstellen, um Informationen über die Firma und erweiterte Informationen über die Kontakte zu erhalten. In diesem Fall wird `Contoso, Ltd. (sample)` neun anderen Kontakten über die `contact_customer_accounts`-sammlungswertige Navigationseigenschaft zugeordnet.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts(86546951-c543-e611-80d5-00155da84802)?$select=name&$expand=contact_customer_accounts($select=fullname,jobtitle,annualincome) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 4073  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,contact_customer_accounts,contact_customer_accounts(fullname,jobtitle,annualincome))/$entity",  
   "@odata.etag":"W/\"620921\"",  
   "name":"Contoso, Ltd. (sample)",  
   "accountid":"86546951-c543-e611-80d5-00155da84802",  
   "contact_customer_accounts":[  
      {  
         "@odata.etag":"W/\"620847\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"8e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620849\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"92546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620851\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"96546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620853\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9a546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620855\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620857\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a2546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620859\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a6546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620861\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"aa546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620863\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"ae546951-c543-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Account 'Contoso, Ltd. (sample)' has the following contact customers:  
    1) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
    3) Maria Cambell (sample), Accounts Manager, $31,000.00  
    4) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    5) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    6) Robert Lyon (sample), Senior Technician, $78,000.00  
    7) Paul Cannon (sample), Ski Instructor, $68,500.00  
    8) Rene Valdes (sample), Data Analyst III, $86,000.00  
    9) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
### <a name="expand-on-multiple-navigation-properties"></a>Erweitern auf mehrere Navigationseigenschaften

Sie können auf soviele Navigationseigenschaften erweitern, wie für die Abfrage erforderlich. Allerdings kann die `$expand` Option nur eine Ebene tief gehen.  
  
Dieses Beispiel erweitert die `primarycontactid`, `contact_customer_accounts`und `Account_Tasks` Navigationseigenschaften des <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" />.  Diese Abfrage gibt eine Antwort zurück, die Informationen über die Firma und zwei Sammlungen enthält: eine Kontaktsammlung und eine Aufgabensammlung. Der Beispielcode verarbeitet diese Sammlungen separat.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts(86546951-c543-e611-80d5-00155da84802)?$select=name&$expand=primarycontactid($select=fullname,jobtitle,annualincome),contact_customer_accounts($select=fullname,jobtitle,annualincome),Account_Tasks($select=subject,description) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Preference-Applied: odata.maxpagesize=10  
Content-Length: 5093  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,contact_customer_accounts,Account_Tasks,primarycontactid(fullname,jobtitle,annualincome),contact_customer_accounts(fullname,jobtitle,annualincome),Account_Tasks(subject,description))/$entity",  
   "@odata.etag":"W/\"620921\"",  
   "name":"Contoso, Ltd. (sample)",  
   "accountid":"86546951-c543-e611-80d5-00155da84802",  
   "primarycontactid":{  
      "@odata.etag":"W/\"620726\"",  
      "fullname":"Yvonne McKay (sample)",  
      "jobtitle":"Coffee Master",  
      "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
      "annualincome":45000.0000,  
      "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
      "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
      "contactid":"87546951-c543-e611-80d5-00155da84802"  
   },  
   "contact_customer_accounts":[  
      {  
         "@odata.etag":"W/\"620847\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"8e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620849\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"92546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620851\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"96546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620853\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9a546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620855\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9e546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620857\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a2546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620859\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a6546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620861\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"aa546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620863\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"ae546951-c543-e611-80d5-00155da84802"  
      }  
   ],  
   "Account_Tasks":[  
      {  
         "@odata.etag":"W/\"620840\"",  
         "subject":"Task 1",  
         "description":"Task 1 description",  
         "activityid":"8b546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620842\"",  
         "subject":"Task 2",  
         "description":"Task 2 description",  
         "activityid":"8c546951-c543-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"620844\"",  
         "subject":"Task 3",  
         "description":"Task 3 description",  
         "activityid":"8d546951-c543-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
-- Expanding multiple property types in one request --   
Account 'Contoso, Ltd. (sample)' has the following primary contact person:  
    Fullname: 'Yvonne McKay (sample)'   
    Jobtitle: 'Coffee Master'   
    Annualincome: '45000'  
Account 'Contoso, Ltd. (sample)' has the following related contacts:  
    1) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
    3) Maria Cambell (sample), Accounts Manager, $31,000.00  
    4) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    5) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    6) Robert Lyon (sample), Senior Technician, $78,000.00  
    7) Paul Cannon (sample), Ski Instructor, $68,500.00  
    8) Rene Valdes (sample), Data Analyst III, $86,000.00  
    9) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
Account 'Contoso, Ltd. (sample)' has the following tasks:  
    1) Task 1, Task 1 description  
    2) Task 2, Task 2 description  
    3) Task 3, Task 3 description  
```  
  
<a name="bkmk_fetchxml"></a>

## <a name="fetchxml-queries"></a>FetchXML-Abfragen

<!-- TODO:
Besides query filter operations, the Web API also supports FetchXML queries. FetchXml provides an alternative way to define queries and additional options to perform aggregations. More information:[Build queries with FetchXML](../org-service/build-queries-fetchxml.md)   -->
  
<!-- TODO: To use fetch xml you must compose a string representing the query. Make sure the query string conforms to the [FetchXML schema](../org-service/fetchxml-schema.md). Before you include the string in the URL you must URL encode the string.   -->
  
 Alle Abfrageoptionen, die wir normalerweise definieren, wie z.B. `$select`, `$filter` und `$orderby` werden nun in XML definiert. In diesem Vorgang erstellen wir eine Abfrage für alle Kontakte, deren `fullname` `(sample)`entspricht, und sortieren die Ergebnisse absteigend nach `fullname`. Dies ist der XML-Code für dieses Beispiel  
  
```xml  
<fetch mapping="logical" output-format="xml-platform" version="1.0" distinct="false">  
  <entity name="contact">  
    <attribute name="fullname" />  
    <attribute name="jobtitle" />  
    <attribute name="annualincome" />  
    <order descending="true"  
           attribute="fullname" />  
    <filter type="and">  
      <condition value="%(sample)%"  
                 attribute="fullname"  
                 operator="like" />  
    </filter>  
  </entity>  
</fetch>  
```  
  
 **HTTP-Anforderung**  
  
 Die Abfragezeichenfolge der Anforderung wird in codierter Form an den Server gesendet. Die codierte Kopfzeile sieht wie folgt aus.  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?fetchXml=%253Cfetch%2520mapping%253D%2522logical%2522%2520output-format%253D%2522xml-platform%2522%2520version%253D%25221.0%2522%2520distinct%253D%2522false%2522%253E%2520%2520%2520%253Centity%2520name%253D%2522contact%2522%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522jobtitle%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522annualincome%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Corder%2520descending%253D%2522true%2522%2520attribute%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cfilter%2520type%253D%2522and%2522%253E%2520%2520%2520%2520%2520%2520%2520%253Ccondition%2520value%253D%2522%2525(sample)%2525%2522%2520attribute%253D%2522fullname%2522%2520operator%253D%2522like%2522%2520%252F%253E%2520%2520%2520%2520%2520%253C%252Ffilter%253E%2520%2520%2520%253C%252Fentity%253E%2520%253C%252Ffetch%253E%2520 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 4345  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome,_transactioncurrencyid_value,transactioncurrencyid,contactid)",  
   "value":[  
      {  
         "@odata.etag":"W/\"621502\"",  
         "fullname":"Yvonne McKay (sample)",  
         "jobtitle":"Coffee Master",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$45,000.00",  
         "annualincome":45000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9255b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621627\"",  
         "fullname":"Susanna Stubberod (sample)",  
         "jobtitle":"Senior Purchaser",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$52,000.00",  
         "annualincome":52000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9955b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621635\"",  
         "fullname":"Scott Konersmann (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$38,000.00",  
         "annualincome":38000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a955b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621637\"",  
         "fullname":"Robert Lyon (sample)",  
         "jobtitle":"Senior Technician",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$78,000.00",  
         "annualincome":78000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"ad55b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621641\"",  
         "fullname":"Rene Valdes (sample)",  
         "jobtitle":"Data Analyst III",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$86,000.00",  
         "annualincome":86000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b555b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621639\"",  
         "fullname":"Paul Cannon (sample)",  
         "jobtitle":"Ski Instructor",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$68,500.00",  
         "annualincome":68500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b155b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621629\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"9d55b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621633\"",  
         "fullname":"Nancy Anderson (sample)",  
         "jobtitle":"Logistics Specialist",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$63,500.00",  
         "annualincome":63500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a555b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621631\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a155b257-c843-e611-80d5-00155da84802"  
      },  
      {  
         "@odata.etag":"W/\"621643\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b955b257-c843-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts Fetched by fullname containing '(sample)':  
    1) Yvonne McKay (sample), Coffee Master, $45,000.00  
    2) Susanna Stubberod (sample), Senior Purchaser, $52,000.00  
    3) Scott Konersmann (sample), Accounts Manager, $38,000.00  
    4) Robert Lyon (sample), Senior Technician, $78,000.00  
    5) Rene Valdes (sample), Data Analyst III, $86,000.00  
    6) Paul Cannon (sample), Ski Instructor, $68,500.00  
    7) Nancy Anderson (sample), Activities Manager, $55,500.00  
    8) Nancy Anderson (sample), Logistics Specialist, $63,500.00  
    9) Maria Cambell (sample), Accounts Manager, $31,000.00  
    10) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
### <a name="fetchxml-pagination"></a>FetchXML-Paginierung

Die Art, wie FetchXML Auslagerungen verarbeitet, unterscheidet sich von der Verarbeitung durch den Abfragenfilter. In FetchXML können Sie ein `count`-Attribut festlegen, das angibt, wieviele Ergebnisse pro Seite zurückgegeben werden. In derselben Anforderung verwenden Sie das `page`-Attribut, um die gewünschte Seitenzahl anzugeben. Dieser Vorgang erstellt eine Anforderung für Seite 3 aus dem vorherigen FetchXML-Beispiels. Basierend auf unseren Beispieldaten sollten zehn Kontakte in unseren Ergebnissen angezeigt werden. Wenn jede Seite auf nur vier Entitäten pro Seite beschränkt wird, sollten wir also über drei Seiten verfügen. Seite 3 sollte nur zwei Entitäten enthalten. Wenn wir dann eine Seite 4 anfragen, wird das System null Ergebnisse zurückgegeben.  
  
```xml  
<fetch mapping="logical"  
       output-format="xml-platform"  
       version="1.0"  
       distinct="false"  
       page="3"  
       count="4">  
  <entity name="contact">  
    <attribute name="fullname" />  
    <attribute name="jobtitle" />  
    <attribute name="annualincome" />  
    <order descending="true"  
           attribute="fullname" />  
    <filter type="and">  
      <condition value="%(sample)%"  
                 attribute="fullname"  
                 operator="like" />  
    </filter>  
  </entity>  
</fetch>  
```  
  
 **HTTP-Anforderung**  
  
 Die Abfragezeichenfolge der Anforderung wird in codierter Form an den Server gesendet. Die codierte Kopfzeile sieht wie folgt aus.  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?fetchXml=%253Cfetch%2520mapping%253D%2522logical%2522%2520output-format%253D%2522xml-platform%2522%2520version%253D%25221.0%2522%2520distinct%253D%2522false%2522%2520page%253D%25223%2522%2520count%253D%25224%2522%253E%2520%2520%2520%253Centity%2520name%253D%2522contact%2522%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522jobtitle%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cattribute%2520name%253D%2522annualincome%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Corder%2520descending%253D%2522true%2522%2520attribute%253D%2522fullname%2522%2520%252F%253E%2520%2520%2520%2520%2520%253Cfilter%2520type%253D%2522and%2522%253E%2520%2520%2520%2520%2520%2520%2520%253Ccondition%2520value%253D%2522%2525(sample)%2525%2522%2520attribute%253D%2522fullname%2522%2520operator%253D%2522like%2522%2520%252F%253E%2520%2520%2520%2520%2520%253C%252Ffilter%253E%2520%2520%2520%253C%252Fentity%253E%2520%253C%252Ffetch%253E%2520 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 1037  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle,annualincome,_transactioncurrencyid_value,transactioncurrencyid,contactid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621631\"",  
         "fullname":"Maria Cambell (sample)",  
         "jobtitle":"Accounts Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$31,000.00",  
         "annualincome":31000.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"a155b257-c843-e611-80d5-00155da84802"  
      },  
      {   
         "@odata.etag":"W/\"621643\"",  
         "fullname":"Jim Glynn (sample)",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802",  
         "contactid":"b955b257-c843-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Contacts Fetched by fullname containing '(sample)' - Page 3:  
    1) Maria Cambell (sample), Accounts Manager, $31,000.00  
    2) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
```  
  
<a name="bkmk_predefinedqueries"></a>
 
## <a name="predefined-queries"></a>Vordefinierte Abfragen

Sie können die Web-API verwenden, um vordefinierte Abfragen auszuführen. Weitere Informationen: [Abrufen und Ausführen von vordefinierten Abfragen](retrieve-and-execute-predefined-queries.md)  
  
### <a name="saved-query"></a>Gespeicherte Abfrage

In diesem Vorgang stellen wir eine Anfrage für die `savedqueryid` GUID der gespeicherten Abfrage mit dem Namen **Aktive Firmen**. Die mithilfe der GUID und des `savedQuery`-Parameters, erstellen wir eine Abfrage für eine Liste von aktiven Firmen.  
  
 Die GUID der gespeicherten Abfrage abrufen.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/savedqueries?$select=name,savedqueryid&$filter=name%20eq%20'Active%20Accounts' HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
Referer: https://localhost:1469/WebAPIQuery.html  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 251  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#savedqueries(name,savedqueryid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"443067\"",  
         "name":"Active Accounts",  
         "savedqueryid":"00000000-0000-0000-00aa-000010001002"  
      }  
   ]  
}  
```  
  
 Abrufen des Inhalts der gespeicherten Abfrage mit dem `savedQuery`-Parameter  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/accounts?savedQuery=00000000-0000-0000-00aa-000010001002 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
REQ_ID: 2bc532c4-d445-44cd-adae-1909a616d6bc  
OData-Version: 4.0  
Preference-Applied: odata.include-annotations="OData.Community.Display.V1.FormattedValue"  
Content-Length: 446  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,_primarycontactid_value,primarycontactid,accountid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621613\"",  
         "name":"Contoso, Ltd. (sample)",  
         "_primarycontactid_value@OData.Community.Display.V1.FormattedValue":"Yvonne McKay (sample)",  
         "_primarycontactid_value":"9255b257-c843-e611-80d5-00155da84802",  
         "accountid":"9155b257-c843-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
-- Saved Query --   
Saved Query (Active Accounts):  
    1) Contoso, Ltd. (sample)  
```  
  
### <a name="user-query"></a>Benutzerabfrage

In diesem Beispiel wird eine Benutzeranfrage erstellt, ausgeführt und dann aus dem System gelöscht. Diese Benutzeranfrage ruft alle Kontakte ab, deren `fullname` `(sample)`enthält und `jobtitle` `manager`enthält und bei denen das `annualincome` größer als `55000` ist. Unsere Beispieldaten enthalten zwei Kontakte, die der Abfrage entsprechen.  
  
 Die GUID der Benutzerabfrage abrufen.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/userqueries?$select=name,userqueryid,&$filter=name%20eq%20'My%20User%20Query' HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Referer: https://localhost:1469/WebAPIQuery.html  
  
```  
  
 **HTTP-Antwort**  
  
```  
Pragma: no-cache  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 246  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#userqueries(name,userqueryid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621698\"",  
         "name":"My User Query",  
         "userqueryid":"7ec390ab-c943-e611-80d5-00155da84802"  
      }  
   ]  
}  
```  
  
 Abrufen des Inhalts der Benutzeranfrage, indem der GUID-Wert mit dem `userQuery`-Parameter übergeben wird.  
  
 **HTTP-Anforderung**  
  
```  
GET https://[Organization URI]/api/data/v9.0/contacts?userQuery=7ec390ab-c943-e611-80d5-00155da84802 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Prefer: odata.maxpagesize=10, odata.include-annotations=OData.Community.Display.V1.FormattedValue  
  
```  
  
 **HTTP-Antwort**  
  
```  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 1040  
  
{   
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,contactid,jobtitle,annualincome,_transactioncurrencyid_value,transactioncurrencyid)",  
   "value":[   
      {   
         "@odata.etag":"W/\"621643\"",  
         "fullname":"Jim Glynn (sample)",  
         "contactid":"b955b257-c843-e611-80d5-00155da84802",  
         "jobtitle":"Senior International Sales Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$81,400.00",  
         "annualincome":81400.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802"  
      },  
      {   
         "@odata.etag":"W/\"621629\"",  
         "fullname":"Nancy Anderson (sample)",  
         "contactid":"9d55b257-c843-e611-80d5-00155da84802",  
         "jobtitle":"Activities Manager",  
         "annualincome@OData.Community.Display.V1.FormattedValue":"$55,500.00",  
         "annualincome":55500.0000,  
         "_transactioncurrencyid_value@OData.Community.Display.V1.FormattedValue":"US Dollar",  
         "_transactioncurrencyid_value":"518c78c9-d3f6-e511-80d0-00155da84802"  
      }  
   ]  
}  
```  
  
 **Konsolenausgabe**  
  
```  
-- User Query --   
Saved User Query:  
    1) Jim Glynn (sample), Senior International Sales Manager, $81,400.00  
    2) Nancy Anderson (sample), Activities Manager, $55,500.00  
```  
  
### <a name="see-also"></a>Siehe auch

[Verwenden der Common Data Service-Web-API](overview.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Abrufen und Ausführen von vordefinierten Abfragen](retrieve-and-execute-predefined-queries.md)<br />
[Web API-Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)<br />
[Web API-Abfragedatenbeispiele (clientseitiges JavaScript)](samples/query-data-client-side-javascript.md)

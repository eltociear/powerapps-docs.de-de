---
title: Abrufen und Ausführen von vordefinierten Abfragen (Common Data Service for Apps) | Microsoft Docs
description: 'Common Data Service for Apps bietet Administratoren eine Möglichkeit, Systemansichten zu erstellen, die für alle Benutzer verfügbar sind. Lesen Sie, wie Sie eine vordefinierte Abfrage mit FetchXML verfassen können, um eine Abfragezeichenfolge zu erstellen, um die Daten abzurufen'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3d771a18-3dc5-4372-a7c7-40b3b1f986d8
caps.latest.revision: 16
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="retrieve-and-execute-predefined-queries"></a>Abrufen und Ausführen von vordefinierten Abfragen

Common Data Service (CDS) for Apps bietet Administratoren eine Möglichkeit, Systemansichten zu erstellen, die für alle Benutzer verfügbar sind. Einzelne Benutzer können die erweiterten Suchanfragen speichern und in der Anwendung wiederverwenden. Beide stellen vordefinierte Abfragen dar die Sie mit der Web-API abrufen und ausführen können. Sie können eine Abfrage auch mit FetchXml erstellen und zum Abfragen von Daten nutzen.

<a name="bkmk_predefinedQueries"></a>

## <a name="predefined-queries"></a>Vordefinierte Abfragen

Common Data Service for Apps erlaubt Ihnen, wie hier aufgelistet zwei Arten von Abfragen zu definieren, zu speichern und durchzuführen.

|Abfragetyp|Beschreibung|
|----------------|-----------------|
|**Gespeicherte Abfrage**|System-definierte Ansichten für eine Entität Diese Ansichten werden in <xref href="Microsoft.Dynamics.CRM.savedquery?text=savedquery EntityType" /> gespeichert. Weitere Informationen: [Anpassen von Entitätsansichten](../../model-driven-apps/customize-entity-views.md).| 
|**Benutzerabfrage**|Erweiterte Suchen, die vom Benutzer für eine Entität gespeichert wurden Diese Ansichten werden in <xref href="Microsoft.Dynamics.CRM.userquery?text=userquery EntityType" /> gespeichert. Weitere Informationen: [UserQuery (gespeicherte Ansicht)-Entität](../saved-queries.md)|

Datensätze für beide Arten von Entitäten enthalten die FetchXML-Definition für das Zurückgeben der Daten. Sie können den jeweiligen Entitätstyp abfragen, um den Wert des Primärschlüssels abzurufen. Mit dem Primärschlüsselwert können Sie die Abfrage durchführen, indem Sie den Primärschlüsselwert übergeben. Um beispielsweise die gespeicherte Abfrage **Aktive Firmen** auszuführen, müssen Sie erst den Primärschlüssel mit einer Abfrage wie dieser abrufen.

```http
GET [Organization URI]/api/data/v9.0/savedqueries?$select=name,savedqueryid&$filter=name eq 'Active Accounts'
```

Sie können dann den `savedqueryid`-Wert verwenden und als Wert an den savedQuery-Parameter an den Firmen-Entitätssatz übergeben.

```http
GET [Organization URI]/api/data/v9.0/accounts?savedQuery=00000000-0000-0000-00aa-000010001002
```

Verwenden Sie diesen Ansatz auch, um userqueryid zu erhalten und als Wert für den `userQuery`-Parameter an den Entitätssatz zu übergeben, der mit dem entsprechenden `returnedtypecode` der gespeicherten Abfrage übereinstimmt.

```http
GET [Organization URI]/api/data/v9.0/accounts?userQuery=121c6fd8-1975-e511-80d4-00155d2a68d1
```

### <a name="apply-a-query-to-any-collection-of-the-appropriate-type"></a>Anwenden einer Abfrage auf eine Sammlung des entsprechenden Typs

Neben dem einfachen Anwenden der gespeicherten Abfrage auf die hauptsächliche Entitätssatz-Sammlung können Sie auch eine gespeicherte Abfrage oder gespeicherte Benutzerabfrage nutzen, um dieselbe Filterung auf eine Sammlung des entsprechenden Typs der Entitäten anzuwenden. Wenn Sie beispielsweise eine Abfrage auf die Entitäten anwenden möchten, die mit einer bestimmten Entität zusammenhängen, können Sie dasselbe Muster anwenden. Zum Beispiel wendet die folgende URL die Abfrage **Offene Verkaufschancen** auf die Verkaufschancen an, die mit einem bestimmen Konto über eine als Sammlung bewertete Navigationseigenschaft von `opportunity_parent_account` zusammenhängen.

```http
GET [Organization URI]/api/data/v9.0/accounts(8f390c24-9c72-e511-80d4-00155d2a68d1)/opportunity_parent_account/?savedQuery=00000000-0000-0000-00aa-000010003001
```

<a name="bkmk_useFetchXML"></a>

## <a name="use-custom-fetchxml"></a>Benutzerdefiniertes FetchXML verwenden

FetchXML ist eine herstellereigene Abfragesprache, die Möglichkeiten zur Durchführung einer Aggregation bieten. Weitere Informationen: [Verwendung von FetchXML zum Abfragen von Daten](../use-fetchxml-construct-query.md)

Sie können URL-verschlüsseltes FetchXML als Abfrage an den Entitätssatz übergeben, der der Root-Entität der Abfrage entspricht, indem Sie den`fetchXml`Abfrage-Zeichenfolgen-Parameter nutzen, um die Ergebnisse von der Web-API zurückzugeben. Zum Beispiel können Sie das folgende FetchXML haben, das Konto als Entität hat.  

```xml  
<fetch mapping='logical'>
   <entity name='account'>
      <attribute name='accountid'/>
      <attribute name='name'/>
</entity>
</fetch>
```

Der URL-verschlüsselte Wert von diesem FetchXML ist wie hier gezeigt.

```text
%3Cfetch%20mapping='logical'%3E%3Centity%20name='account'%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='name'/%3E%3C/entity%3E%3C/fetch%3E
```

Die meisten Programmiersprachen umfassen eine Funktion zum URL-Codieren einer Zeichenfolge. Beispiel: In JavaScript verwenden Sie die [encodeURI](http://www.ecma-international.org/ecma-262/5.1/)-Funktion. Sie sollten jede Anforderung URL-Codieren, die Sie an einen RESTful-Webdienst senden. Wenn Sie eine URL in die Adressleiste Ihres Browsers eingeben, sollte diese die Adresse automatisch URL-codieren. Das folgende Beispiel zeigt eine GET-Anforderung, die das vorher gezeigte FetchXML einsetzt, die den Entitätspfad für Konten verwendet.

**Anforderung**

```http
GET [Organization URI]/api/data/v9.0/accounts?fetchXml=%3Cfetch%20mapping='logical'%3E%3Centity%20name='account'%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='name'/%3E%3C/entity%3E%3C/fetch%3E HTTP/1.1
Accept: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0
```

**Antwort**

```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(accountid,name)","value":[  
    {  
      "@odata.etag":"W/\"506678\"","accountid":"89390c24-9c72-e511-80d4-00155d2a68d1","name":"Fourth Coffee (sample)"  
    },{  
      "@odata.etag":"W/\"502172\"","accountid":"8b390c24-9c72-e511-80d4-00155d2a68d1","name":"Litware, Inc. (sample)"  
    },{  
      "@odata.etag":"W/\"502174\"","accountid":"8d390c24-9c72-e511-80d4-00155d2a68d1","name":"Adventure Works (sample)"  
    },{  
      "@odata.etag":"W/\"506705\"","accountid":"8f390c24-9c72-e511-80d4-00155d2a68d1","name":"Fabrikam, Inc. (sample)"  
    },{  
      "@odata.etag":"W/\"506701\"","accountid":"91390c24-9c72-e511-80d4-00155d2a68d1","name":"Blue Yonder Airlines (sample)"  
    },{  
      "@odata.etag":"W/\"502180\"","accountid":"93390c24-9c72-e511-80d4-00155d2a68d1","name":"City Power & Light (sample)"  
    },{  
      "@odata.etag":"W/\"502182\"","accountid":"95390c24-9c72-e511-80d4-00155d2a68d1","name":"Contoso Pharmaceuticals (sample)"  
    },{  
      "@odata.etag":"W/\"506704\"","accountid":"97390c24-9c72-e511-80d4-00155d2a68d1","name":"Alpine Ski House (sample)"  
    },{  
      "@odata.etag":"W/\"502186\"","accountid":"99390c24-9c72-e511-80d4-00155d2a68d1","name":"A. Datum Corporation (sample)"  
    },{  
      "@odata.etag":"W/\"502188\"","accountid":"9b390c24-9c72-e511-80d4-00155d2a68d1","name":"Coho Winery (sample)"  
    },{  
      "@odata.etag":"W/\"504177\"","accountid":"0a3238d4-f973-e511-80d4-00155d2a68d1","name":"Litware, Inc."  
    }  
  ]  
}  
```

<a name="bkmk_WebAPIFetchPaging"></a>

### <a name="paging-with-fetchxml"></a>Paging mit FetchXML

Mit FetchXML können Sie Paging anwenden, indem Sie die Attribute `page` und `count` des Elements `fetch` anwenden. Beispiel: Um eine Abfrage für Konten festzulegen und die Anzahl der Entitäten auf 2 zu reduzieren und nur die erste Seite wiederzugeben, sollte das folgende fetchXML:

```xml
<fetch mapping="logical" page="1" count="2">  
 <entity name="account">  
  <attribute name="accountid" />  
  <attribute name="name" />  
  <attribute name="industrycode" />  
 <order attribute="name" />  
 </entity>  
</fetch>
```

<!-- TODO:
With a request using FetchXML you can also request a paging cookie and include it with your query. More information:[Page large result sets with FetchXML](../org-service/page-large-result-sets-with-fetchxml.md)   -->

Ein Paging-Cookie muss als Anmerkung (Annotation) angefordert werden. Stellen Sie die `odata.include-annotations`-Präferenz für das Verwenden (oder Einschließen) von `Microsoft.Dynamics.CRM.fetchxmlpagingcookie` ein und eine `@Microsoft.Dynamics.CRM.fetchxmlpagingcookie` -Eigenschaft wird mit dem Ergebnis zurückgegeben.

<a name="bkmk_FetchXMLwithinBatch"></a>

### <a name="use-fetchxml-within-a-batch-request"></a>FetchXML-Verwendung in einer Batchanforderung

Die Länger einer URL in einer `GET`-Anforderung wird begrenzt. Durch Einschließen von FetchXML als Parameter in der URL kann dieses Limit erreicht werden.  Sie können einen `$batch`-Vorgang mit einer `POST`-Anforderung als eine Methode zum Verschieben von FetchXML aus der URL und in den Anforderungstext verwenden. Dort gilt diese Beschränkung nicht. Weitere Informationen:[Ausführen von Batchvorgängen mit der Web-API](execute-batch-operations-using-web-api.md).

#### <a name="example"></a>Beispiel

**Anforderung**

```http
POST [Organization URI]/api/data/v9.0/$batch HTTP/1.1

Content-Type:multipart/mixed;boundary=batch_AAA123
Accept:application/json
OData-MaxVersion:4.0
OData-Version:4.0

--batch_AAA123
Content-Type: application/http
Content-Transfer-Encoding: binary

GET [Organization URI]/api/data/v9.0/accounts?fetchXml=%3Cfetch%20mapping='logical'%3E%3Centity%20name='account'%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='name'/%3E%3Cattribute%20name='telephone1'/%3E%3Cattribute%20name='accountid'/%3E%3Cattribute%20name='creditonhold'/%3E%3C/entity%3E%3C/fetch%3E HTTP/1.1
Content-Type: application/json
OData-Version: 4.0
OData-MaxVersion: 4.0

--batch_AAA123--
```

**Antwort**

```json
--batchresponse_cbfd44cd-a322-484e-913b-49e18af44e34
Content-Type: application/http
Content-Transfer-Encoding: binary

HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{  
   "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(accountid,name,telephone1,creditonhold)",
   "value":[  
      {  
         "@odata.etag":"W/\"563737\"",
         "accountid":"1f55c679-485e-e811-8151-000d3aa3c22a",
         "name":"Fourth Coffee (sample)",
         "telephone1":"+1-425-555-0121",
         "creditonhold":false
      },
      {  
         "@odata.etag":"W/\"563739\"",
         "accountid":"2555c679-485e-e811-8151-000d3aa3c22a",
         "name":"Litware, Inc. (sample)",
         "telephone1":"+1-425-555-0120",
         "creditonhold":false
      }
   ]
}
--batchresponse_cbfd44cd-a322-484e-913b-49e18af44e34--
```



## <a name="see-also"></a>Siehe auch

[Web API-Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)<br />
[Web API-Abfragedatenbeispiele (clientseitiges JavaScript)](samples/query-data-client-side-javascript.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)<br />

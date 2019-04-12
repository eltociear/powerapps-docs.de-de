---
title: Abrufen einer Entität mit Web-API (Common Data Service) | Microsoft Docs
description: 'Lesen Sie, wie Sie eine GET-Anforderung mit der Common Data Service-Web-API anfordern, um Daten für eine Entität abzurufen, die als die Ressource mit einem eindeutigen Bezeichner angegeben wurde'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: abae4614-9e03-45e7-94fa-9e6e7225ece5
caps.latest.revision: 21
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="retrieve-an-entity-using-the-web-api"></a>Abrufen einer Entität mithilfe des Web-API

Verwenden Sie eine `GET`-Anfrage, um Daten für eine Entität abzurufen, spezifiziert als Ressource mit einzigartigem Bezeichner. Wenn Sie eine Entität abrufen, können Sie auch spezifische Eigenschaften anfordern und Navigationseigenschaften erweitern, um Eigenschaften von den verbundenen Unternehmen zurückgeben zu lassen.  

> [!NOTE]
>  Informationen zum Abrufen von Entitätsmetadaten, siehe [Abfragen von Metadaten mit der Web-API](query-metadata-web-api.md).

<a name="bkmk_basicRetrieve"></a>

## <a name="basic-retrieve-example"></a>Grundlegendes Abruf-Beispiel

Dieses Beispiel gibt Daten für eine Firmenentitätsinstanz mit dem Primärschlüsselwert zurück, der gleich 00000000-0000-0000-0000-000000000001 ist.

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)
```

Um mehrere Entitäten gleichzeitig abzurufen, seihe [Grundlegendes Abfragebeispiel](query-data-web-api.md#bkmk_basicQuery) in [Abfragen von Daten mit Internet-API](query-data-web-api.md).

> [!CAUTION]
>  Das oben genannte Beispiel gibt alle Eigenschaften für den Firmendatensatz zurück, was die Leistung beim Abruf von Daten senkt. Dieses Beispiel war nur dazu gedacht, zu veranschaulichen, wie Sie einen grundlegenden Abruf einer Entitätsinstanz in Common Data Service tätigen können. Weil alle Eigenschaften zurückgegeben wurden, haben wir die Antwortinformation für die Anfrage nicht in dieses Beispiel aufgenommen.
>
>  Als leistungsoptimiertes Verfahren müssen Sie immer die Systemanfragen-Option `$select` verwenden, um die zurückgegebenen Eigenschaften zu begrenzen beim Abruf von Daten. Sehen Sie den folgenden Abschnitt, **Spezifische Eigenschaften abrufen** für Informationen darüber.
  
<a name="bkmk_requestProperties"></a>

## <a name="retrieve-specific-properties"></a>Spezifische Eigenschaften abrufen

Verwenden Sie die `$select` Systemabfrageoption, um die Eigenschaften zu begrenzen, die zurückgegeben werden, indem Sie eine kommagetrennte Liste von Eigenschaftsnamen einschließen. Dies ist eine wichtige Methode für die Leistungssteigerung. Wenn Eigenschaften nicht mithilfe von `$select`angegeben wurden, werden alle Eigenschaften zurückgegeben.  

Das folgende Beispiel ruft die Eigenschaften `name` ind `revenue` für die Firmenentität mit dem Primärschlüssel gleich 00000000-0000-0000-0000-000000000001 ab.

**Anforderung**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name,revenue HTTP/1.1
Accept: application/json
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
```

**Antwort**
```http
HTTP/1.1 200 OK
Content-Type: application/json; odata.metadata=minimal
OData-Version: 4.0

{
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue)/$entity",  
"@odata.etag": "W/\"502186\"",  
"name": "A. Datum Corporation (sample)",  
"revenue": 10000,  
"accountid": "00000000-0000-0000-0000-000000000001",  
"_transactioncurrencyid_value":"b2a6b689-9a39-e611-80d2-00155db44581"  
}  

```

Wenn Sie bestimmte Eigenschaftstypen anfordern, können Sie erwarten, dass zusätzliche Schreibschutzeigenschaften automatisch zurückgegeben werden.

Wenn Sie einen Geldwert anfordern, wird die `_transactioncurrencyid_value`-Sucheigenschaft zurückgegeben. Diese Eigenschaft enthält nur den GUID-Wert der Transaktionswährung, daher könnten Sie diesen Wert verwenden, um Informationen über die Währung mithilfe von <xref href="Microsoft.Dynamics.CRM.transactioncurrency?text=transactioncurrency EntityType" /> abzurufen. Alternativ können Sie durch das Anfordern von Anmerkungen zusätzliche Daten in derselben Anforerung abrufen. Weitere Informationen:[Abrufen von Daten zu Sucheigenschaften](query-data-web-api.md#bkmk_lookupProperty)  

Wenn Sie eine Eigenschaft anfordern, die Teil eines zusammengesetzten Attributs für eine Adresse ist, erhalten Sie auch die zusammengesetzte Eigenschaft. Wenn beispielsweise Ihre Abfrage die `address1_line1`-Eigenschaft für einen Kontakt anfordert, wird die `address1_composite`-Eigenschaft ebenfalls zurückgegeben. 

<a name="BKMK_UsingAltKeys"></a>

## <a name="retrieve-using-an-alternate-key"></a>Abruf mit einem Alternativschlüssel

Wenn eine Entität einen definierten Alternativschlüssel hat, können Sie auch den Alternativschlüssel anstelle des eindeutigen Bezeichners für die Entität verwenden, um die Entität abzurufen. Zum Beispiel: Wenn die `Contact`-Entität eine Definition eines Alternativschlüssels hat, die die Eigenschaften firstname und emailaddress1 umfasst, können Sie den Kontakt unter Verwendung einer Abfrage mit den Daten für diese Schlüssel abrufen, wie hier gezeigt.

```http
GET [Organization URI]/api/data/v9.0/contacts(firstname='Joe',emailaddress1='abc@example.com')
```

Immer, wenn Sie eine Entität zum Abruf, Update oder Löschen eindeutig identifizieren müssen, können Sie Alternativschlüssel verwenden, die für die Entität konfiguriert sind. Standardmäßig sind keine Alternativschlüssel für Entitäten konfiguriert. Alternativschlüssel sind nur verfügbar, wenn die Organisation sie hinzufügt.

<a name="bkmk_retrieveSingleValue"></a>

## <a name="retrieve-a-single-property-value"></a>Rufen Sie einen einzelnen Eigenschaftswert ab

Wenn Sie nur den Wert einer einzelnen Eigenschaft für eine Entität abrufen müssen, können Sie den Namen der Eigenschaft an den URI anfügen, damit die Entität nur den Wert für diese Eigenschaft zurückgibt. Dieses ist ein leistungsoptimales Verfahren, weil weniger Daten in der Antwort zurückgegeben werden müssen.

Dieses Beispiel gibt nur den Wert der Eigenschaft Name für eine Firmenentität zurück.

**Anforderung**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/name HTTP/1.1
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
"@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(00000000-0000-0000-0000-000000000001)/name",
"value":"Adventure Works (sample)"
}
```

<a name="bkmk_retrieveNavigationPropertyValues"></a>

## <a name="retrieve-navigation-property-values"></a>Navigations-Eigenschaftswerte abrufen

Ebenso, wie Sie einzelne Eigenschaftswerte abrufen können, können Sie auch auf die Werte von Navigationseigenschaften (Nachschlagefelder) zugreifen, indem Sie den Namen der Navigationseigenschaft an den URI anfügen, der eine einzelne Entität referenziert.

Das folgende Beispiel bringt den vollständigen Namen des Primärkontaktes einer Firma unter Verwendung der `primarycontactid` Einzelwert-Navigationseigenschaft zurück.  

**Anforderung**
 ```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/primarycontactid?$select=fullname HTTP/1.1
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
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#contacts(fullname)/$entity",  
"@odata.etag": "W/\"500128\"",  
"fullname": "Rene Valdes (sample)",  
"contactid": "ff390c24-9c72-e511-80d4-00155d2a68d1"  
}

```

Für Navigationseigenschaften mit Sammelwerten haben Sie die Option, nur die Anzahl oder Referenzen auf die verbundenen Entitäten abzurufen.

Das folgende Beispiel gibt nur Referenzen auf Aufgaben zurück, die zu einer spezifischen Firma gehören, indem `/$ref` an die Anfrage angefügt wird.

**Anforderung**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/AccountTasks/$ref HTTP/1.1
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
"@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Collection($ref)",  
"value": [  
{  
"@odata.id": "[Organization URI]/api/data/v9.0/tasks(6b5941dd-d175-e511-80d4-00155d2a68d1)"  
},  
{  
"@odata.id": "[Organization URI]/api/data/v9.0/tasks(fcbb60ed-d175-e511-80d4-00155d2a68d1)"  
}  
]  
}  
  
```
Das folgende Beispiel gibt die Anzahl der Aufgaben zurück, bezogen auf eine spezifische Firma, unter Verwendung der Account_Tasks Navigationseigenschaft mit Sammelwerten mit `/$count` hinzugefügt.  

 **Anforderung**
```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/Account_Tasks/$count HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
```
**Antwort**
```http
ï»¿2
```
> [!NOTE]
> Der zurückgegebene Wert umfasst die UTF-8-Byte Order Mark-(BOM)-Zeichen (`ï»¿`), die angeben, dass dieses ein UTF-8-Dokument ist.

<a name="bkmk_expandRelated"></a>

## <a name="retrieve-related-entities-for-an-entity-by-expanding-navigation-properties"></a>Abrufen verwandter Entitäten für eine Entität durch Erweitern der Navigationseigenschaften

Verwenden Sie die `$expand`-Systemabfrageoption, um zu steuern, welche Daten von den verbundenen Entitäten zurückgegeben werden. Es gibt zwei Typen von Navigationseigenschaften:  

- *Einzelwertige* Navigationseigenschaften entsprechen Suchattributen, die viel-zu-ein-Beziehungen unterstützen und eine Referenz auf eine andere Entität einstellen dürfen.
- *Sammlungswertige* Navigationseigenschaften entsprechen ein-zu-vielen oder viel-zu-vielen Verhältnissen.  

Wenn Sie einfach den Namen der Navigationseigenschaft einschließen, rufen Sie alle Eigenschaften für in Verbindung stehende Datensätze ab. Sie können die Eigenschaften begrenzen, die für in Verbindung stehende Aufzeichnungen unter Verwendung der Systemabfrageoption `$select` in Klammern nach dem Namen der Navigationseigenschaft zurückgegeben werden. Verwenden Sie dieses für einzelwertige und sammlungswertige Navigationseigenschaften.

> [!NOTE]
> Um verknüpfte Entitäten für Entitätssätze abzurufen, siehe [Abrufen verwandter Entitäten durch Erweitern der Navigationseigenschaften](query-data-web-api.md#bkmk_expandRelated).  

- **Abrufen verknüpfter Entitäten für eine Entitätsinstanz durch Erweitern einwertiger Navigationseigenschaften**: <br />Im folgenden Beispiel wird gezeigt, wie der Kontakt für eine Firmenentität abgerufen wird. Für den in Verbindung stehenden Kontaktdatensatz rufen wir nur die Kontaktkennung und den vollen Namen ab.

  **Anforderung**
  ```http
    GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name&$expand=primarycontactid($select=contactid,fullname) HTTP/1.1  
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
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(contactid,fullname))/$entity",  
    "@odata.etag":"W/\"550616\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"00000000-0000-0000-0000-000000000001",  
    "primarycontactid":{  
    "@odata.etag":"W/\"550626\"",  
    "contactid":"c59648c3-68f7-e511-80d3-00155db53318",  
    "fullname":"Nancy Anderson (sample)"  
    }  
    }  
  
  ```
  Anstatt die verbundenen Entitäten für Entitätsinstanzen abzurufen, können Sie auch Verweise (Verbindungen) auf die verbundenen Entitäten zurückgeben, indem Sie die einwertige Navigationseigenschaft mit der Option `$ref` erweitern. Im folgenden Beispiel werden Links zum Kontaktdatensatz für die Firmenentität zurückgegeben.  

  **Anforderung**
  ```http
    GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name&$expand=primarycontactid/$ref HTTP/1.1  
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
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid)/$entity",  
    "@odata.etag":"W/\"550616\"",  
    "name":"Adventure Works (sample)",  
    "accountid":"00000000-0000-0000-0000-000000000001",  
    "_primarycontactid_value":"c59648c3-68f7-e511-80d3-00155db53318",  
    "primarycontactid":{  
    "@odata.id":"[Organization URI]/api/data/v9.0/contacts(c59648c3-68f7-e511-80d3-00155db53318)"  
    }  
    }
  ```
- **Abrufen verknüpfter Entitäten für eine Entitätsinstanz durch Erweitern sammlungswertiger Navigationseigenschaften**:<br /> Im folgenden Beispiel wird gezeigt, wie Sie alle Aufgaben abrufen können, die einem Firmendatensatz zugeordnet sind.

  **Anforderung**

  ```http
  GET [Organization URI]/api/data/v9.0/accounts(915e89f5-29fc-e511-80d2-00155db07c77)?$select=name&$expand=Account_Tasks($select=subject,scheduledstart)
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
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,Account_Tasks,Account_Tasks(subject,scheduledstart))/$entity",  
    "@odata.etag":"W/\"514069\"","name":"Sample Child Account 1","accountid":"915e89f5-29fc-e511-80d2-00155db07c77",  
    "Account_Tasks":[  
    {  
    "@odata.etag":"W/\"514085\"",  
    "subject":"Sample Task 1",  
    "scheduledstart":"2016-04-11T15:00:00Z",  
    "activityid":"a983a612-3ffc-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514082\"",  
    "subject":"Sample Task 2",  
    "scheduledstart":"2016-04-13T15:00:00Z",  
    "activityid":"7bcc572f-3ffc-e511-80d2-00155db07c77"  
   }  
  ]  
  }
  ```
  
 > [!NOTE]
 > Wenn Sie auf sammlungswertige Navigationsparameter erweitern, um verbundene Entitäten für *Entitätssätze* zurückzugeben, wird stattdessen eine @odata.nextLink-Eigenschaft für die verbundenen Entitäten zurückgegeben. Sie sollten den Wert der @odata.nextLink-Eigenschaft mit einer neuen GET-Anforderung nutzen, um die benötigten Daten zurückzugeben. Weitere Informationen: [Abrufen verwandter Entitäten durch Erweitern der Navigationseigenschaften](query-data-web-api.md#bkmk_expandRelated)

- **Rufen Sie verbundene Entitäten für eine Entitätsinstanz durch Erweitern von einzelwertigen und sammlungswertigen Navigationseigenschaften ab**: Das folgende Beispiel zeigt, wie Sie verbundene Entitäten für eine Entitätsinstanz unter Verwendung der einzel- und sammlungswertigen Navigationseigenschaften erweitern können.  

  **Anforderung**

  ```http 
    GET [Organization URI]/api/data/v9.0/accounts(99390c24-9c72-e511-80d4-00155d2a68d1)?$select=accountid&$expand=parentaccountid($select%20=%20createdon,%20name),Account_Tasks($select%20=%20subject,%20scheduledstart) HTTP/1.1  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0
  ```

  **Antwort**

  ```http
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  

    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(accountid,parentaccountid,Account_Tasks,parentaccountid(createdon,name),Account_Tasks(subject,scheduledstart))/$entity","@odata.etag":"W/\"514069\"","accountid":"915e89f5-29fc-e511-80d2-00155db07c77",  
    "parentaccountid":{  
    "@odata.etag":"W/\"514074\"","createdon":"2016-04-06T00:29:04Z",  
    "name":"Adventure Works (sample)",  
    "accountid":"3adbf27c-8efb-e511-80d2-00155db07c77"  
    },"Account_Tasks":[  
    {  
    "@odata.etag":"W/\"514085\"",  
    "subject":"Sample Task 1",  
    "scheduledstart":"2016-04-11T15:00:00Z",  
    "activityid":"a983a612-3ffc-e511-80d2-00155db07c77"  
    },{  
    "@odata.etag":"W/\"514082\"",  
    "subject":"Sample Task 2",  
    "scheduledstart":"2016-04-13T15:00:00Z",  
    "activityid":"7bcc572f-3ffc-e511-80d2-00155db07c77"  
    }  
    ]  
    }
  ```

> [!NOTE]
> Sie können keine `/$ref`- oder `/$count`-Pfadsegmente verwenden, um nur den URI für die verbundene Entität oder die Anzahl der verbundenen Entitäten zurückzugeben.

<a name="bkmk_optionsOnExpand"></a>

## <a name="options-to-apply-to-expanded-entities"></a>Optionen, die auf erweiterte Entitäten anwendbar sind

 Sie können bestimmte Systemabfrageoptionen auf die Entitäten anwenden, die für eine sammlungswertige Navigationseigenschaft zurückgegeben werden. Benutzen Sie eine Semikolon-getrennte Liste von Systemabfrageoptionen, die in Klammern nach dem Namen der sammlungswertigen Navigationseigenschaft eingeschlossen werden. Sie können `$select`, `$filter`, `$orderby` und `$top` verwenden.

 Das folgende Beispiel filtert die Ergebnisse der Aufgabenentitäten, die sich auf ein Konto beziehen, zu denen mit Betreff, der auf „1“ endet.

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$expand=Account_Tasks($filter=endswith(subject,'1');$select=subject)  
```

Das folgende Beispiel spezifiziert, dass in Verbindung stehende Aufgaben in aufsteigender Reihenfolge zurückgegeben werden sollen, basierend auf der Eigenschaft `createdon`.

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$expand=Account_Tasks($orderby=createdon asc;$select=subject,createdon)  
```

 Das folgende Beispiel bringt nur die erste bezogene Aufgabe zurück.

```http
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$expand=Account_Tasks($top=1;$select=subject)
```

> [!NOTE]
> Dieses ist eine Teilmenge der Systemabfrageoptionen, die im Abschnitt "11.2.4.2.1 Expand Options" der [OData Version 4.0 Part 1: Protocol Plus Errata 02 beschrieben werden](http://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html) beschrieben werden. Die Optionen`$skip`, `$count`, `$search`, `$expand` und `$levels` werden für die Web-API nicht unterstützt.

<a name="bkmk_DetectIfChanged"></a>

## <a name="detect-if-an-entity-has-changed-since-it-was-retrieved"></a>Erkennen Sie, ob sich eine Entität geändert hat, seit sie abgerufen wurde

Als leistungsoptimales Verfahren sollten Sie nur die Daten anfordern, die Sie benötigen. Wenn Sie zuvor einen Entitätsdatensatz abgerufen haben, können Sie das *ETag* verwenden, das einem zuvor abgerufenen Datensatz zugeordnet ist, um bedingte Abrufe zu diesem Datensatz auszuführen.  Weitere Informationen finden Sie unter [Bedingte Abrufe](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged).  

<a name="bkmk_formattedValues"></a>

## <a name="retrieve-formatted-values"></a>Abrufen von formatierten Werten

Der Anforderung von formatierten Werten beim Abruf einzelner Datensätze wird die gleiche Weise getan wie beim Anfordern von Entitätssätzen. Weitere Informationen:[Formatierte Werte einschließen](query-data-web-api.md#bkmk_includeFormattedValues).

### <a name="see-also"></a>Siehe auch

[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)<br />
[Beispiele grundlegender Web API-Operationen (clientseitiges JavaScript)](samples/basic-operations-client-side-javascript.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)<br />

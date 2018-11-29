---
title: retrieveMultipleRecords (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d4e92999-3b79-4783-8cac-f656fc5f7fda
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="retrievemultiplerecords-client-api-reference"></a>retrieveMultipleRecords (Client-API-Referenz)



[!INCLUDE[./includes/retrieveMultipleRecords-description.md](./includes/retrieveMultipleRecords-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.WebApi.retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>entityLogicalName</td>
<td>String</td>
<td>Ja</td>
<td>Der logische Entitätsname der Datensätze, die abgerufen werden sollen. Zum Beispiel: "Konto".</td>
</tr>
<tr>
<td>Optionen</td>
<td>String</td>
<td>No</td>
<td><p>OData-Systemabfrageoptionen oder FetchXML-Abfragen, um die Daten abzurufen. </p> 
<ul>
<li>Für Systemabfrageoptionen werden unterstützt: <b>$select</b>, <b>$top</b>, <b>$filter</b>, <b>$expand</b> und <b>$orderby</b>.</li>
<li>Um eine FetchXML-Abfrage anzugeben, verwenden Sie das <code>fetchXml</code>-Attribut für die Angabe der Abfrage:</li>
</ul>
<p>HINWEIS: Sie müssen immer <b>$select</b>-Systemabfrageoption verwenden, um Eigenschaften zu begrenzen, die nach einem Entitätsdatensatz zurückgegeben werden, durch Einschließen einer durch Trennzeichen getrennten Liste mit Eigenschaftennamen. Dies ist eine wichtige Methode für die Leistungssteigerung. Wenn Eigenschaften nicht mithilfe von <b>$select</b>angegeben wurden, werden alle Eigenschaften zurückgegeben.</li>
<p>Sie geben die Abfrageoptionen beginnend mit <code>?</code>an. Sie können auch mehrere Systemabfrageoptionen festlegen, indem Sie <code>&</code> zum Trennen der Abfrageoptionen verwenden.
<p>Siehe Beispiele weiter unten in diesem Thema, um zu sehen, wie Sie den <code>options</code>-Parameter für den Abruf mehrerer Szenarios definieren können.</td>
</tr>
<tr>
<td>maxPageSize</td>
<td>Zahl</td>
<td>No</td>
<td><p>Definieren Sie eine positive Zahl, die die Zahl der Entitätsdatensätze angibt, die pro Seite zurückgegeben werden. Wird dieser Parameter nicht angegeben, wird der Standard 5000 verwendet.</p>
<p>Wenn die Anzahl von Datensätzen, die abgerufen werden, mehr ist als im <code>maxPageSize</code>-Wert angegebenen, enthält <code>nextLink</code>-Attribut im zurückgegebenen Versprechenobjekt einen Link, um den nächsten Satz von Entitäten abzurufen. </td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>No</td>
<td><p>Eine Funktion zum Aufrufen, wenn ein Entitätsdatensatz abgerufen wird. Ein Objekt mit folgenden Attributen wird an die Funktion übergeben:</p>
<ul>
<li><b>Entitäten</b>: Ein Array von JSON-Objekten, wobei jedes Objekt den abgerufenen Entitätsdatensatz darstellt, der die Attribute und die Werte als <code>key: value</code> enthält. Die ID des Entitätsdatensatzes wird standardmäßig abgerufen.</li>
<li><b>nextLink</b>: Zeichenfolge. Wenn die Anzahl von Datensätzen, die abgerufen werden, mehr als der Wert ist, der im <code>maxPageSize</code>-Parameter in der Anforderung angegeben ist, gibt dieses Attribut die URL an, um die folgenden Datensatzgruppe zurückzugeben.</li>
</ul>
</td>
</tr>
<tr>
<td>errorCallback</td>
<td>Funktion</td>
<td>No</td>
<td>Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug.</td>
</tr>
</table>

## <a name="return-value"></a>Rückgabewert

Bei Erfolg wird ein Versprechen zurückgegeben, das ein Array von JSON-Objekten enthält (**Entitäten**) die die abgerufenen die Entitätsdatensätze und das Attribut **nextLink** (optional) mit der URL enthalten, die auf folgende Datensatzgruppe verweist, die ausgeführt wird, wenn Auslagerung (`maxPageSize`) in der Anforderung angegeben wurde und die Anzahl der Datensätze den Auslagerungswert übersteigt.

## <a name="examples"></a>Beispiele

Die meisten der Szenarien und Beispiele, die in [Abfragen-Daten mit Internet von](../../../../common-data-service/webapi/query-data-web-api.md) beschrieben werden, können mithilfe der **retrieveMutipleRecords**-Methode erzielt werden. Einige der Beispiele werden unten aufgelistet.

### <a name="basic-retrieve-multiple"></a>Grundlegendes Mehrere abrufen

Dieses Beispiel fragt den Firmen-Entitätssatz ab und verwendet die `$select` und `$top`-Systemabfrageoptionen, um die Name-Eigenschaft für ersten drei Firmen zurückzugeben:

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name&$top=3").then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }                    
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="specify-the-number-of-entities-to-return-in-a-page"></a>Geben Sie die Anzahl der in einer Seite zurückzugebenden Entitäten an

Im folgenden Beispiel wird gezeigt die Verwendung der `maxPageSize`-Parameter, um die Anzahl der in einer Seite anzuzeigenden Datensätze (3) anzugeben.

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name", 3).then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }
        console.log("Next page link: " + result.nextLink);
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

Dieses Beispiel veranschaulicht 3 Datensätze und einen Link zur nächsten Seite. Im Folgenden finden Sie ein Beispiel aus der **Konsole** in den Browserentwicklertools:

```
{@odata.etag: "W/"1035541"", name: "A. Datum", accountid: "475b158c-541c-e511-80d3-3863bb347ba8"}
@odata.etag: "W/"1035541""accountid: "475b158c-541c-e511-80d3-3863bb347ba8"name: "A. Datum"__proto__: Object
VM5595:4 
{@odata.etag: "W/"947306"", name: "Adventure Works", accountid: "a8a19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5595:4 
{@odata.etag: "W/"1033754"", name: "Alpine Ski House", accountid: "aaa19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5595:6 
Next page link: [Organization URI]/api/data/v9.0/accounts?$select=name&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257bAAA19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520first%253d%2522%257b475B158C-541C-E511-80D3-3863BB347BA8%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E
```

Verwenden Sie den Abfragenanteil der URL `nextLink`-Eigenschaft als Wert für den `options`-Parameter in dem nächsten **retrieveMultipleRecords**-Aufruf, um die nächste Datensatzgruppe abzurufen. Sie sollten keine zusätzlichen Systemabfrageoptionen für den Wert ändern oder anfügen. Für jede nachfolgende Anforderung weiterer Seiten sollten Sie denselben `maxPageSize`-Einstellungswert verwenden, der sich in der ursprünglichen retrieve multiple-Anforderung verwendet wurde. Zwischenspeichern Sie auch die zurückgegebenen Ergebnisse oder den Wert der nextLink-Eigenschaft, sodass Sie zu zuvor abgerufenen Seiten zurückkehren können. 

Beispielsweise zum Anzeigen der nächsten Seite von Datensätzen abzurufen, werden wir die Abfrage als Teil die `nextLink` URL dem `options` Parameter übergeben:

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name&$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22%253ccookie%2520page%253d%25221%2522%253e%253caccountid%2520last%253d%2522%257bAAA19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520first%253d%2522%257b475B158C-541C-E511-80D3-3863BB347BA8%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E", 3).then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }
        console.log("Next page link: " + result.nextLink);
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

Gibt die nächste Seite des Resultsets zurück:

```
{@odata.etag: "W/"1035542"", name: "Blue Yonder Airlines", accountid: "aca19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5597:4 
{@odata.etag: "W/"1031348"", name: "City Power & Light", accountid: "aea19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5597:4 
{@odata.etag: "W/"1035543"", name: "Coho Winery", accountid: "b0a19cdd-88df-e311-b8e5-6c3be5a8b200"}
VM5597:6 
Next page link: [Organization URI]/api/data/v9.0/accounts?$select=name&$skiptoken=%3Ccookie%20pagenumber=%223%22%20pagingcookie=%22%253ccookie%2520page%253d%25222%2522%253e%253caccountid%2520last%253d%2522%257bB0A19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520first%253d%2522%257bACA19CDD-88DF-E311-B8E5-6C3BE5A8B200%257d%2522%2520%252f%253e%253c%252fcookie%253e%22%20istracking=%22False%22%20/%3E
``` 
  
> [!IMPORTANT]
>  Der Wert der `nextLink`-Eigenschaft ist URI-codiert. Falls Sie den Wert vor dem Senden URI-codieren, verursachen die XML-Cookieinformationen in der URI einen Fehler.

### <a name="retrieve-related-entities-by-expanding-navigation-properties"></a>Abrufen verwandter Entitäten durch Erweitern der Navigationseigenschaften

Verwenden Sie die **$expand**-Systemabfrageoption in den Navigationseigenschaften, um zu steuern, welche Daten von den verbundenen Entitäten zurückgegeben werden. Im folgenden Beispiel wird gezeigt, wie der Kontakt für alle Firmendatensätze abgerufen wird. Für die in Verbindung stehenden Kontaktdatensätze rufen wir nur die `contactid` und `fullname` ab:

```JavaScript
Xrm.WebApi.retrieveMultipleRecords("account", "?$select=name&$top=3&$expand=primarycontactid($select=contactid,fullname)", 3).then(
    function success(result) {
        for (var i = 0; i < result.entities.length; i++) {
            console.log(result.entities[i]);
        }        
        // perform additional operations on retrieved records
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```


Weitere Beispiele des Abrufens von mehreren Datensätzen mit dem Internet API siehe [Abrufen von Daten mit der Web-API](../../../../common-data-service/webapi/query-data-web-api.md).

 
### <a name="related-topics"></a>Verwandte Themen

[Datenabfrage mit Web-API](../../../../common-data-service/webapi/query-data-web-api.md)

[Xrm.WebApi.retrieveRecord](retrieveRecord.md)

[Xrm.WebApi](../xrm-webapi.md)





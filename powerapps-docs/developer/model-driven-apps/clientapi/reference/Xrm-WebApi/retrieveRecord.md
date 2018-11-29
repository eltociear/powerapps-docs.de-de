---
title: retrieveRecord (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
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
# <a name="retrieverecord-client-api-reference"></a>retrieveRecord (Client-API-Referenz)



[!INCLUDE[./includes/retrieveRecord-description.md](./includes/retrieveRecord-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.WebApi.retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>Der logische Entitätsname des Datensatzes, der abgerufen werden soll. Zum Beispiel: "Konto".</td>
</tr>
<tr>
<td>ID</td>
<td>String</td>
<td>Ja</td>
<td>GUID des Entitätsdatensatzes, den Sie abrufen möchten.</td>
</tr>
<tr>
<td>Optionen</td>
<td>String</td>
<td>No</td>
<td><p>OData-Systemabfrageoptionen <b>$select</b> und <b>$expand</b>-Abfragen, um die Daten abzurufen.</p>
<ul><li>Verwenden Sie die <b>$select</b> Systemabfrageoption, um die Eigenschaften zu begrenzen, die zurückgegeben werden, indem Sie eine kommagetrennte Liste von Eigenschaftsnamen einschließen. Dies ist eine wichtige Methode für die Leistungssteigerung. Wenn Eigenschaften nicht mithilfe von <b>$select</b>angegeben wurden, werden alle Eigenschaften zurückgegeben.</li>
<li>Verwenden Sie die <b>$expand</b>-Systemabfrageoption, um zu steuern, welche Daten von den verbundenen Entitäten zurückgegeben werden. Wenn Sie nur den Namen der Navigationseigenschaft einschließen, rufen Sie alle Eigenschaften für in Verbindung stehende Datensätze ab. Sie können die Eigenschaften begrenzen, die für verknüpfte Datensätze mithilfe der <b>$select</b>-Systemabfrageoption in Klammern nach dem Namen der Navigationseigenschaft zurückgegeben werden. Verwenden Sie dieses für <i>einzelwertige</i> und <i>sammlungswertige</i> Navigationseigenschaften.</li>
</ul>
<p>Sie geben die Abfrageoptionen beginnend mit <code>?</code>an. Um mehrere Abfrageoptionen zu definieren, verwenden Sie <code>&</code>, um die Abfrageoptionen zu trennen. Beispiel:</p>
<code>?$select=name&$expand=primarycontactid($select=contactid,fullname)</code>
<p>Siehe Beispiele weiter unten in diesem Thema, um zu sehen, wie Sie den <code>options</code>-Parameter für den Abruf von Szenarios definieren können.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>No</td>
<td><p>Eine Funktion zum Aufrufen, wenn ein Datensatz abgerufen wird. Ein JSON-Objekt mit den abgerufen Eigenschaften und Werten wird an die Funktion übergeben.</p>
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

Bei Erfolg wird ein Versprechenmit einem JSON-Objekt zurückgegeben, mit den abgerufenen Attributen und den dazugehörigen Werten.

## <a name="examples"></a>Beispiele

### <a name="basic-retrieve"></a>Grundlegendes Abrufen 

Ruft den Namen und den Umsatz eines Firmendatensatz ab, mit Datensatz-ID = 5531d753-95af-e711-a94e-000d3a11e605.

```JavaScript
Xrm.WebApi.retrieveRecord("account", "a8a19cdd-88df-e311-b8e5-6c3be5a8b200", "?$select=name,revenue").then(
    function success(result) {
        console.log(`Retrieved values: Name: ${result.name}, Revenue: ${result.revenue}`);
        // perform operations on record retrieval
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

Im oben aufgeführten Beispiel enthält Folgendes auf der Konsole; Sie sehen ggf. weitere Werte abhängig von Ihren Daten:

`Retrieved values: Name: Sample Account, Revenue: 5000000`

### <a name="retrieve-related-entities-for-an-entity-instance-by-expanding-single-valued-navigation-properties"></a>Abrufen verknüpfter Entitäten für eine Entitätsinstanz durch Erweitern einwertiger Navigationseigenschaften

 Im folgenden Beispiel wird gezeigt, wie der Kontakt für einen Firmendatensatz mit datensatz-ID = a8a19cdd-88df-e311-b8e5-6c3be5a8b200 abgerufen wird. Für den in Verbindung stehenden Kontaktdatensatz rufen wir nur die Eigenschaften **contactid** und **fullname** ab.

```JavaScript
Xrm.WebApi.retrieveRecord("account", "a8a19cdd-88df-e311-b8e5-6c3be5a8b200", "?$select=name&$expand=primarycontactid($select=contactid,fullname)").then(
    function success(result) {
        console.log(`Retrieved values: Name: ${result.name}, Primary Contact ID: ${result.primarycontactid.contactid}, Primary Contact Name: ${result.primarycontactid.fullname}`);
        // perform operations on record retrieval
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

Im oben aufgeführten Beispiel enthält Folgendes auf der Konsole; Sie sehen ggf. weitere Werte abhängig von Ihren Daten:

`Retrieved values: Name: Adventure Works, Primary Contact ID: 49a0e5b9-88df-e311-b8e5-6c3be5a8b200, Primary Contact Name: Adrian Dumitrascu`

 
### <a name="related-topics"></a>Verwandte Themen

[Xrm.WebApi.retrieveMultipleRecords](retrieveMultipleRecords.md)

[Xrm.WebApi](../xrm-webapi.md)





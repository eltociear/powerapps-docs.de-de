---
title: createRecord (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 848c277b-bd44-4388-852a-0f59a3a15538
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="createrecord-client-api-reference"></a>createRecord (Client-API-Referenz)



[!INCLUDE[./includes/createRecord-description.md](./includes/createRecord-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.WebApi.createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

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
<td>Der logische Name der zu erstellenden Entität Zum Beispiel: "Konto".</td>
</tr>
<tr>
<td>-Daten</td>
<td>Objekt</td>
<td>Ja</td>
<td><p>Ein JSON-Objekt, das die Attribute und die Werte für den neuen Entitätsdatensatz definiert.</p>
<p>Siehe Beispiele weiter unten in diesem Thema, um zu sehen, wie Sie das <code>data</code>-Objekt für verschiedene Erstellungsszenarios definieren können.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>No</td>
<td><p>Eine Funktion zum Aufrufen, wenn ein Datensatz erstellt wird. Ein Objekt mit den folgenden Eigenschaften wird übergeben, um den neuen Datensatz zu ermitteln:</p>
<ul>
<li><b>entityType</b>: Zeichenfolge. Der logische Name des neuen Datensatzes.</li>
<li><b>id</b>: Zeichenfolge. GUID des neuen Datensatzes.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>Funktion</td>
<td>No</td>
<td>Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug. Es wird ein Objekt mit den folgenden Eigenschaften übergeben:
<ul>
<li><b>ErrorCode</b>: Zahl. Der Fehlercode.</li>
<li><b>Nachricht</b>: Zeichenfolge. Eine Fehlermeldung, die das Problem beschreibt.</li>
</ul></td>
</tr>
</table>

## <a name="return-value"></a>Rückgabewert

Bei Erfolg wird ein Versprechenobjekt mit den Attributen zurückgegeben, die zuvor in der Beschreibung des **successCallback**-Parameters angegeben wurden.

## <a name="examples"></a>Beispiele

Die Beispiele verwenden dieselben Anforderungsobjekte wie veranschaulicht in [Erstellen einer Entität mit der Web-API](../../../../common-data-service/webapi/create-entity-web-api.md), um das Datenobjekt zum Erstellen eines Entitätsdatensatzes zu definieren.

### <a name="basic-create"></a>Grundlegende Erstellung 

Einen Firmendatensatz erstellen.

```JavaScript
// define the data to create new account
var data =
    {
        "name": "Sample Account",
        "creditonhold": false,
        "address1_latitude": 47.639583,
        "description": "This is the description of the sample account",
        "revenue": 5000000,
        "accountcategorycode": 1
    }

// create account record
Xrm.WebApi.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="create-related-entity-records-along-with-the-primary-record"></a>Erstellen Sie verknüpfte Entitätsdatensätze zusammen mit dem primären Datensatz

 Sie können die Entitäten, die miteinander verknüpft werden, indem Sie sie als Navigationseigenschaftenwerte definieren. Dies ist bekannt als *tiefe Einfügung*. In diesem Beispiel wird ein Beispielfirmendatensatz erstellt zusammen mit dem Datensatz des primären Kontakts und einem zugeordneten Verkaufschancendatensatz.

```JavaScript
// define data to create primary and related entity records
var data =
    {
        "name": "Sample Account",
        "primarycontactid":
        {
            "firstname": "John",
            "lastname": "Smith"
        },
        "opportunity_customer_accounts":
        [
            {
                "name": "Opportunity associated to Sample Account",
                "Opportunity_Tasks":
                [
                    { "subject": "Task associated to opportunity" }
                ]
            }
        ]
    }

// create account record
Xrm.WebApi.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="associate-entities-on-creating-new-records"></a>Zuordnen von Entitäten beim Erstellen neuer Datensätze

Um neue Entitätsdatensätze vorhandenen Entitätsdatensätzen zuzuordnen, müssen Sie den Wert für Einzelwert-Navigationseigenschaften über die `@odata.bind`-Notation festlegen. Für mobile Clients im Offlinemodus können Sie die `@odata.bind`Notiz nicht verwenden und müssen stattdessen das Objekt **Suche** (**logicalname** und **ID**) zum entsprechenden Zieldatensatz übermitteln. Im Anschluss finden Sie Codebeispiele für beide Szenarien: 


**Für Online-Szenario (Verbindung mit Server)**

Im folgenden Beispiel wird ein Firmendatensatz erstellt und in einen vorhandenen Kontaktdatensatz eingeordnet, um den letzteren als primären Kontakt für den neuen Firmendatensatz festzulegen:

```JavaScript
var data =
    {
        "name": "Sample Account",
        "primarycontactid@odata.bind": "/contacts(465b158c-541c-e511-80d3-3863bb347ba8)"
    }

// create account record
Xrm.WebApi.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

**Für mobiles offine Szenario**

Hier der aktualisierte Beispielcode, um einen Firmendatensatzes zu aktualisieren, der mit einem weiteren Kontaktdatensatz als primären Kontakt für die Firma in der mobilen Clients verknüpft ist, während Sie im Offlinemodus arbeiten:

```JavaScript
var data =
    {
        "name": "Sample Account",
        "primarycontactid":
        {
            "logicalname": "contact",
            "id": "465b158c-541c-e511-80d3-3863bb347ba8"
        } 
    }

// create account record
Xrm.WebApi.offline.createRecord("account", data).then(
    function success(result) {
        console.log("Account created with ID: " + result.id);
        // perform operations on record creation
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
``` 
 
### <a name="related-topics"></a>Verwandte Themen

[Erstellen einer Entität mithilfe des Web-API](../../../../common-data-service/webapi/create-entity-web-api.md) 

[Xrm.WebApi](../xrm-webapi.md)
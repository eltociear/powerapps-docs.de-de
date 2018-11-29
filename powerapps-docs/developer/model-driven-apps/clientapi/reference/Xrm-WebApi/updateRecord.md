---
title: updateRecord (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f5d4c8a9-4188-472a-83bf-b986dd135754
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="updaterecord-client-api-reference"></a>updateRecord (Client-API-Referenz)



[!INCLUDE[./includes/updateRecord-description.md](./includes/updateRecord-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.WebApi.updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>Der logische Entitätsname des Datensatzes, der aktualisiert werden soll. Zum Beispiel: "Konto".</td>
</tr>
<tr>
<td>ID</td>
<td>String</td>
<td>Ja</td>
<td>GUID des Entitätsdatensatzes, den Sie aktualisieren möchten.</td>
</tr>
<tr>
<td>-Daten</td>
<td>Objekt</td>
<td>Ja</td>
<td><p>Ein JSON-Objekt, das <code>key: value</code>-Paare enthält, bei denen `key` die Eigenschaft der Entität und <code>value</code> der Wert der Eigenschaft ist, die Sie aktualisieren möchten.</p>
<p>Siehe Beispiele weiter unten in diesem Thema, um zu sehen, wie Sie das <code>data</code>-Objekt für verschiedene Aktualisierungsszenarios definieren können.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>No</td>
<td><p>Eine Funktion zum Aufrufen, wenn ein Datensatz aktualisiert wird. Ein Objekt mit den folgenden Eigenschaften wird übergeben, um den aktualisierten Datensatz zu ermitteln:</p>
<ul>
<li><b>entityType</b>: Zeichenfolge. Der Entitätsyp des aktualisierten Datensatzes.</li>
<li><b>id</b>: Zeichenfolge. Die GUID des aktualisierten Datensatzes.</li>
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

Die Beispiele verwenden einige derselben Anforderungsobjekte wie veranschaulicht in [Aktualisieren und Löschen von Entitäten mit der Web-API](../../../../common-data-service/webapi/update-delete-entities-using-web-api.md), um das Datenobjekt zum Aktualisieren eines Entitätsdatensatzes zu definieren.

### <a name="basic-update"></a>Grundlegende Aktualisierung 

Aktulaisiert einen vorhanden Firmendatensatz mit Datensatz-ID = 5531d753-95af-e711-a94e-000d3a11e605.

```JavaScript
// define the data to update a record
var data =
    {
        "name": "Updated Sample Account ",
        "creditonhold": true,
        "address1_latitude": 47.639583,
        "description": "This is the updated description of the sample account",
        "revenue": 6000000,
        "accountcategorycode": 2
    }
// update the record
Xrm.WebApi.updateRecord("account", "5531d753-95af-e711-a94e-000d3a11e605", data).then(
    function success(result) {
        console.log("Account updated");
        // perform operations on record update
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

### <a name="update-associations-to-the-related-entities"></a>Aktualisieren von Zuordnungen zu verknüpften Entitäten

Um die Zuordnung zu den verbundenen Entitätsdatensätzen zu aktulaisieren (Suchen), müssen Sie den Wert für Einzelwert-Navigationseigenschaften über die `@odata.bind`-Notation auf einen anderen Datensatz festlegen. Für mobile Clients im Offlinemodus können Sie die `@odata.bind`Notiz nicht verwenden und müssen stattdessen das Objekt **Suche** (**logicalname** und **ID**) zum entsprechenden Zieldatensatz übermitteln. Im Anschluss finden Sie Codebeispiele für beide Szenarien:

**Für Online-Szenario (Verbindung mit Server)**

Im folgenden Beispiel wird ein Firmendatensatz aktualisiert und einem anderen Kontaktdatensatz als primärer Kontakt für die Firma zugeordnet:

```JavaScript
// define the data to update a record
var data =
    {
        "primarycontactid@odata.bind": "/contacts(61a0e5b9-88df-e311-b8e5-6c3be5a8b200)"
    }
// update the record
Xrm.WebApi.updateRecord("account", "5531d753-95af-e711-a94e-000d3a11e605", data).then(
    function success(result) {
        console.log("Account updated");
        // perform operations on record update
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
// define the data to update a record
var data =
    {
        "primarycontactid":
        {
            "logicalname": "contact",
            "id": "61a0e5b9-88df-e311-b8e5-6c3be5a8b200"
        }
    }
// update the record
Xrm.WebApi.offline.updateRecord("account", "5531d753-95af-e711-a94e-000d3a11e605", data).then(
    function success(result) {
        console.log("Account updated");
        // perform operations on record update
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```
 
### <a name="related-topics"></a>Verwandte Themen

[Xrm.WebApi](../xrm-webapi.md)
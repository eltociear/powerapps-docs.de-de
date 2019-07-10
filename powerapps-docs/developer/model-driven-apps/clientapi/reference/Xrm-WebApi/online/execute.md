---
title: Xrm.WebApi.online.execute (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 11/21/2018
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
# <a name="xrmwebapionlineexecute-client-api-reference"></a>Xrm.WebApi.online.execute (Client API reference)



[!INCLUDE[./includes/execute-description.md](./includes/execute-description.md)]

> [!NOTE]
> Diese Methode wird nur für den online-Modus unterstützt ([Xrm.WebApi.online](online.md)).

## <a name="syntax"></a>Syntax

`Xrm.WebApi.online.execute(request).then(successCallback, errorCallback);`

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>Anfrage</td>
<td>Objekt</td>
<td>Ja</td>
<td><p>Objekt, das an die Internet API-Endpunkt übergeben wird, um eine Aktion, eine Funktion oder eine CRUD Anforderung auszuführen. Das Objekt exponiert eine <b>getMetadata</b>-Methode, mit der Sie Metadaten für die Aktion, Funktion oder CRUD-Anforderung definieren können, die Sie ausführen möchten. Die <b>getMetadata</b>-Methode hat die folgenden Parameter:</p>
<ul>
<li><b>boundParameter</b>: (Optional) Zeichenfolge. Der Name des gebundenen Parameters für die auszuführende Aktion oder Funktion.
<ul><li>Geben Sie <code>undefined</code> an, wenn Sie eine CRUD Anforderung ausführen.</li>
<li>Geben Sie <code>null</code> an, wenn die auszuführende Aktion oder die Funktionen an eine dieser Entität gebunden ist.</li>
<li>Geben Sie <code>entity</code> an, wenn die auszuführende Aktion oder die Funktionen an eine dieser Entität gebunden ist. </li></ul>
<li><b>operationName</b>: (Optional). Zeichenfolge. Name der Aktion, Funktion oder einer der folgenden Werte, wenn Sie eine CRUD Anforderung ausführen: "Erstellen ", "Anpassen ", "RetrieveMultiple ", "Aktualisieren "oder "Löschen".</li>
<li><b>operationType</b>: (Optional). Nummer. Gibt den Typ des Vorgangs an, den Sie ausführen; geben Sie einen der folgenden Werte an:
<br/><code>0: Action</code>
<br/><code>1: Function</code>
<br/><code>2: CRUD</code></li>
<li><b>parameterTypes</b>: Objekt. Metadaten für Parametertypen. Das Objekt hat die folgenden Attribute:
<ul>
<li><b>enumProperties</b>: (Optional) Objekt. Metadaten für enum-Typen. Das Ziel hat zwei Zeichenfolgenattribute: <b>Name</b> und <b>Wert</b></li>
<li><b>structuralProperty</b>: Zahl. Die Kategorie des Parametertyps. Geben Sie einen der folgenden Werte an:
<br/><code>0: Unknown</code>
<br/><code>1: PrimitiveType</code>
<br/><code>2: ComplexType</code>
<br/><code>3: EnumerationType</code>
<br/><code>4: Collection</code>
<br/><code>5: EntityType</code></li>
<li><b>typeName</b>: Zeichenfolge. Vollqualifizierter Name des Typs des Parameters.
</ul>
</li>
</ul>
</td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>No</td>
<td><p>Eine Funktion zum Aufrufen, wenn der Vorgang erfolgreich ausgeführt wird. Ein Antwortobjekt mit folgenden Attributen wird an die Funktion übergeben:</p>
<ul>
<li><b>Text</b>: (Optional). Objekt. Antworttext.</li>
<li><b>Kopfzeilen</b>: Objekt. Antwortheader.</li>
<li><b>ok</b>: Boolesch. Gibt an, dass die Anforderung erfolgreich war.</li>
<li><b>status</b>: Zahl. Numerischer Wert im Antwortstatuscode. Beispiel: <b>200</b></li>
<li><b>statusText</b>: Zeichenfolge. Beschreibung des Antwortstatuscodes. Beispiel: <b>OK</b>.</li>
<li><b>Typ:</b>: Zeichenfolge. Antworttyp. Werte sind: die leere Zeichenfolge (Standard), "arraybuffer", "Blob", "Dokument", "json" und "Text".</b></li>
<li><b>URL</b>: Zeichenfolge. Anforderungs-URL der Aktion, Funktion oder CRUD-Anfrage, die an den Internet API-Endpunkt gesendet wurde.</b></li>
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

Bei Erfolg wird ein Versprechenobjekt mit den Attributen zurückgegeben, die zuvor in der Beschreibung der **successCallback**-Funktion angegeben wurden.

## <a name="examples"></a>Beispiele

### <a name="execute-an-action"></a>Ausführen einer Aktion

Im folgenden Beispiel wird gezeigt, wie diese die <xref:Microsoft.Dynamics.CRM.WinOpportunity>-Aktion ausgeführt wird. Das Anforderungsobjekt wird anhand der Aktionsdefinition hier erstellt: [Ungebundene Aktionen](../../../../common-data-service/webapi/use-web-api-actions.md#unbound-actions)
```JavaScript
var Sdk = window.Sdk || {};
/**
 * Request to win an opportunity
 * @param {Object} opportunityClose - The opportunity close activity associated with this state change.
 * @param {number} status - Status of the opportunity.
 */
Sdk.WinOpportunityRequest = function (opportunityClose, status) {
    this.OpportunityClose = opportunityClose;
    this.Status = status;

    this.getMetadata = function () {
        return {
            boundParameter: null,
            parameterTypes: {
                "OpportunityClose": {
                    "typeName": "mscrm.opportunityclose",
                    "structuralProperty": 5 // Entity Type
                },
                "Status": {
                    "typeName": "Edm.Int32",
                    "structuralProperty": 1 // Primitive Type
                }
            },
            operationType: 0, // This is an action. Use '1' for functions and '2' for CRUD
            operationName: "WinOpportunity",
        };
    };
};


var opportunityClose = {
    "opportunityid@odata.bind": "/opportunities(c60e0283-5bf2-e311-945f-6c3be5a8dd64)",
    "description": "Product and maintainance for 2018",
    "subject": "Contract for 2018"
}

// Construct a request object from the metadata
var winOpportunityRequest = new Sdk.WinOpportunityRequest(opportunityClose, 3);

// Use the request object to execute the function
Xrm.WebApi.online.execute(winOpportunityRequest).then(
    function (result) {
        if (result.ok) {
            console.log("Status: %s %s", result.status, result.statusText);
            // perform other operations as required;
        }
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```


### <a name="execute-a-function"></a>Führen Sie eine Funktion aus

Im folgenden Beispiel wird gezeigt, wie diese die <xref:Microsoft.Dynamics.CRM.WhoAmI>-Funtion ausgeführt wird:

```JavaScript
var Sdk = window.Sdk || {};
/**
 * Request to execute WhoAmI function
 */
Sdk.WhoAmIRequest = function () { };
Sdk.WhoAmIRequest.prototype.getMetadata = function () {
    return {
        boundParameter: null,
        parameterTypes: {},
        operationType: 1, // This is a function. Use '0' for actions and '2' for CRUD
        operationName: "WhoAmI",
    };
};

// Construct a request object from the metadata
var whoAmIRequest = new Sdk.WhoAmIRequest();

// Use the request object to execute the function
Xrm.WebApi.online.execute(whoAmIRequest).then(
    function (result) {
        if (result.ok) {
            console.log("Status: %s %s", result.status, result.statusText);
            result.json().then(
                function (response) {
                    console.log("User Id: %s", response.UserId);
                    // perform other operations as required;
                });
        }
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```

 
### <a name="related-topics"></a>Verwandte Themen


[Xrm.WebApi](../xrm-webapi.md)





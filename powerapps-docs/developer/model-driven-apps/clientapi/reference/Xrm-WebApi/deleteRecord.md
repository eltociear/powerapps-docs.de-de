---
title: deleteRecord (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="deleterecord-client-api-reference"></a>deleteRecord (Client-API-Referenz)



[!INCLUDE[./includes/deleteRecord-description.md](./includes/deleteRecord-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.WebApi.deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

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
<td>Der logische Entitätsname des Datensatzes, der gelöscht werden soll. Zum Beispiel: "Konto". </td>
</tr>
<tr>
<td>ID</td>
<td>String</td>
<td>Ja</td>
<td>GUID des Entitätsdatensatzes, den Sie löschen möchten.</td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>No</td>
<td><p>Eine Funktion zum Aufrufen, wenn ein Datensatz gelöscht wird. Ein Objekt mit den folgenden Eigenschaften wird übergeben, um den gelöschten Datensatz zu ermitteln:</p>
<ul>
<li><b>entityType</b>: Zeichenfolge. Der Entitätsyp des Datensatzes</li>
<li><b>id</b>: Zeichenfolge. GUID des Datensatzes.</li>
<li><b>name</b>: Zeichenfolge. Name des Datensatzes.</li>
</ul></td>
</tr>
<tr>
<td>errorCallback</td>
<td>Funktion</td>
<td>No</td>
<td>Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug.</td>
</tr>
</table>

## <a name="return-value"></a>Rückgabewert

Bei Erfolg wird ein Versprechenobjekt mit den Attributen zurückgegeben, die zuvor in der Beschreibung des **successCallback**-Parameters angegeben wurden.

## <a name="examples"></a>Beispiele

Die Beispiele verwenden einige derselben Anforderungsobjekte wie veranschaulicht in [Aktualisieren und Löschen von Entitäten mit der Web-API](../../../../common-data-service/webapi/update-delete-entities-using-web-api.md), um das Datenobjekt zum Aktualisieren eines Entitätsdatensatzes zu definieren.

Löscht eine Firma mit Datensatz-ID = 5531d753-95af-e711-a94e-000d3a11e605.

```JavaScript
Xrm.WebApi.deleteRecord("account", "5531d753-95af-e711-a94e-000d3a11e605").then(
    function success(result) {
        console.log("Account deleted");
        // perform operations on record deletion
    },
    function (error) {
        console.log(error.message);
        // handle error conditions
    }
);
```
 
### <a name="related-topics"></a>Verwandte Themen

[Xrm.WebApi](../xrm-webapi.md)





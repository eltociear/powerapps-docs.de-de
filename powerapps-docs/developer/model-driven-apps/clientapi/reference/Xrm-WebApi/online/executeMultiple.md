---
title: Xrm.WebApi.online.executeMultiple (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: reference
ms.assetid: d4e92999-3b79-4783-8cac-f656fc5f7fda
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="xrmwebapionlineexecutemultiple-client-api-reference"></a>Xrm.WebApi.online.executeMultiple (Client API reference)

[!INCLUDE[./includes/executeMultiple-description.md](./includes/executeMultiple-description.md)]

> [!NOTE]
> Diese Methode wird nur für den online-Modus unterstützt ([Xrm.WebApi.online](../online.md)). 

Wenn Sie mehrere Anforderungen in der Transaktion ausführen möchten, müssen Sie in ein Changeset als Parameter übergeben an diese Methode. [Changesets](../../../../../common-data-service/webapi/execute-batch-operations-using-web-api.md#change-sets) sind eine Sammlung Vorgängen, die innerhalb derselben Transaktion ausgeführt werden. Sie können auch einzelne Anforderungen und Changesets zusammen als Parameter an diese Methode übergeben.

> [!NOTE]
> Sie können keine Lesevorgänge einschließen (abrufen, mehrere abrufen und Internet-API-Funktionen) als Bestandteil eines Changesets; dies ist gemäß den ODatas v4-Spezifikation.

## <a name="syntax"></a>Syntax

**Ausführen mehrerer Anforderungen:**

```JavaScript
var requests = [req1, req2, req3];
Xrm.WebApi.online.executeMultiple(requests).then(successCallback, errorCallback);
```

**Mehrere Anforderungen in einer Transaktion ausführen:**

In diesem Fall werdern `req1`, `req2` und `req3` in der Transaktion ausgeführt.

```JavaScript
var changeSet = [req1, req2, req3];
var requests = [changeSet];
Xrm.WebApi.online.executeMultiple(requests).then(successCallback, errorCallback);
```


**Ausführen einer Mischung aus einzelnen Anforderungen und mehreren Anforderungen in der Transaktion:**

In diesem Fall wird `req1`, `req2` und `req3` in der Transaktion ausgeführt, aber `req4` und `req5` werden individuell ausgeführt.

```JavaScript
var changeSet = [req1, req2, req3];
var requests = [req4, req5, changeset];
Xrm.WebApi.online.executeMultiple(requests).then(successCallback, errorCallback);
```

## <a name="parameters"></a>Parameter

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>requests</td>
<td>Array von Objekten</td>
<td>Ja</td>
<td><p>Ein Array von einem von einem der folgenden Typen:</p>
<ul>
<li>Objekte, wobei jedes Objekt eine Aktion, Funktion oder CRUD Anforderung ist, die Sie mit dem Internet API-Endpunkt ausführen möchten. Jedes Objekt exponiert eine <b>getMetadata</b>-Methode, mit der Sie Metadaten für die Aktion, Funktion oder CRUD-Anforderung definieren können, die Sie ausführen möchten. Dies ist dasselbe Objekt, das Sie in der <code>execute</code>-Methode ausführen. Informationen zum Objekt, siehe <a href="execute.md">execute</a>.</li>
<li>Changeset (ein Objektarray), wobei jedes Objekt in Changeset wie oben definiert ist. In diesem Fall werden alle Anforderungsobjekte, die im Changeset angegeben wurden, in einer Transaktion ausgeführt.</li>
</ul>
<p>Weitere Informationen finden Sie in der **Syntax** oben.</p>
</td>
</tr>
<tr>
<td>successCallback</td>
<td>Funktion</td>
<td>No</td>
<td><p>Eine Funktion zum Aufrufen, wenn der Vorgang erfolgreich ausgeführt wird. Ein Array von Antwortobjekte wird an die Funktion übergeben, wobei jedes Antwortobjekt die folgenden Attribute aufweist:</p>
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

Bei Erfolg wird ein Versprechen mit einem Array von Objekten zurückgegeben, die zuvor in der Beschreibung der **successCallback**-Funktion angegeben wurden.

### <a name="related-topics"></a>Verwandte Themen

[Xrm.WebApi](../../xrm-webapi.md)


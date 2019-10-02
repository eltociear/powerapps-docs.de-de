---
title: updateRecord | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 179ced61-ff0f-45ef-aa14-835ce99532cf
---

# <a name="updaterecord"></a>updateRecord

[!INCLUDE [updaterecord-description](includes/updaterecord-description.md)]

## <a name="syntax"></a>Syntax

`updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>Der logische Entitätsname des Datensatzes, der aktualisiert werden soll. Zum Beispiel: &quot;Firma&quot;.</td>
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
<td><p>Ein JSON-Objekt, das <code>key: value</code>-Paare enthält, bei denen <code>key</code> die Eigenschaft der Entität und <code>value</code> der Wert der Eigenschaft ist, die Sie aktualisieren möchten.</p>
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


### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
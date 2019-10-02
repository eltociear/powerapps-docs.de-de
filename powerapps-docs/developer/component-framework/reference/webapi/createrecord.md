---
title: createRecord | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 9179f03b-9d26-4253-9535-13ab544d58ac
---

# <a name="createrecord"></a>createRecord

[!INCLUDE [createrecord-description](includes/createrecord-description.md)]

## <a name="syntax"></a>Syntax

`createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

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
<td>Der logische Name der zu erstellenden Entität Zum Beispiel: &quot;Firma&quot;.</td>
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

### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
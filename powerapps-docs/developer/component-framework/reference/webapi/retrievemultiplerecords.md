---
title: retrieveMultipleRecords | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 824a53f9-c743-435a-9de2-8128846f3191
---

# <a name="retrievemultiplerecords"></a>retrieveMultipleRecords

[!INCLUDE [retrievemultiplerecords-description](includes/retrievemultiplerecords-description.md)]

## <a name="syntax"></a>Syntax

`retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

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
<td>Der logische Entitätsname der Datensätze, die abgerufen werden sollen. Zum Beispiel: &quot;Firma&quot;.</td>
</tr>
<tr>
<td>Optionen</td>
<td>String</td>
<td>Nr.</td>
<td><p>OData-Systemabfrageoptionen oder FetchXML-Abfragen, um die Daten abzurufen. </p> 
<ul>
<li>Für Systemabfrageoptionen werden unterstützt: <b>$select</b>, <b>$top</b>, <b>$filter</b>, <b>$expand</b> und <b>$orderby</b>.</li>
<li>Um eine FetchXML-Abfrage anzugeben, verwenden Sie das <code>fetchXml</code>-Attribut für die Angabe der Abfrage:</li>
</ul>
<p>HINWEIS: Sie müssen immer <b>$select</b>-Systemabfrageoption verwenden, um Eigenschaften zu begrenzen, die nach einem Entitätsdatensatz zurückgegeben werden, durch Einschließen einer durch Trennzeichen getrennten Liste mit Eigenschaftennamen. Dies ist eine wichtige Methode für die Leistungssteigerung. Wenn Eigenschaften nicht mithilfe von <b>$select</b>angegeben wurden, werden alle Eigenschaften zurückgegeben.</li>
<p>Sie geben die Abfrageoptionen beginnend mit <code>?</code>an. Sie können auch mehrere Systemabfrageoptionen festlegen, indem Sie <code>&amp;</code> zum Trennen der Abfrageoptionen verwenden.
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
<td>Nein</td>
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


### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
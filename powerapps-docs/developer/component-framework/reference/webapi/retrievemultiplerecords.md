---
title: Retrievemultiplerecords | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 824a53f9-c743-435a-9de2-8128846f3191
ms.openlocfilehash: d708596e9b8e12ead8f84d31d3b35fb5b27843f8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340803"
---
# <a name="retrievemultiplerecords"></a>retrieveMultipleRecords

[!INCLUDE [retrievemultiplerecords-description](includes/retrievemultiplerecords-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.webAPI.retrieveMultipleRecords(entityLogicalName, options, maxPageSize).then(successCallback, errorCallback);`

## <a name="parameters"></a>Metern

<table style="width:100%">
<tr>
<th>Name</th>
<th>Typ</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
<tr>
<td>entitylogicalname</td>
<td>Zeichenfolge</td>
<td>Ja</td>
<td>Der logische Name der Entität der Datensätze, die Sie abrufen möchten. Beispiel: &quot;account &quot;.</td>
</tr>
<tr>
<td>Optionen</td>
<td>Zeichenfolge</td>
<td>Nein</td>
<td><p>Odata-System Abfrage Optionen oder fetchxml-Abfrage zum Abrufen der Daten. </p> 
<ul>
<li>Folgende System Abfrage Optionen werden unterstützt: <b>$Select</b>, <b>$Top</b>, <b>$Filter</b>, <b>$Expand</b>und <b>$OrderBy</b>.</li>
<li>Um eine fetchxml-Abfrage anzugeben, verwenden Sie das <code>fetchXml</code>-Attribut, um die Abfrage anzugeben.</li>
</ul>
<p>Hinweis: Sie müssen stets die <b>$Select</b> System-Abfrage Option verwenden, um die für einen Entitäts Daten Satz zurückgegebenen Eigenschaften einzuschränken, indem Sie eine durch Trennzeichen getrennte Liste von Eigenschaftsnamen einschließen. Dies ist eine wichtige bewährte Vorgehensweise für die Leistung. Wenn Eigenschaften nicht mit <b>$Select</b>angegeben werden, werden alle Eigenschaften zurückgegeben.</li>
<p>Sie geben die Abfrage Optionen an, die mit <code>?</code> beginnen. Sie können auch mehrere System Abfrage Optionen angeben, indem Sie <code>&amp;</code> verwenden, um die Abfrage Optionen voneinander zu trennen.
<p>Siehe Beispiele weiter unten in diesem Thema, um zu erfahren, wie Sie den <code>options</code>-Parameter für verschiedene Szenarios zum Abrufen mehrerer Szenarien definieren können.</td>
</tr>
<tr>
<td>MaxPageSize</td>
<td>Number</td>
<td>Nein</td>
<td><p>Geben Sie eine positive Zahl an, die die Anzahl der Entitäts Datensätze angibt, die pro Seite zurückgegeben werden. Wenn Sie diesen Parameter nicht angeben, wird der Standardwert als 5000 übergeben.</p>
<p>Wenn die Anzahl der abgerufenen Datensätze über dem angegebenen <code>maxPageSize</code> Wert liegt, enthält <code>nextLink</code> Attribut im zurückgegebenen Promise-Objekt einen Link zum Abrufen der nächsten Entitätenmenge. </td>
</tr>
<tr>
<td>erfolgreich</td>
<td>Funktion</td>
<td>Nein</td>
<td><p>Eine Funktion, die aufgerufen wird, wenn Entitäts Datensätze abgerufen werden. Ein-Objekt mit den folgenden Attributen wird an die-Funktion übermittelt:</p>
<ul>
<li><b>Entities</b>: ein Array von JSON-Objekten, wobei jedes-Objekt den abgerufenen Entitäts Daten Satz darstellt, der Attribute und deren Werte als <code>key: value</code> Paare enthält. Standardmäßig wird die ID des Entitäts Datensatzes abgerufen.</li>
<li><b>Nextlink</b>: Zeichenfolge. Wenn die Anzahl der abgerufenen Datensätze größer ist als der Wert, der im <code>maxPageSize</code>-Parameter in der Anforderung angegeben ist, gibt dieses Attribut die URL zurück, um die nächste Gruppe von Datensätzen zurückzugeben.</li>
</ul>
</td>
</tr>
<tr>
<td>errorcallback</td>
<td>Funktion</td>
<td>Nein</td>
<td>Eine Funktion, die aufgerufen werden soll, wenn der Vorgang fehlschlägt.</td>
</tr>
</table>

## <a name="return-value"></a>Rückgabewert

Typ: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) -<RetrieveMultipleResponse>

Beschreibung: der `RetrieveMultipleResponse` gibt eine Zusage zurück, die ein Array von JSON-Objekten enthält, die die abgerufenen Entitäts Datensätze enthalten, und das **Nextlink** -Attribut mit der URL, die auf den nächsten Datensatz verweist, wenn Paging (`maxPageSize`) in der Anforderung angegeben wird, und das die zurückgegebene Daten Satz Anzahl überschreitet den Auslagerungs Wert. Es verfügt über die folgenden Parameter:

|Parame|Rückgabewert|Beschreibung|
|----|------|-------|
|Kleinstunternehmen|`Entity[]`|Ein Array von JSON-Objekten, wobei jedes-Objekt den abgerufenen Entitäts Daten Satz mit Attributen und deren Werten darstellt.|
|nextLink|`string`|Wenn die Anzahl der abgerufenen Datensätze größer ist als der Wert, der im Parameter "MaxPageSize" in der Anforderung angegeben ist, gibt dieses Attribut die URL zurück, um die nächste Gruppe von Datensätzen zurückzugeben.|


### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
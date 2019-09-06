---
title: RetrieveRecord | Microsoft Docs
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
ms.assetid: dddeecc9-5067-420d-8bd7-4c914218e969
---

# <a name="retrieverecord"></a>retrieveRecord

[!INCLUDE [retrieverecord-description](includes/retrieverecord-description.md)]

## <a name="syntax"></a>Syntax

`retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>Der logische Entitätsname des Datensatzes, der abgerufen werden soll. Zum Beispiel: &quot;Firma&quot;.</td>
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
<p>Sie geben die Abfrageoptionen beginnend mit <code>?</code>an. Um mehrere Abfrageoptionen zu definieren, verwenden Sie <code>&amp;</code>, um die Abfrageoptionen zu trennen. Beispiel:</p>
<code>?$select=name&amp;$expand=primarycontactid($select=contactid,fullname)</code>
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


### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
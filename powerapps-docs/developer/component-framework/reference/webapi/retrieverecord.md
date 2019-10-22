---
title: Abrufen | Microsoft-Dokumentation
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
ms.assetid: dddeecc9-5067-420d-8bd7-4c914218e969
ms.openlocfilehash: 9c77bf9975bd1f1f115df9385061c008975cc184
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341700"
---
# <a name="retrieverecord"></a>retrieveRecord

[!INCLUDE [retrieverecord-description](includes/retrieverecord-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.webAPI.retrieveRecord(entityLogicalName, id, options).then(successCallback, errorCallback);`

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
<td>Der logische Name der Entität des Datensatzes, den Sie abrufen möchten. Beispiel: &quot;account &quot;.</td>
</tr>
<tr>
<td>id</td>
<td>Zeichenfolge</td>
<td>Ja</td>
<td>GUID des Entitäts Datensatzes, den Sie abrufen möchten.</td>
</tr>
<tr>
<td>Optionen</td>
<td>Zeichenfolge</td>
<td>Nein</td>
<td><p>Odata-System Abfrage Optionen, <b>$Select</b> und <b>$Expand</b>, um Ihre Daten abzurufen.</p>
<ul><li>Verwenden Sie die <b>$Select</b> -System Abfrage Option, um die zurückgegebenen Eigenschaften einzuschränken, indem Sie eine durch Trennzeichen getrennte Liste mit Eigenschaftsnamen einschließen. Dies ist eine wichtige bewährte Vorgehensweise für die Leistung. Wenn Eigenschaften nicht mit <b>$Select</b>angegeben werden, werden alle Eigenschaften zurückgegeben.</li>
<li>Verwenden Sie die Abfrage Option <b>$Expand</b> System, um zu steuern, welche Daten aus verknüpften Entitäten zurückgegeben werden. Wenn Sie nur den Namen der Navigations Eigenschaft einschließen, erhalten Sie alle Eigenschaften für verwandte Datensätze. Sie können die Eigenschaften, die für verknüpfte Datensätze zurückgegeben werden, mit der <b>$Select</b> -System Abfrage Option in Klammern nach dem Namen der Navigations Eigenschaft begrenzen. Verwenden Sie diesen Wert sowohl für <i>einwertige</i> als auch für <i>Auflistungs Wert-</i> Navigations Eigenschaften.</li>
</ul>
<p>Sie geben die Abfrage Optionen an, die mit <code>?</code> beginnen. Sie können auch mehrere Abfrage Optionen angeben, indem Sie <code>&amp;</code> verwenden, um die Abfrage Optionen voneinander zu trennen. Beispiel:</p>
<code>?$select=name&amp;$expand=primarycontactid($select=contactid,fullname)</code>
<p>Siehe Beispiele weiter unten in diesem Thema, um zu erfahren, wie Sie den <code>options</code>-Parameter für verschiedene Abruf Szenarien definieren können.</td>
</tr>
<tr>
<td>erfolgreich</td>
<td>Funktion</td>
<td>Nein</td>
<td><p>Eine Funktion, die aufgerufen werden soll, wenn ein Datensatz abgerufen wird. Ein JSON-Objekt mit den abgerufenen Eigenschaften und Werten wird an die Funktion übermittelt.</p>
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

Typ: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[Entitäts](../entity.md) >



### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
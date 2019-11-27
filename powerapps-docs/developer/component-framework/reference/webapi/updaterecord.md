---
title: UpdateRecord | Microsoft-Dokumentation
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
ms.assetid: 179ced61-ff0f-45ef-aa14-835ce99532cf
ms.openlocfilehash: 96037bcd8ca43448e928abef714ae031222d8e98
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340688"
---
# <a name="updaterecord"></a>updateRecord

[!INCLUDE [updaterecord-description](includes/updaterecord-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.webAPI.updateRecord(entityLogicalName, id, data).then(successCallback, errorCallback);`

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
<td>Der logische Name der Entität des Datensatzes, den Sie aktualisieren möchten. Beispiel: &quot;account &quot;.</td>
</tr>
<tr>
<td>id</td>
<td>Zeichenfolge</td>
<td>Ja</td>
<td>GUID des Entitäts Datensatzes, den Sie aktualisieren möchten.</td>
</tr>
<tr>
<td>Vorrats</td>
<td>Objekt</td>
<td>Ja</td>
<td><p>Ein JSON-Objekt, das <code>key: value</code> Paare enthält, wobei <code>key</code> die Eigenschaft der Entität und <code>value</code> der Wert der Eigenschaft, die Sie aktualisieren möchten.</p>
<p>Siehe Beispiele weiter unten in diesem Thema, um zu erfahren, wie Sie das <code>data</code>-Objekt für verschiedene Update Szenarios definieren können.</td>
</tr>
<tr>
<td>erfolgreich</td>
<td>Funktion</td>
<td>Nein</td>
<td><p>Eine Funktion, die aufgerufen wird, wenn ein Datensatz aktualisiert wird. Ein Objekt mit den folgenden Eigenschaften wird zum Identifizieren des aktualisierten Datensatzes übermittelt:</p>
<ul>
<li><b>EntityType</b>: Zeichenfolge. Der Entitätstyp des aktualisierten Datensatzes.</li>
<li><b>ID</b>: Zeichenfolge. GUID des aktualisierten Datensatzes.</li>
</ul></td>
</tr>
<tr>
<td>errorcallback</td>
<td>Funktion</td>
<td>Nein</td>
<td>Eine Funktion, die aufgerufen werden soll, wenn der Vorgang fehlschlägt. Ein Objekt mit den folgenden Eigenschaften wird übermittelt:
<ul>
<li><b>errorCode</b>: Number. Der Fehlercode.</li>
<li><b>Message</b>: Zeichenfolge. Eine Fehlermeldung, in der das Problem beschrieben wird.</li>
</ul></td>
</tr>
</table>

## <a name="return-value"></a>Rückgabewert

Geben Sie Folgendes ein: [Promise] ((dateformattinginfo. MD) <[EntityReference](../entityreference.md) >

Beschreibung: bei Erfolg wird ein Promise-Objekt zurückgegeben, das die zuvor **in der Beschreibung des Parameters** "Success" angegebenen Attribute enthält.


### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
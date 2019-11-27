---
title: "\"Kreaterecord\" | Microsoft-Dokumentation"
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 9179f03b-9d26-4253-9535-13ab544d58ac
ms.openlocfilehash: f3a2b860f17d7efaaf8efebcf2418aef04478947
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340826"
---
# <a name="createrecord"></a>createRecord

[!INCLUDE [createrecord-description](includes/createrecord-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.webAPI.createRecord(entityLogicalName, data).then(successCallback, errorCallback);`

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
<td>Logischer Name der Entität, die Sie erstellen möchten. Beispiel: &quot;account &quot;.</td>
</tr>
<tr>
<td>Vorrats</td>
<td>Objekt</td>
<td>Ja</td>
<td><p>Ein JSON-Objekt, das die Attribute und Werte für den neuen Entitäts Daten Satz definiert.</p>
<p>Siehe Beispiele weiter unten in diesem Thema, um zu erfahren, wie Sie das <code>data</code>-Objekt für verschiedene Erstellungs Szenarien definieren können.</td>
</tr>
<tr>
<td>erfolgreich</td>
<td>Funktion</td>
<td>Nein</td>
<td><p>Eine Funktion, die aufgerufen wird, wenn ein Datensatz erstellt wird. Ein Objekt mit den folgenden Eigenschaften wird an den neuen Datensatz übermittelt:</p>
<ul>
<li><b>EntityType</b>: Zeichenfolge. Der logische Name der Entität des neuen Datensatzes.</li>
<li><b>ID</b>: Zeichenfolge. GUID des neuen Datensatzes.</li>
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

Typ: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[EntityReference](../entityreference.md) >

Beschreibung: bei Erfolg wird ein Promise-Objekt zurückgegeben, das die zuvor **in der Beschreibung des Parameters** "Success" angegebenen Attribute enthält.

### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
---
title: DeleteRecord | Microsoft-Dokumentation
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
ms.assetid: 5c9968bf-d535-425c-b1f1-0db6b7822de1
ms.openlocfilehash: f6c8dd6ea7d156e28ab3ae54d7fe37dad6c4546a
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72340757"
---
# <a name="deleterecord"></a>deleteRecord

[!INCLUDE [deleterecord-description](includes/deleterecord-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.webAPI.deleteRecord(entityLogicalName, id).then(successCallback, errorCallback);`

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
<td>Der logische Name der Entität des Datensatzes, den Sie löschen möchten. Beispiel: &quot;account &quot;. </td>
</tr>
<tr>
<td>id</td>
<td>Zeichenfolge</td>
<td>Ja</td>
<td>GUID des Entitäts Datensatzes, den Sie löschen möchten.</td>
</tr>
<tr>
<td>erfolgreich</td>
<td>Funktion</td>
<td>Nein</td>
<td><p>Eine Funktion, die aufgerufen werden soll, wenn ein Datensatz gelöscht wird. Ein Objekt mit den folgenden Eigenschaften wird an den gelöschten Datensatz übermittelt:</p>
<ul>
<li><b>EntityType</b>: Zeichenfolge. Der Entitätstyp des Datensatzes.</li>
<li><b>ID</b>: Zeichenfolge. GUID des Datensatzes.</li>
<li><b>Name</b>: Zeichenfolge. Der Name des Datensatzes.</li>
</ul></td>
</tr>
<tr>
<td>errorcallback</td>
<td>Funktion</td>
<td>Nein</td>
<td>Eine Funktion, die aufgerufen werden soll, wenn der Vorgang fehlschlägt.</td>
</tr>
</table>

## <a name="return-value"></a>Rückgabewert

Typ: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[EntityReference](../entityreference.md) >

### <a name="related-topics"></a>Verwandte Themen

[Web-API](../webapi.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
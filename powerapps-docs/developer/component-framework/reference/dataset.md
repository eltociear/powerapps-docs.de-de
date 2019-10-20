---
title: DataSet | Microsoft-Dokumentation
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
ms.assetid: 0202d51f-e9a9-4a2e-b3e9-0bfd7f6afb86
ms.openlocfilehash: 5e9408c81fc9587b9dec30f18fc68c3112ba6125
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345311"
---
# <a name="dataset"></a>DataSet

[!INCLUDE [dataset-description](includes/dataset-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="addcolumn"></a>AddColumn ()

Fügt der ColumnSet-Spalte eine Spalte hinzu.

### <a name="remarks"></a>Rede

Diese Methode akzeptiert zwei Parameter.

|Name|Typ|Erforderlich|Beschreibung|
|------|-----|------|-----|
|Benennen|`string`|Ja|Der Spaltenname, der dem DataSet hinzugefügt werden soll.|
|entityalias|`string`|Nein| Der Entitätstyp, für den der Spaltenname hinzugefügt werden muss.|

### <a name="columns"></a>Spalten

Der Satz von Spalten, der in diesem Dataset verfügbar ist.

**Type**: [Column](column.md)[]

### <a name="error"></a>Zeit

Gibt an, ob beim Datenabruf ein Fehler aufgetreten ist.

**Typ**: `boolean`

### <a name="errormessage"></a>ErrorMessage

Die Fehlermeldung, die dem letzten Fehler, sofern zutreffend, zugeordnet ist.

**Typ**: `string`

### <a name="filtering"></a>Filterung

Die Spalten Filterung für die aktuelle Abfrage.

**Typ**: [Filtern](filtering.md)

### <a name="linking"></a>Links

Definiert die Informationen zu verknüpften Entitäten.

**Typ**: [Verknüpfen](linking.md)

### <a name="loading"></a>beim

Gibt an, ob das DataSet geladen wird oder nicht.

**Typ**: `boolean`

### <a name="paging"></a>Paging

Paginierungs Status und-Aktionen.

**Typ**: [Paging](paging.md)

### <a name="records"></a>Best

Zuordnung von IDs zum vollständigen Datensatz-Objekt.

**Typ**: [entityrecord](entityrecord.md)

### <a name="sortedrecordids"></a>sortedrecordids

IDs der Datensätze im DataSet, Reihenfolge nach dem Ergebnis der Abfrage Antwort.

**Typ**: `string[]`

### <a name="sorting"></a>Maschine

Der Sortier Status für die aktuelle Abfrage.

**Typ**: [sortstatus](sortstatus.md)

## <a name="methods"></a>Anzuwenden

|Anzuwenden | Beschreibung | 
| ------------- |-------------|
|[clearselectedrecordids](dataset/clearselectedrecordids.md)|[!INCLUDE [clearselectedrecordids-description](dataset/includes/clearselectedrecordids-description.md)]| 
|[getselectedrecordids](dataset/getselectedrecordids.md)|[!INCLUDE [getselectedrecordids-description](dataset/includes/getselectedrecordids-description.md)]| 
|[gettargetentitytype](dataset/gettargetentitytype.md)|[!INCLUDE [gettargetentitytype-description](dataset/includes/gettargetentitytype-description.md)]| 
|[getTitle](dataset/gettitle.md)|[!INCLUDE [gettitle-description](dataset/includes/gettitle-description.md)]| 
|[getviewid](dataset/getviewid.md)|[!INCLUDE [getviewid-description](dataset/includes/getviewid-description.md)]| 
|[opendatasetitem](dataset/opendatasetitem.md)|[!INCLUDE [opendatasetitem-description](dataset/includes/opendatasetitem-description.md)]| 
|[erneuten](dataset/refresh.md)|[!INCLUDE [refresh-description](dataset/includes/refresh-description.md)]| 
|[setselectedrecordids](dataset/setselectedrecordids.md)|[!INCLUDE [setselectedrecordids-description](dataset/includes/setselectedrecordids-description.md)]| 

## <a name="example"></a>Beispiel

Weitere Informationen zum Implementieren der DataSet-Methoden finden Sie unter [DataSet-Raster Komponente](../sample-controls/data-set-grid-control.md) .

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
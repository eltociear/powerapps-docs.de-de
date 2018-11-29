---
title: GridRowData (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8139c622-e4d9-478f-9510-414d140e5556
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridrowdata-client-api-reference"></a>GridRowData (Client-API-Referenz)



GridRowData wird von der [GridRow](gridrow.md).[getData](gridrow/getData.md)-Methode zurückgegeben.

GridRowData stellt zudem Methoden zum Abrufen von Informationen bereit, die für den in einer bearbeitbaren Rasterzeile angezeigten Datensatz spezifisch sind, die Speichermethode und eine Sammlung aller im Formular enthaltenen Attribute. Attributdaten sind auf die Spalten begrenzt, die im bearbeitbaren Raster angezeigt werden. Soehe [Sammlungen (Client-API-Referenz)](../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.

```JavaScript
var myRows = gridContext.getGrid().getRows();
var myRow = myRows.get(arg);
var gridRowData = myRow.getData();
```

## <a name="properties"></a>Eigenschaften

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|Entität|Gibt [GridEntity](gridentity.md) für GridRowData zurück.|Bearbeitbare und schreibgeschützte Raster|


## <a name="methods"></a>Methoden

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|[getEntity](gridrowdata/getEntity.md)|[!INCLUDE[gridrowdata/includes/getEntity-description.md](gridrowdata/includes/getEntity-description.md)]|Bearbeitbare und schreibgeschützte Raster|



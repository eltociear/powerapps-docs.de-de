---
title: GridRow (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 02fef0b4-b895-4277-b604-3f525c29dca3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridrow-client-api-reference"></a>GridRow (Client-API-Referenz)



Eine Sammlung von GridRow wird zurückgegeben von [Raster](grid.md).[getRows](grid/getRows.md) und [Raster](grid.md).[getSelectedRows](grid/getSelectedRows.md)-Methoden.

```JavaScript
var myRows = gridContext.getGrid().getRows();
var gridRow = myRows.get(arg);
```

## <a name="properties"></a>Eigenschaften

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|-Daten|Ein Sammlung mit [GridRowData](gridrowdata.md) für das GridRow. Soehe [Sammlungen (Client-API-Referenz)](../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.|Bearbeitbare und schreibgeschützte Raster|


## <a name="methods"></a>Methoden

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|[getData](gridrow/getData.md)|[!INCLUDE[gridrow/includes/getData-description.md](gridrow/includes/getData-description.md)]|Bearbeitbare und schreibgeschützte Raster|

### <a name="related-topics"></a>Verwandte Themen

[GridRowData](gridrowdata.md)

[Raster und Unterraster in modellgestützten Apps](../grids.md)



---
title: Raster (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="grid-client-api-reference"></a>Raster (Client-API-Referenz)



Raster werden durch die **gridContext**.[getGrid](gridcontrol/getGrid.md)-Methode zurückgegeben. Verwenden Sie die Raster-Methoden, um auf Informationen über Daten im Raster zuzugreifen.

`var myGrid = gridContext.getGrid();`

## <a name="methods"></a>Methoden

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|[getRows](grid/getRows.md)|[!INCLUDE[grid/includes/getRows-description.md](grid/includes/getRows-description.md)]|Bearbeitbare und schreibgeschützte Raster|
|[getSelectedRows](grid/getSelectedRows.md)|[!INCLUDE[grid/includes/getSelectedRows-description.md](grid/includes/getSelectedRows-description.md)]|Bearbeitbare und schreibgeschützte Raster|
|[getTotalRecordCount](grid/getTotalRecordCount.md)|[!INCLUDE[grid/includes/getTotalRecordCount-description.md](grid/includes/getTotalRecordCount-description.md)]|Bearbeitbare und schreibgeschützte Raster|

### <a name="related-topics"></a>Verwandte Themen

[GridRow](gridrow.md)

[Raster und Unterraster in modellgestützten Apps](../grids.md)

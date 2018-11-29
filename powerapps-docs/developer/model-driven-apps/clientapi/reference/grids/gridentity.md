---
title: GridEntity (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: cc2b7eca-61f4-4949-8398-52c9fc36721c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gridentity-client-api-reference"></a>GridEntity (Client-API-Referenz)



GridEntity wird von der [GridRowData](gridrowdata.md).[getEntity](gridrowdata/getEntity.md)-Methode oder durch direkten Zugriff auf das [GridRowData](gridrowdata.md).**Entität**-Objekt zurückgegeben. Verwenden Sie die GridEntity-Methoden für den Zugriff auf Daten zu den spezifischen Datensätzen in den Zeilen.

```JavaScript
var myRows = gridContext.getGrid().getRows();
var myRow = myRows.get(arg);
var gridEntity = myRow.getData().getEntity();
```

GridEntity unterstützt außerdem die **Attribute**-Sammlung, die eine Sammlung von Arbeitsmethodiken von Attributen für eine Entität im bearbeitbaren Raster bereitstellt. Jedes Attribut ([GridAttribute](gridattribute.md)) vertritt die Daten in der Zelle eines bearbeitbaren Rasters und umfasst einen Verweis auf alle gewünschten Zellen, die dem Attribut zugeordnet werden. Soehe [Sammlungen (Client-API-Referenz)](../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.

## <a name="methods"></a>Methoden

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|[getEntityName](gridentity/getEntityName.md)|[!INCLUDE[gridentity/includes/getEntityName-description.md](gridentity/includes/getEntityName-description.md)]|Bearbeitbare und schreibgeschützte Raster|
|[getEntityReference](gridentity/getEntityReference.md)|[!INCLUDE[gridentity/includes/getEntityReference-description.md](gridentity/includes/getEntityReference-description.md)]|Bearbeitbare und schreibgeschützte Raster|
|[getId](gridentity/getId.md)|[!INCLUDE[gridentity/includes/getId-description.md](gridentity/includes/getId-description.md)]|Bearbeitbare und schreibgeschützte Raster|
|[getPrimaryAttributeValue](gridentity/getPrimaryAttributeValue.md)|[!INCLUDE[gridentity/includes/getPrimaryAttributeValue-description.md](gridentity/includes/getPrimaryAttributeValue-description.md)]|Schreibgeschütztes Raster|

### <a name="related-topics"></a>Verwandte Themen

[GridAttribute](gridattribute.md)

[Raster und Unterraster in modellgestützten Apps](../grids.md)

[Attribute](../attributes.md)



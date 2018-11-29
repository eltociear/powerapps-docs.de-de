---
title: ViewSelector-Methoden (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 37fbabaf-e2ce-4e46-a54e-e46bd884197b
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="viewselector-methods-client-api-reference"></a>ViewSelector-Methoden (Client-API-Referenz)



Stellt Methoden bereit, um Informationen zur Ansichtsauswahl des Unterrastersteuerelements abzurufen oder festzulegen. Wenn das Unterrastersteuerelement nicht so konfiguriert ist, dass die Ansichtsauswahl angezeigt wird, wird durch Aufrufen der **ViewSelector**-Methoden ein Fehler ausgelöst.

ViewSelector ist nur für schreibgeschützte Raster verfügbar. ViewSelector wird von der **gridContext**.[getGrid](gridcontrol/getViewSelector.md)-Methode zurückgegeben.

```JavaScript
var viewSelector = gridContext.getViewSelector();
```

Methoden

|Name|Beschreibung|Verfügbar für|
|--|--|--|
|[getCurrentView](viewselector/getCurrentView.md)|[!INCLUDE[viewselector/includes/getCurrentView-description.md](viewselector/includes/getCurrentView-description.md)]|Schreibgeschütztes Raster|
|[isVisible](viewselector/isVisible.md)|[!INCLUDE[viewselector/includes/isVisible-description.md](viewselector/includes/isVisible-description.md)]|Schreibgeschütztes Raster|
|[setCurrentView](viewselector/setCurrentView.md)|[!INCLUDE[viewselector/includes/setCurrentView-description.md](viewselector/includes/setCurrentView-description.md)]|Schreibgeschütztes Raster|


### <a name="related-topics"></a>Verwandte Themen

[gridContext](../grids.md#bkmk_gridcontext)

[Raster und Unterraster in modellgestützten Apps](../grids.md)



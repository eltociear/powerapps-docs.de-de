---
title: getTotalRecordCount (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 8305f0cb-9959-4429-a721-a864ade4cd35
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gettotalrecordcount-client-api-reference"></a>getTotalRecordCount (Client-API-Referenz)



[!INCLUDE[./includes/getTotalRecordCount-description.md](./includes/getTotalRecordCount-description.md)]

- Wenn der Dynamics 365 for Outlook-Client nicht mit dem Server verbunden ist, ist diese Anzahl auf die Datensätze beschränkt, die der Benutzer für den Offlinemodus ausgewählt hat.
- Für mobile Dynamics 365-Clients gibt diese Methode die Anzahl von Datensätzen im Unterraster zurück.

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`var filteredRecordCount = gridContext.getGrid().getTotalRecordCount();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Gesamtanzahl Datensätze, die ggf. den Filterkriterien der Ansicht entsprechen.

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext).

Soehe [Sammlungen (Client-API-Referenz)](../../collections.md) für Informationen zu Methoden zum Zugreifen auf Daten in einer Sammlung.


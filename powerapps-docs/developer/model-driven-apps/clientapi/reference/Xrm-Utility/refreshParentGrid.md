---
title: refreshParentGrid (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 89123cde-7c66-4c7d-94e4-e287285019f8
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="refreshparentgrid-client-api-reference"></a>refreshParentGrid (Client-API-Referenz)



[!INCLUDE[./includes/refreshParentGrid-description.md](./includes/refreshParentGrid-description.md)] 

## <a name="syntax"></a>Syntax

`Xrm.Utility.refreshParentGrid(lookupOptions)`

## <a name="parameters"></a>Parameter

**lookupOptions**: Ein Objekt mit den folgenden Eigenschaften, um den Datensatzes anzugeben:

|Eigenschaftsname |Typ |Erforderlich  |Beschreibung |
|---|---|---|---|
|entityType|String|Ja |Entitätstyp des Datensatzes.|
|ID|String|Ja |ID des Datensatzes.|
|Name|String|No |Name des Datensatzes.|

### <a name="related-topics"></a>Verwandte Themen

[Xrm.Utility](../xrm-utility.md)




---
title: getTotalResultCount (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1f9169ce-cba3-4bb6-af20-f86140139cfe
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="gettotalresultcount-client-api-reference"></a>getTotalResultCount (Client-API-Referenz)



Erhält die Anzahl der Ergebnisse, die im Suchsteuerelement gefunden werden. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
var searchCount = kbSearchControl.getTotalResultCount();
```

## <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Die Anzahl der Suchergebnisse.
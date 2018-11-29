---
title: getSearchQuery (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getsearchquery-client-api-reference"></a>getSearchQuery (Client-API-Referenz)



Ruft den Text ab, der als Suchkriterien für das Wissensdatenbankverwaltungs-Steuerelement verwendet wird. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
var searchQuery = kbSearchControl.getSearchQuery();
```

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Der Text der Suchabfrage.

### <a name="related-topics"></a>Verwandte Themen

[setSearchQuery](setSearchQuery.md)


---
title: setSearchQuery (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 99e82b80-b6c3-4ee8-83cc-637b13ed8498
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setsearchquery-client-api-reference"></a>setSearchQuery (Client-API-Referenz)



Legt den Text fest, der als Suchkriterien für das Wissensdatenbanksuche-Steuerelement verwendet wird.

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement für die Wissensdatenbank

## <a name="syntax"></a>Syntax

```
var kbSearchControl = formContext.getControl("<name>");
kbSearchControl.setSearchQuery(searchString);
```

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|searchString |String |Ja|Der Text für die Suchabfrage.| 

### <a name="related-topics"></a>Verwandte Themen

[getSearchQuery](getSearchQuery.md)



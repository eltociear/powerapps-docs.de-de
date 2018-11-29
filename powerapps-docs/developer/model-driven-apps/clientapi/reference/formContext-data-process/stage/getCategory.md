---
title: getCategory (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2849a9e1-b2fb-464c-8fc7-90b0df027c86
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcategory-client-api-reference"></a>getCategory (Client-API-Referenz)



[!INCLUDE[./includes/getCategory-description.md](./includes/getCategory-description.md)]

## <a name="syntax"></a>Syntax

`var stageCategoryNumber = stageObj.getCategory().getValue();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Zahl. 

**Beschreibung**: Hier erhalten Sie eine Liste mit möglichen Werten.

|Value |Beschreibung|
|--|--|
|0|Qualifizieren|
|1|Entwickeln|
|2|Vorschlagen|
|3|Schließen|
|4|Identifizieren|
|5|Recherchieren|
|6|Beheben|

### <a name="related-topics"></a>Verwandte Themen

[formContext.data.process](../../formContext-data-process.md)
 



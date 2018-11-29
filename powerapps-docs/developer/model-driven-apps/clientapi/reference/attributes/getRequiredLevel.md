---
title: getRequiredLevel (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c0b6ea26-2a11-4a49-8ecf-fe700e782bf3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getrequiredlevel-client-api-reference"></a>getRequiredLevel (Client-API-Referenz) | MicrosoftDocs



Gibt einen Zeichenfolgenwert zurück, der angibt, ob ein Wert für das Attribut erforderlich oder empfohlen ist. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getRequiredLevel()`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge. 

**Beschreibung**: Gibt einen der folgenden Werte zurück:
- keine
- erforderlich
- Empfohlen

### <a name="related-topic"></a>Verwandtes Thema
[setRequiredLevel (Client-API-Referenz)](setRequiredLevel.md)

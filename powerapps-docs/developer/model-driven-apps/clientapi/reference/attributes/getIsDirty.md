---
title: getIsDirty (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 5f75ecae-a946-47a0-b748-96525b556f31
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getisdirty-client-api-reference"></a>getIsDirty (Client-API-Referenz)



Gibt einen Booleschen Wert zurück, wenn es beim Attributwert nicht gespeicherte Änderungen gibt. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getIsDirty()`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Boolesch. 

**Beschreibung**: „True“, wenn es nicht gespeicherte Änderungen gibt; andernfalls „false“.
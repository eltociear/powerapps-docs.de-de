---
title: getIsPartyList (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 487d0923-9675-4308-b88e-fdbf91853a98
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getispartylist-client-api-reference"></a>getIsPartyList (Client-API-Referenz)



Gibt einen Booleschen Wert zurück, der angibt, ob die Suche eine PartyList-Suche darstellt. PartyList-Suchen ermöglichen das Festlegen mehrerer Datensätze, z. B. das **An:**-Feld für einen E-Mail-Entitätsdatensatz.

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Suche

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getIsPartyList()`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Boolesch. 

**Beschreibung**: „True“, wenn das Suchattribut eine PartyList ist; andernfalls „false“.


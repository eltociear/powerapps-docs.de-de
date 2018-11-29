---
title: getInitialValue (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 56fb62e6-d357-4096-bf4c-f4c1b543d633
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getinitialvalue-client-api-reference"></a>getInitialValue (Client-API-Referenz)



Gibt einen Wert zurück, der den Wert darstellt, der für ein **Boolean**, **OptionSet** oder **MultiSelectOptionSet**-Attribut festgelegt ist, wenn das Formular geöffnet wird.

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Boolescher Wert, OptionSet, MultiSelectOptionSet 

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getInitialValue()`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Der anfängliche Wert für das Attribut.



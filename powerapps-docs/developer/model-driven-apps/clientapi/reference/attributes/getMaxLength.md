---
title: getMaxLength (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 67a96fc4-4d65-4858-90da-f41eeba0365a
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getmaxlength-client-api-reference"></a>getMaxLength (Client-API-Referenz)



Gibt eine Zahl zurück, die die maximale Länge eines Zeichenfolgen- oder Memoattributs angibt. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Zeichenfolge, Memo

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getMaxLength()`

## <a name="return-value"></a>Rückgabewert

**Typ**: Zahl. 

**Beschreibung**: Die maximal zulässige Länge einer Zeichenfolge für dieses Attribut.

> [!NOTE]
> Das-E-Mail-Formularattribut ist ein Memoattribut, es enthält aber keine `getMaxLength`-Methode.
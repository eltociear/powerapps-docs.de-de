---
title: getAttributeType (Client-API-Referenz) | MicrosoftDocs
ms.date: 02/13/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 9ef1c886-a0b8-4ba9-bb9f-e6ecfa9d6dff
author: KumarVivek
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getattributetype-client-api-reference"></a>getAttributeType (Client-API-Referenz)



Gibt einen Zeichenfolgenwert zurück, die den Typ des Attributs darstellt. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getAttributeType()`

## <a name="return-value"></a>Rückgabewert

Diese Methode gibt einen der folgenden **Zeichenfolge**-Werte zurück:

- Boolescher Wert
- datetime
- Dezimalzahl
- double
- integer
- Suche
- memo
- Zahlung
- multiselectoptionset
- optionset
- Zeichenfolge

---
title: getOption (Client-API-Referenz) | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e334d2d9-91c0-4953-956d-444a84dc9da2
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getoption-client-api-reference"></a>getOption (Client-API-Referenz) | MicrosoftDocs



Gibt ein Optionsobjekt zurück, wobei der Wert mit dem Argument (Beschriftung oder Aufzählungswert), das an die Methode übergeben wird, übereinstimmt. 

## <a name="attribute-types-supported"></a>Unterstützte Attributtypen

OptionSet, MultiSelectOptionSet

## <a name="syntax"></a>Syntax

`formContext.getAttribute(arg).getOption(value)`

## <a name="parameters"></a>Parameter

**Zeichenfolge** (Beschriftung der Option) oder **Nummer** (Enumerationswert der Option).

## <a name="return-value"></a>Rückgabewert

**Typ**: Optionsobjekt. 

**Beschreibung**: Der logische Name des Attributs.


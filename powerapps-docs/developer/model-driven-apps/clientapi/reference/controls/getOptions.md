---
title: getOptions (Client-API-Referenz) | MicrosoftDocs
ms.date: 08/13/2019
ms.service: powerapps
ms.topic: reference
ms.assetid: 83347491-68d2-4844-bda4-0cd0abde2edf
author: nkrb
ms.author: kvivek
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getoptions-client-api-reference"></a>getOptions (Client-API-Referenz) | MicrosoftDocs

Gibt ein Optionsobjekt-Array zurück, das die gültigen Optionen darstellt, die für ein Steuerelement zur Verfügung stehen, einschließlich einer leeren Option und mit Ausnahme aller Optionen, die vom Steuerelement mithilfe von [removeOption](removeOption.md) entfernt wurden. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

OptionSet, MultiSelectOptionSet

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getOptions()`

## <a name="return-value"></a>Rückgabewert

**Typ**: Array von Optionsobjekten. 

**Beschreibung**: Das Array der Optionsobjekte, das die gültigen Optionen darstellt, wobei jedes Optionsobjekt die folgenden Attribute aufweist:
- **text**: Zeichenfolge. Beschriftung der Option.
- **value**: Zahl. Enumerationswert der Option.


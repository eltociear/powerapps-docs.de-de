---
title: getCurrentView (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getcurrentview-client-api-reference"></a>getCurrentView (Client-API-Referenz)



[!INCLUDE[./includes/getCurrentView-description.md](./includes/getCurrentView-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Schreibgeschütztes Raster

## <a name="syntax"></a>Syntax

`viewSelector.getCurrentView();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Suchobjekt

**Beschreibung**: Das Suchobjekt, welches die folgenden Attribute aufweist:

- **entityType**: Zahl. Der Objekttypcode für SavedQuery (1039) oder UserQuery (4230), die die Ansicht darstellt, die der Benutzer auswählen kann.
- **id**: Zeichenfolge. Die Id für die Ansicht, die der Benutzer auswählen kann.
- **name**: Zeichenfolge. Der Name der Ansicht, die der Benutzer auswählen kann.

## <a name="remarks"></a>Anmerkungen

Wenn das Unterrastersteuerelement nicht so konfiguriert ist, dass die Ansichtsauswahl angezeigt wird, wird durch Aufrufen dieser Methode für das `viewSelector`-Objekt ein Fehler ausgelöst.

Informationen zum Abrufen des `viewSelector`-Objekt finden Sie unter [ViewSelector](../viewselector.md).




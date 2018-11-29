---
title: getRelationship (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="getrelationship-client-api-reference"></a>getRelationship (Client-API-Referenz)



[!INCLUDE[./includes/getRelationship-description.md](./includes/getRelationship-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`gridContext.getRelationship();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Objekt.

**Beschreibung**: Ein Beziehungsobjekt mit folgenden Attribute:
- **attributeName**: Zeichenfolge. Name des Attributs.
- **name**: Zeichenfolge. Der Name der Beziehung. 
- **navigationPropertyName**: Zeichenfolge. Name der Navigationseigenschaft für die Beziehung.
- **relationshipType**: Zahl. Gibt eine der folgenden Werte zurück, um den Typ der Beziehung anzugeben:
    - 0: OneToMany
    - 1: ManyToMany
- **roleType**: Zahl. Gibt eine der folgenden Werte zurück, um den Rollentyp der Beziehung anzugeben:
    - 1: Referencing
    - 2: AssociationEntity

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext).

### <a name="related-topics"></a>Verwandte Themen

[openRelatedGrid](openRelatedGrid.md)

<!-- TODO:
[Customize entity relationship metadata](../../../../customize-entity-relationship-metadata.md) -->



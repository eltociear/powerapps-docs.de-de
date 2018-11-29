---
title: getFetchXml (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="getfetchxml-client-api-reference"></a>getFetchXml (Client-API-Referenz)



[!INCLUDE[./includes/getFetchXml-description.md](./includes/getFetchXml-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Bearbeitbare und schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`var result = gridContext.getfetchXml();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Die FetchXML-Abfrage.

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext). 

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt das abgerufene Fetch XNL des Kontaktunterrasters in der Konsole:

```JavaScript
function myFunction(executionContext) {
    var formContext = executionContext.getFormContext(); // get the form context
    var gridContext = formContext.getControl("Contacts"); // get the grid context
    var retrieveFetchXML = function () {
        var result = gridContext.getFetchXml();
        console.log(result)
    };
    gridContext.addOnLoad(retrieveFetchXML);    
}
```



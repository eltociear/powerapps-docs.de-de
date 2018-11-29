---
title: addOnLoad (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 24f34ac9-2a15-478e-980c-588a79d84e8d
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addonload-client-api-reference"></a>addOnLoad (Client-API-Referenz)



[!INCLUDE[./includes/addOnLoad-description.md](./includes/addOnLoad-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Schreibgeschützte Raster

## <a name="syntax"></a>Syntax

`gridContext.addOnLoad(myFunction);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|myFunction|Funktionsreferenz|Ja|Die Funktion, die ausgeführt werden soll, wenn die Unterraster geladen werden.  Die Funktion wird unten auf der Ereignishandlerpipeline hinzugefügt. Der Ausführungskontext wird automatisch als der erste Parameter für die Funktion übergeben. Weitere Informationen finden Sie unter [Ausführungskontex](../../../clientapi-execution-context.md).

## <a name="remarks"></a>Anmerkungen

Um den `gridContext` abzurufen, siehe [Abrufen des Rasterkontexts](../../grids.md#bkmk_gridcontext).

## <a name="example"></a>Beispiel

Fügen Sie die myContactsGridOnloadFunction-Funktion im Ereignis des **OnLoad**-Kontakteunterrasters hinzu.

```JavaScript
function myFunction(executionContext) {
    var formContext = executionContext.getFormContext(); // get the form context
    var gridContext = formContext.getControl("Contacts");// get the grid context
    var myContactsGridOnloadFunction = function () { console.log("Contacts Subgrid OnLoad event occurred") };
    gridContext.addOnLoad(myContactsGridOnloadFunction);
}
```

### <a name="related-topics"></a>Verwandte Themen

[removeOnLoad](removeOnLoad.md)




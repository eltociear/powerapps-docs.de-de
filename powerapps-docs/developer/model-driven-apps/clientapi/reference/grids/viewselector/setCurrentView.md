---
title: setCurrentView (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: f5ee65bf-2964-49c9-9dd2-d81416353bf3
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setcurrentview-client-api-reference"></a>setCurrentView (Client-API-Referenz)



[!INCLUDE[./includes/setCurrentView-description.md](./includes/setCurrentView-description.md)]

## <a name="grid-types-supported"></a>Unterstützte Rastertypen

Schreibgeschütztes Raster

## <a name="syntax"></a>Syntax

`viewSelector.setCurrentView(object);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|Objekt|Suchobjekt|Ja|Geben Sie das Suchobjekt an, welches die folgenden Attribute aufweist:<br/>- **entityType**: Zahl. Der Objekttypcode für SavedQuery (1039) oder UserQuery (4230), die die Ansicht darstellt, die der Benutzer auswählen kann.<br/>- **id**: Zeichenfolge. Die Id für die Ansicht, die der Benutzer auswählen kann.<br/>- **name**: Zeichenfolge. Der Name der Ansicht, die der Benutzer auswählen kann.|

## <a name="remarks"></a>Anmerkungen

Wenn das Unterrastersteuerelement nicht so konfiguriert ist, dass die Ansichtsauswahl angezeigt wird, wird durch Aufrufen dieser Methode für das `viewSelector`-Objekt ein Fehler ausgelöst.

Informationen zum Abrufen des `viewSelector`-Objekt finden Sie unter [ViewSelector](../viewselector.md).

## <a name="example"></a>Beispiel

```JavaScript
function setView(executionContext) {
    var ContactsIFollow = {
        entityType: 1039, // SavedQuery
        id: "3A282DA1-5D90-E011-95AE-00155D9CFA02",
        name: "Contacts I Follow"
    }
    // Get the gridContext
    var formContext = executionContext.getFormContext();
    var gridContext = formContext.getControl("Contacts");

    // Set the view using ContactsIFollow
    gridContext.getViewSelector().setCurrentView(ContactsIFollow);
}
```

### <a name="related-topics"></a>Verwandte Themen

[ViewSelector](../viewselector.md)





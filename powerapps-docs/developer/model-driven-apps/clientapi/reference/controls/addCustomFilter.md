---
title: addCustomFilter (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e359b-c4d9-48ac-a57b-367c2e6168c5
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addcustomfilter-client-api-reference"></a>addCustomFilter (Client-API-Referenz)



Fügt weitere Filter zu den Ergebnissen, die in der Suche angezeigt werden, hinzu. Jeder Filter wird mit zuvor hinzugefügten Filtern als „UND”-Bedingung kombiniert.

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Suche

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).addCustomFilter(filter, entityLogicaName)`

## <a name="parameters"></a>Parameter

- **filter**: Zeichenfolge. Das anzuwendende fetchXml-Filterelement. Beispiel:

    ```xml
    <filter type="and">
      <condition attribute="address1_city" operator="eq" value="Redmond" />
    </filter>
    ```

- **entityLogicalName**: (Optional) Zeichenfolge. Wenn dies festgelegt ist, wird der Filter nur zu diesem Entitätstypen angewendet. Andernfalls gilt dieser für alle zurückgesendeten Entitätstypen.

## <a name="remarks"></a>Anmerkungen

Diese Methode kann nur in einer Funktion in einem Ereignishandler für das [Lookup Control PreSearch Event](../events/presearch.md) verwendet werden.

## <a name="example"></a>Beispiel

Das folgende Codebeispiel wird für die Suche des Verkaufschance-Formulars Firma **Firma** (parentaccountid) bereitgestellt. Wenn die **Sdk.setParentAccountIdFilter**-Funktion im Formular **Onload**-Ereignishandler festgelegt ist, wird die **Sdk.filterCustomAccounts**-Funktion zum **PreSearch**-Ereignis für diese Suche hinzugefügt. Vergessen Sie nicht, die Option auszuwählen, um im Ausführungssinne anzumelden, wenn die Funktion im Formular **Onload**-Ereignishandler festgelegt wird. Das Ergebnis ist, dass nur Firmen mit dem **Kategorie** (accountcategorycode)-Wert vom **Bevorzugten Kunden** (1) zurückgegeben werden.

```JavaScript
// A namespace defined for SDK sample code
// You should define a unique namespace for your libraries
var Sdk = window.Sdk || {};

// set 'Sdk.setParentAccountIdFilter' in the Opportunity form onload event handler
Sdk.setParentAccountIdFilter = function (executionContext) {

    // get the form context
    formContext = executionContext.getFormContext();
    formContext.getControl("parentaccountid").addPreSearch(Sdk.filterCustomerAccounts);
}

Sdk.filterCustomerAccounts = function () {

    // Only show accounts with the type 'Preferred Customer'
    var customerAccountFilter = "<filter type='and'><condition attribute='accountcategorycode' operator='eq' value='1'/></filter>";
    formContext.getControl("parentaccountid").addCustomFilter(customerAccountFilter, "account");
}
```
[addPreSearch](addPreSearch.md)

[formContext](../../clientapi-form-context.md)
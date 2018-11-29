---
title: isLoaded (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 1870151d-6029-4733-ac35-6ee4d43f9553
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isloaded-client-api-reference"></a>isLoaded (Client-API-Referenz)



[!INCLUDE[./includes/isLoaded-description.md](./includes/isLoaded-description.md)]

## <a name="syntax"></a>Syntax

`quickViewControl.isLoaded();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Boolesch.

**Beschreibung**: "True" bedeutet, dass die Datenbindung für ein zugehöriges Steuerelement vollständig ist, andernfalls "false". 

## <a name="remarks"></a>Anmerkungen

Die Datenbindung für die zugehörigen Steuerelemente in einem Steuerelement für die Schnellansicht kann im Rahmen des Hauptformulars **OnLoad** nicht abgeschlossen sein, da das Schnellansichtsformular, an das das Steuerelement gebunden ist, möglicherweise nicht vollständig geladen wurde. Dies hat zum Ergebnis, dass [getAttribute](../controls/getattribute.md) oder eine andere datenbezogene Methode in einem zugehörigen Steuerelement nicht funktioniert. Die **isLoaded**-Methode für das Steuerelement für die Schnellansicht hilft dabei, den Datenbindungsstatus des zugehörigen Steuerelements in einem Steuerelement für die Schnellansicht festzustellen.

## <a name="example"></a>Beispiel

Der folgende Beispielcode zeigt, wie Sie **isLoaded**-Methode verwenden können, um den Bindungsstatus zu überprüfen und anschließend den Wert des Attributs abzurufen, an das das zugehörige Steuerelement in einem Steuerelement für die Schnellansicht gebunden ist.

```JavaScript
function getAttributeValue(executionContext) {
    var formContext = executionContext.getFormContext();
    var quickViewControl = formContext.ui.quickForms.get("<QuickViewControlName>");
    if (quickViewControl != undefined) {
        if (quickViewControl.isLoaded()) {
            // Access the value of the attribute bound to the constituent control
            var myValue = quickViewControl.getControl(0).getAttribute().getValue();
            console.log(myValue);
            return;
        }
        else {
            // Wait for some time and check again
            setTimeout(getAttributeValue, 10);
        }
    }
    else {
        console.log("No data to display in the quick view control.");
        return;
    }
}
```

### <a name="related-topics"></a>Verwandte Themen

[formContext.ui.quickForms](../formContext-ui-quickForms.md)
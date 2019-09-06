---
title: getOutputs | MicrosoftDocs
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: c83c3a09-f04e-4dc6-8ddf-ccd0b4cc080e
ms.author: nabuthuk
author: Nkrb
---
# <a name="getoutputs"></a>getOutputs

[!INCLUDE[./includes/getoutputs-description.md](./includes/getoutputs-description.md)]

## <a name="syntax"></a>Syntax

`getOutputs()`

## <a name="remarks"></a>Anmerkungen

Die Ausgabe enthält einen Wert für jede Eigenschaft, die als `input-output` oder `bound` im Manifest markiert ist.
Wenn das Manifest beispielsweise die Eigenschaft `value` aufweist, der ein `input-output`-Element ist, und Sie möchten dies auf die lokal Variable `myvalue` festlegen, sollten Sie Folgendes zurückgeben:

```javascript
{
    value: myvalue
}
```

## <a name="example"></a>Beispiel

```javascript
MyControl.prototype.getOutputs = function () {
    var result = {
        value: this._value
    };
    return result;
};
```


### <a name="related-topics"></a>Verwandte Themen

[Steuerelement](../control.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
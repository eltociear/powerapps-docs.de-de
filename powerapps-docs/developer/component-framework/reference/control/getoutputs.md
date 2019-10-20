---
title: getoutputs | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: c83c3a09-f04e-4dc6-8ddf-ccd0b4cc080e
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 408633e1fd87c3c9517ec0984251bbbce056cc50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345380"
---
# <a name="getoutputs"></a>getOutputs

[!INCLUDE[./includes/getoutputs-description.md](./includes/getoutputs-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="syntax"></a>Syntax

`getOutputs()`

## <a name="remarks"></a>Rede

Die Ausgabe enthält einen Wert für jede Eigenschaft, die als `input-output` oder `bound` im Manifest gekennzeichnet ist.
Wenn das Manifest z. b. eine Eigenschaft `value`, die ein `input-output` ist, und Sie es auf die lokale Variable festlegen möchten `myvalue` sollten Sie Folgendes zurückgeben:

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
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
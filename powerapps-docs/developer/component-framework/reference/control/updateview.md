---
title: UpdateView | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 899d6eb3-62b4-4c1f-947c-aed1f8643caa
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d7ac81ef617aa4e9e3564ade01bc469b0d7f5bc8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345334"
---
# <a name="updateview"></a>updateView

[!INCLUDE[./includes/updateview-description.md](./includes/updateview-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="syntax"></a>Syntax

`updateView(context)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Kontext|`context`|ja|Enthält Werte, die von der Anpassung festgelegt werden, die dem im Manifest definierten Namen zugeordnet ist, sowie in den Hilfsprogrammfunktionen.|

## <a name="example"></a>Beispiel

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.updateView = function (context) {
    this._labelElement.innerText = "Hello World! (JS)";
};
```

## <a name="remarks"></a>Rede

Legen Sie den Wert der Feld Komponente auf den Rohwert aus dem konfigurierten Feld fest.


### <a name="related-topics"></a>Verwandte Themen

[Steuerelement](../control.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
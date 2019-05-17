---
title: updateView| MicrosoftDocs
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 899d6eb3-62b4-4c1f-947c-aed1f8643caa
ms.author: nabuthuk
---
# <a name="updateview"></a>updateView

[!INCLUDE[./includes/updateview-description.md](./includes/updateview-description.md)]

## <a name="syntax"></a>Syntax

`updateView(context)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Kontext|`context`|Ja|Enthält Werte, wie Sie vom Anpasser eingerichtet wurden, die dem im Manifest definierten Namen und in den Hilfsprogrammfunktionen zugeordnet sind.|

## <a name="example"></a>Beispiel

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.updateView = function (context) {
    this._labelElement.innerText = "Hello World! (JS)";
};
```

## <a name="remarks"></a>Anmerkungen

Legen Sie den Wert der Feldkomponente auf den Rohwert aus dem konfigurierten Feld fest


### <a name="related-topics"></a>Verwandte Themen

[Steuerelement](../control.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
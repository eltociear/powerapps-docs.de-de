---
title: init | MicrosoftDocs
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: 4485b7d4-c68f-4298-8676-1820eb33c1ad
ms.author: nabuthuk
---
# <a name="init"></a>init

[!INCLUDE[./includes/init-description.md](./includes/init-description.md)]

## <a name="syntax"></a>Syntax

`init(context,notifyOutputChanged,state,container)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Kontext|[Kontext](../context.md)|Ja|Die *Eingabeeigenschaften*, die die Parameter, die Komponentenmetadaten und die Schnitstellenfunktionen enthalten.|
|notifyOutputChanged|`function`|Nein|Die Methode, mit der das Framework benachrichtigt wird, dass neue Ausgaben vorhanden sind|
|state|`Dictionary`|Nein|Der Komponentenstatus, der von *setControlState* in der letzten Sitzung gespeichert wird|
|Container|[HTMLDivElement](https://developer.mozilla.org/docs/Web/API/HTMLDivElement)|Nein|Das zu rendernde div-Element.|

## <a name="example"></a>Beispiel

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.init = function (context, notifyOutputChanged, state, container) {
    this._labelElement = document.createElement("label");
    this._labelElement.setAttribute("class", "JS_HelloWorldColor");
    container.appendChild(this._labelElement);
};
```

### <a name="related-topics"></a>Verwandte Themen

[Steuerelement](../control.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)

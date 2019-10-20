---
title: init | MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: 4485b7d4-c68f-4298-8676-1820eb33c1ad
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 57a5ce0d4e930184bf42502f1dc16b6a648f1292
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345495"
---
# <a name="init"></a>init

[!INCLUDE[./includes/init-description.md](./includes/init-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="syntax"></a>Syntax

`init(context,notifyOutputChanged,state,container)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Kontext|[Context](../context.md)|ja|Die *Eingabe Eigenschaften* , die die Parameter, Komponenten Metadaten und Schnittstellen Funktionen enthalten.|
|notitputchanged|`function`|Nein|Die Methode zum Benachrichtigen des Frameworks, dass neue Ausgaben aufgetreten sind|
|Land|`Dictionary`|Nein|Der Komponenten Status, der in der letzten Sitzung aus *setcontrolstate* gespeichert wird.|
|Kum|[HTMLDivElement](https://developer.mozilla.org/docs/Web/API/HTMLDivElement)|Nein|Das zu Rendering-div-Element.|

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
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)

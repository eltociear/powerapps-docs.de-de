---
title: Client | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ce41c82-bf4a-4d34-9344-5311c24d76de
ms.openlocfilehash: 17bcd34226be7b2e0b863849defdce532a0b99a8
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025632"
---
# <a name="client"></a>Client

[!INCLUDE [client-description](includes/client-description.md)]

## <a name="syntax"></a>Syntax

`context.client;`

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="properties"></a>Eigenschaften

### <a name="disablescroll"></a>disablescroll

Deaktiviert die scrollfunktionen für die-Komponenten.

**Typ**: `boolean`

## <a name="methods"></a>Anzuwenden

|Anzuwenden | Beschreibung |Verfügbar für|
| ------------- |-------------|------|
|[getClient](client/getclient.md)|[!INCLUDE [getclient-description](client/includes/getclient-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[getformfactor](client/getformfactor.md)|[!INCLUDE [getformfactor-description](client/includes/getformfactor-description.md)]|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)|
|[isOffline](client/isoffline.md)|[!INCLUDE [isoffline-description](client/includes/isoffline-description.md)]|Modellgesteuerte Apps|

## <a name="example"></a>Beispiel 

```TypeScript
private createHTMLTableElement(): HTMLTableElement {
    let tableElement: HTMLTableElement = document.createElement("table");
    tableElement.setAttribute("class", "SampleControlHtmlTable_HtmlTable");
    let key: string = "Example Method";
    let value: string = "Result";
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, true));
    key = "getFormFactor()";
    value = String(this._context.client.getFormFactor());
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, false));
    key = "getClient()";
    value = String(this._context.client.getClient());
    tableElement.appendChild(this.createHTMLTableRowElement(key, value, false));
}
```

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
---
title: Popup | Microsoft-Dokumentation
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
ms.assetid: b0af1803-ae3a-41c2-a8a5-b15970bd6f96
ms.openlocfilehash: bb28a979ac721eded06025a56588023c211ea6f9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342206"
---
# <a name="popup"></a>Popup

[!INCLUDE [popup-description](includes/popup-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="closeonoutsideclick"></a>closeonoutsideclick

Gibt an, ob das Popup Fenster bei einem äußeren Mausklick geschlossen wird. Wenn Sie auf `false` festgelegt ist, wird das Popup Fenster nicht mit einem außen Klick geschlossen.

**Typ**: `boolean`

### <a name="content"></a>Inhaltliche

Das statische DOM-Element, das eingefügt werden soll.

**Type**: [HtmlElement](https://developer.mozilla.org/docs/Web/API/HTMLElement)

### <a name="id"></a>id

Die ID, die ggf. auf die Anker Komponente festgelegt wird.

**Typ**: `string`

### <a name="name"></a>Benennen

Der Name des Popups. Wird als Verweis zum Öffnen von Popups verwendet.

**Typ**: `string`

### <a name="popuptoopen"></a>popuptoopen

Der Name des Popups, das geöffnet werden soll.

**Typ**: `string`

### <a name="remarks"></a>Rede

Sollte nur in einem root-Popup definiert werden. Zum Öffnen von "popsted Popups" sollte eine Zeichenfolge wie `rootName.nestedName.[allOtherNestedNames]` angegeben werden. Um Popups zu schließen, sollte eine leere Zeichenfolge bereitgestellt werden. Diese Eigenschaft wird automatisch an die untergeordneten Elemente weitergegeben.

## <a name="type"></a>type

Der Typ des Popups, das in der Aufzählung popuptype beschrieben wird. Für jede Gruppe von Popups sollte nur ein `root` Popup vorhanden sein.

**Typ**: `enum`

Der `type` Wert ist eine Enumeration mit den folgenden möglichen Werten.

|Value|Member|
|--|--|
|1|Fasst|
|2|Geschachtelte|

### <a name="remarks"></a>Rede

Sollte nur ein `Root` Popup für jede Gruppe von Popups sein.

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
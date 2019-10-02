---
title: Popup | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b0af1803-ae3a-41c2-a8a5-b15970bd6f96
---

# <a name="popup"></a>Popup

[!INCLUDE [popup-description](includes/popup-description.md)]

## <a name="closeonoutsideclick"></a>closeOnOutsideClick

Gibt an, ob das Popup bei einem externen Mausklick geschlossen wird.

**Typ**: `boolean`

## <a name="content"></a>content

Statisches DOM-Element, das eingeführt werden soll.

**Typ**: [HTMLElement](https://developer.mozilla.org/docs/Web/API/HTMLElement)

## <a name="id"></a>ID

Die für die Ankerkomponente festzulegende ID, sofern vorhanden.

**Typ**: `string`

## <a name="name"></a>Name

Der Name des Popups. Wird wie ein Verweis auf geöffnete Popups verwendet.

**Typ**: `string`

## <a name="popuptoopen"></a>popupToOpen

Der Name des Popups, das geöffnet werden soll.

**Typ**: `string`

### <a name="remarks"></a>Anmerkungen

Soll nur in einem Stammpopup definiert werden. Zum Öffnen geschachtelte Popups, sollten einer Zeichenfolge wie `rootName.nestedName.[allOtherNestedNames]` bereitgestellt werden. Zum Schließen des Popups, sollte einer leeren Zeichenfolge bereitgestellt werden. Diese Eigenschaft wird automatisch an untergeordnete Elemente propagiert.

## <a name="type"></a>typ

Der Typ des Popups

**Typ**: `enum`

Der `type`-Wert ist eine Enumeration mit folgenden möglichen Werten:

|Value|Mitglied|
|--|--|
|1|Stamm|
|2|Geschachtelt|

### <a name="remarks"></a>Anmerkungen

Es sollte nur ein `Root`-Popup für jeden Datensatz des Popups geben.

### <a name="related-topics"></a>Verwandte Themen

[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
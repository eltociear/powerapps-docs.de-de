---
title: openConfirmDialog | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83f2c208-696c-48b1-b65c-2ba7374d6cfc
---

# <a name="openconfirmdialog"></a>openConfirmDialog

[!INCLUDE [openconfirmdialog-description](includes/openconfirmdialog-description.md)]

## <a name="syntax"></a>Syntax

`openConfirmDialog(confirmStrings, options)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|confirmStrings|`ConfirmDialogStrings`|Ja|Zeichenfolgen, die im Dialogfeld verwendet werden. ConfirmDialogStrings hat die folgenden Attribute:<br/>- **title**: `string`. Dialogtitel bestätigen. <br/>- **subtitle**: `string`. Dialoguntertitel bestätigen.<br/>- **text**: `string`. Dialogtext/Meldung bestätigen.<br/>- **confirmButtonLabel**: `string`. Die Bestätigensschaltflächenbeschriftung. Wenn Sie nicht die Beschriftung der Schaltfläche angeben, wird OK (in der bevorzugten Sprache des Benutzers) als Beschriftung der Schaltfläche verwendet.|
|Optionen|`ConfirmDialogOptions`|Ja|Optionen des Dialogs ConfirmDialogOptions hat die folgenden Attribute:<br/>- **height**: `number`. Höhe des Bestätigung-Dialogfelds in Pixeln. <br/>- **width**: `number`. Breite des Bestätigung-Dialogfelds in Pixeln|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<ConfirmDialogResponse>`

Gibt ein Objekt mit dem bestätigten Attribut (boolesch) zurück und gibt es zurück, das angibt, ob die Bestätigen-Schaltfläche angeklickt wurde, um das Dialogfeld zu schließen.

## <a name="remarks"></a>Anmerkungen

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
---
title: openAlertDialog | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4acd3f17-74c0-4de1-9326-3778ff413f1e
---

# <a name="openalertdialog"></a>openAlertDialog

[!INCLUDE [openalertdialog-description](includes/openalertdialog-description.md)]

## <a name="syntax"></a>Syntax

`openAlertDialog(alertStrings, options)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|alertStrings|`AlertDialogStrings`|Ja|Die im Warnungsdialog zu verwendeten Zeichenfolgen. AlertDialogStrings hat die folgenden Attribute:<br/>- **Text**: `string`. Die im Dialogfeld anzuzeigende Nachricht. <br/>- **confirmButtonLabel**:`string`. Die Bestätigensschaltflächenbeschriftung. wenn Sie nicht die Beschriftung der Schaltfläche angeben, wird OK (in der bevorzugten Sprache des Benutzers) als Beschriftung der Schaltfläche verwendet.|
|Optionen|`AlertDialogOptions`|Ja|Dialogoptionen AlertDialogOptions hat die folgenden Attribute:<br/>- **height**: `number`. Höhe des Warnung-Dialogfelds in Pixeln. <br/>- **width**: `number`. Breite des Warnung-Dialogfelds in Pixeln.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

## <a name="remarks"></a>Anmerkungen

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)

### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
---
title: openErrorDialog | Microsoft Docs
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
ms.assetid: 10c154b9-45a0-44ee-a621-73d6a9009c6d
---
# <a name="openerrordialog"></a>openErrorDialog

[!INCLUDE [openerrordialog-description](includes/openerrordialog-description.md)]

## <a name="syntax"></a>Syntax

`openErrorDialog(options)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Optionen|`ErrorDialogOptions`|Ja|Fehlerdialogoptionen ErrorDialogOptions hat die folgenden Attribute: <br/>- **Details**: `string`. Informationen zum Fehler. Wenn Sie dem angeben, ist die Schaltfläche Protokolldatei herunterladen in der Fehlermeldung ist verfügbar, indem Sie darauf klicken und eine Textdatei den Inhalt herunterladen, die in diesem Attribut angegeben ist.<br/>- **errorCode**: `number`. Wenn Sie nur errorCode einstellen, wird die Meldung für den Fehlercode automatisch vom Server abgerufen und im Fehlerdialogfeld angezeigt. Wenn Sie einen errorCode-Wert angeben, wird eine Standardfehlermeldung angezeigt.<br/>- **message**: `string`. Die im Fehler-Dialogfeld anzuzeigende Nachricht.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

## <a name="remarks"></a>Anmerkungen

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
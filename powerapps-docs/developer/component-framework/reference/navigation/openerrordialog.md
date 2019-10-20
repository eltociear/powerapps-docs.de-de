---
title: Openerrordialog | Microsoft-Dokumentation
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
ms.assetid: 10c154b9-45a0-44ee-a621-73d6a9009c6d
ms.openlocfilehash: c3371b7c3ea8bde869acc261ab7d4fc8f28ba7da
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342436"
---
# <a name="openerrordialog"></a>openErrorDialog

[!INCLUDE [openerrordialog-description](includes/openerrordialog-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.navigation.openErrorDialog(options)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Optionen|`ErrorDialogOptions`|Ja|Fehler Dialogfeld Optionen. Errordialogoptions verfügt über die folgenden Attribute: <br/>- **Details**: `String`. Details zum Fehler. Wenn Sie diese Angabe angeben, steht die Schaltfläche **Protokolldatei herunterladen** in der Fehlermeldung zur Verfügung. Wenn Sie darauf klicken, können Benutzer eine Textdatei mit dem in diesem Attribut angegebenen Inhalt herunterladen.<br/>- **errorCode**: `Number`. Der Fehlercode. Wenn Sie nur ErrorCode festlegen, wird die Meldung für den Fehlercode automatisch vom Server abgerufen und im Fehler Dialogfeld angezeigt. Wenn Sie einen **errorCode** -Wert angeben, wird ein Fehler Dialogfeld mit einer Standard Fehlermeldung angezeigt.<br/>- **Meldung**: `String`. Die Meldung, die im Fehler Dialogfeld angezeigt werden soll. Sie müssen entweder das **errorCode** -oder das **Message** -Attribut festlegen.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

## <a name="remarks"></a>Rede

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) und [File](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
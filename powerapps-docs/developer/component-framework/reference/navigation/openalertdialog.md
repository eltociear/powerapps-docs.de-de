---
title: Openalertdialog | Microsoft-Dokumentation
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
ms.assetid: 4acd3f17-74c0-4de1-9326-3778ff413f1e
ms.openlocfilehash: f1f5a2a78faf3dd9c6a1d6d197fab61772969084
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342505"
---
# <a name="openalertdialog"></a>openAlertDialog

[!INCLUDE [openalertdialog-description](includes/openalertdialog-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.navigation.openAlertDialog(alertStrings, options)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|alertstrings|`AlertDialogStrings`|Ja|Die im Warnungs Dialogfeld zu verwendenden Zeichen folgen. Alertdialogstrings weist die folgenden Attribute auf:<br/>- **Text**: `string`. Die Meldung, die im Warnungs Dialogfeld angezeigt werden soll. <br/>- **confirmbuttonlabel**: `string`. Die Bezeichnung der Schaltfläche bestätigen. Wenn Sie die Schaltflächen Bezeichnung nicht angeben, wird **OK** (in der bevorzugten Sprache des Benutzers) als Schaltflächen Bezeichnung verwendet.|
|Optionen|`AlertDialogOptions`|Ja|Dialog Feld Optionen. Alertdialogoptions verfügt über die folgenden Attribute:<br/>- **Höhe**: `number`. Höhe des Warn Dialogfelds in Pixel. <br/>- **Breite**: `number`. Breite des Warn Dialogfelds in Pixel|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

## <a name="remarks"></a>Rede

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) und [File](https://developer.mozilla.org/docs/Web/API/File)

## <a name="example"></a>Beispiel 

```TypeScript
context.navigation.openAlertDialog({text:"This is an alert.", confirmButtonLabel : "Yes",}).then(
        function success()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Alert dialog closed";
        },
        function()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Error in Alert Dialog";
        }
    );
```

### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
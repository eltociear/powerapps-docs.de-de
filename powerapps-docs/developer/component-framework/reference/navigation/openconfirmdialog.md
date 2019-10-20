---
title: Openconfirmdialog | Microsoft-Dokumentation
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
ms.assetid: 83f2c208-696c-48b1-b65c-2ba7374d6cfc
ms.openlocfilehash: 8b7bda89b9c8d83614a4a95281853676db9cf568
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342482"
---
# <a name="openconfirmdialog"></a>openConfirmDialog

[!INCLUDE [openconfirmdialog-description](includes/openconfirmdialog-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.navigation.openConfirmDialog(confirmStrings, options)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|confirmstrings|`ConfirmDialogStrings`|Ja|Die im Dialogfeld verwendeten Zeichen folgen. Confirmdialogstrings weist die folgenden Attribute auf:<br/>- **Titel**: `String`. Der Titel, der im Bestätigungs Dialogfeld angezeigt werden soll. <br/>-  unter**Titel**: `String`. Der Untertitel, der im Bestätigungs Dialogfeld verwendet werden soll.<br/>- **Text**: `String`. Die Meldung, die im Bestätigungs Dialogfeld angezeigt werden soll.<br/>- **confirmbuttonlabel**: `String`. Die Bezeichnung der Schaltfläche bestätigen. Wenn Sie die Schaltflächen Bezeichnung nicht angeben, wird **OK** (in der bevorzugten Sprache des Benutzers) als Schaltflächen Bezeichnung verwendet.<br/>- **CancelButtonLabel**: `String` der Schaltflächen Bezeichnung "Abbrechen". Wenn Sie die Schaltflächen Bezeichnung Abbrechen nicht angeben, wird **Abbrechen** als Schaltflächen Bezeichnung verwendet.|
|Optionen|`ConfirmDialogOptions`|Nein|Optionen für das Dialogfeld. Die confirmdialogoptions verfügt über die folgenden Attribute:<br/>- **Höhe**: `Number`. Höhe des Bestätigungs Dialogfelds in Pixel. <br/>- **Breite**: `Number`. Breite des Bestätigungs Dialogfelds in Pixel|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<ConfirmDialogResponse>`

Description: gibt ein Objekt mit dem bestätigten (booleschen) Attribut zurück, das angibt, ob auf die Bestätigungs Schaltfläche geklickt wurde, um das Dialogfeld zu schließen.

## <a name="remarks"></a>Rede

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
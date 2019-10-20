---
title: OpenFile | Microsoft-Dokumentation
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
ms.assetid: ae94e467-d12c-4a74-96f0-05a09e03c5f8
ms.openlocfilehash: 5de6eefb37450fde50127829f2a922252d08a4fb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342689"
---
# <a name="openfile"></a>openFile

[!INCLUDE [openfile-description](includes/openfile-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.navigation.openFile(file, options)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Datei|`FileObject`|Ja|Ein-Objekt, das die zu öffnende Datei beschreibt. Das FileObject weist die folgenden Attribute auf: <br/>- **FileContent**: `String`. Der Inhalt der Datei. <br/>- **Dateiname**: `String`. Der Name der Datei.<br/>- **FileSize**: `Number`. Größe der Datei in KB. <br/>- **MimeType**: `String`. Datei-MIME-Typ.|
|Optionen|`Object`|Nein|Ein Objekt, das beschreibt, ob die Datei geöffnet oder gespeichert werden soll. Das-Objekt verfügt über das folgende Attribut: <br/>- **OpenMode**: Geben Sie 1 zum Öffnen an. 2 zum Speichern. 
Wenn Sie diesen Parameter nicht angeben, wird standardmäßig 1 (Open) übergeben. Dieser Parameter wird nur auf Unified Interface unterstützt.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

## <a name="remarks"></a>Rede

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) und [FileObject](../fileobject.md)


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
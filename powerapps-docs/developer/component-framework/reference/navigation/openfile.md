---
title: openFile | Microsoft Docs
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
ms.assetid: ae94e467-d12c-4a74-96f0-05a09e03c5f8
---
# <a name="openfile"></a>openFile

[!INCLUDE [openfile-description](includes/openfile-description.md)]

## <a name="syntax"></a>Syntax

`openFile(file, options)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Datei|`FileObject`|Ja|Ein Objekt, das die zu öffnende Datei beschreibt. FileObject hat folgende Attribute: <br/>- **fileContent**: `string`. Inhalt der Datei. <br/>- **fileName**: `string`. Name der Datei.<br/>- **fileSize**: `number`. Größe der Dateigröße in KB. <br/>- **mimeType**: `string`. Datei-MIME-Typ.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

## <a name="remarks"></a>Anmerkungen

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
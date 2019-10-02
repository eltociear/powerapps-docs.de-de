---
title: PickFile | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aae27c64-33c4-47f1-b833-4c04161c01e2
---

# <a name="pickfile"></a>pickFile

[!INCLUDE[./includes/pickfile-description.md](./includes/pickfile-description.md)]

## <a name="syntax"></a>Syntax

`pickFile(options)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|`options`|`object`|Nein|Datei mit zu wählenden Optionen|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<File[]>`

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)

## <a name="remarks"></a>Anmerkungen

Das `options`-Parameterobjekt bietet folgende Eigenschaften:

|Name|Typ|Beschreibung|
|--|--|--|
|`accept`|`string`|Auszuwählender Bilddateityp. Gültige Werte lauten "Audio ", "Video " oder "Bild"|
|`allowMultipleFiles`|`boolean`|Gibt an, ob die Auswahl mehrerer Dateien ermöglicht wird|
|`maximumAllowedFileSize`|`number`|Maximalgröße der Datei(en), die ausgewählt werden soll(en).|


### <a name="related-topics"></a>Verwandte Themen

[Gerät](../device.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
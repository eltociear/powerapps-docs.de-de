---
title: CaptureImage | Microsoft Docs
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
ms.assetid: 1d9c0063-add2-4002-acab-1be07ca1f6b6
---

# <a name="captureimage"></a>captureImage

[!INCLUDE[./includes/captureimage-description.md](./includes/captureimage-description.md)]

## <a name="syntax"></a>Syntax

`captureImage(options)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|`options`|`object`|Nein|Optionen für die Bilderfassung.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<FileObject>`

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)

## <a name="remarks"></a>Anmerkungen

Das `options`-Parameterobjekt bietet folgende Eigenschaften:

|Name|Typ|Beschreibung|
| ---|----|-----------|
|`allowEdit`|`boolean`|Bestimmt, ob das Bild vor dem Speichern zu bearbeiten ist|
|`height`|`number`|Höhe des zu erfassenden Bilds|
|`preferFrontCamera`|`boolean`|Bestimmt, ob das Bild mit der Frontkamera des Geräts aufzunehmen ist|
|`quality`|`number`|Qualität der Bilddatei in Prozent|
|`width`|`number`|Breite des zu erfassenden Bilds|


### <a name="related-topics"></a>Verwandte Themen

[Gerät](../device.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
---
title: Pickfile | Microsoft-Dokumentation
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
ms.assetid: aae27c64-33c4-47f1-b833-4c04161c01e2
ms.openlocfilehash: a36731edc7ee5cc8edede499fc791595bc00bc8c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344621"
---
# <a name="pickfile"></a>pickFile

[!INCLUDE[./includes/pickfile-description.md](./includes/pickfile-description.md)]

## <a name="syntax"></a>Syntax

`context.device.pickFile(options)`

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|`options`|`Object`|Nein|Optionen zum Auswählen der Datei.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<FileObject[]>`

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) und [FileObject](../fileobject.md)

## <a name="remarks"></a>Rede

Das `options` Parameter-Objekt verfügt über die folgenden Eigenschaften:

|Name|Typ|Beschreibung|
|--|--|--|
|`accept`|`String`|Bild Dateitypen, die ausgewählt werden sollen. Gültige Werte sind *auditon*, *Video*oder *Image*.|
|`allowMultipleFiles`|`Boolean`|Gibt an, ob mehrere Dateien ausgewählt werden sollen.|
|`maximumAllowedFileSize`|`Number`|Maximale Größe der Datei (en), die ausgewählt werden soll.|


### <a name="related-topics"></a>Verwandte Themen

[Schutz](../device.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
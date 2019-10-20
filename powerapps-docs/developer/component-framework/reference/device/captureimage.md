---
title: CaptureImage | Microsoft-Dokumentation
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
ms.assetid: 1d9c0063-add2-4002-acab-1be07ca1f6b6
ms.openlocfilehash: e642af17e02334b45041df87386885536e1810af
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345679"
---
# <a name="captureimage"></a>captureImage

[!INCLUDE[./includes/captureimage-description.md](./includes/captureimage-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.device.captureImage(options)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|`options`|`Object`|Nein|Optionen zum Erfassen des Bilds.|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise<FileObject>`

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) und [FileObject](../fileobject.md)

## <a name="remarks"></a>Rede

Das `options` Parameter-Objekt verfügt über die folgenden Eigenschaften:

|Name|Typ|Beschreibung|
| ---|----|-----------|
|`allowEdit`|`Boolean`|Gibt an, ob das Bild vor dem Speichern bearbeitet werden soll.|
|`height`|`Number`|Höhe des zu erfassenden Bilds.|
|`preferFrontCamera`|`Boolean`|Gibt an, ob ein Bild mithilfe der Vorderseite des Geräts erfasst werden soll.|
|`quality`|`Number`|Qualität der Bilddatei in Prozent.|
|`width`|`Number`|Breite des zu erfassenden Bilds.|


### <a name="related-topics"></a>Verwandte Themen

[Schutz](../device.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
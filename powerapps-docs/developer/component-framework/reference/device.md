---
title: Gerät | Microsoft-Dokumentation
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
ms.assetid: a0f9abc5-c605-4433-bf5a-f8253eeeda3b
ms.openlocfilehash: f4c8ce52907c5e49dcd782b51824ab3976ae3fcd
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025488"
---
# <a name="device"></a>Schutz

[!INCLUDE [device-description](includes/device-description.md)]

> [!IMPORTANT]
> Wenn Sie die Geräte-API-Methoden verwenden möchten, müssen Sie die Verwendung dieser Methode in der Manifest-Datei im Knoten [Funktions Verwendung](../manifest-schema-reference/feature-usage.md) deklarieren.

## <a name="syntax"></a>Syntax

`context.device`

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="methods"></a>Anzuwenden

|Anzuwenden | Beschreibung |
| ------------- |-------------|
|[captureaudiodatei](device/captureaudio.md)|[!INCLUDE [captureaudio-description](device/includes/captureaudio-description.md)]|
|[CaptureImage](device/captureimage.md)|[!INCLUDE [captureimage-description](device/includes/captureimage-description.md)]|
|[capturevideo](device/capturevideo.md)|[!INCLUDE [capturevideo-description](device/includes/capturevideo-description.md)]|
|[getbarcodevalue](device/getbarcodevalue.md)|[!INCLUDE [getbarcodevalue-description](device/includes/getbarcodevalue-description.md)]|
|[Navigatorobjekt](device/getcurrentposition.md)|[!INCLUDE [getcurrentposition-description](device/includes/getcurrentposition-description.md)]|
|[pickfile](device/pickfile.md)|[!INCLUDE [pickfile-description](device/includes/pickfile-description.md)]|

## <a name="example"></a>Beispiel

```TypeScript
 private onUploadButtonClick(event: Event): void {
    this._context.device.pickFile().then(this.processFile.bind(this), this.showError.bind(this));
  }
```

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
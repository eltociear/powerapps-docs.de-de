---
title: Verwendung von Features | Microsoft-Dokumentation
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
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
ms.openlocfilehash: 21e76a2a17910fe36967364f063ff2fc9b25e153
ms.sourcegitcommit: 63ea15e2f861d43333aacda19230cd8922d7bdfd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "72339630"
---
# <a name="feature-usage-element"></a>Feature-Usage-Element

Das Feature-Usage-Element fungiert als Wrapper um die `uses-feature` Elemente, die es Entwicklern ermöglichen, zu deklarieren, welche Funktionen von der Komponente verwendet werden sollen. Wenn keine use-Feature-Elemente definiert sind, ist das Feature-Usage-Element nicht erforderlich.

## <a name="available-for"></a>Verfügbar für

Modellgesteuerte Apps

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Verfügbar für|
|--|--|-----|
|[Verwendung-Feature](uses-feature.md)|Gibt an, welche Funktion Ihre Komponenten verwenden möchten.|Modellgesteuerte Apps|


## <a name="example"></a>Beispiel

```XML
<feature-usage>
    <uses-feature name="Device.captureAudio" required="true" />
    <uses-feature name="Device.captureImage" required="true" />
    <uses-feature name="Device.captureVideo" required="true" />
    <uses-feature name="Device.getBarcodeValue" required="true" />
    <uses-feature name="Device.getCurrentPosition" required="true" />
    <uses-feature name="Device.pickFile" required="true" />
    <uses-feature name="Utility" required="true" />
    <uses-feature name="WebAPI" required="true" />
 </feature-usage>
```

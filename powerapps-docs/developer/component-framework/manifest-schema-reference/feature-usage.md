---
title: feature-usage | Microsoft Docs
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
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
---

# <a name="feature-usage-element"></a>feature-usage-Element

Das feature-usage-Element fungiert als Wrapper um die `uses-feature`-Elemente, die es Entwicklern ermöglichen, selbst zu deklarieren, welche Features ihre Komponente verwenden möchte. Wenn keine uses-feature-Elemente definiert sind, ist das feature-usage-Element nicht erforderlich.

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[uses-feature](uses-feature.md)|Gibt an, welches Feature diese Komponenten verwenden möchten.|


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

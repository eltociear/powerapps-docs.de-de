---
title: Resources Element | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66599c2f-6651-4b27-92da-a38897acdfb5
---

# <a name="resources-element"></a>Ressource-Element

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [resources-description](includes/resources-description.md)]

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[Steuerelement](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Vorkommen|
|--|--|--|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|1 oder mehr|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|0 oder mehr|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|0 oder mehr|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|0 oder mehr|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|0 oder mehr|

## <a name="example"></a>Beispiel

```xml
<resources>
  <code path="JS_HelloWorldControl.js" order="1" />
<css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
```

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
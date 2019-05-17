---
title: Modus | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
---

# <a name="manifest-element"></a>Manifest-Element

[!INCLUDE [mode-description](includes/mode-description.md)]

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Vorkommen|
|--|--|--|
|[lesen](read.md)|[!INCLUDE [read-description](includes/read-description.md)]|1 oder mehr|
|[bearbeiten](edit.md)|[!INCLUDE [edit-description](includes/edit-description.md)]|0 oder mehr|
|[Container](container.md)|[!INCLUDE [property-description](includes/container-description.md)]|0 oder mehr|
|[Datensatz](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 oder mehr|
|[Ressource](resources.md)|[!INCLUDE [resource-description](includes/resources-description.md)]|1 oder mehr|

## <a name="example"></a>Beispiel

```xml
<?xml version="1.0" encoding="utf-8" ?>
<manifest>
    <control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0" display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key" control-type="standard">
        <property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
        <resources>
            <code path="JS_HelloWorldControl.js" order="1" />
            <css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
    </control>
</manifest>
```

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)

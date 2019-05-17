---
title: Typgruppen-Element | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec7c1ad4-b834-4755-8a04-2c8940f75674
---

# <a name="type-group-element"></a>Typ-Gruppen-Element

[!INCLUDE [type-group-description](includes/type-group-description.md)]

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name des Datentyps|`string`|Ja|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[Steuerelement](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|


## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Vorkommen|
|--|--|--|
|[type](type.md)|[!INCLUDE [type-description](includes/type-description.md)]|1 oder mehr|

### <a name="example"></a>Beispiel

```XML
<type-group name="numbers">
      <type>Whole.None</type>
      <type>Currency</type>
      <type>FP</type>
      <type>Decimal</type>
    </type-group>
```

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
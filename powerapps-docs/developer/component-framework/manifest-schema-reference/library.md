---
title: Bibliothekselement | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 90f2b4c9-7396-4ab9-bc9f-810189dc18b7
---

# <a name="library-element"></a>Bibliothekselement

[!INCLUDE [library-description](includes/library-description.md)]

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name der Bibliothek.|`string`|Ja|
|`version`|Die aktuelle Bibliotheksversion|Positive Ganzzahl|Ja|
|`order`|Die Reihenfolge, in der die Bibliotheksdateien geladen werden müssen|Positive Ganzzahl|Ja|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[Ressourcen](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Vorkommen|
|--|--|--|
|[packaged_library]||0 oder mehr|

## <a name="example"></a>Beispiel

```xml
<resources>
<library name="AngularJSCore" version=">=1" order="1">
<packaged_library path="libs/angular.min.js" version="1.5.8" />
</library>
  </resources>
```

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
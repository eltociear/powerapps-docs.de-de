---
title: Library-Element | Microsoft-Dokumentation
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
ms.assetid: 90f2b4c9-7396-4ab9-bc9f-810189dc18b7
ms.openlocfilehash: bd766864e6ef971b5245afad7d49af54b9369087
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346300"
---
# <a name="library-element"></a>Library-Element

[!INCLUDE [library-description](includes/library-description.md)]

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name der Bibliothek|`string`|Ja|
|`version`|Die aktuelle Bibliotheksversion|Positive ganze Zahl|Ja|
|`order`|Die Reihenfolge, in der die Bibliotheksdateien geladen werden sollen.|Positive ganze Zahl|Ja|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Alltag|
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

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
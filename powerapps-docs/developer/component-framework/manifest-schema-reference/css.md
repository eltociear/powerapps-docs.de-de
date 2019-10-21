---
title: CSS-Element | Microsoft-Dokumentation
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: b6119424-c0a4-4412-b25c-8239da6cbe36
ms.openlocfilehash: b7c96ba2bbb3e5d6d20df92e58ef0bc4005e7d37
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346576"
---
# <a name="css-element"></a>CSS-Element

[!INCLUDE [css-description](includes/css-description.md)]

## <a name="available-for"></a>Verfügbar für

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|Verfügbar für|
|--|--|--|--|-----|
|`path`|Relativer Pfad w. r. t-Manifest, in dem sich die CSS-Dateien befinden|`string`|Ja|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
|`order`|Die Reihenfolge, in der die CSS-Dateien geladen werden sollen.|`Positive integer`|Optionale|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>Beispiel

```xml
<css path="css/JS_HelloWorldControl.css" order="1" />
```

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)

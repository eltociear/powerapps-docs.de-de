---
title: Typgruppen Element | Microsoft-Dokumentation
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
ms.assetid: ec7c1ad4-b834-4755-8a04-2c8940f75674
ms.openlocfilehash: 7b09fad6097bb837c19116d59bb90afbde4d46b2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345978"
---
# <a name="type-group-element"></a>Type-Group-Element

[!INCLUDE [type-group-description](includes/type-group-description.md)]

## <a name="available-for"></a>Verfügbar für

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name des Datentyps|`string`|Ja|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|


## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Alltag|
|--|--|--|
|[Sorte](type.md)|[!INCLUDE [type-description](includes/type-description.md)]|1 oder mehr|


Type-Group bietet in dieser experimentellen Vorschauversion nur eingeschränkte Unterstützung für Canvas-apps. Folgende Probleme treten auf, wenn Sie versuchen, Komponenten zu importieren:

1. Wenn alle in der Typgruppe aufgeführten Typen kompatible JavaScript-Typen sind, versucht der Entwickler, die allgemeinste Option auszuwählen. Die Typen, die als kompatibel eingestuft werden, sind:
   - Zeichen folgen: Singleline. Text, Multiple, SingleLine. Textarea, SingleLine. Email, SingleLine. Phone, SingleLine. URL, SingleLine. Ticker.
   - Ziffern: Decimal, Floating Point, all. None, Currency.
   - Datumsangaben: DateAndTime. DateAndTime, DateAndTime. DATEONLY.

2. Wenn die in der Gruppe aufgeführten Typen nicht als kompatibel eingestuft werden, wird der Parameter als erster Typ behandelt, der in der Typgruppe aufgeführt ist.

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

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
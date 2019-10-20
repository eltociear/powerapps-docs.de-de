---
title: verwendet-Feature | Microsoft-Dokumentation
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
ms.openlocfilehash: fe4d384c8dd53fc0f9efcf5558252984a4be74a3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345886"
---
# <a name="uses-feature-element"></a>verwendet-Feature-Element

Gibt an, welche Funktion Ihre Komponenten verwenden möchten.

## <a name="available-for"></a>Verfügbar für

Modellgesteuerte Apps

## <a name="parent-element"></a>Übergeordnetes Element

|Element|Beschreibung|
|--|--|
|Verwendung von Features|Das Feature-Usage-Element fungiert als Wrapper für die Elemente der Verwendung von Features, die es Entwicklern ermöglichen, zu deklarieren, welche Funktionen von der Komponente verwendet werden sollen. Wenn keine use-Feature-Elemente definiert sind, ist das Feature-Usage-Element nicht erforderlich.|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Typ|Erforderlich|
|--|--|---|----|
|Benennen|Der Name der Funktion, die in der Komponente deklariert ist.|`string`|Ja|
|Erforderlich|Gibt an, ob die Komponente diese Funktion erfordert.|`boolean`|Ja|

### <a name="example"></a>Beispiel 

```XML
<feature-usage>
    <uses-feature name="WebAPI" required="true" />
</feature-usage>
```

In der folgenden Tabelle ist die Beziehung zwischen diesen Einstellungen und den im Code zur Laufzeit beschriebenen Aktionen dargestellt, unabhängig davon, ob die Funktions Funktion basierend auf den im Manifest definierten Einstellungen für Verwendungs Merkmale aufgerufen werden kann.

|Kundiger|Wenn der Host unterstützt|Wenn der Host nicht unterstützt|
|----|----|-----|
|`uses-feature name="device.captureImage" required=”true"`|`Context.device.captureImage != null`, keine Überprüfung erforderlich.|Warnung zur Entwurfszeit. Die Komponenten Auslastung kann zur Laufzeit nicht ausgeführt werden.|
|`uses-feature name="device.captureImage" required=”false"`|`Context.device.captureImage != null`|`Context.device.captureImage == null` kann die Komponente dies zur Laufzeit adaptiv überprüfen. |
|gar|`Context.device.captureImage == null` |`Context.device.captureImage == null` |

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
---
title: uses-feature | Microsoft Docs
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

# <a name="uses-feature-element"></a>uses-feature-Element

Gibt an, welches Feature diese Komponenten verwenden möchten.

## <a name="parent-element"></a>Parent-Element

|Element|Beschreibung|
|--|--|
|feature-usage|Das feature-usage-Element fungiert als Wrapper um die Use-Feature-Elemente, die es Entwicklern ermöglichen, selbst zu deklarieren, welche Features ihre Komponente verwenden möchte. Wenn keine uses-feature-Elemente definiert sind, ist das feature-usage-Element nicht erforderlich.|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|--|--|
|Name|Name des Features, das in der Komponente deklariert ist.|
|erforderlich|Gibt an, ob die Komponente dieses Feature erfordert oder nicht.|


### <a name="example"></a>Beispiel 

```XML
<feature-usage>
    <uses-feature name="WebAPI" required="true" />
</feature-usage>
```

Die folgende Tabelle zeigt das Verhältnis dieser Einstellungen zu dem, was zur Laufzeit im Code passiert, ob die Feature-Funktion basierend auf den im Manifest definierten Einstellungen der Use-Features aufgerufen werden kann.

|Manifest|Wenn der Host unterstützt|Wenn der Host keine Unterstützung bietet|
|----|----|-----|
|`uses-feature name="device.captureImage" required=”true"`|`Context.device.captureImage != null`, kein Check erforderlich.|Warnung zur Designzeit. Das Laden von Komponenten schlägt zur Laufzeit fehl.|
|`uses-feature name="device.captureImage" required=”false"`|`Context.device.captureImage != null`|`Context.device.captureImage == null` kann die Komponente dies zur Laufzeit adaptiv überprüfen. |
|(keine)|`Context.device.captureImage == null` |`Context.device.captureImage == null` |

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
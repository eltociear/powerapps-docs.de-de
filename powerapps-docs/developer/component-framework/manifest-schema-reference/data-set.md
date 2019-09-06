---
title: DataSet-Element | Microsoft Docs
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
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: 9ffe8930-b290-4252-98d4-a1195b00205f
---

# <a name="data-set-element"></a>Dataset-Element

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [data-set-description](includes/data-set-description.md)]

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`description-key`|Wird im Anpassungsbildschirm als lokalisierte Zeichenfolge verwendet, die die Beschreibung der Eigenschaft beschreibt.|`string`|Optional|
|`display-name-key`|Wird in den Anpassungsbildschirmen als lokalisierte Zeichenfolge verwendet, die den Namen der Eigenschaft beschreibt.|`string`|Ja|
|`name`|Name des Rasters.|`string`|Ja|
|`cds-data-set-options`|Zeigt die Commandbar, den ViewSelector und die QuickFindSearch an, wenn auf „true“ gesetzt |`boolean`|Ja|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[Steuerelement](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="example"></a>Beispiel

```xml
 <data-set name="dataSetGrid" display-name-key="DataSetGridProperty" cds-data-set-options="displayCommandBar:true;displayViewSelector:true;displayQuickFindSearch:true">
 </data-set>
```

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
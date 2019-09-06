---
title: Steuerelement | Microsoft Docs
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
ms.assetid: 4dacd337-c9df-458e-86f3-bfb3ab543ea7
---

# <a name="control-element"></a>Steuerelement

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [control-description](includes/control-description.md)]

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`namespace`|Definiert den Objektprototyp der Komponente|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Ja|
|`constructor`|Eine Möglichkeit für das Initialisieren des Objekts|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Ja|
|`control-type`|Standard|[!INCLUDE [controltype-description](includes/controltype-description.md)]|Nein|
|`description-key`|Wird in den Anpassungsbildschirmen als lokalisierte Zeichenfolge verwendet, die die Beschreibung der Eigenschaft beschreibt.|`string`|Nein|
|`display-name-key`|Wird in den Anpassungsbildschirmen als lokalisierte Zeichenfolge verwendet, die den Namen der Eigenschaft beschreibt.|`string`|Ja|
|`preview-image`|Bild, das auf Anpassungsbildschirmen verwendet wird, um dem Anpasser eine Vorschau der Komponente anzuzeigen|`string`|Nein|
|`version`|Definiert die Version der Komponente, die in [Semantische Versionsverwaltung](https://semver.org) definiert wurde|`string`|Ja|
|`hidden`|Definiert, ob die Komponente ausgeblendet werden soll oder nicht|[!INCLUDE [booleantype-description](includes/booleantype-description.md)]| Nein|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[Manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Vorkommen|
|--|--|--|
|[Datensatz](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 oder mehr|
|[Eigenschaft](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 oder mehr|
|[Ressourcen](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|1|
|[Typ-Gruppe](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 oder mehr|

## <a name="example"></a>Beispiel

```xml
<control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0"
 display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key"
 control-type="standard" preview-image="img/preview.png">
</control>
  ```

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
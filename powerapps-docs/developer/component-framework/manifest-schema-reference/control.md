---
title: Control-Element | Microsoft-Dokumentation
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
ms.assetid: 4dacd337-c9df-458e-86f3-bfb3ab543ea7
ms.openlocfilehash: aa02b89ce1e032a3cf2fdedca8f0fdf79cb84045
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346622"
---
# <a name="control-element"></a>Control-Element

[!INCLUDE [control-description](includes/control-description.md)]

## <a name="available-for"></a>Verfügbar für

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|Verfügbar für|
|--|--|--|--|--------|
|`namespace`|Definiert den Objekt Prototyp der Komponente.|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Ja|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
|`constructor`|Eine Methode zum Initialisieren des Objekts.|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|Ja|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
|`control-type`|Norm|[!INCLUDE [controltype-description](includes/controltype-description.md)]|Nein|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
|`description-key`|Definiert die Beschreibung der Komponente, die auf der Benutzeroberfläche angezeigt wird.|`string`|Nein|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
|`display-name-key`|Definiert den Namen des Steuer Elements, das auf der Benutzeroberfläche angezeigt wird.|`string`|Ja|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
|`preview-image`|Bild, das auf den Anpassungs Bildschirmen zum Anzeigen einer Vorschau der Komponente verwendet wird.|`string`|Nein|Modellgesteuerte Apps|
|`version`|Definiert die Version der Komponente, die in der [semantischen Versions](https://semver.org) Verwaltung definiert ist.|`string`|Ja|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
<!--|`hidden`|Definiert, ob die Komponente ausgeblendet werden soll oder nicht.|[!INCLUDE [booleantype-description](includes/booleantype-description.md)]| Nein|Modellgesteuerte Apps|-->

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Alltag|
|--|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0 oder mehr|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0 oder mehr|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|1|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0 oder mehr|

## <a name="example"></a>Beispiel

```xml
<control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0"
 display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key"
 control-type="standard" preview-image="img/preview.png">
</control>
  ```

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
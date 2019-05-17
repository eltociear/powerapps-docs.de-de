---
title: Eigenschaftensatz-Element | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 996f10e5-8057-40ea-9680-555e4cd682ff
---

# <a name="property-set-element"></a>Eigenschaftensatzelement

[!INCLUDE [property-set-description](includes/property-set-description.md)]

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name des Felds|`string`|Ja|
|`display-name-key`|Wird in Anpassungsbildschirmen als lokalisierte Zeichenfolge verwendet, die den Namen der Eigenschaft beschreiben.|`string`|Ja|
|`description-key`|Wird in Anpassungsbildschirmen als lokalisierte Zeichenfolge verwendet, die die Beschreibung der Eigenschaft beschreiben.|`string`|Optional|
|`of-type`|Definiert den Datentyp der Eigenschaft|Vgl. [Anmerkungen](#remarks)|Optional|
|`required`|Ob die Eigenschaft erforderlich ist oder nicht|`boolean`|Optional|
|`of-type-group`|Name der Typ-Gruppe, wie im Manifest definiert|`string`|Optional|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[Datensatz](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Vorkommen|
|--|--|--|
|[Typen](types.md)||0 oder mehr|

### <a name="remarks"></a>Anmerkungen

Der `of-type`-Attributwert muss einer der folgenden sein:

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)
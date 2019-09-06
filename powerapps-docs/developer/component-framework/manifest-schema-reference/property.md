---
title: Eigenschaften-Element | Microsoft Docs
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
ms.assetid: 45f4872d-c1d2-4c5a-8721-251b96ede370
---

# <a name="property-element"></a>Eigenschaftenelement

[!INCLUDE[cc-beta-prerelease-disclaimer](../../../includes/cc-beta-prerelease-disclaimer.md)]

[!INCLUDE [property-description](includes/property-description.md)]

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name der Eigenschaft.|`string`|Ja|
|`display-name-key`|Wird in den Anpassungsbildschirmen als lokalisierte Zeichenfolge verwendet, die den Namen der Eigenschaft beschreibt.|`string`|Ja|
|`of-type`|Definiert den Datentyp der Eigenschaft|Vgl. [Anmerkungen](#remarks)|Optional|
|`usage`|Das Verwendungsattribut erkannt, ob die Eigenschaft ein Entitätsattribut darstellen soll, dass die Komponente ändern kann (gebunden) oder schreibgeschützte Werte (Eingabe)|`bound` oder `input`|Optional|
|`required`|Ob die Eigenschaft erforderlich ist oder nicht|`boolean`|Optional|
|`of-type-group`|Name der Typ-Gruppe, wie im Manifest definiert|`string`|Optional|
|`description-key`|Wird in den Anpassungsbildschirmen als lokalisierte Zeichenfolge verwendet, die die Beschreibung der Eigenschaft beschreibt.|`string`|Optional|

### <a name="remarks"></a>Anmerkungen

Der `of-type`-Attributwert muss einer der folgenden sein:

[!INCLUDE [type-table](includes/type-table.md)]

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[Manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|


## <a name="example"></a>Beispiel

```xml
<property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" 
description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
```

### <a name="related-topics"></a>Verwandte Themen

[Schema-Referenz des PowerApps Komponenten-Frameworks](index.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../overview.md)

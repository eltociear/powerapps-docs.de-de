---
title: Property-Element | Microsoft-Dokumentation
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
ms.assetid: 45f4872d-c1d2-4c5a-8721-251b96ede370
ms.openlocfilehash: ee4e0b0259d5978f3e84757d4023827ada45f01e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346139"
---
# <a name="property-element"></a>Property-Element

[!INCLUDE [property-description](includes/property-description.md)]

## <a name="available-for"></a>Verfügbar für

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name der Eigenschaft|`string`|Ja|
|`display-name-key`|Wird in den Anpassungs Bildschirmen als lokalisierte Zeichen folgen verwendet, die den Namen der Eigenschaft beschreiben.|`string`|Ja|
|`of-type`|Definiert den Datentyp der Eigenschaft.|Siehe [Hinweise](#remarks)|Optionale|
|`usage`|Das Usage-Attribut gibt an, ob die-Eigenschaft ein Entitäts Attribut darstellen soll, das von der Komponente geändert (gebunden) werden kann, oder schreibgeschützte Werte (Eingabe).|`bound` oder `input`|Optionale|
|`required`|Gibt an, ob die Eigenschaft erforderlich ist oder nicht.|`boolean`|Optionale|
|`of-type-group`|Name der Typgruppe, wie im Manifest definiert|`string`|Optionale|
|`description-key`|Wird in den Anpassungs Bildschirmen als lokalisierte Zeichen folgen verwendet, die die Beschreibung der Eigenschaft beschreiben.|`string`|Optionale|
|`default-value`|Der Standard Konfigurations Wert, der für die Komponente bereitgestellt wird. In Modell gesteuerten Apps ist dieses Attribut nur bei Eingaben zulässig, da den gebundenen Parametern erwartet wird, dass ein Feld zugeordnet ist.|`string`|Optionale|

### <a name="remarks"></a>Rede

Der Wert des `of-type`-Attributs muss einer der folgenden sein:

[!INCLUDE [type-table](includes/type-table.md)]

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|


## <a name="example"></a>Beispiel

```xml
<property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" 
description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
```

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)

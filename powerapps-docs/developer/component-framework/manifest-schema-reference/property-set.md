---
title: Property Set-Element | Microsoft-Dokumentation
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
ms.assetid: 996f10e5-8057-40ea-9680-555e4cd682ff
ms.openlocfilehash: 98e0bcf7588e72f001e45471c87f0050dd0846ba
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346231"
---
# <a name="property-set-element"></a>Property-Set-Element

[!INCLUDE [property-set-description](includes/property-set-description.md)]

## <a name="available-for"></a>Verfügbar für

Modellgesteuerte Apps

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|
|--|--|--|--|
|`name`|Name des Felds|`string`|Ja|
|`display-name-key`|Wird in Anpassungs Bildschirmen als lokalisierte Zeichen folgen verwendet, die den Namen der Eigenschaft beschreiben.|`string`|Ja|
|`description-key`|Wird in Anpassungs Bildschirmen als lokalisierte Zeichen folgen verwendet, die die Beschreibung der Eigenschaft beschreiben.|`string`|Optionale|
|`of-type`|Definiert den Datentyp der Eigenschaft.|Siehe [Hinweise](#remarks)|Optionale|
|`required`|Gibt an, ob die Eigenschaft erforderlich ist.|`boolean`|Optionale|
|`of-type-group`|Name der Typgruppe, wie im Manifest definiert|`string`|Optionale|
|`usage`|Das Usage-Attribut gibt an, ob die-Eigenschaft ein Entitäts Attribut darstellen soll, das von der Komponente geändert (gebunden) werden kann, oder schreibgeschützte Werte (Eingabe).|`bound` oder `input`|Ja|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|

## <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|Alltag|
|--|--|--|
|[solche](types.md)||0 oder mehr|

### <a name="remarks"></a>Rede

Der Wert des `of-type`-Attributs muss einer der folgenden sein:

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
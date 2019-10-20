---
title: Image-Element | Microsoft-Dokumentation
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
ms.assetid: 0e776647-a4a2-42c9-85e8-62718154052f
ms.openlocfilehash: f3abd4f6a4061161a86d270f1bb4d0037632880c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346507"
---
# <a name="img-element"></a>IMG-Element

[!INCLUDE [img-description](includes/img-description.md)]

## <a name="available-for"></a>Verfügbar für

Modellgesteuerte Apps

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|Verfügbar für|
|--|--|--|--|-------|
|`path`|Relativer Pfad w. r. t-Manifest, in dem sich die Bilddateien befinden.|`string`|Ja|Modellgesteuerte Apps|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|


### <a name="example"></a>Beispiel

```XML
<img path="img/default.png" />
```

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
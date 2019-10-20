---
title: Code-Element | Microsoft-Dokumentation
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 44d9fcfb-0cd8-48cc-aace-dd589099dd79
ms.openlocfilehash: 2caf89a73dba006240c5bb6e8c874dfdd795d8c2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346645"
---
# <a name="code-element"></a>Code-Element

[!INCLUDE [code-description](includes/code-description.md)]

## <a name="available-for"></a>Verfügbar für

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="attributes"></a>Attribute

|Name|Beschreibung|Typ|Erforderlich|Verfügbar für|
|--|--|--|--|-----|
|`path`|Speicherort der Ressourcen Dateien|`String`|Ja|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|
|`order`|Die Reihenfolge, in der die Ressourcen Dateien geladen werden sollen.|`Positive integer`|Ja|Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau) (experimentelle Vorschau)|

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

### <a name="example"></a>Beispiel

```XML
<code path="TS_IncrementControl.js" order="1" />
        <css path="css/TS_IncrementControl.css" order="1" />
      <resx path="strings/TSIncrementControl.1033.resx" version="1.0.0" />
```

### <a name="related-topics"></a>Verwandte Themen

[Schema Referenz für das powerapps-Komponenten Framework](index.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
---
title: Lookupobjects | Microsoft-Dokumentation
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
ms.assetid: d213b401-cfc4-44df-b55c-f040fb6d7072
ms.openlocfilehash: 0dca29df3537389decefe2584d2fc931cea8979c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341148"
---
# <a name="lookupobjects"></a>lookupObjects

[!INCLUDE [lookupobjects-description](includes/lookupobjects-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.utils.lookupObjects(lookupOptions)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|LookupOptions|`UtilityApi.LookupOptions`|Ja|Definiert die Optionen zum Öffnen des Such Dialogfelds. Die lookupoptions-Option verfügt über die folgenden Attribute:<br/>- **AllowMultiSelect**: `Boolean`. Gibt an, ob die Suche zulässt, dass mehrere Elemente ausgewählt werden.<br/>- **defaultentitytype**: `String`. Der zu verwendende Standard Entitätstyp.<br/>- **defaultviewid**: `String`. Die zu verwendende Standardansicht.<br/>- **EntityTypes**: `String[]`. Die anzuzeigenden Entitäts Typen.<br/>- **viewids**: `String[]`. Die Ansichten, die in der Ansichts Auswahl verfügbar sein sollen. Nur System Sichten werden unterstützt (keine Benutzer Sichten).|

## <a name="return-value"></a>Rückgabewert

Typ: [Promise](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) <[EntityReference](../entityreference.md)[] >


### <a name="related-topics"></a>Verwandte Themen

[Utility](../utility.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
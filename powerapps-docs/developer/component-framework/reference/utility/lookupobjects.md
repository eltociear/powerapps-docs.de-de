---
title: lookupObjects | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d213b401-cfc4-44df-b55c-f040fb6d7072
---

# <a name="lookupobjects"></a>lookupObjects

[!INCLUDE [lookupobjects-description](includes/lookupobjects-description.md)]

## <a name="syntax"></a>Syntax

`lookupObjects(lookupOptions)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|lookupOptions|`UtilityApi.LookupOptions`|Ja|Optionen zum Öffnen des Suchdialogs. LookupOptions hat die folgenden Attribute:<br/>- **allowMultiSelect**: `boolean`. Ob die Suche mehr als ein ausgewähltes Element erlaubt.<br/>- **defaultEntityType**: `string`. Der Standardentitätstyp.<br/>- **defaultViewId**: `string`. Die zu verwendende Standardansicht<br/>- **entityTypes**: `string[]`. Die anzuzeigenden Entitätstypen.<br/>- **viewIds**: `string[]`. Die Ansichten die in der Ansichtsauswahl verfügbar sein sollen. Nur Systemansichten werden unterstützt (keine Benutzeransichten).|

## <a name="return-value"></a>Rückgabewert

Typ: `Promise`

Siehe [Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) und [Datei](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>Verwandte Themen

[Hilfsprogramm](../utility.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
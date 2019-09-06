---
title: openUrl | Microsoft Docs
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
ms.assetid: 590078f3-c604-4bd0-ac74-9cf6d8806802
---

# <a name="openurl"></a>openUrl

[!INCLUDE [openurl-description](includes/openurl-description.md)]

## <a name="syntax"></a>Syntax

`openUrl(url, options)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|URL|`string`|Ja|Zu öffnende URL.|
|Optionen|`OpenUrlOptions`|Ja|Fensteroptionen für die URL. OpenUrlOptions hat folgende Parameter: <br/>- **height**: `number`. Höhe des Fensters zum Anzeigen der resultierenden Seite in Pixeln.<br/>- **width**: `number`. Breite des Fensters zum Anzeigen der resultierenden Seite in Pixeln.|


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
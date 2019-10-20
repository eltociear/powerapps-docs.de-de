---
title: OpenURL | Microsoft-Dokumentation
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
ms.assetid: 590078f3-c604-4bd0-ac74-9cf6d8806802
ms.openlocfilehash: 21e097c739364b6cdb3935654ae9bf2b61143a06
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342275"
---
# <a name="openurl"></a>openUrl

[!INCLUDE [openurl-description](includes/openurl-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.navigation.openUrl(url, options)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Urne|`string`|Ja|Die URL, die geöffnet werden soll.|
|Optionen|`OpenUrlOptions`|Nein|Optionen zum Öffnen der URL. Openurloptions verfügt über die folgenden Parameter: <br/>- **Höhe**: `Number`. Höhe des Fensters, um die resultierende Seite in Pixel anzuzeigen.<br/>- **Breite**: `Number`. Breite des Fensters, in dem die resultierende Seite in Pixel angezeigt werden soll.|


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
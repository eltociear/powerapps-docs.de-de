---
title: Openwebresource | Microsoft-Dokumentation
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
ms.assetid: 27a1e54c-71fe-450f-8f84-b4cc125970bf
ms.openlocfilehash: 577c26dd87149fabebafe32b77395029ef4df335
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342252"
---
# <a name="openwebresource"></a>openWebResource

[!INCLUDE [openwebresource-description](includes/openwebresource-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="syntax"></a>Syntax

`context.navigation.openWebResource(name, options, data)`

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Benennen|`String`|Ja|Der Name der HTML-Webressource, die geöffnet werden soll.|
|Optionen|`OpenWebResourceOptions`|Nein|Fenster Optionen zum Öffnen der Webressource. Openwebresourceoptions verfügt über die folgenden Attribute:<br/>- **Höhe**: `Number`. Höhe des Fensters, um die resultierende Seite in Pixel anzuzeigen.<br/>- **Breite**: `Number`. Breite des Fensters, in dem die resultierende Seite in Pixel angezeigt werden soll.<br/>- **OpenInNewWindow**: `Boolean`. Gibt an, ob die Webressource in einem neuen Fenster geöffnet werden soll.|
|Vorrats|`String`|Nein|An den Daten Parameter zu über gebenden Daten.

### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
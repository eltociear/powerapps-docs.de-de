---
title: openWebResource | Microsoft Docs
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
ms.assetid: 27a1e54c-71fe-450f-8f84-b4cc125970bf
---

# <a name="openwebresource"></a>openWebResource

[!INCLUDE [openwebresource-description](includes/openwebresource-description.md)]

## <a name="syntax"></a>Syntax

`openWebResource(name, options, data)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Name|`string`|Ja|Der Name der zu öffnenden HTML-Webressource.|
|Optionen|`OpenWebResourceOptions`|Ja|Fensteroptionen für die Webressource. OpenWebResourceOptions hat die folgenden Attribute:<br/>- **height**: `number`. Höhe des Fensters zum Anzeigen der resultierenden Seite in Pixeln.<br/>- **width**: `number`. Breite des Fensters zum Anzeigen der resultierenden Seite in Pixeln.<br/>- **openInNewWindow**: `boolean`. ob die Webressource in einem neuen Fenster geöffnet wird.|
|-Daten|`string`|Nein|Daten, die in den Datenparameter übergeben werden.


### <a name="related-topics"></a>Verwandte Themen

[Navigation](../navigation.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
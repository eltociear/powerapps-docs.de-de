---
title: formatTime | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 148964b5-106e-4f2e-8038-9086d29dc54f
---

# <a name="formattime"></a>formatTime

[!INCLUDE [formattime-description](includes/formattime-description.md)]

## <a name="syntax"></a>Syntax

`formatTime(value, behavior)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|Wert|`Date`|Ja|Das zu formatierende Datum.|
|Verhalten|`DateTimeFieldBehavior`|Ja|Die Verhaltensweisen des Datum-Zeit-Objekts, das formatiert werden sollen. Für `DateTimeFieldBehavior` gelten die folgenden Attribute:<br/>- `None =0`: Unbekanntes DatumTime-Verhalten <br/>- `UserLocal =1`: Lokale Zeitzone für den Benutzer respektieren Datumsangaben als UTC gespeichert<br/>- `TimeZoneIndependent =3`: Datum und Uhrzeit ohne Konvertierung zu UTC gespeichert|

## <a name="return-value"></a>Rückgabewert

Typ: `string`


### <a name="related-topics"></a>Verwandte Themen

[Formatierung](../formatting.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
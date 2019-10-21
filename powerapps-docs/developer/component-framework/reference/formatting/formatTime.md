---
title: FormatTime | Microsoft-Dokumentation
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
ms.assetid: 148964b5-106e-4f2e-8038-9086d29dc54f
ms.openlocfilehash: cc2c7dfdbe9952d69dcda9fdd4c813965f539478
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72343333"
---
# <a name="formattime"></a>formatTime

[!INCLUDE [formattime-description](includes/formattime-description.md)]

## <a name="syntax"></a>Syntax

`context.formatting.formatTime(value, behavior);`

## <a name="available-for"></a>Verfügbar für 

Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau)

## <a name="parameters"></a>Metern

| Parameter Name|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|value|`Date`|Ja|Das zu formatierende Datum.|
|Verhalten|`DateTimeFieldBehavior`|Ja|Das Verhalten des DateTime-Objekts, das formatiert werden soll. Der `DateTimeFieldBehavior` verfügt über die folgenden Attribute:<br/>-  `None =0`: Unbekanntes DateTime-Verhalten <br/>-  `UserLocal =1`: Beachten Sie die Ortszeit des Benutzers. Als UTC gespeicherte Datumsangaben<br/>-  `TimeZoneIndependent =3`: Datums-und Uhrzeitangaben ohne Konvertierung in UTC|

## <a name="return-value"></a>Rückgabewert

Typ: `string`


### <a name="related-topics"></a>Verwandte Themen

[Formatierung](../formatting.md)<br/>
[API-Referenz für das powerapps-Komponenten Framework](../../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../../overview.md)
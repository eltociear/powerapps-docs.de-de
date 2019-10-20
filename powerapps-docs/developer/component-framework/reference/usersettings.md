---
title: UserSettings | Microsoft-Dokumentation
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
ms.assetid: c237ff96-9268-4068-9d61-aea0bdc79fc2
ms.openlocfilehash: 5325091d8f82ffd98cfc4e5fdab4e0228a5d541e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341033"
---
# <a name="usersettings"></a>UserSettings

[!INCLUDE [usersettings-description](includes/usersettings-description.md)]

## <a name="available-for"></a>Verfügbar für 

Modellgesteuerte Apps

## <a name="properties"></a>Eigenschaften

### <a name="dateformattinginfo"></a>dateformattinginfo

Datums Formatierungsinformationen, die vom Server abgerufen werden.

**Type**: [dateformattinginfo](dateformattinginfo.md)

### <a name="isrtl"></a>isrtl

Gibt true zurück, wenn die Sprache von rechts nach links ist.

**Typ**: `boolean`

### <a name="languageid"></a>LanguageID

Die Sprach-ID des aktuellen Benutzers.

**Typ**: `number`

### <a name="numberformattinginfo"></a>numformattinginfo

Zahlen Formatierungsinformationen, die vom Server abgerufen werden.

**Typ**: [numformattinginfo](numberformattinginfo.md)

### <a name="securityroles"></a>securityrollen

Aktuelle Benutzer Rollen.

**Typ**: `string[]`

### <a name="userid"></a>UserID

Die ID des aktuellen Benutzers.

**Typ**: `string`

### <a name="username"></a>userName

Der Benutzername des aktuellen Benutzers.

**Typ**: `string`

## <a name="methods"></a>Anzuwenden

|Anzuwenden | Beschreibung | 
| ------|-------------|
|[gettimezoneoffsetminutes](usersettings/gettimezoneoffsetminutes.md)|[!INCLUDE [gettimezoneoffsetminutes-description](usersettings/includes/gettimezoneoffsetminutes-description.md)]|

### <a name="related-topics"></a>Verwandte Themen

[API-Referenz für das powerapps-Komponenten Framework](../reference/index.md)<br/>
[Übersicht über das powerapps-Komponenten Framework](../overview.md)
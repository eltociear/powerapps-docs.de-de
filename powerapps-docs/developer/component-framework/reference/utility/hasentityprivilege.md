---
title: hasEntityPrivilege | Microsoft Docs
description: null
keywords: null
ms.author: nabuthuk
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
ms.assetid: f22723f0-c606-465c-abba-0a8c46a10e32
---

# <a name="hasentityprivilege"></a>hasEntityPrivilege

[!INCLUDE [hasentityprivilege-description](includes/hasentityprivilege-description.md)]

## <a name="syntax"></a>Syntax

`hasEntityPrivilege(entityTypeName, privilegeType, privilegeDepth)`

## <a name="parameters"></a>Parameter

| Parametername|Typ|Erforderlich|Beschreibung|
| ------------- |----|--------|-----------|
|entityTypeName|`string`|Ja|Entitätentypname|
|privilegeType|`enum`|Nein|Entitätsrechttypen. Es hat die folgenden Attribute:<br/>- `None =1`<br/>- `Create =1` <br/>- `Read =2`<br/>- `Write =3`<br/>- `Delete =4`<br/>- `Assign =5`<br/>- `Share =6`<br/>- `Append =7`<br/>- `AppendTo =8`|
|privilegeDepth|`enum`|Nein|Entitätsrechttiefe. Es hat das folgende Attribut: <br/>- `None =-1`<br/>- `Basic =0`<br/>- `Local =1`<br/>- `Deep =2`<br/>- `Global =3`|

## <a name="return-value"></a>Rückgabewert

**Typ**: `boolean`

### <a name="related-topics"></a>Verwandte Themen

[Hilfsprogramm](../utility.md)<br/>
[PowerApps-Komponentenframework-API-Referenz](../../reference/index.md)<br/>
[Übersicht über das PowerApps-Komponentenframework](../../overview.md)
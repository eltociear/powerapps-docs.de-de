---
title: getShowTime (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 43341b96-ca2c-4c7e-b6d5-fe7a5fd3c8b2
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getshowtime-client-api-reference"></a>getShowTime (Client-API-Referenz)



Dient zum Abrufen, ob ein Datumssteuerelement den Zeitteil des Datums anzeigt. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Standardsteuerelement für **datetime**-Attribute.

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getShowTime();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Beschreibung**: true, wenn der Zeitteil des Datums angezeigt wird, sonst false.

### <a name="related-topics"></a>Verwandte Themen

[setShowTime](setShowTime.md)


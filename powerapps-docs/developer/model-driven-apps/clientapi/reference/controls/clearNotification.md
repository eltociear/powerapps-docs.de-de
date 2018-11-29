---
title: clearNotification (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 4d025f92-db16-440c-9f82-e40d71e09862
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="clearnotification-client-api-reference"></a>clearNotification (Client-API-Referenz)



Entfernt eine Nachricht, die bereits für ein Steuerelement angezeigt wird.

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).clearNotification(uniqueId);`

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|uniqueId |String |No|Die ID wird zum Löschen einer bestimmten Meldung, die bei Verwendung von **setNotification** oder **addNotification** gesetzt wurde, verwendet. Wenn der **uniqueId**-Parameter nicht festgelegt ist, wird die aktuell angezeigte Benachrichtigung entfernt.| 


## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch 

**Beschreibung**: Gibt an, ob die Methode erfolgreich war. 

### <a name="related-topics"></a>Verwandte Themen

[addNotification](addNotification.md)

[setNotification](setNotification.md)
---
title: setNotification (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
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
# <a name="setnotification-client-api-reference"></a>setNotification (Client-API-Referenz)



Zeigt eine Fehlermeldung für das Steuerelement an, um anzugeben, dass Daten ungültig sind. Wenn diese Methode verwendet wird, erscheint ein rotes „X“-Symbol neben dem Steuerelement. Bei mobilen Dynamics 365-Clients wird die Meldung angezeigt, indem Sie auf das Symbol tippen. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Alle

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).setNotification(message,uniqueId);`

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|Meldung |String |Ja|Die angezeigte Meldung.| 
|uniqueId |String |No|Die zum Löschen dieser Nachricht zu verwendende ID, wenn die **clearNotification**-Methode angewendet wird.
| | |

## <a name="return-value"></a>Rückgabewert
**Typ**: Boolesch 

**Beschreibung**: Gibt an, ob die Methode erfolgreich war.

## <a name="remarks"></a>Anmerkungen

Das Festlegen einer Fehlermeldung für ein Steuerelement blockiert das Speichern des Formulars.

### <a name="related-topics"></a>Verwandte Themen

[addNotification](addNotification.md)

[clearNotification](clearNotification.md)
---
title: setShowTime (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 77999c82-3d6a-4db9-af9c-7322491768d9
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setshowtime-client-api-reference"></a>setShowTime (Client-API-Referenz)



Geben Sie an, ob ein Datumssteuerelement den Zeitteil des Datums anzeigen soll. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Standardsteuerelement für **datetime**-Attribute.

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).setShowTime(bool);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|bool|Boolean|Ja|Festlegen, um den Zeitteil des Datums anzuzeigen, sonst false.|

## <a name="remarks"></a>Anmerkungen

Diese Methode zeigt oder verbirgt die Zeitkomponente eines Datumssteuerelements, wobei das Attribut das **DateAndTime**-Format verwendet. Diese Methode hat keine Auswirkungen, wenn das Format **DateOnly** verwendet wird.

### <a name="related-topics"></a>Verwandte Themen

[getShowTime](getShowTime.md)


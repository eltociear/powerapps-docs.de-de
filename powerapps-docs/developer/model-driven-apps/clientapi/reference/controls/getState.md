---
title: getState (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 199d1344-351a-44ee-8c43-f6b00b85a793
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getstate-client-api-reference"></a>getState (Client-API-Referenz)



Gibt den Status des Zeitgeber-Steuerelements zurück.

Diese Methode wird nur für [Einheitliche Oberfläche](/dynamics365/get-started/whats-new/customer-engagement/new-in-july-2017-update#unified-interface-framework-for-new-apps) unterstützt. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Zeitgeber

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getState();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Anzahl

**Beschreibung**: Gibt einen der folgenden Werte zurück:

|Value | Zustand |
|--|--|
|1 | Nicht festgelegt|
|2 | In Bearbeitung|
|3 | Warnung|
|4 | Verletzt|
|5 | Erfolgreich|
|6 | Abgelaufen|
|7 | Storniert|
|8 | Angehalten|

### <a name="related-topics"></a>Verwandte Themen

[Steuerelemente](../controls.md)

---
title: clearFormNotification (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 6c57db71-a76d-404c-852e-9c36a1c549ee
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="clearformnotification-client-api-reference"></a>clearFormNotification (Client-API-Referenz)



[!INCLUDE[./includes/clearFormNotification-description.md](./includes/clearFormNotification-description.md)]

## <a name="syntax"></a>Syntax

`formContext.ui.clearFormNotification(uniqueId)`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|uniqueId|String|Ja|Ein eindeutiger Bezeichner für die zu löschende Nachricht, die mit der [setFormNotification](setFormNotification.md)-Methode gesetzt wurde.|

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch

**Bezeichnung**: true, wenn die Methode erfolgreich ist, ansonsten false. 


### <a name="related-topics"></a>Verwandte Themen

[setFormNotification](setFormNotification.md)

[formContext.ui](../formContext-ui.md)

[formContext](../../clientapi-form-context.md)


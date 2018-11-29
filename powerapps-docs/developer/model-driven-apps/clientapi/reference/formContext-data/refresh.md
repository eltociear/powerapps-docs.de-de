---
title: refresh (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 03e970ee-7ed3-4df2-9670-222d76a479fd
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="refresh-client-api-reference"></a>refresh (Client-API-Referenz)



[!INCLUDE[./includes/refresh-description.md](./includes/refresh-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.refresh(save).then(successCallback, errorCallback);`

## <a name="parameter"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|Speichern|Boolean|No|true, wenn die Daten gespeichert werden sollen, nachdem sie aktualisiert wurden, andernfalls false.|
|successCallback|Funktion|No|Eine Funktion zum Aufrufen, wenn der Vorgang erfolgreich war.|
|errorCallback|Funktion|No|Eine Funktion zum Aufrufen, wenn der Vorgang fehlschlug.|

### <a name="related-topics"></a>Verwandte Themen

[formContext](../../clientapi-form-context.md)


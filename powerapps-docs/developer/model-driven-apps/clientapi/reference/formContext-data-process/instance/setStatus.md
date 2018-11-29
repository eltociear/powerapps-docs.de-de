---
title: setStatus (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 649fe7b0-016d-409f-ba3c-b14e0f1953e0
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setstatus-client-api-reference"></a>setStatus (Client-API-Referenz)



[!INCLUDE[./includes/setStatus-description.md](./includes/setStatus-description.md)]

## <a name="syntax"></a>Syntax

`formContext.data.process.setStatus(status, callbackFunction);`

## <a name="parameters"></a>Parameter

|Name|Typ|Erforderlich|Beschreibung|
|--|--|--|--|
|Status|String|Ja|Der neue Status. Die Werte können **aktiv**, **abgebrochen** oder **fertig** sein.|
|callbackFunction|Funktion|No|Eine Funktion, die aufgerufen wird, wenn der Vorgang abgeschlossen ist. Dieser Rückruffunktion wird der Status als neuer Zeichenfolgenwert übergeben.|

**Typ:**: Zeichenfolge. 

**Beschreibung**: Gibt einen der folgenden Werte zurück: **aktiv**, **abgebrochen** oder **abgeschlossen**.

### <a name="related-topics"></a>Verwandte Themen

[formContext.data.process](../../formContext-data-process.md)
 



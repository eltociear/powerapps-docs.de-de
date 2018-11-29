---
title: isDefaultPrevented (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 9a8802ad-80aa-4386-a192-573280587546
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="isdefaultprevented-client-api-reference"></a>isDefaultPrevented (Client-API-Referenz)



[!INCLUDE[./includes/isDefaultPrevented-description.md](./includes/isDefaultPrevented-description.md)]

## <a name="syntax"></a>Syntax

`executionContext.getEventArgs().isDefaultPrevented();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Boolesch.

**Beschreibung**: **true** wenn das Speichern-Ereignis storniert wurde, da die preventDefault Methode verwendet wurde; Andernfalls **false**.


### <a name="related-topics"></a>Verwandte Themen

[getSaveMode](getSaveMode.md)

[preventDefault](preventDefault.md)


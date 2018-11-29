---
title: getEntityTypes (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: c20ba958-821f-4168-a518-e39431603b28
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getentitytypes-client-api-reference"></a>getEntityTypes (Client-API-Referenz)



Ruft die Typen von Entitäten aus, die im Suchsteuerelement zulässig sind. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suchsteuerelement

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getEntityTypes();`

## <a name="return-value"></a>Rückgabewert

**Typ**: Zeichenfolgenarray

**Beschreibung**: Die logischen Namen der Entitäten, die in diesem Steuerelement zulässig sind.

### <a name="related-topics"></a>Verwandte Themen

[setEntityTypes](setEntityTypes.md)

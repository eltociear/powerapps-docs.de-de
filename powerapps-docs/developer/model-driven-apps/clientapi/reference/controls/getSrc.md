---
title: getSrc (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: e003d21f-393a-4681-a6fc-256949167fcc
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getsrc-client-api-reference"></a>getSrc (Client-API-Referenz)



Gibt die aktuelle URL zurück, die in einem IFRAME oder einer Webressource angezeigt wird. 

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

IFrame, Webressource

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).getSrc();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Zeichenfolge

**Beschreibung**: Eine URL, die die **src**-Eigenschaft des IFRAMEs oder der Webressource darstellt.

### <a name="related-topics"></a>Verwandte Themen

[setSrc](setSrc.md)


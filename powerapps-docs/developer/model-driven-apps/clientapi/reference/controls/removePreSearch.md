---
title: removePreSearch (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 2451c4ac-527c-4487-8f52-bde1690c5bde
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="removepresearch-client-api-reference"></a>removePreSearch (Client-API-Referenz)



Entfernt Ereignishandlerfunktionen, die zuvor für das [PreSearch](../events/PreSearch.md)-Ereignis festgelegt wurden.

## <a name="control-types-supported"></a>Unterstützter Steuerelementtypen

Suche

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).removePreSearch(myFunction)`

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja| Die Funktion zum Entfernen. Der [Ausführungskontext](../../clientapi-execution-context.md) wird automatisch bei der ersten der zu den Funktionen übergeben, die mithilfe des Codes festgelegt wird.|

### <a name="related-topics"></a>Verwandte Themen

[PreSearch-Ereignis](../events/PreSearch.md)

[addPreSearch](addPreSearch.md) 



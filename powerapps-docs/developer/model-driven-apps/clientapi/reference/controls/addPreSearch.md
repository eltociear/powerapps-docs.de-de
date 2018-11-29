---
title: addPreSearch (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: d69a432a-1d74-4782-bedd-f9f30d3d7d9c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="addpresearch-client-api-reference"></a>addPreSearch (Client-API-Referenz)



Wendet Änderungen für Suchen basierend auf aktuellen Werten an, wenn dem Benutzer Ergebnisse der Suche angezeigt werden.

## <a name="control-types-supported"></a>Unterstützte Steuerelementtypen

Suche

## <a name="syntax"></a>Syntax

`formContext.getControl(arg).addPreSearch(myFunction)`

## <a name="parameters"></a>Parameter

|Name | Typ | Erforderlich | Beschreibung|
|--|--|--|--|
|myFunction |Funktion |Ja| Das ist eine Funktion, die kurz vor Suche ausgeführt wird, um Ergebnisse für eine Suche bereitzustellen. Sie können diese Funktion verwenden, um eine der anderen Suchsteuerelementfunktionen aufzurufen und die in der Suche anzuzeigenden Ergebnisse zu optimieren. Der [Ausführungskontext](../../clientapi-execution-context.md) wird automatisch bei der ersten der zu den Funktionen übergeben, die mithilfe des Codes festgelegt wird.|

### <a name="related-topics"></a>Verwandte Themen

[PreSearch-Ereignis](../events/PreSearch.md)

[removePreSearch](removePreSearch.md) 



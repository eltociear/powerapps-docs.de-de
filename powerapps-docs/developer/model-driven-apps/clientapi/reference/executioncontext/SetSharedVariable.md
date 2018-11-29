---
title: setSharedVariable (Client-API-Referenz) in modellgestützten Apps | MicrosoftDocs
description: 'Infos zur getEventSource Methode, die einen Verweis auf das Formular oder ein Element auf dem Formular zurückgibt, je nachdem, von wo die Methode aufgerufen wurde.'
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 702a13c1-f4ae-4de2-9e8b-95360ad9240c
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="setsharedvariable-client-api-reference"></a>setSharedVariable (Client-API-Referenz)



Legt den Wert für eine Variable fest, die von einem Handler verwendet werden kann, nachdem der aktuelle Handler seine Ausführung beendet.

## <a name="syntax"></a>Syntax

`ExecutionContextObj.setSharedVariable(key, value)`

## <a name="parameters"></a>Parameter

- **Schlüssel**: Zeichenfolge: Der Name der Variable
- **Wert**: Objekt. Die einzustellenden Werte



## <a name="return-value"></a>Rückgabewert

**Typ:**: Objekt.

**Description**: Der verfügbare Typ hängt davon ab, was das Wertobjekt ist.

### <a name="related-topics"></a>Verwandte Themen
[getSharedVariable](getSharedVariable.md)

[Context-Ausführungen](../execution-context.md)






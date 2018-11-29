---
title: getSharedVariable (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
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
# <a name="getsharedvariable-client-api-reference"></a>getSharedVariable (Client-API-Referenz)



Ruft eine Variable ab, die mithilfe von [setSharedVariable](setSharedVariable.md) festgelegt wurde.

## <a name="syntax"></a>Syntax

`ExecutionContextObj.getSharedVariable(key)`

## <a name="parameters"></a>Parameter

**key**

   **Typ:**: Zeichenfolge

   **Beschreibung**: Der Name der Variable.

## <a name="return-value"></a>Rückgabewert

**Typ:**: Objekt.

**Description**: Der verfügbare Typ hängt davon ab, was das Wertobjekt ist.

### <a name="related-topics"></a>Verwandte Themen
[setSharedVariable](setSharedVariable.md)

[Context-Ausführungen](../execution-context.md)






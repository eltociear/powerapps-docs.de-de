---
title: getActiveProcess (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: a977a250-b79f-4c88-a6af-776350b110f7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="getactiveprocess-client-api-reference"></a>getActiveProcess (Client-API-Referenz)



[!INCLUDE[./includes/getActiveProcess-description.md](./includes/getActiveProcess-description.md)]

## <a name="syntax"></a>Syntax

`var activeProcess = formContext.data.process.getActiveProcess();`

## <a name="return-value"></a>Rückgabewert

**Typ:**: Prozess. 

**Beschreibung**: Der derzeit aktive Prozess. Informationen zu den Methoden, um auf die Eigenschaften des zurückgegebenen Prozesses zuzugreifen finden Sie unter [Prozessmethoden](../../formContext-data-process.md#process-methods).

### <a name="related-topics"></a>Verwandte Themen

[setActiveProcess)](setActiveProcess.md)

[formContext.data.process](../../formContext-data-process.md)
 



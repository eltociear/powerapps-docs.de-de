---
title: OnStageChange-Ereignis (Client-API-Referenz) in modellgestützten Apps| MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 0c85fe34-1368-4d0d-87eb-4109206ce4f7
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="onstagechange-event-client-api-reference"></a>OnStageChange-Ereignis (Client-API-Referenz)



Dieses Ereignis tritt auf, wenn die Geschäftsprozessflusssteuerung geändert wird. Dieses Ereignis tritt auf, wenn der Benutzer auf die Schaltflächen **Nächste Phase** oder **Zurück zur vorherigen Phase** auf der Benutzeroberfläche klickt, oder wenn ein Entwickler die `formContext.data.process.moveNext` oder `formContext.data.process.movePrevious`-Methode verwendet. Sie können die Phasenänderung nicht mithilfe von Code in einem Handler für dieses Ereignis abbrechen.

Ein Ausführungskontextobjekt wird an den Ereignishandlern für dieses Ereignis übergeben. Sie können die [getEventArgs](../executioncontext/getEventArgs.md)-Methode verwenden, um ein Objekt abzurufen, das über die folgenden Methoden verfügt:
- **getDirection**: Gibt eine Zeichenfolge zurück, die entweder "Weiter" oder "Zurück" ist, um die Richtung der Phasenänderung anzuzeigen.
- **getStage**: Gibt ein Phasenobjekt zurück. Ausßer wenn die Navigation zu einer neuen Entität weitergeht, repräsentiert die zurückgegebene Phase das Zielphasenobjekt, d. h. die nächste aktive Phase. Wenn die Navigation zu einer neuen Entität weitergeht, ist die Phase die Phase, vob der navigiert wird, d. h. das vorige aktive Phasenobjekt. Weitere Informationen: [Phasenmethoden](../formContext-data-process.md#stage-methods).

## <a name="methods-supported-for-this-event"></a>Unterstütze Möglichkeiten für das Ereignis
- **formContext.data.process**.[addOnStageChange](../formcontext-data-process/eventhandlers/addOnStageChange.md)-Methode, um Ereignishandler für das Ereignis hinzuzufügen.
- **formContext.data.process**.[removeOnStageChange](../formcontext-data-process/eventhandlers/removeOnStageChange.md)-Methode, um Ereignishandler vom Ereignis zu entfernen. 




---
title: OnPreStageChange-Ereignis (Client-API-Referenz) in Dynamics 365 for Customer Engagement | MicrosoftDocs
ms.date: 07/20/2019
ms.service: crm-online
ms.topic: reference
applies_to: Dynamics 365 for Customer Engagement (online)
ms.assetid: null
author: msftman
ms.author: deonhe
manager: kvivek
search.audienceType:
  - developer
search.app:
  - D365CE
---
# <a name="onprestagechange-event-client-api-reference"></a>OnPreStageChange-Ereignis (Client-API-Referenz)

Dieses Ereignis tritt auf, **bevor** die Geschäftsprozessflusssteuerung geändert wird. Dieses Ereignis tritt auf, nachdem der Benutzer die Schaltflächen **Nächste Phase**, **Zurück zur vorherigen Phase** oder **Aktive Phase festlegen** auf der Benutzeroberfläche ausgewählt hat oder wenn ein Entwickler die `formContext.data.process.moveNext`-, `formContext.data.process.movePrevious`- oder `formContext.data.process.setActiveStage`-Methode verwendet.

Über ein Webressourcenskript, das für das onPreStageChange-Ereignis registriert wurde, kann ein Entwickler folgende Schritte für das executionContext-Objekt aufrufen, das an das Webressourcenskript übergeben wird: 

`executionContext.getEventArgs().preventDefault();` 

Wenn Sie `preventDefault` aufrufen:

- Die Statusnavigation wird nicht verarbeitet. Die Prozessinstanz bleibt in der ursprünglichen Phase.
- Die Speichern des Hauptformulars wird nicht verarbeitet. Wenn das Hauptformular in einem geänderten Status war, bleibt es im geänderten Status.
- Webressourcen mit onStageChange-Registrierung werden nicht aufgerufen.


Ein Ausführungskontextobjekt wird an den Ereignishandlern für dieses Ereignis übergeben. Sie können die [getEventArgs](../executioncontext/getEventArgs.md)-Methode verwenden, um ein Objekt abzurufen, das über die folgenden Methoden verfügt:
- **getDirection**: Gibt eine Zeichenfolge zurück, die entweder "Weiter" oder "Zurück" ist, um die Richtung der Phasenänderung anzuzeigen.
- **getStage**: Gibt ein Phasenobjekt zurück. Ausßer wenn die Navigation zu einer neuen Entität weitergeht, repräsentiert die zurückgegebene Phase das Zielphasenobjekt, d. h. die nächste aktive Phase. Wenn die Navigation zu einer neuen Entität weitergeht, ist die Phase die Phase, vob der navigiert wird, d. h. das vorige aktive Phasenobjekt. Weitere Informationen: [Phasenmethoden](../formContext-data-process.md#stage-methods).

Diese Client-API wird nur im einheitlichen Client unterstützt. Der Vorgängerwebclient unterstützt diese Client-API nicht.

## <a name="methods-supported-for-this-event"></a>Unterstütze Möglichkeiten für das Ereignis
- **formContext.data.process**.[addOnPreStageChange](../formcontext-data-process/eventhandlers/addOnPreStageChange.md)-Methode, um Ereignishandler für das Ereignis hinzuzufügen.
- **formContext.data.process**.[removeOnPreStageChange](../formcontext-data-process/eventhandlers/removeOnPreStageChange.md)-Methode, um Ereignishandler vom Ereignis zu entfernen. 




---
title: Grundlegendes zum Client-API-Objektmodell in modellgestützten Apps | MicrosoftDocs
ms.date: 10/31/2018
ms.service: crm-online
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: 3335aec5-6b48-4ef6-8d49-2833b177f318
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-the-client-api-object-model"></a>Grundlegendes zum Client API-Objektmodell



Das Client-API-Objektmodell für modellgestützte Apps bietet Objekte und Methoden, die Sie verwenden können, um angepasste Geschäftslogik in modellgestützten Apps mithilfe von JavaScript anzuwenden, z. B.:
- Abrufen oder Festlegen von Attributwerten.
- Anzeigen und Ausblenden von Benutzeroberflächenelementen.
- Verweisen auf mehrere Steuerelemente pro Attribut.
- Zugreifen auf mehrere Formulare pro Entität.
- Bearbeiten von Formularnavigationselementen.
- Interagieren mit der Geschäftsprozessflusssteuerung.

Es ist wichtig, dass Sie das Client-API-Objektmodell für modellgestützte Apps verstehen, um JavaScript-Code in Customer Enagagement effektiv zu schreiben und zu verwenden.

## <a name="root-objects-in-the-client-api-object-model"></a>Stammobjekte im Client-API-Objektmodell

Am Stamm des Client-API-Objektmodells sind folgende Kontexten und das Xrm-Objekt:

|Objekt|Beschreibung|
|--|--|
|**executionContext**|Stellt den Ausführungskontext für ein Ereignis in Formularen und Rastern für modellgestützte Apps dar.<br/>Weitere Informationen: [Client-API-Ausführungskontext](clientapi-execution-context.md)|
|**formContext** |Enthält einen Verweis auf ein Formular oder ein Element im Formular, für das der aktuelle Code ausgeführt wird. Um das Objekt **formContext** abzurufen, verwenden Sie die Methode **executionContext**.[getFormContext](reference/executioncontext/getFormContext.md).<br/>Weitere Informationen: [Client-API-Formularkontext](clientapi-form-context.md)|
|**gridContext** |Enthält einen Verweis auf ein Raster oder ein Unterraster im Formular, für das der aktuelle Code ausgeführt wird.<br/>Weitere Informationen: [Client-API-Rasterkontext](clientapi-form-context.md)|
|**Xrm**| Stellt ein globales Objekt zum Ausführen von Vorgängen bereicht, die sich nicht direkt auf die Daten und die Benutzeroberfläche in Formularen, in Rastern, in Unterrastern, Steuerelementen oder oder Attributen auswirken. Beispielsweise Navigieren in Formularen, Erstellen und Verwalten von Datensätzen unter Verwendung der Web-API.<br/>Weitere Informationen: [Client-API-Xrm-Objekt](clientapi-xrm.md)|

### <a name="related-topics"></a>Verwandte Themen

[Globaler API-Kontext](clientapi-xrm.md#client-api-global-context)<br/>
[Client-API-Referenz](reference.md)









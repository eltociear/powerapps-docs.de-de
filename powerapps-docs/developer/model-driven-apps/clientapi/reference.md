---
title: Client-API-Referenz für modellgestützte Apps| MicrosoftDocs
description: Das Thema bietet eine Client-API-Referenz für modellgesteuerteApps.
ms.date: 06/27/2019
ms.service: powerapps
ms.topic: conceptual
applies_to:
  - Dynamics 365 (online)
ms.assetid: null
author: KumarVivek
ms.author: kvivek
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="client-api-reference-for-model-driven-apps"></a>Client-API-Referenz für modellgesteuerte Apps



Dieser Abschnitt enthält Referenzdokumentation für Client-API-Objektmodelle, die mit JavaScript-Bibliotheken verwendet werden können.

> [!IMPORTANT]
> - Alle Client-Skripting-APIs, die in dieser Dokumentation verfügbar sind, gelten auch für Dynamics 365 for Customer Engagement-Apps, da Customer Engagement-Apps tatsächlich modellgesteuerte Apps sind, die auf der Common Data Service-Plattform erstellt werden.
> - Das Client API-Objektmodell enthält auch den **Xrm.Internal**-Namespace, und Verwendung der Objekte und Methoden in diesem Namespace wird nicht unterstützt. Diese Objekte und alle Bestandteile des HTML-Dokument-Objektmodells (DOM) können ohne vorherige Ankündigung geändert werden. Wir empfehlen, diese Funktionen oder Skripts, vom DOM abhängig sind, nicht zu verwenden.
> - Während des Debuggens finden Sie möglicherweise Methoden und Objekte im Client-API-Objektmodell, die nicht dokumentiert sind. Nur dokumentierte Objekte und Methoden werden unterstützt.

Die Themen unter diesem Abschnitt sind organisiert wie folgt:
- Es beginnt mit Verweis für alle Fälle,Sammlungen und das Ausführungskontextobjekt.
- Weiter werden Informationen zu Methoden für **Attribute** und **Steuerelemente** in Customer Engagement bereitgestellt, die eigentlich Sammlungen sind, die unter verschiedenen Objekten im Client API-Objektmodell erscheinen.
- Stellt Verweis für Eigenschaften und Methoden für **formContext** und **gridContext** bereit.
- Stellt Verweis auf Namespaces im Objektmodell **Xrm** bereit. 

### <a name="related-topics"></a>Verwandte Themen

[Anwenden von Geschäftslogik mit Client-Skripting in modellgestützten Apps](../client-scripting.md)<br/>
[Grundlegendes zum Client API-Objektmodell](understand-clientapi-object-model.md)<br/>
[Modellgestützte Apps Entwicklerübersicht](../overview.md)

---
title: Anwenden von Geschäftslogik mit Client-Skripting in modellgesteuerten Anwendungen mit JavaScript | Microsoft Docs
description: 'Erfahren Sie, wie Entwickler JavaScript in clientseitigen Skripts verwenden können, um angepasste Geschäftslogik in modellgesteuerten Apps und Dynamics 365 for Customer Engagement-Apps anzuwenden'
services: ''
suite: powerapps
author: KumarVivek
ms.service: powerapps
ms.topic: article
ms.date: 06/27/2019
ms.author: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="apply-business-logic-using-client-scripting-in-model-driven-apps-using-javascript"></a>Anwenden von Geschäftslogik mit Client-Skripting in modellgesteuerten Anwendungen mit JavaScript

Clientseitiges Skripting mit JavaScript ist eine der Möglichkeiten, benutzerdefinierte Geschäftsprozesslogik zum Anzeigen der Daten in einem Formular in einer modellgesteuerten App anzuwenden.

> [!IMPORTANT]
> Alle Client-Skripting-Konzepte und -APIs, die in dieser Dokumentation erläutert werden, gelten auch für Dynamics 365 for Customer Engagement-Apps, da Customer Engagement-Apps tatsächlich modellgesteuerte Apps sind, die auf der Common Data Service erstellt werden.

Client-Skripting sollte jedoch nicht die erste Wahl zum Anwenden der benutzerdefinierten Geschäftsprozesslogik in modellgesteuerten App-Formularen sein. *Geschäftsregeln* bieten jemandem, der kein JavaScript kennt und kein Entwickler ist, die Möglichkeit, Geschäftsprozesslogik in einem Formular anzuwenden. Weitere Informationen: [Erstellen von Geschäftsregeln zur Anwendung der Logik](/powerapps/maker/model-driven-apps/create-business-rules-recommendations-apply-logic-form). Den Geschäftsregeldesigner finden Sie im Bereich **Common Data Service** unter [powerapps.com](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc). Wenn Sie eine Entität anzeigen, suchen Sie nach der Registerkarte **Geschäftsregeln**.

Wenn Ihre Geschäftsanforderung mit einer Geschäftsregel jedoch nicht erreicht werden kann, werden Sie feststellen, dass das Client-Scripting mit dem Objektmodell der Client-API eine leistungsstarke Möglichkeit bietet, das Verhalten der Anwendung zu erweitern und die Automatisierung im Client zu ermöglichen.

## <a name="use-client-scripting-in-model-driven-apps"></a>Verwenden Sie Client-Skripting in modellgesteuerten Anwendungen.

Formulare in modellgesteuerten Anwendungen helfen dem Benutzer, Daten anzuzeigen. Ein Formular in modellgesteuerten Anwendungen kann Elemente wie Felder, eine Schnellerfassung oder ein Raster enthalten. Ein [Ereignis](clientapi/events-forms-grids.md) tritt in den modellgesteuerten App-Formularen stets auf, wenn:
- Ein Formular wird geladen
- Daten werden in einem Feld oder einem Element innerhalb des Formulars geändert.
- Daten werden in einem Formular gespeichert.

Sie können Ihren JavaScript-Code ans „Reagieren” auf diese Ereignisse anzufügen, so dass Ihr Code ausgeführt wird, wenn das Ereignis im Formular auftritt. Sie fügen Ihre JavaScript-Code (Skripte) an diese Ereignisse an, indem Sie eine [Script-Webressource](script-jscript-web-resources.md) in modellgesteuerten Anwendungen verwenden. 

Modellgesteuerte Anwendungen bieten Ihnen eine Vielzahl von **Client-APIs** zur Interaktion mit Formularobjekten und Ereignissen, um zu steuern, was und wann in einem Formular angezeigt werden soll.

> [!NOTE]
> Einige Client-APIs sind in der aktuellen Version der modellgesteuerten Apps veraltet. Stellen Sie sicher, dass Sie diese APIs kennen, wenn Sie clientseitigen Code für modellgesteuerte Apps schreiben. Weitere Informationen: [Veraltete Client-APIs](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#some-client-apis-are-deprecated)

## <a name="get-started-here"></a>Legen wir los.

[Ereignisse in Formularen und in Rastern](clientapi/events-forms-grids.md)<br/>
[Grundlegendes zum Client API-Objektmodell](clientapi/understand-clientapi-object-model.md)<br/>
[Durchlauf: Schreiben Sie Ihren ersten Clientskript](clientapi/walkthrough-write-your-first-client-script.md)

## <a name="reference"></a>Referenz

[Client-API-Referenz](clientapi/reference.md)


### <a name="related-topics"></a>Verwandte Themen

[Webressourcen für modellgesteuerte Apps](web-resources.md)<br/>
[Passen Sie Befehle und das Menüband an](customize-commands-ribbon.md)<br/>
[Entwicklerhandbuch zu Dynamics 365 for Customer Engagement-Apps](/dynamics365/customer-engagement/developer/developer-guide)


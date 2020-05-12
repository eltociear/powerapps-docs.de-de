---
title: Übersicht über die Erstellung von Apps | Microsoft Docs
description: Übersicht über die Erstellung von Apps im Canvas- oder modellgesteuerten Modus und die Einbindung von Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.date: 12/05/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 79a1a5351bc3fe72a7558697e7cf8e8dfa079ce8
ms.sourcegitcommit: d194d2fa009ca7bfcbe95e5f31473832a130e0a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "3302332"
---
# <a name="overview-of-creating-apps-in-power-apps"></a>Übersicht über die Erstellung von Apps in Power Apps

Power Apps ist eine hochproduktive Entwicklungsplattform für Geschäftsanwendungen und umfasst vier Hauptkomponenten:

- [Canvas-Apps](canvas-apps/getting-started.md) setzen bei der Anwenderfreundlichkeit an. Gestalten Sie auf Grundlage eines leeren Hintergrunds eine maßgeschneiderte Oberfläche, und verbinden Sie sie mit 200 Datenquellen Ihrer Wahl. Canvas-Apps lassen sich für Internet-, mobile und Tablet-Anwendungen erstellen.
- [Modellgesteuerte Apps](model-driven-apps/model-driven-app-overview.md) setzen bei Ihrem Datenmodell an. Anhand der Daten aus Ihrem Kerngeschäft und Ihrer Prozesse in Common Data Service werden Formulare, Ansichten und andere Komponenten modelliert. Modellgesteuerte Apps generieren automatisch eine leistungsstarke UI, die geräteübergreifend reagiert.
- [Portale](portals/overview.md) beginnen mit der Erstellung externer Websites, bei denen sich Benutzer außerhalb Ihrer Organisation mit einer Vielzahl von Identitäten anmelden, Daten in Common Data Service erstellen und anzeigen oder sogar Inhalte anonym durchsuchen können.
- [Common Data Service](common-data-service/data-platform-intro.md) ist die Datenplattform von Power Apps. Damit können Sie Geschäftsdaten speichern und modellieren. Es ist die Plattform, auf der Dynamics 365-Anwendungen entwickelt werden. Wenn Sie Dynamics-Kunde sind, sind Ihre Daten bereits in Common Data Service vorhanden.

Sie können Ihre erste App schnell und einfach erstellen. Es gibt einen 30-tägigen Testversionsplan und einen kostenlosen Communityplan. Finden Sie heraus, welcher am besten zu Ihnen passt, und legen Sie los.

## <a name="canvas-apps"></a>Canvas-Apps

Mit Canvas-Apps können Sie Benutzerfreundlichkeit und Benutzeroberfläche nach Ihren Vorstellungen gestalten. Lassen Sie sich bei Erscheinungsbild und Funktionsweise Ihrer Apps von Ihrer Kreativität und Ihrem Geschäftssinn leiten.

Sie können Ihre App mithilfe der Microsoft-Tools erstellen, in denen sich Ihre Daten befinden, z. B.:

- [In einer SharePoint-Liste](canvas-apps/app-from-sharepoint.md#create-an-app-from-within-sharepoint-online)
- [In einem Power BI-Dashboard](canvas-apps/embed-powerapps-powerbi.md)

Die Entwicklung von Canvas-Apps ist einfach. Mit Power Apps haben Sie mehrere Möglichkeiten Ihre App zu erstellen:

- [Aus Daten](canvas-apps/app-from-sharepoint.md)
- [Mithilfe eines Musters](canvas-apps/open-and-run-a-sample-app.md)
- [Über eine Common Data Service-Quelle](canvas-apps/data-platform-create-app.md)
- [In einem leeren Canvas](canvas-apps/data-platform-create-app-scratch.md)
- [Über AppSource](../user/app-source.md)

## <a name="model-driven-apps"></a>Modellgesteuerte Apps

Wenn Sie eine modellgesteuerte App entwerfen, können Sie auf das gesamte Leistungsspektrum von Common Data Service zugreifen und Formulare, Geschäftsregeln und Prozessflüsse schnell konfigurieren. Modellgestützte Apps werden auf der Website von Power Apps erstellt.

Die ersten Schritte mit modellgesteuerten Apps sind einfach. Sie können mit folgenden Themen beginnen:

- [App erstellen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [Formulare erstellen und gestalten](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [Ansichten erstellen oder bearbeiten](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [Ein Systemdiagramm erstellen oder bearbeiten](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [Erstellen oder Bearbeiten von Systemdashboards](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [Sicherheitsfunktionen hinzufügen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [Geschäftslogik hinzufügen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="common-data-service"></a>Common Data Service

Mit Common Data Service können Sie Ihre Daten innerhalb mehrerer Standard- und benutzerdefinierter Entitäten sicher speichern und verwalten. Diesen Entitäten können Sie bei Bedarf auch Felder hinzufügen.

Erste Schritte mit dem Common Data Service. Sie können beispielsweise mit folgenden Elementen beginnen:

- [Eine benutzerdefinierte Entität erstellen](common-data-service/data-platform-create-entity.md)
- [Felder verwalten](common-data-service/data-platform-manage-fields.md)
- [Benutzerdefinierte Optionssätze erstellen](common-data-service/custom-picklists.md)
- [Geschäftsregel erstellen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

## <a name="canvas-and-model-driven-artifacts"></a>Canvas-Apps und modellgesteuerte Artefakte

Während wir die Funktionen von Canvas-Apps und modellgesteuerten Apps zusammenführen, sind diese Artefakte entweder für Canvas-Apps oder modellgesteuerte Apps relevant.

| Artefakt            | App-Typ     |
|---------------------|--------------|
| Entität > Ansichten      | Modellgesteuerte |
| Entität > Formulare      | Modellgesteuerte |
| Entität > Dashboards | Modellgesteuerte |
| Verbindungen         | Canvas       |
| Gateways            | Canvas       |
| Benutzerdefinierte Connectors   | Canvas       |
| Apps > Importieren       | Canvas       |

Wenn Ihre App fertig ist, können Sie sie für die Mitglieder Ihres Teams [freigeben](canvas-apps/share-app.md).

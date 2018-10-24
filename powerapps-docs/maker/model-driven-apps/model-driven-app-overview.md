---
title: Übersicht über die Erstellung einer modellgesteuerten App mit PowerApps | Microsoft-Dokumentation
description: Ausführliche Anleitungen zum Erstellen und Konfigurieren einer Entität zur Verwendung mit einer PowerApps-App
documentationcenter: na
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 08/09/2018
ms.author: matp
ms.openlocfilehash: f6434e6a9248586c05fa0b56b8934d910af3087a
ms.sourcegitcommit: 2a61989be5880fede31510c5dab1593a6f42a741
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2018
ms.locfileid: "39723844"
---
# <a name="what-are-model-driven-apps-in-powerapps"></a>Was sind modellgesteuerte Apps in PowerApps?

Das Design einer modellgesteuerten App ist ein auf Komponenten bezogener Ansatz zum Entwickeln von Apps. Das Design modellgesteuerter Apps erfordert keinen Code, und die Apps, die Sie erstellen, können so einfach oder sehr komplex sein.  Im Gegensatz zur Entwicklung einer Canvas-App, bei der der Designer über die vollständige Kontrolle über das Layout der App verfügt, wird bei modellgesteuerten Apps beinahe das gesamte Layout für Sie bestimmt und von den von Ihnen zur App hinzugefügten Komponenten größtenteils festgelegt. 

![Beispiel für eine modellgesteuerte App](media/model-driven-app-overview/model-app-sample.png)

Das Design modellgesteuerter Apps bietet folgende Vorteile:
- Umfangreiche Entwurfsumgebungen, die sich auf Komponenten statt Code konzentrieren 
- Erstellen von komplexen dynamischen Apps mit einer ähnlichen Benutzeroberfläche auf unterschiedlichen Geräten, egal ob es sich dabei um Desktopgeräte oder Mobilgeräte handelt
- Entwerfen von Funktionen, die den auf der Dynamics 365 Customer Engagement-Plattform verfügbaren Funktionen ähnlich sind 
- Ihre App kann als eine Lösung verteilt werden
 
## <a name="the-approach-to-model-driven-app-making"></a>Ansatz für die Erstellung modellgesteuerter Apps
Die Erstellung modellgesteuerter Apps besteht grundsätzlich aus drei Schwerpunktbereichen.

- Modellieren von Geschäftsdaten 
- Definieren von Geschäftsprozessen 
- Entwerfen der App

### <a name="modeling-business-data"></a>Modellieren von Geschäftsdaten
Um Geschäftsdaten zu modellieren, bestimmen Sie, welche Daten Ihre App benötigt und wie diese Daten mit anderen Daten in Zusammenhang stehen. Der modellgesteuerte Entwurf nutzt eine durch Metadaten gesteuerte Architektur, damit Designer die Anwendung anpassen können, ohne Code schreiben zu müssen. Metadaten sind im Grunde genommen „Daten über Daten“ und definieren die Struktur der im System gespeicherten Daten. [Tutorial: Erstellen benutzerdefinierter Entitäten mit Komponenten in PowerApps](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>Definieren von Geschäftsprozessen
Das Definieren und Erzwingen konsistenter Geschäftsprozesse ist ein wichtiger Aspekt beim Entwurf modellgesteuerter Apps. Konsistente Prozesse können Benutzer dabei unterstützen, sich auf ihre Arbeit zu konzentrieren, da sie nicht manuell mehrere verschiedene Schritte ausführen müssen. Prozesse können einfach oder komplex sein und sich über die Jahre oft ändern. Um einen Prozess zu erstellen, wählen Sie unter PowerApps.com im modellgesteuerten Bereich ![Einstellungen](media/powerapps-gear.png) > **Erweiterte Anpassungen** > **Projektmappen-Explorer öffnen** aus. Wählen Sie anschließend im linken Bereich im Projektmappen-Explorer **Prozesse** und dann **Neu** aus. Weitere Informationen finden Sie unter [Übersicht über Geschäftsprozessflüsse](/flow/business-process-flows-overview) und [Anwenden von Geschäftslogik mit Common Data Service für Apps](../common-data-service/cds-processes.md). 

### <a name="composing-the-model-driven-app"></a>Erstellen der modellgesteuerten App
Nachdem Sie die Daten modelliert und Prozesse definiert haben, erstellen Sie Ihre App, indem Sie mithilfe des App-Designers die erforderlichen Komponenten auswählen und konfigurieren.

![App-Designer](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>Nächste Schritte

[Erstellen Ihrer ersten modellgesteuerten App](build-first-model-driven-app.md)

[Grundlegendes zu Komponenten von modellgesteuerten Apps](model-driven-app-components.md)


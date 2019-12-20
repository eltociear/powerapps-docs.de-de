---
title: Übersicht über die Erstellung einer modellgetriebenen App mit Power Apps | Microsoft Docs
description: Schritt-für-Schritt-Anleitung zum Erstellen und Konfigurieren einer Entität für die Verwendung mit einer Power Apps App.
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 11febe03a69fe774f2c0394ee5d3a016c901498d
ms.sourcegitcommit: 5e6d71967902c463f34a9254f988b9c10e431eb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "2890657"
---
# <a name="what-are-model-driven-apps-in-power-apps"></a>Was sind modellgetriebene Apps in Power Apps?

Modell-angetriebener App-Entwurf ist eine Komponenten-fokussierte Methode zur App-Entwicklung. Modellgesteuertes App-Design erfordert keinen Code und die von Ihnen erstellten Apps können einfach oder sehr komplex sein.  Im Gegensatz zur Entwicklung von Canvas-Apps, bei denen der Designer die volle Kontrolle über das App-Layout hat, wird bei modellgesteuerten Apps ein Großteil des Layouts für Sie bestimmt und weitgehend durch die Komponenten bestimmt, die Sie der App hinzufügen. 

![Beispiel einer modellgesteuerten Anwendung](media/model-driven-app-overview/model-app-sample.png)

Das modellgesteuerte App-Design bietet folgende Vorteile:
- Umfangreiche komponentenorientierte Entwurfsumgebungen ohne Eingabe von Code 
- Erstellen Sie komplexe, reaktionsschnelle Anwendungen mit einer ähnlichen Benutzeroberfläche für eine Vielzahl von Geräten, vom Desktop bis zum Smartphone.
- Umfangreiche Designfähigkeit 
- Ihre App kann als Lösung verteilt werden kann
 
## <a name="the-approach-to-model-driven-app-making"></a>Die Methode zur modellgesteuerten App-Erstellung
Grundsätzlich besteht die modellgetriebene App-Erstellung aus drei Schwerpunktbereichen.

- Modellierung von Geschäftsdaten 
- Definieren der Geschäftsprozesse 
- Erstellen der App

### <a name="modeling-business-data"></a>Modellierung von Geschäftsdaten
Um Geschäftsdaten zu modellieren, bestimmen Sie, welche Daten Ihre Anwendung benötigt und wie sich diese Daten auf andere Daten beziehen. Das modellgetriebene Design verwendet eine metadatengesteuerte Architektur, so dass Designer die Anwendung anpassen können, ohne Code schreiben zu müssen. Metadaten sind "Daten über Daten"; diese definieren die Struktur der im System gespeicherten Daten. [Tutorial: Erstellen Sie eine benutzerdefinierte Entität, die Komponenten in Power Apps enthält](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>Definieren der Geschäftsprozesse
Die Definition und Durchsetzung konsistenter Geschäftsprozesse ist ein wesentlicher Aspekt des modellgesteuerten App-Designs. Konsistente Prozesse sorgen dafür, dass sich Ihre App-Anwender auf ihre Arbeit konzentrieren können und nicht daran denken müssen, eine Reihe von manuellen Schritten auszuführen. Prozesse können einfach oder komplex sein und sich oft im Laufe der Zeit ändern. Um einen Prozess zu erstellen, wählen Sie aus dem modellgetriebenen Bereich PowerApps.com ![Einstellungen](media/powerapps-gear.png) > **Erweiterte Anpassungen** > **Lösungsexplorer öffnen**. Wählen Sie dann im linken Navigationsbereich im Lösungsexplorer **Prozesse** aus und wählen Sie dann **Neu**. Mehr Informationen: [Geschäftsprozessabläufe im Überblick](/flow/business-process-flows-overview) und [Geschäftslogik mit Common Data Service anwenden](../common-data-service/cds-processes.md). 

### <a name="composing-the-model-driven-app"></a>Zusammenstellen der modellgesteuerten App
Nach der Modellierung von Daten und der Definition von Prozessen erstellen Sie Ihre App, indem Sie die benötigten Komponenten mit dem App-Designer auswählen und konfigurieren.

![App-Designer](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>Nächste Schritte

[Erstellen Sie Ihre erste modellgesteuerte App](build-first-model-driven-app.md)

[Grundlegendes zu Komponenten modellgestützter Apps](model-driven-app-components.md)


---
title: Übersicht über das powerapps-Komponenten Framework | Microsoft-Dokumentation
description: Verwenden Sie das powerapps-Komponenten Framework, um Code Komponenten zu erstellen, die es Benutzern ermöglichen, Daten in Formularen, Ansichten und Dashboards anzuzeigen und mit Ihnen zu arbeiten.
keywords: Komponenten Framework, Code Komponenten, powerapps-Steuerelemente
author: nkrb
manager: kvivek
ms.date: 09/05/2019
ms.service: powerapps
ms.custom:
- dyn365-a11y
- dyn365-developer
ms.topic: article
ms.assetid: 7923e36d-3640-49f7-9f2f-c97358a632db
ms.author: nabuthuk
ms.openlocfilehash: a9f157dfb3d0a7d29cebadee935c84826ae040d6
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73025660"
---
# <a name="powerapps-component-framework-overview"></a>Übersicht über das powerapps-Komponenten Framework

Das powerapps-Komponenten Framework ermöglicht professionellen Entwicklern und App-Entwicklern das Erstellen von Code Komponenten für Modell gesteuerte apps und Canvas-Apps (experimentelle Vorschau), um Benutzern eine verbesserte Benutzeroberfläche zur Anzeige und Bearbeitung von Daten in Formularen, Ansichten, und Dashboards. Beispiel:

- Ersetzen Sie ein Feld, das einen numerischen Textwert anzeigt, durch einen `dial` oder `slider` Code Komponente.
- Transformieren Sie eine Liste in eine ganz andere visuelle Darstellung, die an das DataSet gebunden ist, wie eine `Calendar` oder `Map`.

> [!IMPORTANT]
> - Das powerapps-Komponenten Framework ist als experimentelle Vorschau für Canvas-apps und in allgemeiner Verfügbarkeit für Modell gesteuerte apps verfügbar. Dies bedeutet, dass alle APIs, die für Modell gesteuerte Apps unterstützt werden, für Canvas-Apps möglicherweise noch nicht unterstützt werden.
> - Standardmäßig ist das powerapps-Komponenten Framework für Modell gesteuerte apps aktiviert. Informationen zum Aktivieren dieses Features für Canvas-apps finden Sie unter [Verfügbarkeit für Canvas-apps](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Canvas-apps unterstützen nur den *Feldtyp* von Code Komponenten und nicht den *DataSet* -Typ.


Verwenden Sie das powerapps-Komponenten Framework zum Erstellen von Code Komponenten, die in allen Funktionen von powerapps verwendet werden können. Im Gegensatz zu HTML-Webressourcen werden Code Komponenten als Teil desselben Kontexts gerendert, gleichzeitig mit allen anderen Komponenten geladen, was eine nahtlose Benutzer Darstellung ermöglicht. Entwickler können alle HTML-, CSS-und typescript-oder JavaScript-Dateien in einer einzelnen Projektmappenpaketdatei bündeln. Code Komponenten können in unterschiedlichen Entitäten und Formularen mehrmals wieder verwendet werden.

Code Komponenten haben Zugriff auf einen umfangreichen Satz von Framework-APIs, die Funktionen wie die Verwaltung des Komponenten Lebenszyklus, den kontextbezogenen Daten und den Metadatenzugriff, den nahtlosen Server Zugriff über Web-API, das Hilfsprogramm und Daten Formatierungs Methoden, Gerätefunktionen wie Kamera Speicherort und Mikrofon sowie leicht aufzurufende UX-Elemente wie Dialogfelder, Lookups und das vollständige Rendering.  

Entwickler und App-Ersteller können moderne Webpraktiken verwenden und die Leistungsfähigkeit externer Bibliotheken nutzen, um erweiterte Benutzerinteraktionen zu erstellen. Das Framework kümmert sich automatisch um den Lebenszyklus der Komponente, behält die Geschäftslogik der Anwendung bei und optimiert die Leistung (keine weiteren Async-iframes). Komponenten Definitionen, [Abhängigkeiten und Konfigurationen](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) können alle in eine Projekt Mappe gepackt und in Umgebungen verschoben werden. Sie können über [appsource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365)ausgeliefert werden.  

## <a name="related-topics"></a>Verwandte Themen

[Was sind Code Komponenten?](custom-controls-overview.md)<br/>
[Verfügbarkeit für Canvas-apps](component-framework-for-canvas-apps.md)<br/>
[Erstellen und Erstellen einer Code Komponente](create-custom-controls-using-pcf.md)<br/>
[PowerApps für Entwickler](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)


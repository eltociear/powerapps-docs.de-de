---
title: PowerApps component framework Übersicht | Microsoft Docs
description: Verwenden Sie das PowerApps component framework, um Code-Komponenten zu erstellen, um Personen ein verbessertes Erlebnis beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten.
keywords: component framework, Code-Komponenten, PowerApps-Steuerelemente
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
ms.openlocfilehash: 03534f925750b7c99e6d53822aab766421854968
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753622"
---
# <a name="powerapps-component-framework-overview"></a>PowerApps component framework Übersicht

Mit dem PowerApps component framework können professionelle Entwickler und App-Ersteller Codekomponenten für modellgesteuerte Apps und Canvas-Apps (experimentelle Vorschau) erstellen, um eine Erhöhung Benutzerfreundlichkeit angeben, um Benutzern ein verbessertes Benutzererlebnis beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten. Beispiel:

- Ersetzen Sie ein Feld, das einen numerischen Textwert anzeigt, mit einer `dial`- oder `slider`-Code-Komponente.
- Transformieren Sie eine Liste in eine völlig andere Sichterfahrung, die an das Dataset gebunden ist, z. B. `Calendar` oder `Map`.

> [!IMPORTANT]
> - PowerApps component framework befindet sich in der experimentellen Vorschau für Canvas-Anwendungen und in GA für modellgetriebene Anwendungen. Dies bedeutet, dass alle APIs, die für modellgetriebene Anwendungen unterstützt werden, möglicherweise noch nicht auf Canvas-Anwendungen unterstützt werden.
> - Standardmäßig ist das PowerApps component framework für modellgesteuerte Apps aktiviert. Um diese Funktion für Canvas-Anwendungen zu aktivieren, siehe [Verfügbarkeit für Canvas-Anwendungen](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Canvas-Anwendungen unterstützen nur den Typ *Feld* der Codekomponenten und nicht den Typ *Datensatz*.


Nutzen Sie das PowerApps component framework, um Code-Komponenten zu erstellen, die bei allen PowerApps-Funktionen verwendet werden können. Im Gegensatz zu HTML-Webressourcen werden Codekomponenten als Teil desselben Kontextes dargestellt, der gleichzeitig mit allen anderen Komponenten geladen wird, was den Benutzern ein nahtloses Erlebnis bietet. Entwickler können alle HTML-, CSS- und TypeScript- oder JavaScript-Dateien in einer einzigen Lösungspaketdatei bündeln. Codekomponenten können mehrfach über verschiedene Entitäten und Formulare hinweg wiederverwendet werden.

Code-Komponenten haben Zugriff auf eine große Palette von Framework-APIs, die Funktionen wie Komponentenlebenszyklusverwaltung, Kontextdaten und Metadatenzugriff, nahtlosen Serverzugriff über die Web-API, Hilfsprogramm- und Datenformatierungsmethoden, Gerätefunktionen wie Kamera, Standort und Mikrofon zusammen mit einfach aufzurufenden UX-Elementen wie Dialoge, Suchen und Rendering der gesamten Seite zur Verfügung stellen.  

Entwickler und App-Ersteller können moderne Webpraktiken verwenden und so die Möglichkeiten externer Bibliotheken nutzen, um erweiterte Benutzerinteraktionen zu erstellen. Das Framework übernimmt automatisch den Lebenszyklus der Komponenten, behält die Anwendungslogik bei und optimiert die Leistung (keine asynchronen IFrames mehr). Komponentendefinition, Abhängigkeiten und Konfigurationen können alle in einer [Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) verpackt, zu verschiedenen Umgebungen verschoben und über [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=dynamics-365) bereitgestellt werden.  

## <a name="related-topics"></a>Verwandte Themen

[Was sind Code-Komponenten](custom-controls-overview.md)<br/>
[Verfügbarkeit für Canvas-Anwendungen](component-framework-for-canvas-apps.md)<br/>
[Erstellen und Entwickeln einer Code-Komponente](create-custom-controls-using-pcf.md)<br/>
[PowerApps für Entwickler](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)


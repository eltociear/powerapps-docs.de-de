---
title: PowerApps component framework Übersicht | Microsoft Docs
description: 'Verwenden Sie das PowerApps component framework, um Codekomponenten zu erstellen, die eine verbesserte Benutzerfreundlichkeit für die Anzeige und Arbeit mit Daten in Formularen, Ansichten und Dashboards bieten.'
keywords: 'component framework, Code-Komponenten, PowerApps-Steuerelemente'
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
---

# <a name="powerapps-component-framework-overview"></a>PowerApps component framework Übersicht

Verwenden Sie das PowerApps component framework, um Codekomponenten für modellgetriebene Anwendungen und Canvas-Anwendungen zu erstellen (experimentelle Vorschau), um den Benutzern eine verbesserte Benutzererfahrung beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten. Beispiel:

- Ersetzen Sie ein Feld, das einen numerischen Textwert anzeigt, mit einer `dial`- oder `slider`-Komponente.
- Transformieren Sie eine Liste in eine völlig andere Sichterfahrung, die an das Dataset gebunden ist, z. B. `Calendar` oder `Map`.

 
> [!IMPORTANT]
> - PowerApps component framework befindet sich in der experimentellen Vorschau für Canvas-Anwendungen und in GA für modellgetriebene Anwendungen. Dies bedeutet, dass alle APIs, die für modellgetriebene Anwendungen unterstützt werden, möglicherweise noch nicht auf Canvas-Anwendungen unterstützt werden.
> - Standardmäßig ist das PowerApps component framework für modellgesteuerte Apps aktiviert. Um diese Funktion für Canvas-Anwendungen zu aktivieren, siehe [Verfügbarkeit für Canvas-Anwendungen](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Canvas-Anwendungen unterstützen nur den Typ *Feld* der Codekomponenten und nicht den Typ *Datensatz*.


Das PowerApps component framework ermöglicht es professionellen Entwicklern und App-Herstellern, Code-Komponenten zu erstellen, die über die gesamte Bandbreite der PowerApps Funktionen verwendet werden können. Im Gegensatz zu HTML-Webressourcen werden Codekomponenten als Teil desselben Kontextes dargestellt, der gleichzeitig mit allen anderen Komponenten geladen wird, was den Benutzern ein nahtloses Erlebnis bietet. Entwickler können alle HTML-, CSS- und TypeScript- oder JavaScript-Dateien in einer einzigen Lösungspaketdatei bündeln. Codekomponenten können mehrfach über verschiedene Entitäten und Formulare hinweg wiederverwendet werden.

Code-Komponenten haben Zugriff auf einen umfangreichen Satz von Framework-APIs, die Funktionen wie Component Lifecycle Management, kontextabhängigen Daten- und Metadatenzugriff, nahtlosen Serverzugriff über Web API, Utility- und Datenformatierungsmethoden, Gerätefunktionen wie Kamera, Standort und Mikrofon sowie einfach aufrufbare UX-Elemente wie Dialoge, Lookups, Ganzseiten-Rendering usw. bereitstellen.  


Entwickler und App-Ersteller können moderne Web-Praktiken nutzen und auch die Leistungsfähigkeit externer Bibliotheken nutzen, um erweiterte Benutzerinteraktionen zu erstellen. Das Framework übernimmt automatisch den Lebenszyklus der Komponenten, behält die Anwendungslogik bei und optimiert die Leistung (keine asynchronen IFrames mehr). Komponentendefinition, Abhängigkeiten und Konfigurationen können alle in eine [Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) gebündelt und über mehrere Umgebungen verteilt werden und können über [Anwendungsquelle](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365) bereitgestellt werden.  

## <a name="related-topics"></a>Verwandte Themen

[Was sind Code-Komponenten](custom-controls-overview.md)<br/>
[Verfügbarkeit für Canvas-Anwendungen](component-framework-for-canvas-apps.md)<br/>
[Erstellen und Bereitstellen von Codekomponenten](create-custom-controls-using-pcf.md)<br/>
[PowerApps für Entwickler](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)


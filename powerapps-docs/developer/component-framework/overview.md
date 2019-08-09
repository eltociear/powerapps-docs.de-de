---
title: Übersicht über das PowerApps component framework | MicrosoftDocs
description: 'Verwenden Sie das PowerApps Komponentenframework, um benutzerdefinierte Komponenten zu erstellen, um Personen ein verbessertes Erlebnis beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten.'
keywords: 'Komponentenframework, benutzerdefinierte Komponenten, PowerApps-Steuerelemente'
author: nkrb
manager: kvivek
ms.date: 04/23/2019
ms.service: powerapps
ms.custom:
  - dyn365-a11y
  - dyn365-developer
ms.topic: article
ms.assetid: 7923e36d-3640-49f7-9f2f-c97358a632db
ms.author: nabuthuk
---

# <a name="powerapps-component-framework-overview"></a>Übersicht über das PowerApps component framework

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Verwenden Sie das PowerApps Komponentenframework, um benutzerdefinierte Komponenten in modellgesteuerten Apps zu erstellen, um Benutzern ein verbessertes Benutzererlebnis beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten. Beispiel:

- Ersetzen Sie ein Feld, das einen numerischen Textwert anzeigt, mit einer `dial`- oder `slider`-Komponente.
- Transformieren Sie eine Liste in eine völlig andere Sichterfahrung, die an das Dataset gebunden ist, z. B. `Calendar` oder `Map`.

> [!IMPORTANT]
> - PowerApps-Komponentenframework ist eine Vorschaufunktion.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 


PowerApps Komponentenframework ermöglicht es professionellen Entwicklern benutzerdefinierte Komponenten zu erstellen, die bei allen PowerApps-Funktionen verwendet werden können. Benutzerdefinierte Komponenten haben Zugriff auf eine große Palette von Framework-APIs, die Funktionen wie Komponentenlebenszyklusverwaltung, Kontextdaten und Metadatenzugriff, nahtlosen Serverzugriff über die Web-API, Hilfsprogramm- und Datenformatierungsmethoden, Gerätefunktionen wie Kamera, Standort und Mikrofon zusammen mit einfach aufzurufenden UX-Elementen wie Dialoge, Suchen, Rendering der gesamten Seite usw. zur Verfügung stellen.  

> [!NOTE]
> Benutzerdefinierte Komponenten werden auf der Einheitlichen Schnittstelle lediglich für [Modellgestützte Apps](/powerapps/maker/model-driven-apps/model-driven-app-overview) der Version 9.1.0.3842 oder später unterstützt.

Komponentenentwickler können moderne Webpraktiken verwenden und so die Möglichkeiten externer Bibliotheken nutzen, um erweiterte Benutzerinteraktionen zu erstellen. Das Framework behandelt den Komponentenlebenszyklus automatisch, behält die Anwendungsgeschäftslogik bei und optimiert für Leistung (kein Iframes async mehr). Komponenten, die mit diesem Framework erstellt werden, sind vollständig konfigurierbar und können auf mehreren Oberflächen in modellgesteuerten Apps wie Formularen, Dashboards, Rastern usw. wiederverwendet werden. Komponentendefinition, Abhängigkeiten und Konfigurationen können alle in einer [Lösung](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) verpackt, zu verschiedenen Umgebungen verschoben und über [App Source](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=dynamics-365) bereitgestellt werden.  

## <a name="related-topics"></a>Verwandte Themen

[Was sind benutzerdefinierte Komponenten?](custom-controls-overview.md)<br/>
[Erstellen und bereitstellen benutzerdefinierter Komponenten](create-custom-controls-using-pcf.md)<br/>
[PowerApps für Entwickler](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)


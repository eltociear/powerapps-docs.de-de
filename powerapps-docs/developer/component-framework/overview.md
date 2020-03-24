---
title: Power Apps component framework Übersicht | Microsoft Docs
description: Verwenden Sie das Power Apps component framework, um Code-Komponenten zu erstellen, um Personen ein verbessertes Erlebnis beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten.
keywords: component framework, Code-Komponenten, Power Apps-Steuerelemente
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
ms.openlocfilehash: cc809d81b7b9adf7327aa9cb8f74515816022118
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "3091233"
---
# <a name="power-apps-component-framework-overview"></a>Power Apps component framework Übersicht

Power Apps component framework können professionelle Entwickler und App-Hersteller Code-Komponenten für modellgesteuerte und Canvas-Apps erstellen (öffentliche Vorschau), um den Benutzern eine verbesserte Benutzererfahrung für die Arbeit mit Daten in Formularen, Ansichten und Dashboards zu bieten. Beispiel:

- Ersetzen Sie ein Feld, das einen numerischen Textwert anzeigt, mit einer `dial`- oder `slider`-Code-Komponente.
- Transformieren Sie eine Liste in eine völlig andere Sichterfahrung, die an das Dataset gebunden ist, z. B. `Calendar` oder `Map`.

> [!IMPORTANT]
> - PowerApps component framework befindet sich in der öffentlichen Vorschau für Canvas-Apps und ist im Allgemeinen für modellgesteuerte Apps verfügbar. Dies bedeutet, dass alle APIs, die für modellgetriebene Anwendungen unterstützt werden, möglicherweise noch nicht auf Canvas-Anwendungen unterstützt werden.
> - Standardmäßig ist das Power Apps component framework für modellgesteuerte Apps aktiviert. Informationen zum Aktivieren dieser Funktion für Canvas-Apps finden Sie unter [Codekomponenten für Canvas-Apps](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Power Apps component framework funktioniert nur auf Einheitliche Oberfläche und nicht auf dem Webclient. 
> - Power Apps component framework funktioniert nicht für lokale Instanzen. 

## <a name="how-is-it-different-from-web-resources"></a>Wie unterscheidet es sich von Webressourcen

Im Gegensatz zu HTML-Webressourcen werden Codekomponenten als Teil desselben Kontextes dargestellt, der gleichzeitig mit allen anderen Komponenten geladen wird, was den Benutzern ein nahtloses Erlebnis bietet. 

Entwickler können den gesamten HTML-Code, CSS und TypeScript-Dateien zu einer einzigen [Lösung ](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview) Paketdatei bündeln und über Umgebungen bewegen und auch über [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=dynamics-365) versenden. 

Codekomponenten können mehrfach über verschiedene Entitäten und Formulare hinweg wiederverwendet werden. Nutzen Sie das Power Apps component framework, um Code-Komponenten zu erstellen, die bei allen Power Apps-Funktionen verwendet werden können.

## <a name="advantages"></a>Vorteile 

- Zugriff auf eine Vielzahl von Framework-APIs, die Funktionen wie Management des Komponentenlebenszyklus, Kontextdaten und Metadaten bereitstellen. 
- Nahtloser Serverzugriff über Web-API-, Dienstprogramm- und Datenformatierungsmethoden, Gerätefunktionen wie Kamera, Standort und Mikrofon sowie einfach aufzurufende UX-Elemente wie Dialogfelder, Nachschlagen und ganzseitiges Rendern.  
- Unterstützung für moderne Webpraktiken.
- Optimieren der Leistung.
- Wiederverwendbarkeit
- Bündeln Sie alle Dateien in einer einzigen Lösungsdatei.

## <a name="licensing"></a>Lizenzierung

Power Apps Lizenzanforderungen für das component framework stimmen mit den vorhandenen Konnektoren und Komponenten überein und basieren auf der Art der in Ihrer App verwendeten Daten und Verbindungen. Weitere Informationen [Power Apps Preise](https://powerapps.microsoft.com/pricing/). Um den Lizenzanforderungen gerecht zu werden, werden wir Codekomponenten in zwei Typen klassifizieren:

- Code-Komponenten, die direkt und nicht über Konnektoren eine Verbindung zu externen Diensten oder Daten herstellen. Wenn diese Komponenten in einer App verwendet werden, wird die App zu einer Premium-App, für die Endbenutzer **Power Apps** Lizenzen benötigen.
- Codekomponenten, die keine Verbindung zu externen Diensten oder Daten herstellen. Wenn diese Komponenten in einer App verwendet werden, die Standardfunktionen verwendet, bleibt die App Standard, und Endbenutzer müssen mindestens eine Lizenz für **Office 365** haben.

> [!NOTE]
> Wenn Sie derzeit Codekomponenten in modellgesteuerten Apps verwenden, mit denen eine Verbindung  zu Common Data Service besteht, benötigen Endbenutzer **Power Apps** Lizenzen.

Mit der allgemeinen Verfügbarkeit des Frameworks können Entwickler von Codekomponenten Komponenten als Teil des Komponentenmanifests klassifizieren, damit Hersteller sehen können, welche Komponenten Premium sind.

## <a name="related-topics"></a>Verwandte Themen

[Was sind Code-Komponenten](custom-controls-overview.md)<br/>
[Codekomponenten für Canvas-Apps](component-framework-for-canvas-apps.md)<br/>
[Erstellen und Entwickeln einer Code-Komponente](create-custom-controls-using-pcf.md)<br/>
[Power Apps für Entwickler](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)


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
ms.openlocfilehash: 6401bead52f3a36fdd51595cb1fdf38510438459
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909203"
---
# <a name="power-apps-component-framework-overview"></a>Power Apps component framework Übersicht

Power Apps component framework ermöglicht professionellen Entwicklern und App-Entwicklern das Erstellen von Code-Komponenten für modellbasierte und Canvas-Apps (experimentelle Vorschau), um den Benutzern eine verbesserte Benutzererfahrung für die Arbeit mit Daten in Formularen, Ansichten und Dashboards zu bieten. Beispiel:

- Ersetzen Sie ein Feld, das einen numerischen Textwert anzeigt, mit einer `dial`- oder `slider`-Code-Komponente.
- Transformieren Sie eine Liste in eine völlig andere Sichterfahrung, die an das Dataset gebunden ist, z. B. `Calendar` oder `Map`.

> [!IMPORTANT]
> - Power Apps component framework befindet sich in der experimentellen Vorschau für Canvas-Anwendungen und in GA für modellgetriebene Anwendungen. Dies bedeutet, dass alle APIs, die für modellgetriebene Anwendungen unterstützt werden, möglicherweise noch nicht auf Canvas-Anwendungen unterstützt werden.
> - Standardmäßig ist das Power Apps component framework für modellgesteuerte Apps aktiviert. Informationen zum Aktivieren dieser Funktion für Canvas-Apps finden Sie unter [Codekomponenten für Canvas-Apps](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Canvas-Anwendungen unterstützen nur den Typ *Feld* der Codekomponenten und nicht den Typ *Datensatz*.

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

## <a name="related-topics"></a>Verwandte Themen

[Was sind Code-Komponenten](custom-controls-overview.md)<br/>
[Codekomponenten für Canvas-Apps](component-framework-for-canvas-apps.md)<br/>
[Erstellen und Entwickeln einer Code-Komponente](create-custom-controls-using-pcf.md)<br/>
[Power Apps für Entwickler](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer)


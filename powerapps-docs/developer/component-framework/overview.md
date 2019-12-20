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
ms.openlocfilehash: c86182fe14617f971b8ca2183bdb4627b8e8c5b9
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2019
ms.locfileid: "2895076"
---
# <a name="power-apps-component-framework-overview"></a>Power Apps component framework Übersicht

Mit dem Power Apps component framework können professionelle Entwickler und App-Ersteller Codekomponenten für modellgesteuerte Apps und Canvas-Apps (experimentelle Vorschau) erstellen, um eine Erhöhung Benutzerfreundlichkeit angeben, um Benutzern ein verbessertes Benutzererlebnis beim Anzeigen und Arbeiten mit Daten in Formularen, Ansichten und Dashboards zu bieten. Beispiel:

- Ersetzen Sie ein Feld, das einen numerischen Textwert anzeigt, mit einer `dial`- oder `slider`-Code-Komponente.
- Transformieren Sie eine Liste in eine völlig andere Sichterfahrung, die an das Dataset gebunden ist, z. B. `Calendar` oder `Map`.

> [!IMPORTANT]
> - Power Apps component framework befindet sich in der experimentellen Vorschau für Canvas-Anwendungen und in GA für modellgetriebene Anwendungen. Dies bedeutet, dass alle APIs, die für modellgetriebene Anwendungen unterstützt werden, möglicherweise noch nicht auf Canvas-Anwendungen unterstützt werden.
> - Standardmäßig ist das Power Apps component framework für modellgesteuerte Apps aktiviert. Informationen zum Aktivieren dieser Funktion für Canvas-Apps finden Sie unter [Codekomponenten für Canvas-Apps](component-framework-for-canvas-apps.md).
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]
> - Canvas-Anwendungen unterstützen nur den Typ *Feld* der Codekomponenten und nicht den Typ *Datensatz*.

## <a name="how-its-different-from-webresources"></a>Unterschiede zu Webressourcen

 Im Gegensatz zu HTML-Webressourcen werden Codekomponenten als Teil desselben Kontextes dargestellt, der gleichzeitig mit allen anderen Komponenten geladen wird, was den Benutzern ein nahtloses Erlebnis bietet. Entwickler können alle HTML-, CSS- und TypeScript- oder JavaScript-Dateien in einer einzigen [Lösungs](https://docs.microsoft.com/dynamics365/customer-engagement/customize/solutions-overview)-Paketdatei bündeln und über Umgebungen hinweg verschieben und per [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=dynamics-365) versenden. Codekomponenten können mehrfach über verschiedene Entitäten und Formulare hinweg wiederverwendet werden. Nutzen Sie das Power Apps component framework, um Code-Komponenten zu erstellen, die bei allen Power Apps-Funktionen verwendet werden können.

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


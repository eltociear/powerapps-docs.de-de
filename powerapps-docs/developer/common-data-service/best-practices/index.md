---
title: 'Entwickler: Bewährte Methoden und Leitlinien für den Common Data Service | Microsoft-Dokumentation'
description: Bewährte Methoden und Anleitungen für Entwickler des Common Data Service in Power Apps.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/07/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 24a873eab99dc8e453d18f5bf32f1f5c56903008
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2883540"
---
# <a name="best-practices-and-guidance-for-the-common-data-service"></a>Bewährte Methoden sowie Anweisungen zum Common Data Service

Der Common Data Service ist ein erweiterbares Framework, das es Entwicklern ermöglicht, hochgradig individuelle und maßgeschneiderte Erfahrungen zu erstellen. Bei der Anpassung, Erweiterung oder Integration mit dem Common Data Service sollte sich ein Entwickler über die etablierten Richtlinien und bewährten Methoden im Klaren sein. 

In diesem Abschnitt erfahren Sie mehr über die von uns identifizierten Probleme, ihre Auswirkungen und verstehen die Leitlinien zu ihrer Lösung. Wir werden die Hintergründe erklären, warum die Dinge auf eine bestimmte Weise geschehen sollten und mögliche Probleme in der Zukunft vermeiden. Dies kann der Benutzerfreundlichkeit, der Supportfähigkeit und der Leistung Ihrer Umgebung zugute kommen. Die Anleitungsdokumentation unterstützt die vorhandenen Informationen innerhalb der Entwickler- und Administrationsleitfäden.

## <a name="targeted-customization-types"></a>Betroffene Anpassungsarten
Die Dokumentation richtet sich an die folgenden Anpassungsarten:

- Benutzerdefinierte Workflow-Aktivitäten und Plug-Ins
- Arbeiten mit Common Data Service-Daten
- Integrationen zur Erweiterung des Common Data Service

## <a name="sections"></a>Abschnitte
Jeder Leitartikel enthält die meisten oder alle der folgenden Abschnitte:

- Titel - Beschreibung des Leitfadens
- Kategorie - ein oder mehrere Bereiche, die von der Nichteinhaltung der Richtlinien betroffen sind.
- Wirkungspotential - das Ausmaß des Risikos (hoch, mittel oder niedrig), die Umwelt zu belasten, wenn die Leitlinien nicht eingehalten werden.
- Symptome - mögliche Anzeichen dafür, dass die Anweisungen nicht befolgt wurden.
- Anleitung - Empfehlungen, die auch Beispiele enthalten können.
- Problematische Muster - Beschreibung oder Beispiele für die Nichteinhaltung der Anleitung
- Zusatzinformationen - unterstützende Details für eine umfangreichere Ansicht
- Siehe auch - Referenzen, um mehr über etwas zu erfahren, das im Artikel erwähnt wird.

## <a name="categories"></a>Kategorien
Jeder Leitartikel wird in eine oder mehrere der folgenden Kategorien eingeteilt:

- Verwendung - unsachgemäße Verwendung einer bestimmten API, eines bestimmten Musters oder einer bestimmten Konfiguration.
- Design - Designfehler in einer Individualisierung
- Leistung - Anpassung oder Muster, die sich negativ auf die Leistung in Bereichen wie Speicherverwaltung, CPU-Auslastung, Netzwerkverkehr oder Benutzererfahrung auswirken können.
- Sicherheit - potenzielle Schwachstellen in einer Anpassung, die in einer Laufzeitumgebung genutzt werden können.
- Upgrade Readiness - Anpassung oder Muster, die das Risiko eines erfolglosen Versions-Upgrades erhöhen können.
- Online-Migration - Anpassung oder Muster, die das Risiko einer erfolglosen Online-Migration erhöhen können.
- Wartbarkeit - Anpassung, die den Aufwand für die Entwicklung von Änderungen, die Häufigkeit der erforderlichen Änderungen oder die Möglichkeit der Einführung von Regressionen unnötig erhöht.
- Supportfähigkeit - Anpassung oder Muster, die außerhalb der Grenzen veröffentlichter Supportfunktionen liegen, einschließlich der Verwendung entfernter APIs oder der Implementierung verbotener Techniken.

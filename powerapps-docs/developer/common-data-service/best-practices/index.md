---
title: 'Entwickler: Best Practices und Leitlinien für den Common Data Service for Apps | Microsoft Docs'
description: Best Practices und Anleitungen für Entwickler des Common Data Service for Apps in PowerApps.
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
---

# <a name="best-practices-and-guidance-for-the-common-data-service-for-apps"></a>Best Practices und Leitlinien für den Common Data Service for Apps

Der Common Data Service (CDS) for Apps ist ein erweiterbares Framework, das es Entwicklern ermöglicht, hochgradig individuelle und maßgeschneiderte Erfahrungen zu erstellen. Bei der Anpassung, Erweiterung oder Integration mit dem Common Data Service (CDS) for Apps sollte sich ein Entwickler über die etablierten Richtlinien und Best Practices im Klaren sein. 

In diesem Abschnitt erfahren Sie mehr über die von uns identifizierten Probleme, ihre Auswirkungen und verstehen die Leitlinien zu ihrer Lösung. Wir werden die Hintergründe erklären, warum die Dinge auf eine bestimmte Weise geschehen sollten und mögliche Probleme in der Zukunft vermeiden. Dies kann der Benutzerfreundlichkeit, der Supportfähigkeit und der Leistung Ihrer Umgebung zugute kommen. Die Anleitungsdokumentation unterstützt die vorhandenen Informationen innerhalb der Entwickler- und Administrationsleitfäden.

# <a name="targeted-customization-types"></a>Betroffene Anpassungsarten
Die Dokumentation richtet sich an die folgenden Anpassungsarten:

- Benutzerdefinierte Workflow-Aktivitäten und Plug-Ins
- Arbeiten mit CDS-Daten
- Integrationen zur Erweiterung des Common Data Service for Apps

# <a name="sections"></a>Abschnitte
Jeder Leitartikel enthält die meisten oder alle der folgenden Abschnitte:

- Titel - Beschreibung des Leitfadens
- Kategorie - ein oder mehrere Bereiche, die von der Nichteinhaltung der Richtlinien betroffen sind.
- Wirkungspotential - das Ausmaß des Risikos (hoch, mittel oder niedrig), die Umwelt zu belasten, wenn die Leitlinien nicht eingehalten werden.
- Symptome - mögliche Anzeichen dafür, dass die Anweisungen nicht befolgt wurden.
- Anleitung - Empfehlungen, die auch Beispiele enthalten können.
- Problematische Muster - Beschreibung oder Beispiele für die Nichteinhaltung der Anleitung
- Zusatzinformationen - unterstützende Details für eine umfangreichere Ansicht
- Siehe auch - Referenzen, um mehr über etwas zu erfahren, das im Artikel erwähnt wird.

# <a name="categories"></a>Kategorien
Jeder Leitartikel wird in eine oder mehrere der folgenden Kategorien eingeteilt:

- Verwendung - unsachgemäße Verwendung einer bestimmten API, eines bestimmten Musters oder einer bestimmten Konfiguration.
- Design - Designfehler in einer Individualisierung
- Leistung - Anpassung oder Muster, die sich negativ auf die Leistung in Bereichen wie Speicherverwaltung, CPU-Auslastung, Netzwerkverkehr oder Benutzererfahrung auswirken können.
- Sicherheit - potenzielle Schwachstellen in einer Anpassung, die in einer Laufzeitumgebung genutzt werden können.
- Upgrade Readiness - Anpassung oder Muster, die das Risiko eines erfolglosen Versions-Upgrades erhöhen können.
- Online-Migration - Anpassung oder Muster, die das Risiko einer erfolglosen Online-Migration erhöhen können.
- Wartbarkeit - Anpassung, die den Aufwand für die Entwicklung von Änderungen, die Häufigkeit der erforderlichen Änderungen oder die Möglichkeit der Einführung von Regressionen unnötig erhöht.
- Supportfähigkeit - Anpassung oder Muster, die außerhalb der Grenzen veröffentlichter Supportfunktionen liegen, einschließlich der Verwendung entfernter APIs oder der Implementierung verbotener Techniken.

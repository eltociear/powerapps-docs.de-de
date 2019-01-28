---
title: 'Entwickler: Best Practices und Handlungsempfehlungen für Common Data Service für Apps | Microsoft-Dokumentation'
description: Best Practices und Handlungsempfehlungen für Entwickler von Common Data Service für Apps in PowerApps.
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
ms.openlocfilehash: bf449f801e4e7617e7fe91d0884b3443559e71c6
ms.sourcegitcommit: 11486fb4c16095e3fef785126003cac3e3e06c0d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54271441"
---
# <a name="best-practices-and-guidance-for-the-common-data-service-for-apps"></a>Best Practices und Handlungsempfehlungen für Common Data Service für Apps

Common Data Service (CDS) für Apps ist ein erweiterbares Framework, mit dem Entwickler benutzerdefinierte und sehr individuelle Lösungen erstellen können. Bei der Anpassung, Erweiterung oder Integration von Common Data Service (CDS) für Apps sollten Entwickler bewährte Handlungsempfehlungen und Best Practices beachten. 

In diesem Abschnitt werden häufig auftretende Probleme, ihre Auswirkungen und Handlungsempfehlungen zur Lösung der Probleme beschrieben. Dabei werden auch die Hintergründe von Empfehlungen beschrieben. Zusätzlich lernen Sie, wie sich mögliche Probleme in der Zukunft vermeiden lassen. Dies kann sich positiv auf die Benutzerfreundlichkeit, Kompatibilität und Leistung Ihrer Umgebung auswirken. Die Dokumentation mit Handlungsempfehlungen ergänzt die vorhandenen Informationen in den Entwicklungs- und Verwaltungsleitfäden.

# <a name="targeted-customization-types"></a>Behandelte Anpassungstypen
In dieser Dokumentation werden die folgenden Anpassungstypen behandelt:

- benutzerdefinierte Workflowaktivitäten und Plug-Ins
- Arbeiten mit CDS-Daten
- Integrationen zur Erweiterung von Common Data Service für Apps

# <a name="sections"></a>Abschnitte
Jeder Artikel mit Handlungsempfehlungen enthält die meisten oder alle der folgenden Abschnitte:

- Titel: Beschreibung der Handlungsempfehlung
- Kategorie: ein oder mehrere Bereiche, die negativ betroffen sind, falls die Handlungsempfehlungen nicht berücksichtigt werden
- Gefährdungspotenzial: das Risiko (hoch, mittel oder niedrig) für negative Auswirkungen auf die Umgebung, falls die Handlungsempfehlungen nicht berücksichtigt werden
- Symptome: mögliche Anzeichen dafür, dass die Handlungsempfehlungen nicht berücksichtigt wurden
- Handlungsempfehlungen: Vorschläge, die gelegentlich auch Beispiele enthalten
- Problematische Muster: Beschreibungen oder Beispiele, in denen die Handlungsempfehlungen nicht berücksichtigt werden
- Zusätzliche Informationen: ergänzende Details für eine noch genauere Darstellung des Sachverhalts
- Siehe auch: Referenzmaterialien, in denen im Artikel erwähnte Themen vertieft werden

# <a name="categories"></a>Kategorien
Jeder Artikel mit Handlungsempfehlungen wird in eine oder mehrere der folgenden Kategorien eingeteilt:

- Verwendung: falsche Nutzung einer API, eines Musters oder einer Konfiguration
- Entwurf: Entwurfsfehler in einer Anpassung
- Leistung: Anpassungen oder Muster, die sich beispielsweise negativ auf die Leistung der Speicherverwaltung, der CPU-Auslastung, des Netzwerkdatenverkehrs oder der Servicequalität für Benutzer auswirken können
- Sicherheit: potenzielle Sicherheitsrisiken in einer Anpassung, die in einer Laufzeitumgebung unter Umständen ausgenutzt werden können
- Upgradebereitschaft: Anpassungen oder Muster, die das Risiko eines fehlerhaften Versionsupgrades erhöhen
- Onlinemigration: Anpassungen oder Muster, die das Risiko einer fehlerhaften Onlinemigration erhöhen
- Wartbarkeit: Anpassung, die den Entwicklungsaufwand zur Implementierung von Änderungen, die Häufigkeit von erforderlichen Änderungen oder die Wahrscheinlichkeit der Einführung von Regressionen unnötigerweise erhöht
- Kompatibilität: Anpassungen oder Muster, in denen veröffentlichte Kompatibilitätshinweise nicht berücksichtigt wurden. Dies kann sich beispielsweise in der Nutzung nicht mehr vorhandener APIs oder der Implementierung unzulässiger Methoden widerspiegeln

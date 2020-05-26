---
title: Überblick über die Regional Government Emergency Response and Monitoring-Lösung für Power Platform | Microsoft Docs
description: Bietet einen Überblick über die Regional Government Emergency Response and Monitoring-Lösung für staatliche und lokale Behörden.
author: KumarVivek
manager: annbe
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 05/06/2020
ms.author: kvivek
ms.reviewer: kvivek
searchScope:
- PowerApps
ms.openlocfilehash: e91dadf24010ebf1fcffbbe7000f3d622238abc5
ms.sourcegitcommit: 2e186321d124dd6c0a4b51df5e8bc94a83ccf1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "3342017"
---
# <a name="regional-governmentemergency-response-and-monitoring---power-platform-solution-for-state-and-local-governments"></a>Regional Government Emergency Response and Monitoring - Power Platform-Lösung für Landes- und Kommunalverwaltungen

Die Lösung für Emergency Response and Monitoring der Regionalregierung bietet eine Reihe von Funktionen, mit denen staatliche und lokale Behörden Gesundheitssystemdaten von allen übergeordneten Organisationen und angeschlossenen Krankenhäusern in ihrem Netzwerk oder ihrer Region sammeln und visualisieren können, um bei Notfalleinsätzen ein Situationsbewusstsein zu schaffen. Die Daten enthalten Informationen über verfügbare Betten, Verbrauchsmaterialien, Geräte, COVID-19-Patienten und Personal.

Die Hauptkomponenten der Regional Government Emergency Response and Monitoring-Lösung sind

- **Web App für Admins regionaler Organisationen**: Verwenden Sie die App, um die Stammdaten für jede übergeordnete medizinische Organisation im Staat oder in der Region zu verwalten, wobei jede übergeordnete medizinische Organisation ein oder mehrere Krankenhaussysteme hat, die Daten an die regionale medizinische Organisation melden. Der Admin der Regionalorganisation kann Admin-Benutzer für jede übergeordnete Organisation hinzufügen und verwalten, so dass letztere ein Web-Portal nutzen können, um Daten für ihre medizinische Organisation zu melden.

- **Webportal für Administratoren und Benutzer übergeordneter Unternehmen**: Administratoren übergeordneter Unternehmen können mit dem Webportal Benutzer in ihrem Unternehmen schnell hinzufügen und verwalten sowie Masterdaten für ihre Krankenhaussysteme, darunter Regionen und Einrichtungen, verwalten. Das Webportal wird auch von Mitarbeitern des Gesundheitswesens genutzt, um Daten zu Bettenkapazität, Personal, Ausrüstung, Verbrauchsmaterialien und COVID-19-Patienten schnell anzuzeigen, hinzuzufügen und zu verwalten.

- **Dashboards für Entscheidungsträger im Gesundheitswesen**: Verwenden Sie Dashboards, um wichtige Daten und Metriken schnell anzuzeigen, die Ihnen bei der effizienten Entscheidungsfindung helfen.
    - Admins regionaler Organisationen können das Dashboard in ihrem Power BI-Mandanten anzeigen.
    - Benutzer der übergeordneten Organisation können das Dashboard im Webportal anzeigen.

## <a name="demo-quick-overview"></a>Demo: Schnelle Übersicht

Sehen Sie sich einen kurzen Überblick über die Lösung an.

<br/>

> [!VIDEO https://www.youtube.com/embed/4WaniuC7pWs]

## <a name="licensing-requirements"></a>Lizenzanforderungen

- Power Apps-Plan zusammen mit Power Apps-Portal-Kapazität
- Power BI Premium- oder Pro-Lizenz

Wenden Sie sich an Ihren lokalen Microsoft-Kundenbetreuer, wenn Sie Fragen zur Lizenzierung gemäß Ihren Anforderungen haben.

Siehe auch: 
- [Lizenzierungsübersicht für Power Platform](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
- [Power Apps für US-Regierungsbehörden](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
- [Power BI für US-Regierungsbehörden](https://docs.microsoft.com/power-bi/service-govus-overview)

## <a name="start-here"></a>Starten Sie hier

|Aufgabe | Zielgruppe|Unter|
|--|--|--|
|Herunterladen und Bereitstellen der Beispiellösung und Einrichten von Benutzern und Sicherheit|Regionale Organisation IT-Admin|[Die Regional Government Emergency Response and Monitoring Lösung bereitstellen](deploy.md)|
|Upgrade der Beispiellösung (für Orgs mit bestehender Installation der Lösung)|Regionale Organisation IT-Admin|[Aktualisierung der Regional Government Emergency Response and Monitoring Lösung](upgrade.md)|
|Verwenden Sie die Admin App, um Stammdaten zu konfigurieren, Portalbenutzer anzulegen/zu verwalten und Dashboard anzuzeigen|Admin der Regionalorganisation|[Admin App und Dashboard verwenden](configure.md)|
|Verwenden Sie das Portal zum Hinzufügen/Verwalten von Portalbenutzern für ihre Krankenhäuser, zum Einrichten und Verwalten von Stammdaten für ihre Krankenhäuser und zum Anzeigen von Dashboard für Einblicke und Metriken.|Admin der übergeordneten Organisation|[Verwaltung des Regional Government Emergency Response and Monitoring Portals](portals-admin-reporting.md)|
|Verwenden Sie das Portal zum schnellen Anzeigen und Hinzufügen von Daten zu Bettenkapazität, Personal, Ausrüstung, Verbrauchsmaterialien und COVID-19-Patienten.|Mitarbeiter des Gesundheitswesens|[Nutzen Sie das Regional Government Emergency Response and Monitoring-Portal](portals-user.md)|


## <a name="issues-and-feedback"></a>Probleme und Feedback

- Um ein Problem mit der Lösung Regional Government Emergency Response and Monitoring zu melden, besuchen Sie <https://aka.ms/rer-issues>.

- Rückmeldungen über die Lösung Regional Government Emergency Response and Monitoring finden Sie unter <https://aka.ms/rer-feedback>.


### <a name="disclaimer"></a>Haftungsausschluss

Diese App ist ein Beispiel und darf mit Microsoft Power Platform nur zur Verbreitung von Referenzinformationen verwendet werden. Diese App ist nicht vorgesehen oder verfügbar gemacht für die Verwendung als Medizinprodukt, klinische Unterstützung, Diagnosewerkzeug oder andere Technologie, die zur Diagnose, Heilung, Linderung, Behandlung oder Vorbeugung von Krankheiten oder anderen Erkrankungen verwendet werden soll. Microsoft gewährt keine Lizenz oder kein Recht, diese App für solche Zwecke zu verwenden. Diese App ist nicht als Ersatz für professionelle medizinische Beratung, Diagnose, Behandlung oder Beurteilung konzipiert oder gedacht und sollte nicht als solche verwendet werden. Der Kunde trägt das alleinige Risiko und die alleinige Verantwortung für die Nutzung dieser App. Microsoft garantiert nicht, dass die App oder die in Verbindung damit bereitgestellten Materialien für medizinische Zwecke ausreichen oder die gesundheitlichen oder medizinischen Anforderungen einer Person erfüllen. Die in dieser App enthaltenen Beispieldaten dienen nur zur Veranschaulichung und sind fiktiv. Eine echte Vereinigung ist weder beabsichtigt noch wird daraus geschlossen.

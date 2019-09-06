---
title: App-Seite von ISV Studio | Microsoft Docs
description: 'Erfahren Sie mehr über die App-Seitenfunktionen, die vom ISV Studio-Portal bereitgestellt werden.'
services: ''
suite: powerapps
documentationcenter: na
author: phecke
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.reviewer: pehecke
ms.workload: na
ms.date: 07/11/2019
ms.author: prkoduku
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="the-app-page"></a>Die App-Seite

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Nachdem der Benutzer eine App ausgewählt hat, wird der Benutzer zur Detailseite der App geführt, die eine Ansicht zur Analyse der Installationshistorie in den Mandanten für diese bestimmte App bietet. Die Beschreibung der App stammt von [AppSource](https://appsource.microsoft.com/).

![App-Detailseite](media/isv-portal-apppage-appname.png)

Die App-Detailseite enthält die folgenden Diagramme und Metriken.

## <a name="successful-package-installs-by-environment-type"></a>Erfolgreiche Paketinstallationen nach Umgebungstyp

Das Kreisdiagramm unten zeigt das Verhältnis der Produktions- zu den Sandboxpaketinstallationen der ausgewählten App in der Installationsbasis an.

Beim Hovern über das Diagramm werden die folgenden Informationen angezeigt:

1. Organisationstyp – Produktion oder Sandbox
2. Anzahl der Paketinstallationen für den Organisationstyp

![Paketinstallationen nach Umgebungstyp](media/isv-portal-apppage-graph1.png)

## <a name="package-install-attempts-by-tenant-last-28-days"></a>Paketinstallationsversuche nach Mandant (letzte 28 Tage)

Das Balkendiagramm unten zeigt die Anzahl der erfolgreichen und fehlerhaften Paketinstallationen der ausgewählten App nach Mandant in den letzten 28 Tagen an.

Beim Hovern über ein Diagrammelement werden die folgenden Informationen angezeigt:

1. Mandantenname und Mandanten-ID
2. Status der Paketinstallation (erfolgreich und fehlerhaft) im Mandanten
3. Anzahl der Paketinstallationsversuche im Mandanten

![Paketinstallationsversuche nach Mandant (letzte 28 Tage)](media/isv-portal-apppage-graph2.png)

## <a name="successful-package-installs-by-location-of-tenants"></a>Erfolgreiche Paketinstallationen nach Standort von Mandanten

Die Zuordnung unten zeigt die geografische Verteilung der App nach Mandantenstandort.

Beim Hovern über eine Diagrammregion werden die folgenden Informationen angezeigt:

1. Standort
2. Anzahl der Paketinstallationen am ausgewählten Standort

![Paketinstallationen nach Standort von Mandanten](media/isv-portal-apppage-graph3.png)

## <a name="successful-package-and-version-installs-by-tenant"></a>Erfolgreiche Paket- und Versionsinstallationen nach Mandant

Das Säulendiagramm unten zeigt die eindeutigen Namen des Pakets an, wo Versionen der ausgewählten App in einem Dropdownmenü angezeigt werden. Alle Pakete werden standardmäßig ausgewählt, und alle installierten Versionen aller Pakete (nach Mandant) werden im Diagramm angezeigt. Der Benutzer kann ein oder mehrere Pakete und Versionen für die weitere Aufgliederung auswählen. Wenn der Benutzer ein Paket auswählt, wird das Versionsdropdownfeld aktualisiert, um die entsprechenden Versionen des ausgewählten Pakets zu erhalten.

Beim Hovern über ein Diagrammelement werden die folgenden Informationen angezeigt:

1. Mandantenname und Mandanten-ID
2. Paketversion
3. Anzahl der Paketinstallationen der Version im ausgewählten Mandanten


![Paket- und Versionsinstallationen nach Mandant](media/isv-portal-apppage-graph4.png)

### <a name="see-also"></a>Siehe auch

[Einführung in ISV Studio für die Power Platform](isv-app-management.md)  
[Homepage](isv-app-management-homepage.md)  
[Mandantenseite](isv-app-management-tenantpage.md)

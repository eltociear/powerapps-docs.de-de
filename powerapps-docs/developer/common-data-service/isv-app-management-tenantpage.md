---
title: Mandantenseite von ISV Studio | Microsoft Docs
description: 'Erfahren Sie mehr über die Mandantenseitenfunktionen, die vom ISV Studio-Portal bereitgestellt werden.'
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

# <a name="the-tenant-page"></a>Die Mandantenseite

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

Um die Installationshistorie eines Mandanten anzuzeigen, kann der ISV zur Ansicht **Die wichtigsten Mandanten** auf der Homepage wechseln und einen Mandanten auswählen.

![Installationshistorie eines Mandanten](media/isv-portal-homepage-tenantpivot.png)

Die Mandantenseite enthält die folgenden Diagramme und Metriken:

![Mandantenseite](media/isv-portal-tenantpage.png)

## <a name="successfully-installed-apps"></a>Erfolgreich installierte Apps

Das Kreisdiagramm unten veranschaulicht die ISV-App-Verteilung in allen Umgebungen im ausgewählten Mandanten.

Beim Hovern über die Diagrammelemente werden die folgenden Informationen angezeigt:

1. App-Name
2. Anzahl der Paketinstallationen der App im ausgewählten Mandanten

![Erfolgreich installierte Apps](media/isv-portal-tenantpage-graph1.png)

## <a name="successful-production-vs-sandbox-package-installs-by-environment"></a>Erfolgreiche Produktions- und Sandboxpaketinstallationen nach Umgebung

Das Balkendiagramm unten veranschaulicht die Produktions- und Sandboxinstallationen der ISV-Apps im ausgewählten Mandanten. Aus Datenschutzgründen kann der Umgebungsname hier nicht angezeigt werden.

Beim Hovern über ein Diagrammelement werden die folgenden Informationen angezeigt:

1. Umgebungs-ID
2. Umgebungstyp (Produktion oder Sandbox)
3. Anzahl der Paketinstallationen in der Umgebung

![Paketinstallationen nach Umgebungstyp](media/isv-portal-tenantpage-graph2.png)

## <a name="successful-package-installs-by-environment-location"></a>Erfolgreiche Paketinstallationen nach Umgebungsstandort

Die Zuordnung unten zeigt die geografische Verteilung der ISV-Paketinstallationen nach Umgebungsstandort.

Beim Hovern über einen Diagrammstandort werden die folgenden Informationen angezeigt:

1. Standort
2. Anzahl der Paketinstallationen am ausgewählten Standort

![Paketinstallationen nach Umgebungsstandort](media/isv-portal-tenantpage-graph3.png)

## <a name="successful-app-package-and-version-installs-by-environment"></a>Erfolgreiche App-Paket- und Versionsinstallationen nach Umgebung

Das Säulendiagramm unten zeigt die App-Namen, die eindeutigen Paketnamen und die Versionen des ausgewählten Mandanten in einem Dropdownmenü an. Alle Apps werden standardmäßig ausgewählt und ein ISV kann weitere Detailinformationen anzeigen, indem er eine oder mehrere Apps, Pakete und Versionen auswählt. Wenn der Benutzer eine App auswählt, wird das **Paket**-Dropdownfeld aktualisiert, um die entsprechenden Pakete der ausgewählten App anzuzeigen. Wenn der Benutzer ein Paket auswählt, wird das Dropdownfeld **Versionen** aktualisiert, um die entsprechenden Versionen des ausgewählten Pakets anzuzeigen.

Beim Hovern über ein Diagrammelement werden die folgenden Informationen angezeigt:

1. Umgebungs-ID
2. Paketversion
3. Anzahl der Paketinstallationen der Version in der Umgebung

![Paket- und Versionsinstallationen nach Umgebung](media/isv-portal-tenantpage-graph4.png)

### <a name="see-also"></a>Siehe auch

[Einführung in ISV Studio für die Power Platform](isv-app-management.md)  
[Homepage](isv-app-management-homepage.md)  
[App-Seite](isv-app-management-apppage.md)

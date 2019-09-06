---
title: Einführung in das Power Platform ISV Studio | Microsoft Docs
description: Erfahren Sie mehr über die Verwaltung und Unterstützung von Apps über das ISV Studio-Portal
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

# <a name="introduction-to-isv-studio-for-the-power-platform"></a>Einführung in ISV Studio für die Power Platform

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

ISV Studio wurde als bevorzugtes Power Platform-Ziel für unabhängige Softwarehersteller (Independent Software Vendors, ISV) konzipiert, um Anwendungen zu überwachen und zu verwalten. ISV Studio bietet eine zusammengefasste mandantenübergreifende Ansicht aller Anwendungen, die ein ISV an Kunden verteilt.

> [!IMPORTANT]
>
> - ISV Studio ist eine Vorschaufunktion.
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)]

ISV Studio unterstützt Anwendungen, die auf der Grundlage von Common Data Service erstellt und für [AppSource](https://appsource.microsoft.com/) veröffentlicht und darüber bereitgestellt werden. Für seitengeladene Lösungen, die nicht über AppSource bereitgestellt werden, wird keine Telemetrie zur Verfügung gestellt.

Die Anwendungen, die derzeit für Common Data Service verfügbar sind, umfassen PowerApps sowie Dynamics 365 for Sales, Marketing, Service und Talent.

Wenn ein Endbenutzer eine Anwendung von AppSource installiert, wird ein Zustimmungsdialogfeld angezeigt, das den Benutzer auffordert, anzuerkennen, dass die Kontakt-, Nutzungs- und Transaktionsinformationen für den Anwendungsanbieter freigegeben werden dürfen. Diese Informationen werden vom Anbieter verwendet, um Rechnungs- und andere Transaktionsaktivitäten zu unterstützen und Telemetrie in ISV Studio für den ISV zu ermöglichen, um Erkenntnisse zu gewinnen und diese in Aktionen umsetzen zu können.

Kunden können anfordern, dass diese Daten nicht für den Anbieter freigegeben werden. In diesem Fall entfernt Microsoft alle Daten aus diesem speziellen Mandanten in ISV Studio.

Um auf die öffentliche Vorschau von ISV Studio zuzugreifen, navigieren Sie über Ihren Browser zu [https://aka.ms/ISVStudio](https://aka.ms/ISVStudio/).

## <a name="pre-requisites"></a>Voraussetzungen

1. Der ISV muss einer registrierten Microsoft-Partnerorganisation [ISV] zugeordnet sein, von der mindestens eine unterstützte App in [AppSource](https://appsource.microsoft.com/) veröffentlicht wurde. Zu den unterstützen Apps zählen Dynamics 365 for Customer Engagement-Apps und PowerApps.

2. Der ISV muss über eine [Azure Active Directory](https://azure.microsoft.com/services/active-directory/) (AAD)-Firma verfügen und die Firma muss als App-Mitwirkender oder -Besitzer im Cloud-Partnerportal (CPP) für den jeweiligen ISV konfiguriert sein.

Wenn weitere Benutzer Zugriff auf ISV Studio erhalten sollen, können sie als App-Mitwirkende in CPP hinzugefügt werden.  Anweisungen finden Sie unter [Verwalten von Benutzern im Cloud-Partnerportal](https://docs.microsoft.com/en-us/azure/marketplace/cloud-partner-portal-orig/cloud-partner-portal-manage-users).

Fahren Sie mit den Seitenthemen „App“ und „Mandant“ unten fort, um mehr über die Funktionen von ISV Studio zu erfahren.

Bitte senden Sie eine E-Mail an [ISVFeedback@microsoft.com](mailto:ISVFeedback@microsoft.com) mit Ihrem Feedback oder Ihren Fragen. Ihr Feedback ist wichtig für uns, damit wir die Erfahrung weiter verbessern können.

## <a name="in-this-section"></a>In diesem Abschnitt

[Homepage](isv-app-management-homepage.md)  
[App-Seite](isv-app-management-apppage.md)  
[Mandantenseite](isv-app-management-tenantpage.md)

### <a name="see-also"></a>Siehe auch

[Einführung in Lösungen](introduction-solutions.md)  
[App auf AppSource veröffentlichen](publish-app-appsource.md)

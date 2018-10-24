---
title: Anzeigen oder Herunterladen von Entwicklerressourcen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie nach Entwicklerressourcen und Dienstendpunkt-URLs suchen.
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.openlocfilehash: ae93b57d9ead3a62fb538ae986eb524367259545
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688098"
---
<!-- TODO: The Developer Resources page have to be updated to match this page -->

# <a name="view-or-download-developer-resources"></a>Anzeigen oder Herunterladen von Entwicklerressourcen

Diese Seite stellt Ressourcen für Entwickler und Informationen zu bestimmten Instanzen, an denen Sie arbeiten, zur Verfügung. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Anzeigen der Seite „Entwicklerressourcen“ für Ihre Umgebung

1. Wählen Sie im PowerApps-Portal die Schaltfläche „Einstellungen“ ![Schaltfläche „Einstellungen“](../../administrator/media/settings-button-nav-bar.png) und anschließend **Erweiterte Anpassungen** aus.

    ![Erweiterte Anpassungen](media/advanced-customizations-menu.png)

1. Wählen Sie im Bereich **Erweiterte Anpassungen** den Link **Entwicklerressourcen** aus:<br />![Link „Entwicklerressourcen“](media/developer-resources-link.png)

## <a name="getting-started"></a>Erste Schritte 

Dieser Abschnitt enthält Links für Entwickler, damit sie Ressourcen finden. Die folgenden Ressourcen sind verfügbar:


|Link |Beschreibung|
|---------|---------|
|[Developer Center](https://go.microsoft.com/fwlink/?LinkId=551006)|Der wichtigste Einstiegspunkt für die Dokumentation für Entwickler.|
|[Entwicklerforen](https://go.microsoft.com/fwlink/?LinkId=550993)|Hier können Sie sich mit anderen Entwicklern austauschen, Fragen stellen und beantworten.|
|[NuGet-Pakete](https://go.microsoft.com/fwlink/?LinkId=550994)|Untersuchen Sie NuGet-Pakete, um Ihren Projekten SDK-Assemblys hinzuzufügen.|
|[Downloadtools](https://go.microsoft.com/fwlink/?LinkID=512122)|Tools, die Sie benötigen, können Sie bei NuGet herunterladen. Verwenden Sie das PowerShell-Skript auf dieser Seite, um die neuesten Versionen abzurufen.|
|[Beispielcode](https://go.microsoft.com/fwlink/?LinkId=553007)|Eine Liste der verfügbaren Beispiele.|
|[Entwicklerübersicht](https://go.microsoft.com/fwlink/?LinkId=550995)|Link zu einem Thema, das einen Überblick für Entwickler bietet.|

<!-- TODO update 512122 to go to https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget -->


## <a name="connect-your-apps-to-this-instance-of-common-data-service-for-apps"></a>Verbinden von Apps mit dieser Instanz von Common Data Service für Apps

Dieser Abschnitt enthält nützliche Informationen, damit Sie eine Verbindung mit Ihrer Instanz von Common Data Service für Apps herstellen.

### <a name="instance-web-api"></a>Web-API der Instanz

Dies ist die URL für die Web-API Ihrer Instanz. Bei der Web-API handelt es sich um eine OData v4 RESTful-API. Sie können auch das Dienstdokument herunterladen, das die in Ihrer Instanz verfügbaren Metadaten und Vorgänge beschreibt. Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Verwenden der Web-API von Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api).

### <a name="organization-service"></a>Organisationsdienst

Dies ist die URL für den SOAP-Endpunkt des Organisationsdiensts für Ihre Instanz.
Sie können die WSDL für diesen Dienst hier herunterladen, doch i.d.R. wird das Codegenerierungstool „CrmSvcUtil.exe“ zum Erstellen von Entitätsklassen für .NET-Projekte verwendet. Weitere Informationen finden Sie unter: 
- [Dokumentation für Entwickler: Erstellen von Entitätsklassen mit früher Bindung mithilfe des Codegenerierungstools (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)
- [Dokumentation für Entwickler: Verwenden des Organisationsdiensts zum Lesen und Schreiben von Daten oder Metadaten](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)

### <a name="instance-reference-information"></a>Referenzinformationen für Instanzen

Diese Informationen beschreiben Ihre Instanz eindeutig. Es gibt eine GUID-**ID** und einen **Eindeutigen Namen**.
Diese Informationen sind erforderlich, wenn Sie Azure-Erweiterungen mit Ihrer Instanz verwenden.
Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Azure-Erweiterungen für Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions).

## <a name="connect-your-apps-to-the-common-data-service-for-apps-discovery-service"></a>Verbinden von Apps mit dem Ermittlungsdienst von Common Data Service für Apps

Da Benutzer ggf. Zugriff auf mehrere Umgebungen von Common Data Service für Apps haben, lassen sich mit den Ermittlungsdiensten die verfügbaren Umgebungen abrufen, auf die ein Benutzer aufgrund seiner Anmeldeinformationen zugreifen kann.

### <a name="discovery-web-api"></a>Web-API des Ermittlungsdiensts

Dies ist die Endpunktadresse für die RESTful-OData v4-Version des Ermittlungsdienstes, die für Ihre Instanz verwendet wird. Sie können das Dienstdokument auch hier herunterladen.
Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Ermitteln der URL für Ihre Organisation mit der Web-API](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api).


### <a name="discovery-service"></a>Ermittlungsdienst

Dies ist die Endpunktadresse für die SOAP-Version des Ermittlungsdiensts, die für Ihre Instanz verwendet wird. Sie können das Dienstdokument auch hier herunterladen.
Weitere Informationen finden Sie unter [Dokumentation für Entwickler: Ermitteln der URL für Ihre Organisation mit dem Ermittlungsdienst](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service).
  
### <a name="more-information"></a>Weitere Informationen

[Dokumentation für Entwickler: Entwicklerressourcenseite](/dynamics365/customer-engagement/developer/developer-resources-page)<br />
[Dokumentation für Entwickler: Verwenden der Web-API von Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)<br />
[Dokumentation für Entwickler: Verwenden des Organisationsdiensts zum Lesen und Schreiben von Daten oder Metadaten](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)<br />
[Dokumentation für Entwickler: Azure-Erweiterungen für Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)<br />
[Dokumentation für Entwickler: Ermitteln der URL für Ihre Organisation mit der Web-API](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)<br />
[Dokumentation für Entwickler: Ermitteln der URL für Ihre Organisation mit dem Ermittlungsdienst](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  


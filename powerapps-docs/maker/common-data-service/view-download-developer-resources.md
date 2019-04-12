---
title: Anzeigen oder Herunterladen von Entwicklerressourcen | MicrosoftDocs
description: Suchen Sie Entwicklerressourcen und Serviceendpunkt URLs
keywords: ''
ms.date: 06/06/2018
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
<!-- TODO: The Developer Resources page have to be updated to match this page -->

# <a name="view-or-download-developer-resources"></a>Anzeigen oder Herunterladen von Entwicklerressourcen

Diese Seite bietet Ressourcen für Entwickler und Informationen über die spezifische Instanz, an der Sie arbeiten. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Zeigen Sie die Entwicklerressourceseite für Ihre Umgebung an

1. Wählen Sie im PowerApps-Portal die Einstellungs-Schaltfläche ![Einstellungs-Schaltfläche](../../administrator/media/settings-button-nav-bar.png) und wählen Sie **Erweiterte Anpassungen** aus.

    ![Erweiterte Anpassungen](media/advanced-customizations-menu.png)

1. Innerhalb des Bereichs **Erweiterte Anpassungen** wählen Sie den Link **Entwicklerressourcen** aus:<br />![Entwicklerressourcen-Link](media/developer-resources-link.png)

## <a name="getting-started"></a>Erste Schritte 

Dieser Abschnitt enthält Links für Entwickler zum Finden von Ressourcen. Die folgenden Ressourcen stehen zur Verfügung:


|Link |Beschreibung|
|---------|---------|
|[Developer Center](https://go.microsoft.com/fwlink/?LinkId=551006)|Der zentrale Einstieg in die Dokumentation für Entwickler.|
|[Entwicklerforen](https://go.microsoft.com/fwlink/?LinkId=550993)|Tauschen Sie Fragen und Antworten mit anderen Entwicklern aus.|
|[NuGet Pakete](https://go.microsoft.com/fwlink/?LinkId=550994)|Entdecken Sie NuGet-Pakete, um SDK-Assemblies zu Ihren Projekten hinzuzufügen.|
|[Tools herunterladen](https://go.microsoft.com/fwlink/?LinkID=512122)|Tools, die Sie benötigen, können Sie bei NuGet herunterladen. Verwenden Sie das PowerShell-Skript auf dieser Seite, um die neuesten Versionen zu erhalten.|
|[Beispielcode](https://go.microsoft.com/fwlink/?LinkId=553007)|Eine Liste der verfügbaren Beispiele.|
|[Entwicklerübersicht](https://go.microsoft.com/fwlink/?LinkId=550995)|Verknüpfen Sie sich mit einem Thema, um eine Übersicht für Entwickler zu erhalten.|

<!-- TODO update 512122 to go to https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget -->


## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Verbinden Sie Ihre Apps mit dieser Instanz von Common Data Service.

Dieser Abschnitt enthält Informationen, die Sie benötigen, um eine Verbindung zu Ihrem Common Data Service herzustellen.

### <a name="instance-web-api"></a>Instanz-Web-API

Dies ist die URL für das Web-API Ihrer Instanz. Das Web-API ist eine OData v4 RESTful API. Sie können auch das Servicedokument herunterladen, das die in Ihrer Instanz verfügbaren Metadaten und Operationen beschreibt. Weitere Informationen: [Dokumentation für Entwickler: Verwenden Sie das Dynamics 365 Customer Engagement Web API](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)

### <a name="organization-service"></a>Organisationsdienst

Dies ist die URL für den SOAP-Endpunkt des Organisationsservice Ihrer Instanz.
Sie können die WSDL für diesen Dienst hier herunterladen, aber normalerweise werden Sie das Codegenerierungstool CrmSvcUtil.exe verwenden, um Entitätsklassen für .NET-Projekte zu erstellen. Weitere Informationen: 
- [Dokumentation für Entwickler: Entitätsklassen mit früher Bindung mit dem Codegenerierungstool erstellen (CrmSvcUtil.exe)](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)
- [Dokumentation für Entwickler: Verwenden des Organisationsdienstes, um Daten oder Metadaten zu lesen und zu schreiben](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)

### <a name="instance-reference-information"></a>Instanzreferenzinformationen

Diese Informationen beschreiben eindeutig Ihre Instanz. Es gibt eine GUID **ID** und **Eindeutiger Name**.
Diese Informationen werden benötigt, wenn Sie Azure-Erweiterungen mit Ihrer Instanz verwenden.
Weitere Informationen: [Dokumentation für Entwickler: Azure-Erweiterungen für Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>Verbinden Sie Ihre Apps mit dem Common Data Service-Suchdienst.

Da Personen Zugriff auf mehrere Common Data Service-Umgebungen haben können, ermöglichen die Suchdienste das Abrufen der verfügbaren Umgebungen, auf die eine Person basierend auf ihren Benutzerdaten zugreifen kann.

### <a name="discovery-web-api"></a>Suchdienst-Web-API

Dies ist die Endpunktadresse für die RESTful OData v4-Version des Suchdienstes, die für Ihre Instanz verwendet werden soll. Sie können das Servicedokument auch hier herunterladen.
Weitere Informationen: [Dokumentation für Entwickler: Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Suchdienst

Dies ist die Endpunktadresse für die SOAP-Version des Suchdienstes, die für Ihre Instanz verwendet werden soll. Sie können das Servicedokument auch hier herunterladen.
Weitere Informationen: [Dokumentation für Entwickler: Ermitteln Sie die URL für Ihre Organisation mithilfe des Suchdienstes](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
### <a name="more-information"></a>Weitere Informationen

[Dokumentation für Entwickler: Entwicklerressourceseite](/dynamics365/customer-engagement/developer/developer-resources-page)<br />
[Dokumentation für Entwickler: Verwenden Sie das Dynamics 365 Customer Engagement Web API](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)<br />
[Dokumentation für Entwickler: Verwenden des Organisationsdienstes, um Daten oder Metadaten zu lesen und zu schreiben](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)<br />
[Dokumentation für Entwickler: Azure-Erweiterungen für Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/azure-extensions)<br />
[Dokumentation für Entwickler: Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)<br />
[Dokumentation für Entwickler: Ermitteln Sie die URL für Ihre Organisation mithilfe des Suchdienstes](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  


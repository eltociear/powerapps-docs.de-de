---
title: Anzeigen oder Herunterladen von Entwicklerressourcen für PowerApps und Common Data Service | MicrosoftDocs
description: Finden Sie Entwicklerressourcen und Service-Endpunkt-URLs für PowerApps und Common Data Service.
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

# <a name="view-or-download-developer-resources"></a>Anzeigen oder Herunterladen von Entwicklerressourcen

Diese Seite bietet Ressourcen für Entwickler und Informationen über die spezifische Instanz, an der Sie arbeiten. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Zeigen Sie die Entwicklerressourceseite für Ihre Umgebung an

1. Wählen Sie im Portal PowerApps die Schaltfläche ![Einstellungsschaltfläche](../../administrator/media/settings-button-nav-bar.png) Einstellungen und wählen Sie **Erweiterte Anpassungen**.

    ![Erweiterte Anpassungen](media/advanced-customizations-menu.png)

1. Innerhalb des Bereichs **Erweiterte Anpassungen** wählen Sie den Link **Entwicklerressourcen** aus:<br />![Entwicklerressourcen-Link](media/developer-resources-link.png)

## <a name="getting-started"></a>Erste Schritte 

Dieser Abschnitt enthält Links für Entwickler zum Finden von Ressourcen. Die folgenden Ressourcen stehen zur Verfügung:


|Link |Beschreibung|
|---------|---------|
|[Developer Center](https://go.microsoft.com/fwlink/?LinkId=551006)|Der zentrale Einstieg in die Dokumentation für Entwickler.|
|[Entwicklerforen](https://go.microsoft.com/fwlink/?LinkId=550993)|Tauschen Sie Fragen und Antworten mit anderen Entwicklern aus.|
|[NuGetPakete](https://go.microsoft.com/fwlink/?LinkId=550994)|Finden Sie NuGet-Pakete, um SDK-Assemblies zu Ihren Projekten hinzuzufügen.|
|[Tools herunterladen](https://go.microsoft.com/fwlink/?LinkID=512122)|Tools, die Sie benötigen, können Sie unter NuGet herunterladen. Verwenden Sie das PowerShell-Skript auf dieser Seite, um die neuesten Versionen zu erhalten.|
|[Beispielcode](https://go.microsoft.com/fwlink/?LinkId=553007)|Eine Liste der verfügbaren Beispiele.|
|[Entwicklerübersicht](https://go.microsoft.com/fwlink/?LinkId=550995)|Verknüpfen Sie sich mit einem Thema, um eine Übersicht für Entwickler zu erhalten.|


## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>Verbinden von Apps mit dieser Instanz von Common Data Service

Dieser Abschnitt enthält Informationen, die Sie für die Verbindung zu Ihrer Common Data Service-Instanz benötigen.

### <a name="instance-web-api"></a>Instanz-Web-API

Dies ist die URL für das Web-API Ihrer Instanz. Das Web-API ist eine OData v4 RESTful API. Sie können auch das Servicedokument herunterladen, das die in Ihrer Instanz verfügbaren Metadaten und Operationen beschreibt. Mehr Informationen: [Dokumentation für Entwickler: Verwenden Sie die Common Data Service Web API](/powerapps/developer/common-data-service/webapi/overview).

### <a name="organization-service"></a>Organisationsdienst

Dies ist die URL für den SOAP-Endpunkt des Organisationsservice Ihrer Instanz.
Sie können die WSDL für diesen Dienst hier herunterladen, aber normalerweise werden Sie das Codegenerierungstool CrmSvcUtil.exe verwenden, um Entitätsklassen für .NET-Projekte zu erstellen. Weitere Informationen: 
- [Dokumentation für Entwickler: Entitätsklassen mit früher Bindung mit dem Codegenerierungstool erstellen (CrmSvcUtil.exe)](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [Dokumentation für Entwickler: Verwenden Sie den Organisationsservice](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>Instanzreferenzinformationen

Diese Informationen beschreiben eindeutig Ihre Instanz. Es gibt eine GUID **ID** und **Eindeutiger Name**.
Diese Informationen werden benötigt, wenn Sie Azure-Erweiterungen mit Ihrer Instanz verwenden.
Mehr Informationen: [Azure-Integration](/powerapps/developer/common-data-service/azure-integration)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>Verbinden Sie Ihre Apps mit dem Common Data Service Discovery Service.

Da Personen möglicherweise Zugriff auf mehrere Common Data Service-Umgebungen haben, können mit den Discovery Services die verfügbaren Umgebungen abgerufen werden, auf die eine Person basierend auf ihren Benutzerdaten zugreifen kann.

### <a name="discovery-web-api"></a>Suchdienst-Web-API

Dies ist die Endpunktadresse für die RESTful OData v4-Version des Suchdienstes, die für Ihre Instanz verwendet werden soll. Sie können das Servicedokument auch hier herunterladen.
Weitere Informationen: [Dokumentation für Entwickler: Ermitteln Sie die URL für Ihre Organisation mithilfe der Web-API](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>Suchdienst

Dies ist die Endpunktadresse für die SOAP-Version des Suchdienstes, die für Ihre Instanz verwendet werden soll. Sie können das Servicedokument auch hier herunterladen.
Mehr Informationen: [Dokumentation für Entwickler: Finden Sie die URL für Ihr Unternehmen mit dem Organisationsservice](/powerapps/developer/common-data-service/org-service/discovery-service).
  
  


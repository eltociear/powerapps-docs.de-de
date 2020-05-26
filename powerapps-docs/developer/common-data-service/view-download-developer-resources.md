---
title: Anzeigen oder Herunterladen von Entwicklerressourcen für Power Apps und Common Data Service | MicrosoftDocs
description: Finden Sie Entwicklerressourcen und Service-Endpunkt-URLs für Power Apps und Common Data Service.
keywords: ''
ms.date: 04/09/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: pehecke
ms.suite: ''
ms.tgt_pltfrm: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bd3b907411d0e43b572908204aeff9c64069ed15
ms.sourcegitcommit: cbaf5ba8b6435796a538ece2da5cc172c0781fad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "3254400"
---
# <a name="view-or-download-developer-resources"></a>Anzeigen oder Herunterladen von Entwicklerressourcen

Diese Seite bietet Ressourcen für Entwickler und Informationen über die spezifische Instanz, an der Sie arbeiten. 

## <a name="view-the-developer-resources-page-for-your-environment"></a>Zeigen Sie die Entwicklerressourceseite für Ihre Umgebung an

1. Melden Sie sich bei [Power Apps](https://make.powerapps.com) an und wählen Sie Ihre Umgebung in der oberen rechten Ecke aus.

1. Wählen Sie in der oberen rechten Ecke die Schaltfläche **Einstellungen** aus und wählen Sie **Erweiterte Einstellungen** aus.

    ![Erweiterte Anpassungen](media/advanced-customizations-menu.png)

1. Wählen Sie auf der Seite **Einstellungen** den Dropdownpfeil neben **Einstellungen** aus und wählen Sie **Anpassungen** aus.

    ![Anpassungen auswählen](media/dev-customization.png)

1. Wählen Sie auf der Seite **Anpassungen** die Option **Entwicklerressourcen** aus, um die Seite mit Ressourcen und Entwicklern anzuzeigen.

    ![Entwicklerressourcenseite](media/developer-resources-page.png)

In den folgenden Abschnitten werden alle Informationen erläutert, die auf der Entwicklerressourcenseite verfügbar sind.

## <a name="getting-started"></a>Erste Schritte 

Dieser Abschnitt enthält Links für Entwickler zum Finden von Ressourcen. Die folgenden Ressourcen stehen zur Verfügung:


|Link |Beschreibung|
|---------|---------|
|[Developer Center](https://go.microsoft.com/fwlink/?LinkId=551006)|Der zentrale Einstieg in die Dokumentation für Entwickler.|
|[Entwicklerforen](https://go.microsoft.com/fwlink/?LinkId=550993)|Tauschen Sie Fragen und Antworten mit anderen Entwicklern aus.|
|[SDK NuGet-Pakete](https://go.microsoft.com/fwlink/?LinkId=550994)|Finden Sie NuGet-Pakete, um SDK-Assemblies zu Ihren Projekten hinzuzufügen.|
|SDK-Download|Wir liefern das SDK-Paket nicht mehr als Download im Microsoft Download Center. Stattdessen sind die SDK-Assemblys und -Tools als [NuGet-Pakete](https://go.microsoft.com/fwlink/?LinkId=550994) verfügbar. Verwenden Sie das PowerShell-Skript in diesem Artikel, um die neueste Version der SDK-Tools zu erhalten: [Tools von NuGet herunterladen](https://docs.microsoft.com/powerapps/developer/common-data-service/download-tools-nuget)|
|[Beispielcode](https://go.microsoft.com/fwlink/?LinkId=553007)|Eine Liste der verfügbaren Codebeispiele.|
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

Dies ist die Endpunktadresse für die SOAP-Version des Discovery Service, die Sie für Ihre Instanz verwenden können. Sie können das Servicedokument auch hier herunterladen.
Mehr Informationen: [Dokumentation für Entwickler: Finden Sie die URL für Ihr Unternehmen mit dem Organisationsservice](/powerapps/developer/common-data-service/org-service/discovery-service).
  
  


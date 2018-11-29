---
title: 'Verwenden der Common Data Service für Apps-Web-API-Hilfe-Bibliothek (C#) (Common Data Service für Apps) | Microsoft Docs'
description: 'Die Common Data Service für Apps-Web-API-Hilfe-Bibliothek unterstützt Sie bei der Durchführung allgemeiner Aufgaben wie Anwendungskonfiguration, Authentifizierung mit einem Common Data Service für Apps-Dienst und HTTP-Antwort-Fehlerbehandlung'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: ba9d94fe-d189-4873-aef5-0010f3ccecba
caps.latest.revision: 7
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-the-common-data-service-for-apps-web-api-helper-library-c"></a>Verwenden der Common Data Service für Apps-Web-API-Hilfe-Bibliothek (C#)

Die meisten Common Data Service für Apps-Web-API (C#)-Codebeispiele, die in dieser SDK beschrieben werden, verwenden die *Common Data Service für Apps-Web-API-Hilfe-Bibliothek*, um beim Ausführen allgemeiner Aufgaben zu unterstützen, wie beispielsweise der Anwendungskonfiguration, der Authentifizierung anhand eines Common Data Service für Apps-Services und der HTTP-Antwort-Fehlerbehandlung. Dieser Hilfecode ist möglicherweise nützlich in Ihren .Net Framework-basierten Projekten.  
  
## <a name="obtain-and-use-the-helper-library"></a>Hilfebibliothek erwerben und nutzen

Die Common Data Service für Apps-Web-API-Hilfe-Bibliothek wird als NuGet-Paket [Microsoft.CrmSdk.WebApi.Samples.HelperCode](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode) verteilt. Wenn Sie mit Downloading und dem Installieren von NuGet-Paketen in Visual Studio-Projekten nicht vertraut sind, finden Sie im folgenden Abschnitt weitere Informationen: [Fügen Sie dem Projekt alle benötigten Ressourcen hinzu](start-web-api-project-visual-studio-csharp.md#bkmk_addAllRequiredResources).  
  
> [!WARNING]
>  Dieses NuGet-Paket ist die maßgebende Quelle für die Hilfebibliothek.  Die Themen in diesem Abschnitt enthalten zudem eine Codeliste für jede Klasse in der Hilfebibliothek. Allerdings sind die Listen möglicherweise nicht vollständig oder aktuell und sollten deshalb nicht in Projekten verwendet werden.  
  
## <a name="in-this-section"></a>Inhalt dieses Abschnitts 
 
[Hilfscode: Konfigurationsklassen](web-api-helper-code-configuration-classes.md)<br />
[Hilfecode: Authentifizierungsklasse](web-api-helper-code-authentication-class.md)<br /> 
[Hilfecode: CrmHttpResponseException class](web-api-helper-code-crmhttpresponseexception-class.md)  
  
### <a name="see-also"></a>Siehe auch
 
[Erste Schritte mit dem Web API (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Starten eines Web-API-Projekts in Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)

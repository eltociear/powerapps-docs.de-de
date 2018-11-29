---
title: Arbeiten mit Daten mithilfe von Code in Common Data Service für Apps (PowerApps) | Microsoft Docs
description: 'CDS für Apps bietet zwei Webdienste, die Sie verwenden können, um mit Daten zu interagieren: Web-API und Organisationsdienst.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="work-with-data-using-code-in-common-data-service-for-apps"></a>Arbeiten mit Daten mithilfe von Code in Common Data Service für Apps

Common Data Service (CDS) für Apps verfügt über [Entitäten](entities.md), die verwendet werden, um Geschäftsdaten zu modellieren und zu verwalten. Sie können Standardentitäten verwenden oder Ihre eigenen benutzerdefinierten Entitäten erstellen, um Daten zu speichern. 

## <a name="use-web-services-to-work-with-data"></a>Webdienste zum Arbeiten mit Daten verwenden

CDS für Apps bietet zwei Webdienste, die Sie verwenden können, um mit Daten zu interagieren: **Web-API** und **Organisationsdienst**. Wählen Sie den, der den Anforderungen und Ihren Qualifikationen am Besten entspricht. 

![Flussdiagramm, um den Webdienst auszuwählen](media/whentousewebapi.png)

### <a name="web-api"></a>Web-API

Das Web-API ist ein OData v4 RESTful-Endpunkt. Verwenden Sie dies für jede beliebige Programmiersprache, die HTTP-Anforderungen und Authentifizierung mithilfe von OAuth 2.0 unterstützt.

Weitere Informationen: [Verwenden des Common Data Service für Apps-Web-API](webapi/overview.md) 

### <a name="organization-service"></a>Organisationsdienst

Verwenden Sie die .NET Framework-SDK-Assemblys für Projekte, bei denen Plug-Ins oder Workflowerweiterungen geschrieben werden müssen. 

Weitere Informationen: [Verwenden des Common Data Service für Apps-Organisationsdiensts](org-service/overview.md)

> [!NOTE]
> Verwenden Sie die Xrm-Tooling-Assemblys, wenn Sie eine Windows-Client-Anwendung erstellen. Weitere Informationen: [Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](xrm-tooling/build-windows-client-applications-xrm-tools.md)

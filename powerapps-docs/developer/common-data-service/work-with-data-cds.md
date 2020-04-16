---
title: Arbeiten mit Daten mit Hilfe von Code in Common Data Service (PowerApps) | Microsoft-Dokumentation
description: 'Common Data Service bietet zwei Webdienste, die Sie verwenden können, um mit Daten zu interagieren: Web-API und Organisationsdienst.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 3da5976eba337c6b816f7414403876f3470b77ea
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154910"
---
# <a name="work-with-data-using-code-in-common-data-service"></a>Arbeiten mit Daten mit Hilfe von Code in Common Data Service

Common Data Service verfügt über [Entitäten](entities.md), die verwendet werden, um Geschäftsdaten zu modellieren und zu verwalten. Sie können Standardentitäten verwenden oder Ihre eigenen benutzerdefinierten Entitäten erstellen, um Daten zu speichern. 

## <a name="use-web-services-to-work-with-data"></a>Webdienste zum Arbeiten mit Daten verwenden

Common Data Service bietet zwei Webdienste, die Sie verwenden können, um mit Daten zu interagieren: **Web-API** und **Organisationsdienst**. Wählen Sie den, der den Anforderungen und Ihren Qualifikationen am Besten entspricht. 

![Flussdiagramm, um den Webdienst auszuwählen](media/whentousewebapi.png)

### <a name="web-api"></a>Web-API

Das Web-API ist ein OData v4 RESTful-Endpunkt. Verwenden Sie dies für jede beliebige Programmiersprache, die HTTP-Anforderungen und Authentifizierung mithilfe von OAuth 2.0 unterstützt.

Weitere Informationen: [Verwenden der Common Data Service-Web-API](webapi/overview.md) 

### <a name="organization-service"></a>Organisationsdienst

Verwenden Sie die .NET Framework-SDK-Assemblys für Projekte, bei denen Plug-Ins oder Workflowerweiterungen geschrieben werden müssen. 

Weitere Informationen: [Verwenden des Common Data Service-Organisationsdienstes](org-service/overview.md)

> [!NOTE]
> Verwenden Sie die Xrm-Tooling-Assemblys, wenn Sie eine Windows-Client-Anwendung erstellen. Weitere Informationen: [Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](xrm-tooling/build-windows-client-applications-xrm-tools.md)

---
title: Beispiele für Web-API-Datenvorgänge (Common Data Service) | Microsoft Docs
description: 'Das "Common Data Service"-SDK bietet eine Matrix von Beispielen, die zeigen, wie die Web-API auf mehrere unterschiedliche Arten verwendet wird. Sie finden hier die C#- und JavaScript-Implementierungen grundlegender Operationen, Abfragedaten, bedingter Operationen sowie Beispiele für Funktionen und Aktionen'
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: cdcb02f5-3baa-4fb7-8fb3-6fe53c2d4271
caps.latest.revision: 11
author: brandonsimons
ms.author: jdaly
ms.reviewer: susikka
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-data-operations-samples"></a>Beispiele für Web-API-Datenvorgänge

Sie können die "Common Data Service"-Web-API mit einer Vielzahl von Programmiersprachen oder - bibliotheken verwenden. Dieser Leitfaden bietet eine Matrix von Beispielen, die zeigen, wie die Web-API auf mehrere unterschiedliche Arten verwendet wird. In diesem Thema sind Beispiele enthalten, die für jede Gruppe verfügbar sind und zeigen, wie diese Vorgänge mithilfe verschiedener Sprachen oder Verwendungen ausgeführt werden.

<!-- TODO:
> [!NOTE]
> With the availability of the new [Xrm.WebApi](../clientapi/reference/xrm-webapi.md) client API methods, we are working on updating the client-side JavaScript samples to use the new client API methods. Check back soon.   -->
  
## <a name="web-api-sample-matrix"></a>Web API Beispielmatrix

Die folgende Tabelle beschreibt die "Common Data Service"-Web-API-Beispiele und die sprachspezifischen Implementierungen.  
  
|Sprachunabhängige Beschreibung|C# Implementierung|Clientseitiges JavaScript-Implementierung|  
|-----------------------------------|------------------------|--------------------------------------------|  
|[Web-API-Beispiele](web-api-samples.md) (dieses Thema)|[Web API Beispiele (C#)](web-api-samples-csharp.md)|[Web API Beispiele (Clientseitiges JavaScript)](web-api-samples-client-side-javascript.md)|  
<!-- TODO:
|[Web API Basic Operations Sample](web-api-basic-operations-sample.md)|[Web API Basic Operations Sample (C#)](samples/basic-operations-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|  
|[Web API Query Data Sample](web-api-query-data-sample.md)|[Web API Query Data Sample (C#)](samples/query-data-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|   
|[Web API Conditional Operations Sample](web-api-conditional-operations-sample.md)|[Web API Conditional Operations Sample (C#)](samples/conditional-operations-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|  
|[Web API Functions and Actions Sample](web-api-functions-actions-sample.md)|[Web API Functions and Actions Sample (C#)](samples/functions-actions-csharp.md)|Under construction. See [Xrm.WebApi](../clientapi/reference/xrm-webapi.md)|  -->
  
 Die folgenden Tabellen kategorisieren die Beispielthemen durch die dargelegten Gruppen und durch Implementierungsprobleme.  
  
### <a name="groups-of-operations"></a>Gruppen von Vorgängen
 
Die folgende Tabelle klassifiziert die Beispiele von veranschaulichte Vorgangsgruppen.  
  
|Gruppe|Beschreibung|  
|-----------|-----------------|  
|[Beispiel grundlegender Web-API-Operationen](web-api-basic-operations-sample.md)|Wie Sie grundlegende CRUD- (Erstellen, abrufen, aktualisieren und löschen) und dazugehörende Vorgänge ausführen.<br /><br /> Weitere Informationen: <br /><br /> -   [Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />-   [Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />-   [Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />-   [Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)|  
|[Web API-Abfragedatenbeispiel](web-api-query-data-sample.md)|Wie Sie grundlegende Abfragenanforderungen ausführen.<br /><br /> Weitere Informationen: <br /><br /> -   [Datenabfrage mit Web-API](query-data-web-api.md)<br />-   [Abrufen und Ausführen von vordefinierten Abfragen](retrieve-and-execute-predefined-queries.md)|  
|[Beispiel bedingter Web-API-Operationen](web-api-conditional-operations-sample.md)|Wie bestimmte Kategorien von Vorgängen ausgeführt werden, die auf der Version des Entitätsdatensatzes basiert, die sich auf dem Server befindet und/oder vom Kunden derzeit gewartet wird. Weitere Informationen: [Ausführen bedingter Vorgänge mit der Web-API](perform-conditional-operations-using-web-api.md).|  
|[Web API-Funktionen- und Aktionen-Beispiel](web-api-functions-actions-sample.md)|So verwenden Sie gebundene/ungebundene Funktionen und Aktionen, einschließlich benutzerdefinierte Aktionen.<br /><br /> Weitere Informationen: <br /><br /> -   [Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />-   [Nutzen von Web-API-Aktionen](use-web-api-actions.md)|  
  
### <a name="language-or-library"></a>Sprache oder Bibliothek
 
Die folgende Tabelle enthält Themen, die standardsprachliche oder bibliotheksspezifische Implementierungsprobleme enthalten.  
  
|Sprache oder Bibliothek|Beschreibung|  
|-------------------------|-----------------|  
|[Web API Beispiele (C#)](web-api-samples-csharp.md)|Beschreibt allgemeine Elemente, die in dieser Gruppe von C#-Beispielen verwendet werden, die grundlegende .NET-Klassen zeigen und minimale Hilfebibliotheken enthalten.|  
|[Web API Beispiele (Clientseitiges JavaScript)](web-api-samples-client-side-javascript.md)|Im Aufbau.|  
  
### <a name="see-also"></a>Siehe auch

[Common Data Service-Web-API verwenden](overview.md)<br />
[Beispiel grundlegender Web-API-Operationen](web-api-basic-operations-sample.md)<br />
[Web API-Abfragedatenbeispiel](web-api-query-data-sample.md)<br />
[Beispiel bedingter Web-API-Operationen](web-api-conditional-operations-sample.md)<br />
[Web API-Funktionen- und Aktionen-Beispiel](web-api-functions-actions-sample.md)<br />
[Web API Beispiele (C#)](web-api-samples-csharp.md)<br />

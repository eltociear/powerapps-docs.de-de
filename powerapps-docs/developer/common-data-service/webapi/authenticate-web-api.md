---
title: Authentifizierung beim Common Data Service mit der Web-API (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie über die unterschiedlichen Wege, wie die Authentifizierung zu verwalten, wenn Sie die Web-API verwenden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: susikka
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 767f39d4-6a8e-48f0-bf7d-69ea1191acef
caps.latest.revision: 8
author: brandonsimons
ms.author: jdaly
manager: annbe
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="authenticate-to-common-data-service-with-the-web-api"></a>Authentifizierung beim Common Data Service mit der Web-API


Sie müssen OAuth, wie in [OAuth mit Common Data Service verwenden](../authenticate-oauth.md) beschrieben verwenden.

Der Code, den Sie schreiben, um die Authentifizierung bei Verwendung der Web-API zu verwalten, hängt vom Typ der Bereitstellung und davon ab, wo sich der Code befindet.  
  
### <a name="authenticate-with-javascript-in-web-resources"></a>Mit JavaScript in Webressourcen authentifizieren  

Wenn Sie die Web-API mit JavaScript innerhalb von HTML-Webressourcen, Formularskripts oder Menübandbefehlen verwenden, brauchen Sie keinen Code für die Authentifizierung aufnehmen. In jedem dieser Fälle wird bereits der Benutzer mithilfe der Anwendung authentifiziert und die Authentifizierung wird von der Anwendung verwaltet.  

Wenn Sie eine Einzelseitenanwendung (SPA) mithilfe von JavaScript erstellen, können Sie die adal.js-Bibliothek so verwenden, wie in [Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung zu verbinden](../oauth-cross-origin-resource-sharing-connect-single-page-application.md) beschrieben ist.  
  
### <a name="see-also"></a>Siehe auch
 
[Common Data Service-Web-API verwenden](overview.md)<br />
[Internet API-Typen und -Vorgänge](web-api-types-operations.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[OAuth mit Common Data Service verwenden](../authenticate-oauth.md)<br />
[Verwenden von OAuth mit Cross-Origin Resource Sharing, um eine Single Page-Anwendung zu verbinden](../oauth-cross-origin-resource-sharing-connect-single-page-application.md)

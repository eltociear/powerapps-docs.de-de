---
title: Zugriff auf externe Webservices (Common Data Service) | MicrosoftDocs
description: Erfahren Sie, wie Sie über ein benutzerdefiniertes Plug-in oder eine Workflow-Aktivität auf einen Webservice zugreifen können.
ms.custom: ''
ms.date: 8/19/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b236ba63a4e82f5969c5496af58a5aa015b89a1b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748265"
---
# <a name="access-external-web-services"></a>Zugriff auf externe Webservices

Plug-Ins und benutzerdefinierte Workflowaktivitäten können über die Protokolle HTTP und HTTPS auf das Netzwerk zugreifen. Diese Funktion bietet Unterstützung für den Zugriff auf gängige Webdienste wie Social Sites, Newsfeeds, Webservices und mehr. Die folgenden Internet-Zugriffsbeschränkungen gelten für diese Sandboxfunktion.  
  
- Nur die HTTP- und HTTPS-Protokolle sind erlaubt.
- Der Zugriff auf localhost (Loopback) ist nicht erlaubt.
- IP-Adressen können nicht verwendet werden. Sie müssen eine benannte Internetadresse verwenden, die die DNS-Namensauflösung erfordert.
- Anonyme Authentifizierung wird unterstützt und empfohlen. Es gibt keine Vorkehrung für die Aufforderung des angemeldeten Benutzers zur Eingabe oder zum Speichern von Anmeldeinformationen.

Andere Methoden des Zugriffs auf Webdienste sind die Verwendung von Webhooks und die [!INCLUDE [pn_azure_service_bus](../../includes/pn_azure_service_bus.md)]. Weitere Informationen zu diesen Themen finden Sie unter den untenstehenden Links.

## <a name="how-to-access-external-web-services"></a>So greifen Sie auf externe Webservices zu

Heute sind die meisten Menschen mit der [System.Net.Http.HttpClient-Klasse](/dotnet/api/system.net.http.httpclient) vertraut. `HttpClient` wurde mit .NET 4.5 eingeführt und bietet umfassende Funktionen im Vergleich zur [System.Net.WebClient-Klasse](/dotnet/api/system.net.webclient), die jedoch weiterhin verfügbar ist.

Für neue Plug-Ins sollten Sie `HttpClient` verwenden, weil [das .NET-Team WebClient nicht für die Neuentwicklung empfiehlt](/dotnet/api/system.net.webclient?#remarks). Dies bedeutet jedoch nicht, dass Sie in älterem Code jedes Vorkommen von `WebClient` ersetzen müssen. Die meisten der Vorteile von `HttpClient` gelten nicht notwendigerweise innerhalb eines Plug-Ins. `HttpClient` dient zur Wiederverwendung und ist standardmäßig asynchron. Sofern Sie nicht mehrere HTTP-Anforderungen innerhalb des Plug-Ins senden, gilt `WebClient` für eine einzige Anforderung. Da `HttpClient` standardmäßig asynchron ist, müssen Sie von typischen Gebrauchsmustern Abstand nehmen und Code hinzufügen, der erzwingt, dass die Vorgänge synchron durchgeführt werden. Dies geschieht in der Regel durch Entfernen des Schlüsselworts `await` und Anhängen von `.Result` an jeden asynchronen Aufruf.

`WebClient` bietet einfache synchrone Methoden wie z. B. [UploadData](/dotnet/api/system.net.webclient.uploaddata), [DownloadFile](/dotnet/api/system.net.webclient.downloadfile), die die zugrunde liegende verwendete HTTP-Methode nicht klar offenlegen. Sie können jedoch durch bestimmte Übersteuerungen festgelegt werden, darunter z. B. [UploadString(String, String, String)](/dotnet/api/system.net.webclient.uploadstring#System_Net_WebClient_UploadString_System_String_System_String_System_String_), wenn Sie nicht `PATCH` anstelle von `POST` verwenden möchten.

In den meisten Fällen werden Sie außerhalb von Plug-Ins `HttpClient` verwenden. Innerhalb von Plug-Ins können Sie auch `WebClient` verwenden, wenn Sie dies vorziehen.

## <a name="best-practices"></a>Bewährte Methoden

Gemäß den folgenden Themen zu bewährten Methoden:

- [KeepAlive auf falsch setzen, wenn Sie mit externen Hosts in einem Plug-in interagieren](best-practices/business-logic/set-keepalive-false-interacting-external-hosts-plugin.md)
- [Timeout festlegen, wenn externe Aufrufe in einem Plug-In getätigt werden](best-practices/business-logic/set-timeout-for-external-calls-from-plug-ins.md)

Sie müssen sicherstellen, dass ein angemessener `Timeout`-Zeitraum für Ihre externen Aufrufe festgelegt und `KeepAlive` deaktiviert wird. Weitere Informationen finden Sie in diesen Themen.


## <a name="see-also"></a>Siehe auch

[Plug-Ins](plug-ins.md)<br />
[Workflowerweiterungen](workflow/workflow-extensions.md)<br />
[Azure-Integration](azure-integration.md)<br />
[Web-Hooks verwenden](use-webhooks.md)<br />
[Beispiel: Webzugriff über ein Sandkasten-Plug-In](org-service/samples/web-access-plugin.md)

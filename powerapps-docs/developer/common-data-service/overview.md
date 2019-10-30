---
title: Entwicklerhandbuch zu Common Data Service | Microsoft Docs
description: 'Erfahren Sie, wie Entwickler mithilfe des Common Data Service einen Wertzusatz bewirken können.'
author: JimDaly
manager: annbe
ms.service: powerapps
ms.topic: article
ms.date: 03/27/2019
ms.author: jdaly
ms.reviewer: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="common-data-service-developer-guide"></a>Entwicklerhandbuch zu Common Data Service

PowerApps bietet Benutzern, Unternehmen, unabhängigen Softwareherstellern (Independent Software Vendors, ISVs) und Systemintegratoren (SIs) eine leistungsfähige Plattform zum Erstellen von Unternehmens-Apps. **Common Data Service** ist die zugrunde liegende Datenplattform für PowerApps, die die Kernfunktion der [Dynamics 365 für Customer Engagement-Plattform ](/dynamics365/customer-engagement/developer/developer-guide) beinhaltet, z. B. serverseitige Logik (Plug-Ins und Workflows), Geschäftsprozessflüsse, ein hochkomplexes Sicherheitsmodell und eine erweiterbare Plattform für Entwickler, um Apps zu erstellen.

> [!NOTE]
> Dies bedeutet effektiv, dass Common Data Service auch die zugrunde liegende Plattform for Customer Engagement-Apps wie Dynamics 365 for Sales, Dynamics 365 for Customer Service und Dynamics 365 for Marketing ist. Wenn Sie bereits mit Dynamics 365 for Customer Engagement-Apps vertraut sind, werden sich diese Erfahrung zu Nutze machen können, um Common Data Service anzupassen und zu erweitern, um Apps zu erstellen. 

Es gibt zahlreiche Aspekte, wie Entwickler zur Erstellung von Apps beitragen können, die Common Data Service verwenden. Während es möglich ist, eine Anwendung mit Code mithilfe von Common Data Service für die Datenquelle zu erstellen, nutzen die meisten Projekte entweder [modellgestützte](/powerapps/maker/model-driven-apps/model-driven-app-overview) Apps oder [Canvas-Apps](/powerapps/maker/canvas-apps/getting-started), um die Umgebung zu generieren, die Personen verwenden. 

## <a name="working-with-model-driven-apps"></a>Verwenden von modellgestützten Apps

Modellgestützte Apps werden auf Common Data Service erstellt und können nur eine Verbindung mit der Common Data Service-Umgebung herstellen. Alle Daten, die eine modellgestützte App definieren, werden im Common Data Service gespeichert.

Modellgestützte Apps teilen die Methode zum Verteilen von Anpassungen und Erweiterungen, die von Common Data Service mit [Lösungen](introduction-solutions.md) verwendet werden.

Modellgestützte Apps bieten auch einige Möglichkeiten für Entwickler, um Code für Erweiterungen zu schreiben. Weitere Informationen darüber, was Entwickler mit modellgestützten Apps vornehmen können, finden Sie unter [Entwicklerhandbuch für modellgestützte Apps ](../model-driven-apps/overview.md)

## <a name="understand-when-to-write-code"></a>Erfahren Sie, wann Sie Code schreiben müssen

Weil Common Data Service viele Funktionen umfasst, damit Benutzer angepasste Geschäftslogik konfigurieren können, ohne Code zu verfassen, können Entwickler am besten beitragen, indem Sie die Stellen füllen, in denen die vorhandenen Funktionen nicht die Funktionalität bereitstellen, um bestimmte Anforderungen zu erfüllen. Glücklicherweise enthält Common Data Service viele Punkte für Entwickler, um die allgemeine Funktionen mithilfe von Code zu erweitern.

Für einen Entwickler, der zu einem Projekt beiträgt, ist es wichtig, dass er versteht, was erreicht werden kann, ohne Code zu schreiben. Sie sollten sich mit diesen Features vertraut machen. Weitere Informationen finden Sie unter [Neuheiten bei Common Data Service](../../maker/common-data-service/data-platform-intro.md) 

## <a name="content-for-on-premises-deployments"></a>Inhalt für lokale Bereitstellungen:

Common Data Service ist derzeit nicht für lokale Bereitstellungen verfügbar. Der Inhalt dieses Handbuch enthält keine Informationen zur Unterstützung von Optionen, die nur lokal oder mit Internetzugriff Bereitstellung (IFD) verfügbar sind. Für Informationen in Zusammenhang mit diesen Optionen finden Sie unter [Entwicklerhandbuch für Dynamics 365 for Customer Engagement-Apps](/dynamics365/customer-engagement/developer/developer-guide)

> [!div class="nextstepaction"]
> [Erste Schritte](get-started-cds-developers.md)

### <a name="see-also"></a>Siehe auch

[PowerApps für Entwickler](/powerapps/#pivot=home&panel=developer)<br/>
[Entwicklerhandbuch zu modellgestützten Apps](../model-driven-apps/overview.md)

---
title: Common Data Service Entwicklerhandbuch | Microsoft Docs
description: 'Erfahren Sie, wie Entwickler mit Common Data Service Mehrwert schaffen können.'
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

# <a name="common-data-service-developer-guide"></a>Common Data Service Entwicklerhandbuch

PowerApps bietet Anwendern, Unternehmen, unabhängigen Softwareanbietern (ISVs) und Systemintegratoren (SIs) eine leistungsstarke Plattform für den Aufbau von Branchenanwendungen. **Common Data Service** ist die zugrunde liegende Datenplattform für PowerApps, die die Kernfunktionalitäten wie serverseitige Logik (Plugins und Workflows), Geschäftsprozessabläufe, ein hoch entwickeltes Sicherheitsmodell und eine erweiterbare Plattform für Entwickler zum Erstellen von Anwendungen enthält. 

Es gibt viele Aspekte, wie Entwickler zur Erstellung von Apps mit Common Data Service beitragen können. Während es möglich ist, eine Anwendung mit Code unter Verwendung von Common Data Service als Datenquelle zu erstellen, werden die meisten Projekte entweder [modellgesteuerte Anwendungen](/powerapps/maker/model-driven-apps/model-driven-app-overview) oder [Canvas-Anwendungen](/powerapps/maker/canvas-apps/getting-started) verwenden, um die Erfahrung zu generieren, die die Menschen nutzen werden. 

## <a name="working-with-model-driven-apps"></a>Verwenden von Modell-angetriebenen Apps

Modellgetriebene Anwendungen basieren auf Common Data Service und können sich nur mit einer Common Data Service Umgebung verbinden. Alle Daten, die eine modellgetriebene App definieren, werden in Common Data Service gespeichert.

Modellgetriebene Anwendungen teilen sich die Methode der Verteilung von Anpassungen und Erweiterungen, die von Common Data Service verwendet werden, mit [Lösungen](introduction-solutions.md).

Modell angetriebene Apps haben auch einige Punkte für Entwickler Codes zu schreiben und zu erweitern. Informationen darüber, was Entwickler mit modellgetriebenen Anwendungen machen können, finden Sie unter [Entwicklerhandbuch für modellgetriebene Anwendungen](../model-driven-apps/overview.md).

Einige Beispiele für modellgetriebene Anwendungen, die von Microsoft erhältlich sind, sind [Dynamics 365 Customer Service](https://docs.microsoft.com/dynamics365/customer-service/help-hub), [Dynamics 365 Field Service](https://docs.microsoft.com/dynamics365/field-service/overview) und [Dynamics 365 Marketing](https://docs.microsoft.com/dynamics365/marketing/help-hub).

## <a name="understand-when-to-write-code"></a>Erfahren Sie, wann Sie Code schreiben müssen

Da Common Data Service viele Möglichkeiten für Personen beinhaltet, benutzerdefinierte Geschäftslogik zu konfigurieren, ohne Code zu schreiben, sind die häufigsten Szenarien für Entwickler, die dazu beitragen, Leerräume dazwischen zu füllen, in denen bestehende Funktionen möglicherweise keine Funktionalität bieten, die Sie benötigen, um eine Anforderung zu erfüllen. Glücklicherweise bietet Common Data Service viele Punkte für Entwickler, um die gängige Funktionalität durch Code zu erweitern.

Bei einem Entwickler, der zu einem Projekt beiträgt, ist es wichtig, dass sie informieren, welche abgeschlossen werden können, ohne Code zu schreiben. Sie sollten sich mit diesen Features vertraut sein. Mehr Informationen: [Was ist Common Data Service?](../../maker/common-data-service/data-platform-intro.md) 

## <a name="content-for-on-premises-deployments"></a>Inhalt für lokale Bereitstellungen:

Common Data Service ist derzeit nicht für On-Premise-Bereitstellungen verfügbar. Der Inhalt dieses Handbuch enthält keine Informationen zur Unterstützung von Optionen, die nur lokal oder mit Internetzugriff Bereitstellung (IFD) verfügbar sind. Informationen zu diesen Optionen finden Sie im [Entwicklerleitfaden für Dynamics 365 Customer Engagement (on-premises))](/dynamics365/customer-engagement/on-premises/developer/overview).

> [!div class="nextstepaction"]
> [Erste Schritte](get-started-cds-developers.md)

### <a name="see-also"></a>Siehe auch

[PowerApps für Entwickler](/powerapps/#pivot=home&panel=developer)<br/>
[Entwicklerhandbuch zu modellgestützten Apps](../model-driven-apps/overview.md)

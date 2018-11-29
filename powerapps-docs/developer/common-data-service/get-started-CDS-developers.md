---
title: 'Entwickler: Erste Schritte mit Common Data Service for Apps | MicrosoftDocs'
description: 'Erfahren Sie, wie Entwickler Wert mithilfe des Common Data Service für Apps in PowerApps hinzufügen können.'
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="developers-get-started-with-common-data-service-for-apps"></a>Entwickler: Erste Schritte mit Common Data Service für Apps

Es gibt zahlreiche Aspekte, wie Entwickler zur Erstellung von Apps beitragen können, die  Common Data Service (CDS) für Apps verwenden. Während es möglich ist, eine Anwendung mit Code mithilfe von CDS für Apps für die Datenquelle zu erstellen, nutzen die meisten Projekte entweder Modell-angetriebene Apps oder Canvas-Apps, um die Erfahrung zu generieren, die Personen verwenden. 

## <a name="working-with-model-driven-apps"></a>Verwenden von Modell-angetriebenen Apps

Modell-angetriebene Apps werden auf CDS für Apps erstellt. Eine Modell-angetriebene App kann sich nur mit einer CDS nur für App-Umgebung verbinden und alle Daten, die Modell-angetriebene App definieren, werden in der CDS für Apps gespeichert.

Modell-angetriebene Apps teilen die Methode zum Verteilen von Anpassungen und Erweiterungen, die von CDS Apps verwendet werden: Lösungen. Weitere Informationen zu Lösungen finden Sie unter [Einführung in Lösungen](introduction-solutions.md).

Modell angetriebene Apps haben auch einige Punkte für Entwickler Codes zu schreiben und zu erweitern. Weitere Informationen darüber, was Entwickler mit Modell-angetriebenen Apps vornehmen können, finden Sie unter [Modell-angetriebene Apps Entwickler-Übersicht](../model-driven-apps/overview.md)

## <a name="understand-when-to-write-code"></a>Erfahren Sie, wann Sie Code schreiben müssen

Weil CDS für Apps viele Funktionen umfassen, damit Benutzer angepasste Geschäftslogik konfigurieren können, ohne Code zu verfassen, sind die gängigsten Szenarien für Entwickler , Leerzeichen beizutragen, die unter Umständen auch Auswirkungen auf vorhandene Features haben, die nicht von der Funktionalität bereitgestellt werden, um bestimmte Anforderungen zu erfüllen. Glücklicherweise enthält CDS für Apps Punkte für Entwickler, um  die allgemeine Funktionen mithilfe des Codes zu erweitern.

Bei einem Entwickler, der zu einem Projekt beiträgt, ist es wichtig, dass sie informieren, welche abgeschlossen werden können, ohne Code zu schreiben. Sie sollten sich mit diesen Features vertraut sein. Weitere Informationen finden Sie unter [Neuheiten bei Common Data Service für Apps?](../../maker/common-data-service/data-platform-intro.md)

## <a name="where-to-begin"></a>Wo beginnen?

Wo beginnen hängt vom Problem ab, das Sie lösen möchten. Es enthält ein großes Angebot an Inhalten bezüglich Funktionen und es ist unwahrscheinlich, dass alle verwendet werden. Das folgende enthält mehrere Schlüsselschlüsselbereiche, um zu beginnen.

> [Verwenden von Daten mithilfe von Webservices](#work-with-data-using-web-services)<br/>
> [Geschäftslogik anwenden](#applying-business-logic)<br/>
> [CDS für App-Entitäten](#cds-for-apps-entities)<br/>
> [Arbeiten mit Metadaten](#work-with-metadata)<br/>
> [Packen und Verteilen von Erweiterungen mithilfe von Lösungen](#use-solutions-to-package-and-distribute-extensions)<br/>
> [Erstellen von Clientanwendungen und Authentifizierung](#create-client-applications-and-authentication)<br/>
> [Inhalt für lokale Bereitstellungen:](#content-for-on-premises-deployments)<br/>

### <a name="work-with-data-using-web-services"></a>Verwenden von Daten mithilfe von Webservices

Es gibt zwei verschiedene Webdienste, die Sie verwenden können, um die Daten zu verwenden. Welche Sie verwenden können, hängt vom Typ des Projektumfangs ab, mit dem Sie arbeiten. Weitere Informationen: [Arbeiten mit Daten mithilfe von Code](work-with-data-cds.md).

### <a name="applying-business-logic"></a>Geschäftslogik anwenden

Die meisten allgemeinen Erweiterungen, die mit Code erstellt werden, umfassen automatische Prozesse mithilfe von Unternehmen. Sie können eine Zusammenfassung der Optionen finden, die für Sie verfügbar sind [Wenden Sie Geschäftslogik von Code an](apply-business-logic-with-code.md). Jeder dieser Ansätze wird normalerweise nach Ereignissen ausgelöst, die auf dem Server ausgeführt werden, und das [Ereignisframework](event-framework.md) ist dann von Nutzen.

### <a name="cds-for-apps-entities"></a>CDS für App-Entitäten

Entitäten speichern die Geschäftsdaten, die Sie verwenden. Ein Verständnis, was sie sind und wie Sie mit ihnen arbeiten, ist von größter Bedeutung.
Weitere Informationen:

- [Common Data Service für Apps-Entitäten](entities.md)
- [Über die Entitätsreferenz](reference/about-entity-reference.md)

### <a name="work-with-metadata"></a>Arbeiten mit Metadaten

Ein gutes Verständnis der Metadaten im System hilft dabei zu verstehen, wie CDS für Apps-Plattform funktioniert. Im Allgemeinen können Sie die Designers hinzufügen, aktualisieren oder löschen, die Metadaten definiert, aber sowohl Web API und Organisationsservicewebdienste bieten Funktionen, um CRUD-Vorgänge auf dem Entitätsschema auszuführen. Weitere Informationen: [Arbeiten mit Metadaten mithilfe von Code](metadata-services.md). 

### <a name="use-solutions-to-package-and-distribute-extensions"></a>Packen und Verteilen von Erweiterungen mithilfe von Lösungen

Wenn Sie die Aktivität zu den Erweiterungen verteilen, die Sier erstellen oder Anpassungen, die davon abhängen, müssen Sie die Lösungen verstehen. Die Lösungen, die von einer Person erstellt wurden, sind verhältnismäßig einfach, und erfodern keine Fähigkeiten eines Entwicklers. Aber ein Team von Entwicklern, mit Lösungen und Verwendungs-Anwendungin der Lebenszyklus-Verwaltungsprinzipien produktiv zum Verwenden eines entwickelteren Methode. Weitere Informationen:

 - [Einführung in Lösungen](introduction-solutions.md)
 - [SolutionPackager ToolSolutionPackager tool](compress-extract-solution-file-solutionpackager.md)
 - [Package Deployer tool](./package-deployer/create-packages-package-deployer.md)
 - [Veröffentlichen Sie die App für AppSource](publish-app-appsource.md)

### <a name="create-client-applications-and-authentication"></a>Erstellen von Clientanwendungen und Authentifizierung

Wenn Sie Erweiterungen erstellen, um die Geschäftslogik auf dem Server anzuwenden, müssen Sie keinen Code zur authentifizieren integrieren. Die Authentifizierung ist nur erforderlich, wenn Sie eine Clientanwendung erstellen. Eine einfache Konsolen-Client-Anwendung ist eine gute Methode, sich mit den CDS für App-APIs vertraut machen. Das Aktivieren von Möglichkeiten, um sich mit Daten zu verbinden, ist ein wichtiger erster Schritt. Die meisten Codebeispiele, die gespeichert werden, enthalten Wege zur Authentifizierung. Der Xrm.Toolings-Konnektor stellt Funktionen bereit, die Authentifizierung zu vereinfachen. Weitere Informationen:

- [Authentifizierung](authentication.md)
- [Erstellen von Client-Anwendungen](connect-cds.md)
- [Schnellstart: Erstellen einer Konsolen-App mithilfe des Organisationsservice](org-service/quick-start-org-service-console-app.md)
- [Schnellstart: Web API Beispiel (C#)](webapi/quick-start-console-app-csharp.md)
- [Beispiel: Schnellstart für XRM Tooling API](xrm-tooling/sample-quick-start-xrm-tooling-api.md)

## <a name="content-for-on-premises-deployments"></a>Inhalt für lokale Bereitstellungen:

CDS für Apps ist nicht für lokale Bereitstellungen verfügbar. Der Inhalt dieses Handbuch enthält keine Informationen zur Unterstützung von Optionen, die nur lokal oder mit Internetzugriff Bereitstellung (IFD) verfügbar sind. Für Informationen in Zusammenhang zu den Optionen, gehen Sie zu [Software Entwicklungs-Kit für Microsoft Dynamics 365 (online) und Dynamics 365 (on-premises)](https://msdn.microsoft.com/library/hh547453.aspx)
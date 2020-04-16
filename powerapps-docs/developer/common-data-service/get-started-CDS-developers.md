---
title: 'Entwickler: Erste Schritte mit Common Data Service | Microsoft Docs'
description: Erfahren Sie, wie Entwickler Wert mithilfe des Common Data Service in Power Apps hinzufügen können.
suite: powerapps
author: JimDaly
manager: ryjones
ms.service: powerapps
ms.date: 08/05/2019
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bfc3415d95e8861cdd2ba4c4835e453c0ddc2720
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156190"
---
# <a name="developers-get-started-with-common-data-service"></a>Entwickler: Erste Schritte mit Common Data Service

Wo zu beginnen hängt vom Problem ab, das Sie lösen möchten. Es enthält ein großes Angebot an Informationen bezüglich Funktionen und es ist unwahrscheinlich, dass alle verwendet werden. Der folgende Abschnitt umfasst mehrere Schlüsselschlüsselbereiche, um zu beginnen.

## <a name="work-with-data-using-web-services"></a>Verwenden von Daten mithilfe von Webservices

Es gibt zwei verschiedene Webdienste, die Sie verwenden können, um mit Daten zu arbeiten: **Web-API** und **Organisationsdienst**. 

Welche Sie verwenden können, hängt vom Typ des Projektumfangs ab, mit dem Sie arbeiten. Weitere Informationen: [Arbeiten mit Daten mithilfe von Code](work-with-data-cds.md).

## <a name="applying-business-logic"></a>Geschäftslogik anwenden

Die meisten allgemeinen Erweiterungen, die mit Code erstellt werden, umfassen automatische Prozesse mithilfe von Unternehmen. Sie können eine Zusammenfassung der Optionen finden, die für Sie verfügbar sind [Wenden Sie Geschäftslogik von Code an](apply-business-logic-with-code.md). Jeder dieser Ansätze wird normalerweise nach Ereignissen ausgelöst, die auf dem Server ausgeführt werden, und das [Ereignisframework](event-framework.md) ist dann von Nutzen.

## <a name="integrate-with-external-data"></a>Integration in externe Daten

Datenverwaltungsfunktionen in Common Data Service lassen Sie nicht nur mit Daten innerhalb von Common Data Service arbeiten, sondern auch effektiv mit externen Daten interagieren, die für ein Unternehmen von entscheidender Bedeutung sind. Weitere Informationen: 

- [Importieren von Daten](/powerapps/developer/common-data-service/import-data)
- [Synchronisieren von Daten](/powerapps/developer/common-data-service/data-synchronization)
- [Virtuelle Entitäten](/powerapps/developer/common-data-service/virtual-entities/get-started-ve)
- [Azure-Integration](/powerapps/developer/common-data-service/azure-integration)
- [Webhooks](/powerapps/developer/common-data-service/use-webhooks
)

## <a name="common-data-service-entities"></a>Common Data Service-Entitäten

Entitäten speichern die Geschäftsdaten, die Sie verwenden. Ein Verständnis, was sie sind und wie Sie mit ihnen arbeiten, ist von größter Bedeutung.
Weitere Informationen:

- [Common Data Service-Entitäten](entities.md)
- [Über die Entitätsreferenz](reference/about-entity-reference.md)

## <a name="work-with-metadata"></a>Arbeiten mit Metadaten

Ein gutes Verständnis der Metadaten im System hilft dabei zu verstehen, wie die Common Data Service-Plattform funktioniert. Im Allgemeinen können Sie die Designers hinzufügen, aktualisieren oder löschen, die Metadaten definiert, aber sowohl Web API und Organisationsservicewebdienste bieten Funktionen, um CRUD-Vorgänge auf dem Entitätsschema auszuführen. Weitere Informationen: [Arbeiten mit Metadaten mithilfe von Code](metadata-services.md). 

## <a name="use-solutions-to-package-and-distribute-extensions"></a>Packen und Verteilen von Erweiterungen mithilfe von Lösungen

Wenn Sie die Aktivität zu den Erweiterungen verteilen, die Sier erstellen oder Anpassungen, die davon abhängen, müssen Sie die Lösungen verstehen. Die Lösungen, die von einer Person erstellt wurden, sind verhältnismäßig einfach, und erfodern keine Fähigkeiten eines Entwicklers. Aber ein Team von Entwicklern, mit Lösungen und Verwendungs-Anwendungin der Lebenszyklus-Verwaltungsprinzipien produktiv zum Verwenden eines entwickelteren Methode. Weitere Informationen:

 - [Einführung in Lösungen](introduction-solutions.md)
 - [SolutionPackager-Tool](compress-extract-solution-file-solutionpackager.md)
 - [Package Deployer-Tool](./package-deployer/create-packages-package-deployer.md)
 - [App auf AppSource veröffentlichen](publish-app-appsource.md)

## <a name="create-client-applications-and-authentication"></a>Erstellen von Clientanwendungen und Authentifizierung

Wenn Sie Erweiterungen erstellen, um die Geschäftslogik auf dem Server anzuwenden, müssen Sie keinen Code zur authentifizieren integrieren. Die Authentifizierung ist nur erforderlich, wenn Sie [Eine Clientanwendung erstellen](/powerapps/developer/common-data-service/connect-cds). Eine einfache Konsolen-Client-Anwendung ist eine gute Methode, sich mit den Common Data Service-APIs vertraut zu machen. Das Aktivieren von Möglichkeiten, um sich mit Daten zu verbinden, ist ein wichtiger erster Schritt. Die meisten Codebeispiele, die gespeichert werden, enthalten Wege zur Authentifizierung. Der Xrm.Toolings-Konnektor stellt Funktionen bereit, die Authentifizierung zu vereinfachen. Weitere Informationen:

- [Authentifizierung](authentication.md)
- [Erstellen von Webanwendungen mit Server-to-Server-Authentifizierung (S2S)](/powerapps/developer/common-data-service/build-web-applications-server-server-s2s-authentication)
- [Erstellen von Windows-Client-Anwendungen mithilfe von XRM-Tools](/powerapps/developer/common-data-service/xrm-tooling/build-windows-client-applications-xrm-tools)

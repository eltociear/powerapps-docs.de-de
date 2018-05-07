---
title: Was ist Common Data Service für Apps? | Microsoft-Dokumentation
description: Einführung in Common Data Service (CDS) für Apps, Entitäten und serverseitige Logik
documentationcenter: na
author: SKjerland
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: overview
ms.component: cds
ms.date: 05/01/2018
ms.author: sharik
ms.openlocfilehash: 0f829548f8d2066d36fc722fa616aa388ccb1a69
ms.sourcegitcommit: 45fac73f04aa03b5796ae6833d777f4757e67945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="what-is-common-data-service-for-apps"></a>Was ist Common Data Service für Apps?
Mit CDS für Apps können Sie Daten sicher speichern und verwalten, die von Geschäftsanwendung verwendet werden. Die Daten in CDS für Apps werden in mehreren Standardentitäten gespeichert. Eine *Entität* ist eine Gruppe von Datensätzen, die ähnlich wie eine Tabelle in einer Datenbank zum Speichern von Daten verwendet wird. CDS für Apps beinhaltet einen grundlegenden Satz an Standardentitäten, die gängige Szenarios abdecken. Sie können aber auch benutzerdefinierte Entitäten erstellen, die auf Ihre Organisation zugeschnitten sind, und diese mithilfe von Power Query mit Daten auffüllen. App-Entwickler können dann mit PowerApps umfangreiche Anwendungen mit diesen Daten erstellen.

Informationen zum Erwerb eines Plans für die Verwendung von CDS für Apps finden Sie unter [Pricing Info (Preise)](../../administrator/pricing-billing-skus.md).

## <a name="why-use-common-data-service-for-apps"></a>Gründe für die Verwendung von Common Data Service für Apps
Entitäten (Standard und benutzerdefiniert) in CDS für Apps sind eine sichere und cloudbasierte Speicheroption für Ihre Daten. Mit Entitäten können Sie eine auf Ihr Unternehmen zugeschnittene Definition Ihrer Daten für die Verwendung in Ihren Apps erstellen. Wenn Sie nicht sicher sind, ob Entitäten die beste Option sind, sollten Sie diese Vorteile bedenken:

* **Einfache Verwaltung:** Sowohl die Metadaten als auch die Daten werden in der Cloud gespeichert. Sie müssen sich nicht um die Details kümmern, wie diese gespeichert werden.
* **Einfache Freigabe:** Sie können Daten problemlos für Ihre Kollegen freigeben, und PowerApps verwaltet die Berechtigungen für Sie.
* **Einfaches Sichern:** Daten werden sicher gespeichert, damit Benutzer sie nur dann sehen können, wenn Sie ihnen Zugriff gewähren. Durch die rollenbasierte Sicherheit können Sie den Zugriff auf Entitäten für verschiedene Benutzer innerhalb Ihrer Organisation steuern.
* **Umfassende Metadaten:** Datentypen und Beziehungen werden direkt in PowerApps genutzt. Wenn Sie z.B. den Feldtyp als URL definieren, werden die Daten innerhalb Ihrer App als Hyperlink angezeigt.
* **Logik und Validierung:** Definieren Sie berechnete Felder, Geschäftsregeln, Workflows und Workflows für Geschäftsprozesse, um die Datenqualität sicherzustellen und Geschäftsprozesse zu optimieren.
* **Produktivitätstools:** Entitäten sind in den Add-Ins für Microsoft Excel verfügbar, um die Produktivität zu steigern und die Datenverfügbarkeit sicherzustellen.

## <a name="interacting-with-entities"></a>Interagieren mit Entitäten
Wenn Sie eine App entwickeln, können Sie Standardentitäten, benutzerdefinierte Entitäten oder beides verwenden. CDS für Apps stellt standardmäßig Standardentitäten bereit. Diese sind in Übereinstimmung mit bewährten Methoden entwickelt und dienen zum Erfassen der am häufigsten verwendeten Konzepte für Szenarios in einem Unternehmen.

![Screenshot mit einer Liste von Entitäten](./media/data-platform-cds-intro/entitylist.png "Entitätsliste")

Eine vollständige Liste der Entitäten finden Sie in der [Referenz zu Entitäten](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/reference/about-entity-reference).

Sie können die Funktionalität der Standardentitäten erweitern, indem Sie eine oder mehrere benutzerdefinierte Entitäten zum Speichern von Informationen erstellen, die für Ihr Unternehmen einzigartig sind. Weitere Informationen finden Sie unter [Create a custom entity in the Common Data Model (Erstellen einer benutzerdefinierten Entität im Common Data Model)](create-custom-entity.md).

## <a name="logic-and-validation"></a>Logik und Überprüfung
In CDS für Apps können die Entitäten eine umfangreichere serverseitige Logik und Überprüfung nutzen, um die Datenqualität zu gewährleisten und sich wiederholenden Code in jeder App reduzieren, die Daten in der Entität erstellt und verwendet.

* Durch **Geschäftsregeln** können Daten in mehreren Feldern und Entitäten überprüft werden. Außerdem können unabhängig von der App, die zum Erstellen der Daten verwendet wurde, Warnungen und Fehlermeldungen angezeigt werden. Weitere Informationen finden Sie unter [Create a business rule (Erstellen einer Geschäftsregel)](./data-platform-create-business-rule.md).
* Die **Flows für Geschäftsprozesse** unterstützen die Benutzer dabei, sicherzustellen, dass sie Daten konsistent eingeben und dabei jedes Mal die gleichen Schritte befolgt haben. Die Flows für Geschäftsprozesse werden derzeit nur für modellgesteuerte Apps unterstützt. Weitere Informationen finden Sie unter [Business process flows overview (Übersicht über Flows für Geschäftsprozesse)](/dynamics365/customer-engagement/customize/business-process-flows-overview).
* **Workflows** ermöglichen Ihnen das Automatisieren von Geschäftsprozessen ohne Aktionen durch Benutzer. Weitere Informationen finden Sie unter [Workflows overview (Übersicht über Workflows)](/dynamics365/customer-engagement/customize/workflow-processes).
* Durch **Geschäftslogiken mit Code** werden erweiterte Entwicklerszenarios unterstützt, um die Anwendung direkt über den Code zu erweitern. Weitere Informationen finden Sie unter [Anwenden von Geschäftslogik mit Code](../../developer/common-data-service/apply-business-logic-with-code.md).

## <a name="developer-capabilities"></a>Funktionen für Entwickler
Zusätzlich zu den Features, die über das [PowerApps-Portal](https://web.powerapps.com) zur Verfügung gestellt werden, enthält CDS für Apps ebenfalls Features für Entwickler, mit denen programmgesteuert auf Metadaten und Daten zugegriffen werden kann, um Entitäten und Geschäftslogiken zu erstellen. Außerdem wird die Interaktion mit den Daten ermöglicht. Weitere Informationen finden Sie unter [Übersicht für Entwickler: Common Data Service für Apps](../../developer/common-data-service/overview.md).

## <a name="next-steps"></a>Nächste Schritte
Einstieg in CDS für Apps:
* [Erstellen Sie eine App mithilfe einer Common Data Service-Datenbank.](../canvas-apps/data-platform-create-app-scratch.md)
* [Erstellen Sie eine benutzerdefinierte Entität](create-custom-entity.md), und [erstellen Sie eine App, die diese Entität verwendet](../canvas-apps/data-platform-create-app.md).
* [Verwenden Sie Power Query](./data-platform-cds-newentity-pq.md), um eine Verbindung mit einer Onlinedatenquelle oder einer lokalen Datenquelle herzustellen, und importieren Sie diese direkt in CDS für Apps.

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfasst und speichert Microsoft benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen. Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller erstellen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

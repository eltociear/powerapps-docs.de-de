---
title: Was ist Common Data Service für Apps? | Microsoft-Dokumentation
description: Einführung in Common Data Service für Apps, Entitäten und serverseitige Logik
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: cc7eb07b45db1271607ffb65d37258ec6f88f38b
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="what-is-common-data-service-for-apps"></a>Was ist Common Data Service für Apps?

Durch Common Data Service (CDS) für Apps können Sie Daten, die in von Ihnen entwickelten Apps oder in Apps von Microsoft und anderen App-Anbietern verwendet werden, sicher speichern und verwalten. Die Daten in CDS für Apps werden in mehreren Standardentitäten und benutzerdefinierten Entitäten gespeichert. Eine Entität ist eine Gruppe von Feldern, die zum Speichern von Daten ähnlich wie eine Tabelle in einer Datenbank verwendet werden. Nachdem die Daten gespeichert sind, können Sie mit Microsoft PowerApps anspruchsvolle Anwendungen mithilfe Ihrer Daten erstellen:

* Nutzen Sie vorhandene Standardentitäten, oder erstellen Sie benutzerdefinierte Entitäten, um Ihr Szenario und Ihre Anwendung zu unterstützen.
* Erstellen Sie PowerApps und Flows direkt für CDS für Apps.
* Fügen Sie benutzerdefinierte Felder und Beziehungen zu Standardentitäten hinzu, für die zusätzliche Informationen benötigt werden.
* Erstellen Sie berechnete Felder und Rollupfelder für Ihre Entitäten, um konsistente Berechnungen für Apps und Analysen bereitzustellen.
* Definieren Sie Geschäftsregeln, um die Datenqualität innerhalb von Entitäten unabhängig davon sicherzustellen, welche App auf Ihre Daten zugreift oder diese bearbeitet.
* Erstellen Sie Workflows, und nutzen Sie die Integration in Microsoft Flow, um zusätzliche Aktionen oder Geschäftsprozesse für Ihre Daten durchzuführen.
* Integrieren Sie Standardentitäten und benutzerdefinierte Entitäten in eine App, die Sie entwickeln, so einfach wie Daten aus anderen Quellen.
* Verbinden Sie Ihre Daten von Microsoft Excel mithilfe der Produktivitäts-Add-Ins von CDS für Apps.
* Importieren und Synchronisieren Sie Ihre Daten im Handumdrehen mithilfe von Power Query.
* Sichern Sie Ihre Daten innerhalb Ihrer Organisation mithilfe der rollenbasierten Sicherheit für Standardentitäten und benutzerdefinierte Entitäten.
* Bieten Sie globale Unterstützung für Ihre Daten und Anwendungen an, indem Sie die Übersetzung der Entitäts- und Feldnamen in die Benutzersprache nutzen.

Jede Entität enthält eine Gruppe von Datensätzen, die Benutzer abhängig von ihren Berechtigungen erstellen, lesen, aktualisieren und löschen können. Sie können Beziehungen zwischen Entitäten erstellen, damit Sie in einer Entität anhand eines Datensatz einer anderen Entität nach Informationen suchen können. Sie können beispielsweise eine benutzerdefinierte Entität erstellen, um nachzuverfolgen, an welchen Veranstaltungen ein Benutzer teilgenommen hat. Indem Sie den Kunden als Nachschlagefeld zu Ihrer benutzerdefinierten Entität hinzufügen, bilden Sie eine Beziehung zwischen den zwei Entitäten, was in Ihrer App und in der Berichterstellung genutzt werden kann.

Informationen zum Erwerb eines Plans für die Verwendung von CDS für Apps finden Sie unter [Pricing Info (Preise)](../../administrator/pricing-billing-skus.md).

## <a name="why-use-common-data-service-for-apps"></a>Gründe für die Verwendung von Common Data Service für Apps
Entitäten (Standard und benutzerdefiniert) in CDS für Apps bieten eine sichere und cloudbasierte Speicheroption für Ihre Daten. Mit Entitäten können Sie eine auf Ihr Unternehmen fokussierte Definition Ihrer Daten für die Verwendung in Ihren Apps erstellen. Wenn Sie nicht sicher sind, ob Entitäten die beste Option sind, sollten Sie diese Vorteile bedenken:

* **Einfach zu verwalten**: Sowohl die Metadaten als auch die Daten werden in der Cloud gespeichert. Sie müssen sich nicht um die Details kümmern, wie diese gespeichert werden.
* **Einfache Freigabe**: Sie können Daten problemlos für Ihre Kollegen freigeben, da die Berechtigungen von PowerApps verwaltet werden.
* **Bequem zu sichern**: Daten werden sicher gespeichert, damit Benutzer sie nur dann sehen können, wenn Sie ihnen Zugriff gewähren. Durch die rollenbasierte Sicherheit können Sie den Zugriff auf Entitäten für verschiedene Benutzer innerhalb Ihrer Organisation steuern.
* **Umfassende Metadaten**: Datentypen und Beziehungen werden direkt in PowerApps genutzt. Wenn Sie z.B. den Feldtyp als URL definieren, werden die Daten innerhalb Ihrer App als Hyperlink angezeigt.
* **Logik und Validierung:** Definieren Sie berechnete Felder, Geschäftsregeln, Workflows und Workflows für Geschäftsprozesse, um die Datenqualität sicherzustellen und Geschäftsprozesse zu optimieren.
* **Produktivitätstools:** Entitäten sind in den Add-Ins für Microsoft Excel verfügbar, um die Produktivität zu steigern und die Verfügbarkeit Ihrer Daten sicherzustellen.

Wenn Sie eine App entwickeln, können Sie Standardentitäten, benutzerdefinierte Entitäten oder beides verwenden. Wenn eine Standardentität einem bestimmten Zweck in Ihrer App dienen kann, sollten Sie sie verwenden, anstatt eine benutzerdefinierte Entität zu entwickeln, die die gleiche Aufgabe erfüllt. Wenn eine Standardentität mit einigen Änderungen passend wäre, können Sie Felder entsprechend Ihren Anforderungen hinzufügen.

* CDS für Apps stellt standardmäßig Standardentitäten bereit. Diese sind in Übereinstimmung mit bewährten Methoden entwickelt und dienen zum Erfassen der am häufigsten verwendeten Konzepte für ein Unternehmen, z.B. Kontakte, Konten und Produkte. Eine vollständige Liste der Entitäten finden Sie unter [Standard entities (Standardentitäten)](data-platform-intro.md#standard-entities).
* Sie können die Funktionalität der Standardentitäten erweitern, indem Sie eine oder mehrere benutzerdefinierte Entitäten zum Speichern von Informationen erstellen, die für Ihr Unternehmen einzigartig sind. Weitere Informationen finden Sie unter [Create a custom entity in the Common Data Model (Erstellen einer benutzerdefinierten Entität im Common Data Model)](create-custom-entity.md).

> [!NOTE]
> Verwenden Sie, wenn möglich, Standardentitäten (mit benutzerdefinierten Feldern, die bei Bedarf hinzugefügt werden). Dadurch wird sichergestellt, dass Sie von neuen Features oder Apps profitieren können, die diese Entitäten in der Zukunft zu nutzen.

## <a name="interacting-with-entities"></a>Interagieren mit Entitäten

Wenn Sie eine Standardentität verwenden oder eine benutzerdefinierte Entität erstellen, sind in jeder davon mehrere Elemente verfügbar, mit denen verschiedene Aktionen durchgeführt werden können. Je nachdem, ob Ihr Geschäftsszenario einfach oder erweitert ist, wird bestimmt, welche Features Sie verwenden sollten. Melden Sie sich bei [PowerApps](https://web.powerapps.com) an, und klicken Sie im linken Menü auf Daten > Entitäten, um die verfügbaren Entitäten in Ihrer Umgebung anzuzeigen.

![Entitätsdetails](./media/data-platform-cds-intro/entitylist.png "Entity Details")

* In jedem **Feld** können Sie eine zu sammelnde Information definieren sowie den Datentyp oder das Format, in dem diese angezeigt werden sollen. Felder weisen Ähnlichkeiten zu Spalten in Datenbanken oder in Excel auf.
* Durch alternative **Schlüssel** werden effiziente und präzise Suchen und die Interaktion mit Datensätzen in der Entität ermöglicht, wenn nicht der eindeutige Standardbezeichner verwendet wird. Dies ist dann wichtig, wenn Sie einen Geschäftsschlüssel verwenden oder eine Integration mit einem externen System vornehmen.
* Jede Entität kann mehrere **Beziehungen** zu anderen Entitäten aufweisen, um entitätsübergreifende Suchvorgänge und Abfragen durchzuführen. Es gibt m:1-, 1:m- und m:n-Beziehungen.
* Durch **Ansichten** kann jede Entität auf verschiedene Weisen dargestellt werden. Dazu zählt neben dem Filtern und Sortieren der Daten auch, welche Felder angezeigt werden. Diese Darstellungen werden als Ansichten gespeichert und können von verschiedenen Apps verwendet werden. Wenn Sie beispielsweise nur aktive Konten in Ihrer App anzeigen lassen möchten, können Sie eine Ansicht mit einem Filter verwenden. Dadurch werden nur aktive Konten angezeigt, und es wird vermieden, dass der Filter für jede App wiederholt eingestellt werden muss.
* **Geschäftsregeln** können verwendet werden, um die Daten zu überprüfen, die in Entitäten erstellt und aktualisiert werden und somit die Datenqualität zu gewährleisten. Jede Geschäftsregel kann Daten für mehrere Felder und Entitäten überprüfen und unabhängig von der App, die zum Erstellen der Daten verwendet wird, Warnungen und Fehlermeldungen anzeigen.
* Die in CDS für Apps gespeicherten **Daten** sind im PowerApps-Portal, in PowerApps und Microsoft Excel sowie in den Web-APIs für Entwickler verfügbar.

### <a name="system-fields"></a>Systemfelder
Alle Standardentitäten oder benutzerdefinierten Entitäten werden mit einem Satz von schreibgeschützten Feldern erstellt, die Sie nicht ändern, löschen oder auf einen Wert festlegen können. Dies sind die wichtigsten Systemfelder:

## <a name="logic-and-validation"></a>Logik und Überprüfung

In CDS für Apps können die Entitäten eine umfangreichere serverseitige Logik und Überprüfung nutzen, um die Datenqualität zu gewährleisten und sich wiederholenden Code in jeder App reduzieren, die Daten in der Entität erstellt und verwendet.

* Durch **Geschäftsregeln** können Daten in mehreren Feldern und Entitäten überprüft werden, außerdem können unabhängig von der App, die zum Erstellen der Daten verwendet wurde, Warnungen und Fehlermeldungen angezeigt werden. Weitere Informationen finden Sie unter [Create a business rule (Erstellen einer Geschäftsregel)](./data-platform-create-business-rule.md).
* Die **Flows für Geschäftsprozesse** unterstützen die Benutzer dabei, sicherzustellen, dass die Daten konsistent eingegeben und dabei jedes Mal die gleichen Schritte befolgt werden. Die Flows für Geschäftsprozesse werden derzeit nur für modellgesteuerte Apps unterstützt. Weitere Informationen finden Sie unter [Business process flows overview (Übersicht über Flows für Geschäftsprozesse)](/dynamics365/customer-engagement/customize/business-process-flows-overview).
* **Workflows** ermöglichen Ihnen das Automatisieren von Geschäftsprozessen ohne Interaktionen durch Benutzer. Weitere Informationen finden Sie unter [Workflows overview (Übersicht über Workflows)](/dynamics365/customer-engagement/customize/workflow-processes).
* Durch **Geschäftslogiken mit Code** werden erweiterte Entwicklerszenarios unterstützt, um die Anwendung direkt über den Code zu erweitern. Weitere Informationen finden Sie unter [Anwenden von Geschäftslogik mit Code](../../developer/common-data-service/apply-business-logic-with-code.md).

## <a name="getting-data-into-common-data-service-for-apps"></a>Einfügen von Daten in Common Data Service für Apps

Es gibt verschiedene Möglichkeiten, um Daten in CDS für Apps einzufügen.

* Erstellen Sie eine PowerApp oder einen Flow, um mit dem Erstellen von Daten zu beginnen.
* Verwenden Sie Power Query, um eine Verbindung mit einer Onlinedatenquelle oder einer lokalen Datenquelle herzustellen, und importieren Sie diese direkt in CDS für Apps. Power Query ermöglicht Ihnen während des Importierens ebenfalls das Erstellen von Entitäten, die auf dem Schema Ihrer Quelle basieren, sowie das Durchführen von Transformationen an Ihren Daten. Weitere Informationen finden Sie unter [Add data to an entity in the Common Data Service for Apps by using Power Query (Hinzufügen von Daten zu einer Entität in Common Data Service für Apps mithilfe von Power Query)](./data-platform-cds-newentity-pq.md).

## <a name="developer-capabilities"></a>Funktionen für Entwickler

Zusätzlich zu den Features, die über das [PowerApps-Portal](https://web.powerapps.com) zur Verfügung gestellt werden, enthält CDS für Apps ebenfalls Features für Entwickler, mit denen programmgesteuert auf Metadaten und Daten zugegriffen werden kann, um Entitäten und Geschäftslogiken zu erstellen. Außerdem wird die Interaktion mit den Daten ermöglicht. Weitere Informationen finden Sie unter [Übersicht für Entwickler: Common Data Service für Apps](../../developer/common-data-service/overview.md).

## <a name="get-started"></a>Erste Schritte
Probieren Sie es aus, indem Sie eine App mithilfe einer Standardentität erstellen, oder [erstellen Sie eine benutzerdefinierte Entität](create-custom-entity.md). Erstellen Sie anschließend [eine App, die diese Entität verwendet](../canvas-apps/data-platform-create-app.md).

## <a name="privacy-notice"></a>Hinweis zum Datenschutz
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfassen und speichern wir benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen.  Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller schaffen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und in Lücken in der Abdeckung der Standardentität des Diensts ermittelt werden, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

---
title: Was ist Common Data Service für Apps? | Microsoft-Dokumentation
description: Einführung in Common Data Service (CDS) für Apps, Entitäten und serverseitige Logik
author: clwesene
manager: kfile
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 05/01/2018
ms.author: matp
ms.openlocfilehash: 586750edf476a9145e2822522cc0b4b5ad729539
ms.sourcegitcommit: 7296649d03ebc33dc5ddb9e7c551869dc781f154
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250821"
---
# <a name="what-is-common-data-service-for-apps"></a>Was ist Common Data Service für Apps?
Mit CDS für Apps können Sie Daten sicher speichern und verwalten, die von Geschäftsanwendung verwendet werden. Die Daten in CDS für Apps werden in mehreren Standardentitäten gespeichert. Eine *Entität* ist eine Gruppe von Datensätzen, die ähnlich wie eine Tabelle in einer Datenbank zum Speichern von Daten verwendet wird. CDS für Apps bieten einen grundlegenden Satz von Standardentitäten, die gängige Szenarien abdecken. Sie können aber auch benutzerdefinierte Entitäten erstellen, die auf Ihre Organisation zugeschnitten sind, und diese mithilfe von Power Query mit Daten auffüllen. App-Entwickler können dann mit PowerApps umfangreiche Anwendungen mit diesen Daten erstellen.

![Screenshot: Übersicht über die Plattform für Geschäftsanwendungen](./media/data-platform-cds-intro/platform.png "Plattformübersicht")

Informationen zum Erwerb eines Plans für die Verwendung von CDS für Apps finden Sie unter [Pricing Info (Preise)](../../administrator/pricing-billing-skus.md).

## <a name="why-use-common-data-service-for-apps"></a>Gründe für die Verwendung von Common Data Service für Apps
Entitäten (Standard und benutzerdefiniert) in CDS für Apps sind eine sichere und cloudbasierte Speicheroption für Ihre Daten. Mit Entitäten können Sie eine auf Ihr Unternehmen zugeschnittene Definition Ihrer Daten für die Verwendung in Ihren Apps erstellen. Wenn Sie nicht sicher sind, ob Entitäten die beste Option sind, sollten Sie diese Vorteile bedenken:

* **Einfache Verwaltung:** Sowohl die Metadaten als auch die Daten werden in der Cloud gespeichert. Sie müssen sich nicht um die Details kümmern, wie diese gespeichert werden.
* **Einfaches Sichern:** Daten werden sicher gespeichert, damit Benutzer sie nur dann sehen können, wenn Sie ihnen Zugriff gewähren. Durch die rollenbasierte Sicherheit können Sie den Zugriff auf Entitäten für verschiedene Benutzer innerhalb Ihrer Organisation steuern.
* **Zugriff auf Dynamics 365-Daten:** Daten aus Dynamics 365-Anwendungen werden auch in Common Data Service für Apps gespeichert, sodass Sie Apps, die Ihre Dynamics 365-Daten nutzen, schnell erstellen und Ihre Apps mit PowerApps erweitern können.
* **Umfassende Metadaten:** Datentypen und Beziehungen werden direkt in PowerApps genutzt.
* **Logik und Validierung:** Definieren Sie berechnete Felder, Geschäftsregeln, Workflows und Workflows für Geschäftsprozesse, um die Datenqualität sicherzustellen und Geschäftsprozesse zu optimieren.
* **Produktivitätstools:** Entitäten sind in den Add-Ins für Microsoft Excel verfügbar, um die Produktivität zu steigern und die Datenverfügbarkeit sicherzustellen.

## <a name="dynamics-365-and-the-common-data-service-for-apps"></a>Dynamics 365 und Common Data Service für Apps

Dynamics 365-Anwendungen, wie Dynamics 365 for Sales, Service oder Talent, verwenden ebenfalls Common Data Service für Apps, um Daten, die von der Anwendungen verwendet werden, zu speichern und zu sichern. Dadurch können Sie Apps mit PowerApps und Common Data Service für Apps direkt mit Ihren wichtigsten Unternehmensdaten erstellen, die bereits in Dynamics 365 verwendet werden, ohne diese integrieren zu müssen.

* **Erstellen von Apps mit Ihren Dynamics 365-Daten:** Erstellen Sie im Handumdrehen Apps mit Ihren Unternehmensdaten in PowerApps oder mit dem Pro Developer SDK.
* **Verwalten wiederverwendbarer Unternehmenslogik und -regeln:** Unternehmensregeln und -logik, die bereits in Ihren Dynamics 365-Entitäten definiert wurden, werden auf Ihre PowerApps-Apps angewendet, um Datenkonsistenz sicherzustellen, unabhängig davon, wie oder über welche App die Benutzer auf die Daten zugreifen.
* **Wiederverwenden von Kenntnissen zu Dynamics 365 und PowerApps:** Benutzer, die bereits mit PowerApps oder Dynamics 365 vertraut sind, können Ihre Kenntnisse und Fähigkeiten auch auf der neuen Plattform Common Data Service für Apps einsetzen. Der Prozess zum Erstellen von Entitäten, Formen und Diagrammen usw. ist jetzt in allen Anwendungen der gleiche.

    > [!NOTE]
    > Dynamics 365 for Finance and Operations erfordert aktuell die Konfiguration des Datenintegrators, um Ihre Finanz- und Betriebsdaten in Common Data Service für Apps verfügbar zu machen.

## <a name="integrating-data-into-the-common-data-service"></a>Integrieren von Daten in Common Data Service

Wenn Sie eine App erstellen, nutzen Sie dafür normalerweise Daten aus mehreren Quellen. Oft kann dies auf der Anwendungsebene erfolgen. Es gibt jedoch auch Fälle, in denen die Integration dieser Daten in einen gemeinsamen Speicher das Erstellen einer App erleichtern kann, sodass nur ein Logiksatz zum Verwalten und Betreiben der Daten erforderlich ist. Mit Common Data Service für Apps können Daten aus mehreren Quellen in einen einzigen Speicher integriert werden, der dann wiederum von PowerApps, Flow und Power BI gemeinsam mit bereits aus Dynamics 365-Anwendungen bereitgestellten Daten verwendet werden kann.

* **Zeitlich geplante Integration in andere Systeme:** Daten, die in einer anderen Anwendung gespeichert sind, können in regelmäßigen Abständen mit Common Data Service für Apps synchronisiert werden, damit Daten anderer Anwendungen in PowerApps genutzt werden können.
* **Transformieren und Importieren von Daten mit PowerQuery:** Sie können Daten beim Import in Common Data Service mit PowerQuery aus vielen Onlinedatenquellen transformieren. PowerQuery ist ein Tool, das sowohl Excel als auch Power BI verwenden.
* **Einmaliger Import von Daten:** Der einfache Import und Export von Excel- und CSV-Dateien kann für einen einmaligen oder unregelmäßigen Datenimport in Common Data Service für Apps verwendet werden.


## <a name="interacting-with-entities"></a>Interagieren mit Entitäten
Wenn Sie eine App entwickeln, können Sie Standardentitäten, benutzerdefinierte Entitäten oder beides verwenden. CDS für Apps stellt standardmäßig Standardentitäten bereit. Diese sind in Übereinstimmung mit bewährten Methoden entwickelt und dienen zum Erfassen der am häufigsten verwendeten Konzepte für Szenarios in einem Unternehmen.

![Screenshot mit einer Liste von Entitäten](./media/data-platform-cds-intro/entitylist.png "Entitätsliste")

Eine vollständige Liste der Entitäten finden Sie in der [Referenz zu Entitäten](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference).

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
Mit dem allgemeinen Datenmodell in Microsoft PowerApps erfasst und speichert Microsoft benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen. Wir verwenden dieses Wissen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die Ersteller erstellen, helfen uns dabei, Szenarios zu verstehen, die in der Microsoft PowerApps-Community häufig vorkommen und Lücken in der Abdeckung der Standardentität des Diensts offenlegen, z.B. Schemas im Zusammenhang mit Organisationen. Microsoft nutzt die Daten in den Datenbanktabellen nicht, die mit diesen Entitäten verbunden sind, und greift auch nicht auf diese zu. Sie werden auch nicht außerhalb der Region repliziert, in der die Datenbank bereitgestellt wird. Beachten Sie jedoch, dass die benutzerdefinierten Entitäts- und Feldnamen möglicherweise über Regionen hinweg repliziert werden können und unter Einhaltung unserer Richtlinien für die Datenaufbewahrung gelöscht werden. Microsoft ist bestrebt, zu Ihrer Privatsphäre beizutragen, so wie ausführlich in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

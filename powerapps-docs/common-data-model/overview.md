---
title: 'Übersicht: Common Data Model | Microsoft-Dokumentation'
description: Erfahren Sie, wie Common Data Model eine Verbindung zwischen Common Data Service für Apps und Common Data Service für Analysen herstellt.
author: RobertBruckner
ms.service: powerapps
ms.topic: article
ms.date: 03/14/2018
ms.author: jdaly
ms.openlocfilehash: 4e9b929558de0b2451bb2df4add4b300d7115848
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34803238"
---
# <a name="common-data-model-overview"></a>Übersicht: Common Data Model

**Common Data Model** (CDM) ist eine Open-Source-Definition von Standardentitäten, die häufig verwendete Konzepte und Aktivitäten für eine Vielzahl von Geschäfts- und Anwendungsdomänen darstellen. Common Data Model bietet *klar definierte, modulare und erweiterbare* Geschäftsentitäten wie z.B. Konto, Geschäftseinheit, Fall, Kontakt, Lead, Verkaufschance und Produkt sowie Interaktionen und Beziehungen zwischen Lieferanten, Arbeitern und Kunden, wie z.B. Aktivitäten und Vereinbarungen zum Servicelevel. 

[Common Data Service für Apps](../maker/common-data-service/data-platform-intro.md) und Common Data Service für Analysen <!-- TODO add link when available  --> von Microsoft implementieren Common Data Model. Diese Dienste enthalten Daten, die der Definition von Common Data Model entsprechen. Da auf diesen Diensten aufgebaut wird, können gepackte Anwendungen und analytische Lösungen mit klar definierten Formen von Entitäten arbeiten und Daten freigeben, egal woher diese Daten ursprünglich stammen oder wo sie gemastert wurden. Benutzerdefinierte branchenspezifische Apps und analytische Lösungen können dieselben Entitäten zum Freigeben von Daten verwenden und dadurch Ihren spezifischen und geschäftlichen Anforderungen entsprechen. 

Microsoft arbeitet mitsamt seiner Partner daran, Apps auf Grundlage von Common Data Service zu erstellen und Ihre Geschäftsdaten im CDM-Format zu speichern. Es gibt eine *große, wachsende Auflistung von Lösungen, die effizient zusammenarbeiten, wenn Daten im CDM-Format gespeichert werden*. Das bedeutet, dass Sie neue Geschäftsprozesse einfach und schnell implementieren und Einblicke in Ihre Geschäftsvorgänge erhalten können, ohne dass Unstimmigkeiten entstehen. Im folgenden Diagramm wird veranschaulicht, wie Anwendungen auf Basis von Common Data Service Entitäten von Common Data Model nutzen.

![Anwendungen auf Basis von Common Data Service nutzen Entitäten von Common Data Model](media/cdm-overview.png)

Common Data Model vereinfacht die Herausforderungen der Datenverwaltung, durch Vereinheitlichung von Daten in einer bekannten Form mit *struktureller und semantischer Konsistenz zwischen Anwendungen und Bereitstellungen*. Common Data Model hilft beim Integrieren und *Verdeutlichen von Daten*, die aus Geschäftsprozessen, digitalen Interaktionen, Produkttelemetrie, Interaktionen von Personen usw. gesammelt wurden. 

Daten, die in Common Data Service für Apps gespeichert sind, können mithilfe von Common Data Service für Analysen für Kunden, die beide Dienste verwenden, *einfach und automatisch integriert werden*. Sie können mit Enterprise- und Transaktionsdaten, die Sie bereits besitzen (z.B. Leads, Kampagneninformationen, vorherige Bestellungen von Kunden) beginnen und diese mit Daten aus anderen Quellen (z.B. Weblogs oder Produkttelemetrie) kombinieren, um einen einheitlichen Überblick zu erhalten.

Außerdem ist Common Data Model *erweiterbar*: Sie können jeder anpassbaren Entität Felder hinzufügen, die mit CDM bereitgestellt werden, oder Sie erstellen Ihre eigenen benutzerdefinierten Entitäten. Standardmäßig definiert CDM eine einheitliche Sprache für geschäftliche Entitäten über das gesamte Spektrum von Geschäftsprozessen hinweg, über Vertrieb, Services, Marketing, Vorgänge, Finanzen, Mitarbeiter und Handel sowie für die Kunden-, Personen- und Produktentitäten, die im Mittelpunkt der Geschäftsprozesse eines Unternehmens stehen. Common Data Model ermöglicht die Interoperabilität von Daten, die mehrere Kanäle, Dienstimplementierungen und Lieferanten umfasst.

Mithilfe der folgenden Features bieten Common Data Model und Common Data Service eine umfangreiche und produktive Entwicklungsplattform:

- **Definition von Standardentitäten**: Common Data Model stellt eine Definition von Entitäten bereit, die die am häufigsten in Geschäfts- und Produktivitätsanwendungen verwendeten Entitäten darstellen. Das öffentliche CDM-GitHub-Repository [(https://github.com/Microsoft/CDM)](https://github.com/Microsoft/CDM) wird fortlaufend mit Kernentitäten verbessert, die den gesamten Umfang von Geschäftsprozessen, zusätzliche vertikale branchenspezifische Datenmodelle und übergreifende Quellen umfassen (z.B. Umfragen, Suchmaschinen und Produkttelemetrie).
- **Datenintegration**: Verwenden Sie Power Query als integrierte Webumgebung zum Importieren und visuellen Transformieren von Daten aus Ihren vorhandenen Systemen und zum Zusammenführen von Daten aus lokalen Quellen und Onlinequellen mit keinen oder nur wenigen Codekomponenten. Hier können Sie Ihre Kenntnisse zu der Transformation von Daten in Excel oder Power BI nahtlos anwenden. Informationen finden Sie unter [Add data to an entity in the Common Data Service by using Power Query (Hinzufügen von Daten zu einer Entität in Common Data Service mithilfe von Power Query)](../maker/common-data-service/data-platform-cds-newentity-pq.md).
    
    Wenn Sie Daten in Common Data Service importieren, können Sie diese Standardentitäten von Common Data Model zuordnen oder neue Entitäten erstellen und diesen zuordnen. Sofort verfügbare Datenintegration und Zuordnungsvorlagen vereinfachen das Herstellen einer Verbindung zu geläufigen Datenquellen wie Salesforce. Diese Zuordnungsvorlagen sind vollständig anpassbar und erweiterbar. Der folgende Screenshot zeigt das Importieren von externen Daten und das Zuordnen zu Standardentitäten in Power Query. 
    
    ![Importieren von externen Daten und Zuordnen zu Standardentitäten in Power Query ](media/cdm-mapping-entities.png)<br />

- **Erweiterbarkeit**: Sie können die Entitäten erweitern, ohne die Datenfreigabe für andere Apps zu unterbrechen.
- **Zuverlässigkeit**: Da Sie sich auf allgemeine Entitäten verlassen können, können Sie wiederverwendbare Komponenten erstellen, die an die Entitäten gebunden sind. Common Data Model unterstützt die Erweiterbarkeit und Versionsverwaltung, die Ihre Investition in die Entwicklung schützt.
- **Konsistenz der Entitäten über Bereitstellungen hinweg**: Ihre Lösungen können Information von Produktivitätsplattformen mit Daten von Geschäftsanwendungen verbinden. Sie können beispielsweise einen Kalendertermin oder eine Aufgabe in Microsoft Outlook mit einer Verkaufschance verbinden. 

[Common Data Service für Apps](../maker/common-data-service/data-platform-intro.md) implementiert Common Data Model, wodurch für die Entwicklung einer Geschäftsanwendung Folgendes ermöglicht wird:

- **Nutzen von gepackten Geschäftsanwendungen**: Dynamics 365-Anwendungen für Marketing, Vertrieb, Service, Mitarbeiter, Finanzen und Vorgänge sowie Drittanbieteranwendungen nutzen und bzw. oder basieren auf Common Data Service für Apps.
- **Anpassen von Anwendungen und Erstellen von nativen Erweiterungen für Ihre Anforderungen**: Anpassungen und Entwickler verteilen Anwendungslösungen mit einem gut definierten Anwendungslebenszyklus. Mithilfe von Lösungen können Anwendungen und Erweiterungen verteilt werden. Informationen finden Sie unter [Einführung in Lösungen](../developer/common-data-service/introduction-solutions.md).
- **Erstellen von Canvas-Apps mit PowerApps ohne bzw. mit nur wenig Code, modellgesteuert und nach dem WYSIWYG-Prinzip**: Verwenden Sie die gleichen freigegebenen Entitäten, die von gepackten Anwendungen oder Anwendungen von Drittanbietern erstellt wurden oder verwendet werden, und erstellen Sie zusätzliche eigenständige Apps. Siehe: 
    - [Build a model-driven app (Erstellen einer modellgesteuerten App)](../maker/model-driven-apps/model-driven-app-overview.md)
    - [Build a canvas app (Erstellen einer Canvas-App)](../maker/canvas-apps/getting-started.md) 
- **Automatisieren von Geschäftsprozessen mithilfe von Flow**: Verwenden von Geschäftsprozessflows zum Definieren von mehreren Stufen und Schritten, um ein gewünschtes Ergebnis zu erzielen. Informationen finden Sie unter [Create a flow that uses the Common Data Service (Erstellen eines Flows, der Common Data Service verwendet)](/flow/common-data-model-intro).
 
Die bevorstehende öffentliche Vorschauversion von **Common Data Service für Analyse**<!-- TODO add link when available  --> implementiert auch Common Data Model, wodurch die Datenanalyse von Geschäftsdaten in einem standardisierten Format unterstützt wird, einschließlich:

- **Gepackte und angepasste analytische Lösungen basierend auf Datenentitäten**: Analytische Anwendungen (z.B. Sales Insights), die den Verlauf von Vertriebsergebnissen nachverfolgen und unabhängig davon, wo die Daten ursprünglich gemastert wurden, konsistente Einblicke bieten, da die Datenintegration Daten von anderen Quellen (z.B. Salesforce) zu Entitätsformen von Common Data Model zuordnet. Damit wird Ihre analytische Lösung vereinfacht und konzentriert sich auf die Semantik der Daten von klar definierten Entitäten, wie Leads und Verkaufschancen.
- **Power Query-Datenintegration mit keinen oder nur wenigen Codekomponenten**: Verwenden der integrierten Benutzeroberfläche zum Erstellen, Füllen, Transformieren und Erweitern von Entitäten. 
- **Verwenden Ihres eigenen Azure-Speichers**: Nutzen Sie die Vorteile des Azure-Datenstapels, um Daten für Common Data Service für Analysen zur Verfügung zu stellen. Die Entitäten werden in dem Common Data Model-Format gespeichert, das von analytischen Lösungen erkannt wird.


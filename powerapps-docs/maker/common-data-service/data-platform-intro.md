---
title: Was ist Common Data Service für Apps? | Microsoft Docs
description: 'Einführung in den Common Data Service (CDS) for Apps, Entitäten und serverseitige Logik.'
author: clwesene
manager: kfile
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 05/01/2018
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="what-is-common-data-service-for-apps"></a>Was ist Common Data Service für Apps?
Mit Common Data Service (CDS) for Apps können Sie Daten sicher speichern und verwalten, die von Geschäftsanwendungen verwendet werden. Daten in der CDS for Apps werden in einem Satz von Entitäten gespeichert. Eine *Entität* ist eine Datensatzgruppe, in der Daten gespeichert werden, ähnlich zur Speicherung von Daten in einer Tabelle einer Datenbank. CDS für Apps umfasst einen Basissatz an Standardentitäten, die typischen Szenarien abdecken, jedoch können Sie auch benutzerdefinierte Entitäten erstellen, die für Ihre Organisation spezifisch sind und sie mit Power Query mit Daten auffüllen. App-Hersteller können dann PowerApps verwenden, um mithilfe dieser Daten umfangreiche Anwendungen zu erstellen.

![Screenshot, der Übersicht der Geschäftsanwendungsplattform](./media/data-platform-cds-intro/platform.png "Plattformübersicht")

Informationen zum Erwerb eines Plans zur Verwendung von CDS for Apps finden Sie unter [Preisinformationen](../../administrator/pricing-billing-skus.md).

## <a name="why-use-common-data-service-for-apps"></a>Warum Common Data Service für Apps verwenden?
Standard und benutzerdefinierte Entitäten in der CDS for Apps bieten eine sichere und cloudbasierte Speicheroption für die erfassten Daten. Mit Entitäten können Sie eine auf Ihr Geschäft ausgerichtete Definition der Daten Ihrer Organisation für die Verwendung in der Apps erstellen. Falls Sie nicht sicher sind, ob Entitäten die beste Option sind, bedenken Sie diese Vorteile:

* **Einfach zu verwalten** &ndash; Metadaten und Daten werden in der Cloud gespeichert. Sie müssen sich nicht um die Details der Speicherung sorgen.
* **Einfach zu sichern** &ndash; Die Daten werden sicher gespeichert, sodass die Benutzer sie nur sehen, wenn Sie ihnen Zugriff gewähren. Mit rollenbasierter Sicherheit können Sie den Zugriff auf Entitäten für verschiedene Benutzer in der Organisation steuern.
* **Auf Ihre Dynamics 365-Daten zugreifen** &ndash; Daten aus den Dynamics 365-Anwendungen werden auch im Common Data Service for Apps gespeichert, sodass Sie schnell Apps erstellen, die Dynamics 365-Daten nutzen und Ihre Apps mit PowerApps erweitern können.
* **Umfangreiche Metadaten** &ndash; Datentypen und Beziehungen werden direkt in PowerApps genutzt.
* **Logik und Überprüfen** &ndash; Definieren Sie berechnete Felder, Geschäftsregeln, Workflows und Geschäftsprozessflüsse, um die Datenqualität sicherzustellen und Geschäftsprozesse voranzutreiben.
* **Produktivitätstools** &ndash; Innerhalb der Add-Ins für Microsoft Excel stehen Entitäten zur Verfügung, um die Produktivität und den Zugriff auf Daten sicherzustellen.

## <a name="dynamics-365-and-the-common-data-service-for-apps"></a>Dynamics 365 und der Common Data Service für Apps-Analyse

Dynamics 365-Anwendungen, wie Dynamics 365 for Sales, Service oder Talent verwenden auch den Common Data Service for Apps, um die Daten zu speichern und zu sichern, die von Anwendungen verwendet werden. Dadurch können Sie Apps mit PowerApps und dem Common Data Service for Apps direkt mit den Kerngeschäftsdaten erstellen, die bereits in Dynamics 365 verwendet werden, ohne eine Integration verwenden zu müssen.

* **Apps mit Ihren Dynamics 365-Daten erstellen** &ndash; Apps schnell mit Ihren Geschäftsdaten in PowerApps oder mit dem Pro Developer SDK erstellen.
* **Wiederverwendbare Geschäftslogik und Regeln verwalten** &ndash; Geschäftsregeln und -logik, die bereits in Dynamics 365-Entitäten definiert werden, werden bei PowerApps angewendet, um die Datenkonsistenz sicherzustellen, unabhängig davon, wie Benutzer auf die Daten zugreifen, oder mit welcher App.
* **Wiederverwendbare Fähigkeiten in Dynamics 365 und PowerApps** &ndash; Benutzer mit Fähigkeiten, die zuvor aus PowerApps oder Dynamics 365 stammen, können diese neuen Funktionen jetzt zu der neuen Common Data Service for Apps-Plattform nutzen. Das Erstellen von Entitäten, Formularen, Diagrammen usw. ist jetzt in Ihren Anwendungen üblich.

    > [!NOTE]
    > Dynamics 365 for Finance and Operations erfordert derzeit die Konfiguration des Data Integrator, damit Ihre Daten aus Finance and Operations innerhalb des Common Data Service for Apps verfügbar gemacht werden können.

## <a name="integrating-data-into-the-common-data-service"></a>Integrieren von Daten in den Common Data Service

Das Erstellen einer App erfordert in der Regel Daten aus mehr als einer Quelle. Obwohl dies gelegentlich auf Anwendungsebene geschehen kann, gibt es auch Fälle, in denen eine gemeinsame Integration dieser Daten in einem allgemeinen Speicher eine einfache App-Erstellungserfahrung zulässt, und einen einzelnen Logiksatz, um die Daten zu warten, und damit zu arbeiten. Common Data Service for Apps gestattet die Integration der Daten aus verschiedenen Quellen in einen einzelnen Speicher, der in PowerApps, Flow und Power BI zusammen mit den Daten verwendet werden kann, die von aus Dynamics 365-Anwendungen stammen.

* **Geplante Integration mit anderen Systemen** &ndash; Daten, die in einer anderen Anwendung gespeichert werden, können regelmäßig mit dem Common Data Service for Apps synchronisiert werden, damit Sie andere Anwendungsdaten in PowerApps nutzen können.
* **Daten mit PowerQuery transformieren und importieren** &ndash; Daten beim Import in den Common Data Service zu transformieren kann über PowerQuery aus vielen Datenquellen online durchgeführt werden. Es ist ein Tool, das in Excel und Power BI genutzt wird.
* **Einmaliger Datenimport** &ndash; Einfacher Import und Export von Excel- und CSV-Dateien kann für einen einmaligen oder gelegentlichen Datenimport in den Common Data Service for Apps verwendet werden.

Weitere Informationen zur Integration von Daten in Common Data Service finden Sie unter [Daten mit Power Query in Common Data Service for Apps hinzufügen](data-platform-cds-newentity-pq.md).

## <a name="interacting-with-entities"></a>Interagieren mit Entitäten
Wenn Sie eine App entwickeln, können Sie Standardentitäten, benutzerdefinierte Entitäten oder beides erstellen. CDS for Apps bietet standardmäßig Standardentitäten. Diese wurden in Übereinstimmung mit bewährten Methoden entworfen, um die gängigsten Konzepte und Szenarien innerhalb der Organisation darzustellen.

![Screenshot einer Liste mit Entitäten](./media/data-platform-cds-intro/entitylist.png "Entitätenliste")

Eine vollständige Liste der Entitäten finden Sie unter [Entitätsreferenz](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference).

Sie können die Funktionen von Standardentitäten erweitern, indem Sie mindestens eine benutzerdefinierte Entität verwenden, um Informationen zu speichern, die in Ihrer Organisation eindeutig sind. Weitere Informationen finden Sie unter [So erstellen Sie eine benutzerdefinierte Entität](create-custom-entity.md).

## <a name="logic-and-validation"></a>Logik und Überprüfung
Entitäten in der CDS for Apps können reichhaltige serverseitige Logik und Validierung nutzen, um die Datenqualität sicherzustellen und wiederkehrenden Code in jeder App zu verringern, die Daten innerhalb einer Entität erstellt und verwendet.

* **Geschäftsregeln** validieren Daten für mehrere Felder und Entitäten und erstellen Warn- und Fehlermeldungen, unabhängig von der App, die zur Erstellung der Daten verwendet wird. Weitere Informationen finden Sie unter [Erstellen einer Geschäftsregel](./data-platform-create-business-rule.md)
* **Geschäftsprozessflüsse** führen Benutzer, um sicherzustellen, dass sie Daten einheitlich eingeben ein jedes Mal den gleichen Schritten folgen. Geschäftsprozessflüsse werden derzeit nur in modellgesteuerten Apps unterstützt. Weitere Informationen finden Sie unter [Übersicht über Geschäftsprozessflüsse](/dynamics365/customer-engagement/customize/business-process-flows-overview).
* Mit **Workflows** können Sie Geschäftsprozesse ohne Interaktion mit eine Benutzeroberfläche automatisieren. Weitere Informationen finden Sie in [Überblick zu Workflows](/dynamics365/customer-engagement/customize/workflow-processes).
* **Geschäftslogik mit Code** unterstützt erweiterte Entwicklerszenarien, , um die Anwendung direkt durch Code zu erweitern. Weitere Informationen finden Sie unter [Anwenden einer Geschäftslogik mit Code](../../developer/common-data-service/apply-business-logic-with-code.md).

## <a name="developer-capabilities"></a>Entwicklerfunktionen
Zusätzlich zu den Features, die über das [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)-Portal verfügbar sind, umfasst der CDS for Apps auch Funktionen, mit denen Entwickler programmgesteuert auf Metadaten und Daten zugreifen können, um Entitäten und Geschäftslogik zu erstellen sowie mit Daten zu interagieren. Weitere Informationen finden Sie unter [Entwicklerübersicht zu Common Data Service for Apps](../../developer/common-data-service/overview.md)

## <a name="next-steps"></a>Nächste Schritte
Erste Schritte mit der CDS for Apps:
* [Erstellen einer App mit einer Common Data Service-Datenbank](../canvas-apps/data-platform-create-app-scratch.md).
* [Erstellen einer benutzerdefinierten Entität](create-custom-entity.md) und dann [Erstellen einer App, die diese Entität verwendet](../canvas-apps/data-platform-create-app.md).
* [Verwenden von Power Query](./data-platform-cds-newentity-pq.md), um eine Verbindung mit einer Online- oder lokalen Datenquelle herzustellen und Daten direkt in CDS for Apps zu importieren.

## <a name="privacy-notice"></a>Datenschutzbestimmungen
Mit dem allgemeinen Datenmodell vom Microsoft PowerApps sammelt und speichert Microsoft benutzerdefinierte Entitäts- und Feldnamen in unseren Diagnosesystemen. Wir verwenden diese Informationen, um das allgemeine Datenmodell für unsere Kunden zu verbessern. Die Entitäts- und Feldnamen, die von App-Erstellern erstellt werden, helfen uns dabei, Szenarien zu verstehen, die in der Microsoft PowerApps Community üblich sind, und Lücken bei den Standardentitäten des Service festzustellen, z. B. Schemas bezüglich der Organisationen. Die Daten in den Datenbanktabellen, die mit diesen Entitäten verknüpft werden, werden von Microsoft nicht verwendet, es wird nicht darauf zugegriffen und sie werden nicht außerhalb der Region, in der die Datenbank bereitgestellt wird, repliziert. Beachten Sie jedoch, dass die benutzerdefinierte Entität und die Feldnamen möglicherweise in Regionen repliziert werden und in Übereinstimmung mit unseren Richtlinien zur Datenaufbewahrung gelöscht werden. Microsoft legt großen Wert auf Ihren Datenschutz, wie weiter unten in unserem [Trust Center](https://www.microsoft.com/trustcenter/Privacy/default.aspx) beschrieben.

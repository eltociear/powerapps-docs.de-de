---
title: Entwicklung mit dem Common Data Model | Microsoft-Dokumentation
description: Enthält Informationen zur Verwendung des Common Data Model, um Apps und Lösungen zu entwickeln.
author: RobertBruckner
ms.service: powerapps
ms.topic: article
ms.date: 07/24/2018
ms.author: robruc
ms.openlocfilehash: 6e99fbe13d9b6e3acdd0cfdd08662676a321471c
ms.sourcegitcommit: abe4d4728db7f56088f618af5b820af78e7099c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332098"
---
# <a name="how-to-use-the-common-data-model"></a>Verwenden des Common Data Model

Mit dem **CDM (Common Data Model)** können Sie Ihre Daten in Formate einfügen, die häufig verwendete Konzepte und Aktivitäten darstellen sowie weitgehend verwendet und verstanden werden. Dadurch können Sie diese Daten abfragen, wiederverwenden und mit anderen Unternehmen und Anwendungen zusammenarbeiten, die ebenfalls dieses Format verwenden. Ähnlich wie bei Batterien können all Ihre Remote-Steuerelemente die Formate verwenden, wenn sie die entsprechende Größe und Form kennen. CDM definiert die Größe und Form eines *Kontakts* (Beispiel), sodass Ihre Anwendungsentwickler und Geschäftspartner wissen, wie sie diese Daten zuverlässig und schnell verwenden und Ihre Apps erstellen (oder mit ihnen zusammenarbeiten) können. Da CDM außerdem eine Open Source-Definition von Standardentitäten ist, kann die Community interessierter Entwickler Schemadefinitionen leicht verstehen und mitarbeiten.

Heutzutage wird CDM in Common Data Service für Apps (CDS) verwendet. Dieser Dienst unterstützt Dynamics und PowerApps sowie die Datenaufbereitungsfunktionen von Power BI, um schematisierte Dateien in Azure Data Lake zu erstellen.

![Common Data Model mit CDS für Apps](media/cdm-with-cds.png)

Sie können das CDM und CDS für Apps auf folgende Weisen verwenden:

-   **Daten sicher im CDM-Format speichern und verwalten:** Sie können CDS für Apps verwenden, um Ihre Daten sicher im standardisierten CDM-Format zu speichern und zu verwalten. Auf diese Weise können Sie dann in Microsoft-Apps und -Diensten wie Dynamics, PowerApps, Flow, Power BI oder Ihren eigenen benutzerdefinierten Anwendungen auf diese Daten zugreifen und diese verwenden.

-   **Benutzerdefinierte CDM-Entitäten erstellen:** Das CDM ist erweiterbar. Sie können also beliebige Entitäten erstellen, die noch nicht im CDM enthalten und auf Ihre Organisation zugeschnitten sind. Diese Entitäten können Sie dann mithilfe von **Power Query** mit Ihren vorhandenen Daten auffüllen. Dadurch können Sie die Vorteile vom CDM nutzen und es für Ihr Unternehmen anpassen.

-   **Eigene Datenrepositorys erstellen:** Sie können Datenrepositorys erstellen, die dem **CDM**-Schema entsprechen, und eine Verbindung mit diesen Datenquellen mithilfe von Datenconnectors von Microsoft herstellen. So können Sie benutzerdefinierte branchenspezifische Apps erstellen, die Ihre CDM-Daten verwenden oder freigeben, unabhängig davon, woher die Daten stammen oder wo sie gespeichert sind.

-   **Erkenntnisse schnell mithilfe von Power BI ableiten und verteilen:** Sie können erweiterte Datenaufbereitungsdienste in Power BI verwenden, die auf Ihre CDM-Datenspeicher zugreifen (z.B. Daten, die Sie in CDS für Apps eingefügt haben), um Berichte und Dashboards zu erstellen. Anschließend können Sie Apps erstellen, die Berichte generieren und Ihre CDM-Daten automatisch in benutzerdefinierte Erkenntnisse für einzelne Benutzer und Gruppen in Ihrer Organisation miteinbeziehen.

-   **Angepasste organisationsweite Berichte in Power BI erstellen:** Sie können Apps verwenden, die angepasste Berichte automatisch generieren, die Sie für Benutzer innerhalb und außerhalb Ihrer Organisation in Power BI-Arbeitsbereichen bereitstellen können.

Im Zuge der Erweiterung des Common Data Model wird mit vielen Partnern und Fachexperten zusammengearbeitet, damit neue Branchen wie das Gesundheitswesen vom CDM und den Plattformen, die es unterstützen, profitieren können.

## <a name="data-integration-and-power-query-online"></a>Datenintegration und Power Query Online

Beide Plattformen, die das CDM derzeit unterstützen, bieten über Power Query Online auch Datenintegrationsfunktionen, mit denen Benutzer Daten aus einer Vielzahl von Quellen importieren, diese bei Bedarf transformieren und anschließend CDM-Standardentitäten zuordnen oder benutzerdefinierte Entitäten erstellen können. Power Query Online nutzt die gleichen visuellen Self-Service-Datenvorbereitungsfunktionen wie Power Query in Excel und Power BI Desktop, sodass bestehende Benutzer sich schnell damit vertraut machen können.

![Zuordnen von Daten mit Entitäten in CDM](media/cdm-map-entities.png)

## <a name="common-data-service-for-apps"></a>Common Data Service für Apps

Mithilfe der darin enthaltenen Geschäftslogik, Sicherheit und Integration ermöglicht CDS für Apps Ihnen einen schnellen Einstieg in die Entwicklung von Apps mit dem CDM. Mit der Plattform können Sie:

-   **Gepackte Geschäftsanwendungen nutzen:** Viele Microsoft Dynamics-Lösungen und Drittanbieter-Anwendungen basieren auf (oder nutzen) CDS für Apps. Wenn Ihre Daten das CDM-Format verwenden, können Sie die gepackten Anwendungen nutzen.

-   **Zugriff auf benutzerdefinierte Lösungen erhalten:** Es gibt viele Erweiterungen und vollständige Anwendungen, die von Entwicklern erstellt wurden, die sich mit Daten im CDM-Format auskennen und mit diesen arbeiten. Weitere Informationen finden Sie in der [Einführung in Lösungen](https://docs.microsoft.com/powerapps/developer/common-data-service/introduction-solutions).

Mit dem CDM erhalten Ihre Daten ein einheitliches Format, sodass Sie diese für jeden Zweck einfacher verwenden, freigeben und analysieren können.

**Referenzmaterial zu CDS für Apps**

-   [Was ist CDS für Apps?](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)

-   [Hinzufügen von Daten zu einer Entität in CDS für Apps mithilfe von Power Query](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)

-   [Einführung in Lösungen](https://docs.microsoft.com/powerapps/developer/common-data-service/introduction-solutions)

-   [Build a model-driven app (Erstellen einer modellgesteuerten App)](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

-   [Build a canvas app (Erstellen einer Canvas-App)](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started)

-   [Erstellen eines Flows, der den Microsoft Common Data Service verwendet](https://docs.microsoft.com/flow/common-data-model-intro)


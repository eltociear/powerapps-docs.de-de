---
title: Über das Common Data Model | Microsoft-Dokumentation
description: Das Common Data Model ist eine standardisierte, modulare und erweiterbare Sammlung von Datenschemas, die von Microsoft veröffentlicht wurde und darauf ausgelegt ist, das Erstellen, Verwenden und Analysieren von Daten zu vereinfachen.
author: RobertBruckner
ms.service: powerapps
ms.topic: article
ms.date: 07/24/2018
ms.author: robruc
ms.openlocfilehash: 1469646301c273067ad035428f03c452ae223604
ms.sourcegitcommit: abe4d4728db7f56088f618af5b820af78e7099c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2018
ms.locfileid: "39331992"
---
# <a name="what-is-the-common-data-model"></a>Was ist das Common Data Model?

Wenn Sie jemals vor Herausforderungen mit Daten standen, die *nahezu* identisch sind oder gemeinsam funktionieren *sollten*, und Sie daraufhin beträchtlichen Aufwand in das Transformieren von Feldern und Tabellen gesteckt haben, um mit Ihren anderen Daten zu arbeiten, wissen Sie, dass einheitliche Datenelemente Aufwand sparen, zukünftige Entwicklung optimieren und schnellere Analysen ermöglichen können. Diese und weitere Funktionen können durch das Common Data Model bereitgestellt werden.

Das **Common Data Model (CDM)** ist eine standardisierte, modulare und erweiterbare Sammlung von Datenschemas, die von Microsoft veröffentlicht wurde und darauf ausgelegt ist, das Erstellen, Verwenden und Analysieren von Daten zu vereinfachen. Diese Sammlung vordefinierter Schemas, die aus *Entitäten*, *Attributen*, *semantischen Metadaten* und *Beziehungen* besteht, stellt häufig verwendete Konzepte und Aktivitäten (z.B. Konten und Kampagnen) dar, die die Erstellung, Aggregation und Analyse von Daten vereinfachen. Weitere Information: [CDM repo on GitHub (CDM-Repository auf GitHub)](https://aka.ms/cdmrepo)

![Common Data Model](media/cdm-entities.png)

Weitere Informationen: [CDM-Poster](https://aka.ms/cdmposter)

## <a name="why-use-the-common-data-model"></a>Gründe für die Verwendung des Common Data Model

Das CDM vereinfacht die Verwaltung von Daten und die Anwendungsentwicklung durch Vereinheitlichung in ein bekanntes Format und durch die Anwendung struktureller und semantischer Konsistenz auf Anwendungen und Bereitstellungen. Das heißt, sobald Ihre Daten dem CDM entsprechen, können Sie sie in vielen verschiedenen Anwendungen verwenden, die Erstellung oder Verwendung anderer Anwendungen zur Nutzung vorhandener Daten optimieren und problemlos Berichte für jede Anwendung (oder alle Anwendungen) erstellen. Darüber hinaus können Datenintegratoren, die Daten aus einer Vielzahl von Systemen integrieren, sich darauf konzentrieren, die Daten in das CDM-Format zu transformieren, anstatt ein neues Modell für jede Anwendung zu erstellen.

Angenommen, Sie verfügen über drei Unternehmensanwendungen: eine Material-App, eine Fertigungs-App und eine Vertriebs-App. Häufig wird jede dieser Anwendungen unabhängig voneinander mit verschiedenen Strukturen erstellt, die Entitäten darstellen, z.B. *Konten*, die sich stark ähneln, aber nicht identisch sind. Mit dem CDM können Sie Ihre Daten in einem standardisierten Format erstellen (mit CDM- Entitäten, -Attributen und -Beziehungen) und für jede dieser drei Apps die gleichen Daten als Grundlage verwenden. Jede App kann basierend auf der Funktionalität der jeweiligen App über eigene zusätzliche Daten und Schemas verfügen. Bei der Entwicklung können Sie die einheitlichen Datenelemente schnell, problemlos und zuverlässig für Ihre Anwendungen und Berichte abrufen.

Und wie sieht es aus, wenn Sie eine vierte App erstellen müssen? Ihre Daten stehen im CDM-Schema zur Verfügung, Sie können sich bei der Entwicklung also voll und ganz auf die Geschäftslogik konzentrieren, ohne erneut Zeit in Daten und Transformationen investieren zu müssen.

Das bedeutet, dass CDM Folgendes für Ihre Daten bietet:

-   **Strukturelle und semantische Konsistenz** für Anwendungen und Bereitstellungen.

-   **Vereinfachte Integration und Eindeutigkeit von Daten**, die aus Prozessen, digitalen Interaktionen, Produkttelemetrie, Interaktionen von Personen usw. gesammelt werden.

-   **Eine einheitliche Form**, in die Datenintegratoren **vorhandene Unternehmensdaten mit anderen Quellen zusammenführen** und diese Daten ganzheitlich verwenden, um neue Anwendungen zu entwickeln oder Erkenntnisse abzuleiten.

-   **Die Möglichkeit, das Schema und CDM-Entitäten zu erweitern**, um das CDM an Ihre Organisation anzupassen.

Sie können das CDM verwenden, um neue Datenrepositorys zu erstellen, die mit dem Schema übereinstimmen. Außerdem können Sie Ihre vorhandenen Daten in das CDM-Schema transformieren. In beiden Fällen beschleunigt und optimiert die Standardisierung Ihre zukünftigen Schritte mit den Daten.

## <a name="who-uses-the-common-data-model"></a>Wer verwendet das Common Data Model?

Das CDM wird von einer Vielzahl von Kunden, Partnern und Produkten mit dem gleichen Ziel verwendet: zur Vereinheitlichung von Daten in einem bekannten Format mit semantischer Bedeutung.

-   **Anwendungsentwickler:** Unabhängig davon, ob diese Benutzer codebasierte Plattformen oder eine Plattform mit keinen oder nur wenigen Codekomponenten wie PowerApps verwenden, müssen sie Daten für Ihre Anwendungen speichern und verwalten.

-   **Datenintegratoren:** Diese Benutzer sind dafür verantwortlich, Daten aus verschiedenen Systemen zusammenzuführen, um diese zur Verwendung durch Anwendungen zur Verfügung zu stellen.

Früher war das Erstellen einer Anwendung eng mit der Datenintegration verknüpft. Mit dem CDM und den Plattformen, die es unterstützen, kann beides jedoch unabhängig voneinander durchgeführt werden.

## <a name="common-data-model-in-action"></a>Common Data Model in Aktion

Microsoft und seine Partner verwenden das CDM für ihre eigenen Anwendungen und Angebote. Außerdem erstellen sie zusätzliche Dienste und Angebote auf der Grundlage von CDM-Schemas. In den folgenden Beispielen wird veranschaulicht, wie Organisationen das CDM verwenden:

-   **Common Data Service für Apps** unterstützt Dynamics und PowerApps und speichert Daten konform zur CDM-Definition. Tatsächlich stammen viele der ursprünglichen im CDM enthaltenen Geschäftsentitäten aus Dynamics-Angeboten wie Dynamics 365 for Sales und Dynamics 365 for Marketing.

-   **Industriezweige** wie das Gesundheitswesen arbeiten eng mit Microsoft zusammen, um das CDM mit ihren spezifischen Geschäftskonzepte zu erweitern, z.B. *Patienten* und *Pflegepläne*, sodass diese Daten freigegeben und Dienste erstellt werden können, mit denen Partner Daten einfach austauschen und interoperable Apps und Dienste sowie schnelle Analysen erstellen können, die einfach freizugeben sind.

## <a name="next-step"></a>Nächster Schritt

[How to use the Common Data Model (Verwenden des Common Data Model):](use-common-data-model.md) In diesem Artikel wird das CDM ausführlich beschrieben. Außerdem werden Anwendungsfälle für die Erstellung neuer Daten im CDM und die Transformierung vorhandener Daten in CDM erläutert.
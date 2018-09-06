---
title: 'Übersicht für Entwickler: Modellgesteuerte Apps | Microsoft-Dokumentation'
description: Erfahren Sie, wie Entwickler zu modellgesteuerten Apps beitragen können.
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/17/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 39fe83cdb059e0f1df634b9933f4a2f4251bca7b
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42852412"
---
# <a name="model-driven-apps-developer-overview"></a>Übersicht für Entwickler: Modellgesteuerte Apps

PowerApps bietet Benutzern, Unternehmen, Partnern, unabhängigen Softwareherstellern und Systemintegratoren eine leistungsstarke Plattform für das Erstellen von branchenspezifischen Apps. Modellgesteuerte Apps, die mit Common Data Service für Apps erstellt wurden, wurden in diesem Release von PowerApps neu hinzugefügt. Common Data Service für Apps enthält nun die Kernfunktionen der Dynamics 365 Customer Engagement-Anwendungen. Mit modellgesteuerten Apps können Sie Apps erstellen, die dieselben Erweiterungsfunktionen wie diese Anwendungen verwenden.

Modellgesteuerte Apps sind in erster Linie ein Ansatz zum Entwickeln von Apps ohne oder nur mit wenigen Codekomponenten. Entwickler können durch Erweiterungen zu der Anwendung beitragen. Bevor Sie mit dem Schreiben von Code beginnen, sollten Sie lernen, wie Sie eine modellgesteuerte App erstellen, und welche Optionen ohne Code angewendet werden können. 

## <a name="get-started"></a>Erste Schritte
Wenn Sie bereits Erfahrung mit den Dynamics 365 Customer Engagement-Apps haben, können Sie diese Erfahrungen beim Erstellen von modellgesteuerten Apps nutzen. Es stehen zwar neue Designer zur Verfügung, im Allgemeinen sind deren Konzepte jedoch gleich.

> [!NOTE]
> Modellgesteuerte Apps sind mit Common Data Service für Apps verbunden. Informationen darüber, wie Entwickler auf Anwendungsebene einen Beitrag leisten können, finden Sie unter [Common Data Service for Apps Developer Overview (Übersicht für Entwickler: Common Data Service für Apps)](../common-data-service/overview.md).
> Der Inhalt dieses Abschnitts befasst sich ausschließlich mit Erweiterungen, die von Entwicklern angewendet werden können und sich auf die Benutzerfreundlichkeit von modellgesteuerten Apps beziehen. 

Wenn Sie noch nicht mit Dynamics 365 Customer Engagement-Anwendungen vertraut sind, finden Sie in den Themen in diesem Abschnitt eine allgemeine Übersicht über die wichtigen Konzepte, die beim Einstieg in die Arbeit mit modellgesteuerten Apps helfen. 

> [!NOTE]
> Da Common Data Service für Apps und Dynamics 365 Customer Engagement dieselbe Plattform verwenden, finden Sie ausführlichere Informationen für Entwickler im [Entwicklerhandbuch zu Dynamics 365 Customer Engagement](/dynamics365/customer-engagement/developer/developer-guide). In diesen Artikel erhalten Sie eine Übersicht mit Links zum Entwicklerhandbuch und anderen Handbüchern, die weitere Informationen enthalten.


## <a name="community-tools-for-model-driven-apps"></a>Communitytools für modellgesteuerte Apps

Die Dynamics 365-Community erstellt Tools. Viele der beliebtesten Tools werden über [XrmToolBox](https://www.xrmtoolbox.com/) veröffentlicht. XrmToolBox ist eine Windows-Anwendung, die eine Verbindung mit Common Data Service für Apps herstellt, um Tools bereitzustellen, mit denen die Anpassungs-, Konfigurations- und Vorgangsaufgaben erleichtert werden. Die Anwendung enthält mehr als 30 Plug-Ins, um Verwaltungs-, Anpassungs- oder Konfigurationsaufgaben zu vereinfachen und zu beschleunigen.

Im Folgenden finden Sie eine Liste mit ausgewählten Communitytools, die über XrmToolBox verteilt wurden und die Sie für die Arbeit mit modellgesteuerten Apps verwenden können.

|Tool  |Beschreibung  |
|---------|---------|
|[Easy Translator](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/)|Exportieren und Importieren von Übersetzungen mit kontextbasierten Informationen|
|[Export to Excel](https://www.xrmtoolbox.com/plugins/Ryr.XrmToolBox.ExportToExcel/)|Einfaches Exportieren von Datensätzen aus der ausgewählten Ansicht oder über FetchXML in Excel|
|[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)|Verwalten von benutzerdefinierten Entitätssymbolen in nur einem Bildschirm|
|[Ribbon Workbench 2016](https://www.xrmtoolbox.com/plugins/RibbonWorkbench2016/)|Bearbeiten des Dynamics CRM-Menübands oder der Befehlsleiste innerhalb von XrmToolBox|
|[View Designer](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.ViewDesigner/)|Einfache Benutzeroberfläche zum Entwerfen von Ansichtslayouts und Ändern von Abfragen mithilfe von FetchXML Builder|
|[View Layout Replicator](https://www.xrmtoolbox.com/plugins/MsCrmTools.ViewLayoutReplicator/)|Anwenden des gleichen Layouts auf mehrere Ansichten der gleichen Entität innerhalb eines einzelnen Vorgangs|
|[WebResources Manager](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/)|Einfaches Verwalten von Webressourcen|

Ein weiteres nützliches Tool, das nicht über XrmToolBox veröffentlicht wird, heißt [CRM REST Builder](https://github.com/jlattimer/CRMRESTBuilder) von Jason Lattimer. Dieses Tool erstellt JavaScript-Code für die Verwendung mit der Web-API.

> [!NOTE]
> Von der Community erstellte Tools werden nicht von Microsoft unterstützt. Wenden Sie sich an den Herausgeber, wenn Sie Probleme mit oder Fragen zu einem Tool haben.





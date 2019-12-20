---
title: Erstellen Sie 1:n- (eins-zu-viele) oder n:1-Beziehungsentitäten (viele zu eins) in Power Apps-Übersicht | Microsoft-Dokumentation
description: Erfahren Sie, wie 1:n- oder n:1-Entitäts-Beziehungen erstellt werden
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 52c00707-b2bc-4950-abec-89baefd94f6e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 07e173dff08a10de5354c08d3530605f530e512d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866133"
---
# <a name="create-one-to-many-or-many-to-one-entity-relationships-overview"></a>Erfahren Sie, wie 1:n- oder n:1-Entitäts-Beziehungsübersichten erstellt werden

Definieren Sie in Common Data Service 1:n oder n:1-Beziehungen, wie zwei Entitäten miteinander verknüpft sind. 
  
Bevor Sie eine benutzerdefinierte Entitätsbeziehung erstellen, prüfen Sie, ob die Verwendung einer vorhandenen Entitätsbeziehung Ihre Anforderungen erfüllen könnte. <br />Weitere Informationen [Neue Metadaten oder bestehende Metadaten erstellen](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Es gibt zwei Ansicht, die Sie verwenden können, um 1:n (eine-zu-vielen) oder N:1 (viele-zu-einer) Beziehungen:

|Designer| Beschreibung|
|--|--|
|[Power Apps-Portal](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.<br />Weitere Informationen: [Erstellen und Bearbeiten von 1:n oder n:1-Entitätsbeziehungen im Power Apps-Portal](create-edit-1n-relationships-portal.md)|
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen. <br />Weitere Informationen: [Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen mit dem Lösungsexplorer](create-edit-1n-relationships-solution-explorer.md) |

> [!NOTE]
> Sie können eine neue Entitätsbeziehung folgendermaßen auch in Ihrer Umgebung erstellen mithilfe des Folgenden:
> - In Modell-angetriebenen Apps wählen Sie **Neues Feld** vom Formular-Editor und erstellen ein Feld *Suchen*. <br />Weitere Informationen: [Hinzufügen von Feldern zu einem Formular](../model-driven-apps/add-field-form.md)
> - Erstellen Sie ein neues Suchfeld für die verknüpfte Entität. <br />Weitere Informationen: [Erstellen und Bearbeiten von Feldern](create-edit-fields.md)
> - Importieren Sie eine Lösung, die die Definition der Entitäsbeziehung enthält. <br />Weitere Informationen dazu finden Sie [Lösungen importieren, aktualisieren und exportieren](import-update-export-solutions.md)
> - Verwenden Sie Power-Abfrage, um neue Entitäten zu erstellen und diese mit Daten auszufüllen. <br />Weitere Informationen: [Daten einer Entität in Common Data Service mithilfe von Power Query hinzufügen](data-platform-cds-newentity-pq.md).
> - Ein Entwickler kann [Metadatendienste](../../developer/common-data-service/metadata-services.md) verwenden, um ein Programm zum Schreiben, um Entitätsbeziehungen zu erstellen und zu aktualisieren. <br />Weitere Informationen finden Sie unter [Anpassen von Entitätsbeziehungsmetadaten](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata).

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. 

Sie sollten das Power Apps-Portal verwenden, um 1:n oder n:1-Entitätsbeziehungen zu erstellen und zu bearbeiten, es sei denn, Sie müssen eine der folgenden Anforderungen erfüllen:

- Konfigurieren der Feldzuordnung
- Konfigurieren Sie Navigationsbereichsoptionen für modellgetriebene Apps.
- Konfigurieren des Verhaltens von Beziehungen
- Definieren Sie, ob in der Beziehung der erweiterten Suche ausgeblendet ist.
- Hierarchische Beziehung erstellen


## <a name="community-tools"></a>Community-Tools

**[Entitätsbeziehungs-Diagrammersteller](https://www.xrmtoolbox.com/plugins/JourneyIntoCRM.XrmToolbox.ERDPlugin/)** ist ein Tool, das XrmToolbox-Community für Common Data Service entwickelte. Weitere Informationen finden Sie im Thema [Entwicklertools Common Data Service](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Microsoft und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)<br />
[Erstellen und Bearbeiten von 1:N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen im Power Apps-Portal](create-edit-1n-relationships-portal.md)<br />
[Erstellen oder Bearbeiten von 1: N (1: n- oder n: n) Entitätsbeziehungen 1 mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)<br />
[Entwicklerdokumentation: Entitätsbeziehungseignungsmetadaten anpassen](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[Entwicklerdokumentation: Entitätsbeziehungseignung](/dynamics365/customer-engagement/developer/entity-relationship-eligibility)



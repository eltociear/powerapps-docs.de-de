---
title: 'Erstellen Sie 1:n- (eins-zu-viele) oder n:1-Beziehungsentitäten (viele zu eins) in PowerApps Übersicht | MicrosoftDocs'
description: 'Erfahren Sie, wie 1:n- oder n:1-Entitäts-Beziehungen erstellt werden'
ms.custom: ''
ms.date: 05/27/2018
ms.reviewer: ''
ms.service: crm-online
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
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-one-to-many-or-many-to-one-entity-relationships-overview"></a>Erfahren Sie, wie 1:n- oder n:1-Entitäts-Beziehungsübersichten erstellt werden

Im Common Data Service für Apps 1: N (1: n) oder n: 1-Beziehungen definieren Sie, wie zwei Entitäten miteinander verknüpft sind. 
  
Bevor Sie eine benutzerdefinierte Entitätsbeziehung erstellen, prüfen Sie, ob die Verwendung einer vorhandenen Entitätsbeziehung Ihre Anforderungen erfüllen könnte. <br />Weitere Informationen [Neue Metadaten oder bestehende Metadaten erstellen](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

Es gibt zwei Ansicht, die Sie verwenden können, um 1:n (eine-zu-vielen) oder N:1 (viele-zu-einer) Beziehungen:

|Designer| Beschreibung|
|--|--|
|[PowerApps-Portal](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|Gibt eine einfache konzentrierte Erfahrung, aber einige besondere Einstellungen sind nicht verfügbar.<br />Weitere Informationen: [Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen im PowerApps Portal](create-edit-1n-relationships-portal.md)|
|Projektmappen-Explorer|Nicht so einfach, aber gibt mehr Flexibilität für weniger allgemeine Anforderungen. <br />Weitere Informationen: [Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen mit dem Lösungsexplorer](create-edit-1n-relationships-solution-explorer.md) |

> [!NOTE]
> Sie können eine neue Entitätsbeziehung folgendermaßen auch in Ihrer Umgebung erstellen mithilfe des Folgenden:
> - In Modell-angetriebenen Apps wählen Sie **Neues Feld** vom Formular-Editor und erstellen ein Feld *Suchen*. <br />Weitere Informationen: [Hinzufügen von Feldern zu einem Formular](../model-driven-apps/add-field-form.md)
> - Erstellen Sie ein neues Suchfeld für die verknüpfte Entität. <br />Weitere Informationen: [Erstellen und Bearbeiten von Feldern](create-edit-fields.md)
> - Importieren Sie eine Lösung, die die Definition der Entitäsbeziehung enthält. <br />Weitere Informationen dazu finden Sie [Lösungen importieren, aktualisieren und exportieren](import-update-export-solutions.md)
> - Verwenden Sie Power-Abfrage, um neue Entitäten zu erstellen und diese mit Daten auszufüllen. <br />Weitere Informationen:  [Daten einer Entität in Common Data Service für Apps mithilfe der Power-Abfrage hinzufügen](data-platform-cds-newentity-pq.md).
> - Ein Entwickler kann [Metadatendienste](../../developer/common-data-service/metadata-services.md) verwenden, um ein Programm zum Schreiben, um Entitätsbeziehungen zu erstellen und zu aktualisieren. <br />Weitere Informationen finden Sie unter [Anpassen von Entitätsbeziehungsmetadaten](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata).

Die Informationen in diesem Thema helfen Ihnen auswählen, welche Designer Sie verwenden können. 

Sie sollten das PowerApps-Portal verwenden, um Eine-zu-viele (1:N) oder N:1 ( viele-zu-einer)-Entitätsbeziehungen zu erstellen und zu bearbeiten, außer Sie müssen eine der folgenden Anforderungen erfüllen:

- Konfigurieren der Feldzuordnung
- Konfigurieren Sie Navigationsbereichsoptionen für modellgetriebene Apps.
- Konfigurieren des Verhaltens von Beziehungen
- Definieren Sie, ob in der Beziehung der erweiterten Suche ausgeblendet ist.
- Hierarchische Beziehung erstellen


## <a name="community-tools"></a>Community-Tools

**[Entitäts-Beziehungs-Diagramm-Ersteller](https://www.xrmtoolbox.com/plugins/JourneyIntoCRM.XrmToolbox.ERDPlugin/)** ist ein Tool, das XrmToolbox-Community für CDS für Apps entwickelte. Weitere Informationen finden Sie im [Entwicklertools für Common Data Service für Apps](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) Thema für Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Microsoft und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).

### <a name="see-also"></a>Siehe auch

[Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](create-edit-entity-relationships.md)<br />
[Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer) Entitätsbeziehungen im PowerApps Portal zu erstellen oder zu bearbeiten](create-edit-1n-relationships-portal.md)<br />
[Erstellen oder Bearbeiten von 1: N (1: n- oder n: n) Entitätsbeziehungen 1 mithilfe des Lösungs-Explorers](create-edit-1n-relationships-solution-explorer.md)<br />
[Entwicklerdokumentation: Entitätsbeziehungseignungsmetadaten anpassen](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[Entwicklerdokumentation: Entitätsbeziehungseignung](/dynamics365/customer-engagement/developer/entity-relationship-eligibility)



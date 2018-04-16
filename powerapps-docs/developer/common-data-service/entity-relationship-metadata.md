---
title: Entitätsbeziehungsmetadaten | Microsoft-Dokumentation
description: Informationen zu Entitätsbeziehungsmetadaten, die in Common Data Service für Apps verwendet werden.
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
ms.date: 03/12/2018
ms.author: jdaly
ms.openlocfilehash: da8899151fdb40713d19ca1cb82444a486526549
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="entity-relationship-metadata"></a>Entitätsbeziehungsmetadaten

Wenn man den Projektmappen-Explorer oder die drei Auflistungen in `EntityMetadata` betrachtet, könnte man annehmen, dass es drei Typen von Entitätsbeziehungen gibt. Wie in der folgenden Tabelle dargestellt, sind es allerdings nur zwei.

|Beziehungstyp|Beschreibung|
|--|--|
|1:n<br />[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)|Eine Entitätsbeziehung, bei der ein Entitätseintrag zur **primären Entität** vielen anderen Einträgen zur **verknüpften Entität** zugewiesen werden kann, da auf der verknüpften Entität ein Nachschlagefeld verfügbar ist.<br />Wenn Sie einen Eintrag zu einer primären Entität abrufen, wird eine Liste der Einträge zu der verknüpften Entität angezeigt, die dieser zugewiesen sind.|
|m:n<br />[ManyToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata)|Eine Entitätsbeziehung, die von einer bestimmten *Entitätsbeziehung* abhängig ist (manchmal als *überschneidende* Entität bezeichnet), damit mehrere Einträge für eine Entität mehreren Einträgen für eine andere Entität zugeordnet werden können.<br />Wenn Sie die Einträge zu einer beliebigen Entität in einer m:n-Beziehung abrufen, wird eine Liste der Einträge zu der anderen Entität angezeigt, die dieser zugeordnet sind.|

Die `ManyToOneRelationships`-Auflistung von `EntityMetadata` enthält [OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)-Typen. 1:n-Beziehungen bestehen zwischen Entitäten und verweisen entweder als *primäre Entitäten* oder als *verknüpfte Entitäten* auf die einzelnen Entitäten. Die verknüpfte Entität, die manchmal als *untergeordnete Entität* bezeichnet wird, verfügt über ein Suchattribut, über das ein Verweis auf einen Eintrag aus der primären Entität gespeichert werden kann, die manchmal als *übergeordnete Entität* bezeichnet wird. Aus der Sicht der verknüpften Entität ist eine n:1-Beziehung nur eine 1:n-Beziehung.

> [!NOTE]
> Verknüpfte Entitäten werden zwar manchmal als *untergeordnete Entitäten* bezeichnet, Sie sollten sie aber nicht mit [untergeordneten Entitäten](entity-metadata.md#child-entities) verwechseln, die sich darauf beziehen, wie Sicherheit auf verknüpfte Entitäten angewendet wird.

Weitere Informationen finden Sie unter:
- [Erstellen und Bearbeiten von Beziehungen zwischen Entitäten](/dynamics365/customer-engagement/customize/create-edit-entity-relationships)
- [Anpassen von Entitätsbeziehungsmetadaten](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

## <a name="cascade-configuration"></a>Weitergeben von Konfigurationen

Wenn eine 1:n-Beziehung besteht, bestehen auch Weitergabeverhalten, die konfiguriert werden können, um die Datenintegrität beizubehalten und Unternehmensprozesse zu automatisieren.

Weitere Informationen finden Sie unter:

- [Dynamics 365 Customer Engagement Customization Guide: Create 1:N (one-to-many) or N:1 (many-to-one) relationships > Relationship behavior (Handbuch zur Anpassung von Dynamics 365 Customer Engagement: Erstellen von 1:n- oder n:1-Beziehungen > Beziehungsverhalten)](/dynamics365/customer-engagement/customize/create-and-edit-1n-relationships#relationship-behavior)
- [Entitätenbeziehungsverhalten](/dynamics365/customer-engagement/developer/entity-relationship-behavior)


## <a name="create-a-hierarchy-of-entities"></a>Erstellen einer Entitätshierarchie

Sie können innerhalb einer auf sich selbst verweisenden 1:n-Beziehung eine Hierarchie einrichten, indem Sie die `IsHierarchical`-Eigenschaft auf `true` festlegen.

Bei modellgesteuerten Apps wird dadurch eine Funktion aktiviert, mit der Sie die Hierarchie anzeigen und mit ihr interagieren können. 

Für Entwickler werden dadurch neue Abfragetypen aktiviert, die auf der Hierarchie basieren, die die Operatoren `Under` und `Not Under` verwendet.

Weitere Informationen finden Sie unter: [Abfragen und Visualisieren von hierarchiebezogenen Daten](/dynamics365/customer-engagement/customize/query-visualize-hierarchical-data)

### <a name="see-also"></a>Siehe auch

[Entitäten in Common Data Service für Apps](entities.md)
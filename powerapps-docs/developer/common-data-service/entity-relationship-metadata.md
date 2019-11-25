---
title: Entitätsbeziehungsmetadaten | Microsoft Docs
description: Weitere Informationen über die Entitätsbeziehungsmetadaten, die in Common Data Service verwendet werden.
services: ''
suite: powerapps
documentationcenter: na
author: mayadumesh
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/31/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d6d0f5aee398d83227f365ac5bb73ccea8068ed4
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748290"
---
# <a name="entity-relationship-metadata"></a>Entitätsbeziehung von Metadaten

Wenn Sie sich den Lösungsexplorer oder die drei Beziehungssammlungen in er `EntityMetadata` ansehen, denken Sie vielleicht, dass es drei Arten von Entitätsbeziehungen gibt. Tatsächlich sind es nur zwei, wie in der nachfolgenden Tabelle gezeigt wird.

|Beziehungstyp|Beschreibung|
|--|--|
|Eine zu Vielen<br />[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)|Eine Entitätsbeziehung, bei der ein Datensatz für die **Primäre Entität** mit mehreren anderen **Verknüpften Entitäts**-Datensätzen durch ein Suchfeld in der verknüpften Entität verknüpft werden kann.<br />Wenn Sie einen Datensatz der primären Entität anzeigen, sehen Sie eine Liste der verknüpften Datensätze, die dieser Entität zugeordnet sind.|
|Viele zu Viele<br />[ManyToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata)|Eine Entitätsbeziehung, die von einer speziellen *Beziehungsentität* abhängig ist, oft als *Überschneidungs*entität bezeichnet, so dass mehrere Datensätze einer Entität mit mehreren Datensätzen einer anderen Entität verknüpft werden können.<br />Wenn Datensätze von verschiedenen Entitäten in einer N:N-Beziehung angezeigt werden, können Sie eine Liste aller Datensätze der anderen Entität anzeigen, die damit verknüpft sind.|

Eine `EntityMetadata` `ManyToOneRelationships` Sammlung enthält [OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)-Typen. 1:n-Beziehungen bestehen zwischen Entitäten und verweisen auf jede Entität entweder als *Primäre Entität* or *Verknüpfte Entität*. Die verknüpfte Entität, oft als *untergeordnete* Entität bezeichnet, verfügt über ein Suchattribut, in dem das Speichern eines Verweises zu einem Datensatz aus der primären Entität, oft als *übergeordnete* Entität bezeichnet, möglich ist. Eine n: 1-Beziehung ist nur die untergeordnete Perspektive einer 1: n-Beziehung von der verknüpften Entität betrachtet.

> [!NOTE]
> Die verknüpfte Entitäten werden in *untergeordnete Entitäten* angezeigt, verwechseln Sie diese nicht mit [Untergeordnete Entitäten](entity-metadata.md#child-entities), die sich darauf bezieht, wie die  Sicherheit zu verknüpften Entitäten angewendet werden.

Weitere Informationen: [Erstellen von Beziehungen zwischen Entitäten](../../maker/common-data-service/data-platform-entity-lookup.md)

## <a name="cascade-configuration"></a>Kaskadierende Konfiguration

Wenn eine 1:n-Entitätsbeziehung vorhanden ist, gibt es kaskadierende Verhaltensweisen, die konfiguriert werden können, um die Datenintegrität und zu erhalten und Geschäftsprozesse zu automatisieren. Weitere Informationen: [ Konfigurieren der Entitätsbeziehungen mit ableitendem Verhalten](configure-entity-relationship-cascading-behavior.md)

## <a name="create-a-hierarchy-of-entities"></a>Erstellen Sie eine Hierarchie von Entitäten

Innerhalb einer auf sich selbst verweisenden 1: n-Beziehung können Sie eine Hierarchie festlegen, indem Sie die angezeigten `IsHierarchical`Eigenschaften auf `true` festlegen.

Mit Modell-angetriebenen Apps ermöglicht es eine Umgebung, die Sie aktivieren, die Hierarchie anzuzeigen und damit und interagieren zu können. 

Entwickler können diese neue Typen von Abfragen anhand der Hierarchie mit `Under` und `Not Under` Operatoren aktivieren.

Weitere Informationen: [Common Data Service Entwicklerhandbuch: Hierarchisch verknüpfte Daten abfragen und visualisieren](/dynamics365/customer-engagement/customize/query-visualize-hierarchical-data).

### <a name="see-also"></a>Siehe auch

[Common Data Service-Entitäten](entities.md)

---
title: Common Data Service-Entitäten | Microsoft-Dokumentation
description: Weitere Informationen über die Entitäten, die in Common Data Service verfügbar sind.
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
ms.openlocfilehash: 8bd68d7a1039be8254dda59d7d1f45d52e15b899
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861795"
---
<!-- 
Was Mike Carter
This topic was not migrated it was written for Power Apps 

Overlap with content in https://docs.microsoft.com/dynamics365/customer-engagement/developer/introduction-entities

-->

# <a name="common-data-service-entities"></a>Common Data Service-Entitäten

Stellt Speicher für Daten in den wichtigsten Funktion des Common Data Service bereit. Common Data Service umfasst einen Basissatz von Entitäten, die die Struktur für die erfassten Daten bereitstellt, die von Geschäftsanwendungen verwendet werden. 

Sie können den Basissatz der Entitäten in der [Common Data Service-Entitätsreferenz anzeigen](reference/about-entity-reference.md).

## <a name="modify-entities"></a>Ändern von Entitäten

Sie können die Entitätsmetadaten mithilfe von einer Reihe von Methoden ändern.

### <a name="use-designers"></a>Designer nutzen

Es gibt verschiedene Möglichkeiten, Entitätsmetadaten mithilfe eines Designers zu bearbeiten:


|Designer  |Beschreibung  |
|---------|---------|
|powerapps.com|Die einfachste und beste Methode, das Schema zu ändern ist es, die Website [powerapps.com](https://make.powerapps.com/) zu verwenden, um die Common Data Service zu bearbeiten, die einer Umgebung zugeordnet sind. Änderungen, die angewendet werden, werden im Rahmen einer nicht verwalteten Common Data Service-Standardlösung ausgeführt. <!-- TODO: Add link to topic that describes this -->|
|Common Data Service Standard-Projektmappen-Explorer|Es gibt einen anderen Designer von der Website [powerapps.com](https://make.powerapps.com/), wenn Sie Common Data Service bearbeiten. In der unteren linken Ecke öffnet die Schaltfläche **Erweitert** den Lösungsexplorer in der Standardlösung Common Data Service. |
|Lösungsexplorer für Ihre Lösung |Wenn Sie eine Lösung verteilen, sollten Sie alle neuen Entitäten, Attribute und Beziehungen im Kontext einer nicht verwalteten Lösung erstellen, die Sie verwenden, um Ihre Lösung zu entwickeln. <br /> Weitere Informationen: [Erstellen eines Lösungsherausgebers und eine Lösung](introduction-solutions.md#create-a-solution-publisher-and-solution)|
|Vom Formular-Editor|Wenn Sie ein Modell-angetriebenes App-Formular für eine Entität bearbeiten, können Sie auf der Schaltfläche **Neues Feld** auf **Feld-Explorer** klicken. Wenn Sie ein Suchfeld erstellen, erstellen Sie eine neue Entitätsbeziehung zur Unterstützung|

### <a name="import-a-solution"></a>Importieren einer Lösung

Eine Lösung kann Entitätsmetadaten und andere benutzerdefinierte Komponenten enthalten. Das Importieren einer verwalteten oder nicht verwalteten Lösung in Ihren Common Data Service-Mandanten enthält die Entitäten oder erweiterte vorhandene Entitäten mit den neuen Entitätsmetadaten, die sie beinhalten.

### <a name="from-a-data-source-using-power-query"></a>Von einer Datenquelle mithilfe Power-Abfrage

Sie können neue Entitäten erstellen und diese mit Daten mithilfe von Power-Abfrage ausfüllen. Weitere Informationen: [Daten einer Entität in Common Data Service mithilfe von Power Query hinzufügen](../../maker/common-data-service/data-platform-cds-newentity-pq.md)

### <a name="use-metadata-services"></a>Verwenden von Metadaten-Services

Die Webdienste, die in den Common Data Service verfügbar gemacht werden, umfassen Funktionen, um Entitätsmetadaten zu erstellen, lesen, schreiben und löschen. Diese Dienste werden am häufigsten verwendet, um die Metadatenänderung zu lesen, da diese Daten  Ihren Code zu Laufzeit informieren können, inwieweit die Umgebung angepasst wurde. Weitere Informationen: [Metadaten-Services](metadata-services.md)

## <a name="entity-metadata"></a>Entitätsmetadaten

Das Datenmodell ist als Metadaten definiert, die innerhalb des Common Data Service gespeichert ist. Diese Daten über das Schema sind als *Entitätsmetadaten* bekannt. 

- [EntityMetadata-Klasse](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata) definiert die mit dem Organisationsservice. 
- Der [EntityMetadata EntityType](/dynamics365/customer-engagement/web-api/entitymetadata) definiert das für die Web API. 

Die Entitätsmetadaten umfassen die folgenden Informationen:


|Daten  |Beschreibung  |
|---------|---------|
|Entitätseigenschaften|Jede Entität besitzt fast 100 Eigenschaften, die beschreiben, wie es identifiziert wird und was mit ihm abgeschlossen werden kann.  Weitere Informationen finden Sie unter [Entitätsmetadaten](entity-metadata.md).|
|Attribute|Die Entitäts `Attributes` eigenschaft ist eine Sammlung von Attributen. Jedes Attribut enthält ungefähr 50 Eigenschaften, die beschreiben, wie es erkannt wird, den Datentyp, den es enthält, wie es formatiert wird und was mit ihm abgeschlossen werden kann. Weitere Informationen: [Metadaten-Attribut](entity-attribute-metadata.md)|
|Beziehungen|Drei der Entitätseigenschaften sind Sammlungen von Beziehungen zwischen Entitäten. Diese Sammlungen enthalten verschiedene Arten von Beziehungen: M: n, n: 1 und 1: n-. Weitere Informationen: [Entitätsbeziehungen Metadaten](entity-relationship-metadata.md)|
|Rechte|Eine der Entitätseigenschaften ist eine Sammlung zwischen 0 und 8 Rechten, die die Arten von Datenenvorgängen identifizieren, die auf der betreffenden Entität mit einem eindeutigen Bezeichner ausgeführt werden, die jedem zugeordnet sind. Diese umfassen Vorgänge: *Anfügen*, *AppendTo*, *Zuweisen*, *Erstellen*, *Löschen*, *Lesen*, *Freigeben* und *Schreiben*.|
|Schlüssel|Standardmäßig verfügt jede Entität über ein einzelnes GUID Attribut (Globally Unique Identifier) und die `Keys`-Eigenschaft ist eine leere Sammlung. Sie können Alternativschlüssel einer Entität hinzufügen. Weitere Informationen:[Entitätsschlüssel](entity-metadata.md#entity-keys)|

> [!TIP]
> Ein gutes Verständnis der Entitäts-Metadaten im System hilft dabei zu verstehen, wie die Common Data Service funktioniert. Viele der Eigenschaften steuern auch, welche Entitäten Sie in Modell-angetriebenen Apps vornehmen können. Die Designer, die zum Bearbeiten der Metadaten verfügbar sind, können nicht alle Details anzeigen, die in den Metadaten gefunden werden. Sie können eine modellgesteuerte App mit dem Namen Browser für Metadaten installieren, die es Ihnen ermöglicht, alle ausgeblendeten Entitäten- und Metadateneigenschaften anzuzeigen, die im System vorhanden sind. Weitere Informationen: [Durchsuchen der Metadaten für Ihre Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata).

### <a name="see-also"></a>Siehe auch

[Common Data Service-Entwicklerübersicht](overview.md)



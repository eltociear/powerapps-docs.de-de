---
title: Entitäten in Common Data Service für Apps | Microsoft-Dokumentation
description: Informationen zu Entitäten, die in Common Data Service für Apps verfügbar sind.
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
ms.date: 03/19/2018
ms.author: jdaly
ms.openlocfilehash: 98f2360e29af7cb0bdf5caf041dfa13b933e6323
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-service-for-apps-entities"></a>Entitäten in Common Data Service für Apps

Die wichtigste Funktion von Common Data Service für Apps ist das Speichern von Daten. Common Data Service umfasst verschiedene grundlegende Entitäten, die die von Geschäftsanwendungen verwendeten Daten strukturieren. 

Diese grundlegenden Entitäten werden in der Referenz [Entitäten in Common Data Service für Apps](reference/about-entity-reference.md) aufgeführt.

## <a name="modify-entities"></a>Ändern von Entitäten

Es gibt verschiedene Möglichkeiten, die Entitätsmetadaten zu ändern.

### <a name="use-designers"></a>Verwenden von Designern

Es gibt verschiedene Möglichkeiten, mithilfe von Designern Entitätsmetadaten zu bearbeiten.


|Designer  |Beschreibung  |
|---------|---------|
|powerapps.com|Sie können über die Website [powerapps.com](https://web.powerapps.com/) einen Common Data Service-Dienst bearbeiten, der einer Umgebung zugeordnet ist. Dies ist der einfachste und am häufigsten verwendete Ansatz. Änderungen, die hier angewendet werden, werden vor dem Hintergrund einer nicht verwalteten Common Data Service-Standardlösung vorgenommen. <!-- TODO: Add link to topic that describes this -->|
|Standardprojektmappen-Explorer für Common Data Service|Auf der Website [powerapps.com](https://web.powerapps.com/) können Sie auf einen weiteren Designer zugreifen, wenn Sie Common Data Service bearbeiten. Im unteren linken Bereich können Sie über die Schaltfläche **Erweitert** die Common Data Service-Standardprojektmappe im Projektmappen-Explorer öffnen. |
|Projektmappen-Explorer für Ihre Lösung |Wenn Sie eine Lösung verteilen möchten, sollten Sie sämtliche neue Entitäten, Attribute oder Beziehungen vor dem Hintergrund der nicht verwalteten Lösung erstellen, die Sie verwenden möchten, um Ihre Lösung zu entwickeln. <br /> Weitere Informationen finden Sie unter [Create a solution publisher and solution (Erstellen eines Lösungsherausgebers und einer Lösung)](introduction-solutions.md#create-a-solution-publisher-and-solution).|
|Im Formular-Editor|Wenn Sie ein modellgesteuertes App-Formular für eine Entität bearbeiten, können Sie auf die Schaltfläche **Neues Feld** im **Feld-Explorer** klicken. Wenn Sie ein Nachschlagefeld erstellen, erstellen Sie gleichzeitig auch eine Entitätsbeziehung, um dieses zu unterstützen.|

### <a name="import-a-solution"></a>Importieren einer Lösung

Lösungen können Entitätsmetadaten und andere benutzerdefinierte Komponenten enthalten. Wenn Sie eine verwaltete oder nicht verwaltete Lösung in ihren allgemeinen Common Data Service-Mandanten importieren, werden diese Entitäten hinzugefügt oder bereits vorhandene Entitäten um die neuen Entitätsmetadaten erweitert.

### <a name="from-a-data-source-using-power-query"></a>In einer Datenquelle unter Verwendung von Power Query

Sie können neue Entitäten erstellen und mithilfe von Power Query mit Daten auffüllen. Weitere Informationen finden Sie unter [Add data to an entity in the Common Data Service by using Power Query (Hinzufügen von Daten zu einer Entität in Common Data Service mithilfe von Power Query)](../../maker/common-data-service/data-platform-cds-newentity-pq.md).

### <a name="use-metadata-services"></a>Verwenden von Metadatendiensten

Die in Common Data Service zur Verfügung gestellten Webdienste umfassen Funktionen zum Erstellen, Lesen, Schreiben und Löschen von Entitätsmetadaten. Diese Dienste werden am häufigsten verwendet, um die Metadaten zu lesen, da diese Daten Ihrem Code zur Laufzeit mitteilen können, wie die Umgebung verändert wurde.

Weitere Informationen finden Sie unter [Metadatendienste](use-web-services.md#metadata-services)

## <a name="entity-metadata"></a>Entitätsmetadaten

Das Datenmodell wird als Metadatenelement definiert, das in Common Data Service gespeichert ist. Diese Schemadaten werden als *Entitätsmetadaten* bezeichnet. 

- Die [EntityMetadata-Klasse](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata) definiert diese Daten mithilfe des Organisationsdiensts. 
- Der [Entitätstyp EntityMetadata](/dynamics365/customer-engagement/web-api/entitymetadata) definiert diese Daten für die Web-API. 

Die Entitätsmetadaten enthalten die folgenden Informationen:


|Daten  |Beschreibung  |
|---------|---------|
|Entitätseigenschaften|Jede Entität verfügt über ca. 100 Eigenschaften, die beschreiben, wie sie jeweils ermittelt werden und wozu sie verwendet werden können.  Weitere Informationen finden Sie unter [Entitätsmetadaten](entity-metadata.md)|
|Attribute|Die Entitätseigenschaft `Attributes` ist eine Auflistung von Attributen. Jedes Attribut verfügt über ca. 50 Eigenschaften, die beschreiben, wie dieses ermittelt wird, welche Daten es enthält, wie es formatiert ist und wozu es verwendet werden kann. Weitere Informationen finden Sie unter [Attributmetadaten](entity-attribute-metadata.md).|
|Beziehungen|Bei drei der Entitätseigenschaften handelt es sich um Auflistungen von Beziehungen zwischen Entitäten. Diese Auflistungen enthalten verschiedene Beziehungstypen: n:n, n:1 und 1:n. Weitere Informationen finden Sie unter [Entity Relationships Metadata (Metadaten von Entitätsbeziehungen)](entity-relationship-metadata.md)|
|Berechtigungen|Bei einer der Entitätseigenschaften handelt es sich um eine Auflistung von bis zu acht Berechtigungen, über die die verschiedenen Datenvorgänge ermittelt werden, die für diese Entität mit einem eindeutigen Bezeichner ausgeführt werden können, der dem jeweiligen Vorgang zugeordnet ist. Dabei geht es z.B. um die folgenden Vorgänge: *Append*, *AppendTo*, *Assign*, *Create*, *Delete*, *Read*, *Share* und *Write*.|
|Schlüssel|Standardmäßig verfügt jede Entität über ein GUID-Attribut. Bei der `Keys`-Eigenschaft handelt es sich um eine leere Auflistung. Sie können alternative Schlüssel zu einer Entität hinzufügen. Weitere Informationen finden Sie unter [Entitätsschlüssel](entity-metadata.md#entity-keys).|

> [!TIP]
> Wenn Sie einen Überblick über die Entitätsmetadaten im System haben, kann Ihnen das helfen, wenn Sie verstehen möchten, wie Common Data Service funktioniert. Viele der Eigenschaften steuern auch die Funktionen von Entitäten in modellgesteuerten Apps. Die Designer, mit denen Sie Metadaten bearbeiten können, können nicht alle Informationen anzeigen, die in den Metadaten gefunden werden. Sie können eine modellgesteuerte App installieren, die als Metadata Browser bezeichnet wird und über die Sie alle ausgeblendeten Eigenschaften von Entitäten und Metadaten, die im System gefunden werden, abrufen können. Weitere Informationen finden Sie unter [Durchsuchen der Metadaten für die Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata).

### <a name="see-also"></a>Siehe auch

[Common Data Service for Apps Developer Overview (Übersicht für Entwickler: Common Data Service für Apps)](overview.md)



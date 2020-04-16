---
title: Meldungen für Entitätsbeziehungen-Metadaten (Common Data Service) | Microsoft-Dokumentation
description: In diesem Artikel sind die Meldungen aufgeführt, die Sie verwenden können, um Entitätsmetadatenbeziehungen mithilfe von Web API und Organisationservice zu erstellen, abzurufen, zu aktualisieren und zu löschen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 88ced3454045917012c3736dcc6faad5dfcdf091
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156210"
---
# <a name="entity-relationship-metadata-messages"></a>Entitätsbeziehungsmetadatennachrichten

Entitätsbeziehungen legen fest, wie Entität ist anderen Entitäten verknüpft sind. Dies umfasst auch Informationen zur Vorgehensweise, wie Beziehungen in der Anwendung angezeigt werden. Wenn außerdem Aktionen für einen Datensatz ausgeführt werden, zeigt die Beziehung an, welche Aktionen auf verknüpften Datensätze auszuführen sind.  
  
In der folgenden Tabelle sind die Meldungen aufgeführt, die Sie verwenden können, um Entitätsmetadatenbeziehungen zu erstellen, abzurufen, zu aktualisieren und zu löschen.  
  
|Web-API|Organisationsdienst|Beschreibung|  
|-------------|-------------|-----------------|  
|`POST` Anforderung für `RelationshipDefinitions` Entität. <br/>Weitere Informationen: [Erstellen einer n:n-Beziehung](webapi/create-update-entity-relationships-using-web-api.md#create-a-many-to-many-relationship). |<xref:Microsoft.Xrm.Sdk.Messages.CreateManyToManyRequest>|Erstellt eine n: n-Beziehung zwischen zwei Entitäten.|  
|`POST` Anforderung für `RelationshipDefinitions` Entität. <br/>Weitere Informationen: [Erstellen einer 1:n-Beziehung](webapi/create-update-entity-relationships-using-web-api.md#create-a-one-to-many-relationship).|<xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest>|Erstellt eine 1:n-Beziehung zwischen zwei Entitäten.|  
|`DELETE` Anforderung für `RelationshipDefinitions` Entität.<br/>Weitere Informationen: [Beziehung löschen](webapi/create-update-entity-relationships-using-web-api.md#delete-relationships)|<xref:Microsoft.Xrm.Sdk.Messages.DeleteRelationshipRequest>|Löscht eine Entitätsbeziehung.|  
|`GET` Anforderung für `RelationshipDefinitions` Entität.|<xref:Microsoft.Xrm.Sdk.Messages.RetrieveRelationshipRequest>|Ruft eine Entitätsbeziehung ab.|  
|`PUT` Anforderung für `RelationshipDefinitions` Entität.<br/>Weitere Informationen: [Beziehung aktualisieren](webapi/create-update-entity-relationships-using-web-api.md#update-relationships)|<xref:Microsoft.Xrm.Sdk.Messages.UpdateRelationshipRequest>|Aktualisiert eine Entitätsbeziehung.|  
  
### <a name="see-also"></a>Siehe auch  

 [Entitätsbeziehungseignung](entity-relationship-eligibility.md)   
 [Konfigurieren der Entitätsbeziehungen mit ableitendem Verhalten](configure-entity-relationship-cascading-behavior.md)
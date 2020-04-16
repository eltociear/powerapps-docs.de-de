---
title: Meldungen für Entitätsattributmetadaten (Common Data Service) | Microsoft-Dokumentation
description: Über die Nachrichten, die verwendet werden, um Entitätsattributmetadaten zu bearbeiten, auch als Eigenschaften oder Felder bekannt.
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
ms.openlocfilehash: 2b03cc7aa48f6f4a732e45dc0201c184baa59631
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156218"
---
# <a name="entity-attribute-metadata-messages"></a>Meldungen für Entitätsattributsmetadaten

<!-- 
Was Mike Carter
https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-attribute-metadata-messages -->

Ein Entitätsattribut ist ein Container für ein Datenelement in einer Entität. Der Begriff *Attribut* und *Eigenschaft* (Klasseneigenschaft) werden oftmals synonym für den Begriff *Entitätsattribut* verwendet. Die modellgesteuerte Anwendung verwendet den Begriff *Feld*, wenn sie auf Entitätsattribute verweist.  

> [!NOTE]
> Es ist möglich, Entitätsattribute mit der Internet-API zu erstellen und zu aktualisieren. Siehe [Erstellen von Attributen](webapi/create-update-entity-definitions-using-web-api.md#create-attributes) für weitere Informationen.

## <a name="entity-attribute-messages"></a>Meldungen für Entitätsattribute  
 In der folgenden Tabelle werden die Meldungen aufgeführt, die Sie verwenden können, um Aktionen für Entitätsattribute auszuführen.  
  
|Meldung|Web-API-Vorgang|SDK-Assembly|   
|-------------|-----------------|-----------------|  
|CreateAttribute</br></br>Erstellen von Entitätsattributen|VERÖFFENTLICHEN zu EntityMetadata-Attributsammlung-bewertete Navigationseigenschaft mit JSON-Definition des Attributs. Weitere Informationen: [Attribute erstellen](webapi/create-update-entity-definitions-using-web-api.md#create-attributes)|<xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>| 
|DeleteAttribute</br></br>Löscht Entitätsattribute.|LÖSCHEN zur URL des Attributs|<xref:Microsoft.Xrm.Sdk.Messages.DeleteAttributeRequest>|  
|DeleteOptionValue</br></br>Löscht eine Option aus den Attributen <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> oder <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata>.|<xref href="Microsoft.Dynamics.CRM.DeleteOptionValue?text=DeleteOptionValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.DeleteOptionValueRequest>|  
|InsertOptionValue</br></br>Fügt einem Attribut <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> eine Option hinzu.|<xref href="Microsoft.Dynamics.CRM.InsertOptionValue?text=InsertOptionValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.InsertOptionValueRequest>|Fügt einem Attribut <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> eine Option hinzu.|  
|InsertStatusValue</br></br>Fügt einem Attribut <xref:Microsoft.Xrm.Sdk.Metadata.StatusAttributeMetadata> eine Option hinzu.|<xref href="Microsoft.Dynamics.CRM.InsertStatusValue?text=InsertStatusValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.InsertStatusValueRequest>|  |Ändert die Reihenfolge der Optionen, die in einem Attribut <xref:Microsoft.Xrm.Sdk.Metadata.PicklistAttributeMetadata> aufgeführt sind.|<xref href="Microsoft.Dynamics.CRM.OrderOption?text=OrderOption Action" />|<xref:Microsoft.Xrm.Sdk.Messages.OrderOptionRequest>|  
|RetrieveAttribute</br></br>Ruft Entitätsattribute ab.|Verwenden Sie die Web-API-Abfrage, die beschrieben wird in [Abfragen von EntityMetadata-Attributen](webapi/query-metadata-web-api.md#bkmk_queryAttributesexample), um Entitätsattribute abzurufen.|<xref:Microsoft.Xrm.Sdk.Messages.RetrieveAttributeRequest>|  
|UpdateAttribute</br></br>Aktualisieren von Entitätsattributen|Siehe [Aktualisieren von Entitäten](webapi/create-update-entity-definitions-using-web-api.md#update-entities)|<xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest>|  
|UpdateStateValue</br></br>Aktualisiert eine Beschriftung für ein Attribut <xref:Microsoft.Xrm.Sdk.Metadata.StateAttributeMetadata> .|<xref href="Microsoft.Dynamics.CRM.UpdateStateValue?text=UpdateStateValue Action" />|<xref:Microsoft.Xrm.Sdk.Messages.UpdateStateValueRequest>|  

### <a name="see-also"></a>Siehe auch  

[Attribut-Metadaten](entity-attribute-metadata.md)<br />
[Automatisches Nummerierungsattribut erstellen](create-auto-number-attributes.md)<br />
<!-- TODO: [Work with Attributes](org-service/work-attribute-metadata.md)<br />
[Sample: Work with Attributes](org-service/sample-work-attribute-metadata.md) -->
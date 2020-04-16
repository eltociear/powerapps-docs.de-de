---
title: Konfigurieren von Entitäten und Attributen für die Überwachung (Common Data Service) | Microsoft-Dokumentation
description: Erläutert die Konfigurationsanforderungen, um die Entitäten und Attributen für die Überwachung zu aktivieren und zu deaktivieren.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3db84b0806f9fc1136e60d4b92febacc5b351df9
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156370"
---
# <a name="configure-entities-and-attributes-for-auditing"></a>Konfigurieren von Entitäten und Attributen für die Überwachung

Es gibt drei Ebenen, auf denen die Überwachung konfiguriert werden kann: Organisation, Entität und Attribut. Die Organisationsebene ist die oberste Ebene, anschließend folgt die Entitätsebene und schließlich die Attributebene. Für die Attributüberwachung muss die Überwachung auf der Attribut-, Entitäts- und Organisationsebene aktiviert werden. Für die Entitätsüberwachung muss die Überwachung auf der Entitäts- und Organisationsebene aktiviert werden.  
  
 Es gibt einen geringfügigen Unterschied im Hinblick darauf, wie die Überwachung für eine Organisation aktiviert bzw. deaktiviert wird, verglichen mit einer Entität bzw. einem Attribut. Sie aktivieren oder deaktivieren die Überwachung auf Organisationsebene, indem Sie einen bestimmten Attributwert des Organisationsdatensatzes festlegen. Für Entitäten und Attribute dagegen legen Sie einen Eigenschaftswert der Entitäts- oder Attributmetadaten fest.  
  
 Einem Benutzer muss die Rolle "Systemadministrator" oder "Systemanpasser" zugewiesen werden, um die Überwachung zu aktivieren oder zu deaktivieren.  
  
## <a name="enabling-auditing"></a>Aktivieren der Überwachung  

 Indem die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> der Metadaten einer Entität und die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.IsAuditEnabled> der Metadaten jedes gewünschten Attributs auf `true` festgelegt werden, können Datenänderungen an den Datensätzen dieser Entitäten von der Plattform protokolliert werden. Wenn Sie die Überwachung auf einer Entität aktivieren, werden jedoch standardmäßig alle Attribute der Entität für die Überwachung aktiviert. Selbstverständlich können Sie die Überwachung auf einem oder allen Attributen bei Bedarf explizit deaktivieren. Die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> kann festgelegt werden, wenn die Entitäts- oder Attributmetadaten durch die folgenden Anforderungen erstellt oder aktualisiert werden: <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>, <xref:Microsoft.Xrm.Sdk.Messages.UpdateAttributeRequest>.  
  
 Nachdem Sie die Entitäts- oder Attributmetadaten geändert haben, müssen Sie die Entität mithilfe von <xref:Microsoft.Crm.Sdk.Messages.PublishXmlRequest> veröffentlichen. Das Ändern der Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> auf der Entitätsebene erfordert keine Veröffentlichung. Normalerweise werden Anpassung und Veröffentlichung von demselben Benutzer ausgeführt. Wenn diese Aufgaben jedoch von verschiedenen Benutzern ausgeführt werden, erfasst die Überwachung die Veröffentlichungsaktion, den Benutzer, der den Veröffentlichungsvorgang initiiert hat, und nicht die Updateaktion.  
  
 Zusätzlich wird die Überprüfung auf Organisationsebene aktiviert, indem der <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled>-Attributwert des Datensatzes der Zielorganisation auf `true` festgelegt wird.  
  
## <a name="disabling-auditing"></a>Deaktivieren der Überwachung  
 Um die Überwachung zu deaktivieren, legen Sie einfach, wie zuvor beschrieben, <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> auf `false` fest. Veröffentlichen Sie die Entitätsanpassungen, wenn Sie die Überwachung auf Attributen deaktiviert haben. Sie können die Überwachung für eine ganze Organisation deaktivieren, indem Sie das Attribut <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAuditEnabled> im Datensatz der Zielorganisation auf `false` festlegen.  
  
## <a name="entities-that-can-be-audited"></a>Entitäten, die überwacht werden können  
 Alle benutzerdefinierten und die meisten anpassbaren Entitäten können überwacht werden. Eine Liste der anpassbaren Entitäten finden Sie unter [Welche Entitäten sind anpassbar?](/dynamics365/customer-engagement/developer/which-entities-are-customizable).  
  
 Die folgende Tabelle enthält die nicht-anpassbaren Entitäten, die nicht überwacht werden können. Diese Tabelle wurde durch ermittelt, indem die Metadaten jeder Entität auf einen `CanModifyAuditSettings`-Attributwert von `false` überprüft wurden.  
  
||  
|-|  
|ActivityPointer|  
|Annotation|  
|BulkOperation|  
|Kalender|  
|CalendarRule|  
|CustomerOpportunityRole|  
|Rabatt|  
|DiscountType|  
|IncidentResolution|  
|KbArticle|  
|KbArticleComment|  
|KbArticleTemplate|  
|Benachrichtigung|  
|OpportunityClose|  
|OrderClose|  
|ProductPriceLevel|  
|QuoteClose|  
|RecurrenceRule|  
|Ressource|  
|ResourceGroup|  
|ResourceGroupExpansion|  
|ResourceSpec|  
|SalesLiteratureItem|  
|SalesProcessInstance|  
|Dienst|  
|Betreff|  
|Vorlage|  
|UoM|  
|UoMSchedule|  
|Workflow|  
|WorkflowLog|  
  
### <a name="see-also"></a>Siehe auch  
 [Datenverwaltung in Dynamics 365](/dynamics365/customer-engagement/developer/manage-data)   
 [Überwachung von Entitätsdatenänderungen](/dynamics365/customer-engagement/developer/audit-entity-data-changes)   
 [Abrufen und Löschen des Verlaufs von überwachten Datenänderungen](retrieve-and-delete-the-history-of-audited-data-changes.md)   
 [Beispiel: Überwachung von Entitätsdatenänderungen](/dynamics365/customer-engagement/developer/sample-audit-entity-data-changes)   
 [Überwachung von Datenänderungen in Dynamics 365](/dynamics365/customer-engagement/developer/audit-entity-data-changes)
---
title: Entitätsbeziehungseignung (Common Data Service) | Microsoft-Dokumentation
description: In diesem Artikel werden die Meldungen aufgelistet, die Sie verwenden können, um zu bestimmen, ob Entitäten an Entitätsbeziehungen teilnehmen können.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
ms.openlocfilehash: 3d5899cebc5e52ed48e99f2ae36fcaabbd5dddc3
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748292"
---
# <a name="entity-relationship-eligibility"></a>Entitätsbeziehungseignung

Bevor Sie eine Entitätsbeziehung erstellen, müssen Sie bestätigen, ob die Entität geeignet ist, um an der Beziehung teilzunehmen. In der folgenden Tabelle werden die Meldungen aufgelistet, die Sie verwenden können, um zu bestimmen, ob Entitäten an Entitätsbeziehungen teilnehmen können.  
  
|Meldung|Web-API-Vorgang|SDK-Assembly|  
|-------------|-----------------|----------------|  
|CanBeReferenced</br>Überprüft, ob die angegebene Entität als primäre Entität (eins) in einer 1:n-Beziehung verwendet werden kann.|<xref href="Microsoft.Dynamics.CRM.CanBeReferenced?text=CanBeReferenced Action" />|<xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencedRequest>|  
|CanBeReferencing</br>Überprüft, ob die angegebene Entität als verweisende Entität (viele) in einer 1:n-Beziehung verwendet werden kann.|<xref href="Microsoft.Dynamics.CRM.CanBeReferencing?text=CanBeReferencing Action" />|<xref:Microsoft.Xrm.Sdk.Messages.CanBeReferencingRequest>|  
|CanManyToMany</br>Überprüft, ob die Entität an einer n:n-Beziehung teilnehmen kann.|<xref href="Microsoft.Dynamics.CRM.CanManyToMany?text=CanManyToMany Action" />|<xref:Microsoft.Xrm.Sdk.Messages.CanManyToManyRequest>|  
|GetValidManyToMany</br>Gibt den Satz von Entitäten zurück, die an einer n:n-Beziehung teilnehmen können.|<xref href="Microsoft.Dynamics.CRM.GetValidManyToMany?text=GetValidManyToMany Function" />|<xref:Microsoft.Xrm.Sdk.Messages.GetValidManyToManyRequest>|  
|GetValidReferencedEntities</br>Gibt den Satz von Entitäten zurück, der als die primäre Entität (eins) von der angegebenen Entität in einer 1: n-Beziehung gültig ist.|<xref href="Microsoft.Dynamics.CRM.GetValidReferencedEntities?text=GetValidReferencedEntities Function" />|<xref:Microsoft.Xrm.Sdk.Messages.GetValidReferencedEntitiesRequest>|  
|GetValidReferencingEntities</br>Gibt den Satz von Entitäten zurück, der als die verknüpfte Entität (viele) mit der angegebenen Entität in einer 1:n-Beziehung gültig ist.|<xref href="Microsoft.Dynamics.CRM.GetValidReferencingEntities?text=GetValidReferencingEntities Function" />|<xref:Microsoft.Xrm.Sdk.Messages.GetValidReferencingEntitiesRequest>|  
  
### <a name="see-also"></a>Siehe auch  
 [Anpassen von Entitätsbeziehungsmetadaten](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)   
 [Erweitern Sie das Metadatenmodell für Dynamics 365](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)   
 [Entitätsbeziehungsmetadaten](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)   
 [Entitätsbeziehungsnachrichten](entity-relationship-metadata-messages.md)   
 [Entitätenbeziehungsverhalten](/dynamics365/customer-engagement/developer/entity-relationship-behavior)   
 [Erstellen einer 1:n-Entitätsbeziehung](/dynamics365/customer-engagement/developer/org-service/create-retrieve-entity-relationships#BKMK_Create1NEntityRelationship)   
 [Erstellen einer n:n-Entitätsbeziehung](/dynamics365/customer-engagement/developer/org-service/create-retrieve-entity-relationships#BKMK_CreateNNEntityRelationship)

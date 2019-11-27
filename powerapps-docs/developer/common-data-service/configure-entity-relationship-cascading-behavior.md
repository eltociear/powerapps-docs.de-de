---
title: Konfigurieren der Entitätsbeziehungen mit kaskadierendem Verhalten (Common Data Service) | Microsoft-Dokumentation
description: Konfigurieren Sie kaskadierendes Verhalten für eine 1:n-Beziehung in Common Data Service, um die Datenintegrität zu erhalten und Geschäftsprozesse zu automatisieren.
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
ms.openlocfilehash: 6c6d37d688ad60054be4387d813dcb7d9c9305fb
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748430"
---
# <a name="configure-entity-relationship-cascading-behavior"></a>Konfigurieren der Entitätsbeziehungen mit ableitendem Verhalten  

 Konfigurieren Sie kaskadierendes Verhalten für eine 1:n-Beziehung, um die Datenintegrität zu erhalten und Geschäftsprozesse zu automatisieren. Sowohl die Web-API als auch der Organisationsdienst unterstützen die Konfiguration des kaskadierenden Verhaltens.

## <a name="using-web-api-to-configure-cascading-behavior"></a>Verwendung der Web-API zur Konfiguration des kaskadierenden Verhaltens

Bei der Verwendung von Internet API, können Sie eine 1: n-Beziehung mit <xref href="Microsoft.Dynamics.CRM.OneToManyRelationshipMetadata?text=OneToManyRelationshipMetadata EntityType" /> definieren. Die Definition enthält den Namen der zu erstellenden überschneidende Entität und wie Beziehungen in der Anwendung angezeigt werden soll, indem <xref href="Microsoft.Dynamics.CRM.AssociatedMenuConfiguration?text=AssociatedMenuConfiguration ComplexType" />, <xref href="Microsoft.Dynamics.CRM.Label?text=Label ComplexType" /> und <xref href="Microsoft.Dynamics.CRM.LocalizedLabel?text=LocalizedLabel ComplexType" /> verwendet wird. 

Weitere Informationen: [Erstellen einer 1: n-Beziehung mit Internet-API](webapi/create-update-entity-relationships-using-web-api.md#create-a-one-to-many-relationship).

## <a name="using-organization-service-to-configure-cascading-behavior"></a>Verwendung des Organisationsservice zur Konfiguration des kaskadierenden Verhaltens

Wenn Sie <xref:Microsoft.Xrm.Sdk.Messages.CreateOneToManyRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.UpdateRelationshipRequest> verwenden, fügen Sie im Textteil der Anfrage eine Instanz einer <xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata>-Klasse ein. In der <xref:Microsoft.Xrm.Sdk.Metadata.OneToManyRelationshipMetadata.CascadeConfiguration>-Eigenschaft dieser Klasse verwenden Sie die <xref:Microsoft.Xrm.Sdk.Metadata.CascadeConfiguration>-Klasse.  

Die `CascadeConfiguration` (<xref:Microsoft.Xrm.Sdk.Metadata.CascadeConfiguration>-Klasse oder <xref href="Microsoft.Dynamics.CRM.CascadeConfiguration?text=CascadeConfiguration ComplexType" />) enthält die Eigenschaften, die für Aktionen stehen, die möglicherweise in der referenzierten Entität in der 1: n-Entitätsbeziehung ausgeführt werden. Jede Eigenschaft kann einem der Werte des <xref href="Microsoft.Dynamics.CRM.CascadeType?text=CascadeType EnumType" /> zugewiesen werden.  

|Value|Anwendungsbeschriftung|Beschreibung|  
|-----------|-----------------------|-----------------|  
|Active|Aktive kaskadieren|Führen Sie die Aktion auf allen aktiven verweisenden Entitätsdatensätzen aus, die dem referenzierten Entitätsdatensatz zugeordnet sind.|  
|Kaskadieren|Alle kaskadieren|Führen Sie die Aktion auf allen verweisenden Entitätsdatensätzen aus, die dem referenzierten Entitätsdatensatz zugeordnet sind.|  
|NoCascade|Nicht kaskadieren|Keine Aktion.|  
|RemoveLink|Link entfernen|Entfernen Sie den Wert des referenzierenden Attributs für alle referenzierenden Entitätsdatensätze, die dem referenzierten Datensatz zugeordnet sind.|  
|Einschränken|Einschränken|Verhindern, dass der referenzierte Entitätsdatensatz gelöscht wird, wenn referenzierte Entitäten vorhanden sind.|  
|UserOwned|Benutzereigene kaskadieren|Durchführen der Aktion für alle referenzierten Entitätsdatensätze, deren Besitzer mit dem des referenzierten Entitätsdatensatzes identisch ist.|  
  
 Die `CascadeConfiguration` (<xref:Microsoft.Xrm.Sdk.Metadata.CascadeConfiguration>-Klasse oder <xref href="Microsoft.Dynamics.CRM.CascadeConfiguration?text=CascadeConfiguration ComplexType" />) enthält die folgenden Eigenschaften, die für Aktionen stehen, die möglicherweise in der referenzierten Entität in der 1: n-Entitätsbeziehung ausgeführt werden.  
  
|Aktion|Beschreibung|Gültige Optionen|  
|------------|-----------------|-------------------|  
|Zuweisen|Der referenzierte Entitätsdatensatzbesitzer wurde geändert.|Active<br />Kaskadieren<br />NoCascade<br />UserOwned|  
|Löschen|Der referenzierte Entitätsdatensatz wurde gelöscht. **Hinweis:** Die Optionen für diese Aktion sind begrenzt.|Kaskadieren<br />RemoveLink<br />Einschränken|  
|Zusammenführen|Der Datensatz wurde bereits mit einem anderen Datensatz zusammengeführt. **Hinweis:** Für referenzierte Entitäten, die zusammengeführt werden können, ist Kaskadierung die einzige gültige Option. Verwenden Sie in anderen Fällen NoCascade.|Kaskadieren<br />NoCascade|  
|Erneut überordnen|Siehe [Informationen zur erneut übergeordneten Aktion](#about-the-reparent-action) weiter unten.|Active<br />Kaskadieren<br />NoCascade<br />UserOwned|  
|Freigeben|Wenn der referenzierte Entitätsdatensatz für einen anderen Benutzer freigegeben wird.|Active<br />Kaskadieren<br />NoCascade<br />UserOwned|  
|Freigabe aufheben|Wenn das Freigeben für den referenzierten Entitätsdatensatz entfernt wird.|Active<br />Kaskadieren<br />NoCascade<br />UserOwned|  
  
<a name="BKMK_ReparentAction"></a>   
### <a name="about-the-reparent-action"></a>Informationen zur erneut übergeordneten Aktion  
 Die erneut übergeordnete Aktion ist der Freigabenaktion sehr ähnlich, außer dass sie mit den geerbten Lesezugriffsauskunftsrechten anstelle der expliziten Lesezugriffsauskunftsrechte arbeitet. Die Aktion zur erneuten Überordnen geschieht, wenn der Wert des Referenzattributs in einer übergeordneten Beziehung geändert wird. Wenn eine reparent-Aktion auftritt, ändert sich möglicherweise der gewünschte Bereich der geerbten Lesezugriffsauskunftsrechte für verknüpfte Entitäten. Die cascade-Aktionen, die mit der reparent-Aktion verknüpft sind, verweisen auf Änderungen der Lesezugriffsauskunftsrechte bei Entitätsdatensätzen und allem verknüpften Entitätsdatensätzen.  

### <a name="see-also"></a>Siehe auch

[Entitätsbeziehung von Metadaten](entity-relationship-metadata.md)  


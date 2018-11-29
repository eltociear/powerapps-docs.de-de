---
title: SLAs für Entitäten übernehmen (Common Data Service for Apps) | Microsoft Docs
description: 'Erfahren Sie über das Übernehmen von SLAs für die benutzerdefinierten Entitäten, wenn Sie die Entitäten zum Übernehmen von Vereinbarungen zum Servicelevel (SLAs) aktivieren. Also können Sie auch SLA-KPIs erstellen.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="apply-slas-to-entities"></a>SLAs für Entitäten übernehmen

Vereinbarungen zum Service Level (SLAs) in Common Data Service for Apps helfen Ihnen festzulegen, welchen Service- oder Supportlevel Ihre Organisation einem Kunden anbietet, indem Elemente zum Definieren von Metriken oder Key Performance Indicators (KPI) eingeschlossen werden, damit der Servicelevel erreicht wird. Sie können SLAs auf benutzerdefinierte Entitäten und die folgenden Systementitäten anwenden:  
  
-   Alle Aktivitätsentitäten (wie E-Mail, Aufgabe und Termine) außer Serienterminen (RecurringAppointmentMaster)  
  
-   Konto  
  
-   Kontakt  
  
-   Rechnung  
  
-   Vorfall (Fallstudie)  
  
-   Verkaufschance  
  
-   Angebot  
  
-   Lead  
  
-   SalesOrder (Auftrag)  
  
<a name="EnableSLAs"></a> 
  
## <a name="enable-entities-for-applying-slas"></a>Aktivieren von Entitäten für das Anwenden von SLAs  

 Um SLAs auf eine Entität anzuwenden, müssen Sie das Attribut <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsSLAEnabled> auf true für die Entität setzen. Sie können diese Einstellung nicht ändern, nachdem sie ermöglicht worden ist. Standardmäßig ist die `Incident`-Entität für SLAs aktiviert.  
  
 Sie können auch das Anpassungstool zum Aktivieren von Entitäten für SLAs verwenden. Für weitere Informationen, siehe [Entitäten für Vereinbarungen zum Servicelevel aktivieren](/dynamics365/customer-engagement/customer-service/enable-entities-service-level-agreements).  
  
 Nachdem Sie eine Entität für SLAs aktiviert haben, werden neue SLA-bezogene Attribute wie `SLAId` und `SLAInvokedId` automatisch zur Entität hinzugefügt.  
  
<a name="CreateSLAKPI"></a>   

## <a name="create-sla-kpis"></a>Erstellen von SLA KPIs  

 Um programmatisch SLA KPIs für eine Entität zu schaffen, erstellen Sie ein Suchattribut auf einer SLA-aktivierten Entität und richten Sie dann eine Beziehung zwischen dem Attribut und der `SLAKPIInstance`-Entität ein.  
  
<a name="ApplySLA"></a>
   
## <a name="apply-slas-to-entity-records"></a>Anwenden von SLAs auf Entitätsdatensätze  

 Unter Verwendung des CDS for Apps-Webclients können Sie SLAs für eine SLA-aktivierte Entität erstellen und ein SLA als Standard für die Entität festlegen, sodass diese automatisch auf alle neuen Entitätsdatensätze angewendet wird.  
  
 Wenn Sie jedoch manuell SLAs auf Entitätsdatensätze basierend auf benutzerdefinierten Geschäftsanforderungen anwenden möchten, können Sie den Entitätsdatensatz programmgesteuert so aktualisieren, dass er den `SLAId`-Attributwert auf den gewünschten aktiven SLA-Datensatz setzt.  
  
<a name="Limitations"></a>   

## <a name="limitations-to-applying-slas-in-dynamics-365-online"></a>Beschränkungen beim Anwenden von SLAs in Dynamics 365 (online)  

 In CDS for Apps gelten die folgenden Beschränkungen für SLAs per CDS for Apps-Instanz (Organisation):  
  
-   Sie können ein Maximum von 7 Entitäten haben, die aktive SLAs haben. Es kommt zu einem Fehler beim Aktivieren einer SLA, wenn die Begrenzung überschritten wird.  
  
-   Sie können ein Maximum von 5 SLA KPIs pro Entität für aktive SLAs haben. Es kommt zu einem Fehler beim Aktivieren einer SLA, wenn die Begrenzung überschritten wird. Diese Beschränkung gilt nicht für die `Incident`-Entität.  
  
### <a name="see-also"></a>Siehe auch  
 [Serviceentitäten in Customer Engagement](/dynamics365/customer-engagement/developer/service-entities)   
 [Erweiterte Vereinbarungen zum Service Level (SLAs)](/dynamics365/customer-engagement/admin/enhanced-service-level-agreements)
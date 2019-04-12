---
title: Verknüpfen Sie Attribute für benutzerdefinierte Serienterminmaster- und Terminentitäten (Common Data Service) | Microsoft Docs
description: 'Verknüpfen benutzerdefinierter Attribute der RecurringAppointmentMaster-Entität mit benutzerdefinierten Attributen der Terminentität, um Daten automatisch zu kopieren.'
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
---
# <a name="link-custom-attributes-of-the-recurring-appointment-master-and-appointment-entities"></a>Verknüpfen von benutzerdefinierten Attributen für Serienterminmaster- und Termin-Entitäten

Sie können die benutzerdefinierten Attribute, die für die `RecurringAppointmentMaster`-Entität erstellt wurden, mit den benutzerdefinierten Attributen verknüpfen, die für die `Appointment`-Entität erstellt wurden, um jedesmal automatisch die Daten vom benutzerdefinierten Serienterminmaster-Attribut zu den verknüpften benutzerdefinierten Serientermininstanzen zu kopieren, wenn es erweitert wird.  
  
 Es besteht eine 1:1-Zuordnung zwischen den benutzerdefinierten Attributen, was impliziert, dass ein benutzerdefiniertes Attribut der Serienterminmasterentität nur mit einem benutzerdefinierten Attribut in der Entität für Termine zugeordnet werden kann. Darüber hinaus müssen die benutzerdefinierten Attribute, die zusammen verknüpft werden sollen, vom gleichen Typ sein. Beispielsweise kann ein benutzerdefiniertes Attribut vom Typ `decimal` nicht mit einem benutzerdefinierten Attribut `string` verknüpft werden. Weitere Informationen zu den unterschiedlichen Typen von Attributen, siehe [Anpassen von Entitätsattributmetadaten](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata).  
  
> [!NOTE]
>  Sie können die benutzerdefinierten Attribute nicht verknüpfen, für die *die Sicherheit auf Feldebene* aktiviert ist. Ebenso können Sie nicht Sicherheit auf Feldebene für verknüpfte benutzerdefinierte Attribute aktivieren.  
  
### <a name="link-custom-attributes"></a>Benutzerdefinierte Attribute verknüpfen  
  
1. Erstellen Sie ein benutzerdefiniertes Attribut für die Termine-Entität, indem Sie die <xref:Microsoft.Xrm.Sdk.Messages.CreateAttributeRequest>-Klasse verwenden.  
  
2. Erstellen Sie ein benutzerdefiniertes Attribut für die Entität Termin (Serienterminmaster). Beim Angeben der Attributmetadaten für das benutzerdefinierte Attribut, verwenden Sie <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata><xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LinkedAttributeId> Eigenschaft, um benutzerdefinierte Attributs zu verknüpfen, die Sie in Schritt 1 erstellten.  
  
3. Veröffentlichen Sie die Änderungen an der Lösung.  
  
   Für Beispielcode, siehe [Beispiel: Verknüpfen von benutzerdefinierten Attributen zwischen Reihen und Instanzen](org-service/samples/link-custom-attributes-between-series-instances.md).  
  
### <a name="see-also"></a>Siehe auch

 [Serientermin-Entitäten](/dynamics365/customer-engagement/developer/recurring-appointment-entities)   
 [RecurringAppointmentMaster-Entität](/reference/entities/recurringappointmentmaster.md)   
 [Beispiel: Verknüpfen von benutzerdefinierten Attributen zwischen Reihen und Instanzen](org-service/samples/link-custom-attributes-between-series-instances.md)   
 [Anpassen von Entitätsattributmetadaten](/dynamics365/customer-engagement/developer/customize-entity-attribute-metadata)

---
title: Field-Sicherheitsentitäten (Common Data Service für Apps) | Microsoft Docs
description: 'Infos zum Verwenden von Feldsicherheitsentitäten, um Sicherheit auf Feldebene anzuwenden, was den Feldzugriff auf angegebene Benutzer und Teams beschränkt.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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
---
# <a name="field-security-entities"></a>Feldsicherheitsentitäten

Sie verwenden Feldsicherheitsentitäten, um Sicherheit auf Feldebene anzuwenden, was den Feldzugriff auf angegebene Benutzer und Teams beschränkt. Der Umfang der Sicherheit auf Feldebene ist global, was bedeutet, dass sie für alle Datensätze innerhalb der Organisationen gilt, unabhängig von der Hierarchieebene der Unternehmenseinheit, zu der der Datensatz oder Benutzer gehört. Die Field-Sicherheit arbeitet in allen Common Data Service für Apps Clients, also auch für den Webclient Dynamics 365 for Outlook und Dynamics. Sie gilt für alle Komponenten, also für CDS für Apps Web-Services,, Berichte, Suche, Offlinekomponente, gefilterte Ansichten, Überwachung und Duplikaterkennung. Für diese Version kann die Feldsicherheit sowohl für benutzerdefinierten Felder als auch viele vordefinierte (OOB)- Felder angewendet werden.  
  
 Weitere Informationen, wie gesicherte Felder das Verhalten von Methoden ändern, siehe [Wie Feldsicherheit verwendet werden kann, um Zugriff auf Feldwerte in Dynamics 365 zu steuern](/dynamics365/customer-engagement/developer/security-dev/use-field-security-control-access-field-values).  
  
> [!IMPORTANT]
>  Profile für Sicherheit auf Feldebene hindern Benutzer daran, Zugriff auf CDS für Apps-Daten anhand der Profildefinitionen zu erlangen. Wenn die SQL-Server-ACLs falsch konfiguriert sind oder wenn es ein SQL-Einschleusungsproblem gibt, können Unbefugte direkten Zugriff auf Daten in  erhalten und auf diese Weise die Beschränkungen der Sicherheit auf Feldebene umgehen. Weitere Informationen finden Sie unter [Übersicht über Webanwendungs-Sicherheitsbedrohungen](https://msdn.microsoft.com/library/f13d73y6.aspx).  
  
<a name="bkmk_setup"></a>   

## <a name="set-up-and-use-field-security"></a>Einrichten und Verwenden von Feldsicherheit  
 Um die Feldsicherheit zu verwenden, müssen Sie folgendermaßen vorgehen:  
  
1. Erstellen Sie einen Feldsicherheitsprofil-Datensatz.  
  
2. Fügen Sie dem Profil Benutzer oder Teams hinzu.  
  
3. Ein Attribut suchen, das auf Feldebene gesichert werden kann  
  
4. Sichern Sie das Attribut, wenn Sie das Attribut erstellen, oder durch Aktualisieren der Attributmetadaten.  
  
5. Veröffentlichen Sie die Attributanpassungen.  
  
6. Erstellen Sie einen Feldberechtigungsdatensatz, der definiert, welchen Zugriff (Erstellen, Aktualisieren, Lesen) das Profil für das benutzerdefinierte Attribut erhält.  
  
   Beispielcode dazu, wie diese Schritte ausgeführt werden, finden Sie unter [Beispiel: Aktivieren der Feldsicherheit für eine Entität](/dynamics365/customer-engagement/developer/sample-enable-field-security-entity).  
  
   Verwenden Sie die folgenden Feldberechtigungsattribute, um festzulegen, dass das angegebene Feldsicherheitsprofil ein Attribut erstellen, lesen oder aktualisieren kann. 
   Sie können den Wert für diese Attribute vergleichen oder festlegen, indem Sie den globalen Optionssatz `field_security_permission_type` verwenden:  
  
-   `FieldPermission`.`CanCreate`  
  
-   `FieldPermission`.`CanRead`  
  
-   `FieldPermission`.`CanUpdate`  
  
> [!IMPORTANT]
>  Wenn Benutzer mit wenigen Rechten Lesezugriff auf die Entität des Feldsicherheitsprofils erhalten, können sie sehen, welche Profile andere Benutzer haben und andere Benutzer mit Zugriff auf sichere Attribute finden, an denen sie interessiert sind. Sie können dann Social Engineering-Techniken verwenden, damit ihnen ein Profil mit Zugriff auf diese sicheren Attribute zugewiesen wird.  
  
<a name="bkmk_whichattributes"></a>   

## <a name="which-attributes-can-be-secured"></a>Welche Attribute können gesichert werden?  
 Um festzustellen, welche Attribute gesichert werden können, können Sie für die folgenden Entitätsmetadaten Eigenschaften abfragen:  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanBeSecuredForCreate>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanBeSecuredForRead>  
  
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.CanBeSecuredForUpdate>  
  
  Es gibt einige zusätzliche Regeln, die für bestimmte Attributdatentypen gelten:  
  
- Die booleschen Attribute können zum Erstellungs- und Aktualisierungsvorgänge gesichert werden, aber nicht für Lesen.  
  
- Optionssatzattribute können für Erstellen, Aktualisieren und Lesen gesichert werden, wenn ein Standardwert nicht angegeben ist.  
  
  Es gibt tausenden von Attributen, die gesichert werden können, daher gibt es zwei einfachere Möglichkeiten, nach diesen Informationen zu suchen. Zum Anzeigen der Entitätsmetadaten für Ihre Organisation installieren Sie die Metadatenbrowserlösung, die in [Durchsuchen der Metadaten für Ihre Organisation](/dynamics365/customer-engagement/developer/browse-your-metadata) beschrieben ist. Sie können die Referenzdokumentation für Entitäten auch in der [Entitätsreferenz](/dynamics365/customer-engagement/developer/about-entity-reference) durchsuchen.  
  
<a name="bkmk_sharing"></a>   
## <a name="share-secured-fields"></a>Gesicherte Felder freigeben  
 Sie können sichere Felder genau wie Datensätze freigeben. Dazu müssen Sie einen `PrincipalObjectAttributeAccess`-Datensatz (Feldfreigabe) erstellen, löschen oder aktualisieren, in dem Sie den Benutzer oder das Team, die Entität und Berechtigungen angeben.  
  
 In der folgenden Tabelle werden die entsprechenden Methoden zum Sichern eines Felds im Vergleich zum Sichern eines Datensatzes aufgelistet.  
  
|Freigeben von Datensätzen|Freigegeben des Feldzugriffs|  
|--------------------|--------------------------|  
|Verwenden Sie <xref:Microsoft.Crm.Sdk.Messages.GrantAccessRequest>-Meldung, um einem Benutzer oder Team Datensatzzugriff zu gewähren.|Mithilfe der <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> Nachricht oder der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> Methode, um gesicherten Feldzugriff für einen Benutzer oder ein Team zu geben.|  
|Verwenden Sie <xref:Microsoft.Crm.Sdk.Messages.ModifyAccessRequest>-Meldung, um Datensatzzugriff für einen Benutzer oder Team zu aktualisieren.|Mithilfe der <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> Nachricht oder der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> Methode, um gesicherten Feldzugriff für einen Benutzer oder ein Team zu aktualisieren.|  
|Verwenden Sie <xref:Microsoft.Crm.Sdk.Messages.RevokeAccessRequest>-Meldung, um Datensatzzugriff für einen Benutzer oder Team zu entfernen.|Mithilfe der <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> Nachricht oder der <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> Methode, um gesicherten Feldzugriff für einen Benutzer oder ein Team zu entfernen.|  
  
### <a name="see-also"></a>Siehe auch  
 [Das Dynamics 365-Sicherheitsmodell](security-model.md)   
 [Verwaltungs- und Sicherheitsentitäten](/dynamics365/customer-engagement/developer/administration-security-entities)   
 [FieldSecurityProfile-Entität](/reference/entities/fieldsecurityprofile.md)   
 [Entitätsberechtigung-Entität](/reference/entities/fieldpermission.md)   
 [PrincipalObjectAttributeAccess-Entität](/reference/entities/principalobjectattributeaccess.md)    
 [Beispiel: Abrufen von Feldberechtigungen](/dynamics365/customer-engagement/developer/sample-retrieve-field-permissions)   
 [Beispiel: Aktivierung der Feldsicherheit für eine Entität](org-service/samples/enable-field-security-entity.md)   
 [Beispiel: Abrufen von Feldfreigabedatensätzen](/dynamics365/customer-engagement/developer/sample-retrieve-field-sharing-records)

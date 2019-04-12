---
title: Aktivieren und deaktivieren von Duplikaterkennung (Common Data Service) | Microsoft Docs
description: 'Dieses Thema enthält Informationen dazu, wie Sie die Duplikaterkennung für alle Entitäten in einer Organisation, für eine bestimmte Entität oder für Einzelgeschäfte aktivieren und wie Sie diese global oder für einen Entitätstyp deaktivieren, indem die Veröffentlichung der Duplikaterkennungsregeln rückgängig gemacht wird oder indem die veröffentlichten Regeln gelöscht werden.'
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
# <a name="enable-and-disable-duplicate-detection"></a>Aktivieren und Deaktivieren der Duplikaterkennung

Dieses Thema enthält Informationen dazu, wie Sie die Duplikaterkennung in Dynamics 365 aktivieren und deaktivieren.

<a name="bkmk_enable"></a>

## <a name="enable-duplicate-detection"></a>Aktivieren der Duplikaterkennung

Vor der Ausführung der Duplikaterkennung müssen Sie diese für jede der folgenden Aufgaben aktivieren:  
  
-   global (für alle Entitäten in der Organisation)  
  
-   für eine Entität  
  
-   für bestimmte Vorgänge  
  
> [!NOTE]
>  Sie müssen die Duplikaterkennung in allen drei Bereichen aktivieren, um Duplikate für eine Entität sowie für Vorgänge auf einer Entität zu erkennen.  
  
### <a name="enable-duplicate-detection-globally"></a>Globales Aktivieren der Duplikaterkennung  
  
-   Verwenden Sie die Meldung <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>, um das Attribut `Organization.IsDuplicateDetectionEnabled` auf den Wert `true` zu setzen.
-   Lesen Sie [Aktivierung von Duplikaterkennungsregeln ein- oder ausschalten für die gesamte Organisation](/dynamics365/customer-engagement/admin/turn-duplicate-detection-rules-off-whole-organization), um festzustellen, wie Sie die Benutzeroberfläche verwenden können, um die Duplikaterkennung für die gesamte Organisation zu aktivieren.
  
### <a name="enable-duplicate-detection-for-an-entity"></a>Aktivieren der Duplikaterkennung für eine Entität  
  
-   Verwenden Sie die Meldung <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>, um die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsDuplicateDetectionEnabled> auf `true` festzulegen.  
  
### <a name="enable-duplicate-detection-for-specific-operations"></a>Aktivieren der Duplikaterkennung für bestimmte Operationen  
  
- Setzen Sie die folgenden Attribute auf `true`:  
  
  - `Organization.IsDuplicateDetectionEnabledForOnlineCreateUpdate`. Erstellen oder Aktualisieren von Datensätzen in den Common Data Service mithilfe der Webanwendung oder von Dynamics 365 for Outlook. Dieses Attribut aktiviert bzw. deaktiviert die Duplikaterkennung für Datensätze, die mit dem Parameter <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> und der Nachricht <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> erstellt oder aktualisiert wurden. Dies hat jedoch keine Auswirkungen auf Datensätze, die mithilfe der Methoden <xref:Microsoft.Xrm.Sdk.IOrganizationService>. und <xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*> erstellt oder aktualisiert wurden. und <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> Methoden.  
  
  - `Organization.IsDuplicateDetectionEnabledForOfflineSync`. Synchronisieren Sie Offline-Datensätzen, wenn Dynamics 365 for Outlook vom Offlinemodus in den Onlinemodus wechselt.  
  
  - `Organization.IsDuplicateDetectionEnabledForImport`. Importierten Sie Massendaten.  
  
  > [!NOTE]
  >  Sie müssen die Duplikaterkennungsregeln nicht veröffentlichen, um die Duplikaterkennung für diese Vorgänge zu aktivieren. Sie müssen die Duplikaterkennungsregeln jedoch veröffentlichen, bevor Sie die Vorgänge ausführen.  

<a name="bkmk_disable"></a>

## <a name="disable-duplicate-detection"></a>Deaktivieren der Duplikaterkennung

Deaktivieren Sie die Duplikaterkennung global oder für einen Entitätstyp, indem Sie die Veröffentlichung der Duplikaterkennungsregeln aufheben oder indem Sie die veröffentlichten Regeln löschen.  
  
 **Globales Deaktivieren der Duplikaterkennung**  
  
 Zum globalen Deaktivieren der Duplikaterkennung verwenden Sie die Meldung `Organization.IsDuplicateDetectionEnabled` <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>, um das Attribut auf `false` festzulegen. Dadurch wird automatisch die Veröffentlichung aller Duplikaterkennungsregeln für alle Entitätstypen in der Organisation aufgehoben.  
  
 **Deaktivieren der Duplikaterkennung für eine Entität**  
  
 Um die Duplikaterkennung für einen Entitätstyp zu deaktivieren, führen Sie einen der folgenden Schritte aus:  
  
-   Verwenden Sie die Meldung <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest>, um die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsDuplicateDetectionEnabled> auf `false` festzulegen. Dadurch wird automatisch die Veröffentlichung aller Duplikaterkennungsregeln für einen Entitätstyp aufgehoben. Die Unterstützung der Duplikaterkennung für den Entitätstyp wird entfernt, und Sie können keine neue Duplikaterkennungsregel für diesen Entitätstyp erstellen.  
  
-   Heben Sie die Veröffentlichung aller Duplikaterkennungsregeln für einen Entitätstyp auf, indem Sie die Meldung <xref:Microsoft.Crm.Sdk.Messages.UnpublishDuplicateRuleRequest> verwenden.  
  
**Löschen von veröffentlichten Duplikaterkennungsregeln**  
  
Löschen Sie alle veröffentlichten Regeln im System, um die Duplikaterkennung global zu deaktivieren, oder löschen Sie veröffentlichte Regeln für bestimmte Entitätstypen, indem Sie die Methode <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*> verwenden. Methode.  

## <a name="see-also"></a>Siehe auch

[Duplikaterkennung](detect-duplicate-data-with-code.md)  
[Duplikaterkennung ausführen](run-duplicate-detection.md)   
[Duplikatregelentitäten](duplicaterule-entities.md) 
---
title: Benutzerdefinierte Aktivitäten (Common Data Service für Apps) | Microsoft Docs
description: 'Benutzerdefinierte Aktivitäten unterstützen den Kommunikationsbedarf eines modernen Unternehmens, wie z. B. Instant Messaging (IM) in Dynamics 365.'
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
# <a name="custom-activities"></a>Benutzerdefinierte Aktivitäten

In Common Data Service for Apps können Sie benutzerdefinierte Aktivitäten erstellen, um den Kommunikationsbedarf eines modernen Unternehmens zu unterstützen, wie z. B. Instant Messaging (IM) und Short Message Service (SMS). Um eine benutzerdefinierte Aktivität in CDs for Apps zu erstellen, erstellen Sie eine benutzerdefinierte Entität, und legen diese als Aktivitätsentität mithilfe der <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsActivity> fest. -Eigenschaft verfügbar.  
  
 Im Unterschied zu anderen benutzerdefinierten Entitäten können Sie jedoch kein primäres Attribut für eine benutzerdefinierte Aktivität angeben, da standardmäßig jede benutzerdefinierte Aktivität über ein primäres Attribut mit dem Namen "Betreff" verfügen muss.  
  
 Wenn Sie eine benutzdefinierte Aktivitätsentität erstellen, werden alle Rechte der `activitypointer`-Entität von der benutzerdefinierten Aktivität vererbt. Außerdem werden alle Aktivitätsparteitypen für die benutzerdefinierte Aktivität verfügbar, und als Ergebnis werden auch die entsprechenden Eigenschaften vererbt.  
  
 1:n-Beziehungen für eine benutzerdefinierte Aktivität können auf die gleiche Weise erstellt werden wie bei anderen Aktivitäten, und auch vorhandene Beziehungen können aktualisiert werden.  
  
## <a name="privileges-and-access-rights"></a>Rechte und Zugriffsrechte 
 
 Sie benötigen denselben Satz von CDs for Apps-Rechten und -Zugriffsrechten , um benutzerdefinierten Aktivitäten zu verwenden wie die, die nötig sind, um benutzerdefinierte Entitäten zu verwenden. Weitere Informationen zum Erstellen benutzerdefinierter Entitäten siehe [Anpassen von Entitätsmetadaten](customize-entity-metadata.md).  
  
## <a name="creating-a-custom-activity"></a>Erstellen einer benutzerdefinierten Aktivität  
 Um eine beutzerdefinierte Aktivitätsentität zu erstellen, legen Sie die Werte der Eigenschaften fest, die in der folgenden Tabelle aufgeführt sind.  
  
|Eigenschaftenname|Wert|Notizen|  
|-------------------|-----------|-----------|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsActivity>|`true`|Geben Sie die benutzerdefinierte Entität als Aktivitätsentität an.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAvailableOffline>|`true`|Eine benutzerdefinierte Aktivitätsentität muss eine Offlineverfügbarkeit besitzen.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsMailMergeEnabled>|`false`|Für eine benutzerdefinierte Aktivitätsentität kann Seriendruck nicht aktiviert werden.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.OwnershipType>|<xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>. TeamOwned<br />oder<br /><xref:Microsoft.Xrm.Sdk.Metadata.OwnershipTypes>. UserOwned|Eine benutzerdefinierte Entität kann sich entweder im Besitz Teams oder eines Benutzers befinden.|  
|<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ActivityTypeMask>|0 - Keine<br />oder<br />1 – Kommunikationsaktivitäten|(Optional) Geben Sie an, dass eine benutzerdefinierte Aktivität während der Aktivitätsmenüs in der Webanwendung angezeigt werden soll.<br /><br /> -   Geben Sie **0 (None)** an, um sie in den Aktivitätsmenüs auszublenden. Die benutzerdefinierte Aktivität wird in den zugeordneten Rastern nur derjenigen Entitäten angezeigt, denen sie zugeordnet ist (Beziehung enthält).<br />-   Geben Sie **1 (Kommunikations-Aktivität)** an, um sie in den Aktivitätsmenüs anzuzeigen.<br /><br /> Wenn Sie nicht diese Eigenschaft nicht angeben, wird die benutzerdefinierte Aktivität mit dem Standard-Eigenschaftswert erstellt: 1. Das bedeutet, dass die benutzerdefinierte Aktivität in den Aktivitätsmenüs verfügbar ist. Außerdem kann `ActivityTypeMask` nur während der Aktivitätserstellung festgelegt werden, und kann nach Festlegung nicht mehr geändert werden.|  
|<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasActivities>|`false`|Eine benutzerdefinierte Aktivitätsentität darf keine Beziehung zu Aktivitäten haben.|  
|<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>.<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.HasNotes>|`true`|Eine benutzerdefinierte Aktivitätsentität muss Beziehung zu Hinweisen haben.|  
|<xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest>. <xref:Microsoft.Xrm.Sdk.Messages.CreateEntityRequest.PrimaryAttribute>|<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName> ist “Betreff”.|Der Schemaname des `PrimaryAttribute` muss für alle Aktivitäten “Betreff” sein.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie eine benutzerdefinierte Aktivität erstellen können.  
  
```csharp
String prefix = "new_";

String customEntityName = prefix + "instantmessage";

// Create the custom activity entity.
CreateEntityRequest request = new CreateEntityRequest
{
    HasNotes = true,
    HasActivities = false,
    PrimaryAttribute = new StringAttributeMetadata
    {
        SchemaName = "Subject",
        RequiredLevel = new AttributeRequiredLevelManagedProperty(AttributeRequiredLevel.None),
        MaxLength = 100,
        DisplayName = new Label("Subject", 1033)
    },
    Entity = new EntityMetadata
    {
        IsActivity = true,
        SchemaName = customEntityName,
        DisplayName = new Label("Instant Message", 1033),
        DisplayCollectionName = new Label("Instant Messages", 1033),
        OwnershipType = OwnershipTypes.UserOwned,
        IsAvailableOffline = true,

    }
};

_serviceProxy.Execute(request);

//Entity must be published
``` 

### <a name="see-also"></a>Siehe auch  
 [Aktivitätsentitäten](activity-entities.md)   
 [ActivityPointer (Aktivität) Entität](activitypointer-activity-entity.md)   
 [Beispiel: Erstellen einer benutzerdefinierten Aktivität](/dynamics365/customer-engagement/developer/sample-create-custom-activity)   
 [Beispiel: Erstellen und Aktualisieren von Entitäts-Metadaten](/dynamics365/customer-engagement/developer/org-service/sample-create-update-entity-metadata)
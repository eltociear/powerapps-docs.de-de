---
title: 'Abrufen, aktualisieren und Löschen von Entitäten (Common Data Service) | Microsoft Docs'
description: <Description>
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="retrieve-update-and-delete-entities"></a>Abrufen, Aktualisieren und Löschen von Entitäten

In diesem Thema wird gezeigt, wie Sie eine Entität abrufen, aktualisieren und löschen, indem Sie die benutzerdefinierte `Bank Account`-Entität verwenden, die in [Erstellen einer benutzerdefinierten Entität](create-custom-entity.md) erstellt wurde.  
  
<a name="BKMK_RetrieveAndUpdateEntity"></a>  
 
## <a name="retrieve-and-update-an-entity"></a>Abrufen und Aktualisieren einer Entität  

 Im folgenden Beispiel wird eine Entität mithilfe der Meldung <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityRequest> abgerufen. Sie aktualisiert dann die Entität zum Deaktivieren des Seriendrucks, indem die Eigenschaft <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsMailMergeEnabled> auf `false` festgelegt wird, und legt <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest.HasNotes> auf `true` in der <xref:Microsoft.Xrm.Sdk.Messages.UpdateEntityRequest> fest, um anzugeben, dass die Entität eine Beziehung zu der Entität `Annotation` enthalten sollte, damit die Entität Notizen anzeigen kann.  
  
```csharp

RetrieveEntityRequest retrieveBankAccountEntityRequest = new RetrieveEntityRequest
{
 EntityFilters = EntityFilters.Entity,
 LogicalName = _customEntityName
};
RetrieveEntityResponse retrieveBankAccountEntityResponse = (RetrieveEntityResponse)_serviceProxy.Execute(retrieveBankAccountEntityRequest);
EntityMetadata BankAccountEntity = retrieveBankAccountEntityResponse.EntityMetadata;

// Disable Mail merge
BankAccountEntity.IsMailMergeEnabled = new BooleanManagedProperty(false);
// Enable Notes
UpdateEntityRequest updateBankAccountRequest = new UpdateEntityRequest
{
 Entity = BankAccountEntity,
 HasNotes = true
};



_serviceProxy.Execute(updateBankAccountRequest);
```
  
<a name="BKMK_DeleteCustomEntity"></a>   

## <a name="delete-a-custom-entity"></a>Löschen einer benutzerdefinierten Entität  

Das folgende Beispiel verwendet die Meldung <xref:Microsoft.Xrm.Sdk.Messages.DeleteEntityRequest>, um die Entität mit dem logischen Namen, der durch die Variable `_customEntityName` angegeben wird, zu löschen.  
  
```csharp

DeleteEntityRequest request = new DeleteEntityRequest()
{
 LogicalName = _customEntityName,
};
_serviceProxy.Execute(request);
```
  
### <a name="see-also"></a>Siehe auch  
 [Verwenden Sie den IOrganizationService und Helper Code](/dynamics365/customer-engagement/developer/use-sample-helper-code)   
 [Anpassen von Entitätsmetadaten](../customize-entity-metadata.md)   
 [Entität, die per E-Mail gesendet werden kann, erstellen und aktualisieren](/dynamics365/customer-engagement/developer/create-update-entity-emailed)   
 [Erstellen einer benutzerdefinierten Entität.](create-custom-entity.md)
---
title: Entitäten zuordnen und ihre Zuordnung aufheben mithilfe des Organisationsdienstes (Common Data Service) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe des Organisations-Service Entitäten zuordnen und trennen
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
ms.openlocfilehash: 05a61e984f06bf5b2d6f93637799ce97951fa592
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748401"
---
# <a name="associate-and-disassociate-entities-using-the-organization-service"></a>Entitäten mithilfe des Organisations-Service zuordnen oder trennen

Entitätsdatensätze werden miteinander mit Suchattributen für die verknüpfte Entität zugeordnet. Die einfachste Methode, zwei Entitätsdatensätze in einer 1: n-Beziehung zuzuordnen ist es, <xref:Microsoft.Xrm.Sdk.EntityReference> zu verwenden, um den Wert eines Suchattributs für die verknüpfte Entität festzulegen.

Die einfachste Methode, zwei Entitätsdatensätze in einer 1: n-Beziehung zu trennen ist es, eine 1:n-Beziehung zu verwenden, um den Wert eines Suchattributs auf Null festzulegen.

Beziehungen mit einer n: n-Beziehung hängen auch von Suchattributen auf *Entität überschneidet* ab, die die n: n-Beziehung unterstützt. Diese Beziehungen definieren sich am Vorhandensein von Entitätsdatensätzen in dieser überschneidenden Entität. Wenn Sie mit der überschneidendem Entität direkt interagieren können, ist es viel einfacher, die API dafür zu verwenden.

## <a name="use-the-associate-method-or-associaterequest"></a>Nutzen Sie die Zuordnungsmethode doder AssociateRequest

Der Hauptwert während der Verwendung von <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*> Methode oder der <xref:Microsoft.Xrm.Sdk.Messages.AssociateRequest> mit dem <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methode liegt darin, dass Sie können:

- Ordnen Sie mehrere Datensätze in einen Vorgang zu
- Ordnen Sie problemlos Datensätzen mithilfe einer n: n-Beziehung zu, ohne sich mit der überschneidenen Entität zu befassen

Um den Entitätsdatensatz mit diesen APIs zuzuordnen brauchen Sie folgende drei Dinge:

- Eine Entitätsreferenz zur Entität, die Sie zuordnen möchten
- Der Name der Beziehung
- Eine oder mehrere Referenzen, die Sie der Entität zuordnen möchten

Ob die Beziehung eine 1: n- oder n: n-Beziehung ist, ist nicht von Bedeutung. Die Parameter oder die Eigenschaften sind gleich.

Sie können die Namen von Beziehungen finden, indem die die Benutzeroberfläche oder die Metadaten mithilfe des Browsers für Metadaten nutzen. Weitere Informationen: 

- [Erstellen oder Bearbeiten von 1: N (eine-zu-vielen) oder N:1 (viele-zu einer)-Entitätsbeziehungen](../../../maker/common-data-service/create-edit-1n-relationships.md)
- [Erstellen und Bearbeiten von n:n (viele zu viele)-Beziehungen](../../../maker/common-data-service/create-edit-nn-relationships.md)
- [Durchsuchen Sie Metadaten für die Organisation](../browse-your-metadata.md)

Das folgende Beispiel stellt eine bestimmte Kontaktentität (`jimGlynn`) als primären Kontakt fest für alle Firmen in Redmond.


```csharp

// Retrieve the accounts
var query = new QueryByAttribute("account")
{
ColumnSet = new ColumnSet("name")
};
query.AddAttributeValue("address1_city", "Redmond");

EntityCollection accounts = svc.RetrieveMultiple(query);

//Convert the EntityCollection to a EntityReferenceCollection
var accountReferences = new EntityReferenceCollection();

accounts.Entities.ToList().ForEach(x => {
accountReferences.Add(x.ToEntityReference());
});

// The contact to associate to the accounts
var jimGlynn = new EntityReference("contact", 
new Guid("cf76763a-ba1c-e811-a954-000d3af451d6"));

// The relationship to use
var relationship = new Relationship("account_primary_contact");

// Use the Associate method
svc.Associate(jimGlynn.LogicalName, jimGlynn.Id, relationship, accountReferences);
```
Obwohl es keinen bestimmten Vorteil auf diese Weise gibt, wenn Sie <xref:Microsoft.Xrm.Sdk.Messages.AssociateRequest> verwenden möchten, können Sie die letzten Zeile mit diesem ersetzen:


```csharp
// Use AssociateRequest
AssociateRequest request = new AssociateRequest()
{
RelatedEntities = accountReferences,
Relationship = relationship,
Target = jimGlynn
};

svc.Execute(request);
```

Dieser Code ist identisch mit drei verschiedene Aktualisierungsvorgänge zu [Firma](../reference/entities/account.md).[PrimaryContactId](../reference/entities/account.md#BKMK_PrimaryContactId) Suchattribut, aber auch verwenden die [account_primary_contact](../reference/entities/contact.md#BKMK_account_primary_contact) Beziehung, die eine n: 1-Entitätsbeziehung auf der Firmaenentität und einer 1: n-Entitätsbeziehung für die Kontaktentität ist.

Wenn die Eigenschaften der Beziehungsmetadaten überprüfen, sehen Sie, dass der Wert `ReferencingEntity` ist `account` und der `ReferencingAttribute`-Wert ist `primarycontactid`.


## <a name="use-the-disassociate-method-or-disassociaterequest"></a>Nutzen Sie die Trennungsmethode oder DissassociateRequest

Im <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*> Methode oder der <xref:Microsoft.Xrm.Sdk.Messages.DisassociateRequest> mit dem <xref:Microsoft.Xrm.Sdk.IOrganizationService><xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> Methoe ist einfach die umgekehrte Art, wie Sie die Datensätze zuordnen.

Der folgende Code kehrt die Zuordnungen um, die im Beispiel oben gemacht werden.


```csharp
// Retrieve the accounts
var query = new QueryByAttribute("account")
{
ColumnSet = new ColumnSet("name")
};
query.AddAttributeValue("address1_city", "Redmond");

EntityCollection accounts = svc.RetrieveMultiple(query);

//Convert the EntityCollection to a EntityReferenceCollection
var accountReferences = new EntityReferenceCollection();

accounts.Entities.ToList().ForEach(x => {
accountReferences.Add(x.ToEntityReference());
});

// The contact to associate to the accounts
var jimGlynn = new EntityReference("contact", 
new Guid("cf76763a-ba1c-e811-a954-000d3af451d6"));

// The relationship to use
var relationship = new Relationship("account_primary_contact");

// Use the Disassociate method
svc.Disassociate(jimGlynn.LogicalName, jimGlynn.Id, relationship, accountReferences);
```
Obwohl es keinen bestimmten Vorteil auf diese Weise gibt, wenn Sie <xref:Microsoft.Xrm.Sdk.Messages.DisassociateRequest> verwenden möchten, können Sie die letzten Zeile mit diesem ersetzen:

```csharp
// Use DisassociateRequest
DisassociateRequest request = new DisassociateRequest()
{
RelatedEntities = accountReferences,
Relationship = relationship,
Target = jimGlynn
};

svc.Execute(request);
```

### <a name="see-also"></a>Siehe auch

[Erstellen von Entitäten mit dem Organisationsservice](entity-operations-create.md)<br />
[Abrufen einer Entität mithilfe des Organisationsdienstes](entity-operations-retrieve.md)<br />
[Aktualisieren und Löschen von Entitäten mit dem Organisationsservice](entity-operations-update-delete.md)<br />

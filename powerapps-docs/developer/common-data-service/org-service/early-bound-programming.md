---
title: Programmierung von später und früher Bindung mithilfe des Organisationsservice (Common Data Service für Apps) | Microsoft Docs
description: 'Beschreibt die verschiedenen Programmierungsstile, die verfügbar sind, wenn .NET-SDK-Assemblys mit dem Organisationsservice  verwendet wird.'
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
# <a name="late-bound-and-early-bound-programming-using-the-organization-service"></a>Programmierung mit später und früher Bindung mithilfe des Organisationsdiensts

Wenn Sie mit den Organisationsserviceassemblys arbeiten, haben Sie zwei Stile, die Sie verwenden können: *spät gebunden* und *früh gebunden*.

Der entscheidende Unterschied zwischen früher und später Bindung enthält die Typkonvertierung. Wenn die frühere Bindung Kompilierzeitüberprüfung aller Typen zur Verfügung stellt, sodass keine impliziten Umwandlungen auftreten, überprüfen späte Bindung nur Typen, wenn das Objekt erstellt oder eine Aktion am Typ ausgeführt wurde. Die <xref:Microsoft.Xrm.Sdk.Entity> Klasse erfordert, dass Typen explizit angegeben werden, um implizite Umwandlungen zu vermeiden.

Späte Bindung erlaubt die Verwendung mit benutzerdefinierten Entitäten oder Attributen, die nicht verfügbar sind, als Ihr Code kompiliert wurde.

## <a name="late-bound"></a>Spät gebunden

Spät gebundene verwendet die <xref:Microsoft.Xrm.Sdk.Entity> Klasse und Sie müssen Entitäten und Attribute mithilfe der Eigenschaftswerte`LogicalName` beziehen: 
- <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.LogicalName> 
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.LogicalName>

Beziehungen besitzen keine `LogicalName`Eigenschaft, und so wird die <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase><xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.SchemaName> Eigenschaft verwendet.

Der Hauptvorteil für spät gebundene Programmierung ist, dass keine weiteren Schritte erforderlich sind, um die zu generieren Klassen in der Datei der generiert Projekte zu werden. Die generierte Datei kann recht groß sein. 

Die Hauptnachteile sind:

- Sie erhalten deshalb keine Kompilierzeitüberprüfung von Entitäten, Attributen und Beziehungen.
- Sie müssen die Namen der Attribute und Beziehungen den Metadaten kennen. 

> [!TIP]
> Ein Tool, das Sie verwenden können, um die Informationen problemlos zu finden, ist der Browser für Metadaten. Dies ist eine App, die in Ihrer Organisation heruntergeladen und installiert werden kann. Weitere Informationen: [Durchsuchen der Metadaten für die Umgebung](../browse-your-metadata.md).

### <a name="example"></a>Beispiel

Im folgenden Beispiel erstellt eine Firma mit dem später Bindung.

```csharp
//Use Entity class with entity logical name
var account = new Entity("account");

// set attribute values
    // string primary name
    account["name"] = "Contoso";            
    // Boolean (Two option)
    account["creditonhold"] = false;
    // DateTime
    account["lastonholdtime"] = new DateTime(2017, 1, 1);
    // Double
    account["address1_latitude"] = 47.642311;
    account["address1_longitude"] = -122.136841;
    // Int
    account["numberofemployees"] = 500;
    // Money
    account["revenue"] = new Money(new decimal(5000000.00));
    // Picklist (Option set)
    account["accountcategorycode"] = new OptionSetValue(1); //Preferred customer
                
//Create the account
Guid accountid = svc.Create(account);
```

## <a name="early-bound"></a>Frühe Bindung

Früh gebundene Programmierung erfordert, dass Sie zunächst einen Satz von Klassen in den Metadaten für eine bestimmte Organisation mithilfe des Codegenerierungstools (CrmSvcUtil.exe) generieren. Weitere Informationen [Generieren von Klassen für die Programmierung mit früher Bindung mithilfe des Organisationsservices](generate-early-bound-classes.md)

Wenn Sie früh gebundene Entitätsklassen mithilfe des Codegenerierungstools generiert haben, haben Sie eine bessere Erfahrung, während Sie Code schreiben, da Klassen und Attributeigenschaften die entsprechenden `SchemaName`  Eigenschaftswerte nutzen:

- <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.SchemaName> 
- <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName>
- <xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase>.<xref:Microsoft.Xrm.Sdk.Metadata.RelationshipMetadataBase.SchemaName>

Sie Instanziieren einfach die Klasse und lassen IntelliSense in Visual Studio die Namen und Eigenschaften von Beziehungen angeben.

Die Klassen, die für früh gebundene Programmierung erstellt wurden, können auch Definitionen für alle benutzerdefinierten Aktionen enthalten, die auch für die Umgebung definiert werden. Dies gibt Ihnen ein Paar Anforderungs- und Warteklassen für diese benutzerdefinierte Aktionen. Weitere Informationen: [Benutzerdefinierte Aktionen](../custom-actions.md).

Darüber hinaus ist es auch eine Option, die Generierung von Code zu erweitern, um die Ausgabe zu ändern. Eine Erweiterung erstellt Enumerationen für jeden optionset Optionswert. Dies bietet eine verbesserte Erfahrung, da Sie die ganzzahligen Werte nicht jeder Option suchen müssen. Weitere Informationen finden Sie unter [Erweiterungen für das Codegenerierungstool erstellen](extend-code-generation-tool.md).

Da jedoch die Klassen mithilfe der Metadaten für eine bestimmte Instanz erstellt wurden, und jede Instanz verschiedene Entitäten und Attribute festgelegt hat, können sie im Laufe der Zeit geändert werden. Möglicherweise müssen Sie Code schreiben für Entitäten, die nicht vorhanden sind, wenn Sie stark typisierten Klassen generieren.

> [!IMPORTANT]
> Wenn Sie <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> nutzen um die <xref:Microsoft.Xrm.Sdk.IOrganizationService> bereitzustellen, verwenden Sie die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.EnableProxyTypes> Methode, um Typen mit früher Bindung zu aktivieren.


### <a name="example"></a>Beispiel

Das folgende Beispiel erstellt eine Firma mit früher Bindung.

```csharp
var account = new Account();
// set attribute values
    // string primary name
    account.Name = "Contoso";
    // Boolean (Two option)
    account.CreditOnHold = false;
    // DateTime
    account.LastOnHoldTime = new DateTime(2017, 1, 1);
    // Double
    account.Address1_Latitude = 47.642311;
    account.Address1_Longitude = -122.136841;
    // Int
    account.NumberOfEmployees = 500;
    // Money
    account.Revenue = new Money(new decimal(5000000.00));
    // Picklist (Option set)
    account.AccountCategoryCode = new OptionSetValue(1); //Preferred customer

//Create the account
Guid accountid = svc.Create(account);
```

## <a name="choose-which-style"></a>Wählen Sie den Stil

Welchen Stil Sie wählen ist Ihnen überlassen. In der folgenden Tabelle werden die Vorteile und Nachteile für jeden bereitgestellt.

|Frühe Bindung|Späte Bindung|
|--|--|
|Sie können Entitäten, Attribute und Beziehungsnamen zur Kompilierungszeit überprüfen|Keine Kompilierungszeit von Entitäten, Attributen und Beziehungsnamen|
|Generieren Sie Entitätsklassen|Sie müssen keine Entitätsklassen generieren|
|Besserer IntelliSense-Support|Weniger IntelliSense-Support|
|Kleinerer, besser lesbarer Code| Mehr, weniger lesbarer Code|
|Etwas weniger leistungsstark|Etwas leistungsstarker|


## <a name="mix-early-and-late-bound"></a>Früh und spät gebundene Bindungen kombinieren

Da alle generierten Klassen von der <xref:Microsoft.Xrm.Sdk.Entity> Klasse erben, die mit spät gebundener Programmierung verwendet wird, können Sie sie für Entitäten, Attribute und Beziehungen verwenden, die nicht innerhalb der Klassen definiert werden.

### <a name="example"></a>Beispiel

Wenn ein benutzerdefiniertes Attribut nicht in der erstellen Klassen hinzugefügt wurde, können Sie es erneut verwenden.


```csharp
var account = new Account();
// set attribute values
    // string primary name
    account.Name = "Contoso";
    // A custom boolean attribute not included in the generated classes.
    account["sample_customboolean"] = false;


//Create the account
Guid accountid = svc.Create(account);
```

### <a name="see-also"></a>Siehe auch

[Entitäts-Vorgänge mithilfe des Organisationsservice](entity-operations.md)<br />
[Erstellen von Entitäten mit dem Organisationsservice](entity-operations-create.md)<br />
[Abrufen einer Entität mithilfe des Organisationsdienstes](entity-operations-retrieve.md)<br />
[Daten abfragen mithilfe des Organisation-Service](entity-operations-query-data.md)<br />
[Aktualisieren und Löschen von Entitäten mit dem Organisationsservice](entity-operations-update-delete.md)<br />
[Entitäten mithilfe des Organisations-Service zuordnen oder trennen](entity-operations-associate-disassociate.md)<br />
[IOrganizationService-Schnittstelle](iorganizationservice-interface.md)<br />
[Verwenden von OrganizationServiceContext](organizationservicecontext.md)<br />
---
title: Verwenden von OrganizationServiceContext (Common Data Service) | Microsoft Docs
description: Durch die OrganizationServiceContext-Klasse können Sie Änderungen nachverfolgen, Identitäten und Beziehungen verwalten und auf den LINQ-Anbieter zugreifen.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
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
ms.openlocfilehash: 849fa63edf2997eabbb67c80bbcad6bdec4eec2d
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156010"
---
# <a name="use-organizationservicecontext"></a>Verwenden von OrganizationServiceContext

In Common Data Service können Sie einige der Klassen verwenden, durch die die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Benutzeroberfläche implementiert wird, sodass auf Webdienste zugegriffen werden kann. Alternativ können Sie den durch das Codegenerierungstool generierten <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> verwenden, um Zugriff auf zusätzliche Funktionen zu erhalten. Durch die `OrganizationServiceContext`-Klasse können Sie Änderungen nachverfolgen, Identitäten und Beziehungen verwalten und auf den LINQ-Anbieter zugreifen. Diese Klasse enthält eine <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> Methode, die Sie verwenden können, um die Änderungen an den Daten zu übermitteln, die der Kontext nachverfolgt. Diese Klasse basiert auf dem gleichen Konzept wie die [DataServiceContext](/dotnet/api/system.data.services.client.dataservicecontext)-Klasse im Windows Communication Foundation (WCF) Data Services.  
  
Um diese Klasse zu generieren, stellen Sie einen Wert für den Parameter `/serviceContextName` bereit, wenn Sie Typen mit früher Bindung generieren. Das Codegenerierungstool verwendet diesen Namen als den Namen der generierten Klasse. Weitere Informationen zur Verwendung des Codegenerierungstools finden Sie unter [Generieren von Klassen für die Programmierung der frühen Bindung mit dem Organisationsservice](generate-early-bound-classes.md). Sie können den Kontext des Organisationsdienstes verwenden, wenn Sie Anwendungen, Plug-Ins und Workflowaktivitäten entwickeln.  
  
<a name="how_to_use"></a>

## <a name="how-to-use-the-organizationservicecontext-class"></a>So verwenden Sie die OrganizationServiceContext-Klasse  

Um die Kontextklasse zu instanziieren, müssen Sie dem Klassenkonstruktor ein Objekt übergeben, das die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Schnittstelle implementiert. Eine Option ist dabei, eine Instanz der <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>-Klasse zu übergeben. Weitere Informationen zur <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Benutzeroberfläche finden Sie unter [Organisationsservice-Benutzeroberfläche](iorganizationservice-interface.md).
  
Das folgende Codebeispiel zeigt, wie eine neuen Instanz der Kontextklasse erstellt wird. In diesem Beispiel wurde die Kontextklasse mit den Namen `AdventureWorksCycleServiceContext` versehen, indem der Parameter `/serviceContextName` im Codegenerierungstool angegeben wurde:  
  
```csharp  
//For early bound types to work correctly, they have to be enabled on the proxy.  
_serviceProxy.EnableProxyTypes();  
AdventureWorksCycleServiceContext context = new AdventureWorksCycleServiceContext(svc);  
```  
  
Nachdem Sie das Kontextobjekt für den Organisationsdienst erstellt haben, können Sie damit beginnen, Entitäten nachzuverfolgen, zu erstellen, zu ändern oder zu löschen. 
  
Der Organisationsdienstkontext muss jede Entität oder Beziehung nachverfolgen, die Sie an Common Data Service senden möchten. Sie könnten beispielsweise einen Datensatz mit einer LINQ-Abfrage abrufen und der Kontext würde diese Entität nachverfolgen, oder Sie können die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)> Methode verwenden, damit der Kontext mit der Nachverfolgung der Entität beginnt. Sie können mit den Daten in einer Client-Anwendung arbeiten und neue Entitäten oder verknüpfte Entitäten erstellen sowie vorhandene Entitäten bearbeiten, aber Sie müssen die `SaveChanges`-Methode für nachverfolgte Entitäten aufrufen, um Änderungen an Common Data Service zu übermitteln.  
  
<a name="track_changes"></a>

## <a name="track-changes"></a>Änderungen nachverfolgen
 
Um festzustellen wie eine Entität vom Kontext nachverfolgt wird, können Sie die Eigenschaft <xref:Microsoft.Xrm.Sdk.Entity.EntityState> auf der Entitätsinstanz überprüfen. Sie müssen dem Organisationsdienstkontext mitteilen, dass eine Entität in Common Data Service nachverfolgt werden soll, indem Sie die verschiedenen Methoden aufrufen oder eine LINQ-Abfrage verwenden. Alle Entitäten, die von einer LINQ-Abfrage zurückgegeben werden, werden vom Dienstkontext nachverfolgt.  
  
Sie können Objekte zum Dienstkontext hinzufügen, indem Sie eine der folgenden Methoden in <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> aufrufen.  
  
|Methode|Verwenden|  
|------------|---------|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)>|Fügt der Gruppe von Entitäten, die der Organisationsdienstkontext nachverfolgt, eine Entität hinzu. Der Status der Entität im Kontext wird auf `Created` gesetzt. Wenn die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>-Methode aufgerufen wird, wird dieser Datensatz auf dem Server erstellt oder hinzugefügt.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)>|Fügt der Gruppe von Entitäten, die der Organisationsdienstkontext nachverfolgt, eine Entität hinzu. Der Status der Entität im Kontext wird auf `Unchanged` gesetzt. Wenn die Methode <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> aufgerufen wird, wird diese Entität nur zum Server gesendet, wenn sich ihr Status ändert.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.CreateQuery(System.String)>|Fügt der Gruppe von Entitäten, die der Organisationsdienstkontext nachverfolgt, das Ergebnis einer Abfrage hinzu.|  
  
<a name="track_related"></a>

## <a name="track-related-objects"></a>Nachverfolgen von verwandten Objekten

In Common Data Service können Sie mit dem Organisationsdienstkontext Beziehungen zwischen Entitäten erstellen und aktualisieren. Durch die vom CrmSvcUtil.exe-Tool generierten Navigationseigenschaften in früh gebundenen Klassen können Sie auf Eigenschaften und Beziehungen der verknüpften Entität zugreifen und diese ändern. Der Organisationsdienstkontext muss die verknüpfte Entität nachverfolgen, damit die verknüpfte Entität auf dem Server aktualisiert werden kann.  
  
Verwenden Sie die folgenden Methoden in <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> um mit verknüpften Entitäten zu arbeiten und die Entität dem Dienstkontext hinzuzufügen:  
  
|Methode|Verwenden|  
|------------|---------|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddRelatedObject(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Fügt das Ziel dem Kontext hinzu. Ruft die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)>-Methode für die Zielentität und dann die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>-Methode zwischen der Quellentität und der (verknüpften) Zielentität auf.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AttachLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Fügt die verknüpfte Entität dem Kontext zur Nachverfolgung hinzu. Der Status der Entität im Kontext wird auf `Unchanged` gesetzt.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Erstellt eine Beziehung zwischen Quell- und Zielentitäten. Fügt das Ziel dem Kontext hinzu. Der Status der Zielentität im Kontext wird auf `Created` gesetzt.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.LoadProperty(Microsoft.Xrm.Sdk.Entity,System.String)>|Lädt den verknüpften Entitätssatz, der für die angegebene Beziehung festgelegt wurde. Ermöglicht den Zugriff auf verknüpfte Entitäten mithilfe der Navigationseigenschaft. Rufen Sie die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)>-Methode für die verknüpfte Entität auf, nachdem Sie auf die Entität zugegriffen haben, indem Sie eine Navigationseigenschaft für die übergeordnete Entität verwenden.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.UpdateObject(Microsoft.Xrm.Sdk.Entity)>|Ändert den Status der angegebenen Entität im `OrganizationServiceContext` auf "Geändert".|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.DeleteObject(Microsoft.Xrm.Sdk.Entity)>|Ändert den Status der zu löschenden Entität im `OrganizationServiceContext`.|  
  
<a name="BKMK_LoadRelatedEntities"></a>

### <a name="load-related-entities-using-navigation-properties"></a>Laden verknüpfter Entitäten mithilfe der Navigationseigenschaften

Verknüpfte Entitäten von Entitäten, die Sie mithilfe von LINQ abgerufen haben, weisen so lange einen Nullwerte auf, bis Sie <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.LoadProperty(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship)> verwenden, um sie abzurufen. Das folgende Codebeispiel zeigt, wie auf Aufgabendatensätze zugegriffen wird, die einem bestimmten Kontaktdatensatz zugeordnet sind.  
  
```csharp  
Contact pam = context.ContactSet.Where(c => c.FirstName == "Pamela").FirstOrDefault();  
if (pam != null)  
{  
// pam.Contact_Tasks is null until you use LoadProperty  
    context.LoadProperty(pam, "Contact_Tasks");  
    Task firstTask = pam.Contact_Tasks.FirstOrDefault();  
}  
```  
### <a name="use-the-addlink-method"></a>Verwendung der AddLink-Methode  
 Sie können die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddLink(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)> Methode verwenden, um Verbindungen herzustellen. Sie müssen die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> aufrufen, bevor der Server mit den neuen Linkinformationen aktualisiert wird.  
  
 Die folgenden Codebeispiel zeigen, wie Sie eine Zuordnung zwischen einem Kontakt und einer Firma herstellen.  
  
```csharp  
Relationship relationship = new Relationship("account_primary_contact");  
context.AddLink(contact, relationship, account);  
context.SaveChanges();  
```  

<a name="save_changes"></a>

## <a name="save-changes"></a>Änderungen speichern

Der Organisationsdienstkontext enthält ein Diagramm der nachverfolgten Entitäten. Die Reihenfolge, in der der Organisationsdienstkontex Entitätsänderungen verarbeitet und an den Server übermittelt, ist wichtig. Zunächst werden die Aktualisierungen primärer Entitäten verarbeitet, anschließend die verknüpfter Entitäten. Wenn ein Wert in der primären Entität von der verknüpfte Entität festgelegt wird, wird dieser Wert verwendet, wenn Daten auf dem Server aktualisiert werden.  
  
Wenn ein Fehler auftritt, wenn Entitätsinformationen gespeichert werden, wird ein neuer Ausnahmetyp, der <xref:Microsoft.Xrm.Sdk.SaveChangesResult> enthalt, von der <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> Methode ausgelöst, unabhängig vom Wert des <xref:Microsoft.Xrm.Sdk.Client.SaveChangesOptions>-Parameters, der an diese Methode übergeben wird.  
  
<a name="virtual"></a>

## <a name="use-virtual-methods-when-the-context-is-changed"></a>Verwenden virtueller Methoden, wenn der Kontext geändert wird

Manchmal kann es erforderlich sein, Aktionen basierend auf Änderungen des <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> auszuführen. Um dies zu erleichtern, werden virtuelle Methoden bereitgestellt, die es ermöglichen, Vorgänge abzufangen bzw. eine entsprechende Benachrichtigung zu erhalten. Um diese Möglichkeiten nutzen zu können, müssen Sie entweder vom <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext> ableiten oder den generierten Organisationsdienstkontext ändern. Die folgende Tabelle listet die virtuellen Methoden auf.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnBeginEntityTracking(Microsoft.Xrm.Sdk.Entity)>|Aufgerufen nachdem eine Entität an den `OrganizationServiceContext` angefügt wurde.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnBeginLinkTracking(Microsoft.Xrm.Sdk.Entity,Microsoft.Xrm.Sdk.Relationship,Microsoft.Xrm.Sdk.Entity)>|Aufgerufen nachdem ein Link an den `OrganizationServiceContext` angefügt wurde.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnEndEntityTracking(Microsoft.Xrm.Sdk.Entity)>|Aufgerufen nachdem eine Entität aus dem `OrganizationServiceContext` entfernt wurde.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnEndEntityTracking(Microsoft.Xrm.Sdk.Entity)>|Aufgerufen nachdem ein Link aus dem `OrganizationServiceContext` entfernt wurde.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnExecuting(Microsoft.Xrm.Sdk.OrganizationRequest)>|Aufgerufen, direkt bevor eine Abfrage an Common Data Service gesendet wird.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnExecute(Microsoft.Xrm.Sdk.OrganizationRequest,Microsoft.Xrm.Sdk.OrganizationResponse)>|Aufgerufen direkt nachdem eine Abfrage an Common Data Service gesendet wurde, unabhängig davon, ob eine Ausnahme aufgetreten ist oder nicht.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnSavingChanges(Microsoft.Xrm.Sdk.Client.SaveChangesOptions)>|Aufgerufen bevor ein Vorgang nach einem vom Aufruf von `SaveChanges` auftritt.|  
|<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.OnSaveChanges(Microsoft.Xrm.Sdk.SaveChangesResultCollection)>|Aufgerufen, wenn alle Vorgänge für einen Aufruf von `SaveChanges` abgeschlossen wurden, oder falls ein Fehler auftritt.|  


<a name="use_context"></a>   

## <a name="data-operations"></a>Datenvorgänge

Sie können Objekte im Organisationsservicekontext ändern, erstellen und löschen, und die an den Objekten vorgenommenen Änderungen werden von Common Data Service nachverfolgt. Wenn <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> Wenn die Common Data Service.-Methode aufgerufen wird, werden die Befehle, die die entsprechenden Einfüge-, Aktualisierungs- oder Löschanweisungen für Daten in Common Data Service ausgeführt.  
  
Bei der Verwendung von Entitätsklassen mit früher Bindung verwenden Sie den Entitätsnamen und Attributschemanamen, um eine Entität oder ein Attribut anzugeben, die bzw. das verwendet werden soll. Attributschemanamen werden in <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata><xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.SchemaName> und <xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata>.<xref:Microsoft.Xrm.Sdk.Metadata.AttributeMetadata.SchemaName>definiert oder Sie können die Klassen- und Eigenschaftennamen verwenden, die in der Code-generierten Datei angezeigt werden. Das folgende Beispiel zeigt, wie Sie einen Wert dem E-Mail-Attribut einer neuen Kontaktinstanz zuweisen.  
  
```csharp  
Contact contact = new Contact();
contact.EMailAddress1 = “sonny@contoso.com”;  
```  
 
  
<a name="create_new"></a>   

## <a name="create-a-new-entity-record"></a>Erstellen eines neuen Entitätsdatensatzes

 Wenn Sie Daten in Common Data Service einfügen möchten, indem Sie das Entity Data Model verwenden, müssen Sie eine Instanz eines Entitätstyps erstellen und das Objekt zu einem Organisationsservicekontext hinzufügen. Der Organisationsservicekontext muss das Objekt nachverfolgen, damit er das Objekt in Common Data Service speichern kann.  
  
 Wenn Sie einen neuen Entitätsdatensatz erstellen, fügen Sie das Objekt zum Organisationsservicekontext hinzu, indem Sie die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)>-Methode verwenden. Methode.  
  
 Das folgende Beispiel zeigt, wie Sie einen neuen Kontaktdatensatz mithilfe des Entity Data Models instanziieren und speichern. Es veranschaulicht außerdem den Zugriff auf ein benutzerdefiniertes Attribut.  
  
```csharp  
OrganizationServiceContext orgContext =new OrganizationServiceContext(svc);  
Contact contact = new Contact()     
 {  
   FirstName = "Charles",  
   LastName = "Brown",  
   Address1_Line1 = "123 Main St.",  
   Address1_City = "Des Moines",  
   Address1_StateOrProvince = "IA",  
   Address1_PostalCode = "21254",  
   new_twittername = "Chuck",  
   Telephone1 = "123-234-5678"  
 };   
orgContext.AddObject(contact);
orgContext.SaveChanges();  
```  

Es gibt mehrere Punkte, die Sie im vorherigen Codebeispiel beachten sollten. Nachdem ein neuer Kontakt instanziiert wurde müssen Sie zunächst dieses Kontaktobjekt an die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.AddObject(Microsoft.Xrm.Sdk.Entity)>- Methode übergeben, damit der Kontext mit der Nachverfolgung des Objekts beginnen kann. Der zweite Punkt, den Sie beachten sollten, ist, dass das neue Objekt auf dem Server gespeichert wird, indem die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>- Methode.  
  
Wenn Sie ein Ziel zum Kontext und vor der <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> Methode wurde, der generiert Kontext eine ID für das neue Objekt bezeichnet. Eine Ausnahme, die `SaveChangesResults` enthält, wird über die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges>-Methode ausgelöst, wenn Aktualisierungen an den Common Data Service-Daten nicht erfolgreich sind.  
  
<a name="update"></a>   

## <a name="update-an-entity-record"></a>Aktualisieren eines Entitätsdatensatzes  

Änderungen an Objekten, die an den Organisationsservicekontext angefügt sind, werden von Common Data Service nachverfolgt. Um einen vorhandenen Entitätsdatensatz zu ändern, müssen Sie zunächst das Objekt zum Kontext hinzufügen. Um ein Objekt zum Kontext hinzuzufügen, müssen Sie zunächst den Entitätsdatensatz aus Common Data Service abrufen und dann das Objekt zum Kontext hinzufügen, indem Sie die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.Attach(Microsoft.Xrm.Sdk.Entity)>-Methode verwenden. Wenn das Objekt vom Kontext nachverfolgt wird, können Sie den Datensatz aktualisieren, indem Sie die Attribute der Entität festlegen.  
  
Das folgende Beispiel zeigt, wie ein Kontenattribut mithilfe von Klassen mit früher Bindung aktualisiert wird.  
  
```csharp  
Account.EMailAddress1 = “Contoso-WebMaster@contoso.com”;  
```  
  
 Das folgende Beispiel zeigt, wie ein Attributwert gelöscht wird.  
  
```csharp  
Account.EMailAddress1 = null;  
```  
  
 Es gibt zwei partielle Methoden mit der Bezeichnung `OnPropertyChanging` und `OnPropertyChanged` für jede Entität. Diese Methoden werden im Eigenschaftensetter aufgerufen. Sie können diese Methoden erweitern, indem Sie partielle Klassen verwenden, um benutzerdefinierte Geschäftslogik einzufügen.  
  
<a name="delete"></a>   

## <a name="delete-an-entity-record"></a>Löscht einen Entitätsdatensatz   

Der Organisationsservicekontext muss das Objekt nachverfolgen, damit ein Entitätsdatensatz gelöscht werden kann. Nachdem das Objekt im Kontext verfügbar ist, können Sie die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.DeleteObject(Microsoft.Xrm.Sdk.Entity)>-Methode verwenden, um das Objekt im Kontext zum Löschen zu markieren. Beachten Sie, dass der Entitätsdatensatz in Common Data Service erst gelöscht wird, wenn die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext.SaveChanges> Methode aufgerufen wird.  
  
### <a name="see-also"></a>Siehe auch

[LINQ-Abfragenbeispiele mithilfe von OrganizationServiceContext mit Common Data Service](linq-query-examples.md)<br />
[Generieren von Klassen für die Programmierung mit früher Bindung mithilfe des Organisationsservices](generate-early-bound-classes.md)<br />
<xref:Microsoft.Xrm.Sdk.IOrganizationService><br />
<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceContext>
---
title: Verwenden von Messages mithilfe des Organisationsservices (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie, wie Messages verwendet werden, um Vorgänge mithilfe des Organisationsservices aufzurufen.'
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
# <a name="use-messages-with-the-organization-service"></a>Verwenden von Messages mithilfe des Organisationsservices

Alle Datenvorgänge im Organisationsservice werden als Messages definiert. Während <xref:Microsoft.Xrm.Sdk.IOrganizationService> 7 Methoden für das Durchführen von Datenvorgängen bietet (<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Retrieve*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Delete*>, <xref:Microsoft.Xrm.Sdk.IOrganizationService.Associate*>, und <xref:Microsoft.Xrm.Sdk.IOrganizationService.Disassociate*> ), ist jede dieser Methoden ein bequemer Wrapper für die zugrunde liegende Message, die schließlich mithilfe der <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>-Methode aufgerufen wird. Die zugrunde liegende Organisationsservice verfügt lediglich über die <xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>-Methode als einzelnen Parameter: eine Instanz der <xref:Microsoft.Xrm.Sdk.OrganizationRequest>-Klasse. Der Wert, der durch die `Execute`-Methode zurückgegeben wird, ist eine Instanz der <xref:Microsoft.Xrm.Sdk.OrganizationResponse>-Klasse.

Um Ihre Erfahrung zu verbessern, wenn Sie Code schreiben, können alle Standardsystemdatenvorgänge ein Paar der `*Request`- und `*Response`-Klassen haben, die in den SDK-Assemblys definiert werden. Jede dieser Klassen übernehmen Eigenschaften der entsprechenden <xref:Microsoft.Xrm.Sdk.OrganizationRequest>- und <xref:Microsoft.Xrm.Sdk.OrganizationResponse>-Klassen und liefern eine produktivere Erfahrung für Sie, wenn Sie Code schreiben.

Die folgenden Beispiele zeigen drei unterschiedliche Möglichkeiten, einen Firmaentitätsdatensatz zu erstellen, der so definiert ist:

```csharp
var account = new Account();
account.Name = "Test account";
```

Mithilfe von <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Create*>

```csharp
var id = svc.Create(account);
```

Mithilfe von <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> und <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

```csharp
CreateRequest request = new CreateRequest()
{ Target = account };
var id = ((CreateResponse)svc.Execute(request)).id;
```

Mithilfe von <xref:Microsoft.Xrm.Sdk.OrganizationRequest> und <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*>

```csharp
ParameterCollection parameters = new ParameterCollection();
parameters.Add("Target", account);

OrganizationRequest request = new OrganizationRequest() {
RequestName = "Create",
Parameters = parameters
};

OrganizationResponse response = svc.Execute(request);

var id = (Guid)response.Results["id"];
```

Wie Sie sehen, werden allgemeine Datenvorgänge mithilfe der <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methoden optimiert und System-Messages durch die `*Request`- und `*Response`-Klassen in den SDK-Assemblys vereinfacht. Meistens müssen Sie nicht die zugrunde liegenden <xref:Microsoft.Xrm.Sdk.OrganizationRequest>- und <xref:Microsoft.Xrm.Sdk.OrganizationResponse>-Klassen verwenden. Ausnahmen gelten in den folgenden Fällen.

## <a name="working-with-messages-in-plug-ins"></a>Arbeiten von Messages in Plug-Ins

Die Daten, die einen Vorgang in einem Plug-In beschreiben, liegen in folgender Form vor: <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> und <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>. Diese <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Eigenschaften enthalten die Werte, die für die <xref:Microsoft.Xrm.Sdk.OrganizationRequest> in den ersten zwei Phasen der Ereignisausführungspipeline und in der <xref:Microsoft.Xrm.Sdk.OrganizationResponse>-Klasse in der Phase nach dem Hauptvorgang verwendet werden.

Wenn Sie die Struktur der Messages verstehen, erkennen Sie auch, wo Sie die Daten finden, die innerhalb des Plug-Ins prüfen oder ändern möchten.

Weitere Informationen: 

- [Schreiben von Plug-Ins, um Geschäftsprozesse zu erweitern](../plug-ins.md)
- [Ereignisframework](../event-framework.md)

## <a name="using-custom-actions"></a>Verwenden benutzerdefinierter Aktionen

Wenn Sie eine benutzerdefinierte Aktionen verwenden, gibt es für diese Vorgänge keine Klassen in den SDK-Assemblys. Sie können mithilfe des Codegenerierungstools `CrmSvcUtil.exe` Klassen für sie generieren, indem Sie den Parameter `generateActions` verwenden, oder Sie können eine <xref:Microsoft.Xrm.Sdk.OrganizationRequest>-Instanz instanziieren und festlegen, dass <xref:Microsoft.Xrm.Sdk.OrganizationRequest.RequestName> und <xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters> ohne die generierten Klassen verwendet werden. Um mit den Ergebnissen zu arbeiten, müssen Sie die Werte analysieren, die hiervon zurückgegeben werden: <xref:Microsoft.Xrm.Sdk.OrganizationResponse>.<xref:Microsoft.Xrm.Sdk.OrganizationResponse.Results> -Eigenschaft verfügbar.

Weitere Informationen: 

- [Generieren von Klassen für die Programmierung mit früher Bindung mithilfe des Organisationsservices](generate-early-bound-classes.md)
- [Benutzerdefinierte Aktionen](../custom-actions.md)

## <a name="passing-optional-parameters-with-a-request"></a>Übergeben optionaler Parameter mit einer Anfrage

Sie können die optionalen Parameters in Messages mithilfe der <xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters>-Eigenschaft übergeben, die für alle *Anfrage-Message-Klassen in den SDK-Assemblys eingeblendet werden. Es gibt zwei optionale Parameter, die Sie mit Messages übergeben können.

|`Parameter`|Beschreibung|Meldungen|  
|-----------------|-----------------|--------------|  
|`SolutionUniqueName`|Eine `String`, die den eindeutigen Namen der Lösung angibt, für die der Vorgang gilt. Weitere Informationen: [Abhängigkeitsnachverfolgung für Lösungskomponenten](../dependency-tracking-solution-components.md).|<xref:Microsoft.Crm.Sdk.Messages.AddPrivilegesRoleRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.DeleteRequest> <br /> <xref:Microsoft.Crm.Sdk.Messages.MakeAvailableToOrganizationTemplateRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>|  
|`SuppressDuplicateDetection`|Eine `Boolean` wird verwendet, um Duplikaterkennung auf einem Erstellungs- der Aktualisierungsvorgang zu deaktivieren. Weitere Informationen: [Verwenden des SuppressDuplicateDetection-Parameters, um Fehler beim Erstellen oder Aktualisieren von Datensätzen auszugeben](detect-duplicate-data.md#use-suppressduplicatedetection-parameter-to-throw-errors-when-you-create-or-update-record).|<xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> <br /> <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest>|  
  
 Das folgende Beispiel zeigt, wie ein optionaler parameter übergeben wird:  
  
```csharp  
Account account = new Account();  
account.Name = "Fabrikam";  
CreateRequest req = new CreateRequest();  
req.Target = account;  
req["SuppressDuplicateDetection"] = true;  
CreateResponse response = (CreateResponse)svc.Execute(req);  
```  

### <a name="see-also"></a>Siehe auch

[Entitäts-Vorgänge mithilfe des Organisationsservice](entity-operations.md)<br />
[Verwenden von ExecuteAsync](use-executeAsync.md)<br />
[Verwenden von ExecuteTransaction](use-executetransaction.md)<br />
[Ausführen mehrerer Anfragen mithilfe des Organisationsservices](execute-multiple-requests.md)




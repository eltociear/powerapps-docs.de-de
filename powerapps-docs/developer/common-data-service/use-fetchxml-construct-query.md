---
title: Verwendung von FetchXML zum Abfragen von Daten (Common Data Service für Apps) | Microsoft Docs
description: 'FetchXML ist eine herstellereigene Abfragesprache, die in Common Data Service (CDS) für Apps verwendet wird. Sie basiert auf einem Schema, das die Funktionalität der Sprache beschreibt.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="use-fetchxml-to-construct-a-query"></a>Verwenden von FetchXML zum Erstellen einerAbfrage

FetchXML ist eine herstellereigene Abfragesprache, die in Common Data Service (CDS) für Apps verwendet wird. Sie basiert auf einem Schema, das die Funktionalität der Sprache beschreibt. Die FetchXML-Sprache unterstützt ähnliche Abfragefunktionen als Abfrageausdrücke. Zusätzlich wird sie als serialisiertes Abfrageformular verwendet, das verwendet wird, um eine Abfrage als gespeicherte benutzereigene Ansicht in der [UserQuery Entität](reference/entities/userquery.md) und als gespeicherte organisationseigene Ansicht in der [SavedQuery-Entität](reference/entities/savedquery.md) zu speichern.  
  
Eine FetchXML-Abfrage kann mithilfe von **Web API** oder **Organization Service** ausgeführt werden.

## <a name="create-the-fetchxml-query-string"></a>Erstellen der FetchXML-Abfragezeichenfolge
  
Um eine FetchXML-Abfrage auszuführen, müssen Sie zuerst die XML-Abfragezeichenfolge erstellen. Nach dem Erstellen der Abfragezeichenfolge verwenden Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> Methode, um die Abfragezeichenfolge auszuführen. Die Rechte des angemleldeten Benutzers haben Auswirkungen auf den zurückgegebenen Satz von Datensätzen. Nur Datensätze, für die der angemeldete Benutzer über Leseberechtigung verfügt, werden zurückgegeben.  
  
 Die FetchXML-Abfragezeichenfolge muss der Schemadefinition für die FetchXML-Sprache entsprechen. Weitere Informationen finden Sie unter [FetchXML-Schema](fetchxml-schema.md).  
  
 Sie können auch eine Abfrage speichern, indem Sie einen `SavedQuery`-Datensatz erstellen. Legen Sie `visible` im `link-entity`-Knoten auf `false` fest, um die verknüpfte Entität in der Benutzeroberfläche der **Erweiterten Suche** auszublenden. Sie wird weiterhin an der Ausführung der Abfrage teilnhmn und die entsprechenden Ergebnisse zurückgeben.  
  
> [!WARNING]
>  Rufen Sie nicht alle Attribute in einer Abfrage ab, da dadurch die Leistung beeinträchtigt wird. Das trifft insbesondere zu, wenn die Abfrage als Parameter in einer Updateanforderung verwendet wird. Wenn in einem Update alle Attribute enthalten sind, werden dadurch alle Feldwerte festgelegt, selbst wenn sie unverändert sind, und häufig werden kaskadierende Updates zu untergeordneten Datensätzen ausgelöst.  
  

### <a name="example-fetchxml-query-strings"></a>Beispiel-FetchXML-Abfragezeichenfolgen

Im folgenden Beispiel ruft die Anweisung **FetchXML** alle Konten ab:  
  
```xml  
  
<fetch mapping='logical'>   
   <entity name='account'>  
      <attribute name='accountid'/>   
      <attribute name='name'/>   
</entity>  
</fetch>  
  
```  
  
 Im folgenden Beispiel ruft die Anweisung **FetchXML** alle Konten ab, bei denen der Nachname des besitzenden Benutzers nicht gleich Cannon ist:  
  
```xml  
  
<fetch mapping='logical'>  
   <entity name='account'>   
      <attribute name='accountid'/>   
      <attribute name='name'/>   
      <link-entity name='systemuser' to='owninguser'>   
         <filter type='and'>   
            <condition attribute='lastname' operator='ne' value='Cannon' />   
          </filter>   
      </link-entity>   
   </entity>   
</fetch>  
  
```  
  
 Im folgenden Beispiel verwendent die **FetchXML**-Anweisung Zählung, um die maximalen Anzahl der Datensätze festzulegen, die von der Abfrage zurückgegeben werden. In diesem Fall werden die ersten 3 Konten von der Abfrage zurückgegeben.  
  
```xml  
<fetch mapping='logical' count='3'>  
  <entity name='account'>  
   <attribute name='name' alias='name'/>  
  </entity></fetch>  
```  
  
Dieses Beispiel zeigt eine innere Verbindung zwischen EntityMap und AttributeMap, wo die EntityMapID übereinstimmt.  
  
```xml  
<fetch version='1.0' mapping='logical' distinct='false'>  
   <entity name='entitymap'>  
      <attribute name='sourceentityname'/>  
      <attribute name='targetentityname'/>  
      <link-entity name='attributemap' alias='attributemap' to='entitymapid' from='entitymapid' link-type='inner'>  
         <attribute name='sourceattributename'/>  
         <attribute name='targetattributename'/>  
      </link-entity>  
   </entity>  
 </fetch>  
```  
  
## <a name="execute-the-fetchxml-query"></a>Ausführen der FetchXML-Abfrage

Sie können eine FetchXML-Abfrage ausführen, indem Sie entweder die **Web API** oder den **Organization Service** verwenden.

### <a name="using-web-api"></a>Verwenden von Web-API
Sie können eine URL codierte FetchXml-Zeichenfolge zum entsprechenden entityset mithilfe des Abfragezeichenfolgenparameters `fetchXml` ausführen. Weitere Informationen: [Benutzerdefiniertes FetchXML verwenden](webapi/retrieve-and-execute-predefined-queries.md#use-custom-fetchxml).

### <a name="using-organization-service"></a>Verwenden des Organisationsservice

Verwenden Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> Methode, um einen <xref:Microsoft.Xrm.Sdk.Query.FetchExpression> zu übergeben, bei der die <xref:Microsoft.Xrm.Sdk.Query.FetchExpression.Query>-Eigenschaft die FetchXml-Abfrage enthält.

Der folgende Code zeigt, wie eine **FetchXML**-Abfrage mithilfe des Organisationservice ausgeführt wird:  
  
```csharp  
  
// Retrieve all accounts owned by the user with read access rights to the accounts and   
// where the last name of the user is not Cannon.   
string fetch2 = @"  
   <fetch mapping='logical'>  
     <entity name='account'>   
        <attribute name='accountid'/>   
        <attribute name='name'/>   
        <link-entity name='systemuser' to='owninguser'>   
           <filter type='and'>   
              <condition attribute='lastname' operator='ne' value='Cannon' />   
           </filter>   
        </link-entity>   
     </entity>   
   </fetch> ";   
  
EntityCollection result = _serviceProxy.RetrieveMultiple(new FetchExpression(fetch2));
foreach (var c in result.Entities)
{
   System.Console.WriteLine(c.Attributes["name"]);
}  
```  
> [!NOTE]
> Sie können eine FetchXML-Abfrage in einen Abfrageausdruck mit der <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>-Nachricht konvertieren. 

  
## <a name="fetchxml-query-results"></a>FetchXML-Abfrageergebnisse  
 Wenn Sie einer FetchXML-Abfrage ausführen, indem Sie die <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy>.<xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy.RetrieveMultiple(Microsoft.Xrm.Sdk.Query.QueryBase)> Methode authentifiziert den Benutzer. Methode, ist der Rückgabewert eine <xref:Microsoft.Xrm.Sdk.EntityCollection>, die die Ergebnisse der Abfrage enthält. Sie können dann die Entitätssammlung durchlaufen. Der vorherige Beispiel verwendet die `foreach`-Schleife, um die Ergebnissammlung der FetchXML-Abfrage zu durchlaufen.  
  

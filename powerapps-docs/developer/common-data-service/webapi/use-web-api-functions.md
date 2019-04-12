---
title: Nutzen von Web-API-Funktionen (Common Data Service) | Microsoft Docs
description: 'Funktionen sind wiederverwendbare Vorgänge, die mit einer GET-Anforderung zum Abrufen von Daten aus Common Data Service verwendet werden'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: c6de9c12-e8e3-4ed5-a6ed-18ade572065f
caps.latest.revision: 45
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-web-api-functions"></a>Nutzen von Web-API-Funktionen

Funktionen und Aktionen stellen wiederverwendbare Vorgänge dar, die Sie mithilfe der Web-API ausführen können. Es gibt zwei Arten von Funktionen im Web API:  
  
**Funktionen**  
Nutzen Sie eine `GET`-Anforderung mit den Funktionen, die in <xref:Microsoft.Dynamics.CRM.FunctionIndex> aufgeführt sind, um Vorgänge ausführen, die keine Nebenwirkungen haben. Diese Funktionen rufen üblicherweise Daten ab. Sie geben entweder eine Sammlung oder einen komplexen Typ zurück. Jede der Funktionalitäten verfügt über eine entsprechende Meldung im Organisationsservice.  
  
**Abfragefunktionen**  
Verwenden Sie die in <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex> aufgeführten Funktionen, um die Eigenschaften und Werte in einer Abfrage auswerten. Jede dieser Funktionalitäten verfügt über einen entsprechenden <xref:Microsoft.Xrm.Sdk.Query.ConditionOperator>-Wert.  
  
<a name="bkmk_passParametersToFunctions"></a>

## <a name="passing-parameters-to-a-function"></a>Übergeben von Parametern an eine Funktion
  
Für Funktionen, die Parameter benötigen, wird empfohlen, die Werte mithilfe von Parametern zu übergeben. Wenn Sie z. B. <xref href="Microsoft.Dynamics.CRM.GetTimeZoneCodeByLocalizedName?text=GetTimeZoneCodeByLocalizedName Function" /> verwenden, müssen die Parameterwerte `LocalizedStandardName` und `LocaleId` enthalten sein. Sie könnten also die im Folgenden gezeigte Inlinesyntax verwenden.  
  
```http
GET [Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName='Pacific Standard Time',LocaleId=1033)  
```  
  
Es gibt jedoch ein noch nicht gelöstes Problem bei der Verwendung von DateTimeOffset-Werten mit der Inlinesyntax, wie im Artikel erläutert: [DateTimeOffset als Abfrageparameter 204](https://github.com/OData/WebApi/issues/204).  
  
Daher wird empfohlen, die Werte als Parameter zu übergeben, wie im folgenden Codebeispiel zu sehen. Wenn Sie diese bewährte Methode verwenden, können Sie das offene Problem vermeiden, das für `DateTimeOffset` gilt.  
  
```http
GET [Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName=@p1,LocaleId=@p2)?@p1='Pacific Standard Time'&@p2=1033  
```  
  
Parameteraliase ermöglichen auch die Wiederverwendung von Parameterwerten, um die Gesamtlänge der URL zu verringern, wenn der Parameterwert mehrmals verwendet wird.  
  
<a name="bkmk_passCrmEntityReference"></a>

## <a name="pass-reference-to-an-entity-to-a-function"></a>Verweis auf eine Entität an eine Funktion übergeben

Bestimmte Funktionen benötigen das Übergeben eines Verweises auf eine vorhandene Entität. Beispielsweise verfügen die folgenden Funktionen über einen Parameter, der einen <xref href="Microsoft.Dynamics.CRM.crmbaseentity?text=crmbaseentity EntityType" /> benötigt.  
  
||||  
|-|-|-|  
|<xref href="Microsoft.Dynamics.CRM.CalculateRollupField?text=CalculateRollupField Function" />|<xref href="Microsoft.Dynamics.CRM.IncrementKnowledgeArticleViewCount?text=IncrementKnowledgeArticleViewCount Function" />|<xref href="Microsoft.Dynamics.CRM.InitializeFrom?text=InitializeFrom Function" />|  
|<xref href="Microsoft.Dynamics.CRM.IsValidStateTransition?text=IsValidStateTransition Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveLocLabels?text=RetrieveLocLabels Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrievePrincipalAccess?text=RetrievePrincipalAccess Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveRecordWall?text=RetrieveRecordWall Function" />|<xref href="Microsoft.Dynamics.CRM.ValidateRecurrenceRule?text=ValidateRecurrenceRule Function" />|  
  
Wenn Sie einen Verweis an eine vorhandene Entität übergeben, verwenden Sie die `@odata.id`-Anmerkung zum URI für die Entität. Angenommen Sie verwenden die <xref href="Microsoft.Dynamics.CRM.RetrievePrincipalAccess?text=RetrievePrincipalAccess Function" />, können Sie folgenden URI verwenden, um das Abrufen des Zugriffs zu einem bestimmten Kontakt anzugeben:  
  
```http
GET [Organization URI]/api/data/v9.0/systemusers(af9b3cf6-f654-4cd9-97a6-cf9526662797)/Microsoft.Dynamics.CRM.RetrievePrincipalAccess(Target=@tid)?@tid={'@odata.id':'contacts(9f3162f6-804a-e611-80d1-00155d4333fa)'}
```  
  
Die `@odata.id`-Anmerkung kann der vollständige URI sein, aber ein relativer URI funktioniert auch.  
  
<a name="bkmk_boundAndUnboundFunctions"></a>
 
## <a name="bound-and-unbound-functions"></a>Gebundene und ungebundene Funktionen

Es können nur die Funktionen in <xref:Microsoft.Dynamics.CRM.FunctionIndex> gebunden werden. Abfragefunktionen sind niemals gebunden.  
  
<a name="bkmk_boundFunctions"></a>

### <a name="bound-functions"></a>Gebundene Funktionen

Im [CSDL-Metadatendokument](web-api-types-operations.md#bkmk_csdl), wenn ein `Function`-Element eine gebundene Funktion darstellt, besitzt es ein `IsBound`-Attribut mit dem Wert `true`. Das erste `Parameter`-Element innerhalb der Funktion repräsentiert die Entität, an die die Funktion geknüpft ist. Wenn das Attribut `Type` des Parameters eine Sammlung ist, wird die Funktion an eine Entitätssammlung gebunden. Als Beispiel wird die folgende Definition der <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" /> und <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse?text=CalculateTotalTimeIncidentResponse ComplexType" /> in der CSDL dargestellt.  
  
```xml
<ComplexType Name="CalculateTotalTimeIncidentResponse">  
  <Property Name="TotalTime" Type="Edm.Int64" Nullable="false" />  
</ComplexType>  
<Function Name="CalculateTotalTimeIncident" IsBound="true">  
  <Parameter Name="entity" Type="mscrm.incident" Nullable="false" />  
  <ReturnType Type="mscrm.CalculateTotalTimeIncidentResponse" Nullable="false" />  
</Function>  
```  
  
Diese Bindungsfunktion ähnelt <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest>, was vom Organisationsservice verwendet wird. In der Web-API ist diese Funktion an <xref href="Microsoft.Dynamics.CRM.incident?text=incident EntityType" /> gebunden, der die <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest>.<xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentRequest.IncidentId> -Eigenschaft verfügbar. Anstatt eine <xref:Microsoft.Crm.Sdk.Messages.CalculateTotalTimeIncidentResponse> zurückzugeben, gibt diese Funktion eine <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse?text=CalculateTotalTimeIncidentResponse ComplexType" /> zurück. Gibt eine Funktion einen komplexen Datentyp zurück, so wird dessen Definition direkt über der Definition der Funktion in CSDL angezeigt.  
  
Um eine gebundene Funktion aufzurufen, hängen Sie den vollständigen Namen der Funktion an die URL an. Beziehen Sie alle benannten Parameter in den Klammer nach dem Funktionsnamen mit ein. Der vollständige Funktionsname enthält den Namespace `Microsoft.Dynamics.CRM`. Für nicht gebundene Funktionen das nicht der vollständige Name verwendet werden.  
  
> [!IMPORTANT]
>  Eine Funktion muss mithilfe einer URI aufgerufen werden, um den ersten Parameterwert festzulegen. Sie können es nicht als Parameterwert mit Namen festlegen.  
  
Das folgende Beispiel zeigt ein Beispiel mittels <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" />, das an die `incident`-Entität gebunden ist.  
  
 **Anforderung**

```http
GET [Organization URI]/api/data/v9.0/incidents(90427858-7a77-e511-80d4-00155d2a68d1)/Microsoft.Dynamics.CRM.CalculateTotalTimeIncident() HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**
 
```http 
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse","TotalTime":30  
}  
```  
  
<a name="bkmk_unboundFunctions"></a>
 
### <a name="unbound-functions"></a>Ungebundene Funktionen

Der <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> ist nicht an eine Entität gebunden. Es wird in CSDL ohne `IsBound`-Attribut definiert.  
  
```xml
<ComplexType Name="WhoAmIResponse">  
  <Property Name="BusinessUnitId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="UserId" Type="Edm.Guid" Nullable="false" />  
  <Property Name="OrganizationId" Type="Edm.Guid" Nullable="false" />  
</ComplexType>  
<Function Name="WhoAmI">  
  <ReturnType Type="mscrm.WhoAmIResponse" Nullable="false" />  
</Function>  
```  
  
Diese Funktion entspricht <xref:Microsoft.Crm.Sdk.Messages.WhoAmIRequest> und gibt einen <xref href="Microsoft.Dynamics.CRM.WhoAmIResponse?text=WhoAmIResponse ComplexType" /> zurück, der <xref:Microsoft.Crm.Sdk.Messages.WhoAmIResponse> entspricht, was vom Organisationsservice verwendet wird. Diese Funktion verfügt über keine Parameter.  
  
Wenn Sie eine ungebundene Funktion aufrufen, verwenden Sie nur den Funktionsnamen wie im folgenden Beispiel gezeigt.  
  
 **Anforderung**

```http
GET [Organization URI]/api/data/v9.0/WhoAmI() HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**

```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
{  
 "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.WhoAmIResponse",  
 "BusinessUnitId": "ded5a64f-f06d-e511-80d0-00155db07cb1",  
 "UserId": "d96e9f55-f06d-e511-80d0-00155db07cb1",  
 "OrganizationId": "4faf1f34-f06d-e511-80d0-00155db07cb1"  
}  
```  
  
<a name="bkmk_composeQueryWithFunctions"></a>

## <a name="compose-a-query-with-functions"></a>Verfassen Sie Sie eine Abfrage mit Funktionen

Es gibt zwei Möglichkeiten, mit denen Funktionen verwendet werden können, um Daten, die mit Anfragen zurückgesendet werden, zu kontrollieren. Bestimmte Funktionen ermöglichen Kontrolle über die Spalten oder Bedingungen, die sie zurückgeben, und Sie verwenden Abfragefunktionen, um die Bedingungen in einer Abfrage zu evaluieren.  
  
<a name="bkmk_composableFunctions"></a>
  
### <a name="composable-functions"></a>Verfassbare Funktionen

Einige in <xref:Microsoft.Dynamics.CRM.FunctionIndex> aufgeführte Funktionen, geben eine Sammlung von Einträgen zurück. Eine Teilmenge dieser Funktionen ist *zusammensetzbar*, das heißt, Sie können eine weitere Systemabfrageoption `$select` oder `$filter` einschließen, um zu steuern, welche Spalten in den Ergebnissen zurückgegeben werden. Diese Funktionen haben ein `IsComposable`-Attribut im CDSL. Jede dieser Funktionen enthält eine Begleitnachricht im Organisationsservice, der entweder einen Parameter vom Typ <xref:Microsoft.Xrm.Sdk.Query.ColumnSet> oder <xref:Microsoft.Xrm.Sdk.Query.QueryBase> akzeptiert. Die OData Systemabfrageoptionen enthalten dieselben Features, also haben diese Funktionen nicht die gleichen Parameter wie die Begleitnachrichten im Organisationsservice. Die folgende Tabelle enthält eine Liste dieser zusammensetzbaren Funktionen in dieser Version.  
  
||||  
|-|-|-|  
|<xref href="Microsoft.Dynamics.CRM.GetDefaultPriceLevel?text=GetDefaultPriceLevel Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveAllChildUsersSystemUser?text=RetrieveAllChildUsersSystemUser Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveBusinessHierarchyBusinessUnit?text=RetrieveBusinessHierarchyBusinessUnit Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrieveByGroupResource?text=RetrieveByGroupResource Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveByResourceResourceGroup?text=RetrieveByResourceResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveMembersBulkOperation?text=RetrieveMembersBulkOperation Function" />|  
|<xref href="Microsoft.Dynamics.CRM.RetrieveParentGroupsResourceGroup?text=RetrieveParentGroupsResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveSubGroupsResourceGroup?text=RetrieveSubGroupsResourceGroup Function" />|<xref href="Microsoft.Dynamics.CRM.RetrieveUnpublishedMultiple?text=RetrieveUnpublishedMultiple Function" />|  
|<xref href="Microsoft.Dynamics.CRM.SearchByBodyKbArticle?text=SearchByBodyKbArticle Function" />|<xref href="Microsoft.Dynamics.CRM.SearchByKeywordsKbArticle?text=SearchByKeywordsKbArticle Function" />|<xref href="Microsoft.Dynamics.CRM.SearchByTitleKbArticle?text=SearchByTitleKbArticle Function" />|  
  
<a name="bkmk_queryevaluationFunctions"></a>
  
### <a name="query-functions"></a>Abfragefunktionen

In <xref:Microsoft.Dynamics.CRM.QueryFunctionIndex> aufgeführte Funktionen sind für das Verfassen einer Abfrage vorgesehen. Diese Funktionen können ähnlich wie die [Integrierte Abfragefunktionen](query-data-web-api.md#bkmk_buildInQueryFunctions) verwendet werden, aber es gibt einige wichtige Unterschiede.  
  
Sie müssen den vollständigen Namen der Funktion eingeben und die Parameternamen mit einschließen. Das folgende Beispiel zeigt die Anwendung von <xref href="Microsoft.Dynamics.CRM.LastXHours?text=LastXHours Function" /> zum Zurückgeben aller Firmenentitäten, die in den letzten 12 Stunden geändert wurden.  
  
```http
GET [Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber&$filter=Microsoft.Dynamics.CRM.LastXHours(PropertyName=@p1,PropertyValue=@p2)&@p1='modifiedon'&@p2=12  
```  
  
### <a name="see-also"></a>Siehe auch

[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](samples/functions-actions-csharp.md)<br />
[Beispiele von Web API-Funktionen und Aktionen (clientseitiges JavaScript)](samples/functions-actions-client-side-javascript.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)

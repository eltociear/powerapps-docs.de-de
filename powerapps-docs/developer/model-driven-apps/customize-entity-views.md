---
title: Entitätsansichten anpassen (modellgesteuerte Apps) | Microsoft Docs
description: Informationen zur Anpassung der Entitätsansichten.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: da2a9b57-fcd2-38c5-c670-63acf1767efa
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e0d0b9dc84ea44e971871213a480c0094bc249d4
ms.sourcegitcommit: 5701e7a755fade6c3bac5c4a5774fcc74627e168
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "3115654"
---
# <a name="customize-entity-views"></a>Anpassen von Entitätsansichten

Entitätsansichten sind spezielle gespeicherte Abfragen, die Daten mithilfe eines spezifischen Filters abrufen. Sie enthalten auch Informationen dazu, wie die Daten in der Ansicht in der Anwendung angezeigt werden sollen. Entitätsansichten sind `SavedQuery`-Datensätze, die Sie programmgesteuert erstellen können. Sie können sie auch als XML definieren und mit einer nicht verwalteten Lösung importieren.  
  
 Eine Entitätsansicht unterscheidet sich von einer `UserQuery`. Eine Benutzerabfrage, die in der Anwendung als gespeicherte Ansicht bezeichnet wird, befindet sich im Besitz eines einzelnen Benutzers, kann anderen Benutzern zugewiesen und für andere Benutzer freigegeben werden und kann von anderen Benutzern abhängig von den Zugriffsrechten der Abfrage angezeigt werden. Dies ist für häufig verwendete Abfragen, die sich über mehrere Entitätstypen erstrecken, und Abfragen, die eine Aggregation ausführen, geeignet. Weitere Informationen: [Gespeicherte Abfragen](../common-data-service/saved-queries.md) 
  
 Sie können auch das Anpassungstool verwenden, um die Ansichten anzupassen. Weitere Informationen: [Erstellen und Bearbeiten von Ansichten](../../maker/model-driven-apps/create-edit-views.md)
  
<a name="BKMK_TypesOfViews"></a>   
## <a name="types-of-views"></a>Typen von Ansichten  
 In der folgenden Tabelle werden die fünf Ansichtstypen aufgeführt, die für die Anpassung unterstützt werden. Der Typcode einer Ansicht wird im `SavedQuery.QueryType`-Attribut gespeichert. Beachten Sie, dass es andere gültige Werte für das `QueryType`-Attribut gibt, die hier nicht aufgeführt sind, da diese Entität auch zum Speichern von Office Outlook-Filtern und -Vorlagen verwendet wird. Weitere Informationen finden Sie unter [Offline- und Outlook-Filter und Vorlagen](../common-data-service/outlook-client/offline-outlook-filters-templates.md). 
  
 Wenn Ansichten für eine bestimmte Entität definiert werden, gibt das `SavedQuery.ReturnedTypeCode`-Attribut den logischen Namen der Entität zurück.  
  
|Ansichtstyp|Typcode|Beschreibung|  
|---------------|---------------|-----------------|  
|**Öffentlich**|0|- **Vorkommen**: Viele<br />- **Aktionen**: Erstellen, Aktualisieren, Löschen<br />- **Kommentare**: Sie können eine dieser Ansichten als standardmäßige öffentliche Ansicht festlegen, indem Sie `SavedQuery.IsDefault` auf "true" festlegen.|  
|**Erweiterte Suche**|1|- **Vorkommen**: 1<br />- **Aktionen**: Nur Aktualisieren.<br />- **Kommentare**: Diese Ansicht wird standardmäßig angezeigt, wenn Ergebnisse in **Erweiterte Suche** angezeigt werden.|  
|**Zugeordnet**|2|- **Vorkommen**: 1<br />- **Aktionen**: Nur Aktualisieren.<br />- **Kommentare**: Diese Ansicht wird standardmäßig angezeigt, wenn ein Raster mit verknüpften Datensätzen im Navigationsbereich eines Datensatzes angezeigt wird.|  
|**Schnellsuche**|4|- **Vorkommen**: 1<br />- **Aktionen**: Nur Aktualisieren.<br />- **Kommentare**: Diese Ansicht definiert die Spalten, die durchsucht werden, wenn ein Benutzer nach Datensätzen sucht, indem er das Suchfeld in einer Listenansicht verwendet.|  
|**Suche**|64|- **Vorkommen**: 1<br />- **Aktionen**: Nur Aktualisieren.<br />- **Kommentare**: Dies ist die standardmäßige Ansicht, die verwendet wird, um einen Datensatz zu suchen, wenn keine andere Ansicht für das Suchfeld konfiguriert wurde.|  
  
<a name="BKMK_CreateViews"></a>   
## <a name="create-views"></a>Erstellen von Ansichten  
 Wenn Sie eine öffentliche Ansicht erstellen, geben Sie die folgenden Eigenschaften an:
  
- `SavedQuery.Name`: ein eindeutiger Bezeichner für die gespeicherte Abfrage.
  
- `SavedQuery.ReturnedTypeCode`: stimmt mit dem logischen Name der Entität überein. 
  
- `SavedQuery.FetchXml`: Siehe [Verwenden von FetchXML zum Erstellen einer Abfrage](../common-data-service/use-fetchxml-construct-query.md).  
  
- `SavedQuery.LayoutXml`: Lesen Sie das `layoutxml`-Element in [Anpassungslösungs-Dateischema](../common-data-service/customization-solutions-file-schema.md) für die gültigen Elemente.
  
- `SavedQuery.QueryType`: muss immer Null (0) sein.  
  
  Das folgende Bespiel erstellt eine neue öffentliche Ansicht für die Verkaufschancenentität:  
  
  ```csharp
  System.String layoutXml =
  @"<grid name='resultset' object='3' jump='name' select='1' 
    preview='1' icon='1'>
    <row name='result' id='opportunityid'>
    <cell name='name' width='150' /> 
    <cell name='customerid' width='150' /> 
    <cell name='estimatedclosedate' width='150' /> 
    <cell name='estimatedvalue' width='150' /> 
    <cell name='closeprobability' width='150' /> 
    <cell name='opportunityratingcode' width='150' /> 
    <cell name='opportunitycustomeridcontactcontactid.emailaddress1' 
        width='150' disableSorting='1' /> 
    </row>
  </grid>";

  System.String fetchXml =
  @"<fetch version='1.0' output-format='xml-platform' 
    mapping='logical' distinct='false'>
    <entity name='opportunity'>
    <order attribute='estimatedvalue' descending='false' /> 
    <filter type='and'>
        <condition attribute='statecode' operator='eq' 
        value='0' /> 
    </filter>
    <attribute name='name' /> 
    <attribute name='estimatedvalue' /> 
    <attribute name='estimatedclosedate' /> 
    <attribute name='customerid' /> 
    <attribute name='opportunityratingcode' /> 
    <attribute name='closeprobability' /> 
    <link-entity alias='opportunitycustomeridcontactcontactid' 
        name='contact' from='contactid' to='customerid' 
        link-type='outer' visible='false'>
        <attribute name='emailaddress1' /> 
    </link-entity>
    <attribute name='opportunityid' /> 
    </entity>
  </fetch>";

  SavedQuery sq = new SavedQuery
    {
      Name = "A New Custom Public View",
      Description = "A Saved Query created in code",
      ReturnedTypeCode = "opportunity",
      FetchXml = fetchXml,
      LayoutXml = layoutXml,
      QueryType = 0
    };
                    
  _customViewId = _serviceProxy.Create(sq);
  Console.WriteLine("A new view with the name {0} was created.", sq.Name);
  ```  
  
<a name="BKMK_UpdateViews"></a>   
## <a name="update-views"></a>Aktualisieren von Ansichten  
 Wenn die `SavedQuery.IsCustomizable` verwaltete Eigenschaft erlaubt, die Ansicht zu aktualisieren, können Sie verwenden<xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Update*> Methode bzw. die <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> Meldung, um die Ansicht zu aktualisieren.  
  
<a name="BKMK_DeleteViews"></a>   
## <a name="delete-views"></a>Löschen von Ansichten  
 Sie sollten nur gespeicherte Abfragen löschen, die Sie erstellt haben. Eine Lösungskomponente oder ein Teil der Anwendung ist möglicherweise von einer spezifischen gespeicherten Abfrage abhängig. Wenn Abfragen vorhanden sind, die nicht in der Anwendung angezeigt werden sollen, sollten Sie sie deaktivieren.  
  
<a name="BKMK_RetrieveViews"></a>   
## <a name="retrieve-views"></a>Abrufen von Ansichten  
 Verwenden Sie eine <xref:Microsoft.Xrm.Sdk.Messages.RetrieveMultipleRequest>oder <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.RetrieveMultiple*> um gespeicherte Abfragedatensätze abzurufen.  
  
 Das folgende Bespiel ruft alle öffentlichen Ansichten für die Verkaufschancenentität ab:  
  
 ```csharp
 QueryExpression mySavedQuery = new QueryExpression
        {
            ColumnSet = new ColumnSet("savedqueryid", "name", "querytype", "isdefault", "returnedtypecode", "isquickfindquery"),
            EntityName = SavedQuery.EntityLogicalName,
            Criteria = new FilterExpression
            {
                Conditions =
{
    new ConditionExpression
    {
        AttributeName = "querytype",
        Operator = ConditionOperator.Equal,
        Values = {0}
    },
    new ConditionExpression
    {
        AttributeName = "returnedtypecode",
        Operator = ConditionOperator.Equal,
        Values = {Opportunity.EntityTypeCode}
    }
}
            }
        };
        RetrieveMultipleRequest retrieveSavedQueriesRequest = new RetrieveMultipleRequest { Query = mySavedQuery };

        RetrieveMultipleResponse retrieveSavedQueriesResponse = (RetrieveMultipleResponse)_serviceProxy.Execute(retrieveSavedQueriesRequest);

        DataCollection<Entity> savedQueries = retrieveSavedQueriesResponse.EntityCollection.Entities;

        //Display the Retrieved views
        foreach (Entity ent in savedQueries)
        {
            SavedQuery rsq = (SavedQuery)ent;
            Console.WriteLine("{0} : {1} : {2} : {3} : {4} : {5},", rsq.SavedQueryId, rsq.Name, rsq.QueryType, rsq.IsDefault, rsq.ReturnedTypeCode, rsq.IsQuickFindQuery);
        }
```
  
<a name="BKMK_DeactivateViews"></a>   
## <a name="deactivate-views"></a>Deaktivieren von Ansichten  
 Wenn eine öffentliche Ansicht nicht in der Anwendung angezeigt werden soll, können Sie sie deaktivieren. Sie können eine öffentliche Ansicht nicht deaktivieren, die als Standardansicht festgelegt ist. Das folgende Beispiel deaktiviert die Ansicht **Abgeschlossene Verkaufschancen im aktuellen Geschäftsjahr** für die Verkaufschancenentität:  
  
 ```csharp
 System.String SavedQueryName = "Closed Opportunities in Current Fiscal Year";
QueryExpression ClosedOpportunitiesViewQuery = new QueryExpression
{
    ColumnSet = new ColumnSet("savedqueryid", "statecode", "statuscode"),
    EntityName = SavedQuery.EntityLogicalName,
    Criteria = new FilterExpression
    {
        Conditions =
        {
            new ConditionExpression
            {
                AttributeName = "querytype",
                Operator = ConditionOperator.Equal,
                Values = {0}
            },
            new ConditionExpression
            {
                AttributeName = "returnedtypecode",
                Operator = ConditionOperator.Equal,
                Values = {Opportunity.EntityTypeCode}
            },
                            new ConditionExpression
            {
                AttributeName = "name",
                Operator = ConditionOperator.Equal,
                Values = {SavedQueryName}
            }
        }
    }
};

RetrieveMultipleRequest retrieveOpportuntiesViewRequest = new RetrieveMultipleRequest { Query = ClosedOpportunitiesViewQuery };

RetrieveMultipleResponse retrieveOpportuntiesViewResponse = (RetrieveMultipleResponse)_serviceProxy.Execute(retrieveOpportuntiesViewRequest);

SavedQuery OpportunityView = (SavedQuery)retrieveOpportuntiesViewResponse.EntityCollection.Entities[0];
_viewOriginalState = (SavedQueryState)OpportunityView.StateCode;
_viewOriginalStatus = OpportunityView.StatusCode;


SetStateRequest ssreq = new SetStateRequest
{
    EntityMoniker = new EntityReference(SavedQuery.EntityLogicalName, (Guid)OpportunityView.SavedQueryId),
    State = new OptionSetValue((int)SavedQueryState.Inactive),
    Status = new OptionSetValue(2)
};
_serviceProxy.Execute(ssreq);
 ``` 
 
> [!NOTE]
> Der Ansichtsstatus, aktiv oder inaktiv, wird beim Hinzufügen zu einer Lösung nicht in die Ansicht aufgenommen. Wenn die Lösung in eine Zielorganisation importiert wird, wird der Status daher standardmäßig auf aktiv gesetzt.

  
<a name="BKMK_EditFilterOrSorting"></a>   
## <a name="edit-filter-criteria-or-configure-sorting"></a>Bearbeiten von Filterkriterien oder Konfigurieren der Sortierung  
 Wenn Sie den Filter bearbeiten oder die Sortierung der Daten bearbeiten möchten, müssen Sie das Attribut `SavedQuery.FetchXml` festlegen. Weitere Informationen finden Sie unter [Verwenden von FetchXML, um eine Abfrage zu erstellen](/powerapps/developer/common-data-service/use-fetchxml-construct-query).  
  
> [!TIP]
>  Wenn Sie mit FetchXML nicht vertraut sind, können die folgenden Meldungen verwendet werden, um QueryExpression in FetchXML zu konvertieren und umgekehrt: <xref:Microsoft.Crm.Sdk.Messages.QueryExpressionToFetchXmlRequest> und <xref:Microsoft.Crm.Sdk.Messages.FetchXmlToQueryExpressionRequest>.  
  
<a name="BKMK_EditColumns"></a>   
## <a name="edit-columns"></a>Bearbeiten von Spalten  
 Die Spalten, die in den Ansichten angezeigt werden sollen, können von der Entität oder von verknüpften Entitäten übernommen werden. Weitere Informationen, wie Spalten angegeben werden, die angezeigt werden sollen, finden Sie unter dem `layoutxml`-Element im [Anpassungslösungsdateischema](../common-data-service/customization-solutions-file-schema.md).  
  
<a name="BKMK_CustomIcons"></a>   
## <a name="add-custom-icons-with-tooltip-for-a-column"></a>Fügen Sie benutzerdefiniert Symbole QuickInfo für eine Spalte hinzu  
 Sie können benutzerdefinierte Symbole mit QuickInfotext in einer Spalte abhängig vom Spaltenwert hinzufügen; Sie können auch den lokalisiertem QuickInfotext angeben. Dies kann erfolgen, indem benutzerdefinierte Symbole wie Bildwebressourcen Ihrer Instanz hinzugefügt werden und dann eine JavaScript-Webressource verwendet wird, um den JavaScript-Code für eine Spalte hinzuzufügen und das Symbol abhängig vom Spaltenwert hinzuzufügen.  
  
> [!NOTE]
>  Das Hinzufügen benutzerdefinierter Symbole mit QuickInfos wird nur für die schreibgeschützten Raster unterstützt; diese Funktion wird für bearbeitbare Raster nicht unterstützt. Weitere Informationen zum Abfrage-Assistenten bearbeitbare Raster, siehe [Bearbeitbare Raster verwenden](/powerapps/developer/model-driven-apps/use-editable-grids).  
  
 Zwei neue Attribute, `imageproviderwebresource` und `imageproviderfunctionname`, werden dem `cell`-Element der layoutxml von savedquery hinzugefügt, mit dem Sie den Namen einer Webressource und einen JavaScript-Funktionsnamen angeben können, um benutzerdefinierte Symbole und Schnellinfos für eine Spalte anzugeben. Der JavaScript-Code wird ausgeführt, wenn die Seite geladen wird.  
  
 Sie können die Felder neue **Webressource** und **Funktionsname** auf der Seite **Spalten-Eigenschaften** beim Ändern der Eigenschaft eines Attributes (Spalte) in einer Ansichtsdefinition auch verwenden, um den Webressourcenamen und den JavaScript-Funktionsnamen anzugeben.  
  
 Der folgende Beispielcode zeigt, wie Sie eine Webressource und einen JavaScript-Funktionsnamen zum Hinzufügen benutzerdefinierter und Symbole und QuickInfo für die `opportunityratingcode`-Spalte in layoutxml programmgesteuert angeben können:  
  
```csharp  
System.String layoutXml =  
@"<grid name='resultset' object='3' jump='name' select='1'  
  preview='1' icon='1'>  
  <row name='result' id='opportunityid'>  
    <cell name='name' width='150' />  
    <cell name='customerid' width='150' />  
    <cell name='estimatedclosedate' width='150' />  
    <cell name='estimatedvalue' width='150' />  
    <cell name='closeprobability' width='150' />  
    <cell name='opportunityratingcode' width='150' imageproviderwebresource='new_SampleWebResource'  
          imageproviderfunctionname='displayIconTooltip' />  
    <cell name='opportunitycustomeridcontactcontactid.emailaddress1'  
        width='150' disableSorting='1' />  
  </row>  
</grid>";  
```  
  
 Die JavaScript-Funktion zum Anzeigen benutzerdefinierter Symbole und QuickInfo-Text erwartet die folgenden beiden Argumente: das gesamte Zeilenobjekt angegeben in layoutxml und des aufrufender Benutzers Gebietsschema-ID (LCID). Der LCID-Parameter ermöglicht Ihnen, QuickInfotext für das Symbol in mehreren Sprachen zu definieren. Weitere Informationen zu den unterstützten Sprachen, finden Sie unter [Aktivieren weiterer Sprachen](/dynamics365/customer-engagement/customize/enable-additional-languages) <!-- TODO need to update the link in the powerapps repo--> und [Installieren oder Aktualisieren von Sprachpaketen](https://technet.microsoft.com/library/hh699674.aspx). Eine Liste mit Werten von lokalen Gebietsschema-ID (LCID)-Werten, die Sie in Ihrem Code verwenden können, finden Sie unter [Von Microsoft zugewiesene lokale IDs](https://go.microsoft.com/fwlink/?linkid=829588).  
  
 Sie werden wahrscheinlich benutzerdefinierte Symbole für einen Optionssatztyp von Attributen hinzufügen, da die vordefinierten Optionen begrenzt sind. Stellen Sie sicher, dass Sie den ganzzahligen Wert der Optionen anstelle der Beschriftung verwenden, um zu verhindern, dass der Code aufgrund der Änderung in der lokalisierten Beschriftungszeichenfolge unterbrochen wird. In der JavaScript-Funktion geben Sie einfach den Namen einer Bildwebressource an, die Sie als Symbol für einen Wert im Attribut verwenden möchten. Das Bild sollte von der Größe der Pixel 16x16 betragen; größere Bilder werden automatisch auf die Größe von 16x16 Pixel heruntergeschraubt.  
  
 Der folgende Beispielcode zeigt Symbole und Tooltiptexte auf Basis von drei Werten an (1: Hot, 2: Warm, 3: Cold) im Attribut `opportunityratingcode (Rating)` (Bewertung) an. Der Beispielcode zeigt auch, wie ein lokalisiertes Tooltip angezeigt wird. Damit dieses Beispiel funktioniert, müssen Sie drei Image-Webressourcen mit jeweils 16x16 Bildern (![Bewertungsschaltfläche Heiß](media/dynamics365hotgridicon.png "Bewertungsschaltfläche Heiß"), ![Bewertungssymbol Warm](media/dynamics365warmgridicon.png "Bewertungssymbol Warm") und ![Bewertungsschaltfläche Kalt](media/dynamics365coldgridicon.png "Bewertungsschaltfläche Kalt")) in Ihrer Instanz mit den folgenden Namen erstellen: `new_Hot`, `new_Warm`, und `new_Cold`.  
  
```javascript 
function displayIconTooltip(rowData, userLCID) {      
    var str = JSON.parse(rowData);  
    var coldata = str.opportunityratingcode_Value;  
    var imgName = "";  
    var tooltip = "";  
    switch (coldata) {  
        case 1:  
            imgName = "new_Hot";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Hot";  
                    break;  
                default:  
                    tooltip = "Opportunity is Hot";  
                    break;  
            }  
            break;  
        case 2:  
            imgName = "new_Warm";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Warm";  
                    break;  
                default:  
                    tooltip = "Opportunity is Warm";  
                    break;  
            }  
            break;  
        case 3:  
            imgName = "new_Cold";  
            switch (userLCID) {  
                case 1036:  
                    tooltip = "French: Opportunity is Cold";  
                    break;  
                default:  
                    tooltip = "Opportunity is Cold";  
                    break;  
            }  
            break;  
        default:  
            imgName = "";  
            tooltip = "";  
            break;  
    }  
    var resultarray = [imgName, tooltip];  
    return resultarray;  
}  
```  
  
 Dies kann dazu führen, dass die Werte in der `Rating` Spalte mit entsprechenden Symbolen dargestellt werden, abhängig vom Wert und von Symbol Quickinfotext, wenn Sie über die Symbole fahren.  
  
 ![Benutzerdefinierte Symbole werden für eine Spalte in einer Ansicht angezeigt](media/customiconsinviews.png "Benutzerdefinierte Symbole werden für eine Spalte in einer Ansicht angezeigt")  
  
<a name="BKMK_SetAsDefault"></a>   
## <a name="set-as-default"></a>Als Standard festlegen  
 Nur eine aktive öffentliche Ansicht kann als Standardansicht festgelegt werden. Um eine Ansicht als Standardansicht festzulegen, legen Sie die Eigenschaft `IsDefault` auf "true" fest.  
  

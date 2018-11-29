---
title: Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung (Common Data Service für Apps) | Microsoft Docs
description: 'Mit der neuen Änderungsnachverfolgungsfunktion in Dynamics 365 Customer Engagement können die Daten performant synchronisiert werden, indem feststellt wird, welche Daten geändert wurden, nachdem die Daten ursprünglich extrahiert oder zuletzt synchronisiert wurden.'
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
# <a name="use-change-tracking-to-synchronize-data-with-external-systems"></a>Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung

Mit der neuen Änderungsnachverfolgungsfunktion in Common Data Service für Apps können die Daten performant synchronisiert werden, indem festgestellt wird, welche Daten geändert wurden, nachdem die Daten ursprünglich extrahiert oder zuletzt synchronisiert wurden. Zuvor war es ohne diese neue Funktion schwierig, einen effizienten und zuverlässigen Mechanismus zu entwickeln, um zu bestimmen, welche Datensätze in CDS für Apps geändert wurden. In diesem Thema wird erläutert, wie Änderungen für eine Entität abgerufen werden.  
  
<a name="BKMK_enable"></a>   
## <a name="enable-change-tracking-for-an-entity"></a>Aktivieren der Änderungsnachverfolgung für eine Entität  

 Bevor Sie die Änderungen für eine Entität abrufen, sollten Sie sicherstellen, dass die Änderungsnachverfolgungsfunktion für diese Entität aktiviert ist. Diese Funktion kann aktiviert werden, indem Sie die Anpassungsbenutzeroberfläche verwenden, oder programmgesteuert, indem die <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.ChangeTrackingEnabled>-Eigenschaft auf `True` festgelegt wird. Anmerkung `Org.OData.Capabilities.V1.ChangeTracking ` wird Entitätssätzen hinzugefügt, die die Änderungsnachverfolgung aktiviert haben. Um Anmerkungen in Entitätsmetadaten, gehen Sie so vor 

 ```http 
 GET [Organization URI]/api/data/v9.0/$metadata?annotations=true
 ```
 Lesen Sie mehr über Metadatenanmerkungen unter [Metadatenanmerkungen](webapi/web-api-types-operations.md#bkmk_metannot).
 
 Weitere Informationen zur Verwendung von Anpassungsbenutzeroberfläche finden Sie unter [Aktivieren der Änderungsnachverfolgung zur Steuerung der Datensynchronisierung](https://technet.microsoft.com/library/3fa9c316-9dc9-4b28-9abf-43a3fce5b01d.aspx).  
  
<a name="BKMK_webapi"></a>   
## <a name="retrieve-changes-for-an-entity-using-the-web-api"></a>Abrufen von Änderungen für eine Entität mithilfe der Web-API  
Änderungen, die in den Entitäten vorgenommen werden, können mithilfe von Web-API-Anforderungen nachverfolgt werden, indem `odata.track-changes` als Einstellungskopfzeile hinzugefügt wird. Einstellungskopfzeile `odata.track-changes` wird verwendet, um anzufordern, dass ein *Deltalink* zurückgegeben wird, der später verwendet werden kann, um Entitätsänderungen abzurufen.

Deltalinks sind opake, Service-generierte Links, die der Client verwendet, um nachfolgende Änderungen an einem Ergebnis abzurufen. Sie basieren auf einer definierende Abfrage, die den Datensatz der Ergebnisse beschreibt, für die Änderungen nachverfolgt werden; beispielsweise die Anforderung, die die Ergebnisse generiert hat, die den Deltalink enthalten. Der Deltalink codiert die Sammlung von Entitäten, für die Änderungen nachverfolgt werden, zusammen mit einem Ausgangspunkt, ab dem Änderungen nachverfolgt werden solleen. Lesen Sie mehr über Deltalinks hier [Oasis OData Version 4.0 - Deltalinks](http://docs.oasis-open.org/odata/odata/v4.0/cs01/part1-protocol/odata-v4.0-cs01-part1-protocol.html#_Toc365046305)

<a name="BKMK_webapiexample"></a>   
## <a name="retrieve-changes-in-entities-using-web-api-example"></a>Abrufen von Änderungen an Entitäten mit dem Web-API-Beispiel

In diesem Beispiel wird gezeigt, wie die an Firmendaten vorgenommenen Änderungen mit der Web-API abgerufen werden.

Anforderung
```http
GET [Organization URI]/org1/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax HTTP/1.1
Prefer: odata.track-changes
Cache-Control: no-cache
OData-Version: 4.0
Content-Type: application/json
```
Antwort
```json
{
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts(name,accountnumber,telephone1,fax)",
"@odata.deltaLink": "[Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax&$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44",
"value":[
           {
              "@odata.etag":"W/\"915244\"",
              "name":"Monte Orton",
              "accountnumber":null,
              "telephone1":"555000",
              "fax":"10101",
              "accountid":"60c4e274-0d87-e711-80e5-00155db19e6d"
           }
       ]
}
```
Der Deltalink, der im oben aufgeführten Beispiel zurückgegeben wurde, kann verwendet werden, um Änderungen in den Entitäten anzuzeigen. In diesem Beispiel wird eine neue Firma erstellt und eine vorhandene Firma gelöscht. Der Deltalink, der aus der vorherigen Anfrage zurückgegeben wurde, ruft diese Änderungen ab, wie im Beispiel unten.

Anforderung
```http
GET [Organization URI]/api/data/v9.0/accounts?$select=name,accountnumber,telephone1,fax&$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44
```
Antwort
```json
{
          "@odata.context":"[Organization URI]/data/v9.0/$metadata#accounts(name,telephone1,fax)/$delta",
          "@odata.deltaLink":"[Organization URI]/api/data/v9.0/accounts?$select=name,telephone1,fax&$deltatoken=919058%2108%2f22%2f2017%2008%3a21%3a20",
"value":
    [
        {
            "@odata.etag":"W/\"915244\"",
            "name":"Monte Orton",
            "telephone1":"555000",
            "fax":"10101",
            "accountid":"60c4e274-0d87-e711-80e5-00155db19e6d"
        },
        {
            "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#accounts/$deletedEntity",
            "id":"2e451703-c686-e711-80e5-00155db19e6d",
            "reason":"deleted"
        }
    ]
}
```
Die Antwort für den Deltalink, der in der ersten Änderungsnachverfolgungsanforderung zurückgegeben werden, enthält einen anderen Deltalink. Dieser Deltalink ruft alle nachfolgenden Änderungen in den Entitäten ab. Eine leere JSON-Antwort wird zurückgegeben, wenn keine Entitätsänderungen eingetreten sind, nachdem die erste Änderungsnachverfolgungsanforderung abgerufen wurde.

<a name="bkmk_count"></a>
## <a name="retrieve-count-of-the-changes-made-in-entities-using-web-api"></a>Abrufen der Anzahl der Änderungen in den Entitäten mit der Web-API
`$count` kann zu dem Deltalink hinzugefügt werden, der von der ursprünglichen Änderungsnachverfolgungsanforderung zurückgegeben wird, wie im Beispiel unten, um die Anzahl der vorgenommenen Änderungen abzurufen.

Anforderung
```http
GET [Organization URI]/api/data/v9.0/accounts/$count?$deltatoken=919042%2108%2f22%2f2017%2008%3a10%3a44
```

<a name="bkmk_unsupported"></a>
## <a name="query-options-not-supported-in-change-tracking-web-api-request"></a>Abfrageoptionen werden nicht unterstützt in der Änderungsnachverfolgungs-Web-API-Anforderung
Systemabfrageoptionen `$filter`, `$orderby` und `$top` werden nicht unterstützt, wenn `odata.track-changes` als Kopfzeile in einer Web-API-Anforderung verwendet wird. Eine Fehlermeldung mit dem Hinweis, dass der Abfrageparameter `$filter`/ `$orderby`/ `$top` nicht unterstützt wird, wenn die Änderungsnachverfolgung aktiviert ist, wird angezeigt. wird zurückgegeben, wenn diese Abfrageoptionen in der Web-API-Anforderung verwendet werden.

<a name="BKMK_retrieve"></a>   
## <a name="retrieve-changes-for-an-entity-using-the-organization-service"></a>Abrufen von Änderungen für eine Entität mithilfe des Organisationsdienstes
 Wenn Änderungsnachverfolgung für eine Entität aktiviert ist, können Sie die <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityChangesRequest>-Nachricht verwenden, um die Änderungen für diese Entität abzurufen. Beim ersten Verwenden dieser Nachricht werden alle Datensätze für die Entität zurückgegeben, und diese Daten können verwendet werden, um den externen Speicher aufzufüllen. Die Nachricht gibt zudem eine Versionsnummer zurück, die mit der nächsten Verwendung der <xref:Microsoft.Xrm.Sdk.Messages.RetrieveEntityChangesRequest>-Nachricht zurückgesendet wird, sodass nur Daten für Änderungen, die seit dieser Version aufgetreten sind, zurückgegeben werden.  
  
 Sie sollten folgende Einschränkungen beim Abrufen von Änderungen für eine Entität berücksichtigen:  
  
- Nur eine Entität wird beim Abrufen von Änderungen nachverfolgt. Wenn das Abrufen von Änderungen ohne Version/Token ausgeführt wird, behandelt der Server dies als Mindestversion des Systems, wobei alle Datensätze als neu zurückgegeben werden. Gelöschte Objekte werden nicht zurückgegeben.  
  
- Änderungen werden zurückgegeben, wenn das letzte Token innerhalb eines Standardwerts von 90 Tagen liegt. Liegt es über 90 Tagen, gibt das System alle Datensätze zurück.  
  
- Wenn ein Client einen Änderungssatz für eine Entität besitzt, z. B. Version 1, wird ein Datensatz erstellt und vor der nächsten Änderungsabfrage gelöscht, sie erhalten das gelöschte Element, selbst wenn sie nicht das Element für den Start hatten.  
  
- Datensätze werden in der Reihenfolge abgerufen wie von der serverseitige Logik bestimmt. Normalerweise erhält der Endbenutzer zuerst alle neuen oder aktualisierten Datensätze (sortiert nach Versionsnummer), gefolgt von den gelöschten Datensätzen.  Wenn 3000 Datensätze erstellt oder aktualisiert werden und 2000 Datensätze gelöscht werden, gibt CDS für Apps eine Sammlung von 5000 Datensätzen zurück, in der die ersten 3000 Einträge die der neuen oder aktualisierten Datensätze sind und die letzten 2000 Einträge die der gelöschten Datensätze.  
  
- Wenn die neue oder aktualisierte Elementsammlung größer als 5000 ist, kann der Benutzer durch die Sammlung blättern.  
  
<a name="BKMK_SampleCode"></a>   
## <a name="sample-code"></a>Beispielcode   
 Der folgende Codeausschnitt zeigt, wie die `RetrieveEntityChangesRequest`-Nachricht verwendet wird, um die Änderungen für eine Entität abzurufen. Das vollständige Beispiel finden Sie unter [Synchronisieren von Daten mit externen Systemen mithilfe der Änderungsnachverfolgung](http://go.microsoft.com/fwlink/p/?LinkId=533957).  
  
```csharp
string token;

// Initialize page number.
int pageNumber = 1;
List<Entity> initialrecords = new List<Entity>();

// Retrieve records by using Change Tracking feature.
RetrieveEntityChangesRequest request = new RetrieveEntityChangesRequest();
request.EntityName = _customBooksEntityName.ToLower();
request.Columns = new ColumnSet("sample_bookcode", "sample_name", "sample_author");
request.PageInfo = new PagingInfo() { Count = 5000, PageNumber = 1, ReturnTotalRecordCount = false };


// Initial Synchronization. Retrieves all records as well as token value.
Console.WriteLine("Initial synchronization....retrieving all records.");
while (true)
{
    RetrieveEntityChangesResponse response = (RetrieveEntityChangesResponse)_serviceProxy.Execute(request);

    initialrecords.AddRange(response.EntityChanges.Changes.Select(x => (x as NewOrUpdatedItem).NewOrUpdatedEntity).ToArray());
    initialrecords.ForEach(x => Console.WriteLine("initial record id:{0}", x.Id));
    if (!response.EntityChanges.MoreRecords)
    {
        // Store token for later query
        token = response.EntityChanges.DataToken;
        break;

    }
    // Increment the page number to retrieve the next page.
    request.PageInfo.PageNumber++;
    // Set the paging cookie to the paging cookie returned from current results.
    request.PageInfo.PagingCookie = response.EntityChanges.PagingCookie;
}

```  
  
### <a name="see-also"></a>Siehe auch  
 [Definieren von Alternativschlüsseln für eine Entität](define-alternate-keys-entity.md)   
 [Verwenden von Alternativschlüsseln](use-alternate-key-create-record.md)   
 [Aktualisieren von Dynamics 365 mit externen Daten mithilfe von Upsert](use-upsert-insert-update-record.md)

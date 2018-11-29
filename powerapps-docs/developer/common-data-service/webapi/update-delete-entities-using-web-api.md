---
title: Aktualisieren und Löschen von Entitäten mithilfe der Web-API (Common Data Service für Apps) | Microsoft Docs
description: 'Lesen Sie, wie Sie das Update und Löschen für Entitäten unter Verwendung der Web-API durchführen'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 694889fd-2b85-43a0-97bc-1e760695db31
caps.latest.revision: 17
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="update-and-delete-entities-using-the-web-api"></a>Entitäten aktualisieren und löschen mithilfe der Web API

Die Operationen, um Daten zu ändern, sind ein Kernteil der Web API. Zusätzlich zu einer einfachen Aktualisierung und zu einer Löschung können Sie Operationen auf einzelnen Attributen durchführen und *upsert*-Anfragen verfassen, die entweder eine Entität aktualisieren oder einfügen abhängig davon, ob sie existiert.  
  
> [!NOTE]
>  Die Metadaten, die Entitäten definieren, werden auf andere Weise aktualisiert. Weitere Informationen: [Erstellen und Aktualisieren von Modellentitäten mit der Web-API](create-update-entity-definitions-using-web-api.md).  
  
<a name="bkmk_update"></a>

## <a name="basic-update"></a>Grundlegende Aktualisierung

Aktualisierungsoperationen verwenden das HTTP `PATCH`-Verb. Übergeben Sie ein JSON-Objekt, das die Eigenschaften enthält, die Sie auf den URI aktualisieren möchten, der die Entität darstellt. Eine Antwort mit einem Status von 204 wird zurückgebracht, wenn die Aktualisierung erfolgreich ist.  
  
 Dieses Beispiel aktualisiert einen vorhandenen Firmendatensatz mit dem `accountid`-Wert von 00000000-0000-0000-0000-000000000001.  
  
> [!IMPORTANT]
>  Wenn Sie eine Entität aktualisieren, schließen Sie im Anfragebody nur die Eigenschaften ein, die Sie ändern. Wenn Sie die Eigenschaften einer Entität einfach aktualisieren, die Sie vorher abgerufen hatten, und das JSON in Ihrer Anfrage einschließen, aktualisieren Sie damit jede Eigenschaft, obwohl der Wert derselbe ist. Dies kann Systemereignisse verursachen, die Geschäftslogik starten können, da angenommen wird, dass die Werte geändert haben. Dieses kann bewirken, dass Eigenschaften so aussehen, als seien sie beim Daten-Bearbeiten aktualisiert worden, wenn tatsächlich sie sich nicht wirklich geändert haben.

> [!NOTE] 
> Metadaten für Attribute enthält eine `RequiredLevel`-Eigenschaft. Falls das auf `SystemRequired` festgelegt ist, können Sie dieser Attribute auf einen NULL-Wert nicht festlegen. Weitere Informationen: [Attributerforderlichkeitsstufe](../entity-attribute-metadata.md#attribute-requirement-level)
  
 **Anforderung**

```http
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{  
    "name": "Updated Sample Account ",  
    "creditonhold": true,  
    "address1_latitude": 47.639583,  
    "description": "This is the updated description of the sample account",  
    "revenue": 6000000,  
    "accountcategorycode": 2  
}  
```  
  
 **Antwort**

```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
> [!NOTE]
>  Siehe [Entitäten beim Update zuordnen](associate-disassociate-entities-using-web-api.md#bkmk_Associateentitiesonupdate) für Informationen zum Zuordnen von Entitäten beim Update.  
  
<a name="bkmk_updateWithDataReturned"></a>

## <a name="update-with-data-returned"></a>Aktualisieren mit den zurückgegebenen Daten
  
Um Daten von einer Entität zu erhalten, die Sie aktualisieren, können Sie die `PATCH`-Anfrage so verfassen, dass die Daten des erstellten Datensatzes mit dem Status „200 (OK)” zurückgegeben werden.  Um dieses Ergebnis zu erzielen, müssen Sie die `return=representation`-Einstellung in den Anforderungsheadern verwenden.  
  
 Um die zurückgegebenen Eigenschaften zu steuern, hängen Sie die `$select`-Abfrageoption für die URL im Entitätssatz an.  Wenn sie verwendet wird, wird die `$expand`-Abfrageoption ignoriert.  
  
 In diesem Beispiel wird eine Firmaenentität aktualisiert und gibt die angeforderten Daten in der Antwort zurück.  
  
 **Anforderung**

```http
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=name,creditonhold,address1_latitude,description,revenue,accountcategorycode,createdon HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Accept: application/json  
Content-Type: application/json; charset=utf-8  
Prefer: return=representation  
  
{"name":"Updated Sample Account"}  
```  
  
 **Antwort** 
 
```http
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
Preference-Applied: return=representation  
OData-Version: 4.0  
  
{  
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",  
    "@odata.etag": "W/\"536537\"",  
    "accountid": "00000000-0000-0000-0000-000000000001",  
    "accountcategorycode": 1,  
    "description": "This is the description of the sample account",  
    "address1_latitude": 47.63958,  
    "creditonhold": false,  
    "name": "Updated Sample Account",  
    "createdon": "2016-09-28T23:14:00Z",  
    "revenue": 5000000.0000,  
    "_transactioncurrencyid_value": "048dddaa-6f7f-e611-80d3-00155db5e0b6"  
}  
  
```  
  
<a name="bkmk_updateSingleProperty"></a> 
  
## <a name="update-a-single-property-value"></a>Aktualisieren Sie einen einzelnen Eigenschaftswert  

Wenn Sie nur einen einzelnen Eigenschaftswert aktualisieren möchten, verwenden Sie eine PUT-Anfrage, bei der der Eigenschaftsname an den Uri der Entität angefügt wird.  
  
 Das folgende Beispiel aktualisiert die name-Eigenschaft einer vorhandenen Firmenentität mit dem `accountid`-Wert von 00000000-0000-0000-0000-000000000001.  
  
 **Anforderung**  

```http
PUT [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/name HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{"value": "Updated Sample Account Name"}  
```  
  
 **Antwort**

```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
<a name="bkmk_deleteSingleProperty"></a>

## <a name="delete-a-single-property-value"></a>Löschen Sie einen einzelnen Eigenschaftswert

Wenn Sie den Wert einer einzelnen Eigenschaft löschen möchten, verwenden Sie eine DELETE- Anfrage, bei der der Eigenschaftsname an den Uri der Entität angefügt wird.  
  
Das folgende Beispiel löscht den Wert der `description` Eigenschaft einer Firmenentität mit dem`accountid`-Wert von 00000000-0000-0000-0000-000000000001.  
  
 **Anforderung**

```http
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)/description HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**

```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
> [!NOTE]
>  Dies kann nicht bei einer Navigationseigenschaft mit einem einzelnen Wert verwendet werden, um zwei Entitäten zu distanzieren. Für eine andere Methode siehe [Entfernen Sie eine Referenz auf eine Entität](associate-disassociate-entities-using-web-api.md#bkmk_Removeareferencetoanentity).  
  
<a name="bkmk_upsert"></a>

## <a name="upsert-an-entity"></a>Upsert einer Entität

Eine *upsert* Operation ist genau wie eine Aktualisierung. Sie verwendet eine `PATCH`-Anfrage und verwendet einen URI, um sich auf eine spezifische Entität zu beziehen. Der Unterschied ist, dass, wenn die Entität nicht existiert, sie erstellt wird. Wenn sie bereits existiert, wird sie aktualisiert. Beim Erstellen einer neuen Entität lassen Sie vom System normalerweise einen eindeutigen Bezeichner zuweisen. Dies ist eine bewährte Methode. Wenn Sie jedoch einen Datensatz mit einem spezifischen `id`-Wert erstellen müssen, bietet `upsert` eine Operation, mit der dies möglich ist. Dieses kann in der Situation wertvoll sein, in der Sie Daten in den verschiedenen Systemen synchronisieren.  
  
Jedoch gibt es manchmal Situationen, in denen Sie ein `upsert` ausführen möchten, aber Sie möchten eine der potenziellen Standardaktionen verhindern: entweder Erstellen oder Update.      Sie können dies bewerkstelligen, indem Sie `If-Match` oder `If-None-Match` den Kopfzeilen hinzufügen. Für weitere Informationen siehe [upsert-Vorgänge begrenzen](perform-conditional-operations-using-web-api.md#bkmk_limitUpsertOperations).  
  
<a name="bkmk_delete"></a>
  
## <a name="basic-delete"></a>Grundlegende Löschung

Eine Löschungsoperation ist sehr direkt. Verwenden Sie das DELETE-Verb mit dem URI der Entität, die Sie löschen möchten. Diese Beispielmitteilung löscht eine Firmenentität mit dem Primärschlüssel `accountid`-Wert gleich 00000000-0000-0000-0000-000000000001.  
  
 **Anforderung**

```http
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**

 Wenn die Entität existiert, erhalten Sie eine normale Antwort mit Status 204, um anzuzeigen, dass die Löschung erfolgreich war. Wenn die Entität nicht gefunden wird, erhalten Sie eine Antwort mit Status 404.  
  
```http
HTTP/1.1 204 No Content  
OData-Version: 4.0  
```  

<a name="bkmk_duplicate"></a>

## <a name="check-for-duplicate-records"></a>Nach doppelten Datensätzen suchen

<!-- TODO:
By default, duplicate detection is suppressed when you are updating records using the Web API. You must include the `MSCRM.SuppressDuplicateDetection: false` header with your PATCH request to enable duplicate detection . Duplicate detection only applies when the organization has enabled duplicate detection, the entity is enabled for duplicate detection, and there are active duplicate detection rules being applied. For more information, see [Detect duplicate data for developers](../detect-duplicate-data-for-developers.md). -->

Sehen Sie [Erkennen Sie Duplikate beim Aktualisieren-Vorgang mit Internet-API](manage-duplicate-detection-create-update.md#bkmk_update), um weitere Informationen zu erhalten, wie Sie nach doppelten Datensätzen beim Aktualisierungsvorgang suchen können.

### <a name="see-also"></a>Siehe auch

[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)<br />
[Beispiele grundlegender Web API-Operationen (clientseitiges JavaScript)](samples/basic-operations-client-side-javascript.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)

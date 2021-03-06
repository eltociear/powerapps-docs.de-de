---
title: Ausführen bedingter Vorgänge mit der Web-API (Common Data Service) | Microsoft Docs
description: Lesen Sie, wie Sie Bedingungen erstellen, die bestimmen, ob und wie die Vorgänge mithilfe von Web-API ausgeführt werden
ms.custom: ''
ms.date: 04/06/2020
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 771002b0-825a-462d-bbf0-1aeba4b726c8
caps.latest.revision: 16
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: aa6d6827994749d48981144fd2deea0d1f839a83
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "3233750"
---
# <a name="perform-conditional-operations-using-the-web-api"></a>Bedingte Vorgänge mithilfe der Web-API ausführen

Common Data Service stellt Unterstützung für einen Satz bedingter Vorgänge bereit, die auf dem standardmäßigen HTTP-Ressourcen-Versionsverwaltungsmechanismus basieren, der als *ETags* bezeichnet wird.  
  
<a name="bkmk_ETags"></a>
  
## <a name="etags"></a>ETags

Das HTTP-Protokoll definiert einen *Entitätstag* oder kurz ausgedrückt [ETag](https://msdn.microsoft.com/library/dd541486.aspx), um spezifische Versionen einer Ressource zu identifizieren. ETag sind undurchsichtige Bezeichner, deren genauen Werte von der Implementierung abhängen. ETag-Werte treten in zwei Arten auf: starke und schwache Überprüfung. Eine starke Überprüfung gibt an, dass eine eindeutige Ressource, die durch eine spezfische URI identifziert ist, auf binärer Ebene identisch ist, wenn ihr entsprechender ETag-Wert unverändert ist. Eine schwache Überprüfung stellt nur sicher, dass die Ressourcendarstellung für denselben ETag-Wert semantisch gleichwertig ist.  
  
Common Data Service generiert eine schwache Überprüfungs-`@odata.etag`-Eigenschaft für jede Entitätsinstanz und diese Eigenschaft wird automatisch bei jedem abgerufenen Entitätsdatensatz zurückgegeben. Weitere Informationen finden Sie unter [Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md).  
  
<a name="bkmk_ifMatchHeaders"></a>
 
## <a name="if-match-and-if-none-match-headers"></a>"If-Match"- und "If-None-Match"-Kopfzeilen

Verwenden Sie [If-Match](https://tools.ietf.org/html/rfc7232#section-3.1) und [If-None-Match](https://tools.ietf.org/html/rfc7232#section-3.2)-Kopfzeilen mit ETag-Werten, um zu prüfen, ob die aktuelle Version einer Ressource mit der zuletzt abgerufenen Version, irgendeiner vorherigen Version oder mit keiner Version übereinstimmt.  Diese Vergleiche bilden die Grundlage bedingter Vorgangsunterstützung. Common Data Service stellt ETags bereit, um bedingte Abrufe, optimistische Parallelität und begrenzte upsert-Vorgänge zu unterstützen.
  
> [!WARNING]
> Der Clientcode sollte dem spezifischen Wert eines ETag keine Bedeutung geben, noch irgendeine offensichtliche Beziehung zwischen ETags außer Gleichheit und Ungleichheit. Beispielsweise wird nicht garantiert, dass ein ETag-Wert für eine aktuellere Version einer Ressource größer als der ETag-Wert für eine frühere Version ist. Außerdem kann der Algorithmus, der zum Generieren neuer ETag-Werte verwendet wird, ohne Vorankündigung zwischen Versionen eines Service geändert werden.  
  
<a name="bkmk_DetectIfChanged"></a>

## <a name="conditional-retrievals"></a>Bedingte Abrufe

ETags ermöglichen es Ihnen, jedes Mal Datensatzabrufe zu optimieren, wenn Sie auf denselben Datensatz mehrere Male zugreifen. Wenn Sie vorher einen Datensatz abgerufen haben, können Sie den ETag-Wert mit dem Header `If-None-Match` senden, damit Daten nur dann abgerufen werden, wenn sie sich seit dem letzten Abruf geändert haben. Wenn sich die Daten geändert haben, gibt die Anfrage einen HTTP-Status von 200 `200 (OK)` mit den neuesten Daten im Text der Anfrage zurück. Wenn sich die Daten nicht geändert haben, wird der HTTP-Statuscode `304 (Not Modified)` zurückgegeben, um anzuzeigen, dass die Entität nicht geändert wurde. 

Das folgende Beispielmeldungspaar gibt Daten für eine Kontoentität mit der `accountid` gleich `00000000-0000-0000-0000-000000000001` zurück, wenn sich die Daten seit dem letzten Abruf nicht geändert haben, als der Etag-Wert `W/"468026"` war

 **Anforderung**  
```http  
GET [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001)?$select=accountcategorycode,accountnumber,creditonhold,createdon,numberofemployees,name,revenue   HTTP/1.1  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-None-Match: W/"468026"  
```  
  
 **Antwort**  
```json  
HTTP/1.1 304 Not Modified  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
```  

In den folgenden Abschnitten werden Einschränkungen für die Verwendung von bedingten Abrufen beschrieben.

### <a name="entity-must-have-optimistic-concurrency-enabled"></a>Für die Entität muss die optimistische Parallelität aktiviert sein

Überprüfen Sie, ob für Entität die optimistische Parallelität aktiviert ist, indem Sie die unten gezeigte Web-API-Anforderung nutzen. Bei Entitäten mit aktivierter optimistischer Parallelität ist die <xref href="Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsOptimisticConcurrencyEnabled?text=EntityMetadata.IsOptimisticConcurrencyEnabled" />-Eigenschaft auf `true` festgelegt.

```http
GET [Organization URI]/api/data/v9.0/EntityDefinitions(LogicalName='<Entity Logical Name>')?$select=IsOptimisticConcurrencyEnabled
```

### <a name="query-must-not-include-expand"></a>Die Abfrage darf $ erweitern nicht enthalten

Das Etag kann nur feststellen, ob sich der einzelne Datensatz, der abgerufen wird, geändert hat. Wenn Sie `$expand` in Ihrer Abfrage verwenden, werden möglicherweise zusätzliche Datensätze zurückgegeben, und es kann nicht festgestellt werden, ob sich einer dieser Datensätze geändert hat. Wenn die Abfrage `$expand` enthält, wird `304 Not Modified` nie zurückgegeben.
  
<a name="bkmk_limitUpsertOperations"></a>
  
## <a name="limit-upsert-operations"></a>upsert-Vorgänge begrenzen

Ein Upsert funktioniert normalerweise durch die Erstellung einer Entität, falls diese noch nicht existiert; andernfalls wird eine bestehende Entität aktualisiert. Allerdings können ETags verwendet werden, um upserts weiter einzuschränken, um entweder Erstellungen oder Updates zu verhindern.  
  
<a name="bkmk_preventCreateOnUpsert"></a>
 
### <a name="prevent-create-in-upsert"></a>Erstellen im Upsert verhindern

Wenn Sie Daten aktualisieren und es irgendeine Möglichkeit gibt, dass die Entität absichtlich gelöscht wurde, möchten Sie die Entität nicht neu erstellen. Um dies zu verhindern, fügen Sie der Anfrage einen `If-Match`-Kopf mit dem Wert "*" hinzu.  
  
 **Anforderung**  
```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-Match: *  
  
{  
    "name": "Updated Sample Account ",  
    "creditonhold": true,  
    "address1_latitude": 47.639583,  
    "description": "This is the updated description of the sample account",  
    "revenue": 6000000,  
    "accountcategorycode": 2  
}  
```  
  
 **Response**  
 Wenn die Entität gefunden wird, erhalten Sie eine normale Antwort mit Status 204 (Kein Inhalt). Wenn die Entität nicht gefunden wird, erhalten Sie die folgende Antwort mit Status 404 (Not Found).  
  
```json  
HTTP/1.1 404 Not Found  
OData-Version: 4.0  
Content-Type: application/json; odata.metadata=minimal  
  
{  
 "error": {  
  "code": "",  
  "message": "account With Id = 00000000-0000-0000-0000-000000000001 Does Not Exist"
 }  
}  
```  
  
<a name="bkmk_preventUpdateInUpsert"></a>
  
### <a name="prevent-update-in-upsert"></a>Update im Upsert verhindern

Wenn Sie Daten einfügen, besteht die Möglichkeit, dass ein Datensatz mit dem gleichen Wert `id` bereits im System vorhanden ist und Sie ihn nicht aktualisieren möchten. Um dies zu verhindern, fügen Sie der Anfrage einen `If-None-Match`-Kopf mit dem Wert "*" hinzu.  
  
 **Anforderung**  
```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
Content-Type: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
If-None-Match: *  
  
{  
    "name": "Updated Sample Account ",  
    "creditonhold": true,  
    "address1_latitude": 47.639583,  
    "description": "This is the updated description of the sample account",  
    "revenue": 6000000,  
    "accountcategorycode": 2  
}  
```  
  
 **Response**  
 Wenn die Entität nicht gefunden wird, erhalten Sie eine normale Antwort mit Status 204 (Kein Inhalt). Wenn die Entität gefunden wird, erhalten Sie die folgende Antwort mit Status 412 (Precondition Failed).  
  
```json  
HTTP/1.1 412 Precondition Failed  
OData-Version: 4.0  
Content-Type: application/json; odata.metadata=minimal  
  
{  
  "error":{  
   "code":"",  
   "message":"A record with matching key values already exists."
  }  
}  
```  
  
<a name="bkmk_Applyoptimisticconcurrency"></a>

## <a name="apply-optimistic-concurrency"></a>Optimistische Parallelität anwenden

Sie können optimistische Gleichzeitigkeit verwenden, um zu ermitteln, ob eine Entität geändert worden ist, seit sie zuletzt abgerufen wurde. Wenn die Entität, die Sie aktualisieren oder löschen möchten, sich auf dem Server geändert hat, seit Sie sie abgerufen haben, sollten Sie nicht den Update- oder Löschvorgang abschließen. Durch das Anwenden des Musters, das hier gezeigt wird, können Sie diese Situation ermitteln, die neueste Version der Entität abrufen, und alle notwendigen Kriterien anwenden, um neu zu bewerten, ob man die Operation noch einmal versucht.  
  
<a name="bkmk_Applyoptimisticconcurrencyondelete"></a>

### <a name="apply-optimistic-concurrency-on-delete"></a>Wenden Sie optimistische Gleichzeitigkeit auf Löschung an

Die folgende Löschanfrage für ein Konto mit `accountid` von`00000000-0000-0000-0000-000000000001` schlägt fehl, weil der ETag-Wert, der mit dem `If-Match`-Header gesendet wurde, sich vom aktuellen Wert unterscheidet. Wenn der Wert zusammengepasst hätte, wird ein Status 204 (Kein Inhalt) erwartet.  
  
 **Anforderung**

```http  
DELETE [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
If-Match: W/"470867"  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
```  
  
 **Antwort**

```json  
HTTP/1.1 412 Precondition Failed  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "error":{  
    "code":"","message":"The version of the existing record doesn't match the RowVersion property provided." 
  }  
}  
```  
  
<a name="bkmk_Applyoptimisticconcurrencyonupdate"></a>

### <a name="apply-optimistic-concurrency-on-update"></a>Wenden Sie optimistische Gleichzeitigkeit auf Aktualisierung an

Die folgende Aktualisierungsanfrage für ein Konto mit `accountid` von `00000000-0000-0000-0000-000000000001` schlägt fehl, weil der ETag-Wert, der mit dem `If-Match`-Header gesendet wurde, sich vom aktuellen Wert unterscheidet. Wenn der Wert zusammengepasst hätte, wird ein Status 204 (Kein Inhalt) erwartet.  
  
 **Anforderung**

```http  
PATCH [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000001) HTTP/1.1  
If-Match: W/"470867"  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
{"name":"Updated Account Name"}  
```  
  
 **Antwort**

```json  
HTTP/1.1 412 Precondition Failed  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "error":{  
    "code":"","message":"The version of the existing record doesn't match the RowVersion property provided."
  }  
}  
```  
  
### <a name="see-also"></a>Siehe auch

[Beispiel bedingter Web-API-Operationen (C#)](samples/conditional-operations-csharp.md)<br />
[Beispiele bedingter Web API-Operationen (clientseitiges JavaScript)](samples/conditional-operations-client-side-javascript.md)<br />
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)

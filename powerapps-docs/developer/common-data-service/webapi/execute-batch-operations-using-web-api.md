---
title: Stapelvorgänge mithilfe von der Web-API ausführen (Common Data Service für Apps) | Microsoft Docs
description: Mit Batchvorgängen können Sie mehrere Vorgänge in einer einzigen HTTPS-Anforderung gruppieren. Infos zum Ausführen von Batchbetrieben mithilfe der Web-API
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 799b2346-bda1-4a26-a330-79d0927a7743
caps.latest.revision: 11
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="execute-batch-operations-using-the-web-api"></a>Ausführen von Batchbetrieben mithilfe der Web-API

Sie können mehrere Vorgänge in einer einzelnen HTTP-Anforderung gruppieren mithilfe des Batchvorgangs.  
  
<a name="bkmk_Whentousebatchrequests"></a>

## <a name="when-to-use-batch-requests"></a>Verwenden der Batchanforderungen

Der Wert, den Stapelverarbeitungsanfragen bieten, ist, dass sie Änderungssätze umfassen können, die eine Weise liefern, einige Operationen zusammenzufassen, die als Gruppe entweder erfolgreich durchgeführt werden oder scheitern. Verglichen mit anderen Operationen, die unter Verwendung der Web-API durchgeführt werden können, sind sie schwieriger zu verfassen ohne irgendein Objektmodell, das Serialisierung von Objekten oder ein tieferes Verständnis des HTTPS-Protokolls umfasst, weil der Anfragekörper im Wesentlichen ein Textdokument ist, das sehr spezifische Anforderungen erfüllen muss.  
  
Beachten Sie, dass zugeordnete Entitäten leichter in einem einzelnen Vorgang erstellt werden können als in einer Batchanforderung. Batchanforderungen werden am besten verwendet, wenn Sie Vorgänge an Entitäten ausführen, die nicht die einander zugeordnet sind, wenn alle Vorgänge in einem einzigen Transaktionsvorgang ausgeführt werden müssen.  
  
Auch die zurückgegebenen Antworten sind im Wesentlichen Textdateien und nicht Objekte, die in JSON einfach analysiert werden können. Sie müssen den Text in der Antwort analsieren oder eine Hilfsbibliothek finden, um auf Daten in der Antwort zuzugreifen.  
 
>[!NOTE]
>  Batchanforderung kann bis zu 100 einzelne Anforderungen enthalten und kann keine anderen Batchanforderungen enthalten.  
  
<a name="bkmk_BatchRequests"></a> 

## <a name="batch-requests"></a>Batchanforderungen

Nutzen Sie eine POST-Anfrage, um eine Batch-Operation zu senden, die mehrere Anforderungen enthält. Eine Batchanforderung kann GET-Anforderungen und Änderungsätze enthalten. Um die Transaktionsfunktionen von Anforderungen für Stapelverarbeitung verwenden zu können, dürfen nur Vorgänge die Daten ändern in einem Changesets berücksichtigt werden. GET-Anfragen dürfen nicht im Änderungssatz eingeschlossen sein.  
  
Die POST Batchanforderung müssen eine Inhaltstyp-Kopfzeile mit einem Wert besitzen, der auf mehrteilig/gemischt festgelegt ist, mit einer Grenze, die so eingerichtet ist, dass sie den Bezeichner des Änderungssets mithilfe dieses Musters einbezieht:  
  
```  
--batch_<unique identifier>  
```  
  
Die eindeutige Kennung muss kein GUID sein, aber einzigartig. Jedem Element im Batch muss der Batchbezeichner vorausgehen mit einer Inhaltstyp und Inhaltstransferkodierung-Kopfzeile wie der Folgenden:  
  
```  
--batch_WKQS9Yui9r  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
```  
  
Das Batchende muss einen Indikator für das Beenden wie den folgenden enthalten:  
  
```  
--batch_WKQS9Yui9r--  
```   
  
<a name="bkmk_ChangeSets"></a>

## <a name="change-sets"></a>Änderungssätze

Wenn mehrere Vorgänge in einem Changeset enthalten sind, gelten alle Vorgänge gelten als unteilbar. Das bedeutet, dass bei einem Fehlerschlag einer der folgenden Vorgänge alle abgeschlossenen Vorgänge rückgängig gemacht werden. Wie eine Batchanforderung müssen Änderungssets eine Inhaltstyp-Kopfzeile mit einem Wert besitzen, der auf mehrteilig/gemischt festgelegt ist, mit einer Grenze, die so eingerichtet ist, dass sie den Bezeichner des Änderungssets mithilfe dieses Musters einbezieht:  
  
```  
--changeset_<unique identifier>  
```  
  
Die eindeutige Kennung muss kein GUID sein, aber einzigartig. Jedem Element im Änderungssatz muss der Änderungssatzbezeichner vorausgehen mit einer Inhaltstyp und Inhaltstransferkodierung-Kopfzeile wie der Folgenden:  
  
```  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
```  
  
Änderungssätze können eine auch eine Inhalts-ID-Kopfzeile mit einem eindeutigen Wert enthalten. Wenn diesem Wert `$` vorangestellt wird, stellt er eine Variable dar, die eine URI für eine beliebige Entität in diesem Vorgang erhält. Wenn Sie z. B. den Wert auf 1 festlegen, können Sie über `$1` später auf diese Entität zurückgreifen.  
  
Das Ende des Änderungssatzes muss einen Indikator für das Beenden wie den folgenden enthalten:  
  
```  
--changeset_BBB456--  
```  
  
<a name="bkmk_Example"></a>

## <a name="example"></a>Beispiel

Das folgende Beispiel enthält einen Batch mit einem eindeutigen Bezeichner von AAA123 und einen Änderungssatz mit einem eindeutigen Bezeichner von BBB456.  
  
Innerhalb des Änderungssatzes werden zwei Aufgaben mithilfe von POST erstellt und einem vorhandenen Konto mit accountid = 00000000-0000-0000-000000000001 zugeordnet.  
  
Und schließlich ist eine GET-Anforderung außerhalb des Änderungssatzes enthalten, um alle sechs Aufgaben zu diesem Konto wiederzugeben, einschließlich der beiden, die in der Batchanforderung erstellt wurden.  
  
 **Anforderung**

```http 
POST[Organization URI]/api/data/v9.0/$batch HTTP/1.1  
Content-Type: multipart/mixed;boundary=batch_AAA123  
Accept: application/json  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
  
--batch_AAA123  
Content-Type: multipart/mixed;boundary=changeset_BBB456  
  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
Content-ID: 1  
  
POST[Organization URI]/api/data/v9.0/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 1 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
Content-ID: 2  
  
POST[Organization URI]/api/data/v9.0/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 2 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456--  
  
--batch_AAA123  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
  
GET[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)/Account_Tasks?$select=subject HTTP/1.1  
Accept: application/json  
  
--batch_AAA123--  
```  
  
 **Antwort**

```http 
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f  
Content-Type: multipart/mixed; boundary=changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
Content-ID: 1  
  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
Location:[Organization URI]/api/data/v9.0/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.0/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
Content-ID: 2  
  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
Location:[Organization URI]/api/data/v9.0/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.0/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc--  
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#tasks(subject)","value":[  
    {  
      "@odata.etag":"W/\"474122\"","subject":"Task Created with Test Account","activityid":"919c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474125\"","subject":"Task 1","activityid":"a29c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474128\"","subject":"Task 2","activityid":"a39c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474131\"","subject":"Task 3","activityid":"a49c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474134\"","subject":"Task 1 in batch","activityid":"a59c24f3-fafc-e411-80dd-00155d2a68cb"  
    },{  
      "@odata.etag":"W/\"474137\"","subject":"Task 2 in batch","activityid":"a69c24f3-fafc-e411-80dd-00155d2a68cb"  
    }  
  ]  
}  
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f--  
```  
Fügen Sie `odata.include-annotations` Einstellungskopfzeile mit den `GET` Anforderungen und setzen Sie den zugehörigen Wert auf " *" fest, um anzugeben, dass sämtliche Anmerkungen, die zu den Eigenschaften gehören, zurückgegeben werden.

```HTTP
--batch_AAA123  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
  
GET[Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-000000000001)?$select=name,telephone1,emailaddress1,shippingmethodcode,customersizecode,accountratingcode,followemail,donotemail,donotphone,statuscode HTTP/1.1  
Accept: application/json  
Prefer: odata.include-annotations="*"
  
--batch_AAA123-- 
```
Weitere Informationen zu den Präferenzen für Einstellungskopfzeilen finden Sie unter [Einstellungskopfzeilen](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752234).

### <a name="see-also"></a>Siehe auch

[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)

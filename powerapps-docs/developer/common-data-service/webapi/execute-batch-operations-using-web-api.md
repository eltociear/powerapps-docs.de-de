---
title: Ausführen von Batchvorgängen mit der Web-API (Common Data Service) | Microsoft Docs
description: Mit Batchvorgängen können Sie mehrere Vorgänge in einer einzigen HTTPS-Anforderung gruppieren. Infos zum Ausführen von Batchbetrieben mithilfe der Web-API
ms.custom: ''
ms.date: 07/13/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 799b2346-bda1-4a26-a330-79d0927a7743
caps.latest.revision: 11
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4029b07d07505d15f216279edbfc774026463a4f
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753698"
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
POST[Organization URI]/api/data/v9.1/$batch HTTP/1.1  
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
  
POST[Organization URI]/api/data/v9.1/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 1 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
Content-ID: 2  
  
POST[Organization URI]/api/data/v9.1/tasks HTTP/1.1  
Content-Type: application/json;type=entry  
  
{"subject":"Task 2 in batch","regardingobjectid_account_task@odata.bind":"[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)"}  
--changeset_BBB456--  
  
--batch_AAA123  
Content-Type: application/http  
Content-Transfer-Encoding:binary  
  
GET[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)/Account_Tasks?$select=subject HTTP/1.1  
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
Location:[Organization URI]/api/data/v9.1/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.1/tasks(a59c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
Content-ID: 2  
  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
Location:[Organization URI]/api/data/v9.1/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
OData-EntityId:[Organization URI]/api/data/v9.1/tasks(a69c24f3-fafc-e411-80dd-00155d2a68cb)  
  
--changesetresponse_ff83b4f1-ab48-430c-b81c-926a2c596abc--  
--batchresponse_c1bd45c1-dd81-470d-b897-e965846aad2f  
Content-Type: application/http  
Content-Transfer-Encoding: binary  
  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
  
{  
  "@odata.context":"[Organization URI]/api/data/v9.1/$metadata#tasks(subject)","value":[  
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
  
GET[Organization URI]/api/data/v9.1/accounts(00000000-0000-0000-000000000001)?$select=name,telephone1,emailaddress1,shippingmethodcode,customersizecode,accountratingcode,followemail,donotemail,donotphone,statuscode HTTP/1.1  
Accept: application/json  
Prefer: odata.include-annotations="*"
  
--batch_AAA123-- 
```
Weitere Informationen zu den Präferenzen für Einstellungskopfzeilen finden Sie unter [Einstellungskopfzeilen](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752234).

## <a name="reference-uris-in-an-operation"></a>Verweis-URIs in einem Vorgang

Sie können `$parameter` wie `$1`, `$2` usw. verwenden, um auf URIs zu verweisen, die in einem frühreren Changeset in einer Batchanfrage verwendet wurden. In diesem Abschnitt werden verschiedene Beispiele dazu aufgeführt, wie `$parameter` im Anforderungstext eines Batchvorgangs verwendet werden kann, um auf URIs zu verweisen.

### <a name="reference-uris-in-request-body"></a>Verweis-URIs im Anforderungstext

Das untengenannte Beispiel veranschaulicht, wie URI-Verweise in einem einzelnen Vorgang verwendet werden können.

**Anforderung**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:  multipart/mixed;boundary=batch_AAA123
Accept:  application/json
OData-MaxVersion:  4.0
OData-Version:  4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

POST [Organization URI]/api/data/v9.1/leads HTTP/1.1
Content-Type: application/json

{
    "firstname":"aaa",
    "lastname":"bbb"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type: application/json

{"@odata.type":"Microsoft.Dynamics.CRM.contact","firstname":"Oncall Contact-1111"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
Content-Type: application/json

{
    "name":"IcM Account",
    "originatingleadid@odata.bind":"$1",
    "primarycontactid@odata.bind":"$2"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```

**Antwort**

```http
200 OK

--batchresponse_3cace264-86ea-40fe-83d3-954b336c0f4a
Content-Type: multipart/mixed; boundary=changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/leads(425195a4-7a75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/leads(425195a4-7a75-e911-a97a-000d3a34a1bd)

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/contacts(495195a4-7a75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/contacts(495195a4-7a75-e911-a97a-000d3a34a1bd)

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/accounts(4f5195a4-7a75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/accounts(4f5195a4-7a75-e911-a97a-000d3a34a1bd)

--changesetresponse_1a5db8a1-ec98-42c4-81f6-6bc6adcfa4bc--
--batchresponse_3cace264-86ea-40fe-83d3-954b336c0f4a--
```

### <a name="reference-uri-in-request-url"></a>Verweis-URI in der Anforderungs-URL

Das folgende Beispiel zeigt, wie Sie mit `$1` auf einen URI in der URL einer nachfolgenden Anforderung verweisen können.

**Anforderung**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:  multipart/mixed;boundary=batch_AAA123
Accept:  application/json
OData-MaxVersion:  4.0
OData-Version:  4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type: application/json

{
  "@odata.type":"Microsoft.Dynamics.CRM.contact",
  "firstname":"Contact",
  "lastname":"AAAAAA"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Transfer-Encoding: binary
Content-Type: application/http
Content-ID: 2

PUT $1/lastname HTTP/1.1
Content-Type: application/json

{
  "value":"BBBBB"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```

**Antwort**

```http
200 OK

--batchresponse_2cb48f48-39a8-41ea-aa52-132fa8ab3c2d
Content-Type: multipart/mixed; boundary=changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4

--changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location:[Organization URI]/api/data/v9.1/contacts(f8ea5d2c-8c75-e911-a97a-000d3a34a1bd)
OData-EntityId:[Organization URI]/api/data/v9.1/contacts(f8ea5d2c-8c75-e911-a97a-000d3a34a1bd)


--changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0


--changesetresponse_d7528170-3ef3-41bd-be8e-eac971a8d9d4--
--batchresponse_2cb48f48-39a8-41ea-aa52-132fa8ab3c2d--
```

### <a name="reference-uris-in-url-and-request-body-using-odataid"></a>Verweis-URIs in der URL und im Anforderungstext unter Verwendung von @odata.id

Das nachfolgende Beispiel zeigt, wie Sie einen Kontaktentitätsdatensatz mit einem Firmenentitätsdatensatz verknüpfen. Auf den URI des Firmenentitätsdatensatzes wird als `$1` verwiesen und auf den URI des Kontaktentitätsdatensatzes wird als `$2` verwiesen.

**Anforderung**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:multipart/mixed;boundary=batch_AAA123
Accept:application/json
OData-MaxVersion:4.0
OData-Version:4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type:application/http
Content-Transfer-Encoding:binary
Content-ID:1

POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
Content-Type: application/json

{"@odata.type":"Microsoft.Dynamics.CRM.account","name":"IcM Account"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type:application/http
Content-Transfer-Encoding:binary
Content-ID:2

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type:application/json

{"@odata.type":"Microsoft.Dynamics.CRM.contact","firstname":"Oncall Contact"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type:application/http
Content-Transfer-Encoding:binary
Content-ID:3

PUT $1/primarycontactid/$ref HTTP/1.1
Content-Type:application/json

{"@odata.id":"$2"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```

**Antwort**

```http
200 OK

--batchresponse_0740a25c-d8e1-41a5-9202-1b50a297864c
Content-Type: multipart/mixed; boundary=changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location:[Organization URI]/api/data/v9.1/accounts(3dcf8c02-8c75-e911-a97a-000d3a34a1bd)
OData-EntityId:[Organization URI]/api/data/v9.1/accounts(3dcf8c02-8c75-e911-a97a-000d3a34a1bd)

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0
Location:[Organization URI]/api/data/v9.1/contacts(43cf8c02-8c75-e911-a97a-000d3a34a1bd)
OData-EntityId:[Organization URI]/api/data/v9.1/contacts(43cf8c02-8c75-e911-a97a-000d3a34a1bd)

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

HTTP/1.1 204 No Content
OData-Version: 4.0

--changesetresponse_19ca0da8-d8bb-4273-a3f7-fe0d0fadfe5f--
--batchresponse_0740a25c-d8e1-41a5-9202-1b50a297864c--
```

### <a name="reference-uris-in-url-and-navigation-properties"></a>Verweis-URIs in der URL und Navigationseigenschaften

Das nachfolgende Beispiel zeigt, wie der Organisations-URI eines Kontaktdatensatzes verwendet wird und wie er unter Verwendung der einzelwertigen Navigationseigenschaft `primarycontactid` mit einem Firmendatensatz verknüpft wird. Auf den URI des Firmenentitätsdatensatzes wird als `$1` verwiesen und auf den URI des Kontaktentitätsdatensatzes wird als `$2` verwiesen in der Anforderung `PATCH`.

**Anforderung**

```http
POST [Organization URI]/api/data/v9.1/$batch HTTP/1.1
Content-Type:multipart/mixed;boundary=batch_AAA123
Accept:application/json
OData-MaxVersion:4.0
OData-Version:4.0

--batch_AAA123
Content-Type: multipart/mixed; boundary=changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
Content-Type: application/json

{"@odata.type":"Microsoft.Dynamics.CRM.account","name":"IcM Account"}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

POST [Organization URI]/api/data/v9.1/contacts HTTP/1.1
Content-Type: application/json

{
  "@odata.type":"Microsoft.Dynamics.CRM.contact",
  "firstname":"Oncall Contact"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

PATCH $1 HTTP/1.1
Content-Type: application/json

{
  "primarycontactid@odata.bind":"$2"
}

--changeset_dd81ccab-11ce-4d57-b91d-12c4e25c3cab--
--batch_AAA123--
```
**Antwort**

```http
200 OK

--batchresponse_9595d3ae-48f6-414f-a3aa-a3a33559859e
Content-Type: multipart/mixed; boundary=changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 2

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/contacts(6ed81853-7b75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/contacts(6ed81853-7b75-e911-a97a-000d3a34a1bd)

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 3

HTTP/1.1 204 No Content
OData-Version: 4.0
Location: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)
OData-EntityId: [Organization URI]/api/data/v9.1/accounts(6cd81853-7b75-e911-a97a-000d3a34a1bd)

--changesetresponse_0c1567a5-ad0d-48fa-b81d-e6db05cad01c--
--batchresponse_9595d3ae-48f6-414f-a3aa-a3a33559859e--
```

> [!NOTE]
> Wenn auf eine Inhalts-ID verwiesen wird, bevor sie im Anforderungstext deklariert worden ist, wird der Fehler **HTTP 400** ungültige Anforderung ausgegeben.
>
> Das Beispiel, das unten angegeben ist, zeigt Anforderungstext an, der diesen Fehler verursachen kann.
> 
> **Anforderungstext**
> 
> ```http
> --batch_AAA123
> Content-Type: multipart/mixed; boundary=changeset_BBB456
> 
> --changeset_BBB456
> Content-Type: application/http
> Content-Transfer-Encoding:binary
> Content-ID: 2
> 
> POST [Organization URI]/api/data/v9.1/phonecalls HTTP/1.1
> Content-Type: application/json;type=entry
> 
> {
>     "phonenumber":"911",
>     "regardingobjectid_account_phonecall@odata.bind" : "$1"
> }
> 
> --changeset_BBB456
> Content-Type: application/http
> Content-Transfer-Encoding:binary
> Content-ID: 1
> 
> POST [Organization URI]/api/data/v9.1/accounts HTTP/1.1
> Content-Type: application/json;type=entry
> 
> {
>     "name":"QQQQ",
>     "revenue": 1.50
> }
> 
> --changeset_BBB456--
> --batch_AAA123--
> ```
>
> **Antwort**
> 
> ```http
> HTTP 400 Bad Request
> Content-ID Reference: '$1' does not exist in the batch context.
> ```

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

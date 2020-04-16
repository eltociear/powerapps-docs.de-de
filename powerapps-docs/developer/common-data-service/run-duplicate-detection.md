---
title: Duplikaterkennung ausführen (Common Data Service) | Microsoft-Dokumentation
description: Führen Sie die Duplikaterkennung für einen bestimmten, ausgewählten Entitätstyp Datensatz aus, beim Erstellen oder während der Aktualisierungsvorgänge.
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: mayadumesh
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 42aea9a1348cd7cbda2ce66f2819b34795064121
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155326"
---
# <a name="run-duplicate-detection"></a>Duplikaterkennung ausführen

Es gibt mehrere Möglichkeiten, Duplikaterkennung auszuführen, nachdem Sie sie aktiviert und die Duplikaterkennungsregeln veröffentlicht haben.  

<a name="BKMK_RetDupwebapi"></a>

## <a name="retrieve-and-detect-duplicates-for-a-specified-record"></a>Erkennt und ruft Duplikate für einen bestimmten Datensatz ab.

Suchen und Abrufen von Duplikaten:

- Bevor Sie eine Entität erstellen
- Für eine vorhandene Entität
- Für andere Entitäten, die den Duplikat-Regeln über Entitäten hinweg entsprechen. Beispielsweise eine Entität Lead, die einer Kontaktentität entspricht.

### <a name="options"></a>Optionen:

- Web-API: <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates Function" />
- Organisationsdienst: <xref:Microsoft.Crm.Sdk.Messages.RetrieveDuplicatesRequest>


### <a name="example-detect-duplicates-for-a-specified-record-using-web-api"></a>Beispiel: Duplikate erkennen für einen bestimmten Datensatz mithilfe von Internet-API

Im folgenden Beispiel wird veranschaulicht, wie Duplikate eines bestimmten Datensatzes mit `RetrieveDuplicates` erkannt werden.

**Anforderung**
```http
GET [Organization URI]/api/data/v9.0/RetrieveDuplicates(BusinessEntity=@p1,MatchingEntityName=@p2,PagingInfo=@p3)?@p1={'@odata.type':'Microsoft.Dynamics.CRM.account','accountid':'0d1156d2-1598-e711-80e8-00155db64062'}&@p2='account'&@p3={'PageNumber':1,'Count':50} HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
```
**Antwort**
```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts",
    "value": [
        <Omitted for brevity: JSON data for any matching accounts including all properties>
    ]
}
```

<a name="BKMK_DupEntwebapi"></a>

## <a name="detect-duplicates-for-an-entity-type"></a>Erkennen von Duplikaten für einen Entitätstyp

Einen asynchronen Duplikaterkennungsauftrag übermitteln, der im Hintergrund ausgeführt wird. Die Duplikate werden in Übereinstimmung mit den veröffentlichten Regeln für doppelten den Entitätstyp erkannt. Die erkannten Duplikate sind als `DuplicateRecord` Datensätze in Dynamics 365 gespeichert. 

Maximal 5000 Duplikate werden durch den Duplikaterkennungsauftrag zurückgegeben.

### <a name="options"></a>Optionen

- Web-API: <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates Action" />
- Organisationsdienst: <xref:Microsoft.Crm.Sdk.Messages.BulkDetectDuplicatesRequest>

### <a name="example-detect-duplicates-for-an-entity-type-using-the-web-api"></a>Beispiel: Duplikate erkennen für einen Entitätstyp mit Internet-API 

Im folgenden Beispiel wird veranschaulicht, wie Duplikate für einen Entitätstyp erkennt werden, indem ein asynchroner Auftrag mithilfe der Aktion `BulkDetectDuplicates` erstellt wird.

**Anforderung**
```http
POST [Organization URI]/api/data/v9.0/BulkDetectDuplicates HTTP/1.1
If-None-Match: null
OData-Version: 4.0
Content-Type: application/json
Accept: application/json
OData-MaxVersion: 4.0

{
    "Query": {
        "@odata.type": "#Microsoft.Dynamics.CRM.QueryExpression",
        "EntityName": "lead"
    },
    "JobName": "jobname1",
    "SendEmailNotification": false,
    "TemplateId": "07B94C1D-C85F-492F-B120-F0A743C540E6",
    "ToRecipients": [],
    "CCRecipients": [],
    "RecurrencePattern": "",
    "RecurrenceStartTime": "2015-07-15T05:30:00Z"
}  
```
**Antwort**
```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.BulkDetectDuplicatesResponse",
    "JobId": "efaff068-7598-e711-80e8-00155db64062"
}
```
Die oben aufgeführte Anforderung erstellt einen asynchronen Duplikaterkennungsauftrag, dessen JobID in der Antwort wird wieder angezeigt. Die JobID, die von der oben Anforderung zurückgegeben wurde, kann verwendet werden, um doppelte Datensätze zu erkennen in einem Entitätstyp, wie im Beispiel angezeigt wird.

**Anforderung**
```http
GET [Organization URI]/api/data/v9.0/asyncoperations(efaff068-7598-e711-80e8-00155db64062)/AsyncOperation_DuplicateBaseRecord
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
```
Die FetchXML-Entsprechung der oben aufgeführte Anforderung wird unten gezeigt.

```xml
<fetch>
    <entity name="duplicaterecord">
        <attribute name="owninguser" />
        <attribute name="ownerid" />
        <attribute name="baserecordid" />
        <attribute name="duplicateid" />
        <attribute name="owningbusinessunit" />
        <attribute name="createdon" />
        <attribute name="asyncoperationid" />
        <filter>
            <condition attribute="asyncoperationid" operator="eq" value="efaff068-7598-e711-80e8-00155db64062" />
        </filter>
    </entity>
</fetch>
```

**Antwort**
```json
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0

{  
   "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#duplicaterecords",
   "value":[  
      {  
         "owninguser":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_ownerid_value":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_baserecordid_value":"3a6fc65b-3f9c-e711-811c-000d3a75ce72",
         "duplicateid":"489a879c-019b-4c28-8539-51ebc850d18f",
         "createdon":"2017-09-19T03:34:25Z",
         "owningbusinessunit":"20a44144-6d9a-e711-811c-000d3a75ce72",
         "_asyncoperationid_value":"efaff068-7598-e711-80e8-00155db64062",
         "_duplicateruleid_value":null,
         "_duplicaterecordid_value":null
      },
      {  
         "owninguser":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_ownerid_value":"b3ac4144-6d9a-e711-811c-000d3a75ce72",
         "_baserecordid_value":"406fc65b-3f9c-e711-811c-000d3a75ce72",
         "duplicateid":"0a4a7dea-1488-4e05-b5eb-c2925ad2925a",
         "createdon":"2017-09-19T03:34:25Z",
         "owningbusinessunit":"20a44144-6d9a-e711-811c-000d3a75ce72",
         "_asyncoperationid_value":"efaff068-7598-e711-80e8-00155db64062",
         "_duplicateruleid_value":null,
         "_duplicaterecordid_value":null
      }
   ]
}
```
Die GUID des Basis-Datensatzes wird als `baserecordid` in Datensätzen `DuplicateRecord` gespeichert. `duplicateid`, in den oben genannten Antwort ist der eindeutige Bezeichner des doppelten Datensatzes. `asyncoperationid` ist der eindeutige Bezeichner des Systemauftrags, von dem dieser Datensatz erstellt wurde. Die, `ownerid` ist der eindeutige Bezeichner des Benutzers oder eines Teams, dem der doppelte Datensatz gehört. Weitere Informationen finden Sie unter [DuplicateRecord-Entität](reference/entities/duplicaterecord.md).

> [!NOTE]
>  Bevor Sie Duplikaterkennungsaufträge erstellen und ausführen, stellen Sie sicher, dass die entsprechenden Duplikaterkennungsregeln vorhanden sind. Dynamics 365 enthält standardmäßige Duplikaterkennungsregeln für Firmen, Kontakte und Leads, jedoch nicht für andere Datensatztypen. Wenn Sie das System von Duplikate für andere Datensatztypen erkennen soll, müssen Sie eine neue Regel erstellen. Weitere Informationen darüber, wie eine Duplikaterkennungsregel erstellt wird, siehe [Duplikaterkennungsregeln](/dynamics365/customer-engagement/admin/set-up-duplicate-detection-rules-keep-data-clean).

<a name="BKMK_CRwebapi"></a>

## <a name="detect-duplicates-during-create-and-update-operations"></a>Duplikate erkennen bei Erstellungs- und Aktualisierungsvorgängen

Duplikaterkennung beim Erstellen oder Aktualisieren von Datensätzen gilt nur, wenn in der Organisation die Duplikaterkennung aktiviert ist, die Entität für Duplikaterkennung aktiviert ist, und aktive Duplikaterkennungsregeln angewendet werden. Standardmäßig wird die Duplikaterkennung unterdrückt, wenn Sie Datensätze mithilfe der Web-API oder dem Organisationsservice erstellen oder aktualisieren. 

Um beim Erstellen oder Aktualisieren von Datensätzen doppelte Daten zu erkennen, siehe:

- WebAPI: [Erkennen von doppelten Daten mit der Web-API](webapi/manage-duplicate-detection-create-update.md)
- Organisationsservice: [Erkennen von doppelten Daten mit dem Organisationsservice](org-service/detect-duplicate-data.md)

  
### <a name="see-also"></a>Siehe auch  
 [Duplikaterkennungsmeldungen](duplicate-detection-messages.md)

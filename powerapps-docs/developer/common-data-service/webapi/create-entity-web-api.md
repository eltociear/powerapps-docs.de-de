---
title: Erstellen eines Entitätsdatensatzes mit der Web-API (Common Data Service) | Microsoft-Dokumentation
description: Lesen Sie, wie Sie eine POST-Anforderung erstellen, um Daten zu senden, um einen Entitätsdatensatz auf Common Data Service mithilfe der Web-API zu erstellen
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 244259ca-2fbc-4fd4-9a74-6166e6683355
caps.latest.revision: 51
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
manager: annbe
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3db4826ca9e08672e8dddd9736a35dad3475fb06
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155114"
---
# <a name="create-an-entity-record-using-the-web-api"></a>Abrufen eines Entitätsdatensatzes mit der Web-API

Nutzen Sie eine POST-Anfrage, um eine Daten zum Erstellen einer Entität zu senden. Sie können mehrere verknüpfte Entitätsdatensätze in einem einzelnen Vorgang erstellten, indem Sie die 'tiefe Einfügung' nutzen. Sie müssen auch damit vertraut sein, wie Sie Werte festlegen, um einen neuen Entitätsdatensatz mit vorhandenen Entitäten mithilfe der @odata.bind-Anmerkung zuzuordnen.  

> [!NOTE]
> Informationen dazu, wie Sie Entitätsmetadaten mit der Internet-API erstellen und aktualisieren, siehe [Erstellen und Aktualisieren von Entitätsdefinitionen mithilfe der Internet-API](create-update-entity-definitions-using-web-api.md).

<a name="bkmk_basicCreate"></a>

## <a name="basic-create"></a>Grundlegende Erstellung

 In diesem Beispiel wird ein neuer Kontoentitätsdatensatz erstellt. Der `OData-EntityId`-Antwortheader enthält die URI der erstellten Entität.

 **Anforderung**

```http

POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
    "name": "Sample Account",
    "creditonhold": false,
    "address1_latitude": 47.639583,
    "description": "This is the description of the sample account",
    "revenue": 5000000,
    "accountcategorycode": 1
}
```

 **Antwort**

```http

HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(7eb682f1-ca75-e511-80d4-00155d2a68d1)

```

Zum Erstellen eines neuen Entitätsdatensatzes müssen Sie die passenden Eigenschaftennamen und -arten ermitteln. Für alle Systementitäten und Attribute können Sie diese Informationen im Thema für diese Entität unter [Über die Entitätsreferenz](../reference/about-entity-reference.md) finden. Informationen zu benutzerdefinierten Entitäten oder Attributen finden Sie in der Definition der Entität im [CSDL $metadata document](web-api-types-operations.md#csdl-metadata-document). Weitere Informationen:[Entitätstypen](web-api-types-operations.md#entity-types)

<a name="bkmk_CreateRelated"></a>

## <a name="create-related-entity-records-in-one-operation"></a>Erstellen verknüpfter Entitätsdatensätze in einem Vorgang

 Sie können die Entitäten, die miteinander verknüpft werden, indem Sie sie als Navigationseigenschaftenwerte definieren. Dies ist bekannt als *tiefe Einfügung*.

 Wie bei einem grundlegenden Erstellen enthält die Antwort `OData-EntityId` Kopfzeile die URI der erstellten Entität. Die für die erstellten URI verknüpften Entitäten werden nicht zurückgegeben.

 Beispielsweise erstellt der folgenden Anforderungstext, der mit der `Account`-Entität veröffentlicht wurde, insgesamt vier neue Entitäten beim Erstellen eines Kontos.

- Ein Kontakt wird erstellt, da er als eine Objekteigenschaft der einwertigen Navigationseigenschaft `primarycontactid` definiert ist.

- Eine Verkaufschance wird erstellt, da sie als Objekt in einem Arrays definiert ist, das auf den Wert einer als Sammlung bewerteten Navigationseigenschaft `opportunity_customer_accounts` festgelegt ist.

- Eine Aufgabe wird erstellt, da sie als Objekt in einem Arrays definiert ist, das auf den Wert einer als Sammlung bewerteten Navigationseigenschaft `Opportunity_Tasks` festgelegt ist.

**Anforderung**

```http
POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
 "name": "Sample Account",
 "primarycontactid":
 {
     "firstname": "John",
     "lastname": "Smith"
 },
 "opportunity_customer_accounts":
 [
  {
      "name": "Opportunity associated to Sample Account",
      "Opportunity_Tasks":
      [
       { "subject": "Task associated to opportunity" }
      ]
  }
 ]
}

```

**Antwort**

 ```http

HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(3c6e4b5f-86f6-e411-80dd-00155d2a68cb)

```

<a name="bkmk_associateOnCreate"></a>

## <a name="associate-entity-records-on-create"></a>Entitätsdatensätze bei Erstellung zuordnen

 Um neue Entitäten vorhandene Entitäten zuzuordnen wenn diese erstellt werden, müssen Sie den Wert für Einzelwert-Navigationseigenschaften über die `@odata.bind`-Notation festlegen.

 Der folgende Anforderungstext, der im Firmenentitätssatz veröffentlicht wird, erstellt eine neue Firma, der ein vorhandener Kontakt mit dem `contactid`-Wert von 00000000-0000-0000-0000-000000000001 zugeordnet ist.

**Anforderung**

```http

POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

{
"name":"Sample Account",
"primarycontactid@odata.bind":"/contacts(00000000-0000-0000-0000-000000000001)"
}

```

**Antwort**

```http

HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/accounts(00000000-0000-0000-0000-000000000002)

```

> [!NOTE]
> Das Zuordnen von Entitäten auf diese Weise mithilfe einer Eigenschaft "als Sammlung bewertet" wird von der Internet-API nicht unterstützt.

<a name="bkmk_SuppressDuplicateDetection"></a>

## <a name="check-for-duplicate-records"></a>Nach doppelten Datensätzen suchen


Standardmäßig wird die Duplikaterkennung unterdrückt, wenn Sie Datensätze mithilfe der Internet API erstellen. Sie müssen die `MSCRM.SuppressDuplicateDetection: false` Kopfzeile in die POST-Anforderung einschließen, die Duplikaterkennung zu aktiveren. Duplikaterkennung gilt nur, wenn in der Organisation die Duplikaterkennung aktiviert ist, die Entität für Duplikaterkennung aktiviert ist, und aktive Duplikaterkennungsregeln angewendet werden. Weitere Informationen finden Sie unter [Erkennen von doppelten Daten](../detect-duplicate-data-with-code.md).

Sehen Sie auch [Erkennen von doppelten Daten mithilfe der Web-API](manage-duplicate-detection-create-update.md#bkmk_create), um weitere Informationen zu erhalten, wie Sie nach doppelten Datensätzen beim Vorgang "Erstellen" suchen können.

<a name="bkmk_initializefrom"></a>

## <a name="create-a-new-entity-record-from-another-entity"></a>Erstellen eines neuen Entitätsdatensatzes aus einer anderen Entität

Verwenden Sie `InitializeFrom function`, um einen neuen Datensatz im Rahmen eines vorhandenen Datensatzes zu erstellen, wobei eine Zuordnung zwischen den Entitäten vorhanden ist, zu denen die Datensätze gehören. 

Im folgenden Beispiel wird gezeigt, wie Sie einen Kontodatensatz mithilfe der Attributwerte eines vorhandenen Datensatzes einen Kontoentität mit `accountid`-Wert gleich c65127ed-2097-e711-80eb-00155db75426 erstellen.

**Anforderung**

```http
GET [Organization URI]/api/data/v9.0/InitializeFrom(EntityMoniker=@p1,TargetEntityName=@p2,TargetFieldType=@p3)?@p1={'@odata.id':'accounts(c65127ed-2097-e711-80eb-00155db75426)'}&@p2='account'&@p3=Microsoft.Dynamics.CRM.TargetFieldType'ValidForCreate' HTTP/1.1
If-None-Match: null
OData-Version: 4.0
OData-MaxVersion: 4.0
Content-Type: application/json
Accept: application/json
```

**Antwort**

```json
{
        "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",
        "@odata.type": "#Microsoft.Dynamics.CRM.account",
        "parentaccountid@odata.bind": "accounts(c65127ed-2097-e711-80eb-00155db75426)",
        "transactioncurrencyid@odata.bind": "transactioncurrencies(732e87e1-1d96-e711-80e4-00155db75426)",
        "address1_line1":"123 Maple St.",
        "address1_city":"Seattle",
        "address1_country":"United States of America"
}
```

Die Antwort, die von InitializeFrom-Anforderung empfangen wird, besteht aus zugeordneten Attributen zwischen Quellentität und Zielentität und der GUID des übergeordneten Datensatzes. Die Attributzuordnung zwischen Entitäten, die eine Entitätsbeziehung haben, ist für verschiedene Entitätssätze verschieden und kann angepasst werden, deshalb variieren die Reaktion von der InitializeFrom-Funktionsanforderung für verschiedene Entitäten und Organisationen. Wenn diese Antwort im Text der Erstellungsanforderung an den neuen Datensatz übergeben wird, werden diese Attributwerte im neuen Datensatz repliziert. Die Werte von benutzerdefinierten zugeordneten Attributen werden auch im neuen Datensatz während des Prozesses festgelegt.

> [!NOTE]
> Um zu bestimmen, dass zwei Entitäten zugeordnet werden können, können Sie diese Abfrage verwenden:  
GET [Organization URI]/api/data/v9.0/entitymaps?$select=sourceentityname,targetentityname&$orderby=sourceentityname

Andere Attributwerte können für den neuen Datensatz auch festgelegt und/oder geändert werden, indem Sie sie im JSON-Anforderungstext, wie im Beispiel gezeigt, hinzufügen.

```http
POST [Organization URI]/api/data/v9.0/accounts HTTP/1.1
Content-Type: application/json; charset=utf-8
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json

    {
        "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",
        "@odata.type": "#Microsoft.Dynamics.CRM.account",
        "parentaccountid@odata.bind": "accounts(c65127ed-2097-e711-80eb-00155db75426)",
        "transactioncurrencyid@odata.bind": "transactioncurrencies(732e87e1-1d96-e711-80e4-00155db75426)",
        "name":"Contoso Ltd",
        "numberofemployees":"200",
        "address1_line1":"100 Maple St.",
        "address1_city":"Seattle",
        "address1_country":"United States of America",
        "fax":"73737"
    }
}
```

<a name="bkmk_createWithDataReturned"></a>

## <a name="create-with-data-returned"></a>Erstellen mit den zurückgegebenen Daten

Sie können Ihre POST-Anforderung so zusammen stellen, dass die Daten aus dem erstellten Datensatz mit dem Status 201 (Erstellt) zurückgegeben werden.  Um dieses Ergebnis zu erzielen, müssen Sie die `return=representation`-Einstellung in den Anforderungsheadern verwenden.

Um die zurückgegebenen Eigenschaften zu steuern, hängen Sie die `$select`-Abfrageoption für die URL im Entitätssatz an.  Wenn sie verwendet wird, wird die `$expand`-Abfrageoption ignoriert.

Wenn eine Entität auf diese Weise erstellt wird, wird der `OData-EntityId`-Header mit der URI für den erstellten Datensatz nicht zurückgegeben.

In diesem Beispiel wird eine Firmaenentität erstellt und gibt die angeforderten Daten in der Antwort zurück.

**Anforderung**

 ```http

POST [Organization URI]/api/data/v9.0/accounts?$select=name,creditonhold,address1_latitude,description,revenue,accountcategorycode,createdon HTTP/1.1
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json
Content-Type: application/json; charset=utf-8
Prefer: return=representation

{
    "name": "Sample Account",
    "creditonhold": false,
    "address1_latitude": 47.639583,
    "description": "This is the description of the sample account",
    "revenue": 5000000,
    "accountcategorycode": 1
}

```

**Antwort**

```http

HTTP/1.1 201 Created
Content-Type: application/json; odata.metadata=minimal
Preference-Applied: return=representation
OData-Version: 4.0

{
    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#accounts/$entity",
    "@odata.etag": "W/\"536530\"",
    "accountid": "d6f193fc-ce85-e611-80d8-00155d2a68de",
    "accountcategorycode": 1,
    "description": "This is the description of the sample account",
    "address1_latitude": 47.63958,
    "creditonhold": false,
    "name": "Sample Account",
    "createdon": "2016-09-28T22:57:53Z",
    "revenue": 5000000.0000,
    "_transactioncurrencyid_value": "048dddaa-6f7f-e611-80d3-00155db5e0b6"
}

```

### <a name="see-also"></a>Siehe auch

[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)<br />
[Beispiele grundlegender Web API-Operationen (clientseitiges JavaScript)](samples/basic-operations-client-side-javascript.md)<br />
<xref href="Microsoft.Dynamics.CRM.InitializeFrom?text=InitializeFrom Function" />  
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)<br />
[HTTP-Anforderungen verfassen und Fehler beheben](compose-http-requests-handle-errors.md)<br />
[Datenabfrage mit Web-API](query-data-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Ausführen von Batchbetrieben mithilfe der Web-API](execute-batch-operations-using-web-api.md)<br />
[Annehmen eines anderen Benutzerkontos mit Web API](impersonate-another-user-web-api.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)<br />

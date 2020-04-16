---
title: Verwenden von Postman, um Operationen mit der Web API durchzuführen (Common Data Service für Apps)| MicrosoftDocs
description: Erfahren Sie, wie Sie Web-API-Anfragen mit Postman erstellen und versenden.
ms.custom: ''
ms.date: 03/22/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: AB50128B-D8E3-47A3-A0F8-9594EF6B7022
caps.latest.revision: 7
author: susikka
ms.author: susikka
manager: shujoshi
search.audienceType:
- developer
search.app:
- D365CE
ms.openlocfilehash: be5300e665c2c116618f5b01ba7186c3627c23d6
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154998"
---
# <a name="use-postman-to-perform-operations-with-the-web-api"></a>Verwenden von Postman, um Operationen mit der Web-API durchzuführen

Verwenden Sie Postman, um Web-API-Anfragen zu erstellen und zu senden und Antworten anzuzeigen. Dieses Thema beschreibt, wie Sie Postman verwenden, um Web-API-Anfragen zu erstellen, abzurufen, zu aktualisieren und zu löschen (CRUD) und Funktionen und Aktionen mit Postman verwenden.

> [!IMPORTANT]
> Sie müssen eine Umgebung haben, die mit den unter [Einrichten einer Postman-Umgebung](setup-postman-environment.md) beschriebenen Schritten erstellt wurde.

Die mit den Anweisungen in [Einrichten einer Postman-Umgebung](setup-postman-environment.md) erstellte Umgebung erzeugt eine `{{webapiurl}}`-Postman-Variable, die die Basis-URL für Anfragen liefert. Fügen Sie an diese Variable an, um die URL für Ihre Anfragen zu definieren.

Die verwendeten HTTP-Methoden und -Werte hängen von der Art der Operation, die Sie durchführen möchten, ab. In den folgenden Abschnitten werden die allgemeinen Funktionen erläutert.

## <a name="retrieve-multiple-records"></a>Mehrere Datensätze abrufen

Verwenden Sie eine `GET`-Abfrage, um einen Satz von Datensätzen abzurufen. Im folgenden Beispiel werden die ersten drei Kontodatensätze abgerufen.

> [!NOTE]
> Web-API-Anfragen sollten bestimmte HTTP-Header enthalten. Jede Anfrage sollte den `Accept`-Kopfzeilenwert von `application/json` beinhalten, auch wenn keine Antwort erwartet wird. Die aktuelle OData-Version ist `4.0`, fügen Sie also Header `OData-Version: 4.0` ein. Fügen Sie den `OData-MaxVersion`-Header ein, damit keine Unklarheiten über die Version mit neuen Versionen von OData entstehen. Weitere Informationen: [HTTP-Header](compose-http-requests-handle-errors.md#http-headers)

**Beispiel**


`GET` `{{webapiurl}}accounts?$select=name,accountnumber&$top=3`

![Mehrere Datensätze mit Postman abrufen](media/postman-retrieve-multiple.png "Mehrere Datensätze mit Postman abrufen")

Der Body der Antwort wird so aussehen:

```json
{
    "@odata.context": "https://yourorg.crm.dynamics.com/api/data/v9.0/$metadata#accounts(name,accountnumber)",
    "value": [
        {
            "@odata.etag": "W/\"2291741\"",
            "name": "Contoso Ltd",
            "accountnumber": null,
            "accountid": "9c706dc8-d2f5-e711-a956-000d3a328903"
        },
        {
            "@odata.etag": "W/\"2291742\"",
            "name": "Fourth Coffee",
            "accountnumber": null,
            "accountid": "a2706dc8-d2f5-e711-a956-000d3a328903"
        },
        {
            "@odata.etag": "W/\"2291743\"",
            "name": "Contoso Ltd",
            "accountnumber": null,
            "accountid": "9c3216b8-3efb-e711-a957-000d3a328903"
        }
    ]
}
```

Mehr Informationen: [Datenabfrage über die Web API](query-data-web-api.md).

## <a name="retrieve-a-particular-record"></a>Einen bestimmten Datensatz abrufen

Verwenden Sie eine `GET`-Abfrage, um einen Datensatz abzurufen. Das folgende Beispiel ruft zwei Eigenschaften von einem bestimmten Konto ab und erweitert die Informationen über den zugehörigen primären Kontakt um den vollständigen Namen.


`GET` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)?$select=name,accountnumber&$expand=primarycontactid($select=fullname)`

![Datensatz mit Postman abrufen](media/postman-retrieve-record.png "Datensatz mit Postman abrufen")

Der Body der Antwort wird so aussehen:

```json
{
    "@odata.context": "https://yourorg.crm.dynamics.com/api/data/v9.0/$metadata#accounts(name,accountnumber,primarycontactid(fullname))/$entity",
    "@odata.etag": "W/\"2291742\"",
    "name": "Fourth Coffee",
    "accountnumber": null,
    "accountid": "a2706dc8-d2f5-e711-a956-000d3a328903",
    "primarycontactid": {
        "@odata.etag": "W/\"1697263\"",
        "fullname": "Susie Curtis",
        "contactid": "a3706dc8-d2f5-e711-a956-000d3a328903"
    }
}
```
Weitere Informationen finden Sie unter [Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md).

## <a name="create-a-record"></a>Erstellen eines Datensatzes

Verwenden Sie eine `POST`-Anfrage, um Daten zu senden, um einen Datensatz zu erstellen. Legen Sie die URL auf den Entitätssetnamen fest (in diesem Fall `accounts`) und legen Sie die Header wie hier fest.

`POST` `{{webapiurl}}accounts`

![Erstellen eines neuen Datensatzes über Web-API](media/postman-create-records.png "Erstellen eines neuen Datensatzes über Web-API")

Legen Sie den Body der Anfrage mit Informationen über das zu erstellende Konto fest.

![Text der Anforderung zum Anlegen eines Datensatzes über Web-API](media/postman-create-record-body.png "Text der Anforderung zum Anlegen eines Datensatzes über Web-API")

Wenn Sie diese Anfrage senden, ist der Body leer, aber die ID des erstellten Kontos befindet sich im `OData-EntityId` Header-Wert.

Weitere Informationen finden Sie unter [Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md).

## <a name="update-a-record"></a>Aktualisieren eines Datensatzes

Verwenden Sie die `PATCH`-Methode, um einen Entitätsdatensatz zu aktualisieren, wie hier gezeigt.

`PATCH` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)`

![Aktualisieren eines Datensatzes über Web-API](media/postman-update-record.png "Aktualisieren eines Datensatzes über Web-API")

Wenn Sie diese Anfrage senden, ist der Body leer, aber die ID des aktualisierten Kontos befindet sich im `OData-EntityId` Header-Wert.

Mehr Informationen: [Update und Löschen von Entitäten über die Web API.](update-delete-entities-using-web-api.md)

## <a name="delete-a-record"></a>Einen Datensatz löschen

Verwenden Sie die `DELETE`-Methode, um einen vorhandenen Datensatz zu löschen.

`DELETE` `{{webapiurl}}accounts(`*&lt;accountid&gt;*`)`

![Löschen eines Datensatzes über Web-API](media/postman-delete-record.png "Löschen eines Datensatzes über Web-API")

Wenn Sie diese Anfrage absenden, wird der Kontodatensatz mit der angegebenen `accountid` gelöscht.

Mehr Informationen: [Update und Löschen von Entitäten über die Web API.](update-delete-entities-using-web-api.md)

## <a name="use-a-function"></a>Verwenden einer Funktion

Verwenden Sie eine `GET`-Abfrage mit Funktionen, die unter [Web API-Funktionsreferenz](https://docs.microsoft.com/dynamics365/customer-engagement/web-api/functions?view=dynamics-ce-odata-9) aufgeführt sind, um wiederverwendbare Operationen mit der Web API durchzuführen. Das folgende Beispiel zeigt, wie man eine Web-API-Anfrage sendet, die <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates function" /> verwendet, um Duplikate eines bestimmten Datensatzes zu erkennen und abzurufen.

|||
|----|----|
|`GET`|`{{webapiurl}}RetrieveDuplicates(BusinessEntity=@p1,MatchingEntityName=@p2,PagingInfo=@p3)?@p1={'@odata.type':'Microsoft.Dynamics.CRM.account','accountid':'`*&lt;accountid&gt;*`'}&@p2='account'&@p3={'PageNumber':1,'Count':50}`|

![Erstellen einer Web-API-Anfrage, die Funktionen verwendet](media/postman-use-function.png "Erstellen einer Web-API-Anfrage, die Funktionen verwendet")

Funktionen geben entweder eine Sammlung oder einen komplexen Typ zurück. Die Antwort der obigen <xref href="Microsoft.Dynamics.CRM.RetrieveDuplicates?text=RetrieveDuplicates function" /> sollte wie folgt aussehen.

```json
{
        {
    "@odata.context": "https://yourorgname.crm.dynamics.com/api/data/v9.0/$metadata#accounts",
    "value": [
        <Omitted for brevity: JSON data for any matching accounts including all properties>
    ]
}
}
```

Weitere Informationen finden Sie unter [Verwenden von Web-API-Funktionen](use-web-api-functions.md).

## <a name="use-an-action"></a>Verwenden einer Aktion

Verwenden Sie eine `POST`-Abfrage mit Aktionen, die unter [Web API-Aktionsreferenz](https://docs.microsoft.com/dynamics365/customer-engagement/web-api/actions?view=dynamics-ce-odata-9) aufgeführt sind, um Operationen mit Nebenwirkungen durchzuführen.

Dieses Beispiel veranschaulicht die Verwendung des <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates action" />.

`POST` `{{webapiurl}}BulkDetectDuplicates`

![Erstellen einer Web-API-Anfrage, die Aktionen verwendet](media/postman-use-action.png "Erstellen einer Web-API-Anfrage, die Aktionen verwendet")

Die Anforderung oben übermittelt einen asynchronen Duplikaterkennungsauftrag, der im Hintergrund ausgeführt wird. Die Duplikate werden in Übereinstimmung mit den veröffentlichten Regeln für doppelten den Entitätstyp erkannt. <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicatesResponse?text=BulkDetectDuplicatesResponse ComplexType" /> wird als Antwort von <xref href="Microsoft.Dynamics.CRM.BulkDetectDuplicates?text=BulkDetectDuplicates action" /> zurückgegeben. Die Antwort enthält die Eigenschaft `JobId`, die die GUID des asynchronen Duplikaterkennungsauftrags enthält, der doppelte Datensätze erkennt und protokolliert.

Weitere Informationen finden Sie unter [Verwenden von Web-API-Aktionen](use-web-api-actions.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von Postman mit Web-API](use-postman-web-api.md)<br>
[Vorgänge mithilfe der Web-API ausführen](perform-operations-web-api.md)

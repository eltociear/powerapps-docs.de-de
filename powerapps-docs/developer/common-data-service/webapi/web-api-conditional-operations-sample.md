---
title: Beispiel für bedingte Web-API-Vorgänge (Common Data Service) | Microsoft-Dokumentation
description: Diese Gruppe von Beispielen zeigt, wie Vorgänge ausgeführt werden, die bedingt auf der Version des Entitätsdatensatzes auf dem Common Data Service-Server basieren und/oder derzeit vom Client verwaltet werden
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: f2e5d22b-93fe-43b7-af15-3e281f3b3084
caps.latest.revision: 13
author: JimDaly
ms.author: jdaly
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 924368f5d72a11fb94445b5e283bfe180871c681
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154962"
---
# <a name="web-api-conditional-operations-sample"></a>Beispiel bedingter Web-API-Operationen

Diese Gruppe von Beispielen zeigt, wie Vorgänge ausgeführt werden, die bedingt auf der Version des Entitätsdatensatzes auf dem Common Data Service-Server basieren und/oder derzeit vom Client verwaltet werden. Weitere Informationen finden Sie unter [Ausführen bedingter Operationen mit der Web-API](perform-conditional-operations-using-web-api.md). Dieses Beispiel wurde als ein separates Projekt für die folgenden Sprachen implementiert:  
  
 [Beispiel bedingter Web-API-Operationen (C#)](samples/conditional-operations-csharp.md)  
 
 Die Common Data Service-Web-API folgt den Konventionen des [OData v4.0](https://www.odata.org/documentation/)-Protokolls, das [ETags](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752236) verwendet, um die Ressourcenversionssteuerung zu implementieren. Web API-bedingte Operationen hängen von diesem Versionenmechanismus ab.  
  
 In diesem Thema werden die Struktur und der Inhalt der Beispiele für eine spätere, sprachunabhängigen Ebene behandelt. Sie erläutert die Details der HTTP-Anforderungen und die Reaktionen und die zugeordnete Programmausgabe, soweit vorhanden. Wiederholen Sie die verknüpften Beispielthemen oben, um sprachspezifische Implementierungen und verwandte Details zu erhalten und zu sehen, wie die in diesem Thema beschriebenen Methoden verwendet werde.  
  
## <a name="demonstrates"></a>Demonstriert

 Dieses Beispiel ist in drei allgemeine Abschnitte unterteilt, die in der folgenden Tabelle aufgeführt sind.   Jeder Abschnitt enthält einen Satz verknüpfter Web-API-Operationen, die im zugehörigen Konzeptabschnitt des Themas [Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md) detaillierter dargestellt werden.  
  
|Abschnitt Code .|Zugeordnete konzeptuelle Themen|  
|------------------|----------------------------------|  
|[Bedingt ABRUFEN](#bkmk_conditionalGet)|[Bedingte Abrufe](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged)|  
|[Optimistische Parallelität beim Löschen und Aktualisieren](#bkmk_optimisiticConcurrency)|[Optimistische Parallelität anwenden](perform-conditional-operations-using-web-api.md#bkmk_Applyoptimisticconcurrency)|  
|[Steuern von upsert Vorgänge](#bkmk_controllingUpsert)|[upsert-Vorgänge begrenzen](perform-conditional-operations-using-web-api.md#bkmk_limitUpsertOperations)|  
  
 Die folgenden Abschnitte enthalten eine kurze Diskussion zu den ausgeführten Common Data Service-Web-API-Vorgängen sowie den entsprechenden HTTP-Nachrichten und der Ausgabe, die der Konsole zugeordnet ist und für jede Sprache gleich ist. Der Kürze halber sind entsprechende HTTP-Kopfzeilen weggelassen worden. Die URIs der Datensätze unterscheiden sich bei der Grundorganisationsadresse und der ID des Datensatzes, der vom Common Data Service-Server zugewiesen wird.  
  
<a name="bkmk_sampleData"></a>
   
## <a name="sample-data"></a>Beispieldaten

 Das Beispiel erstellt den folgenden Datensatz, bevor die Hauptcodeabschnitte ausgeführt werden.  
  
|Entitätstyp|Vom Client zugewiesene Eigenschaften|Vom Server zugewiesene Eigenschaften|  
|-----------------|---------------------------------|---------------------------------|  
|<xref:Microsoft.Dynamics.CRM.account>|Name: `Contoso Ltd.` <br />Umsatz: `5000000`<br />Telefon: `555-0000`<br />Beschreibung: `Parent company of Contoso Pharmaceuticals, etc.`|ID:  `14e151db-9b4f-e611-80e0-00155da84c08`<br />Initialer Etag:  `W/"628448"`|  
  
<a name="bkmk_conditionalGet"></a>

## <a name="conditional-get"></a>Bedingt ABRUFEN

 Dieser Abschnitt des Programms wird veranschaulicht, wie Sie bedingte Abrufe ausführen, um die Netzwerkbandweite und die Serververarbeitung zu optimieren, während der aktuellste Datensatzstatus vom Client beibehalten wird. Weitere Informationen:[Bedingte Abrufe](perform-conditional-operations-using-web-api.md#bkmk_DetectIfChanged).  
  
1.  Versuchen Sie nur dann die Firma `Contoso Ltd.` abzurufen, wenn *nicht* der aktuellen Version entspricht, die vom eTagwert identifiziert wurde, der zurückgegeben wurde, als der Firmendatensatzes erstellt wurde. Diese Bedingung wird von der `If-None-Match` Kopfzeile dargestellt.  
  
 **Anforderung**  
  
   ```http  
   GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
   If-None-Match: W/"628448"  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  

   ```  
  
 **Antwort**  
  
   ```http  
   HTTP/1.1 304 Not Modified  
   ```  
  
 **Konsolenausgabe**  
  
   ```  
   Instance retrieved using ETag: W/"628448"  
   Expected outcome: Entity was not modified so nothing was returned.  
   ```  

   Der Reaktionswert `304 Not Modified` gibt an, dass der aktuelle Datensatz der aktuellste ist, damit der Server *nicht* den angeforderten Datensatz im Antworttext zurückgeben muss.  
  
2.  Aktualisieren Sie die Firma, indem Sie die primäre Telefonnummerneigenschaft ändern.  
  
 **Anforderung**  
  
   ```http
   PUT https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)/telephone1 HTTP/1.1  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  
   Content-Type: application/json  
   {  
      "value": "555-0001"  
   }  
   ```  
  
 **Antwort**  
  
   ```http
   HTTP/1.1 204 No Content  
   ```  
  
 **Konsolenausgabe**  
  
   ```  
   Account telephone number updated.  
   ```  
  
3.  Verringern Sie denselben bedingten Abrufvorgang erneut mit dem ursprünglichen eTagwert. Diesmal gibt der Vorgang die angeforderten Daten zurück, weil die Version auf dem Server anders (und neuer ) ist als die Version, die mit der Anforderung identifiziert wurde. Wie alle Datenabrufe enthält die Antwort die eTagkopfzeile, die die aktuelle Version angibt.  
  
 **Anforderung**  
  
   ```http
   GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
   If-None-Match: W/"628448"  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  
   ```  
  
 **Antwort**  
  
   ```http
   HTTP/1.1 200 OK  
   Content-Type: application/json; odata.metadata=minimal  
   ETag: W/"628460"  
   {  
      "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag":"W/\"628460\"",  
      "name":"Contoso Ltd",  
      "revenue":5000000.0000,  
      "telephone1":"555-0001",  
      "description":"Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid":"14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03"  
   }  
   ```  
  
 **Konsolenausgabe**  
  
   ```
   Instance retrieved using ETag: W/"628448"  
   {  
      "@odata.context": "https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag": "W/\"628460\"",  
      "name": "Contoso Ltd",  
      "revenue": 5000000.0,  
      "telephone1": "555-0001",  
      "description": "Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid": "14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value": "0d4ed62e-95f7-e511-80d1-00155da84c03"  
   }  
  
   ```  
  
<a name="bkmk_optimisiticConcurrency"></a>
  
## <a name="optimistic-concurrency-on-delete-and-update"></a>Optimistische Parallelität beim Löschen und Aktualisieren
 
 Dieser Abschnitt des Programms veranschaulicht, wie Sie bedingte Vorgänge löschen und aktualisieren.  Die häufigste Nutzung für solche Vorgänge ist die Implementierung eines optimistischen Parallelitätsansatzes für die Datensatzverarbeitung in einer Umgebung für mehrere Anwender. Weitere Informationen: [Wenden Sie optimistische Parallelität an](perform-conditional-operations-using-web-api.md#bkmk_Applyoptimisticconcurrency)  
  
1.  Versuchen Sie die ursprüngliche Firma nur dann zu löschen, wenn sie der ursprünglichen Version (ETag-Wert) entspricht.  Diese Bedingung wird von der `If-Match` Kopfzeile dargestellt.  Dieser Vorgang ist fehlerhaft, weil der Firmendatensatz im vorherigen Abschnitt aktualisiert wurde und deshalb diese Version auf dem Server aktualisiert wurde.  
  
 **Anforderung**  
  
   ```http
   DELETE https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
   If-Match: W/"628448"  
   OData-MaxVersion: 4.0  
   OData-Version: 4.0  
   Accept: application/json  
   ```  
  
 **Antwort**  
  
   ```http  
    HTTP/1.1 412 Precondition Failed  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.", . . .  
        }  
    }  
   ```  
  
 **Konsolenausgabe**  
  
   ```  
   Expected Error: The version of the existing record doesn't match the property provided.  
         Account not deleted using ETag 'W/"628448"', status code: '412'.  
   ```  
  
2.  Versuchen Sie, die Firma nur dann zu aktualisieren, wenn sie der ursprünglichen Version (ETag-Wert) entspricht.  Wieder wird diese Bedingung von der `If-Match` Kopfzeile dargestellt und der Vorgang schlägt aus dem gleichen Grund fehl.  
  
 **Anforderung**  
  
   ```http  
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: W/"628448"  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0002",  
      "revenue": 6000000  
    }    
   ```  
  
 **Antwort**  
  
   ```http  
    HTTP/1.1 412 Precondition Failed  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"The version of the existing record doesn't match the RowVersion property provided.", . . .   
      }  
    }    
   ```  
  
 **Konsolenausgabe**  
  
   ```  
    Expected Error: The version of the existing record doesn't match the property provided.  
            Account not updated using ETag 'W/"628448"', status code: '412'.  
   ```  
  
3.  Führen Sie erneut ein Update durch, verwenden Sie aber stattdessen den aktuellen eTagwert aus der letzten Datensatzabfrage im vorherigen Abschnitt.  
  
 **Anforderung**  
  
   ```http
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: W/"628460"  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    {  
      "telephone1": "555-0003",  
      "revenue": 6000000  
    }  
   ```  
  
 **Antwort**  
  
   ```http
    HTTP/1.1 204 No Content  
   ```  
  
 **Konsolenausgabe**  
  
   ```  
    Account successfully updated using ETag: W/"628460", status code: '204'.  
   ```  
  
4.  Bestätigen Sie das Update, indem Sie den Status der aktuellen Firma abrufen und ausgeben.  Dies benötigt eine GET-Anforderung.  
  
 **Anforderung**  
  
   ```http 
    GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
   ```  
  
 **Antwort**  
  
   ```http
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    ETag: W/"628461"  
    OData-Version: 4.0  
    {  
      "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag":"W/\"628461\"",  
      "name":"Contoso Ltd",  
      "revenue":6000000.0000,  
      "telephone1":"555-0003",  
      "description":"Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid":"14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }  
   ```  
  
 **Konsolenausgabe**  
  
   ```
    {  
      "@odata.context": "https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag": "W/\"628461\"",  
      "name": "Contoso Ltd",  
      "revenue": 6000000.0,  
      "telephone1": "555-0003",  
      "description": "Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid": "14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value": "0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }  
   ```  
  
<a name="bkmk_controllingUpsert"></a>

## <a name="controlling-upsert-operations"></a>Steuern von upsert Vorgänge

 Dieser Abschnitt des Programms veranschaulicht, wie Sie bedingte `PATCH` Vorgänge ausführen und upsert Vorgänge begrenzen, um entweder einen Vorgang auszuführen, der nur aktualisiert oder nur einfügt. Weitere Informationen: [upsert-Vorgänge begrenzen](perform-conditional-operations-using-web-api.md#bkmk_limitUpsertOperations).  
  
1.  Versuchen Sie primären Telefon- und Umsatzeigenschaften für diese Firma einzufügen ohne zu aktualisieren. Die `If-None-Match` Kopfzeile mit dem Wert von `*` steht für diese upsert Bedingung. Dieser Vorgang schlägt fehl, weil dieser Firmendatensatz immer noch auf dem Server vorhanden (es sei denn, er wurde gleichzeitig durch einen anderen Benutzer gelöscht).  
  
 **Anforderung**  
  
   ```http
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-None-Match: *  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0004",  
      "revenue": 7500000  
    }  
   ```  
  
 **Antwort**  
  
   ```http
    HTTP/1.1 412 Precondition Failed  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"A record with matching key values already exists.", . . .  
      }  
    }  
   ```  
  
 **Konsolenausgabe**  
  
   ```   
    Expected Error: A record with matching key values already exists.  
            Account not updated using ETag 'W/"628448", status code: '412'.    
   ```  
  
2.  Versucht, den selben Aktualisierungsvorgang ohne Erstellung auszuführen. Um dies zu erzielen, wird die bedingte `If-Match` Kopfzeile mit dem Wert von `*`verwendet.  Dieser Vorgang ist erfolgreich, da der Datensatz auf dem Server vorhanden ist.  
  
 **Anforderung**  
  
   ```http
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: *  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0005",  
      "revenue": 7500000  
    }  
   ```  
  
 **Antwort**  
  
   ```http
    HTTP/1.1 204 No Content  
   ```  
  
 **Konsolenausgabe**  
  
   ```  
    Account updated using If-Match '*'  
   ```  
  
3.  Abrufen und Ausgabe des aktuellen Firmenstatus mit einer einfachen `GET` Anforderung. Beachten Sie, dass der zurückgegebene eTagwert sich geändert hat, um die neue, aktualisierte Version des Firmendatensatzes zu widerspiegeln.  
  
 **Anforderung**  
  
   ```http  
    GET https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08)?$select=name,revenue,telephone1,description HTTP/1.1  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json    
   ```  
  
 **Antwort**  
  
   ```http  
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    ETag: W/"628463"  
    OData-Version: 4.0  
    {  
      "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag":"W/\"628463\"",  
      "name":"Contoso Ltd","revenue":7500000.0000,  
      "telephone1":"555-0005",  
      "description":"Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid":"14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }    
   ```  
  
 **Konsolenausgabe**  
  
   ```http    
    {  
      "@odata.context": "https://[Organization URI]/api/data/v9.0/$metadata#accounts(name,revenue,telephone1,description)/$entity",  
      "@odata.etag": "W/\"628463\"",  
      "name": "Contoso Ltd",  
      "revenue": 7500000.0,  
      "telephone1": "555-0005",  
      "description": "Parent company of Contoso Pharmaceuticals, etc.",  
      "accountid": "14e151db-9b4f-e611-80e0-00155da84c08",  
      "_transactioncurrencyid_value": "0d4ed62e-95f7-e511-80d1-00155da84c03"  
    }    
   ```  
  
4.  Löschen Sie die Firma mit einer einfachen `DELETE`.  
  
 **Anforderung**  
  
   ```http    
    DELETE https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json    
   ```  
  
 **Antwort**  
  
   ```http
    HTTP/1.1 204 No Content  
   ```  
  
 **Konsolenausgabe**  
  
   ```  
    Account was deleted.  
   ```  
  
5.  Wie in Schritt 2, versucht zu aktualisieren, wenn die Firma vorhanden ist.  Wieder wird diese dem von der `If-Match`Kopfzeile mit dem Wert von `*`dargestellt.  Dieser Vorgang schlägt fehl, da der entsprechende Datensatz soeben gelöscht wurde. Wenn aber diese `If-Match`-Kopfzeile fehlte, dann sollte der daraus resultierende einfache upsert-Vorgang erfolgreich einen neuen Datensatz erstellen.  
  
 **Anforderung**  
  
   ```http  
    PATCH https://[Organization URI]/api/data/v9.0/accounts(14e151db-9b4f-e611-80e0-00155da84c08) HTTP/1.1  
    If-Match: *  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    Accept: application/json  
    Content-Type: application/json; charset=utf-8  
    {  
      "telephone1": "555-0006",  
      "revenue": 7500000  
    }    
   ```  
  
 **Antwort**  
  
   ```http    
    HTTP/1.1 404 Not Found  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {  
      "error":{  
        "code":"","message":"account With Id = 14e151db-9b4f-e611-80e0-00155da84c08 Does Not Exist", . . .  
      }  
    }    
   ```  
  
 **Konsolenausgabe**  
  
   ```    
    Expected Error: Account with Id = 14e151db-9b4f-e611-80e0-00155da84c08 does not exist.  
    Account not updated because it does not exist, status code: '404'.    
   ```  
  
 Es ist nicht notwendig, Beispieldaten zu löschen, da bereits der Firmendatensatz in Schritt 4 gelöscht wurde.  
  
### <a name="see-also"></a>Siehe auch

[Verwenden der Common Data Service-Web-API](overview.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](perform-conditional-operations-using-web-api.md)<br />
[Beispiel bedingter Web-API-Operationen (C#)](samples/conditional-operations-csharp.md)   

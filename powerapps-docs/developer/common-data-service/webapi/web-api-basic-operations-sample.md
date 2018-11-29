---
title: Beispiel für grundlegende Web-API-Vorgänge (Common Data Service für Apps) | Microsoft Docs
description: 'Diese Beispiele veranschaulichen, wie Sie CRUD-Operationen (Erstellen, Abrufen, Aktualisieren und Löschen) mithilfe der Web-API ausführen. Diese werden mithilfe clientseitigen JavaScripts und C# implementiert.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: f006f88c-74cb-4fde-90e5-e1faf2051673
caps.latest.revision: 25
author: brandonsimons
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-basic-operations-sample"></a>Beispiel grundlegender Web-API-Operationen

Diese Gruppe von Beispielen veranschaulicht, wie Sie einfache CRUD-Vorgänge (Erstellen, Abrufen, Aktualisieren und Löschen) und assoziative Vorgänge mithilfe der Common Data Service für Apps-Web-API ausführen.  
  
-   [Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)  
  
 Dieses Thema berschreibt einen allgemeinen Satz von Vorgängen, die von jedem Beispiel in dieser Gruppe implementiert wurden. Dieses Thema beschreibt HTTP-Anforderungen, -Antworten und Textausgaben, die von jedem Beispiel dieser Gruppe ohne sprachspezifischen Details ausgeführt wird. Weitere Informationen zum Ausführen dieser Vorgänge, finden Sie in den sprachspezifischen Beschreibungen und den individuellen Beispielen.  
  
<a name="bkmk_demonstrates"></a>  
 
## <a name="demonstrates"></a>Demonstriert  

Dieses Beispiel wird in die folgenden Hauptabschnitte unterteilt und enthält "CDS für Apps"-Web-API-Vorgänge, die in den entsprechenden Themenabschnitten detailliert behandelt werden.  
  
|Abschnitt Code .|Zugeordnete konzeptuelle Themen|  
|------------------|----------------------------------|  
|[Abschnitt 1: Grundlegendes Erstellen und Aktualisieren von Vorgängen](#bkmk_section1)|[Grundlegende Erstellung](create-entity-web-api.md#bkmk_basicCreate) <br /> [Erstellen mit den zurückgegebenen Daten](create-entity-web-api.md#bkmk_createWithDataReturned) <br /> [Grundlegende Aktualisierung](update-delete-entities-using-web-api.md#bkmk_update) <br /> [Aktualisieren mit den zurückgegebenen Daten](update-delete-entities-using-web-api.md#bkmk_updateWithDataReturned)|  
|[Abschnitt 2: Erstellen Sie mit Zuordnung](#bkmk_section2)|[Entitäten bei Erstellung zuordnen](associate-disassociate-entities-using-web-api.md#bkmk_Associateentitiesoncreate)|  
|[Abschnitt 3: Erstellen Sie verknüpfte Entitäten (tiefe folgende)](#bkmk_section3)|[Erstellen verknüpfter Entitäten in einem Vorgang](create-entity-web-api.md#bkmk_CreateRelated)|  
|[Abschnitt 4: Ordnen Sie bestehende Entitäten zu und heben Sie diese hervor](#bkmk_section4)|[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)|  
|[Abschnitt 5: Löschungsentitäten (Beispielbereinigung)](#bkmk_section5)|[Grundlegende Löschung](update-delete-entities-using-web-api.md#bkmk_delete)|  
  
> [!NOTE]
>  Der Kürze halber sind entsprechende HTTP-Kopfzeilen weggelassen worden. Die URLs der Datensätze unterscheiden sich infolge der Grundorganisationsadresse und der ID des Datensatzes, der Ihnen durch Ihren "CDS für Apps"-Server zugewiesen wird.  
  
<a name="bkmk_section1"></a>
   
## <a name="section-1-basic-create-and-update-operations"></a>Abschnitt 1: Grundlegendes Erstellen und Aktualisieren von Vorgängen 
 
Dieser Abschnitt erstellt einen einzelnen Kontakt und führt dann eine Reihe von Updates nach dieser Instanz aus. Beachten Sie, dass der Antwortheader [OData-EntityId](http://docs.oasis-open.org/odata/odata/v4.0/os/part1-protocol/odata-v4.0-os-part1-protocol.html#_Toc372793637) die URL für den neu erstellte Datensatz (Entitätsinstanz) enthält, der parenthetisch die eindeutige ID für den Datensatz enthält.  
  
1.  Erstellen Sie einen neuen Kontakt namens Peter Cambel.  
  
 **Anforderung** 
  
    ```http
    POST http://[Organization URI]/api/data/v9.0/contacts HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "firstname": "Peter",  
      "lastname": "Cambel"  
    }  
    ```  
  
 **Antwort**  
  
    ```http  
    HTTP/1.1 204 No Content  
    OData-Version: 4.0  
    OData-EntityId: http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)  
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Contact 'Peter Cambel' created.  
    ```  
  
     Die Eigenschaften, die für jeden Attributtyp verfügbar sind, werden im Metadatendokuments definiert und sind auch für den Abschnitt <xref:Microsoft.Dynamics.CRM.EntityTypeIndex> dokumentiert. Allgemeinere Informationen finden Sie unter [Web-API-Typen und -Operationen](web-api-types-operations.md).  
  
2.  Aktualisieren Sie den Kontakt mit Werten für das Jahreseinkommen (80.000 Dollar) und Job-Position (Junior Developer).  
  
 **Anforderung** 
  
    ```http  
    PATCH http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "annualincome": 80000,  
      "jobtitle": "Junior Developer"  
    }  
    ```  
  
 **Antwort**  
  
    ```http  
    HTTP/1.1 204 No Content  
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Contact 'Peter Cambel' updated with job title and annual income.  
    ```  
  
3.  Rufen Sie den Kontakt mit den Datensatz explizit mit den initialisierten Eigenschaften ab.  Die `fullname` ist eine schreibgeschützte Eigenschaft, die von den `firstname` und `lastname`-Eigenschaften berechnet wird, die explizit initialisiert wurden, als die Instanz erstellt wurde. Demgegenüber wurde die `description`-Eigenschaft nicht explizit initialisiert, damit diese ein Standardwert, eine `null` Zeichenfolge fest.  
  
     Beachten Sie, dass die Antwort, zusätzlich zu den angeforderten Werten und den typischen Überschriften, ebenfalls automatisch die folgenden Typen an zusätzlichen Informationen zurückgegebe:  
  
    -   Die primäre ID für den aktuellen Entitätstyp, hier `contactid`.  
  
    -   Ein *eTagwert*, steht im `@odata.etag` Schlüssel, auf dem die bestimmte Version der angeforderten Ressource definiert wird. Weitere Informationen finden Sie unter [Ausführen bedingter Operationen mit der Web-API](perform-conditional-operations-using-web-api.md).  
  
    -   Der Metadatenkontext, der vom `@odata.context` Schlüssel definiert wird, bietet eine Möglichkeit, Abfrageergebnisse zu bestimmen, ob Sie von derselben Abfrage kamen.  
  
    -   Ein `_transactioncurrencyid_value`, der die Landeswährung für Finanztransaktionen angibt.  
  
 **Anforderung** 
  
    ```http  
    GET http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)?$select=fullname,annualincome,jobtitle,description HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    ```  
  
 **Antwort**  
  
    ```http
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {   
       "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,annualincome,jobtitle,description)/$entity",  
       "@odata.etag":"W/\"628883\"",  
       "fullname":"Peter Cambel",  
       "annualincome":80000.0000,  
       "jobtitle":"Junior Developer",  
       "description":null,  
       "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03",  
       "contactid":"60f77a42-5f0e-e611-80e0-00155da84c03"  
    }  
    ```  
  
 **Konsolenausgabe**  
  
    ```http    
    Contact 'Peter Cambel' retrieved:  
            Income: 80000  
            Job title: Junior Developer  
            Description: .    
    ```  
  
    > [!IMPORTANT]
    >  Sie sollten immer Auswahl und Filtern bei Abrufvorgängen verwenden, um die Leistung optimieren. Weitere Informationen finden Sie unter [Abfragen von Daten mit Web-API](query-data-web-api.md).  
  
4.  Aktualisieren Sie die Kontaktentitätsinstanz, indem Sie neue Werte für die selben Eigenschaften festlegen.  
  
 **Anforderung** 
  
    ```http
    PATCH http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "jobtitle": "Senior Developer",  
      "annualincome": 95000,  
      "description": "Assignment to-be-determined"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content    
    ```  
  
 **Konsolenausgabe**  
  
    ```http    
    Contact 'Peter Cambel' updated:  
            Job title: Senior Developer  
            Annual income: 95000  
            Description: Assignment to-be-determined    
    ```  
  
    > [!IMPORTANT]
    >  Senden Sie nur geänderte Eigenschaften an Updateanforderungen. Weitere Informationen finden Sie unter [Grundlegendes Update](update-delete-entities-using-web-api.md#bkmk_update).  
  
5.  Legen Sie explizit eine einzelne Eigenschaft fest, die einzelne primäre Telefonnummer. Hinweis: Dies ist eine `PUT` Anforderung und dass der JSON-Schlüssel, der `value` heißt, verwendet wird, wenn der Vorgang oder einzelne Eigenschaften ausgeführt werden.  
  
 **Anforderung** 
  
    ```http  
    PUT http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)/telephone1 HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "value": "555-0105"  
    }  
    ```  
  
 **Antwort**  
  
    ```http  
    HTTP/1.1 204 No Content  
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Contact 'Peter Cambel' phone number updated.  
    ```  
  
6.  Rufen Sie die dieselbe Eigenschaft ab, die einzelne primäre Telefonnummer. Beachten Sie erneut die Verwendung der Schlüssel, der `value` heißt.  
  
 **Anforderung** 
  
    ```http  
    GET http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)/telephone1 HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {   
       "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#contacts(60f77a42-5f0e-e611-80e0-00155da84c03)/telephone1",  
       "value":"555-0105"  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Contact's telephone# is: 555-0105.  
    ```  
  
7.  Einen gleichen Kontakt erstellen aber auch die Instanzinformation im gleichen Vorgang zurückgeben. Die letzte Funktion wird durch die `Prefer: return=representation` Kopfzeile aktiviert.  
  
 **Anforderung** 
  
    ```http    
    POST http://[Organization URI]/api/data/v9.0/contacts?$select=fullname,annualincome,jobtitle,contactid HTTP/1.1  
    OData-Version: 4.0  
    Content-Type: application/json; charset=utf-8  
    Prefer: return=representation  
    {  
      "firstname": "Peter_Alt",  
      "lastname": "Cambel",  
      "jobtitle": "Junior Developer",  
      "annualincome": 80000,  
      "telephone1": "555-0110"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 201 Created  
    Content-Type: application/json; odata.metadata=minimal  
    Preference-Applied: return=representation  
    OData-Version: 4.0  
    {  
      "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#contacts/$entity","@odata.etag":"W/\"758870\"","_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03","annualincome":80000.0000,"contactid":"199250b7-6cbe-e611-80f7-00155da84c08","jobtitle":"Junior Developer","fullname":"Peter_Alt Cambel"  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```    
    Contact 'Peter_Alt Cambel' created:  
            Annual income: 80000  
            Job title: Junior Developer  
    Contact URI: http://[Organization URI]/api/data/v9.0/contacts(199250b7-6cbe-e611-80f7-00155da84c08)  
    ```  
  
8.  Diesen gleichen Kontakt updaten und auch die Instanzinformation im gleichen Vorgang zurückgeben. Diese Funktion wird durch die `Prefer: return=representation` Kopfzeile aktiviert.
  
 **Anforderung** 
  
    ```http    
    POST http://[Organization URI]/api/data/v9.0/contacts?$select=fullname,annualincome,jobtitle,contactid HTTP/1.1  
    OData-Version: 4.0  
    Content-Type: application/json; charset=utf-8  
    Prefer: return=representation  
    {  
      "firstname": "Peter_Alt",  
      "lastname": "Cambel",  
      "jobtitle": "Junior Developer",  
      "annualincome": 80000,  
      "telephone1": "555-0110"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 201 Created  
    Content-Type: application/json; odata.metadata=minimal  
    Preference-Applied: return=representation  
    OData-Version: 4.0  
    {  
      "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#contacts/$entity","@odata.etag":"W/\"758870\"","_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03","annualincome":80000.0000,"contactid":"199250b7-6cbe-e611-80f7-00155da84c08","jobtitle":"Junior Developer","fullname":"Peter_Alt Cambel"  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```    
    Contact 'Peter_Alt Cambel' updated:  
            Annual income: 95000  
            Job title: Senior Developer   
    ```  
  
<a name="bkmk_section2"></a>  
 
## <a name="section-2-create-with-association"></a>Abschnitt 2: Erstellen Sie mit Zuordnung 
 
Dieser Abschnitt erstellt eine neue Firmeninstanz namens `Contoso, Ltd.` und verknüpft diese mit dem vorhandenen Kontakt `Peter Cambel`, der in [Abschnitt 1](#bkmk_section1) erstellt wurde.  Die Erstellung und Zuordnung wird in einem einzelnen Vorgang ausgeführt.  
  
1.  Legen Sie die Firma Contoso, Ltd an, und setzen Sie das primäre Kontaktattribut auf den vorhandenen Kontakt Peter Cambel.  Der `@odata.bind` Zusatz gibt an, dass eine Zuordnung erstellt wurde und die `primarycontactid` einzelbewertete Navigationseigenschaft dem bestehenden Kontakt Peter Cambel hinzugefügt wurde.  
  
 **Anforderung** 
  
    ```http  
    POST http://[Organization URI]/api/data/v9.0/accounts HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "name": "Contoso Inc",  
      "telephone1": "555-5555",  
      "primarycontactid@odata.bind": "http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content  
    OData-Version: 4.0  
    OData-EntityId: http://[Organization URI]/api/data/v9.0/accounts(65f77a42-5f0e-e611-80e0-00155da84c03)    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Account 'Contoso Inc' created.  
    ```  
  
2.  Rufen Sie den primären Kontakt für die Firma Contoso, Ltd. mithilfe von `$expand` mit der `primarycontactid` einzel-bewerteten Navigationseigenschaft auf, um auf den zugeordneten Datensatz <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> zuzugreifen.  
  
 **Anforderung** 
  
    ```http    
    GET http://[Organization URI]/api/data/v9.0/accounts(65f77a42-5f0e-e611-80e0-00155da84c03)?$select=name,&$expand=primarycontactid($select=fullname,jobtitle,annualincome) HTTP/1.1  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0   
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0  
    {   
       "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(fullname,jobtitle,annualincome))/$entity",  
       "@odata.etag":"W/\"628886\"",  
       "name":"Contoso Inc",  
       "accountid":"65f77a42-5f0e-e611-80e0-00155da84c03",  
       "primarycontactid":{   
          "@odata.etag":"W/\"628885\"",  
          "fullname":"Peter Cambel",  
          "jobtitle":"Senior Developer",  
          "annualincome":95000.0000,  
          "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03",  
          "contactid":"60f77a42-5f0e-e611-80e0-00155da84c03"  
       }  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```    
    Account 'Contoso Inc' has primary contact 'Peter Cambel':  
         Job title: Senior Developer  
         Income: 95000    
    ```  
  
<a name="bkmk_section3"></a>  
 
## <a name="section-3-create-related-entities-deep-insert"></a>Abschnitt 3: Erstellen Sie verknüpfte Entitäten (tiefe folgende)  

In diesem Abschnitt werden wir aufzeigen, wie eine Entitätsinstanz und eine verknüpfte Instanz in einer einzigen POST-Anforderung erstellt wird. Mithilfe dieser Methode werden alle Instanzen neu erstellt; es gibt keine vorhandenen Instanzen, die zugeordnet werden können. Diese Methode hat zwei Vorteile. Sie ist effizienter und ersetzt mehrere einfache Erstellungs- und Zuordnungsvorgänge mit einem gemeinsamen Vorgang. Auch ist er [unteilbar](https://msdn.microsoft.com/library/aa719484\(v=vs.71\).aspx), sodass entweder der gesamte Vorgang erfolgreich ist und alle verknüpften Objekte erstellt werden oder der Vorgang schlägt fehl und es wird nichts erstellt.  
  
Dieser Abschnitt erstellt eine Firma, einen primären Kontakt und einen Reihe von Aufgaben für diesen Kontakt in einer Anforderung.  
  
1.  Erstellt die Firma `Fourth Coffee` und den primären Kontakt `Susie Curtis` und die drei verknüpften Aufgaben in einen Vorgang.  Beachten Sie die Verwendung der einzel-bewerteten `primarycontactid` Navigationseigenschaft und der Sammlung-bewerteten Navigationseigenschaft `Contact_Tasks`, um diese Beziehungen zu definieren.  Einzel-bewertete Navigationseigenschaften nehmen einen Objektwert, während Sammlung-bewertete Navigationseigenschaften einen Array-Wert nehmen.  
  
 **Anforderung** 
  
    ```http    
    POST http://[Organization URI]/api/data/v9.0/accounts HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "name": "Fourth Coffee",  
      "primarycontactid": {  
        "firstname": "Susie",  
        "lastname": "Curtis",  
        "jobtitle": "Coffee Master",  
        "annualincome": 48000,  
        "Contact_Tasks": [  
          {  
            "subject": "Sign invoice",  
            "description": "Invoice #12321",  
            "scheduledend": "2016-04-19T00:00:00-07:00"  
          },  
          {  
            "subject": "Setup new display",  
            "description": "Theme is - Spring is in the air",  
            "scheduledstart": "2016-04-20T00:00:00-07:00"  
          },  
          {  
            "subject": "Conduct training",  
            "description": "Train team on making our new blended coffee",  
            "scheduledstart": "2016-06-01T00:00:00-07:00"  
          }  
        ]  
      }  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content  
    OData-Version: 4.0  
    OData-EntityId: http://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Account 'Fourth Coffee' created.  
    ```  
  
2.  Rufen Sie selektiv die neu erstellte Fourth Coffee-Firma und den primären Kontakt ab.  Eine Erweiterung wird auf der einzel-bewerteten Navigationseigenschaft `primarycontactid`ausgeführt.  
  
 **Anforderung** 
  
    ```http    
    GET http://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)?$select=name,&$expand=primarycontactid($select=fullname,jobtitle,annualincome) HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0   
    {   
       "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#accounts(name,primarycontactid,primarycontactid(fullname,jobtitle,annualincome))/$entity",  
       "@odata.etag":"W/\"628902\"",  
       "name":"Fourth Coffee",  
       "accountid":"6af77a42-5f0e-e611-80e0-00155da84c03",  
       "primarycontactid":{   
          "@odata.etag":"W/\"628892\"",  
          "fullname":"Susie Curtis",  
          "jobtitle":"Coffee Master",  
          "annualincome":48000.0000,  
          "_transactioncurrencyid_value":"0d4ed62e-95f7-e511-80d1-00155da84c03",  
          "contactid":"6bf77a42-5f0e-e611-80e0-00155da84c03"  
       }  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```    
    Account 'Fourth Coffee' has primary contact 'Susie Curtis':  
            Job title: Coffee Master  
            Income: 48000    
    ```  
  
3.  Rufen Sie selektiv die dazugehörenden Aufgaben auf, die dem primären Kontakt zugeordnet werden, der im vorherigen Vorgang abgerufen wird.  Eine Erweiterung wird auf der Sammlungs-bewerteten Navigationseigenschaft `Contact_Tasks`ausgeführt.  
  
 **Anforderung** 
  
    ```http    
    GET http://[Organization URI]/api/data/v9.0/contacts(6bf77a42-5f0e-e611-80e0-00155da84c03)?$select=fullname,&$expand=Contact_Tasks($select=subject,description,scheduledstart,scheduledend) HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0   
    {   
       "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,Contact_Tasks,Contact_Tasks(subject,description,scheduledstart,scheduledend))/$entity",  
       "@odata.etag":"W/\"628892\"",  
       "fullname":"Susie Curtis",  
       "contactid":"6bf77a42-5f0e-e611-80e0-00155da84c03",  
       "Contact_Tasks":[   
          {   
             "@odata.etag":"W/\"628903\"",  
             "subject":"Sign invoice",  
             "description":"Invoice #12321",  
             "scheduledstart":"2016-04-19T00:00:00Z",  
             "scheduledend":"2016-04-19T00:00:00Z",  
             "activityid":"6cf77a42-5f0e-e611-80e0-00155da84c03"  
          },  
          {   
             "@odata.etag":"W/\"628905\"",  
             "subject":"Setup new display",  
             "description":"Theme is - Spring is in the air",  
             "scheduledstart":"2016-04-20T00:00:00Z",  
             "scheduledend":"2016-04-20T00:00:00Z",  
             "activityid":"6df77a42-5f0e-e611-80e0-00155da84c03"  
          },  
          {   
             "@odata.etag":"W/\"628907\"",  
             "subject":"Conduct training",  
             "description":"Train team on making our new blended coffee",  
             "scheduledstart":"2016-06-01T00:00:00Z",  
             "scheduledend":"2016-06-01T00:00:00Z",  
             "activityid":"6ef77a42-5f0e-e611-80e0-00155da84c03"  
          }  
       ]  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```    
    Contact 'Susie Curtis' has the following assigned tasks:  
    Subject: Sign invoice,  
            Description: Invoice #12321  
            Start: 4/19/2016  
            End: 4/19/2016  
  
    Subject: Setup new display,  
            Description: Theme is - Spring is in the air  
            Start: 4/20/2016  
            End: 4/20/2016  
  
    Subject: Conduct training  
            Description: Train team on making our new blended coffee,  
            Start: 6/1/2016  
            End: 6/1/2016    
    ```  
  
<a name="bkmk_section4"></a>
   
## <a name="section-4-associate-and-disassociate-existing-entities"></a>Abschnitt 4: Ordnen Sie bestehende Entitäten zu und heben Sie diese hervor  

In diesem Abschnitt wird gezeigt, wie vorhandene Entitätsinstanzen zugeordnet werden und die Zuordnung aufgehoben wird. Die Formung eine Zuordnung für die Verwendung einer Bezugs-URI- und eines-Beziehungsobjekt, die dann an eine POST-Anforderung gesendet werden. Die Aufhebung der Zuordnung erfordert, dass Sie einen Befehl "LÖSCHEN" an die Referenz-URL für diese Zuordnung senden.  Zuerst wird einer 1: n-Zuordnung zwischen einem Kontakt und einer Firma gebildet.  Anschließend wird eine n: n-Zuordnung zwischen einem Mitbewerber und mindestens einer Verkaufschance gebildet.  
  
1.  Fügen Sie Peter Cambel als Kontakt der Firma Fourth Coffee mithilfe der `contact_customer_accounts` Sammlung-bewerteten Navigationseigenschaft hinzu. Beachten Sie die Verwendung des Schlüssels `@odata.id`, um den zugeordneten Datensatz zu definieren.  
  
 **Anforderung** 
  
    ```http    
    POST http://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)/contact_customer_accounts/$ref HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "@odata.id": "http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03)"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Contact 'Peter Cambel' associated to account 'Fourth Coffee'.  
    ```  
  
2.  Bestätigen Sie den vorhergehenden Vorgang, indem Sie die Sammlung von Kontakten für das Konto Fourth Coffee abrufen. Die Antwort enthält das Element Array mit einem einzigen Element, das kürzlich dem Kontakt Peter Cambel hinzugefügt wurde.  
  
 **Anforderung** 
  
    ```http    
    GET http://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)/contact_customer_accounts?$select=fullname,jobtitle HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 200 OK  
    Content-Type: application/json; odata.metadata=minimal  
    OData-Version: 4.0   
    {  
      "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#contacts(fullname,jobtitle)","value":[  
        {  
          "@odata.etag":"W/\"632481\"","fullname":"Peter Cambel","jobtitle":"Senior Developer","contactid":"00b6e0e2-b010-e611-80e1-00155da84c03"  
        }  
      ]  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```    
    Contact list for account 'Fourth Coffee':  
            Name: Peter Cambel, Job title: Senior Developer    
    ```  
  
3.  Entfernen der Zuordnung, die zwischen der Firma Fourth Coffee und dem Kontakte Peter Cambel erstellt wurde.  
  
 **Anforderung** 
  
    ```http    
    DELETE http://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03)/contact_customer_accounts/$ref?$id=http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Contact 'Peter Cambel' dissociated from account 'Fourth Coffee'.  
    ```  
  
4.  Erstellen eines Mitbewerbers namens `Adventure Works`  
  
 **Anforderung** 
  
    ```http    
    POST http://[Organization URI]/api/data/v9.0/competitors HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "name": "Adventure Works",  
      "strengths": "Strong promoter of private tours for multi-day outdoor adventures"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content  
    OData-Version: 4.0  
    OData-EntityId: http://[Organization URI]/api/data/v9.0/accounts(77f77a42-5f0e-e611-80e0-00155da84c03)    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Competitor 'Adventure Works' created.  
    ```  
  
5.  Erstellen einer Verkaufschance namens `River rafting adventure`  
  
 **Anforderung** 
  
    ```http    
    POST http://[Organization URI]/api/data/v9.0/opportunities HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "name": "River rafting adventure",  
      "description": "Sales team on a river-rafting offsite and team building"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content  
    OData-Version: 4.0  
    OData-EntityId: http://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03)    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Opportunity 'River rafting adventure' created.  
    ```  
  
6.  Ordnen Sie die neue Verkaufschance diesem neuen Mitbewerber zu. Beachten Sie, dass dieselbe allgemeine Syntax in dieser m: n-Zuordnung verwendet wird, wie im vorherigen Beispiel eine 1: n-Zuordnung verwendet wurde.  
  
 **Anforderung** 
  
    ```http    
    POST http://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03)/opportunitycompetitors_association/$ref HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0  
    {  
      "@odata.id": "http://[Organization URI]/api/data/v9.0/competitors(77f77a42-5f0e-e611-80e0-00155da84c03)"  
    }    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Opportunity 'River rafting adventure' associated with competitor 'Adventure Works'.  
    ```  
  
7.  Rufen Sie selektiv alle Verkaufschancen ab, die mit dem Mitbewerber Adventure Works zugeordnet werden.  Ein Array mit einer einzelnen Verkaufschance wird zurückgegeben.  
  
 **Anforderung** 
  
    ```http    
    GET http://[Organization URI]/api/data/v9.0/competitors(77f77a42-5f0e-e611-80e0-00155da84c03)?$select=name,&$expand=opportunitycompetitors_association($select=name,description) HTTP/1.1  
    Accept: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 200 OK  
    {   
       "@odata.context":"http://[Organization URI]/api/data/v9.0/$metadata#competitors(name,opportunitycompetitors_association,opportunitycompetitors_association(name,description))/$entity",  
       "@odata.etag":"W/\"628913\"",  
       "name":"Adventure Works",  
       "competitorid":"77f77a42-5f0e-e611-80e0-00155da84c03",  
       "opportunitycompetitors_association":[   
          {   
             "@odata.etag":"W/\"628917\"",  
             "name":"River rafting adventure",  
             "description":"Sales team on a river-rafting offsite and team building",  
             "opportunityid":"7cf77a42-5f0e-e611-80e0-00155da84c03"  
          }  
       ]  
    }    
    ```  
  
 **Konsolenausgabe**  
  
    ```    
    Competitor 'Adventure Works' has the following opportunities:  
            Name: River rafting adventure,  
            Description: Sales team on a river-rafting offsite and team building    
    ```  
  
8.  So heben Sie die Zuordnung eines Mitbewerbers zu einer Verkaufschance auf:  Beachten Sie erneut, das dieselbe allgemeine Syntax verwendet wird, die auch eine 1: n-Zuordnung entfernt..  
  
 **Anforderung** 
  
    ```http    
    DELETE http://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03)/opportunitycompetitors_association/$ref?$id=http://[Token-CRM-Org-Name]/Contoso/api/data/v8.1/competitors(77f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content    
    ```  
  
 **Konsolenausgabe**  
  
    ```  
    Opportunity 'River rafting adventure' disassociated from competitor 'Adventure Works'.  
    ```  
  
<a name="bkmk_section5"></a> 
  
## <a name="section-5-delete-entities-sample-cleanup"></a>Abschnitt 5: Löschungsentitäten (Beispielbereinigung) 
 
<!-- TODO:
This section demonstrates how to delete entity instances. The corresponding message is a straightforward DELETE request that uses the URI of the entity instance to be deleted.  If the target entity has a parent-child relationship with other entities, then deleting the parent will, by default, automatically cascade delete child instances. For example, in this sample, tasks have contact as their parent. For more information, see [Entity relationship behavior](../entity-relationship-behavior.md).   -->
  
1.  Jedes Element der Sammlung der Entität der URLs wird gelöscht.  Der erste ist ein Kontaktdatensatz von Peter Cambel.  
  
 **Anforderung** 
  
    ```http
    DELETE http://[Organization URI]/api/data/v9.0/contacts(60f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    Content-Type: application/json  
    OData-MaxVersion: 4.0  
    OData-Version: 4.0    
    ```  
  
 **Antwort**  
  
    ```http    
    HTTP/1.1 204 No Content    
    ```  
  
2.  Nachfolgende Iterationen durch die Sammlung löschen die verbleibenden Datensätze.  
  
 **Anforderung** 
  
    ```http    
    DELETE http://[Organization URI]/api/data/v9.0/accounts(65f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    . . .  
  
    DELETE http://[Organization URI]/api/data/v9.0/accounts(6af77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    . . .  
  
    DELETE http://[Organization URI]/api/data/v9.0/contacts(6bf77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    . . .  
  
    DELETE http://[Organization URI]/api/data/v9.0/competitors(77f77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    . . .  
  
    DELETE http://[Organization URI]/api/data/v9.0/opportunities(7cf77a42-5f0e-e611-80e0-00155da84c03) HTTP/1.1  
    . . .    
    ```  
  
### <a name="see-also"></a>Siehe auch  

[Verwenden der Common Data Service for Apps-Web-API](overview.md)<br />
[Erstellen einer Entität mithilfe des Web-API](create-entity-web-api.md)<br />
[Abrufen einer Entität mithilfe des Web-API](retrieve-entity-using-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](update-delete-entities-using-web-api.md)<br />
[Entitäten zuordnen und Zuordnungen aufheben mithilfe der Web API](associate-disassociate-entities-using-web-api.md)<br />
[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)<br />


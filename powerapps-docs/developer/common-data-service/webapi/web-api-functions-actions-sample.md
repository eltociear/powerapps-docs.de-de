---
title: Beispiel für Web-API-Funktionen und -Aktionen (Common Data Service) | Microsoft-Dokumentation
description: Diese Beispielgruppe veranschaulicht, wie ungebundene und gebundene Funktionen und Aktionen, einschließlich benutzerdefinierter Aktionen, mit Hilfe der Common Data Service-Web-API ausgeführt werden. Diese werden mithilfe clientseitigen JavaScripts und C# implementiert.
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 953c3137-6171-4e6e-b249-6a96221c6e96
caps.latest.revision: 16
author: JimDaly
ms.reviewer: pehecke
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 531ebab75dcbac2e00004ae91fd9ff5349670382
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3154958"
---
# <a name="web-api-functions-and-actions-sample"></a>Web API-Funktionen- und Aktionen-Beispiel

Diese Beispielgruppe veranschaulicht, wie ungebundene und gebundene Funktionen und Aktionen, einschließlich benutzerdefinierter Aktionen mithilfe dem Common Data Service Web API angerufen werden. Dieses Beispiel wurde als ein separates Projekt für die folgenden Sprachen implementiert:  
  
-   [Beispiel für Funktionen und Aktionen (C#)](samples/functions-actions-csharp.md)  
  
In diesem Thema werden die Struktur und der Inhalt der Beispiele für eine slt.pätere, sprachunabhängigen Ebene behandelt. Wiederholen Sie die verknüpften Beispielthemen oben, um sprachspezifische Implementierungen und verwandte Details zu erhalten und zu sehen, wie die in diesem Thema beschriebenen Methoden verwendet werde.  
  
<a name="bkmk_demonstrates"></a>  
 
## <a name="demonstrates"></a>Demonstriert  

Dieses Beispiel wird in die folgenden Hauptabschnitte unterteilt und enthält Web-API-Funktionen und -Aktionen, die in den entsprechenden Themenabschnitten detailliert behandelt werden.  
  
|Themenabschnitt|Zugeordnete Themen|  
|-------------------|---------------------------|  
|[Beispieldaten](#bkmk_sampleData)||  
|[Verwenden von ungebundenen Funktion ohne Parameter](#bkmk_unboundFunctionNoParams)|[Ungebundene Funktionen](use-web-api-functions.md#bkmk_unboundFunctions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" />|  
|[Verwenden von ungebundenen Funktion mit Parametern](#bkmk_unboundFunctionWithParams)|[Ungebundene Funktionen](use-web-api-functions.md#bkmk_unboundFunctions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.GetTimeZoneCodeByLocalizedName?text=GetTimeZoneCodeByLocalizedName Function" />|  
|[Verwenden von gebundenen Funktion ohne Parameter](#bkmk_boundFunctionWithParams)|[Gebundene Funktionen](use-web-api-functions.md#bkmk_boundFunctions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.CalculateTotalTimeIncident?text=CalculateTotalTimeIncident Function" />|  
|[Verwenden von ungebundenen Aktionen mit Parametern](#bkmk_unboundActionWithParams)|[Ungebundene Aktionen](use-web-api-actions.md#bkmk_unboundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.opportunity?text=opportunity EntityType" />|  
|[Verwenden von gebundenen Aktionen mit Parametern](#bkmk_boundActionWithParams)|[Gebundene Aktionen](use-web-api-actions.md#bkmk_boundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" /><br /><br /> <xref href="Microsoft.Dynamics.CRM.letter?text=letter EntityType" />|  
|[Verwenden von gebundenen benutzerdefinierten Aktionen mit Parametern](#bkmk_boundCustomActionWithParams)|[Nutzen einer benutzerdefinierten Aktion](use-web-api-actions.md#bkmk_customActions)<br /><br /> [Gebundene Aktionen](use-web-api-actions.md#bkmk_boundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />|  
|[Verwenden von ungebundenen benutzerdefinierten Aktionen mit Parametern](#bkmk_unboundCustomActionWithParams)|[Nutzen einer benutzerdefinierten Aktion](use-web-api-actions.md#bkmk_customActions)<br /><br /> [Ungebundene Aktionen](use-web-api-actions.md#bkmk_unboundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.account?text=account EntityType" />|  
|[Behandlung von Ausnahmen für benutzerdefinierte Aktionen](#bkmk_boundCustomActionErrorHandling)|[Nutzen einer benutzerdefinierten Aktion](use-web-api-actions.md#bkmk_customActions)<br /><br /> [Ungebundene Aktionen](use-web-api-actions.md#bkmk_unboundActions)<br /><br /> <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />|  
  
Die folgenden Abschnitte enthalten eine kurze Diskussion zu den ausgeführten Common Data Service Web-API-Vorgängen, sowie den entsprechenden HTTP-Nachrichten und den Ausgaben, die der Konsolen zugeordnet sind.  
  
<a name="bkmk_sampleData"></a>
   
## <a name="sample-data"></a>Beispieldaten  

Um die ordnungsgemäße Ausführung der Vorgänge in diesem Beispiel, erstellen Sie zuerst Beispieldaten auf dem Common Data Service-Server. Diese Beispieldaten werden vom Server gelöscht, es sei denn, der Benutzer entscheidet sich, sie nicht zu löschen. Die Daten in diesem Beispiel werden wie folgt einzeln erstellt.  
  
- Erstellen Sie ein Konto (z. B.: `Fourth Coffee`) und ordnen Sie es einem Vorfall zu, der drei 30-minütige Aufgaben hat (insg. 90 Minuten). Nachdem die Aufgaben erstellt sind, werden sie als abgeschlossen markiert. Der Vorgang berechnet die gesamte Zeit, die zur Ausführung dieser drei Aufgaben erforderlich ist.  
  
    ```json  
    {  
      title: "Sample Case",  
      "customerid_account@odata.bind": accountUri,  
      Incident_Tasks: [  
       {  
        subject: "Task 1",  
        actualdurationminutes: 30  
       },  
       {  
        subject: "Task 2",  
        actualdurationminutes: 30  
       },  
       {  
        subject: "Task 3",  
        actualdurationminutes: 30  
       }  
      ]  
     };  
    ```  
  
- Erstellen Sie ein Konto und ordnen Sie es einer Verkaufschance zu. Diese Verkaufschance wird im Beispielvorgang als gewonnen markiert.  
  
    ```json  
    {  
     name: "Sample Account for WebAPIFunctionsAndActions sample",  
     opportunity_customer_accounts: [{  
      name: "Opportunity to win"  
     }]  
    };  
    ```  
  
- Erstellen Sie eine Brief-Aktivität. Der Brief wird im Beispielvorgang in die aktuelle Warteschlange des Benutzers hinzugefügt.  
  
    ```json  
    {  
      description: "Example letter"  
    }  
    ```  
  
- Erstellen Sie einen Kontakt, der mit einer benutzerdefinierte Aktionen `sample_AddNoteToContact` im Beispielvorgang verwendet wird.  
  
    ```json  
    {  
      firstname: "Jon",  
      lastname: "Fogg"  
    }  
    ```  
  
<a name="bkmk_sampleOperations"></a>
   
## <a name="sample-operations"></a>Beispielvorgänge  

Die Beispielvorgänge in diesem Thema werden folgendermaßen organisiert.  
  
- Verwenden von Funktionen: Diese Vorgänge zeigen gebundene und ungebundene Funktionen, die Parameter akzeptieren oder nicht.  
- Verwenden von Aktionen: Diese Vorgänge zeigen gebundene und ungebundene Aktionen, die Parameter akzeptieren oder nicht.  
- Benutzerdefinierte Aktionen: Diese Vorgänge zeigen gebundene und ungebundene Aktionen und die Verarbeitung von benutzerdefinierte Fehlerausnahmen.  
  
<a name="bkmk_workingWithFunctions"></a> 
  
## <a name="working-with-functions"></a>Verwenden von Funktionen  

[Funktionen](web-api-types-operations.md#bkmk_functions) sind Operationen, die keine Nebenwirkungen haben. Eine Funktion kann an eine Entitätsinstanz oder eine Entitätssammlung gebunden werden. Abfragefunktionen sind niemals gebunden. Weitere Informationen finden Sie unter [Verwenden von Web-API-Funktionen](use-web-api-functions.md). Dieser Abschnitt enthält Beispiele zur Verwendung von gebundenen und ungebundenen Funktionen und zur Übergabe von Parametern.  
  
<a name="bkmk_unboundFunctionNoParams"></a>  
 
### <a name="using-unbound-function-with-no-parameters"></a>Verwenden von ungebundenen Funktion ohne Parameter 
 
Verwenden Sie eine ungebundene Feature, um den aktuellen vollständigen Namen des Benutzers aus, wenn Sie das <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> ausnutzen. Dieser Vorgang veranschaulicht, wie Sie eine ungebundene Funktion aufrufen, die keine Parameter annimmt. Dieser Vorgang gibt den vollständigen Namen des aktuellen Benutzers zurück.  
  
Abrufen des Anforderung und Antwort für die <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" />.  
  
 **Anforderung**  
  
```http  
GET https://[Organization URI]/api/data/v9.0/WhoAmI HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8   
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 273  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.WhoAmIResponse",  
   "BusinessUnitId":"0d6cc84a-d3f6-e511-80d0-00155da84802",  
   "UserId":"b08dc84a-d3f6-e511-80d0-00155da84802",  
   "OrganizationId":"0f47eae2-a906-4ae4-9215-f09875979f6a"  
}  
```  
  
<a name="bkmk_unboundFunctionWithParams"></a>
   
### <a name="using-unbound-function-with-parameters"></a>Verwenden von ungebundenen Funktion mit Parametern  

Verwenden Sie eine ungebundene Funktion, um den Zeitzonencode abzurufen. Dieser Vorgang veranschaulicht, wie Sie eine ungebundene Funktion aufrufen, die Parameter annimmt. Dieser Vorgang gibt den Zeitzonencode für die angegebene Zeitzone zurück. Weitere Informationen: [Übergeben von Parametern an eine Funktion](use-web-api-functions.md#bkmk_passParametersToFunctions)  
  
 **Anforderung**  
  
```http  
GET https://[Organization URI]/api/data/v9.0/GetTimeZoneCodeByLocalizedName(LocalizedStandardName=@p1,LocaleId=@p2)?@p1='Pacific%20Standard%20Time'&@p2=1033 HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8 
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 154  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.GetTimeZoneCodeByLocalizedNameResponse",  
   "TimeZoneCode":4  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Unbound function: GetTimeZoneCodeByLocalizedName  
    Function returned time zone Pacific Standard Time, with code '4'.  
```  
  
<a name="bkmk_boundFunctionWithParams"></a>
   
### <a name="using-bound-function-with-no-parameters"></a>Verwenden von gebundenen Funktion ohne Parameter  

Verwenden Sie eine gebundene Funktion, um die vollständige Zeit zu erhalten, die für alle Aufgaben eines Vorfalls erforderlich war. Dieser Vorgang veranschaulicht, wie Sie eine gebundene Funktion aufrufen, die keine Parameter annimmt. Dieser Vorgang wird die Gesamtanzahl von Minuten zurück, die der Vorfall für alle zugehörigen Aufgaben erforderte. Die Funktion verwendet außerdem die Vorfalldaten, die Sie für das Beispielprogramm erstellen haben. Weitere Informationen: [Gebundene Funktionen](use-web-api-functions.md#bkmk_boundFunctions)  
  
 **Anforderung**  
  
```http  
GET https://[Organization URI]/api/data/v9.0/incidents(3d920da5-fb4a-e611-80d5-00155da84802)/Microsoft.Dynamics.CRM.CalculateTotalTimeIncident() HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
  
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 148  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.CalculateTotalTimeIncidentResponse",  
   "TotalTime":90  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Bound function: CalculateTotalTimeIncident  
    Function returned 90 minutes - total duration of tasks associated with the incident.  
```  
  
<a name="bkmk_workingWithActions"></a> 
  
## <a name="working-with-actions"></a>Verwenden von Aktionen  

[Aktionen](web-api-types-operations.md#bkmk_actions) sind Operationen, die Nebenwirkungen zulassen. Ein Aktion ist entweder gebunden oder ungebunden. Weitere Informationen finden Sie unter [Verwenden von Web-API-Aktionen](use-web-api-actions.md). Dieser Abschnitt enthält Beispiele zur Verwendung von gebundenen und ungebundenen Aktionen und zur Übergabe von Parametern. Er zeigt außerdem, wie benutzerdefinierte Aktionen verwenden werden und wie Ausnahmen dieser benutzerdefinierten Aktionen behandelt werden.  
  
<a name="bkmk_unboundActionWithParams"></a>
   
### <a name="using-unbound-action-with-parameters"></a>Verwenden von ungebundenen Aktionen mit Parametern 
 
Verwenden Sie eine ungebundene Aktion, die einen Satz Parameter verarbeitet. Dieser Vorgang umfasst eine Verkaufschance und markiert sie über den Aufruf von <xref href="Microsoft.Dynamics.CRM.WinOpportunity?text=WinOpportunity Action" /> als gewonnen. Der <xref href="Microsoft.Dynamics.CRM.opportunity?text=opportunity EntityType" /> wurde als Beispieldaten vorher im Programm erstellt. Weitere Informationen: [Ungebundene Aktionen](use-web-api-actions.md#bkmk_unboundActions)  
  
 **Anforderung**  
  
```http  
POST https://[Organization URI]/api/data/v9.0/WinOpportunity HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
  
{  
   "Status":3,  
   "OpportunityClose":{  
      "subject":"Won Opportunity",  
      "opportunityid@odata.bind":"https://[Organization URI]/api/data/v9.0/opportunities(47920da5-fb4a-e611-80d5-00155da84802)"  
   }  
}  
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 204 No Content  
OData-Version: 4.0   
```  
  
 **Konsolenausgabe**  
  
```  
Unbound Action: WinOpportunity  
    Opportunity won.  
```  
  
<a name="bkmk_boundActionWithParams"></a>
   
### <a name="using-bound-action-with-parameters"></a>Verwenden von gebundenen Aktionen mit Parametern
  
Verwenden Sie eine gebundene Aktion, die einen Satz Parameter verarbeitet. Dieser Vorgang fügt einen Brief zur Warteschlange des aktuellen Benutzers hinzu. Um dies zu erzielen, verwenden wir die <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" /> und <xref href="Microsoft.Dynamics.CRM.systemuser?text=systemuser EntityType" />, um einen Verweis auf die aktuellen Warteschlange des Benutzers zu erhalten.  Wir benötigen auch Verweis auf den <xref href="Microsoft.Dynamics.CRM.letter?text=letter EntityType" />. Der Brief wurde als Beispieldaten vorher im Programm erstellt. Anschließend wird die gebundene <xref href="Microsoft.Dynamics.CRM.AddToQueue?text=AddToQueue Action" /> aufgerufen, um den Brief der Warteschlange des aktuellen Benutzers hinzuzufügen. Weitere Informationen: [Gebundene Aktionen](use-web-api-actions.md#bkmk_boundActions)  
  
 **Anforderung**  
  
```http  
POST https://[Organization URI]/api/data/v9.0/queues(1f7bcc50-d3f6-e511-80d0-00155da84802)/Microsoft.Dynamics.CRM.AddToQueue HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 110  
  
{  
   "Target":{  
      "activityid":"4c920da5-fb4a-e611-80d5-00155da84802",  
      "@odata.type":"Microsoft.Dynamics.CRM.letter"  
   }  
}  
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 170  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.AddToQueueResponse",  
   "QueueItemId":"67bdfabd-fc4a-e611-80d5-00155da84802"  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Bound Action: AddToQueue  
    QueueItemId returned from AddToQueue Action: 67bdfabd-fc4a-e611-80d5-00155da84802  
```  
  
<a name="bkmk_customActions"></a> 
  
## <a name="working-with-custom-actions"></a>Verwenden von benutzerdefinierten Aktionen  

Wenn Sie benutzerdefinierte Aktionen in Ihrer Lösung definieren, können Sie diese über die Common Data Service-Web-API aufrufen. Unabhängig davon, ob die Vorgänge in der benutzerdefinierten Aktion Nebenwirkungen haben, können sie möglicherweise Daten ändern und gelten daher eher als Aktionen und nicht als Funktionen. Es gibt keine Möglichkeit, eine benutzerdefinierte Funktion zu erstellen. Weitere Informationen: [Eine benutzerdefinierte Aktion verwenden](use-web-api-actions.md#bkmk_customActions).  
  
Dieses Beispiel verfügt über zwei benutzerdefinierte Aktionen. Sie erfordern beide Parameter. Eine ist gebunden und die andere ungebunden.  
  
- `sample_AddNoteToContact`: Eine gebundene benutzerdefinierte Aktion, die zwei Parameter verarbeitet. Einer ist ein `NoteTitle` und der andere ist ein `NoteText`. Diese benutzerdefinierte Aktion für einem <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> eine Notiz hinzu. Unten finden Sie ein Screenshot der **Informationen**-Seite dieser benutzerdefinierten Aktion.  
  
 <!-- TODO:
 ![Custom Action &#45; AddNoteToContact information](../media/custom-action-add-note-contact.PNG "Custom Action - AddNoteToContact information")   -->
  
- `sample_CreateCustomer`: Eine ungebundene benutzerdefinierte Aktion, die verschiedene Parameter erfordert (je nach Typ des zu erstellenden Kunden). Wenn beispielsweise `AccountType` "Firma" ist, dann ist nur der `AccountName`-Parameter erforderlich. Wenn `AccountType` "Kontakt" ist, sind die Parameter `ContactFirstName` und `ContactLastName` erforderlich. Unten finden Sie ein Screenshot der **Informationen**-Seite dieser benutzerdefinierten Aktion.  
<!-- TODO:  
 ![Custom Action &#45; CreateCustomer information](../media/custom-action-create-customer.PNG "Custom Action - CreateCustomer information")  
   -->
<a name="bkmk_boundCustomActionWithParams"></a>
   
### <a name="using-bound-custom-action-with-parameters"></a>Verwenden von gebundenen benutzerdefinierten Aktionen mit Parametern 
 
Dieses Beispiel ruft die benutzerdefinierte Aktion `sample_AddNoteToContact` auf, die an die Kontaktentität mit den benötigten Parametern gebunden ist. Diese benutzerdefinierte Aktion für eine Notiz zu einem vorhanden Kontakt hinzu. Diese Aktion gibt eine Entität mit einer `annotationid`-Eigenschaft zurück. Um das Hinzufügen der Notiz anzuzeigen, wird die `annotationid` verwendet, um Informationen zur Notiz anzufordern.  
  
Die Anfrage und Antwort der Aktion.  
  
 **Anforderung**  
  
```http  
POST https://[Organization URI]/api/data/v9.0/contacts(4d920da5-fb4a-e611-80d5-00155da84802)/Microsoft.Dynamics.CRM.sample_AddNoteToContact HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 80  
  
{  
   "NoteTitle":"The Title of the Note",  
   "NoteText":"The text content of the note."  
}  
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 200 OK  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 149  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#annotations/$entity",  
   "annotationid":"ba146d0b-fd4a-e611-80d5-00155da84802"  
}  
```  
  
 Die Anfrage und Antwort der Notiz (Annotation).  
  
 **Anforderung**  
  
```http  
GET https://[Organization URI]/api/data/v9.0/annotations(ba146d0b-fd4a-e611-80d5-00155da84802)?$select=subject,notetext&$expand=objectid_contact($select=fullname) HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
  
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 200 OK  
OData-Version: 4.0  
Content-Length: 450  
  
{  
   "@odata.context":"https://[Organization URI]/api/data/v9.0/$metadata#annotations(subject,notetext,objectid_contact,objectid_contact(fullname))/$entity",  
   "@odata.etag":"W/\"622978\"",  
   "subject":"The Title of the Note",  
   "notetext":"The text content of the note.",  
   "annotationid":"ba146d0b-fd4a-e611-80d5-00155da84802",  
   "objectid_contact":{  
      "@odata.etag":"W/\"622968\"",  
      "fullname":"Jon Fogg",  
      "contactid":"4d920da5-fb4a-e611-80d5-00155da84802"  
   }  
}  
```  
  
 **Konsolenausgabe**  
  
```http  
Custom action: sample_AddNoteToContact  
    A note with the title 'The Title of the Note' and the content 'The text content of the note.' was created and associated with the contact Jon Fogg.  
```  
  
<a name="bkmk_unboundCustomActionWithParams"></a> 
  
### <a name="using-unbound-custom-action-with-parameters"></a>Verwenden von ungebundenen benutzerdefinierten Aktionen mit Parametern  

Dieser Vorgang ruft die benutzerdefinierte Aktion `sample_CreateCustomer` auf, um einen "Firmen"-Kunden zu erstellen. Die erforderliche Parameter sind `CustomerType` mit dem Wert `account`.  
  
 **Anforderung**  
  
```http  
POST https://[Organization URI]/api/data/v9.0/sample_CreateCustomer HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 103  
  
{  
   "CustomerType":"account",  
   "AccountName":"Account Customer Created in WebAPIFunctionsAndActions sample"  
}  
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 204 No Content  
OData-Version: 4.0  
  
```  
  
<a name="bkmk_boundCustomActionErrorHandling"></a> 
  
### <a name="handling-custom-action-exceptions"></a>Behandlung von Ausnahmen für benutzerdefinierte Aktionen  

Dieses Beispiel wird angezeigt, das benutzerdefinierte Aktionen benutzerdefinierten Fehlermeldungen zurückgeben können. Sie verarbeiten benutzerdefinierte Ausnahmen genauso wie Standardausnahmen. Um die benutzerdefinierte Fehlermeldung aus der benutzerdefinierten Aktion `sample_CreateCustomer` zu erhalten, erstellt dieses Beispiel einen "Kontakt"-Kunden. Allerdings übergeben wir absichtlich die falsche Parameter für den `CustomerType`-Parameter. Dieser Vorgang fängt dann die Ausnahme ab und zeigt die Fehlermeldung an. Dann führt das Beispielprogramm fort.  
  
 **Anforderung**  
  
```http  
POST https://[Organization URI]/api/data/v9.0/sample_CreateCustomer HTTP/1.1  
OData-MaxVersion: 4.0  
OData-Version: 4.0  
Content-Type: application/json; charset=utf-8  
Content-Length: 103  
  
{  
   "CustomerType":"contact",  
   "AccountName":"Account Customer Created in WebAPIFunctionsAndActions sample"  
}  
```  
  
 **Antwort**  
  
```http  
HTTP/1.1 500 Internal Server Error  
Content-Type: application/json; odata.metadata=minimal  
OData-Version: 4.0  
Content-Length: 2760  
  
{  
   "error":{  
      "code":"",  
      "message":"ContactFirstName and ContactLastName are required when CustomerType is contact.",  
      "innererror":{  
         "message":"ContactFirstName and ContactLastName are required when CustomerType is contact.",  
         ...[truncated]  
      }  
   }  
}  
```  
  
 **Konsolenausgabe**  
  
```  
Expected custom error: ContactFirstName and ContactLastName are required when CustomerType is contact.  
```  
  
### <a name="see-also"></a>Siehe auch  

[Verwenden der Common Data Service-Web-API](overview.md)<br />
[Nutzen von Web-API-Funktionen](use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](use-web-api-actions.md)<br />
[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](samples/functions-actions-csharp.md)<br />


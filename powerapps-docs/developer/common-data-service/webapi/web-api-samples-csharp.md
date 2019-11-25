---
title: Beispiele für Web-API-Datenvorgänge (C#) (Common Data Service) | Microsoft Docs
description: Dieses Thema enthält eine Beschreibung verschiedener Web-API-Beispiele, die mit C# implementiert werden
ms.custom: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 66e26684-819e-45f7-bec4-c250be4d6fed
caps.latest.revision: 14
author: JimDaly
ms.author: jdaly
ms.reviewer: susikka
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7f253c8585d7bac93ed08b4d33637c9c9d7960d3
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2753634"
---
# <a name="web-api-data-operations-samples-c"></a>Beispiele für Web-API-Datenvorgänge (C#)

Dieses Thema enthält Informationen zu den Web-API-Beispielen in C#. Jedes Beispiel beschäftigt sich mit einem anderen Aspekt der Common Data Service-Web-API. Merkmale und Struktur sind ähnlich.  
  
> [!NOTE]
> Dieser Implementierungsansatz verwendet eine Objekterstellung auf niedriger Ebene und explizite HTTP-Nachrichtenaufrufe. Diese Ansatz ermöglicht das Steuern von Objekteigenschaften auf unterer Ebene, die das Verhalten der Web-API steuern. Dies unterstützt Sie dabei, die internen Arbeitsweise zu verstehen. Es ist jedoch nicht notwendigerweise ein Ansatz für die beste Entwicklerproduktivitätserfahrung.  
>
> Übergeordnete Bibliotheken wie die [OData-Bibliothek](https://msdn.microsoft.com/library/hh525392\(v=vs.103\).aspx) dagegen abstrahieren einen großen Teil der Low-Level-Clientlogik.  Die [OData T4-Vorlage](https://blogs.msdn.microsoft.com/odatateam/2012/07/02/trying-out-the-prerelease-odata-client-t4-template/) kann optional in Verbindung mit der OData-Bibliothek verwendet werden, um Cliententitätsklassen automatisch zu generieren.  

<a name="bkmk_prerequisites"></a>
   
## <a name="prerequisites"></a>Voraussetzungen

Das Folgende wird benötigt, um Common Data Service-Web-API C#-Beispiele zu erstellen und auszuführen:  
  
- Eine Version von Microsoft Visual Studio 2015 oder höher.  Eine kostenlose [Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)-Version steht [hier](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) zum Download bereit.  

- Zugriff auf Common Data Service mit Rechten, CRUD-Vorgänge auszuführen.  
 
- Um die Beispiele gegen Common Data Service ausführen, müssen Sie die Anwendung mit Azure Active Directory registrieren, um eine Client-ID und eine Umleitungs-URL zu erhalten. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Registrieren einer Common Data Service-App bei Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).

> [!NOTE]
> Diese Beispiele erfordern die Version 2.x von Assembly [Microsoft.IdentityModel.Client.ActiveDirectory](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory?view=azure-dotnet) für OAuth-basierte Authentifizierung.
  
<a name="bkmk_webApiSamplesListing"></a>

## <a name="web-api-samples-listing-c"></a>Web-API-Beispiel (C#)

Die folgende Tabelle enthält Beispiele in C#.  Jedes Beispiel wird allgemein in einem entsprechenden Beispielgruppenthema beschrieben, das sich auf die HTTP-Anforderung und die Antwortnachrichten im Thema [Web-API-Beispiele](web-api-samples.md) konzentriert.  
  
|Probe|Beispielgruppe|Beschreibung|  
|------------|------------------|-----------------|  
|[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)|[Beispiel grundlegender Web-API-Operationen](web-api-basic-operations-sample.md)|Veranschaulicht, wie Common Data Service Entitätsdatensätze erstellt, abgerufen, aktualisiert, gelöscht zugeordnet und aufgehoben werden.|  
|[Web API-Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)|[Web API-Abfragedatenbeispiel](web-api-query-data-sample.md)|Veranschaulicht, wie OData v4 Abfragensyntax und -Funktionen und Common Data Service Abfragefunktionen verwendet werden. Enthält Beispiele zur Arbeit mit vordefinierten Abfragen und die Verwendung von FetchXML, um Abfragen ausführen.|  
|[Beispiel bedingter Web-API-Operationen (C#)](samples/conditional-operations-csharp.md)|[Beispiel bedingter Web-API-Operationen](web-api-conditional-operations-sample.md)|Veranschaulicht, wie Sie bedingte Operationen ausführen, die mit ETag-Kriterien angegeben werden.|  
|[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](samples/functions-actions-csharp.md)|[Web API-Funktionen- und Aktionen-Beispiel](web-api-functions-actions-sample.md)|Veranschaulicht, wie Sie gebundene/ungebundene Funktionen und Aktionen, einschließlich benutzerdefinierte Aktionen verwenden.|  
  
<a name="bkmk_howDownloadRun"></a>

## <a name="how-to-download-and-run-the-samples"></a>Herunterladen und ausführen der Beispiele
  
Der Quellcode für jedes Sample ist auf [GitHub](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23) verfügbar. Sie können das Repository als Zip-Datei herunterladen, die die Lösungsdateien für die Samples enthält. Weitere Informationen finden Sie im Abschnitt **Ausführen dieses Beispiels** in jedem Beispielthema.  
  
### <a name="utilized-libraries-and-frameworks"></a>Verwendete Bibliotheken und Frameworks

Diese C#-Implementierung hängt von den folgenden Faktoren ab:
  
- Die Standard-.NET Framework HTTP-Messagingklassen, die im [System.Net.Http-Namespace](/dotnet/api/system.net.http) enthalten sind, insbesondere [HttpClient](/dotnet/api/system.net.http.httpclient), [HttpRequestMessage](/dotnet/api/system.net.http.httprequestmessage) und[HttpResponseMessage](/dotnet/api/system.net.http.httpresponsemessage) werden für das HTTP-Messaging verwendet.  
  
- Die Newtonsoft [Json.NET](https://www.newtonsoft.com/json)-Bibliothek, die das JSON-Datenformat unterstützt.  
  
#### <a name="jsonnet-library"></a>Json.NET-Bibliothek

In C# und die meisten sonstigen verwalteten Sprachen das JSON-Datenformat nicht nativ unterstützen, ist die aktuelle beste Methode, eine Bibliothek für diese Funktionen zu verwenden. Weitere Informationen finden Sie unter [Eine Einführung zur JavaScript-Objektnotation (JSON) in JavaScript und in .NET](https://msdn.microsoft.com/library/bb299886.aspx). Json.NET ist eine beliebte Wahl für .NET-Projekte. Es stellt ein robustes, performantes Open-Source-Framework ([MIT-Lizenz](https://opensource.org/licenses/MIT)) für das Serialisieren, Konvertieren, Analysieren, Abfragen sowie zum Formatieren von JSON-Daten bereit. Weitere Informationen finden Sie in der [Json.NET-Dokumentation](https://www.newtonsoft.com/json/help/html/Introduction.htm).  
  
In den C#-Beispielen wird dieser Bibliothek vor allem zur Serialisierung von Daten zwischen .NET-Objekten und HTTP-Nachrichtentexten genutzt. Obwohl die Bibliothek mehrere Möglichkeiten bereitstellt, um diese Aufgabe zu erfüllen, nutzen die Beispiele eine Vorgehensweise, bei der individuelle [JObject](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)-Instanzen für Common Data Service-Entitätsinstanzen (Datensätze) erstellt werden.  Beispielsweise erstellt der folgende Code die Variable `contact1`, die eine Instanz von Common Data Service <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> darstellt, und stellt dann Werte für ausgewählte Eigenschaften für den Typ bereit.  
  
```csharp  
  
JObject contact1 = new JObject();  
contact1.Add("firstname", "Peter");  
contact1.Add("lastname", "Cambel");  
contact1.Add("annualincome", 80000);  
contact1["jobtitle"] = "Junior Developer";  
  
```  
  
 Die Verwendung der Klammernotation in der letzten Anweisung entspricht der [Hinzufügen](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_Linq_JObject_Add.htm)-Methode. Diese Instanziierung kann auch über die statische Methode [Parse](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_Linq_JObject_Parse.htm) erfolgen:  
  
```csharp  
  
JObject contact1 = JObject.Parse(@"{firstname: 'Peter', lastname: 'Cambel', "  
+ @"annualincome: 80000, jobtitle: 'Junior Developer'}");  
  
```  
  
 Da `JObject` ein allgemeiner JSON-Typ ist, arbeitet es mit vielen Typüberprüfungen zur Laufzeit.  Beispielsweise ist die folgende Anweisung syntaktisch gültig. Sie führt jedoch möglicherweise zu Laufzeitfehlern, da <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> keine `age`-Eigenschaft enthält.  
  
 `contact1.Add("age", 37);    //Possible error--no age property exists in contact!`  
  
 Sobald die Entitätsvariable initialisiert wurde, kann sie mithilfe von System.Net.Http-Klassen in einem Nachrichtentext gesendet werden. Beispielsweise:  
  
```csharp  
  
HttpRequestMessage createrequest1 = new HttpRequestMessage(HttpMethod.Post, client.BaseAddress + "contacts");
createrequest1.Content = new StringContent(contact1.ToString());
createrequest1.Content.Headers.ContentType = MediaTypeHeaderValue.Parse("application/json");
HttpResponseMessage createResponse1 = client.SendAsync(createrequest1, HttpCompletionOption.ResponseHeadersRead).Result; 
  
```  
  
 Sie können auch JObject-Instanzen erstellen, indem Sie bei der Entitätsinstanzen während Abfragevorgängen deserialisieren. Beispielsweise:  
  
```csharp  
  
//contact2Uri contains a reference to an existing CRM contact instance.  
string queryOptions = "?$select=fullname,annualincome,jobtitle,description";
HttpResponseMessage retrieveResponse1 = client.GetAsync(contact1Uri + queryOptions, HttpCompletionOption.ResponseHeadersRead).Result;
if (retrieveResponse1.IsSuccessStatusCode) //200
   {
     retrievedcontact1 = JObject.Parse(retrieveResponse1.Content.ReadAsStringAsync().Result);
     Console.WriteLine("Contact '{0}' retrieved: \n\tAnnual income: {1}" + "\n\tJob title: {2} \n\tDescription: {3}.",

// Can use either indexer or GetValue method (or a mix of two)
retrievedcontact1.GetValue("fullname"),
retrievedcontact1["annualincome"],
retrievedcontact1["jobtitle"],
retrievedcontact1["description"]);   //description is initialized empty.
    }
else
{
Console.WriteLine("Failed to retrieve contact for reason: {0}",retrieveResponse1.ReasonPhrase);
throw new Exception(string.Format("Failed to retrieve contact for reason: {0}", retrieveResponse1.Content));
 } 

```
  
### <a name="response-success-and-error-handling"></a>Erfolgreiche Antwort und Fehlerbehandlung

Im Allgemeinen nutzen die Beispiele eine einfachen Methode zum Verarbeiten von HTTP-Antworten. Wenn die Anfrage erfolgreich ist, werden Informationen über den Vorgang der Regel per Konsole ausgegeben. Ob die Antwort eine JSON-Nutzlast oder nützliche Header enthält, werden diese Informationen nur bei Erfolg verarbeitet. Wenn eine Common Data Service-Entität erstellt wurde, wird die `entityUris`-Sammlung mit der URI dieser Ressource aktualisiert. Die `DeleteRequiredRecords`-Methode nutzt die Sammlung, um optional vom Beispiel auf dem Common Data Service-Server erstellten Daten zu löschen.  
  
Wenn die Anforderung fehlschlägt, gibt das Programm eine kontextbezogene Nachricht über den fehlgeschlagenen Vorgang aus und löst dann eine benutzerdefinierte Ausnahme des Typs `Exception` aus. Der Ausnahmehandler gibt mehr Informationen zur Ausnahme aus und dann wird die Kontrolle an einen `finally`-Block übergeben, der eine Bereinigungslogik enthält. Dies ist wieder ein Anruf von `DeleteRequiredRecords` Der folgende Code zeigt diesen Fehlerbehandlungsansatz einer POST-Anfrage zur Erstellung eines Datensatzes.  
  
```csharp
  
if (response.StatusCode == HttpStatusCode.NoContent)  //204  
{  
Console.WriteLine("POST succeeded, entity created!");  
//optionally process response message headers or body here, for example:  
entityUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();  
entityUris.Add(entityUri);  
}  
else  
{  
Console.WriteLine("Operation failed: {0}", response.ReasonPhrase);  
throw new Exception(string.Format(" Operation Failed", response.Content));  
}  
  
```  

 [HttpStatusCode](https://msdn.microsoft.com/library/hh435235.aspx).NoContent entspricht einem HTTP-Statuscode 204 “No content” (Kein Inhalt). Hier zeigt der Statuscode, dass die POST-Anfrage erfolgreich war. Weitere Informationen finden Sie unter [Zusammenstellen von HTTP-Anforderungen und Fehlerbehandlung](https://msdn.microsoft.com/library/gg334391.aspx).  
  
### <a name="characteristics-and-methods"></a>Eigenschaften und Methoden
  
Die meisten Beispiele nutzen dieselben allgemeinen Architekturmuster mit den folgenden Eigenschaften:  
  
- Der C#-Beispielcode befindet sich in der entsprechenden primären Quelldatei namens `SampleProgram.cs`. Diese enthält eine einzelne Klasse mit demselben Namen wie das Beispielprojekt.  
  
- Die Beispiele sind großzügig kommentiert: Zusammenfassungen werden auf Klassen- und Methodenebenen bereitgestellt, und auch die meisten wichtigen Anweisungen sind kommentiert.  Ergänzende Dateien, z. B. die Anwendungskonfigurationsdatei `App.config`, enthalten häufig wichtige Kommentare.  
   
### <a name="see-also"></a>Siehe auch  

[Verwenden der Common Data Service-Web-API](overview.md)<br />
[Web API Beispiele](web-api-samples.md)<br />
[Web API Beispiele (Clientseitiges JavaScript)](web-api-samples-client-side-javascript.md)<br />
[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)<br />
[Web API-Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)<br />
[Beispiel bedingter Web-API-Operationen (C#)](samples/conditional-operations-csharp.md)<br />
[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](samples/functions-actions-csharp.md)

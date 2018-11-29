---
title: 'Beispiele für Web-API-Datenvorgänge (C#) (Common Data Service für Apps) | Microsoft Docs'
description: 'Dieses Thema enthält eine Beschreibung verschiedener Web-API-Beispiele, die mit C# implementiert werden'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 66e26684-819e-45f7-bec4-c250be4d6fed
caps.latest.revision: 14
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-data-operations-samples-c"></a>Beispiele für Web-API-Datenvorgänge (C#)

Dieses Thema enthält Informationen zu den Web-API-Beispielen in C#. Jedes Beispiel beschäftigt sich mit einem anderen Aspekt der "Common Data Service für Apps"-Web-API. Merkmale und Struktur sind ähnlich.  
  
> [!NOTE]
>  Dieser Implementierungsansatz verwendet eine Objekterstellung auf niedriger Ebene und explizite HTTP-Nachrichtenaufrufe. Diese Ansatz ermöglicht das Steuern von Objekteigenschaften auf unterer Ebene, die das Verhalten der Web-API steuern. Dies unterstützt Sie dabei, die internen Arbeitsweise zu verstehen. Es ist jedoch nicht notwendigerweise ein Ansatz für die beste Entwicklerproduktivitätserfahrung.  
>   
>  Übergeordnete Bibliotheken wie die [OData-Bibliothek](https://msdn.microsoft.com/library/hh525392\(v=vs.103\).aspx) dagegen abstrahieren einen großen Teil der Low-Level-Clientlogik.  Die [OData T4-Vorlage](https://blogs.msdn.microsoft.com/odatateam/2012/07/02/trying-out-the-prerelease-odata-client-t4-template/) kann optional in Verbindung mit der OData-Bibliothek verwendet werden, um Cliententitätsklassen automatisch zu generieren.  

<a name="bkmk_prerequisites"></a>
   
## <a name="prerequisites"></a>Voraussetzungen

Folgendes wird benötigt, um die "Common Data Service für Apps"-Web-API-C#-Beispiele auszuführen:  
  
-   Eine Version von Microsoft Visual Studio 2015 oder höher.  Eine kostenlose [Visual Studio Community](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)-Version steht [hier](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) zum Download bereit.  
  
-   Eine Internetverbindung, um die referenzierten NuGet-Pakete herunterzuladen und zu aktualisieren.  
  
-   Zugriff auf Common Data Service für Apps mit Rechten, CRUD-Vorgänge auszuführen.  
  
<!-- TODO:
-   In order to run samples against CDS for Apps, you must register your application with Azure Active Directory to obtain a client ID and redirect URL. For more information, see [Walkthrough: Register a Common Data Service for Apps app with Azure Active Directory](../walkthrough-register-app-azure-active-directory.md).   -->

> [!NOTE]
> Diese Beispiele erfordern die Version 2.x von Assembly [Microsoft.IdentityModel.Client.ActiveDirectory](https://docs.microsoft.com/en-us/dotnet/api/microsoft.identitymodel.clients.activedirectory?view=azure-dotnet) für OAuth-basierte Authentifizierung.
  
<a name="bkmk_webApiSamplesListing"></a>

## <a name="web-api-samples-listing-c"></a>Web-API-Beispiel (C#)

Die folgende Tabelle enthält Beispiele in C#.  Jedes Beispiel wird allgemein in einem entsprechenden Beispielgruppenthema beschrieben, das sich auf die HTTP-Anforderung und die Antwortnachrichten im Thema [Web-API-Beispiele](web-api-samples.md) konzentriert.  
  
|Probe|Beispielgruppe|Beschreibung|  
|------------|------------------|-----------------|  
|[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)|[Beispiel grundlegender Web-API-Operationen](web-api-basic-operations-sample.md)|Veranschaulicht, wie "Common Data Service für Apps"-Entitätsdatensätze erstellt, abgerufen, aktualisiert, gelöscht zugeordnet und deren Zuordnungen aufgehoben werden.|  
|[Web API-Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)|[Web API-Abfragedatenbeispiel](web-api-query-data-sample.md)|Veranschaulicht, wie "OData v4"-Abfragensyntax und -Funktionen sowie "Common Data Service für Apps"-Abfragefunktionen verwendet werden. Enthält Beispiele zur Arbeit mit vordefinierten Abfragen und die Verwendung von FetchXML, um Abfragen ausführen.|  
|[Beispiel bedingter Web-API-Operationen (C#)](samples/conditional-operations-csharp.md)|[Beispiel bedingter Web-API-Operationen](web-api-conditional-operations-sample.md)|Veranschaulicht, wie Sie bedingte Operationen ausführen, die mit ETag-Kriterien angegeben werden.|  
|[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](samples/functions-actions-csharp.md)|[Web API-Funktionen- und Aktionen-Beispiel](web-api-functions-actions-sample.md)|Veranschaulicht, wie Sie gebundene/ungebundene Funktionen und Aktionen, einschließlich benutzerdefinierte Aktionen verwenden.|  
  
<a name="bkmk_howDownloadRun"></a>

## <a name="how-to-download-and-run-the-samples"></a>Herunterladen und ausführen der Beispiele
  
Der Quellcode für jedes Beispiel ist in der [MSDN-Codegalerie](https://code.msdn.microsoft.com/site/search?f%5b0%5d.type=user&f%5b0%5d.value=microsoft%20dynamics%20crm%20sdk%20documentation%20team) verfügbar. Der Link, um jedes Beispiels herunterzuladen ist in dem Beispielthema enthalten. Der Beispieldownload ist eine komprimierten ZIP-Datei, die die Visual Studio 2015-Lösungsdateien zum Beispiel beinhaltet. Weitere Informationen Sie im Abschnitt **Dieses Beispiel ausführen** im jeweiligen Beispielthema.  
  
<a name="bkmk_commonElements"></a>

## <a name="common-elements-found-in-each-sample"></a>Allgemeine Elemente in jedem Beispiel

Die meisten Beispiele haben eine vergleichbare Struktur und umfassen häufige Methoden und Ressourcen, um die grundlegenden Infrastruktur für ein Web-API C#-Programm bereitzustellen.  
  
Viele dieser allgemeinen Elemente sind auch vorhanden, wenn Sie eine neue Lösung erstellen, die auf die "CDS für Apps"-Web-API zugreift. Weitere Informationen finden Sie unter [Starten eines Web-API-Projekts in Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md).  
  
### <a name="utilized-libraries-and-frameworks"></a>Verwendete Bibliotheken und Frameworks
 
Diese C#-Implementierung hängt vom folgenden Hilfecode für die HTTP-Kommunikation, Anwendungskonfiguration, Authentifizierung, Fehlerbehandlung und JSON-Serialisierung ab.  
  
-   Die Standard-.NET Framework HTTP-Messagingklassen, die im [System.Net.Http-Namespace](/dotnet/api/system.net.http) enthalten sind, insbesondere [HttpClient](/dotnet/api/system.net.http.httpclient), [HttpRequestMessage](/dotnet/api/system.net.http.httprequestmessage) und[HttpResponseMessage](/dotnet/api/system.net.http.httpresponsemessage) werden für das HTTP-Messaging verwendet.  
  
-   Die "Common Data Service für Apps"-Web-API Hilfsprogrammbibliothek wird verwendet, um die Anwendungskonfigurationsdatei zu lesen, beim "CDS für Apps"-Server zu authentifizieren und die Fehlerbehandlung während des Vorgangs zu unterstützen.  Weitere Informationen finden Sie unter [Verwenden der "Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
-   Die Newtonsoft [Json.NET](http://www.newtonsoft.com/json)-Bibliothek unterstützt das JSON-Datenformat.  
  
#### <a name="jsonnet-library"></a>Json.NET-Bibliothek

In C# und die meisten sonstigen verwalteten Sprachen das JSON-Datenformat nicht nativ unterstützen, ist die aktuelle beste Methode, eine Bibliothek für diese Funktionen zu verwenden. Weitere Informationen finden Sie unter [Eine Einführung zur JavaScript-Objektnotation (JSON) in JavaScript und in .NET](https://msdn.microsoft.com/library/bb299886.aspx). Json.NET ist eine beliebte Wahl für .NET-Projekte. Es stellt ein robustes, performantes Open-Source-Framework ([MIT-Lizenz](https://opensource.org/licenses/MIT)) für das Serialisieren, Konvertieren, Analysieren, Abfragen sowie zum Formatieren von JSON-Daten bereit. Weitere Informationen finden Sie in der [Json.NET-Dokumentation](http://www.newtonsoft.com/json/help/html/Introduction.htm).  
  
In den C#-Beispielen wird dieser Bibliothek vor allem zur Serialisierung von Daten zwischen .NET-Objekten und HTTP-Nachrichtentexten genutzt. Obwohl die Bibliothek mehrere Möglichkeiten bereitstellt, um diese Aufgabe zu erfüllen, nutzen die Beispiele eine Vorgehensweise, bei der individuelle [JObject](http://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_Linq_JObject.htm)-Instanzen für "Common Data Service für Apps"-Entitätsinstanzen (Datensätze) erstellt werden.  Beispielsweise erstellt der folgende Code die Variable `contact1`, die eine "Common Data Service für Apps"-<xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" />-Instanz darstellt, und stellt dann Werte für ausgewählte Eigenschaften für den Typ bereit.  
  
```csharp  
  
JObject contact1 = new JObject();  
contact1.Add("firstname", "Peter");  
contact1.Add("lastname", "Cambel");  
contact1.Add("annualincome", 80000);  
contact1["jobtitle"] = "Junior Developer";  
  
```  
  
 Die Verwendung der Klammernotation in der letzten Anweisung entspricht der [Hinzufügen](http://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_Linq_JObject_Add.htm)-Methode. Diese Instanziierung kann auch über die statische Methode [Parse](http://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_Linq_JObject_Parse.htm) erfolgen:  
  
```csharp  
  
JObject contact1 = JObject.Parse(@"{firstname: 'Peter', lastname: 'Cambel', "  
+ @"annualincome: 80000, jobtitle: 'Junior Developer'}");  
  
```  
  
 Da `JObject` ein allgemeiner JSON-Typ ist, arbeitet es mit vielen Typüberprüfungen zur Laufzeit.  Beispielsweise ist die folgende Anweisung syntaktisch gültig. Sie führt jedoch möglicherweise zu Laufzeitfehlern, da <xref href="Microsoft.Dynamics.CRM.contact?text=contact EntityType" /> keine `age`-Eigenschaft enthält.  
  
 `contact1.Add("age", 37);    //Possible error--no age property exists in contact!`  
  
 Sobald die Entitätsvariable initialisiert wurde, kann sie mithilfe von System.Net.Http-Klassen in einem Nachrichtentext gesendet werden. Beispielsweise:  
  
```csharp  
  
HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Post, "contacts");  
request.Content = new StringContent(contact1.ToString(), Encoding.UTF8, "application/json");  
HttpResponseMessage response = await httpClient.SendAsync(request1);  
  
```  
  
 Sie können auch JObject-Instanzen erstellen, indem Sie bei der Entitätsinstanzen während Abfragevorgängen deserialisieren. Beispielsweise:  
  
```csharp  
  
//contact2Uri contains a reference to an existing CRM contact instance.  
string queryOptions = "?$select=fullname,annualincome,jobtitle,description";  
HttpResponseMessage response = await httpClient.GetAsync(contact2Uri + queryOptions);  
JObject contact2 = JsonConvert.DeserializeObject<JObject>(await response.Content.ReadAsStringAsync());  
  
```  
  
### <a name="response-success-and-error-handling"></a>Erfolgreiche Antwort und Fehlerbehandlung

Im Allgemeinen nutzen die Beispiele eine einfachen Methode zum Verarbeiten von HTTP-Antworten. Wenn die Anfrage erfolgreich ist, werden Informationen über den Vorgang der Regel per Konsole ausgegeben. Ob die Antwort eine JSON-Nutzlast oder nützliche Header enthält, werden diese Informationen nur bei Erfolg verarbeitet. Wenn letztlich eine "Common Data Service für Apps"-Entität erstellt wurde, wird die `entityUris`-Sammlung mit der URI dieser Ressource aktualisiert. Die [DeleteRequiredRecords](#bkmk_deleteRequiredRecords)-Methode nutzt die Sammlung, um optional Daten, die durch das Beispiel erstellt wurden, auf Ihrem "Common Data Service für Apps"-Server zu löschen.  
  
Wenn die Anforderung fehlschlägt, gibt das Programm eine kontextbezogene Nachricht über den fehlgeschlagenen Vorgang aus und löst dann eine benutzerdefinierte Ausnahme des Typs `CrmHttpResponseException` aus. Der Ausnahmehandler gibt mehr Informationen zur Ausnahme aus und dann wird die Kontrolle an einen `finally`-Block übergeben, der eine Bereinigungslogik enthält. Dies ist wieder ein Anruf von `DeleteRequiredRecords` Der folgende Code zeigt diesen Fehlerbehandlungsansatz einer POST-Anfrage zur Erstellung eines Datensatzes.  
  
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
throw new CrmHttpResponseException(response.Content);  
}  
  
```  
  
 [HttpStatusCode](https://msdn.microsoft.com/library/hh435235.aspx).NoContent entspricht einem HTTP-Statuscode 204 “No content” (Kein Inhalt). Hier zeigt der Statuscode, dass die POST-Anfrage erfolgreich war. Weitere Informationen finden Sie unter [Zusammenstellen von HTTP-Anforderungen und Fehlerbehandlung](https://msdn.microsoft.com/en-us/library/gg334391.aspx).  
  
### <a name="characteristics-and-methods"></a>Eigenschaften und Methoden
  
Die meisten Beispiele nutzen dieselben allgemeinen Architekturmuster mit den folgenden Eigenschaften:  
  
- Der C#-Beispielcode befindet sich in der entsprechenden primären Quelldatei namens `Program.cs`. Diese enthält eine einzelne Klasse mit demselben Namen wie das Beispielprojekt.  
  
- Die Beispielklassen und die ["Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek](use-microsoft-dynamics-365-web-api-helper-library-csharp.md) befinden sich im Namespace `Microsoft.Crm.Sdk.Samples`.  
  
- Die Beispiele sind großzügig kommentiert: Zusammenfassungen werden auf Klassen- und Methodenebenen bereitgestellt, und auch die meisten wichtigen Anweisungen sind kommentiert.  Ergänzende Dateien, z. B. die Anwendungskonfigurationsdatei `App.config`, enthalten häufig wichtige Kommentare.  
  
- Die primäre Beispielklasse ist so strukturiert, dass sie den folgenden allgemeinen Methodensatz enthält: [Main](#bkmk_main), [ConnectToCRM](#bkmk_connectToCrm), [CreateRequiredRecords](#bkmk_createRequiredRecords), [RunAsync](#bkmk_runAsync), [DisplayException](#bkmk_displayException) und [DeleteRequiredRecords](#bkmk_deleteRequiredRecords).  
  
<a name="bkmk_main"></a>
   
#### <a name="main-method"></a>Main-Methode

Definitionsgemäß beginnt mit dieser Methode die Ausführung des Beispiels.  Sie enthält ausschließlich Ablaufsteuerungs- und Ausnahmebehandlungslogik auf hoher Ebene, häufig den folgenden Code:  
  
```csharp  
  
static void Main(string[] args)  
{  
FunctionsAndActions app = new FunctionsAndActions();  
try  
{  
//Read configuration file and connect to specified CRM server.  
app.ConnectToCRM(args);  
app.CreateRequiredRecords();  
Task.WaitAll(Task.Run(async () => await app.RunAsync()));  
}  
catch (System.Exception ex) { DisplayException(ex);  
}  
finally  
{  
if (app.httpClient != null)  
{  
app.DeleteRequiredRecords(true);  
app.httpClient.Dispose();  
}  
Console.WriteLine("Press <Enter> to exit the program.");  
Console.ReadLine();  
}  
}  
  
```  
  
<a name="bkmk_connectToCrm"></a>

#### <a name="connecttocrm-method"></a>ConnectToCRM-Methode
 
Diese Methode ruft die Hilfsprogrammbibliotheken auf, um die Anwendungskonfigurationsdatei zu lesen und richtet dann dann eine Verbindung zum angegebenen "Common Data Service für Apps"-Server ein. Das Ergebnis dieser Schritte ist die Initialisierung einer [HttpClient](https://msdn.microsoft.com/en-us/library/system.net.http.httpclient\(v=vs.110\).aspx)-Klasseneigenschaft, die während des Programms verwendet wird, um Web-Anforderungen zu senden und Antworten zu empfangen.  Beachten Sie, dass die folgenden Eigenschaften für dieses Objekt festgelegt werden:  
  
```csharp  
  
//Define the Web API address, the max period of execute time, the Odata  
// version, and the expected response payload format.  
httpClient.BaseAddress = new Uri(config.ServiceUrl + "api/data/v8.1/");  
httpClient.Timeout = new TimeSpan(0, 2, 0);  // 2 minute timeout  
httpClient.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");  
httpClient.DefaultRequestHeaders.Add("OData-Version", "4.0");  
httpClient.DefaultRequestHeaders.Accept.Add(new MediaTypeWithQualityHeaderValue("application/json"));  
  
```  
  
 Weitere Informationen zur Beispielanwendungskonfiguration und Authentifizierung finden Sie unter [Verwenden der "Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
<a name="bkmk_createRequiredRecords"></a>

#### <a name="createrequiredrecords-method"></a>CreateRequiredRecords-Methode
 
Diese Methode erstellt und initialisiert die Entitätsdatensätze, die das Beispiel benötigt. Jedoch nur, wenn die entsprechenden Vorgänge nicht zum primären Thema des Beispiels gehören.  Das [Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md) enthält beispielsweise diese Methode nicht, da es im Beispiel primär um die Datensatzerstellung geht.  
  
<a name="bkmk_runAsync"></a>

#### <a name="runasync-method"></a>RunAsync-Methode

Diese asynchrone Methode enthält entweder den entsprechenden Quellcode, oder, für längere Programme, ruft die Methoden auf, die den Beispielcode gruppieren. In enthaltene Code wird über eingebettete Kommentare und Kommentar im Abschnitt **Anmerkungen** des entsprechenden Beispielthemas erläutert.  
  
<a name="bkmk_displayException"></a>
  
#### <a name="displayexception-method"></a>DisplayExceptions-Methode

Diese Hilfsmethode zeigt die Ausnahmeinformationen (inkl. der internen Ausnahmen) über die Standardkonsole an.  
  
<a name="bkmk_deleteRequiredRecords"></a>
  
#### <a name="deleterequiredrecords-method"></a>DeleteRequiredRecords-Methode

Diese Begleitermethode löscht optional die Beispieldatensätze und andere "Common Data Service für Apps"-Serverressourcen, die im Programm und insbesondere über die [CreateRequiredRecords](#bkmk_createRequiredRecords)-Methode erstellt wurden. Sie holte eine Überprüfung des Vorgangs über den Benutzer ein, durchläuft dann die `entityUris`-Sammlung, und versucht, jedes Element mit einer HTTPS- DELETE-Nachricht zu löschen.  
  
### <a name="see-also"></a>Siehe auch  

[Verwenden der Common Data Service for Apps-Web-API](overview.md)<br />
[Web API Beispiele](web-api-samples.md)<br />
[Web API Beispiele (Clientseitiges JavaScript)](web-api-samples-client-side-javascript.md)<br />
[Beispiel grundlegender Web-API-Operationen (C#)](samples/basic-operations-csharp.md)<br />
[Web API-Abfragedatenbeispiel (C#)](samples/query-data-csharp.md)<br />
[Beispiel bedingter Web-API-Operationen (C#)](samples/conditional-operations-csharp.md)<br />
[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](samples/functions-actions-csharp.md)

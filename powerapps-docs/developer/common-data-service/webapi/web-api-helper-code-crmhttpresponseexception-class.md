---
title: 'Web-API-Hilfsprogrammcode: CrmHttpResponseException-Klasse (Common Data Service für Apps) | Microsoft Docs'
description: 'Die CrmHttpResponseExceptions-Klasse wird verwendet, um HTTP-Statusfehler darzustellen, die während "Common Data Service für Apps"-Web-API-Aufrufen generiert werden'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 8deb0bc5-6f4a-4ca7-a3a2-75c06dc7f967
caps.latest.revision: 11
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-helper-code-crmhttpresponseexception-class"></a>Web API-Hilfecode: CrmHttpResponseException-Klasse

Verwenden Sie die `CrmHttpResponseException`-Klasse, um [HTTP-Statusfehler](https://msdn.microsoft.com/library/gg334391.aspx) darzustellen, die während "Common Data Service für Apps"-Web-API-Aufrufen generiert werden.  Diese Klasse ist von der Standard-.NET-System.[Exception](https://msdn.microsoft.com/library/system.exception.aspx)-Klasse abgeleitet, um einfach in Ihre vorhandenen Ausnahmebehandlungssmechanismen integriert werden zu können. Allgemeinere Informationen finden Sie unter [Ausnahmen behandeln und auslösen](https://docs.microsoft.com/en-us/dotnet/standard/exceptions/index).  
  
Die `CrmHttpResponseException`-Klasse befindet sich in der Datei "Exceptions.cs" in der [CRM SDK-Web-API-Hilfe-Bibliothek](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode/).  Er wird ausführlich in den anderen Hilfebibliotheksklassen und den C#-Web-API-Beispielen verwendet. Weitere Informationen finden Sie unter [Verwenden der "Common Data Service für Apps"-Web-API-Hilfsprogrammbibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md).  
  
Diese Klasse verwendet die JSON-Zeichenfolgebehandlungsfunktion der Open-Source [Json.NET](http://www.newtonsoft.com/json)-Bibliothek.  
  
## <a name="class-members"></a>Klassenmitglieder  

Die folgende Tabelle gibt Aufschluss über öffentliche Mitglieder der `CrmHttpResponseException`-Klasse.  
  
<!-- TODO:
|||  
|-|-|  
|![Common Data Service for Apps Web API Helper Library&#45;CrmHttpResponseException Class Diagram](../media/web-api-helper-library-crm-exception-class-diagram.png "Common Data Service for Apps Web API Helper Library-CrmHttpResponseException Class Diagram")|**CrmHttpResponseException  class**<br /><br /> *Properties:*<br /><br /> `StackTrace` – the string representation of the immediate frames on the Common Data Service for Apps server’s call stack when the exception was thrown, if available.<br /><br /> *Methods*:<br /><br /> The constructors initialize an instance of this class, and require a [HttpContent](https://msdn.microsoft.com/library/hh193687\(v=vs.110\).aspx) parameter and an optional inner exception parameter.<br /><br /> `ExtractMessageFromContent` – this static method extracts the error message from the specified HTTP content parameter.|  
   -->
## <a name="usage"></a>Verwendung  

Normalerweise erstellen Sie ein `CrmHttpResponseException`-Objekt und lösen es aus, wenn Sie einen Statusfehler verarbeiten, der mit einer HTTP-Antwort-Nachricht zurückgegeben wird. Der folgende Code löst beispielsweise eine solche Fehlermeldung aus, wenn der <xref href="Microsoft.Dynamics.CRM.WhoAmI?text=WhoAmI Function" />-Aufruf fehlschlägt.  
  
```csharp  
response = await httpClient.GetAsync("WhoAmI", HttpCompletionOption.ResponseContentRead);  
if (!response.IsSuccessStatusCode)  
{   
    throw new CrmHttpResponseException(response.Content);   
}  
```  
  
 Sie können die ausgegebenen `CrmHttpResponseException`-Objekte abfangen und verarbeiten wie bei andere Standard-.NET-Ausnahmen.  
  
> [!IMPORTANT]
>  Wenn Sie die HttpResponseMessage.[EnsureSuccessStatusCode](/dotnet/api/system.net.http.httpresponsemessage.ensuresuccessstatuscode)-Methode verwenden, um automatisch HTTP-Antwortfehler zu konvertieren, die in [HttpRequestException](/dotnet/api/system.net.http.httprequestexception)-Objekten ausgelöst werden, schließt dieser Ansatz die Verwendung der `CrmHttpResponseException`-Klasse aus. Beachten Sie, dass, wenn Sie diesen Ansatz nutzen, viele der Antwortnachrichtendetails, einschließlich des Statuscodes, während der Ausnahmebehandlung nicht verfügbar sind.  
  
## <a name="class-listing"></a>Klassenlisten

 Den aktuellen Code für diese Klasse finden Sie im [CRM SDK-Web-API-Hilfebibliothek](https://www.nuget.org/packages/Microsoft.CrmSdk.WebApi.Samples.HelperCode) NuGet-Paket.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Net.Http;  
using Newtonsoft.Json;  
using Newtonsoft.Json.Linq;  
  
namespace Microsoft.Crm.Sdk.Samples.HelperCode  
{  
    /// <summary>  
    /// Produces a populated exception from an error message in the content of an HTTP response.   
    /// </summary>  
    public class CrmHttpResponseException : System.Exception  
    {  
        #region Properties  
        private static string _stackTrace;  
  
        /// <summary>  
        /// Gets a string representation of the immediate frames on the call stack.  
        /// </summary>  
        public override string StackTrace  
        {  
            get { return _stackTrace; }  
        }  
        #endregion Properties  
  
        #region Constructors  
        /// <summary>  
        /// Initializes a new instance of the CrmHttpResponseException class.  
        /// </summary>  
        /// <param name="content">The populated HTTP content in Json format.</param>  
        public CrmHttpResponseException(HttpContent content)  
            : base(ExtractMessageFromContent(content)) { }  
  
        /// <summary>  
        /// Initializes a new instance of the CrmHttpResponseException class.  
        /// </summary>  
        /// <param name="content">The populated HTTP content in Json format.</param>  
        /// <param name="innerexception">The exception that is the cause of the current exception, or a null reference  
        /// if no inner exception is specified.</param>  
        public CrmHttpResponseException(HttpContent content, Exception innerexception)  
            : base(ExtractMessageFromContent(content), innerexception) { }  
  
        #endregion Constructors  
  
        #region Methods  
        /// <summary>  
        /// Extracts the CRM specific error message and stack trace from an HTTP content.   
        /// </summary>  
        /// <param name="content">The HTTP content in Json format.</param>  
        /// <returns>The error message.</returns>  
        private static string ExtractMessageFromContent(HttpContent content)  
        {  
            string message = String.Empty;  
            string downloadedContent = content.ReadAsStringAsync().Result;  
            if (content.Headers.ContentType.MediaType.Equals("text/plain"))  
            {  
                message = downloadedContent;  
            }  
            else if (content.Headers.ContentType.MediaType.Equals("application/json"))  
            {  
                JObject jcontent = (JObject)JsonConvert.DeserializeObject(downloadedContent);  
                IDictionary<string, JToken> d = jcontent;  
  
                // An error message is returned in the content under the 'error' key.   
                if (d.ContainsKey("error"))  
                {  
                    JObject error = (JObject)jcontent.Property("error").Value;  
                    message = (String)error.Property("message").Value;  
                }  
                else if (d.ContainsKey("Message"))  
                    message = (String)jcontent.Property("Message").Value;  
  
                if (d.ContainsKey("StackTrace"))  
                    _stackTrace = (String)jcontent.Property("StackTrace").Value;  
            }  
            else if (content.Headers.ContentType.MediaType.Equals("text/html"))  
            {  
                message = "HTML content that was returned is shown below.";  
                message += "\n\n" + downloadedContent;  
            }  
            else  
            {  
                message = String.Format("No handler is available for content in the {0} format.",    
                    content.Headers.ContentType.MediaType.ToString());  
            }  
            return message;  
            #endregion Methods  
        }  
    }  
}  
  
```  
  
### <a name="see-also"></a>Siehe auch

[Erste Schritte mit dem Web API (C#)](get-started-dynamics-365-web-api-csharp.md)<br />
[Starten eines Web-API-Projekts in Visual Studio (C#)](start-web-api-project-visual-studio-csharp.md)<br />
[Verwenden der Common Data Service für Apps-Web-API-Hilfe-Bibliothek (C#)](use-microsoft-dynamics-365-web-api-helper-library-csharp.md)<br />
[Hilfecode: Authentifizierungsklasse](web-api-helper-code-authentication-class.md)<br />
[Hilfscode: Konfigurationsklasse](web-api-helper-code-configuration-classes.md)

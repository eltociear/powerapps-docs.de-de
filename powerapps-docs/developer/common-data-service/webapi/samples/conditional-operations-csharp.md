---
title: 'Beispiel bedingter Web-API-Operationen (C#) (Common Data Service für Apps) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie Sie bedingte Operationen mit der Common Data Service for Apps-Web-API und C# ausführen'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: 48a6322c-51f3-4368-ae7b-748d0c771a82
caps.latest.revision: 17
author: KumarVivek
ms.author: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-conditional-operations-sample-c"></a>Beispiel bedingter Web-API-Operationen (C#)

Dieses Beispiel veranschaulicht, wie Sie bedingte Vorgänge mit der CDS for Apps-Web-API und C# ausführen.  
  
> [!NOTE]
>  Dieses Beispiel implementiert den Common Data Service für Apps-Operationen und -Konsolenausgaben, der in [Beispiel bedingter Web-API-Operationen](../web-api-conditional-operations-sample.md) beschrieben ist, und verwendet die in [Web API Beispiele (C#)](../web-api-samples-csharp.md) beschriebenen gemeinsamen C#-Konstrukte.  
  
<a name="bkmk_Prereqs"></a>

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzungen für alle CDS for Apps-Web-API C#-Beispiele werden im Abschnitt [Voraussetzungen](../web-api-samples-csharp.md#bkmk_prerequisites) des übergeordneten Themas [Web API Beispiele (C#)](../web-api-samples-csharp.md) aufgeführt.  
  
<a name="bkmk_RunSample"></a>
 
## <a name="run-this-sample"></a>Beispiel ausführen

Um das Beispiel auszuführen:  
  
1.  Gehen Sie zu [Bedingte Web-API-Operationen für Microsoft CRM (C#)](http://go.microsoft.com/fwlink/p/?LinkId=824045), laden Sie die Datei "Microsoft CRM Web API Conditional Operations Sample (CS).zip" herunter und extrahieren Sie die Datei in einen Ordner auf dem Computer. Dieser Ordner sollte die folgenden Datei enthalten:  
  
    |Datei|Beschreibung|  
    |----------|-----------------|  
    |Program.cs|Enthält den primären Quellcode für dieses Beispiel.|  
    |App.config|Die Anwendungskonfigurationsdatei, die Platzhalter für CDS for Apps-Server-Verbindungsinformationen enthält.|  
    |ConditionalOperations.sln<br /> ConditionalOperations.csproj<br /> Packages.config<br /> AssemblyInfo.cs|Die Standard-Visual Studio-Lösung, das Projekt, das NuGet-Paket und Assemblyinformationsdateien für dieses Beispiel.|  
  
2.  Doppelklicken Sie auf die Datei "ConditionalOperations.sln", um die Lösung in Visual Studio zu öffnen.  
  
3.  Erstellen Sie die Lösung (**Erstellen** > **Lösung erstellen**). Dies sollte alle erforderlichen NuGet-Pakete automatisch herunterladen und aktualisieren.  
  
4.  Bearbeiten Sie die Datei "App.Config" in der Lösung, um Ihre CDS for Apps-Serverinstanz anzugeben, mit der Sie dieses Beispiel ausführen wollen.  
  
5.  Führen Sie das Projekt aus.  Alle Beispielprojekte sind für die Ausführung im Debugmodus konfiguriert.  
  
     Die Beispielcodeausgabe wird in einem Konsolenfenster angezeigt.  
  
<a name="bkmk_CodeSample"></a>

## <a name="code-sample"></a>Codebeispiel

 `Program.cs`  
  
```csharp  
using Microsoft.Crm.Sdk.Samples.HelperCode;  
using Newtonsoft.Json;  
using Newtonsoft.Json.Linq;  
using System;  
using System.Net;  
using System.Linq;  
using System.Text;  
using System.Collections.Generic;  
using System.Net.Http;  
using System.Net.Http.Headers;  
using System.Threading.Tasks;  
  
namespace Microsoft.Crm.Sdk.Samples  
{  
    /// <summary>  
    /// This program performs conditional operations using the ETag property during Web  
    /// API calls in Microsoft CRM or later.   
    /// </summary>  
    /// <remarks>  
    /// Etags can be used in the following general areas:  
    /// - Optimize state retrieval (conditional GETs).  
    /// - Control upsert operations, either by preventing create operations (update only)   
    ///   or by preventing updates (create only).  
    /// - Ensure optimistic concurrency in delete or update operations.  
    ///  
    /// Before building this application, you must first modify the following configuration   
    /// information in the app.config file:  
    ///   - All deployments: Provide connection string service URL's for your organization.  
    ///   - CRM (online): Replace the app settings with the correct values for your Azure   
    ///                 application registration.   
    /// See the provided app.config file for more information.   
    /// </remarks>  
    class ConditionalOperations  
    {  
        // Variables used in the sample  
        private HttpClient httpClient;      // Client to CRM server communication  
        private JObject account;            // Sample CRM entity instance  
        private string accountUri;          // Sample instance absolute URI  
        private string queryOptions;        // Select clause to filter the record retrievals  
        private string initialAcctETagVal;  // The initial ETag value of the account created     
        private string updatedAcctETagVal;  // The ETag value of the account after it is updated  
  
        /// <summary>   
        /// Primary method that demonstrates Microsoft CRM Web API  
        /// Conditional operations.   
        /// </summary>  
        public async Task RunAsync()  
        {  
            HttpRequestMessage request;  
            HttpResponseMessage response;  
  
            #region Conditional GET              
            Console.WriteLine("\n--Conditional GET section started--");  
            // Attempt to retrieve using conditional GET with current ETag value.  
            request = new HttpRequestMessage(HttpMethod.Get, accountUri + queryOptions);  
  
            // Retrieve only if it doesn't match previously retrieved version.  
            request.Headers.Add("If-None-Match", initialAcctETagVal);  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.NotModified)  // 304; expected.  
            {  
                Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);  
                Console.WriteLine("Expected outcome: Entity was not modified so nothing was returned.");  
            }  
  
            else if (response.StatusCode == HttpStatusCode.OK)  // 200; not expected  
            {  
                Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);  
                account = JsonConvert.DeserializeObject<JObject>(  
                    await response.Content.ReadAsStringAsync());  
                Console.WriteLine(account.ToString(Formatting.Indented));  
            }  
  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            // Modify the account instance by updating telephone1  
            String accountPhoneUri = String.Format("{0}/{1}", accountUri, "telephone1");  
            JObject phoneProperty = new JObject();  
            phoneProperty.Add("value", "555-0001");  
            response = await SendAsJsonAsync(httpClient, HttpMethod.Put, accountPhoneUri,  
                phoneProperty);  
            if (response.StatusCode == HttpStatusCode.NoContent)  
            {  
                Console.WriteLine("\nAccount telephone number updated.");  
            }  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            // Reattempt conditional GET with original ETag value.               
            request = new HttpRequestMessage(HttpMethod.Get, accountUri + queryOptions);  
            request.Headers.Add("If-None-Match", initialAcctETagVal);  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.OK) //200; expected  
            {  
                Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);  
            }  
            else if (response.StatusCode == HttpStatusCode.NotModified) // 304; not expected  
            {  
                Console.WriteLine("Unexpected status code: '{0}'.", (int)response.StatusCode);  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
  
            // Retrieve and output current account state.  
            account = JsonConvert.DeserializeObject<JObject>(  
            await response.Content.ReadAsStringAsync());  
            updatedAcctETagVal = account["@odata.etag"].ToString(); // Capture updated ETag  
            Console.WriteLine(account.ToString(Formatting.Indented));  
  
            #endregion Conditional GET  
  
            #region Optimistic concurrency on delete and update  
            Console.WriteLine("\n--Optimistic concurrency section started--");  
  
            // Attempt to delete original account (if matches original ETag value).  
            request = new HttpRequestMessage(HttpMethod.Delete, accountUri);  
            request.Headers.Add("If-Match", initialAcctETagVal); // If you replace "initialAcctETagVal" with "updatedAcctETagVal",   
                                                                 // delete will succeed.  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; Precondition failed error expected  
            {  
                Console.WriteLine("Expected Error: The version of the existing record doesn't match the property provided.");  
                Console.WriteLine("\tAccount not deleted using ETag '{0}', status code: '{1}'.",  
                    initialAcctETagVal, (int)response.StatusCode);  
            }  
            else if (response.IsSuccessStatusCode) // 200-299; not expected  
            {  
                Console.WriteLine("Account deleted!");  
            }  
  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            //Attempt to update account (if matches original ETag value).  
            JObject accountUpdate = new JObject();  
            accountUpdate.Add("telephone1", "555-0002");  
            accountUpdate.Add("revenue", 6000000);  
            request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);  
            request.Content = new StringContent(accountUpdate.ToString(),  
                Encoding.UTF8, "application/json");  
            request.Headers.Add("If-Match", initialAcctETagVal);  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; //Precondition failed error expected  
            {  
                Console.WriteLine("Expected Error: The version of the existing record doesn't match the property provided.");  
                Console.WriteLine("\tAccount not updated using ETag '{0}', status code: '{1}'.",  
                  initialAcctETagVal, (int)response.StatusCode);  
            }  
            else if (response.StatusCode == HttpStatusCode.NoContent)  // 204; not expected  
            {  
                Console.WriteLine("Account updated using ETag: {0}, status code: '{1}'.",  
                initialAcctETagVal, (int)response.StatusCode);  
            }  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            // Reattempt update if matches current ETag value.  
            accountUpdate["telephone1"] = "555-0003";  
            request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);  
            request.Content = new StringContent(accountUpdate.ToString(),  
                Encoding.UTF8, "application/json");  
            request.Headers.Add("If-Match", updatedAcctETagVal);  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.NoContent) // 204; expected  
            {  
                Console.WriteLine("\nAccount successfully updated using ETag: {0}, status code: '{1}'.",  
                updatedAcctETagVal, (int)response.StatusCode);  
            }  
            else if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; not expected  
            {  
                Console.WriteLine("Unexpected status code: '{0}'", (int)response.StatusCode);  
            }  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            // Retrieve and output current account state.  
            account = GetCurrentRecord(accountUri, queryOptions);  
            updatedAcctETagVal = account["@odata.etag"].ToString(); //Capture updated ETag  
            Console.WriteLine(account.ToString(Formatting.Indented));  
  
            #endregion Optimistic concurrency on delete and update  
  
            #region Controlling upsert operations  
            Console.WriteLine("\n--Controlling upsert operations section started--");  
            //Attempt to insert without update some properties for this account  
            accountUpdate = new JObject();  
            accountUpdate.Add("telephone1", "555-0004");  
            accountUpdate.Add("revenue", 7500000);  
  
            request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);  
            request.Content = new StringContent(accountUpdate.ToString(),  
                Encoding.UTF8, "application/json");  
            //Perform operation only if matching resource does not exist.   
            request.Headers.Add("If-None-Match", "*");  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; expected  
            {  
                Console.WriteLine("Expected Error: A record with matching key values already exists.");  
                Console.WriteLine("\tAccount not updated using ETag '{0}, status code: '{1}'.",  
                    initialAcctETagVal, (int)response.StatusCode);  
            }  
            else if (response.StatusCode == HttpStatusCode.NoContent) // 204; unexpected  
            {  
                Console.WriteLine("Account updated using If-None-Match '*'");  
            }  
  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            //Attempt to perform same update without creation.   
            accountUpdate["telephone1"] = "555-0005";  
            request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);  
            request.Content = new StringContent(accountUpdate.ToString(),  
                Encoding.UTF8, "application/json");  
            //Perform operation only if matching resource exists.   
            request.Headers.Add("If-Match", "*");  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.NoContent)  // 204; expected  
            {  
                Console.WriteLine("Account updated using If-Match '*'");  
            }  
            else if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412; not expected  
            {  
                Console.WriteLine("Account not updated using If-Match '*', status code: '{0}'.",  
                  (int)response.StatusCode);  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
  
            //Retrieve and output current account state.  
            account = GetCurrentRecord(accountUri, queryOptions);  
            Console.WriteLine(account.ToString(Formatting.Indented));  
  
            // Delete the account record  
            HttpResponseMessage deleteResponse;  
            deleteResponse = httpClient.DeleteAsync(accountUri).Result;  
            if (deleteResponse.IsSuccessStatusCode) // 200-299  
            {  
                Console.WriteLine("\nAccount was deleted.");  
            }  
            else if (deleteResponse.StatusCode == HttpStatusCode.NotFound)  
            // 404; entity record may have been deleted by another user.  
            {  
                Console.WriteLine("Account could not be found.");  
            }  
            else // Failed to delete  
            {  
                // Throw last failure.  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            // Attempt to update it  
            accountUpdate["telephone1"] = "555-0006";  
            request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);  
            request.Content = new StringContent(accountUpdate.ToString(),  
                Encoding.UTF8, "application/json");  
  
            // Perform operation only if matching resource exists.   
            request.Headers.Add("If-Match", "*");  
            response = await httpClient.SendAsync(request);  
  
            if (response.StatusCode == HttpStatusCode.PreconditionFailed ||  
                     response.StatusCode == HttpStatusCode.NotFound)  // 412 or 404; expected  
            {  
                Console.WriteLine("Expected Error: Account with Id = {0} does not exist.", account["accountid"]);  
                Console.WriteLine("Account not updated because it does not exist, status code: '{0}'.",  
                  (int)response.StatusCode);  
            }  
            else if (response.StatusCode == HttpStatusCode.NoContent)  // 204; not expected                                                                         
            {  
                Console.WriteLine("Account upserted using If-Match '*'");  
            }  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            #endregion Controlling upsert operations  
        }  
  
        /// <summary> Main method for the ConditionalOperations project. </summary>  
        /// <param name="args">  
        /// Command line arguments, first is the optional connection string name.  
        /// </param>  
        static void Main(string[] args)  
        {  
            ConditionalOperations app = new ConditionalOperations();  
            try  
            {  
                Console.WriteLine("-- Sample started --");  
                app.ConnectToCRM(args);       // Read configuration file and connect to the specified CRM instance.  
                app.CreateRequiredRecords();  // Create sample records for the sample  
                Task.WaitAll(Task.Run(async () => await app.RunAsync()));  
            }  
            catch (System.Exception ex)  
            { DisplayException(ex); }  
            finally  
            {  
                if (app.httpClient != null)  
                {  
                    app.httpClient.Dispose();  
                }  
                Console.WriteLine("\nPress <Enter> to exit the program.");  
                Console.ReadLine();  
            }  
        }  
  
        /// <summary>  
        /// Obtains the connection information from the application's configuration file,  
        /// and uses this info to connect to the specified CRM service.  
        /// </summary>  
        /// <param name="args">Command line arguments</param>  
        private void ConnectToCRM(String[] cmdargs)  
        {  
            // Create a helper object to read app.config for service URL and application   
            // registration settings.  
            Configuration config = null;  
            if (cmdargs.Length > 0)  
                config = new FileConfiguration(cmdargs[0]);  
            else  
                config = new FileConfiguration(null);  
  
            // Create a helper object to authenticate the user with this connection info.  
            Authentication auth = new Authentication(config);  
  
            // Next use a HttpClient object to connect to specified CRM Web service.  
            httpClient = new HttpClient(auth.ClientHandler, true);  
  
            // Define the Web API base address, the max period of execute time, the   
            // default OData version, and the default response payload format.  
            httpClient.BaseAddress = new Uri(config.ServiceUrl + "api/data/v8.1/");  
            httpClient.Timeout = new TimeSpan(0, 2, 0);  
            httpClient.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");  
            httpClient.DefaultRequestHeaders.Add("OData-Version", "4.0");  
            httpClient.DefaultRequestHeaders.Accept.Add(  
                new MediaTypeWithQualityHeaderValue("application/json"));  
        }  
  
        /// <summary> Creates the CRM entity instance used by this sample. </summary>  
        private void CreateRequiredRecords()  
        {  
            // Create a CRM account record.  
            Console.WriteLine("\nCreate sample data");  
            account = new JObject();  
            account.Add("name", "Contoso Ltd");  
            account.Add("telephone1", "555-0000"); //Phone number value will increment with each update attempt  
            account.Add("revenue", 5000000);  
            account.Add("description", "Parent company of Contoso Pharmaceuticals, etc.");  
            HttpResponseMessage response = SendAsJsonAsync(httpClient, HttpMethod.Post,  
                "accounts", account).Result;  
            if (response.StatusCode == HttpStatusCode.NoContent)  
            {  
                accountUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();                  
            }  
            else  
            {  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            // Retrieve the account record you created.  
            queryOptions = "?$select=name,revenue,telephone1,description";  
            account = GetCurrentRecord(accountUri, queryOptions);  
            Console.WriteLine("Account entity created:");  
            Console.WriteLine(account.ToString(Formatting.Indented));  
            initialAcctETagVal = account["@odata.etag"].ToString();  
        }  
  
        /// <summary>   
        /// Returns the current state of the specified entity, using the specified query criteria.   
        /// </summary>  
        /// <param name="entityUri">Relative URI of the entity instance to retrieve</param>  
        /// <param name="selectCriteria">Query selection, filtering, expansion</param>  
        /// <returns>JObject containing entity's specified properties; otherwise null if not exists.  
        /// </returns>  
        private JObject GetCurrentRecord(string entityUri, string queryOptions)  
        {  
            JObject entity = null;  
            if (String.IsNullOrEmpty(entityUri))  
            { throw new ArgumentNullException(); }  
            HttpResponseMessage response = httpClient.GetAsync(entityUri + queryOptions).Result;  
            if (response.StatusCode == HttpStatusCode.OK) //200  
            {  
                string body = response.Content.ReadAsStringAsync().Result;  
                entity = JsonConvert.DeserializeObject<JObject>(body);  
            }  
            else if (response.StatusCode == HttpStatusCode.NotFound) //404  
            { return null; }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
            return entity;  
        }  
  
        /// <summary> Sends an HTTP message containing a JSON payload to the target URL. </summary>  
        /// <typeparam name="T">Type of the data to send in the message content (payload)</typeparam>  
        /// <param name="client">A preconfigured HTTP client</param>  
        /// <param name="method">The HTTP method to invoke</param>  
        /// <param name="requestUri">The relative URL of the message request</param>  
        /// <param name="value">The data to send in the payload. The data will be converted to a   
        /// serialized JSON payload. </param>  
        /// <returns>An HTTP response message</returns>  
        private async Task<HttpResponseMessage> SendAsJsonAsync<T>(HttpClient client,   
            HttpMethod method, string requestUri, T value)  
        {  
            string content;  
            if (value.GetType().Name.Equals("JObject"))  
            { content = value.ToString(); }  
            else  
            {  
                content = JsonConvert.SerializeObject(value, new JsonSerializerSettings()  
                { DefaultValueHandling = DefaultValueHandling.Ignore });  
            }  
            HttpRequestMessage request = new HttpRequestMessage(method, requestUri);  
            request.Content = new StringContent(content);  
            request.Content.Headers.ContentType = MediaTypeHeaderValue.Parse("application/json");  
            return await client.SendAsync(request);  
        }  
  
        /// <summary> Displays exception information to the console. </summary>  
        /// <param name="ex">The exception to output</param>  
        private static void DisplayException(Exception ex)  
        {  
            Console.WriteLine("The application terminated with an error.");  
            Console.WriteLine(ex.Message);  
            while (ex.InnerException != null)  
            {  
                Console.WriteLine("\t* {0}", ex.InnerException.Message);  
                ex = ex.InnerException;  
            }  
        }  
    }  
}  
```  
  
### <a name="see-also"></a>Siehe auch

[Verwenden der Common Data Service for Apps-Web-API](../overview.md)<br />
[Bedingte Vorgänge mithilfe der Web-API ausführen](../perform-conditional-operations-using-web-api.md)<br />
[Web API Beispiele](../web-api-samples.md)<br />
[Beispiel bedingter Web-API-Operationen](../web-api-conditional-operations-sample.md)
[Beispiel grundlegender Web-API-Operationen (C#)](basic-operations-csharp.md)<br />
[Web API-Abfragedatenbeispiel (C#)](query-data-csharp.md)<br />
[Internet-API-Funktionen- und Aktionen-Beispiel (C#)](functions-actions-csharp.md)

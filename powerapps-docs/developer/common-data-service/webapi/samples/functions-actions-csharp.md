---
title: 'Beispiel für Web-API-Funktionen und Aktionenbeispiel (C#) (Common Data Service for Apps) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie ungebundene und gebundene Funktionen und Aktionen, einschließlich benutzerdefinierter Aktionen, mithilfe der "Common Data Service für Apps"-Web API und C# ausgeführt werden.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: b14a8bff-bf05-412c-89f6-ba7b503dcb51
caps.latest.revision: 13
author: brandonsimons
ms.author: jdaly
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="web-api-functions-and-actions-sample-c"></a>Internet-API-Funktionen- und Aktionen-Beispiel (C#)

Dieses Beispiel veranschaulicht, wie ungebundene und gebundene Funktionen und Aktionen, einschließlich benutzerdefinierter Aktionen, mithilfe der Common Data Service für Apps Web API  ausgeführt werden.  
  
> [!NOTE]
>  Dieses Beispiel implementiert die Vorgänge, die unter [Beispiel für Web-API-Funktionen und -Aktionen](../web-api-functions-actions-sample.md) beschrieben sind, und nutzt bekannte C#-Konstrukte, die in [Web-API-Beispiele (C#)](../web-api-samples-csharp.md) beschrieben sind.  
 
<a name="bkmk_prerequisites"></a>

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzungen für alle Common Data Service for Apps Web API C# Beispiele sind im Abschnitt [Voraussetzungen](../web-api-samples-csharp.md#bkmk_prerequisites) des übergeordneten Themas [Web API Samples (C#)](../web-api-samples-csharp.md) beschrieben.  
  
<a name="bkmk_runSample"></a>
 
## <a name="run-this-sample"></a>Beispiel ausführen

Gehen Sie zu [Beispiel für Web-API-Funktionen und -Aktionen (C#) für Microsoft CRM](http://go.microsoft.com/fwlink/p/?LinkId=824047), laden Sie die Beispielarchivdatei "Microsoft CRM Web API Functions and Actions Sample (CS).zip" herunter und extrahieren Sie die Inhalte in einen lokalen Ordner. Dieser Ordner sollte die folgenden Datei enthalten:  
  
|Datei|Zweck/Beschreibung|  
|----------|--------------------------|  
|Program.cs|Enthält den primären Quellcode für dieses Beispiel.|  
|App.config|Die Konfigurationsdatei der Anwendung, die den Platzhalter Common Data Service for Apps Server-Verbindungsinformationen enthält.|  
|Authentication.cs<br />Configuration.cs<br />Exceptions.cs|Diese Dateien aus dem Ordner **Web API Helper Code** enthalten die ergänzende Bibliothek, die unter [Verwenden der Common Data Service for Apps Web-API-Hilfe-Bibliothek (C#)](../use-microsoft-dynamics-365-web-api-helper-library-csharp.md) aufgeführt ist.|  
|FunctionsAndActions.sln <br />FunctionsAndActions.csproj <br />Packages.config <br />AssemblyInfo.cs|Die Standard-Visual Studio 2015-Lösung, das Projekt, die NuGet-Paketkonfiguration Assemblyinformationsdateien für dieses Beispiel.|  
|WebAPIFunctionsandActions_1_0_0_0_managed.zip|Eine benutzerdefinierte verwaltete Lösung, die zwei benutzerdefinierte Aktionen für dieses Beispiel enthält.|  
  
Führen Sie als Nächstes das folgende Verfahren aus, um dieses Beispiel auszuführen.  
  
1.  Suchen und doppelklicken Sie auf die Lösungsdatei "FunctionsAndActions.sln", um die Lösung in Visual Studio zu laden. Erstellen Sie die **FunctionsAndActions**-Lösung.  Dies sollte alle erforderlichen NuGet-Pakete automatisch herunterladen und installieren.  
  
2.  Bearbeiten Sie die Anwendungskonfigurationsdatei App.config um Verbindungsinformationen für Ihren Common Data Service for Apps-Server anzugeben.  Weitere Informationen finden Sie unter: [Hilfecode: Konfigurationsklassen](../web-api-helper-code-configuration-classes.md).  
  
3.  Führen Sie das Projekt **FunctionsAndActions** in Visual Studio aus.  Alle Beispiellösungen sind für die Ausführung im Debugmodus konfiguriert.  
  
<a name="bkmk_codeListing"></a>

## <a name="code-listing"></a>Codelisten

Den aktuellen Quellcode für diese Datei finden Sie im Beispieldownloadpaket.  
  
 `Program.cs`  
  
```csharp  
  
using Microsoft.Crm.Sdk.Samples.HelperCode;  
using Newtonsoft.Json;  
using Newtonsoft.Json.Linq;  
using System;  
using System.IO;  
using System.Text;  
using System.Collections.Generic;  
using System.Net.Http;  
using System.Net.Http.Headers;  
using System.Threading.Tasks;  
using System.Linq;  
using System.Net;  
  
namespace Microsoft.Crm.Sdk.Samples  
{  
    /// <summary> This program demonstrates calling bound and unbound  
    /// functions and actions using the CRM Web API. </summary>  
    /// <remarks>  
    /// The following standard CRM Web API functions and actions are invoked:  
    /// - WhoAmI, a basic unbound function  
    /// - GetTimeZoneCodeByLocalizedName, an unbound function that requires parameters  
    /// - CalculateTotalTimeIncident, a bound function  
    /// - WinOpportunity, an unbound action that takes parameters  
    /// - AddToQueue, a bound action that takes parameters  
    /// In addition, a managed solution is loaded and custom bound and an unbound actions   
    /// contained within are invoked.   
    ///   
    /// TODO: Before building this application, you must first modify the following    
    /// configuration information in the app.config file:  
    ///   - All deployments: Provide connection string service URL's for your organization.  
    ///   - CRM (online): Replace the app settings with the correct values for your Azure   
    ///                 application registration.   
    /// See the provided app.config file for more information.   
    /// </remarks>  
    class FunctionsAndActions  
    {  
        //Provides a persistent client-to-CRM server communication channel.  
        HttpClient httpClient;  
        //Associated solution package that contains custom actions used by this sample  
        const string customSolutionFilename = "WebAPIFunctionsandActions_1_0_0_0_managed.zip";  
        const string customSolutionName = "WebAPIFunctionsandActions";  
        string customSolutionID = null;  
        //Centralized collection of entity URIs used to manage lifetimes  
        List<string> entityUris = new List<string>();  
        //A set of variables to hold the state of and URIs for primary entity instances.  
        string incident1Uri, opportunity1Uri, contact1Uri;  
        //Objects associated with created URIs, where required.  
        JObject contact1;  
        Guid myUserId;  //CRM User ID for current user.  
  
        /// <summary> Principal sample code that demonstrates calling bound and unbound functions   
        ///  and actions.</summary>  
        public async Task RunAsync()  
        {  
            HttpResponseMessage response = null;  
  
            #region Call an unbound function with no parameters.  
            //Retrieve the current user's full name from the WhoAmI function:  
            // https://msdn.microsoft.com/library/mt607925.aspx, which returns a WhoAmIResponse   
            // complex type: https://msdn.microsoft.com/library/mt607982.aspx.  
            string currentUser;  
            Console.WriteLine("Unbound function: WhoAmI");  
            response = await httpClient.GetAsync("WhoAmI", HttpCompletionOption.ResponseContentRead);  
            if (!response.IsSuccessStatusCode)  
            { throw new CrmHttpResponseException(response.Content); }  
            JObject whoAmIresp = JsonConvert.DeserializeObject<JObject>(await  
                response.Content.ReadAsStringAsync());  
            //First obtain the user's ID.  
            myUserId = (Guid)whoAmIresp["UserId"];  
            //Then retrieve the full name for that unique ID.  
            string requestUri = "systemusers(" + myUserId + ")?$select=fullname";  
            response = await httpClient.GetAsync(requestUri, HttpCompletionOption.ResponseHeadersRead);  
            if (response.IsSuccessStatusCode)  
            {  
                JObject user = JsonConvert.DeserializeObject<JObject>(await  
                    response.Content.ReadAsStringAsync());  
                currentUser = user["fullname"].ToString();  
            }  
            else if (response.StatusCode == HttpStatusCode.NotFound)  
            { currentUser = "[not registered]"; }  
            else  
            {  
                Console.WriteLine("Error calling WhoAmI!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
            Console.WriteLine("\tCurrent user has system name '{0}'.", currentUser);  
            #endregion Call an unbound function with no parameters.  
  
            #region Call an unbound function that requires parameters.  
            //Retrieve the time zone code for the specified time zone, using the GetTimeZoneCodeByLocalizedName   
            //function: https://msdn.microsoft.com/library/mt607644.aspx, which returns a GetTimeZoneCodeBy-  
            //LocalizedNameResponse complex type: https://msdn.microsoft.com/library/mt607889.aspx.  
            string timeZoneCode;  
            int localeID = 1033;  
            string timeZoneName = "Pacific Standard Time";  
            JObject LocalizedNameResponse;  
            //Demonstrates best practice of passing parameters.  
            string[] uria = new string[] {  
                "GetTimeZoneCodeByLocalizedName",  
                "(LocalizedStandardName=@p1,LocaleId=@p2)",  
                "?@p1='" + timeZoneName + "'&@p2=" + localeID };  
            //This would also work:  
            //string[] uria = ["GetTimeZoneCodeByLocalizedName", "(LocalizedStandardName='" +   
            //    timeZoneName + "',LocaleId=" + localeId + ")"];   
            Console.WriteLine("Unbound function: GetTimeZoneCodeByLocalizedName");  
            response = await httpClient.GetAsync(string.Join("", uria),   
                HttpCompletionOption.ResponseHeadersRead);  
            if (response.StatusCode == HttpStatusCode.OK)  
            {  
                LocalizedNameResponse = JsonConvert.DeserializeObject<JObject>(await  
                    response.Content.ReadAsStringAsync());  
            }  
            else  
            {  
                Console.WriteLine("Error calling GetTimeZoneCodeByLocalizedName!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
            timeZoneCode = LocalizedNameResponse["TimeZoneCode"].ToString();  
            Console.WriteLine("\tThe time zone '{0}' has the code '{1}'.", timeZoneName, timeZoneCode);  
            #endregion Call an unbound function that requires parameters.  
  
            #region Call a bound function.      
            //Retrieve the total time, in minutes, spent on all tasks associated with an incident.  
            //Uses the CalculateTotalTimeIncident function: https://msdn.microsoft.com/library/mt593054.aspx,   
            //which returns a CalculateTotalTimeIncidentResponse complex type:   
            //https://msdn.microsoft.com/library/mt607924.aspx.  
            string totalTime;  
            string boundUri = incident1Uri + @"/Microsoft.Dynamics.CRM.CalculateTotalTimeIncident()";  
            Console.WriteLine("Bound function: CalculateTotalTimeIncident");  
            response = await httpClient.GetAsync(boundUri, HttpCompletionOption.ResponseHeadersRead);  
            if (response.IsSuccessStatusCode)  
            {  
                JObject cttir = JsonConvert.DeserializeObject<JObject>(await  
                    response.Content.ReadAsStringAsync());  
                totalTime = cttir["TotalTime"].ToString();  
            }  
            else  
            {  
                Console.WriteLine("Error calling CalculateTotalTimeIncident!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
            Console.WriteLine("\tThe total duration of tasks associated with the incident " +  
                "is {0} minutes.", totalTime);  
            #endregion Call a bound function.      
  
            #region Call an unbound action that requires parameters.  
            //Close an opportunity and marks it as won. Uses the WinOpportunity action:   
            //https://msdn.microsoft.com/library/mt607971.aspx,   
            //which takes a int32 status code and an opportunityclose entity type:   
            //https://msdn.microsoft.com/library/mt593099.aspx.  
            JObject opportClose = new JObject();  
            opportClose["subject"] = "Won Opportunity";  
            opportClose["opportunityid@odata.bind"] = opportunity1Uri;  
            JObject winOpportParams = new JObject();  
            winOpportParams["Status"] = 3;  
            winOpportParams["OpportunityClose"] = opportClose;  
            Console.WriteLine("Unbound action: WinOpportunity");  
            response = await SendAsJsonAsync(httpClient, HttpMethod.Post, "WinOpportunity",  
                winOpportParams);  
            if (!response.IsSuccessStatusCode)  
            {  
                Console.WriteLine("Error calling WinOpportunity!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
            Console.WriteLine("\tOpportunity won.");  
            #endregion Call an unbound action that requires parameters.  
  
            #region Call a bound action that requires parameters.  
            //Add a new letter tracking activity to the current user's queue. Uses the AddToQueue   
            //action: https://msdn.microsoft.com/library/mt607880.aspx, which is bound to the queue   
            //entity type: https://msdn.microsoft.com/library/mt607886.aspx, and returns a   
            //AddToQueueResponse complex type: https://msdn.microsoft.com/en-us/library/mt608105.aspx.  
            string queueItemId;  
            //Create a letter tracking instance.  
            string letterUri;  
            JObject letter = new JObject();  
            letter["description"] = "Example letter";  
            Console.WriteLine("Bound action: AddToQueue");  
            response = await SendAsJsonAsync(httpClient, HttpMethod.Post, "letters", letter);  
            if (response.StatusCode == HttpStatusCode.NoContent)  
            {  
                letterUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();  
                entityUris.Add(letterUri);  
            }  
            else  
            {  
                Console.WriteLine("Error creating tracking letter!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            //Retrieve the ID associated with this new letter tracking activity.  
            string letterActivityId;  
            response = await httpClient.GetAsync(letterUri + "?$select=activityid",  
                HttpCompletionOption.ResponseContentRead);  
            if (response.IsSuccessStatusCode)  
            {  
                JObject letterRetreived = JsonConvert.DeserializeObject<JObject>(await  
                    response.Content.ReadAsStringAsync());  
                letterActivityId = letterRetreived["activityid"].ToString();  
            }  
            else  
            {  
                Console.WriteLine("Error retrieving tracking letter activity ID!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            //Retrieve URL to current user's queue.  
            string myQueueUri;  
            response = await httpClient.GetAsync("systemusers(" + myUserId + ")/queueid/$ref",  
                HttpCompletionOption.ResponseContentRead);  
            if (response.IsSuccessStatusCode)  
            {  
                JObject queueRef = JsonConvert.DeserializeObject<JObject>(await  
                    response.Content.ReadAsStringAsync());  
                myQueueUri = queueRef["@odata.id"].ToString();  
            }  
            else  
            {  
                Console.WriteLine("Error retrieving current user queue URL!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
  
            //Add letter activity to current user's queue, then return its queue ID.  
            JObject addToQueueParams = new JObject();  
            addToQueueParams["Target"] = JObject.Parse(  
              @"{activityid: '" + letterActivityId + @"', '@odata.type': 'Microsoft.Dynamics.CRM.letter' }");  
            response = await SendAsJsonAsync(httpClient, HttpMethod.Post,  
                myQueueUri + "/Microsoft.Dynamics.CRM.AddToQueue", addToQueueParams);  
            if (response.StatusCode == HttpStatusCode.OK)  
            {  
                JObject queueResponse = JsonConvert.DeserializeObject<JObject>(await  
                    response.Content.ReadAsStringAsync());  
                queueItemId = queueResponse["QueueItemId"].ToString();  
            }  
            else  
            {  
                Console.WriteLine("Error adding letter activity to queue!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
            Console.WriteLine("\tQueueItemId returned from AddToQueue action: {0}", queueItemId);  
            #endregion Call a bound action that requires parameters.  
  
            //Attempt to load the associated managed solution so that we can call its custom actions.   
            await InstallCustomSolutionAsync(true);  
            if (customSolutionID == null)  
            {  
                Console.WriteLine("Failed to install custom solution, so custom operations cannot be called.");  
                return;  
            }  
  
            #region Call a bound custom action that requires parameters.  
            //Add a note to a specified contact. Uses the custom action sample_AddNoteToContact, which  
            //is bound to the contact to annotate, and takes a single param, the note to add. It also    
            //returns the URI to the new annotation.   
            string annote1Url;  
            JObject note1 = JObject.Parse(  
                @"{NoteTitle: 'Note Title', NoteText: 'The text content of the note.'}");  
            string actionUri = contact1Uri + "/Microsoft.Dynamics.CRM.sample_AddNoteToContact";  
            Console.WriteLine("Custom action: sample_AddNoteToContact");  
            response = await SendAsJsonAsync(httpClient, HttpMethod.Post, actionUri, note1);  
            if (response.StatusCode == HttpStatusCode.OK)  
            {  
                JObject contact = JsonConvert.DeserializeObject<JObject>(await  
                    response.Content.ReadAsStringAsync());  
                annote1Url = httpClient.BaseAddress + "/annotations(" + contact["annotationid"] + ")";  
            }  
            else  
            {  
                Console.WriteLine("Error calling custom action sample_AddNoteToContact!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
            Console.WriteLine("\tA note with the title '{0}' was created and " +  
                "associated with the contact {2}.",  
                note1["NoteTitle"], note1["NoteText"],  
                contact1["firstname"] + " '" + contact1["lastname"] + "'");  
            #endregion Call a bound custom action that requires parameters.  
  
            #region Call an unbound custom action that requires parameters.  
            //Create a customer of the specified type, using the custom action sample_CreateCustomer,  
            //which takes two prams: the type of customer ('account' or 'contact') and the name of   
            //the new customer.  
            string customerName1 = "New account customer (sample)";  
            JObject customerParam = JObject.Parse(  
                @"{CustomerType: 'account', AccountName: '" + customerName1 + "'}");  
            Console.WriteLine("Custom action: sample_CreateCustomer");  
            response = await SendAsJsonAsync(httpClient, HttpMethod.Post,  
                "sample_CreateCustomer", customerParam);  
            if (!response.IsSuccessStatusCode)  
            {  
                Console.WriteLine("Error calling custom action sample_CreateCustomer!");  
                throw new CrmHttpResponseException(response.Content);  
            }  
            Console.WriteLine("\tThe account '" + customerName1 + "' was created.");  
  
            //Try to call the same custom action with invalid parameters, here the same name is  
            //not valid for a contact. (ContactFirstname and ContactLastName parameters are    
            //required when CustomerType is contact.)  
            customerParam = JObject.Parse(  
                @"{CustomerType: 'contact', AccountName: '" + customerName1 + "'}");  
            response = await SendAsJsonAsync(httpClient, HttpMethod.Post,  
                "sample_CreateCustomer", customerParam);  
            if (response.IsSuccessStatusCode)  
            { Console.WriteLine("\tCall to CreateCustomer not expected to succeed."); }  
            else  
            {  
                CrmHttpResponseException ex = new CrmHttpResponseException(response.Content);  
                Console.WriteLine("\tExpected Error: " + ex.Message);  
            }  
            #endregion Call an unbound custom action that requires parameters.  
        }  
  
        /// <summary> Retrieves the solution ID associated with a solution name </summary>  
        /// <param name="solutionName">Unique name of the solution (uniquename)</param>  
        /// <returns>The solutionid property for this solution if found; otherwise null.</returns>  
        private async Task<string> GetSolutionIDAsync(string solutionName)  
        {  
            HttpResponseMessage response;  
            string solutionID = null;  
            if (String.IsNullOrEmpty(solutionName)) { return null; }  
            string queryOptions = "solutions?$select=solutionid&$filter=uniquename eq '" + solutionName + "'";  
            response = await httpClient.GetAsync(queryOptions, HttpCompletionOption.ResponseHeadersRead);  
            if (response.StatusCode == HttpStatusCode.OK)  
            {  
                JObject solutionArray = JsonConvert.DeserializeObject<JObject>(await   
                    response.Content.ReadAsStringAsync());  
                //There can only be zero or one returned record when filtering on a unique property.  
                if (!solutionArray["value"].Any())  
                { solutionID = null; }  
                else  
                { solutionID = solutionArray["value"].First()["solutionid"].ToString(); }  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
            return solutionID;  
        }  
  
        /// <summary> Installs (or uninstalls) the custom, managed solution associated with   
        /// this sample </summary>  
        /// <remarks>Uses the ImportSolution action: https://msdn.microsoft.com/library/mt608117.aspx  
        /// </remarks>  
        /// <param name="install">true to install (default); otherwise, false to uninstall</param>  
        /// <returns>void</returns>  
        private async Task InstallCustomSolutionAsync(bool install = true)  
        {  
            HttpResponseMessage response;  
            //Check first if the solution is already installed by retrieving its ID.  
            customSolutionID = await GetSolutionIDAsync(customSolutionName);  
  
            //Request to install and solution is not already present  
            if (install == true && customSolutionID == null)  
            {  
                //Locate the custom solution zip file, which should have been copied over to the build   
                //output directory.  
                string solutionPath = Directory.GetCurrentDirectory() + "\\" + customSolutionFilename;  
                if (!File.Exists(solutionPath))  
                { return; }  
                //Read the solution package into memory  
                byte[] packageBytes = File.ReadAllBytes(solutionPath);  
                //Import the solution package.  
                JObject importParams = new JObject();  
                importParams["CustomizationFile"] = packageBytes;  
                importParams["OverwriteUnmanagedCustomizations"] = false;  
                importParams["PublishWorkflows"] = false;  
                importParams["ImportJobId"] = Guid.NewGuid();  
                response = await SendAsJsonAsync(httpClient, HttpMethod.Post, "ImportSolution", importParams);  
                if (response.IsSuccessStatusCode)  
                {  
                    customSolutionID = await GetSolutionIDAsync(customSolutionName);  
                    string solutionUri = httpClient.BaseAddress.ToString() + "solutions(" + customSolutionID + ")";  
                    entityUris.Add(solutionUri);  //Add to lifetime-managed records.  
                    return;  
                }  
                else  
                { throw new CrmHttpResponseException(response.Content); }  
            }  
            //Request to uninstall and solution is present.   
            else if (install == false && customSolutionID != null)  
            {  
                string solutionUri = httpClient.BaseAddress.ToString() + "solutions(" + customSolutionID + ")";  
                response = httpClient.DeleteAsync(solutionUri).Result;  
                customSolutionID = null;  
            }  
        }  
  
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
  
        /// <summary>  
        /// Obtains the connection information from the application's configuration file, then   
        /// uses this info to connect to the specified CRM service.  
        /// </summary>  
        /// <param name="args"> Command line arguments. The first specifies the name of the   
        ///  connection string setting. </param>  
        private void ConnectToCRM(String[] cmdargs)  
        {  
            //Create a helper object to read app.config for service URL and application   
            // registration settings.  
            FileConfiguration config = null;  
            if (cmdargs.Length > 0)  
            { config = new FileConfiguration(cmdargs[0]); }  
            else  
            { config = new FileConfiguration(null); }  
            //Create a helper object to authenticate the user with this connection info.  
            Authentication auth = new Authentication(config);  
            //Next use a HttpClient object to connect to specified CRM Web service.  
            httpClient = new HttpClient(auth.ClientHandler, true);  
            //Define the Web API base address, the max period of execute time, the   
            // default OData version, and the default response payload format.  
            httpClient.BaseAddress = new Uri(config.ServiceUrl + "api/data/v8.1/");  
            httpClient.Timeout = new TimeSpan(0, 2, 0);  
            httpClient.DefaultRequestHeaders.Add("OData-MaxVersion", "4.0");  
            httpClient.DefaultRequestHeaders.Add("OData-Version", "4.0");  
            httpClient.DefaultRequestHeaders.Accept.Add(  
                new MediaTypeWithQualityHeaderValue("application/json"));  
        }  
  
        /// <summary> Creates the CRM entity instances used by this sample. </summary>  
        private void CreateRequiredRecords()  
        {  
            //Create a parent account, an associated incident with three associated tasks   
            //(required for CalculateTotalTimeIncident).  
            JObject account1 = new JObject();  
            string account1Uri;  
            account1["name"] = "Fourth Coffee";  
            HttpResponseMessage response = SendAsJsonAsync(httpClient, HttpMethod.Post,  
                "accounts", account1).Result;  
            if (response.StatusCode == HttpStatusCode.NoContent)  
            {  
                account1Uri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();  
                entityUris.Add(account1Uri);  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
  
            JArray tasks = new JArray(new JObject[]  
            {  
                JObject.Parse(@"{subject: 'Task 1', actualdurationminutes: 30}"),  
                JObject.Parse(@"{subject: 'Task 2', actualdurationminutes: 30}"),  
                JObject.Parse(@"{subject: 'Task 3', actualdurationminutes: 30}")  
            }  
            );  
            JObject incident1 = new JObject();  
            incident1["title"] = "Sample Case";  
            incident1["customerid_account@odata.bind"] = account1Uri;  
            incident1["Incident_Tasks"] = tasks;  
            response = SendAsJsonAsync(httpClient, HttpMethod.Post, "incidents", incident1).Result;  
            if (response.StatusCode == HttpStatusCode.NoContent)  
            {  
                incident1Uri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();  
                entityUris.Add(incident1Uri);  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
            //Close the associated tasks (so that they represent completed work).  
            JObject incidentTaskRefs;  
            //Property value set used to mark tasks as completed.   
            JObject completeCode = JObject.Parse(@"{statecode: 1, statuscode: 5}");  
            response = httpClient.GetAsync(incident1Uri + "/Incident_Tasks/$ref",  
                HttpCompletionOption.ResponseContentRead).Result;  
            if (response.IsSuccessStatusCode)  
            {  
                incidentTaskRefs = JsonConvert.DeserializeObject<JObject>  
                    (response.Content.ReadAsStringAsync().Result);  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
            foreach (var taskRef in incidentTaskRefs["value"])  
            {  
                response = SendAsJsonAsync(httpClient, new HttpMethod("PATCH"),   
                    taskRef["@odata.id"].ToString(), completeCode).Result;  
                if (!response.IsSuccessStatusCode)  
                { throw new CrmHttpResponseException(response.Content); }  
            }  
  
            //Create another account and associated opportunity (required for CloseOpportunityAsWon).  
            JObject account2 = new JObject();  
            string account2Uri;  
            account2["name"] = "Coho Winery";  
            account2["opportunity_customer_accounts"] = JArray.Parse(@"[{ name: 'Opportunity to win' }]");  
            response = SendAsJsonAsync(httpClient, HttpMethod.Post, "accounts", account2).Result;  
            if (response.StatusCode == HttpStatusCode.NoContent)  
            {  
                account2Uri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();  
                entityUris.Add(account2Uri);  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
            //Retrieve the URI to the opportunity.  
            JObject custOpporRefs;  
            response = httpClient.GetAsync(account2Uri + "/opportunity_customer_accounts/$ref",  
                HttpCompletionOption.ResponseContentRead).Result;  
            if (response.IsSuccessStatusCode)  
            {  
                custOpporRefs = JsonConvert.DeserializeObject<JObject>  
                    (response.Content.ReadAsStringAsync().Result);  
                opportunity1Uri = custOpporRefs["value"][0]["@odata.id"].ToString();  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
  
            //Create a contact to use with custom action sample_AddNoteToContact   
            contact1 = JObject.Parse(@"{firstname: 'Jon', lastname: 'Fogg'}");  
            response = SendAsJsonAsync(httpClient, HttpMethod.Post, "contacts", contact1).Result;  
            if (response.StatusCode == HttpStatusCode.NoContent)  
            {  
                contact1Uri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();  
                entityUris.Add(contact1Uri);  
            }  
            else  
            { throw new CrmHttpResponseException(response.Content); }  
        }  
  
        /// <summary> Deletes the CRM entity instance sample data created by this sample. </summary>  
        /// <param name="prompt">True to prompt the user for confirmation and display results;   
        ///   otherwise False to execute silently.</param>  
        /// <returns>Number of entity instances deleted</returns>  
        private int DeleteRequiredRecords(bool prompt)  
        {  
            if (entityUris.Count == 0) return 0;  
            if (prompt)  
            {  
                Console.Write("\nDo you want these sample entity records deleted? (y/n) [y]: ");  
                String answer = Console.ReadLine();  
                answer = answer.Trim();  
                if (!(answer.StartsWith("y") || answer.StartsWith("Y") ||  
                    answer == String.Empty))  
                { return 0; }  
            }  
            HttpResponseMessage response;  
            int successCnt = 0, failCnt = 0;  
            HttpContent lastBadResponseContent = null;  
            foreach (string ent in entityUris)  
            {  
                response = httpClient.DeleteAsync(ent).Result;  
                if (response.IsSuccessStatusCode)   
                { successCnt++; }  
                else if (response.StatusCode == HttpStatusCode.NotFound)   
                {; } //Entity may have been deleted by another user or via cascade delete.  
                else //Failed to delete  
                {  
                    failCnt++;  
                    lastBadResponseContent = response.Content;  
                }  
            }  
            entityUris.Clear();  
            if (failCnt > 0)  
            {  
                //Throw last failure.  
                throw new CrmHttpResponseException(lastBadResponseContent);  
            }  
            if (prompt)  
            { Console.WriteLine("Deleted {0} records!", successCnt); }  
            return successCnt;  
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
  
        /// <summary> Helper method to display caught exceptions </summary>  
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
[Nutzen von Web-API-Funktionen](../use-web-api-functions.md)<br />
[Nutzen von Web-API-Aktionen](../use-web-api-actions.md)<br />
[Web API Beispiele](../web-api-samples.md)<br />
[Beispiel für Web-API-Funktionen und Aktionen](../web-api-functions-actions-sample.md) 
[Beispiel grundlegender Web-API-Operationen (C#)](basic-operations-csharp.md)<br />
[Web API-Abfragedatenbeispiel (C#)](query-data-csharp.md)<br />
[Beispiel bedingter Web-API-Operationen (C#)](conditional-operations-csharp.md)

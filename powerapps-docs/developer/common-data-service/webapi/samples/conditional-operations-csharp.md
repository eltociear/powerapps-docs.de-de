---
title: 'Beispiel bedingter Web-API-Operationen (C#) (Common Data Service für Apps) | Microsoft Docs'
description: 'Dieses Beispiel veranschaulicht, wie Sie bedingte Operationen mit der Common Data Service for Apps-Web-API und C# ausführen'
ms.custom: ''
ms.date: 1/09/2019
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
> Dieses Beispiel implementiert den Common Data Service für Apps-Operationen und -Konsolenausgaben, der in [Beispiel bedingter Web-API-Operationen](../web-api-conditional-operations-sample.md) beschrieben ist, und verwendet die in [Web API Beispiele (C#)](../web-api-samples-csharp.md) beschriebenen gemeinsamen C#-Konstrukte.  
  
<a name="bkmk_Prereqs"></a>

## <a name="prerequisites"></a>Voraussetzungen

Die Voraussetzungen für alle CDS for Apps-Web-API C#-Beispiele werden im Abschnitt [Voraussetzungen](../web-api-samples-csharp.md#bkmk_prerequisites) des übergeordneten Themas [Web API Beispiele (C#)](../web-api-samples-csharp.md) aufgeführt.  
  
<a name="bkmk_RunSample"></a>
 
## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

Gehen Sie zu [Web API Conditional Operations Sample (C#)](https://github.com/Microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23) und klonen oder laden Sie das samples-Repository herunter und extrahieren Sie den Inhalt der Datei in einen Ordner auf Ihrem Computer. Dieser Ordner sollte die folgenden Datei enthalten:

|Datei|Beschreibung|  
|----------|-----------------|  
|SampleProgram.cs|Enthält den primären Quellcode für dieses Beispiel.|  
|App.config|Die Anwendungskonfigurationsdatei, die Platzhalter für CDS for Apps-Server-Verbindungsinformationen enthält. Diese Datei wird mit allen Web-API-Samples im Repo geteilt. Wenn Sie Verbindungsinformationen für ein Sample konfigurieren, können Sie die anderen Samples mit der gleichen Konfiguration ausführen.|  
|SampleHelper.cs|Enthält den Helfercode, der bei der Ausführung allgemeiner Aufgaben wie Konfiguration, Authentifizierung und `HTTP`-Antwortfehlerbehandlung hilft. <br/> Diese Datei wird mit allen Web-API-Samples im Repo geteilt. Es enthält Hilfsmethoden zur Verwaltung von Ausnahmen und das OAuth Token. Weitere Informationen zu den Methoden in dieser Datei finden Sie im Beispiel der Simple Web API.|
|SampleMethod.cs|Enthält alle Methoden, die den Quellcode im Beispiel unterstützen. In dieser Datei können Funktionen definiert werden, die in SampleProgram.cs verwendet werden. |
|ConditionalOperations.sln<br /> ConditionalOperations.csproj<br /> Packages.config<br /> AssemblyInfo.cs|Die Standard-Visual Studio 2017-Lösung, das Projekt, das NuGet-Paket und Assemblyinformationsdateien für dieses Beispiel.|  
  
1. Doppelklicken Sie auf die Datei "ConditionalOperations.sln", um die Lösung in Visual Studio zu öffnen.  
  
1. Erstellen Sie die Lösung (**Erstellen** > **Lösung erstellen**). Dies sollte alle erforderlichen NuGet-Pakete automatisch herunterladen und aktualisieren.  
  
1. Bearbeiten Sie die Datei "App.Config" in der Lösung, um Ihre CDS for Apps-Serverinstanz anzugeben, mit der Sie dieses Beispiel ausführen wollen.  
  
1. Führen Sie das Projekt aus.  Alle Beispielprojekte sind für die Ausführung im Debugmodus konfiguriert.  
  
     Die Beispielcodeausgabe wird in einem Konsolenfenster angezeigt.  
  
<a name="bkmk_CodeSample"></a>

## <a name="code-sample"></a>Codebeispiel

 `SampleProgram.cs`  
  
```csharp  
using Newtonsoft.Json;
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;

namespace PowerApps.Samples
{
  public partial class SampleProgram
   {
     static void Main(string[] args)
      {
        try
         {
          //Get configuration data from App.config connectionStrings
          string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

           using (HttpClient client = SampleHelpers.GetHttpClient(
           connectionString,
            SampleHelpers.clientId,
            SampleHelpers.redirectUrl,"v9.0"))
             {
              // <summary> Creates the CRM entity instance used by this sample. </summary>

               // Create a CRM account record.
               Console.WriteLine("\nCreate sample data");
               account.Add("name", "Contoso Ltd");
               account.Add("telephone1", "555-0000"); //Phone number value will increment with each update attempt
               account.Add("revenue", 5000000);
               account.Add("description", "Parent company of Contoso Pharmaceuticals, etc.");

               HttpRequestMessage request = new HttpRequestMessage(HttpMethod.Post, client.BaseAddress + "accounts");
               request.Content = new StringContent(account.ToString(), Encoding.UTF8, "application/json");

              HttpResponseMessage response = client.SendAsync(request, HttpCompletionOption.ResponseContentRead).Result;

                 if (response.IsSuccessStatusCode)
                  {
                    accountUri = response.Headers.GetValues("OData-EntityId").FirstOrDefault();
                    entityUri = accountUri;
                  }
                  else
                   {
                     throw new Exception(string.Format("Failed to create accounts", response.Content));
                   }

                //Retrieve the account record you created.
                 queryOptions = "?$select=name,revenue,telephone1,description";
                    //JObject entity = null;

                 HttpResponseMessage response1 = client.GetAsync(entityUri + queryOptions).Result;
                  if (response1.IsSuccessStatusCode) //200
                   {
                     account = JObject.Parse(response1.Content.ReadAsStringAsync().Result);
                     Console.WriteLine("Account entity created:");
                     Console.WriteLine(account.ToString(Newtonsoft.Json.Formatting.Indented));
                     initialAcctETagVal = account["@odata.etag"].ToString();
                   }

             #region Conditional GET

             Console.WriteLine("\n--Conditional GET section started--");
             // Attempt to retrieve using conditional GET with current ETag value.
             request = new HttpRequestMessage(HttpMethod.Get, accountUri + queryOptions);

             // Retrieve only if it doesn't match previously retrieved version.
             request.Headers.Add("If-None-Match", initialAcctETagVal);
             response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

              if (response.StatusCode == HttpStatusCode.NotModified)  // 304; expected.
                {
                  Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);
                  Console.WriteLine("Expected outcome: Entity was not modified so nothing was returned.");
                }

                else if (response.StatusCode == HttpStatusCode.OK)  // 200; not expected
                 {
                   Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);
                   account = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                    Console.WriteLine(account.ToString(Formatting.Indented));
                 }

                else
                 {
                   throw new Exception(string.Format("Failed to retrieve", response.Content));
                  }

                // Modify the account instance by updating telephone1

                 string accountPhoneUri = string.Format("{0}/{1}", accountUri, "telephone1");
                 JObject phoneProperty = new JObject();
                 phoneProperty.Add("value", "555-0001");
                 request = new HttpRequestMessage(HttpMethod.Put, accountPhoneUri);
                 request.Content = new StringContent(phoneProperty.ToString(), Encoding.UTF8, "application/json");
                 response = client.SendAsync(request, HttpCompletionOption.ResponseContentRead).Result;
                 if (response.StatusCode == HttpStatusCode.NoContent)
                  {
                    Console.WriteLine("\nAccount telephone number updated.");
                  }
                 else
                  {
                   throw new Exception(string.Format("Failed to update the account telephone number", response.Content));
                  }

                 // Reattempt conditional GET with original ETag value.
                 request = new HttpRequestMessage(HttpMethod.Get, accountUri + queryOptions);
                 request.Headers.Add("If-None-Match", initialAcctETagVal);
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

                 if (response.StatusCode == HttpStatusCode.OK) //200; expected
                  {
                    Console.WriteLine("Instance retrieved using ETag: {0}", initialAcctETagVal);
                  }
                 else if (response.StatusCode == HttpStatusCode.NotModified) // 304; not expected
                  {
                    Console.WriteLine("Unexpected status code: '{0}'.", (int)response.StatusCode);
                  }
                   else
                    { throw new Exception(string.Format("Failed to get original ETag value", response.Content)); }

                 // Retrieve and output current account state.
                 account = JObject.Parse(response.Content.ReadAsStringAsync().Result);
                 updatedAcctETagVal = account["@odata.etag"].ToString(); // Capture updated ETag
                  Console.WriteLine(account.ToString(Formatting.Indented));

                 #endregion Conditional GET

                 #region Optimistic concurrency on delete and update
                 Console.WriteLine("\n--Optimistic concurrency section started--");

                 // Attempt to delete original account (if matches original ETag value).
                 request = new HttpRequestMessage(HttpMethod.Delete, accountUri);
                 // If you replace "initialAcctETagVal" with "updatedAcctETagVal", 
                 // delete will succeed.
                 request.Headers.Add("If-Match", initialAcctETagVal); 
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;
                 // 412; Precondition failed error expected

              if (response.StatusCode == HttpStatusCode.PreconditionFailed) 
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
                 throw new Exception(string.Format("Failed to delete original count",response.Content));
                }

                 //Attempt to update account (if matches original ETag value).
                 JObject accountUpdate = new JObject();
                 accountUpdate.Add("telephone1", "555-0002");
                 accountUpdate.Add("revenue", 6000000);
                 request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                 request.Content = new StringContent(accountUpdate.ToString(),
                 Encoding.UTF8, "application/json");
                 request.Headers.Add("If-Match", initialAcctETagVal);
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

             if (response.StatusCode == HttpStatusCode.PreconditionFailed) // 412;
                    //Precondition failed error expected
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
                throw new Exception(string.Format("Failed to update account (if original ETag value matches)", response.Content));
              }

                  // Reattempt update if matches current ETag value.
                  accountUpdate["telephone1"] = "555-0003";
                  request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                  request.Content = new StringContent(accountUpdate.ToString(),
                  Encoding.UTF8, "application/json");
                  request.Headers.Add("If-Match", updatedAcctETagVal);
                  response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

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
                    throw new Exception(string.Format("Failed to update if matches current ETag value", response.Content));
                  }

                 // Retrieve and output current account state.
                 account = GetCurrentRecord(client,accountUri, queryOptions);
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
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

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
                    throw new Exception(string.Format("Failed to perform operations", response.Content));
                  }

                 //Attempt to perform same update without creation. 
                 accountUpdate["telephone1"] = "555-0005";
                 request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                 request.Content = new StringContent(accountUpdate.ToString(),
                 Encoding.UTF8, "application/json");
                 //Perform operation only if matching resource exists. 
                 request.Headers.Add("If-Match", "*");
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

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
                  {
                   throw new Exception(string.Format("Failed to perform operations", response.Content));
                  }

                //Retrieve and output current account state.
                 account = GetCurrentRecord(client,accountUri, queryOptions);
                 Console.WriteLine(account.ToString(Formatting.Indented));

                 // Delete the account record
                 HttpResponseMessage deleteResponse;
                 deleteResponse = client.DeleteAsync(accountUri).Result;
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
                    throw new Exception(string.Format("Failed to delete account record", response.Content));
                   }

                // Attempt to update it
                 accountUpdate["telephone1"] = "555-0006";
                 request = new HttpRequestMessage(new HttpMethod("PATCH"), accountUri);
                 request.Content = new StringContent(accountUpdate.ToString(),
                 Encoding.UTF8, "application/json");

                 // Perform operation only if matching resource exists.
                 request.Headers.Add("If-Match", "*");
                 response = client.SendAsync(request, HttpCompletionOption.ResponseHeadersRead).Result;

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
                      throw new Exception(string.Format("Failed to perform operations", response.Content));
                    }

                    #endregion Controlling upsert operations
                }
            }
            catch (Exception ex)
            {
                SampleHelpers.DisplayException(ex);
                throw;
            }
            finally
            {
                Console.WriteLine("Press <Enter> to exit the program.");
                Console.ReadLine();
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

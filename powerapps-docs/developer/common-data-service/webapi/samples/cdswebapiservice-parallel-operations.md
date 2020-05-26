---
title: Web API CDSWebApiService Beispiel für parallele Operationen (C#) (Common Data Service)| Microsoft Docs
description: Dieses Beispiel demonstriert die Verwendung der Task Parallel Library (TPL) mit synchronen Anforderungen.
ms.custom: ''
ms.date: 04/20/2020
ms.service: powerapps
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: pehecke
ms.reviewer: pehecke
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8bf51ab169671f95dede5e8b68ca1fcfff8a2a39
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276702"
---
# <a name="web-api-cdswebapiservice-parallel-operations-sample-c"></a>Web API CDSWebApiService Beispiel für parallele Operationen (C#)

Dieses Beispiel zeigt, wie eine [System.Threading.Tasks.Parallel.ForEach Methode](/dotnet/api/system.threading.tasks.parallel.foreach) Schleife verwendet wird, um die Datenparallelität über einen Satz von Datensätzen zu ermöglichen, die in CDS erstellt werden sollen.

In diesem Beispiel werden die synchronen Methoden der CDSWebApiService-Klasse innerhalb von Operationen verwendet. Da die CDSWebApiService-Klasse die Service Protection API-Limits verwalten kann, kann dieser Code gegenüber den vorübergehenden 429 Fehlern, mit denen Kunden rechnen müssen, widerstandsfähig sein. Es wird eine konfigurierbare Anzahl von Wiederholungsversuchen durchgeführt. 

Weitere Informationen:

- [Web-API CDSWebApiService-Klassenbeispiel (C#)](cdswebapiservice.md)
- [Dienstschutz-API-Grenzen](../../api-limits.md)

Dieses Beispiel basiert auf [So geht's: Schreiben Sie ein einfaches Parallel.ForEach-Schleife](/dotnet/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop) Beispiel, das jedoch so modifiziert wurde, dass es Erstellungs- und Löschoperationen mit CDS-Entitäten unter Verwendung der von der CDSWebApiService-Klasse bereitgestellten synchronen Methoden durchführt.

> [!NOTE]
> Wenn Sie Fiddler verwenden möchten, um die erwarteten API-Grenzen für den Dienstschutz einzuhalten, müssen Sie die Anzahl der zu erstellenden Datensätze auf etwa 10.000 festlegen. Sie werden nach 5 Minuten erscheinen. Beachten Sie, wie die Anwendung die Fehler erneut versucht und den Fluss aller Flüsse abschließt.

## <a name="prerequisites"></a>Voraussetzungen

Folgendes ist erforderlich, um die C#-Beispiele für CDSWebApiService zu erstellen und auszuführen:

- Microsoft Visual Studio 2019. 
- Zugang zu Common Data Service mit Privilegien zur Durchführung von CRUD-Operationen.
  
<a name="bkmk_runSample"></a>
  
## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

1. Gehen Sie zu [Web API CDSWebApiService Beispiel](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/CDSWebApiService), klonen Sie das Beispiel-Repository oder laden Sie es herunter und extrahieren Sie seinen Inhalt in einen lokalen Ordner.

1. Öffnen Sie die Datei [CDSWebApiService.sln](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/CDSWebApiService.sln).

1. Wählen Sie das Projekt **ParallelOperations** und öffnen Sie die App.config. Dies ist eine gemeinsame Datei [App.config](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/App.config), die von allen Beispielen in dieser Lösung verwendet wird. Sobald Sie diese bearbeiten, können Sie jedes der Beispiele in dieser Lösung ausführen.

1. Sie müssen die Werte `Url`, `UserPrincipalName` und `Password` bearbeiten, um die CDS-Instanz und die Anmeldedaten festzulegen, mit denen Sie eine Verbindung herstellen möchten.

    ```xml
        <add name="Connect"
            connectionString="Url=https://yourorg.api.crm.dynamics.com;
            Authority=null;
            ClientId=51f81489-12ee-4a9e-aaae-a2591f45987d;
            RedirectUrl=app://58145B91-0C36-4500-8554-080854F2AC97;
            UserPrincipalName=you@yourorg.onmicrosoft.com;
            Password=y0urp455w0rd;
            CallerObjectId=null;
            Version=9.1;
            MaxRetries=3;
            TimeoutInSeconds=180;
            "/>
    ```

1. Stellen Sie sicher, dass das Projekt **ParallelOperations** als Startprojekt festgelegt ist. Der Name des Projekts sollte fettgedruckt sein, um anzuzeigen, dass es sich um das Startprojekt handelt. Wenn der Name nicht fett ist, klicken Sie im Lösungsexplorer mit der rechten Maustaste darauf und wählen Sie **Als Startprojekt festlegen**.

1. Drücken Sie F5, um das Programm im Debug-Modus auszuführen.

## <a name="code-listing"></a>Codelisten

Dieses Beispiel hängt von der im CDSWebAPIService-Projekt enthaltenen Assembly ab. Informationen über die Methoden, die diese Klasse zur Verfügung stellt, finden Sie unter [Web-API CDSWebApiService-Klasse Beispiel (C#)](cdswebapiservice.md).

Es folgt der Code aus der Datei Program.cs:

```csharp
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Concurrent;
using System.Collections.Generic;
using System.Configuration;
using System.Threading.Tasks;

namespace PowerApps.Samples
{
    internal class Program
    {
        //Get configuration data from App.config connectionStrings
        private static readonly string connectionString = ConfigurationManager.ConnectionStrings["Connect"].ConnectionString;

        private static readonly ServiceConfig serviceConfig = new ServiceConfig(connectionString);

        //Controls the max degree of parallelism
        private static readonly int maxDegreeOfParallelism = 10;

        //How many records to create with this sample.
        private static readonly int numberOfRecords = 100;

        private static void Main()
        {
            #region Optimize Connection

            //Change max connections from .NET to a remote service default: 2
            System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
            //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
            System.Threading.ThreadPool.SetMinThreads(100, 100);
            //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
            System.Net.ServicePointManager.Expect100Continue = false;
            //Can decreas overall transmission overhead but can cause delay in data packet arrival
            System.Net.ServicePointManager.UseNagleAlgorithm = false;

            #endregion Optimize Connection

            var parallelOptions = new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism };

            var count = 0;

            //Will be populated with account records to import
            List<JObject> accountsToImport = new List<JObject>();
            //ConcurrentBag is a thread-safe, unordered collection of objects.
            ConcurrentBag<Uri> accountsToDelete = new ConcurrentBag<Uri>();
            Console.WriteLine($"Preparing to create {numberOfRecords} acccount records using Web API.");

            //Add account records to the list to import
            while (count < numberOfRecords)
            {
                var account = new JObject
                {
                    ["name"] = $"Account {count}"
                };
                accountsToImport.Add(account);
                count++;
            }

            try
            {
                using (CDSWebApiService svc = new CDSWebApiService(serviceConfig))
                {
                    Console.WriteLine($"Creating {accountsToImport.Count} accounts");
                    var startCreate = DateTime.Now;

                    //Create the accounts in parallel
                    Parallel.ForEach(accountsToImport, parallelOptions, (account) =>

                    {
                        //Add the Uri returned to the ConcurrentBag to delete later
                        accountsToDelete.Add(svc.PostCreate("accounts", account));
                    });

                    //Calculate the duration to complete
                    var secondsToCreate = (DateTime.Now - startCreate).TotalSeconds;

                    Console.WriteLine($"Created {accountsToImport.Count} accounts in  {Math.Round(secondsToCreate)} seconds.");

                    Console.WriteLine($"Deleting {accountsToDelete.Count} accounts");
                    var startDelete = DateTime.Now;

                    //Delete the accounts in parallel
                    Parallel.ForEach(accountsToDelete, parallelOptions, (uri) =>
                    {
                        svc.Delete(uri);
                    });

                    //Calculate the duration to complete
                    var secondsToDelete = (DateTime.Now - startDelete).TotalSeconds;

                    Console.WriteLine($"Deleted {accountsToDelete.Count} accounts in {Math.Round(secondsToDelete)} seconds.");
                    Console.WriteLine("Sample completed. Press any key to exit.");
                    Console.ReadLine();
                }
            }
            catch (Exception)
            {
                throw;
            }
        }
    }
}
```

### <a name="see-also"></a>Siehe auch

[Verwenden der Common Data Service-Web-API](../overview.md)<br />
[Web-API CDSWebApiService-Klassenbeispiel (C#)](cdswebapiservice.md)<br />
[Web-API CDSWebApiService Async Parallel Operations Beispiel (C#)](cdswebapiservice-async-parallel-operations.md)<br />
[Web-API CDSWebApiService Beispiel für grundlegende Operationen (C#)](cdswebapiservice-basic-operations.md)<br />
[Erstellen einer Entität mithilfe des Web-API](../create-entity-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](../update-delete-entities-using-web-api.md)
---
title: Web-API CDSWebApiService Async Beispiel für parallele Operationen (C#) (Common Data Service) | Microsoft Docs
description: In diesem Beispiel wird die Verwendung von TPL-Datenflusskomponenten (Task Parallel Library) mit asynchronen Anforderungen demonstriert.
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
ms.openlocfilehash: 3a0ac308195bbdb2c13e769c9ccac80c79902f20
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276705"
---
# <a name="web-api-cdswebapiservice-async-parallel-operations-sample-c"></a>Web API CDSWebApiService Beispiel für parallele Operationen (C#)

Dieses Beispiel demonstriert die Verwendung von TPL-Datenflusskomponenten (Task Parallel Library, TPL) [Datenfluss (Task Parallel Library)](/dotnet/standard/parallel-programming/dataflow-task-parallel-library) mit asynchronen Anforderungen.

TPL bietet Funktionen zum Hinzufügen von Parallelität und Gleichzeitigkeit zu Anwendungen. Diese Fähigkeiten sind ein wichtiger Teil der Maximierung des Durchsatzes bei der Durchführung von Operationen, die Daten innerhalb des CDS hinzufügen oder aktualisieren.

In diesem Beispiel werden asynchrone Methoden der CDSWebApiService-Klasse innerhalb asynchroner Vorgänge verwendet. Da die CDSWebApiService-Klasse die Service Protection API-Limits verwalten kann, kann dieser Code gegenüber den vorübergehenden 429 Fehlern, mit denen Kunden rechnen müssen, widerstandsfähig sein. Es wird eine konfigurierbare Anzahl von Wiederholungsversuchen durchgeführt. Für weitere Informationen gehen Sie zu: [API-Grenzwerte für den Serviceschutz](../../api-limits.md)

Dieses Beispiel erstellt einfach eine konfigurierbare Anzahl von zu erstellenden Kontendatensätzen, die es dann wiederum löscht. Dieses Beispiel verwendet Datenflusskomponenten, um die Datensätze zu verarbeiten und die Ergebnisse des Erstellungsvorgangs in die nächste Phase zu transformieren, in der diese Datensätze gelöscht werden. Aufgrund der Art dieses Datenflusses beginnen Löschvorgänge für zuvor erstellte Datensätze, bevor alle zu erstellenden Datensätze abgeschlossen sind.

## <a name="prerequisites"></a>Voraussetzungen

Folgendes ist erforderlich, um die C#-Beispiele für CDSWebApiService zu erstellen und auszuführen:

- Microsoft Visual Studio 2019. 
- Zugang zu Common Data Service mit Privilegien zur Durchführung von CRUD-Operationen.
  
<a name="bkmk_runSample"></a>
  
## <a name="how-to-run-this-sample"></a>Wie man dieses Beispiel ausführt

1. Gehen Sie zu [Web API CDSWebApiService Beispiel](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/webapi/C%23/CDSWebApiService), klonen Sie das Beispiel-Repository oder laden Sie es herunter und extrahieren Sie seinen Inhalt in einen lokalen Ordner.

1. Öffnen Sie die Datei [CDSWebApiService.sln](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/CDSWebApiService.sln).

1. Wählen Sie das Projekt **AsyncParallelOperations** und öffnen Sie die App.config. Dies ist eine gemeinsame Datei [App.config](https://github.com/microsoft/PowerApps-Samples/blob/master/cds/webapi/C%23/CDSWebApiService/App.config), die von allen Beispielen in dieser Lösung verwendet wird. Sobald Sie diese bearbeiten, können Sie jedes der Beispiele in dieser Lösung ausführen.

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

1. Stellen Sie sicher, dass das Projekt **AsyncParallelOperations** als Startprojekt festgelegt ist. Der Name des Projekts sollte fettgedruckt sein, um anzuzeigen, dass es sich um das Startprojekt handelt. Wenn der Name nicht fett ist, klicken Sie im Lösungsexplorer mit der rechten Maustaste darauf und wählen Sie **Als Startprojekt festlegen**.

1. Drücken Sie F5, um das Programm im Debug-Modus auszuführen.

## <a name="code-listing"></a>Codelisten

Dieses Beispiel hängt von der im CDSWebAPIService-Projekt enthaltenen Assembly ab. Informationen über die Methoden, die diese Klasse zur Verfügung stellt, finden Sie unter [Web-API CDSWebApiService-Klasse Beispiel (C#)](cdswebapiservice.md).

Es folgt der Code aus der Datei Program.cs:

```csharp
using Newtonsoft.Json.Linq;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Threading.Tasks;
using System.Threading.Tasks.Dataflow;

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

        private static async Task Main()
        {
            #region Optimize Connection

            //Change max connections from .NET to a remote service default: 2
            System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
            //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
            System.Threading.ThreadPool.SetMinThreads(100, 100);
            //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
            System.Net.ServicePointManager.Expect100Continue = false;
            //Can decrease overall transmission overhead but can cause delay in data packet arrival
            System.Net.ServicePointManager.UseNagleAlgorithm = false;

            #endregion Optimize Connection

            var executionDataflowBlockOptions = new ExecutionDataflowBlockOptions
            {
                MaxDegreeOfParallelism = maxDegreeOfParallelism
            };

            var count = 0;
            double secondsToComplete;

            //Will be populated with account records to import
            List<JObject> accountsToImport = new List<JObject>();

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

            using (var svc = new CDSWebApiService(serviceConfig))
            {
                secondsToComplete = await ProcessData(svc, accountsToImport, executionDataflowBlockOptions);
            }

            Console.WriteLine($"Created and deleted {accountsToImport.Count} accounts in  {Math.Round(secondsToComplete)} seconds.");

            Console.WriteLine("Sample completed. Press any key to exit.");
            Console.ReadLine();
        }

        private static async Task<double> ProcessData(CDSWebApiService svc, List<JObject> accountsToImport,
            ExecutionDataflowBlockOptions executionDataflowBlockOptions)
        {
            var createAccounts = new TransformBlock<JObject, Uri>(
                async a =>
                {
                    return await svc.PostCreateAsync("accounts", a);
                },
                    executionDataflowBlockOptions
                );

            var deleteAccounts = new ActionBlock<Uri>(
                async u =>
                {
                    await svc.DeleteAsync(u);
                },
                executionDataflowBlockOptions
              );

            createAccounts.LinkTo(deleteAccounts, new DataflowLinkOptions { PropagateCompletion = true });

            var start = DateTime.Now;

            accountsToImport.ForEach(a => createAccounts.SendAsync(a));
            createAccounts.Complete();
            await deleteAccounts.Completion;

            //Calculate the duration to complete
            return (DateTime.Now - start).TotalSeconds;
        }
    }
}
```

### <a name="see-also"></a>Siehe auch

[Verwenden der Common Data Service-Web-API](../overview.md)<br />
[Web-API CDSWebApiService-Klassenbeispiel (C#)](cdswebapiservice.md)<br />
[Web-API CDSWebApiService Beispiel für grundlegende Operationen (C#)](cdswebapiservice-basic-operations.md)<br />
[Web-API CDSWebApiService-Beispiel für parallele Operationen (C#)](cdswebapiservice-parallel-operations.md)<br />
[Erstellen einer Entität mithilfe des Web-API](../create-entity-web-api.md)<br />
[Entitäten aktualisieren und löschen mithilfe der Web API](../update-delete-entities-using-web-api.md)

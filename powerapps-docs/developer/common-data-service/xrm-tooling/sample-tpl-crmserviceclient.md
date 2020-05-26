---
title: 'Beispieldaten: Aufgaben-Parallelbibliothek mit CrmServiceClient (Common Data Service)| Microsoft Docs'
description: Task Parallel Library (TPL) macht Entwickler produktiver, indem es den Prozess des Hinzufügens von Parallelität und Gleichzeitigkeit zu Anwendungen vereinfacht. Dieses Beispiel demonstriert die Verwendung mit CrmServiceClient
ms.custom: ''
ms.date: 04/20/2020
ms.reviewer: pehecke
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
- Dynamics 365 (online)
author: JimDaly
ms.author: nabuthuk
manager: kvivek
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 20aeaaf471e99e2201de90ceb1dbc13985baf7a4
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3276704"
---
# <a name="sample-task-parallel-library-with-crmserviceclient"></a>Beispiel: Task Parallel Library mit CrmServiceClient

Task Parallel Library (TPL) macht Entwickler produktiver, indem es den Prozess des Hinzufügens von Parallelität und Gleichzeitigkeit zu Anwendungen vereinfacht.

Das Hinzufügen von Parallelität und Gleichzeitigkeit kann den Gesamtdurchsatz für Anwendungen, die eine große Anzahl von CDS-Operationen in kurzer Zeit durchführen müssen, erheblich verbessern.

Laden Sie das Beispiel herunter: [Beispiel für Parallelbibliothek mit CrmServiceClient ausführen](https://github.com/microsoft/PowerApps-Samples/tree/master/cds/Xrm%20Tooling/TPLCrmServiceClient)

## <a name="how-to-run-the-sample"></a>Wie das Beispiel ausgeführt wird

1. Um eine lokale Kopie zu erhalten, laden Sie den Beispielbericht herunter und extrahieren Sie ihn.  
2. Öffnen Sie die Datei `TPLCrmServiceClient.sln` in Visual Studio.  
3. Drücken Sie **F5**, um das Programm zu kompilieren und auszuführen.  

## <a name="demonstrates"></a>Demonstriert

Da die [Microsoft.Xrm.Tooling.Connector.CrmServiceClient Class](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient) die Behandlung der durch die CDS-Serviceschutzgrenzen hervorgerufenen vorübergehenden Fehler beinhaltet, ist die Kombination von TPL und CrmServiceClient wertvoll, um Anwendungen zu erstellen, die den Durchsatz optimieren können und gleichzeitig gegenüber den Fehlern der Serviceschutzgrenzen widerstandsfähig sind, indem Anfragen, die aufgrund dieser Grenzen abgelehnt werden, erneut versucht werden.

Für weitere Informationen gehen Sie zu: [API-Grenzwerte für den Serviceschutz](../api-limits.md)

Die Seite [CrmServiceClient.Clone Methode](/dotnet/api/microsoft.xrm.tooling.connector.crmserviceclient.clone) ermöglicht es TPL, den Client mit mehreren Threads zu verwenden.

Dieses einfache Beispiel erzeugt eine Reihe von Datensätzen von Kontoentitäten unter Verwendung der Datei [System.Threading.Tasks.Parallel.ForEach Methode](/dotnet/api/system.threading.tasks.parallel.foreach).

Dann wird es diese Technik erneut anwenden, um die erstellten Entitäten zu löschen.

**HINWEIS**: DIESE ANWENDUNG KANN IN EINER UMGEBUNG KONFIGURIERT WERDEN:
> Standardmäßig werden in diesem Beispiel nur 10 Datensätze erstellt, was nicht ausreicht, um die Fehler der Dienstschutz-Api-Limitierung zu treffen. Wenn Sie den Wert der Variablen `numberOfRecords` auf 10000 erhöhen, können Sie mit Fiddler beobachten, wie einige der Anfragen abgelehnt und erneut geprüft werden.

Dieses Beispiel ist nicht so konfiguriert, dass die Azure-Affinitäts-Cookies deaktiviert werden, was eine weitere Empfehlung zur Verbesserung des Durchsatzes darstellt. Um dies zu aktivieren, fügen Sie Folgendes zur App.config Ihrer Anwendung hinzu:

```xml
  <appSettings>
    <add key="PreferConnectionAffinity"
         value="false" />
  </appSettings>
```

## <a name="code-listing"></a>Codelisten

Der Code für dieses Beispiel ist auf zwei Dateien aufgeteilt, die verschiedene Teile derselben Teilklasse definieren.

SampleProgram.cs enthält diesen Code:

```csharp
using Microsoft.Xrm.Sdk;
using Microsoft.Xrm.Tooling.Connector;
using System;
using System.Collections.Generic;
using System.Linq;

namespace PowerApps.Samples
{
    public partial class SampleProgram
    {
        // Limit on the max degree of parallelism
        private static int maxDegreeOfParallelism = 10;

        //How many records to create with this sample.
        private static readonly int numberOfRecords = 10;

        [STAThread] // Added to support UX
        private static void Main()
        {
            CrmServiceClient service = null;

            try
            {
                service = SampleHelpers.Connect("Connect");
                if (service.IsReady)
                {
                    #region Sample Code

                    #region Set up

                    SetUpSample(service);

                    #endregion Set up

                    #region Demonstrate

                    #region Optimize Connection settings

                    //Change max connections from .NET to a remote service default: 2
                    System.Net.ServicePointManager.DefaultConnectionLimit = 65000;
                    //Bump up the min threads reserved for this app to ramp connections faster - minWorkerThreads defaults to 4, minIOCP defaults to 4
                    System.Threading.ThreadPool.SetMinThreads(100, 100);
                    //Turn off the Expect 100 to continue message - 'true' will cause the caller to wait until it round-trip confirms a connection to the server
                    System.Net.ServicePointManager.Expect100Continue = false;
                    //Can decreas overall transmission overhead but can cause delay in data packet arrival
                    System.Net.ServicePointManager.UseNagleAlgorithm = false;

                    #endregion Optimize Connection settings

                    // Generate a list of account entities to create.

                    var accountsToImport = new List<Entity>();
                    var count = 0;
                    Console.WriteLine($"Preparing to create {numberOfRecords} acccount records");
                    while (count < numberOfRecords)
                    {
                        var account = new Entity("account");
                        account["name"] = $"Account {count}";
                        accountsToImport.Add(account);
                        count++;
                    }

                    try
                    {
                        Console.WriteLine($"Creating {accountsToImport.Count} accounts");

                        var startCreate = DateTime.Now;

                        //Import the list of accounts
                        var createdAccounts = CreateEntities(service, accountsToImport);

                        var secondsToCreate = (DateTime.Now - startCreate).TotalSeconds;

                        Console.WriteLine($"Created {accountsToImport.Count} accounts in  {Math.Round(secondsToCreate)} seconds.");

                        Console.WriteLine($"Deleting {createdAccounts.Count} accounts");
                        var startDelete = DateTime.Now;

                        //Delete the list of accounts created
                        DeleteEntities(service, createdAccounts.ToList());

                        var secondsToDelete = (DateTime.Now - startDelete).TotalSeconds;

                        Console.WriteLine($"Deleted {createdAccounts.Count} accounts in {Math.Round(secondsToDelete)} seconds.");
                    }
                    catch (AggregateException)
                    {
                        // Handle exceptions
                    }

                    Console.WriteLine("Done.");
                    Console.ReadLine();
                }

                #endregion Demonstrate

                #endregion Sample Code

                else
                {
                    const string UNABLE_TO_LOGIN_ERROR = "Unable to Login to Common Data Service";
                    if (service.LastCrmError.Equals(UNABLE_TO_LOGIN_ERROR))
                    {
                        Console.WriteLine("Check the connection string values in cds/App.config.");
                        throw new Exception(service.LastCrmError);
                    }
                    else
                    {
                        throw service.LastCrmException;
                    }
                }
            }
            catch (Exception ex)
            {
                SampleHelpers.HandleException(ex);
            }
            finally
            {
                if (service != null)
                    service.Dispose();

                Console.WriteLine("Press <Enter> to exit.");
                Console.ReadLine();
            }
        }
    }
}
```

SampleMethods.cs enthält die Definition von zwei statischen Methoden (`CreateEntities` und `DeleteEntities`), die im Code verwendet werden:


```csharp
/// <summary>
/// Creates entities in parallel
/// </summary>
/// <param name="svc">The CrmServiceClient instance to use</param>
/// <param name="entities">A List of entities to create.</param>
/// <returns></returns>
private static ConcurrentBag<EntityReference> CreateEntities(CrmServiceClient svc, List<Entity> entities)
{
    var createdEntityReferences = new ConcurrentBag<EntityReference>();

    Parallel.ForEach(entities,
        new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism },
        () =>
        {
            //Clone the CrmServiceClient for each thread
            return svc.Clone();
        },
        (entity, loopState, index, threadLocalSvc) =>
        {
            // In each thread, create entities and add them to the ConcurrentBag
            // as EntityReferences
            createdEntityReferences.Add(
                new EntityReference(
                    entity.LogicalName,
                    threadLocalSvc.Create(entity)
                    )
                );

            return threadLocalSvc;
        },
        (threadLocalSvc) =>
        {
            //Dispose the cloned CrmServiceClient instance
            if (threadLocalSvc != null)
            {
                threadLocalSvc.Dispose();
            }
        });

    //Return the ConcurrentBag of EntityReferences
    return createdEntityReferences;
}

/// <summary>
/// Deletes a list of entity references
/// </summary>
/// <param name="svc">The CrmServiceClient instance to use</param>
/// <param name="entityReferences">A List of entity references to delete.</param>
private static void DeleteEntities(CrmServiceClient svc, List<EntityReference> entityReferences)
{
    Parallel.ForEach(entityReferences,
        new ParallelOptions() { MaxDegreeOfParallelism = maxDegreeOfParallelism },
        () =>
        {
            //Clone the CrmServiceClient for each thread
            return svc.Clone();
        },
        (er, loopState, index, threadLocalSvc) =>
        {
            // In each thread, delete the entities
            threadLocalSvc.Delete(er.LogicalName, er.Id);

            return threadLocalSvc;
        },
        (threadLocalSvc) =>
        {
            //Dispose the cloned CrmServiceClient instance
            if (threadLocalSvc != null)
            {
                threadLocalSvc.Dispose();
            }
        });
}
```

### <a name="more-information"></a>Weitere Informationen

[Parallele Aufgabenbibliothek (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)
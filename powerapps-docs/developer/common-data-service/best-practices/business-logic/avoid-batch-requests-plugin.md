---
title: Vermeiden Sie die Verwendung von Batch-Requesttypen in Plugins und Workflow-Aktivitäten | MicrosoftDocs
description: Sie sollten die Nachrichtenanforderungsklassen ExecuteMultipleRequest oder ExecuteTransactionRequest nicht im Rahmen einer Plug-in- oder Workflow-Aktivität verwenden.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e0732dfee3d4824f33042936af7e8f6157bcec83
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748250"
---
# <a name="avoid-usage-of-batch-request-types-in-plug-ins-and-workflow-activities"></a>Vermeiden Sie die Verwendung von Batch-Requesttypen in Plugins und Workflow-Aktivitäten.

**Kategorie**: Nutzung, Zuverlässigkeit, Leistung, Verfügbarkeit

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Nachfolgend sind mögliche Auswirkungen bei der Verwendung von Nachrichtenanforderungsklassen <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> oder <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest> im Rahmen einer Plugin- oder Workflow-Aktivität aufgeführt:

- Aufgrund ihrer Langlebigkeit setzen Batch-Request-Messages Sandbox-isolierte Plug-In-Typen der zweiminütigen (2000 ms) Kanal-Timeout-Ausnahme aus und können die Benutzererfahrung bei synchronen Registrierungen beeinträchtigen.

- Batch-Anfragen unterliegen einer Parallelitätsdrosselung, die zu unnötigen Ausnahmen bei Serverauslastung führen kann, wenn das Plug-in von mehreren Threads ausgeführt wird. Es gibt ein Limit von zwei gleichzeitigen `ExecuteMultiple`-Operationen pro Online-Instanz.

    > [!NOTE]
    > Für lokale Implementierungen vor Ort ermöglicht die Einstellung [ExecuteAsyncPerOrMaxConnectionsPerServer](/dotnet/api/microsoft.xrm.sdk.deployment.throttlesettings.executeasyncmaxconnectionsperserver) die gleiche Drosselung.  Standardmäßig ist sie nicht für lokale Anwendungen definiert.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Verwenden Sie diese Batch-Meldungen, wenn Code außerhalb der Plattform-Ausführungspipeline ausgeführt wird, wie beispielsweise Integrationsszenarien, bei denen die Netzwerklatenz den Durchsatz reduzieren und die Dauer größerer Massenoperationen erhöhen würde.

Genauer gesagt, verwenden Sie sie in den folgenden Szenarien:

- Verwenden Sie <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>, um Daten oder externe Prozesse, die beabsichtigt sind, lang laufende Operationen durchzuführen (länger als zwei Minuten), in großen Mengen zu erfassen.

- Verwenden Sie <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest>, um die Roundtrips zwischen dem benutzerdefinierten Client und Dynamics 365-Servern zu minimieren und so die kumulative Latenzzeit zu reduzieren.

- Verwenden Sie <xref:Microsoft.Xrm.Sdk.Messages.ExecuteTransactionRequest> für externe Clients, die verlangen, dass der Stapel von Operationen als einzelne, atomare Datenbanktransaktion oder Rollback übertragen wird, wenn eine Ausnahme auftritt. Beachten Sie das Potenzial einer Datenbanksperre für die Dauer der lang laufenden Transaktion.

<a name='problem'></a>

## <a name="problematic-patterns"></a>Problematische Muster

Nachfolgend finden Sie ein Beispiel für die Verwendung von <xref:Microsoft.Xrm.Sdk.Messages.ExecuteMultipleRequest> im Rahmen eines Plugins.

> [!WARNING]
> Dieses Szenario sollte vermieden werden.

```csharp
public class ExecuteMultipleRequestInPlugin : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        IPluginExecutionContext context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
        IOrganizationServiceFactory factory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
        IOrganizationService service = factory.CreateOrganizationService(context.UserId);

        QueryExpression query = new QueryExpression("account")
        {
            ColumnSet = new ColumnSet("accountname", "createdon"),
        };

        //Obtain the results of previous QueryExpression
        EntityCollection results = service.RetrieveMultiple(query);

        if (results != null && results.Entities != null && results.Entities.Count > 0)
        {
            ExecuteMultipleRequest batch = new ExecuteMultipleRequest();
            foreach (Entity account in results.Entities)
            {
                account.Attributes["accountname"] += "_UPDATED";

                UpdateRequest updateRequest = new UpdateRequest();
                updateRequest.Target = account;

                batch.Requests.Add(updateRequest);
            }

            service.Execute(batch);
        }
        else return;

    }
}
```

Dieses Beispiel beinhaltet die Verwendung des Typs direkt mit der Methode `Execute`. Die Verwendung kann überall im Rahmen der Ausführung eines Plugins oder einer Workflow-Aktivität erfolgen. Dies kann auch in einer Methode sein, die in derselben oder einer separaten Klasse enthalten ist. Sie ist nicht darauf beschränkt, direkt in der `Execute`-Methodendefinition enthalten zu sein.

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

`ExecuteMultiple` und `ExecuteTransaction` Nachrichten werden als Batch-Anforderungsmeldungen betrachtet. Ihr Ziel ist es, Roundtrips zwischen Client und Server über Verbindungen mit hoher Latenzzeit zu minimieren. Plug-Ins führen entweder direkt im Anwendungsprozess oder in unmittelbarer Nähe aus, wenn sie von der Sandbox isoliert sind, so dass die Latenz selten ein Problem darstellt. Plug-in-Code sollte sehr fokussierte Operationen sein, die schnell ausgeführt werden und die Blockade minimieren, um das Überschreiten von Timeout-Schwellen zu vermeiden und ein reaktionsfähiges System für synchrone Szenarien zu gewährleisten.

Auf der Serverseite werden die in einer Batch-Anfrage enthaltenen Operationen sequentiell und nicht parallel ausgeführt. Dies ist auch dann der Fall, wenn die <xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings>.<xref:Microsoft.Xrm.Sdk.ExecuteMultipleSettings.ReturnResponses> Eigenschaft wird auf false gesetzt. Entwickler neigen dazu, Batch-Requests auf diese Weise zu verwenden, vorausgesetzt, sie ermöglichen eine parallele Verarbeitung. Batch-Anfragen werden dieses Ziel nicht erreichen. Ein weiterer gemeinsamer Motivator ist der Versuch, sicherzustellen, dass jede Operation in eine Transaktion einbezogen wird. Dies ist unnötig, da das Plug-in oft bereits im Rahmen einer Datenbanktransaktion ausgeführt wird, wodurch die Notwendigkeit der Verwendung der `ExecuteTransaction`-Meldung entfällt.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Ereignisframework](../../event-framework.md)<br />
[Laufzeitbeschränkungen](../../org-service/execute-multiple-requests.md#run-time-limitations)<br/>
[Ausführen mehrerer Anfragen mithilfe des Organisationsservices](../../org-service/execute-multiple-requests.md)<br/>
[Führt Nachrichten in einer einzelnen Datenbanktransaktion aus.](../../org-service/use-executetransaction.md)

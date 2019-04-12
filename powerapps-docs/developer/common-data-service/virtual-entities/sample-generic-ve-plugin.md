---
title: 'Beispiel: Generisches virtuelles Entitätsdatenanbieter-Plug-In (Common Data Service) | Microsoft Docs'
description: 'Das Beispiel veranschaulicht, wie ein virtuelles allgemeines benutzerdefiniertes Dynamics 365 Entitäts-Plug-In implementiert wird.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: samples
applies_to:
  - Dynamics 365 (online)
ms.assetid: d329dade-16c5-46e9-8dec-4b8efb996d24
author: mayadumesh
ms.author: jdaly
manager: amyla
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="sample-generic-virtual-entity-data-provider-plug-in"></a>Beispiel: Generisches virtuelles Entitätsdatenanbieter-Plug-In

## <a name="demonstrates"></a>Demonstriert

Dieses Beispiel zeigt eine minimale Implementierung für das allgmeine virtuelle Common Data Service-Entitätsdatenanbieter-Plug-In **DropboxRetrieveMultiplePlugin** für den Filesharing-Service [Dropbox](https://www.dropbox.com/). Es wird der "Bare Metal"-Ansatz verwendet, wobei der <xref:Microsoft.Xrm.Sdk.Query.QueryExpression> durch das Erstellen einer benutzerdefinierten Besucherklasse **DropBoxExpressionVisitor** übersetzt wird. Es wird eine Sammlung der Dateien zurückgegeben, die den Suchkriterien als <xref:Microsoft.Xrm.Sdk.EntityCollection> entsprechen. 

## <a name="getting-started"></a>Erste Schritte

Um dieses Beispiel zu erstellen, müssen Sie zuerst die NuGet-Pakete [Dropbox.Api](https://www.nuget.org/packages/Dropbox.Api/) und [Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/) in Ihrer Lösung installieren.  Sie benötigen auch ein DropBox-Konto und müssen einen realen Zugriffstoken übergeben, wenn Sie eine Instanz des **DropboxClient** erstellen.

Fügen Sie Ihrem Code die folgenden Using-Anweisung hinzu:

```csharp
using Microsoft.Xrm.Sdk;
using Microsoft.Xrm.Sdk.Query;
using Dropbox.Api;
using Dropbox.Api.Files;
```

## <a name="sample-code"></a>Beispielcode   

```csharp  

public class DropBoxExpressionVisitor : QueryExpressionVisitorBase
{
    public string SearchKeyWords { get; private set; }

    public override QueryExpression Visit(QueryExpression query)
    {
        // Very simple visitor that extracts search keywords
        var filter = query.Criteria;
        if (filter.Conditions.Count > 0)
        {
            foreach (ConditionExpression condition in filter.Conditions)
            {
                if (condition.Operator == ConditionOperator.Like && condition.Values.Count > 0)
                {
                    string exprVal = (string)condition.Values[0];

                    if (exprVal.Length > 2)
                    {
                        this.SearchKeyWords += " " + exprVal.Substring(1, exprVal.Length - 2);
                    }
                }
            }
            return query;
        }
    }
}

public class DropboxRetrieveMultiplePlugin : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        var context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));
        var qe = (QueryExpression)context.InputParameters["Query"];
        if (qe != null)
        {
            var visitor = new DropBoxExpressionVisitor();
            qe.Accept(visitor);
            using (var dbx = new DropboxClient(AccessToken))
            {
                if (visitor.SearchKeyWords != string.Empty)
                {
                    var searchCriteria = new SearchArg(string.Empty, visitor.SearchKeyWords);
                    var task = Task.Run(() => this.SearchFile(dbx, searchCriteria));
                    context.OutputParameters["BusinessEntityCollection"] = task.Result;
                }
            }
        }
    }

    public async Task<EntityCollection> SearchFile(DropboxClient dbx, SearchArg arg)
    {
        EntityCollection ec = new EntityCollection();
        var list = await dbx.Files.SearchAsync(arg);
        foreach (var item in list.Matches)
        {
            if (item.Metadata.IsFile)
            {
                Entity e = new Entity("new_dropbox");
                e.Attributes.Add("new_dropboxid", Guid.NewGuid());
                e.Attributes.Add("new_filename", item.Metadata.AsFile.Name);
                e.Attributes.Add("new_filesize", item.Metadata.AsFile.Size);
                e.Attributes.Add("new_modifiedon", item.Metadata.AsFile.ServerModified);
                ec.Entities.Add(e);
            }
        }
        return ec;
    }
}

``` 

### <a name="see-also"></a>Siehe auch

[Erste Schritte mit virtuellen Entitäten](get-started-ve.md)<br />
[API-Rücksichten auf virtuelle Entitäten](api-considerations-ve.md)<br />
[Benutzerdefinierte virtuelle Entitätsdatenanbieter](custom-ve-data-providers.md)
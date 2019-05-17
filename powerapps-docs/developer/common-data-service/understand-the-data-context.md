---
title: Verstehen des Ausführungskontexts (Common Data Service) | Microsoft Docs
description: 'Erfahren Sie mehr über die Daten, die bei der Ausführung an Ihre Plugins übergeben werden.'
ms.custom: ''
ms.date: 1/23/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: phecke
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="understand-the-execution-context"></a>Verstehen des Ausführungskontextes

Die **Event Execution Pipeline** übergibt registrierten Plugins eine Fülle von Daten über den aktuellen Vorgang und die Ausführungsumgebung des Plug-Ins. Sie können auf diese Daten in Ihrem Plugin-Code zugreifen, indem Sie eine Variable setzen, die die Schnittstelle <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> implementiert:

```csharp
// Obtain the execution context from the service provider.  
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));
```

Dieser <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> bietet einige Informationen über die <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.Stage>, für die das Plug-In registriert ist, sowie Informationen über den <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext>, der Informationen über jeglichen Vorgang innerhalb eines anderen Plug-In bereitstellt, das den aktuellen Vorgang ausgelöst hat.

Die übrigen verfügbaren Informationen werden jedoch von der <xref:Microsoft.Xrm.Sdk.IExecutionContext>-Schnittstelle bereitgestellt, die diese Klasse implementiert. Alle Eigenschaften dieser Klasse stellen nützliche Informationen bereit, auf die Sie möglicherweise in Ihrem Code zugreifen müssen, aber zwei der wichtigsten sind die Eigenschaften <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> und <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>. 

Andere häufig verwendete Eigenschaften sind <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables>, <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> und <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages>.

> [!TIP]
> Eine gute Möglichkeit, die Daten, die in den Ausführungskontext übergeben werden, zu visualisieren, besteht darin, die Plug-In-Profiler-Lösung zu installieren, die als Teil des Plug-In-Registrierungstool verfügbar ist. Der Profiler erfasst die Kontextinformationen sowie Informationen, die die erneute Wiedergabe des Ereignisses lokal ermöglichen, sodass Sie debuggen können. Innerhalb des Plug-In-Registrierungstools können Sie ein XML-Dokument mit allen Daten aus dem Ereignis herunterladen, das den Workflow ausgelöst hat. Weitere Informationen: [Plug-In-Profildaten anzeigen](debug-plug-in.md#view-plug-in-profile-data)

## <a name="parametercollections"></a>ParameterCollections

All Eigenschaften des Ausführungskontexts sind schreibgeschützt. Aber die `InputParameters`, `OutputParameters` und `SharedVariables` sind <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Werte. Sie können die Werte der Elemente in diesen Sammlungen manipulieren, um das Verhalten des Vorgangs zu ändern, je nach Phase in der Ereignisausführungspipeline, für die Ihr Plug-In registriert ist.

Die <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Werte sind als <xref:System.Collections.Generic.KeyValuePair%602>-Strukturen definiert. Um auf eine Eigenschaft zuzugreifen, müssen Sie den Namen der Eigenschaft wissen, die von der Nachricht zur Verfügung gestellt wird. Um beispielsweise auf die <xref:Microsoft.Xrm.Sdk.Entity>-Eigenschaft zuzugreifen, die als Teil der <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> übergeben wird, müssen Sie wissen, dass der Name dieser Eigenschaft `Target` ist. Dann können Sie auf diesen Wert folgendermaßen mithilfe von Code zugreifen:

```csharp
var entity = (Entity)context.InputParameters["Target"];
```
Verwenden Sie die Dokumentation <xref:Microsoft.Xrm.Sdk.Messages> und <xref:Microsoft.Crm.Sdk.Messages>, um die Namen der Nachrichten zu erfahren, die in den SDK-Assemblys definiert sind. Für benutzerdefinierte Aktionen finden Sie weitere Informationen unter den Namen der Parameter, die im System definiert sind.

## <a name="inputparameters"></a>InputParameters

Die `InputParameters` stellen den Wert der <xref:Microsoft.Xrm.Sdk.OrganizationRequest>.<xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters>- Eigenschaft dar, die den von den Webdiensten eingehenden Vorgang darstellt.

Wie beschrieben unter [Nachrichten mit Organisationsdienst verwenden](org-service/use-messages.md), sind alle Vorgänge, die sich im System ereignen letztlich Instanzen der `OrganizationRequest`-Klasse, die von <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> vverarbeitet wird Methode.

Wie im [Ereignisframework](event-framework.md) beschrieben, durchlaufen Vorgänge eine Reihe von Phasen, und Sie können Ihr Plug-In in Phasen registrieren, die auftreten, bevor die Daten in die Datenbank geschrieben werden. Innerhalb der **PreValidation**- und **PreOperation**-Phasen können Sie die Werte der `InputParameters` lesen und ändern, sodass Sie das erwartete Ergebnis des Datenenvorgangs steuern können.

Wenn Sie feststellen, dass die Werte in der `InputParameters`-Sammlung eine Bedingung darstellen, die Sie nicht zulassen können, können Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> auslösen (vorzugsweise in der Phase **PreValidation**). Dadurch wird der Vorgang abgebrochen und dem Benutzer mit einem synchronsen Plug-In ein Fehler angezeigt, oder es wird der Fehler protokolliert, wenn das Plug-In asynchron ist. Weitere Informationen: [Abbrechen eines Vorgangs](handle-exceptions.md#cancelling-an-operation)

## <a name="outputparameters"></a>OutputParameters

Die `OutputParameters` stellen den Wert der <xref:Microsoft.Xrm.Sdk.OrganizationResponse>.<xref:Microsoft.Xrm.Sdk.OrganizationResponse.Results>- Eigenschaft dar, die den Rückgabewert des Vorgangs darstellt. Die `OutputParameters` werden nicht vor der Datenbanktransaktion aufgefüllt. Somit sind sie erst für Plug-Ins verfügbar, die in der **PostOperation**-Phase registriert werden. Wenn Sie die Werte ändern möchten, die von dem Vorgang zurückgegeben wurden, können Sie sie in den `OutputParameters` ändern.

## <a name="shared-variables"></a>Freigegebene Variablen

Die <xref:Microsoft.Xrm.Sdk.IExecutionContext.SharedVariables>-Eigenschaft lässt das Einschließen von Daten zu, die von einem Plug-In an einen Schritt übergeben werden können, der später in der Ausführungspipeline auftritt. Da dies ein <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Wert ist, können Plug-Ins Eigenschaften hinzufügen, lesen oder ändern, um Daten für nachfolgende Schritten freizugeben.

Das folgende Beispiel zeigt, wie ein `PrimaryContact`-Wert von einem Plug-In übergeben werden kann, das für einen **PreOperation**-Schritt an einen **PostOperation**-Schritt registriert ist.

```csharp
public class PreOperation : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        // Obtain the execution context from the service provider.
        Microsoft.Xrm.Sdk.IPluginExecutionContext context = (Microsoft.Xrm.Sdk.IPluginExecutionContext)
            serviceProvider.GetService(typeof(Microsoft.Xrm.Sdk.IPluginExecutionContext));

        // Create or retrieve some data that will be needed by the post event
        // plug-in. You could run a query, create an entity, or perform a calculation.
        //In this sample, the data to be passed to the post plug-in is
        // represented by a GUID.
        Guid contact = new Guid("{74882D5C-381A-4863-A5B9-B8604615C2D0}");

        // Pass the data to the post event plug-in in an execution context shared
        // variable named PrimaryContact.
        context.SharedVariables.Add("PrimaryContact", (Object)contact.ToString());
    }
}

public class PostOperation : IPlugin
{
    public void Execute(IServiceProvider serviceProvider)
    {
        // Obtain the execution context from the service provider.
        Microsoft.Xrm.Sdk.IPluginExecutionContext context = (Microsoft.Xrm.Sdk.IPluginExecutionContext)
            serviceProvider.GetService(typeof(Microsoft.Xrm.Sdk.IPluginExecutionContext));

        // Obtain the contact from the execution context shared variables.
        if (context.SharedVariables.Contains("PrimaryContact"))
        {
            Guid contact =
                new Guid((string)context.SharedVariables["PrimaryContact"]);

            // Do something with the contact.
        }
    }
}
```
> [!IMPORTANT]
> Jede Art von Daten, die der Collection der gemeinsamen Variablen hinzugefügt werden, muss serialisierbar sein, da der Server sonst nicht weiß, wie die Daten serialisiert werden sollen, und die Ausführung des Plugins schlägt fehl.  
  
 Bei einem Plug-In, das in Phase 20 oder 40 registriert wird, um auf die freigegebenen Variablen eines in Phase 10 registrierten Plug-Ins zuzugreifen, das beim Erstellen, Aktualisieren Löschen oder <xref:Microsoft.Crm.Sdk.Messages.RetrieveExchangeRateRequest> ausgeführt wird, müssen Sie auf die Sammlung <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext.ParentContext>.**SharedVariables** zugreifen In allen anderen Fällen enthält <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>.**SharedVariables** die Sammlung. 

## <a name="entity-images"></a>Entitätsbilder

Wenn Sie einen Schritt für ein Plug-In registrieren, das eine Entität vom Datenmigrations-Assistenten als einen der Parameter enthält, haben Sie die Möglichkeit anzugeben, ob eine Kopie der Entitätsdaten als *Momentaufnahme* oder Bild mit der <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> und/oder <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages> Eigenschaft ist.

Diese Daten stellen einen Vergleichspunkt für Entitätsdaten zur Verfügung, während sie durch die Ereignispipeline durchfließt. Mithilfe dieser Bilder kann eine bessere Leistung bereitgestellt werden, anstelle Code in einen Plug-In einzubeziehen, um eine Entität abzurufen, nur um die Attributwerte zu vergleichen.

Wenn Sie ein Entitätsbild definieren, geben Sie einen Entitätsaliaswert an, die Sie verwenden können, um auf das gewünschte Bild zuzugreifen. Wenn Sie zum Beispiel ein Vorentitätsbild definieren mit dem Alias "`a`", können Sie den folgenden Code verwenden, um auf den Attributwert `name` zuzugreifen.

```csharp
var oldAccountName = (string)context.PreEntityImages["a"]["name"];
```

Weitere Informationen: [Entitätsbilder definieren](register-plug-in.md#define-entity-images)

### <a name="see-also"></a>Siehe auch

[Ereignisframework](event-framework.md)  
[Schreiben eines Plug-Ins](write-plug-in.md)
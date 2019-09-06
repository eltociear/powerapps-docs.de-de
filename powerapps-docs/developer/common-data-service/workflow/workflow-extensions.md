---
title: Workflow-Erweiterungen (Common Data Service) | Microsoft Docs
description: 'Sie können die Optionen erweitern, die innerhalb des Designers für Workflows zur Verfügung stehen. Diese Erweiterungen werden hinzufügt, indem eine Assembly hinzufügt wird, die eine Klasse enthält, die die CodeActivity-Klasse erweitert. Diese Erweiterungen werden häufig als Workflowassemblys oder Workflowaktivitäten bezeichnet.'
ms.custom: ''
ms.date: 07/16/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="workflow-extensions"></a>Workflowerweiterungen

Sie können die Optionen erweitern, die innerhalb des Designers für Workflows zur Verfügung stehen, die in Common Data Service verwendet werden. Diese Erweiterungen werden hinzufügt, indem eine Assembly hinzufügt wird, die eine Klasse enthält, die die [CodeActivity](/dotnet/api/system.activities.codeactivity)-Klasse erweitert. Diese Erweiterungen werden allgemein als *Workflow-Assemblys* oder *Workflow-Aktivitäten* bezeichnet.

Sie können diese benutzerdefinierten Erweiterungen innerhalb des Designers verwenden, der für Workflows, benutzerdefinierte Aktionen und Dialoge verwendet wird.

> [!IMPORTANT]
> Wenn immer möglich, sollten Sie zunächst erwägen, eine von mehreren deklarativen Optionen zur Definition der Geschäftslogik anzuwenden. Weitere Informationen: [Anwenden von Geschäftslogik in Common Data Service](../../../maker/common-data-service/cds-processes.md)
> 
> Verwenden Sie Workflowerweiterungen, wenn ein deklarativer Prozess nicht Ihre Bedingung erfüllt.
> 
> Dieser Inhalt ist für Common Data Service-Workflow-Assemblys und gilt auch für Dynamics 365 for Customer Engagement-Apps (online). Optionen für lokale Bereitstellungen von Dynamics 365 for Customer Engagement-Apps sind hier beschrieben: [Lokale Optionen](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies#on-premises-options).

## <a name="when-to-create-a-workflow-extension"></a>Wann eine Workflowerweiterung zu erstellen ist

Wenn Sie mithilfe der Standardprozessaktivitäten nicht die erforderliche Funktion finden, können Sie benutzerdefinierte Aktivitäten hinzufügen, sodass sie im Editor verfügbar sind, der zum Erstellen von Workflow-, Dialog- und Aktionsprozessen verwendet wird.

Standardmäßig umfassen diese Prozesse einen allgemeinen Satz von Aktivitäten, die Sie ausführen können, wie in der folgenden Tabelle gezeigt:

|Aktivität|Workflow|Aktion|Dialogfeld|
|--|--|--|--|
|Daten abfragen|||X|
|Wert zuweisen||X|X|
|Datensatz erstellen|X|X|X|
|Datensatz aktualisieren|X|X|X|
|Datensatz zuweisen|X|X|X|
|E-Mail senden|X|X|X|
|Untergeordneten Workflow starten|X|X|X|
|Aktion durchführen|X|X||
|Untergeordnetes Dialogfeld verknüpfen|||X|
|Status ändern|X|X|X|
|Workflow beenden|X|X||
|Dialog anhalten|||X|

Sie können die Aktivität **Aktion durchführen** verwenden, um sämtliche benutzerdefinierten Aktionen oder die folgenden Systemmeldungen, die als **Befehlsaktionen** bezeichnet werden, auszuführen:

||||
|--|--|--|
|AddToQueue|AddUserToRecordTeam|RemoveUserFromRecordTeam|
|SetProcess|SetWordTemplate||

Wenn Sie Dynamics 365 Customer Engagement Sales oder Service-Lösungen haben, können Sie andere Befehlsaktionen, je nach Lösung, finden:

||||
|--|--|--|
|ApplyRoutingRule|CalculateActualValue|Verkaufschance schließen|
|GetQuoteProductsFromOpportunity|GetSalesOrderProductsFromOpportunity|LockInvoicePricing|
|LockSalesOrderPricing|QualifyLead|RemoveUserFromRecordTeam|
|ResolveIncident|ResolveQuote|Überarbeiten|
|UnlockInvoicePricing|UnlockSalesOrderPricing|

Weitere Informationen: 

- [Workflowphasen und Schritte konfigurieren](/flow/configure-workflow-steps)
- [Verwenden von Common Data Service-Dialogen für Kundeninteraktionen](/flow/use-cds-for-apps-dialogs)
- [Erstellen eines benutzerdefinierten Attributs](/flow/create-actions)



## <a name="technology-used"></a>Verwendete Technik

Sie können eine Assembly registrieren, die mit der [.NET Framework Activity Library](/dotnet/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library) erstellt wurde, die benutzerdefinierte Aktivitäten definiert, die im Webanwendungseditor erscheinen und beim Ausführen des Prozesses aufgerufen werden.

Benutzerdefinierte Workflowaktivitäten erfordern das Erstellen einer .NET Framework-Assembly, die mindestens eine Klasse enthält, die aus der Zusammenfassung abgeleitet ist [CodeActivity-Klasse](/dotnet/api/system.activities.codeactivity?view=netframework-4.6.2). Diese Klasse stellt die [Execute(CodeActivityContext)-Methode](/dotnet/api/system.activities.codeactivity.execute?view=netframework-4.6.2) bereit, die von der Common Data Service-Plattform aufgerufen wird, wenn die Aktivität ausgeführt wird. Jede Klasse in Ihrer Assembly definiert eine bestimmte Aktivität.

Workflow-Aktivitäten sollten Ein- und Ausgabeparameter definieren, die im Prozessdesigner sichtbar sind und es jemandem ermöglichen, Daten in die Workflow-Aktivität zu übergeben und die verarbeitete Ausgabe zu erhalten. Wenn Sie die Klasse schreiben, fügen Sie Eigenschaften für diese Parameter hinzu und fügen zu ihnen Anmerkungen mit [.NET-Attributen](/dotnet/standard/attributes/index) hinzu, um die Metadaten bereitzustellen, die Common Data Service verwenden wird, um Ihre benutzerdefinierte Workflowaktivität mit sämtlichen Parametern im Designer verfügbar zu machen.

## <a name="create-a-custom-workflow-activity-assembly"></a>Erstellen einer benutzerdefinierten Workflowaktivitäts-Assembly

Im Folgenden werden allgemeine Schritte angegeben, die verwendet werden, um eine benutzerdefinierte Workflowaktivität mithilfe von Visual Studio zu erstellen. Ein vollständiges Beispiel mit einer Schritt-für-Schritt-Anleitung finden Sie unter [Tutorial: Erstellen einer Workflowerweiterung ](tutorial-create-workflow-extension.md) Sie unter.

1. Erstellen Sie ein Klassenbibliotheksprojekt mit .NET Framework 4.6.2 als Zielframework.
    > [!IMPORTANT]
    > Während die Assemblys, die spätere Versionen verwenden, im Allgemeinen funktionieren. Wenn sie eine Funktion verwenden, die nach 4.6.2 eingeführt wurde, tritt ein Fehler auf.
1. Installieren Sie das [Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/)-NuGet-Paket.

    Dieses Paket umfasst das [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)-Paket.

1. (Optional) Wenn Sie Entitätsklassen mit früher Bindung verwenden möchten, schließen Sie in das Projekt ein.

    Weitere Informationen: 

    - [Programmierung mit später und früher Bindung mithilfe des Organisationsdiensts](../org-service/early-bound-programming.md)
    - [Generieren von Klassen mit früher Bindung für den Organisationsdienst](../org-service/generate-early-bound-classes.md) 

1. Fügen Sie eine öffentliche Klasse hinzu. Der Name der Klasse sollte der von der Aktivität auszuführenden Aktion entsprechen.
1. Die folgenden using-Direktiven hinzufügen

    ```csharp
    using System.Activities;
    using Microsoft.Xrm.Sdk;
    using Microsoft.Xrm.Sdk.Workflow;
    ```

1. Fügen Sie Eigenschaften der Klasse hinzu, um alle Eingabe- oder Ausgabeparameter darzustellen und verwenden Sie [.NET-Attribute](/dotnet/standard/attributes/index), um die erforderlichen Metadaten bereitzustellen, um diese Eigenschaften dem Workflowprozess-Designer verfügbar zu machen.

    Weitere Informationen: [Parameter hinzufügen](#add-parameters)

1. Stellen Sie sicher, dass Ihre Klasse von der [CodeActivity-Klasse](/dotnet/api/system.activities.codeactivity?view=netframework-4.6.2) abgeleitet ist, und implementieren Sie die [Execute(CodeActivityContext)-Methode](/dotnet/api/system.activities.codeactivity.execute?view=netframework-4.6.2), die die Vorgänge enthält, die Ihre Aktivität ausführen wird.

    Weitere Informationen: [Fügen Sie Ihren Code der Execute-Methode hinzu](#add-your-code-to-the-execute-method)

1. Signieren Sie Ihre Assembly
1. Erstellen Sie Ihre Assembly.
1. Registrieren Sie Ihr Assembly mit dem Plug-in-Registrierungstool und legen Sie die Eigenschaften `Name` und `WorkflowActivityGroupName` fest, um den Text zu definieren, der im Prozessdesigner sichtbar sein soll.

    Weitere Informationen: [Ihre Assembly registrieren](#register-your-assembly)

1. Testen Sie Ihre Workflowaktivität, indem Sie sie von innerhalb eines Workflows, eines Dialogs oder von Aktionsprozessen aus aufrufen
1. (Empfohlen) Fügen Sie Ihrer Workflowaktivität einer Lösung hinzu.

## <a name="add-parameters"></a>Parameter hinzufügen

Wenn Sie Parameter für Ihre Klasse definieren, müssen Sie sie als [InArgument\<T>](/dotnet/api/system.activities.inargument-1)-, [OutArgument\<T>](/dotnet/api/system.activities.outargument-1)- oder [InOutArgument\<T>](/dotnet/api/system.activities.inoutargument-1)-Typen definieren. Diese Typen stellen Methoden bereit, die von einer allgemeinen [Argument-Klasse](/dotnet/api/system.activities.argument) geerbt werden zum Abrufen oder Festlegen der Parameter. Ihr Code verwendet diese Methoden in der Execute-Methode. Weitere Informationen: [Fügen Sie Ihren Code der Execute-Methode hinzu](#add-your-code-to-the-execute-method)

Wenn Ihre benutzerdefinierte Workflowaktivität Eingabe- oder Ausgabeparameter verwendet, müssen Sie den öffentlichen Klasseneigenschaften, die sie definieren, entsprechende .NET-Attribute hinzufügen. Die Daten werden vom Prozess-Designer gelesen, um zu definieren, wie die Parameter im Prozess-Designer festgelegt werden können.

Sie können die folgenden Eigenschaftstypen als Eingabe- oder Ausgabeparameter verwenden:

||||
|--|--|--|
|[bool](/dotnet/api/system.boolean)|[DateTime](/dotnet/api/system.datetime)|[Dezimalzahl](/dotnet/api/system.decimal)|
|[Doppelt](/dotnet/api/system.double)|<xref:Microsoft.Xrm.Sdk.EntityReference>|[int](/dotnet/api/system.int32)|
|<xref:Microsoft.Xrm.Sdk.Money>|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|[Zeichenfolge](/dotnet/api/system.string)|

### <a name="input-and-output-parameters"></a>Eingabe- und Ausgabeparameter

Um den Text zu definieren, der für ein Eingabe- oder Ausgabeparameter im Prozess-Designer angezeigt werden soll, verwenden Sie das folgende Muster mithilfe von [.NET Attributen](/dotnet/standard/attributes/index).

```csharp
[Input("Integer input")]
public InArgument<int> IntInput { get; set; }
```

oder

```csharp
[Output("Integer output")]
public OutArgument<int> IntOutput { get; set; }
```

Eine einzelne Eigenschaft in Ihrer Klasse kann sowohl ein Eingabe- als auch ein Ausgabeparameter sein, indem beide Attribute eingeschlossen werden:

```csharp
[Input("Int input")]  
[Output("Int output")]  
public InOutArgument<int> IntParameter { get; set; }
```


### <a name="required-values"></a>Erforderliche Werte

Wenn Sie einen Eingabeparameter erstellen möchten, der bei der Verwendung der Workflowaktivität in einem Prozess erforderlich ist, müssen Sie das `[RequiredArgument]`-Attribut verwenden.

### <a name="default-values"></a>Standardwerte

Wird ein Wert, der als Eingabeparameter übergeben wird oder als Ausgabeparameter festgelegt wird, nicht definiert wird, können Sie einen Standardwert angeben. So legen Sie beispielsweise den Standardwert für eine boolesche Eigenschaft fest:

```csharp
[Input("Bool input")]
[Default("True")]
public InArgument<bool> Bool { get; set; }
```

Das Format für den Standardwert hängt vom Typ der Eigenschaft ab. In der folgenden Tabelle sind einige Beispiele:

|Typ|Beispiel|
|--|--|
|[bool](/dotnet/api/system.boolean)|[Default("True")]|
|[DateTime](/dotnet/api/system.datetime)|[Default("2004-07-09T02:54:00Z")]|
|[Dezimalzahl](/dotnet/api/system.decimal)|[Default("23.45")]|
|[Doppelt](/dotnet/api/system.double)|[Default("23.45")]|
|<xref:Microsoft.Xrm.Sdk.Money>|[Default("23.45")]|
|<xref:Microsoft.Xrm.Sdk.EntityReference>|[Default("3B036E3E-94F9-DE11-B508-00155DBA2902", "account")]|
|[int](/dotnet/api/system.int32)|[Default("23")]|
|<xref:Microsoft.Xrm.Sdk.OptionSetValue>|[Default("3")]|
|[Zeichenfolge](/dotnet/api/system.string)|[Default("string default")]|

### <a name="entityreference-parameters"></a>EntityReference-Parameter

Wenn Sie eine Eigenschaft für einen <xref:Microsoft.Xrm.Sdk.EntityReference>-Parameter definieren, müssen Sie das Attribut `ReferenceTarget` verwenden. Dies legt fest, welcher Attributtyp zulässig ist. Beispiel:

```csharp
[Input("EntityReference input")]
[Output("EntityReference output")]
[ReferenceTarget("account")]
public InOutArgument<EntityReference> AccountReference { get; set; }
```

### <a name="optionsetvalue-parameters"></a>OptionSetValue-Parameter

Wenn Sie eine Eigenschaft für einen <xref:Microsoft.Xrm.Sdk.OptionSetValue>-Parameter definieren, müssen Sie das Attribut `AttributeTarget` verwenden. Dieses Attribut definiert, welche Entitäten und welches Attribut den gültigen Satz von Werten für den Parameter enthält. Beispiel:

```csharp
[Input("Account IndustryCode value")]
[AttributeTarget("account", "industrycode")]
[Default("3")]
public InArgument<OptionSetValue> IndustryCode { get; set; }
```

## <a name="add-your-code-to-the-execute-method"></a>Fügen Sie Ihren Code der Execute-Methode hinzu

Die Logik, die Sie in die [CodeActivity.Execute(CodeActivityContext)-Methode](/dotnet/api/system.activities.codeactivity.execute?view=netframework-4.6.2)-Methode einbeziehen, definiert, was Ihre Workflowaktivität ausführt.

> [!IMPORTANT]
> Der Code in der `Execute`-Methode sollte als statusfrei geschrieben werden. Es wird nicht empfohlen, globale oder Membervariablen zu verwenden, um Daten von einem Aufruf zum nächsten zu übergeben.
> Zur Verbesserung der Leistung werden benutzerdefinierte Workflowaktivitätsinstanzen von Common Data Service zwischengespeichert. Deshalb wird der Konstruktor nicht für jeden Aufruf der benutzerdefinierten Workflowaktivität aufgerufen. Außerdem könnten mehrere Systemthreads die benutzerdefinierte Workflowaktivität gleichzeitig ausführen. Sie sollten nur die Informationen verwenden, die über den Parameter [CodeActivityContext](/dotnet/api/system.activities.codeactivitycontext) an die `Execute`-Methode übergeben werden.

### <a name="reference-parameters"></a>Parameter referenzieren

Um auf Parameter, die für Ihre Klasse definiert sind, zu verweisen, verwenden Sie die Methoden [Argument.Get](/dotnet/api/system.activities.argument.get?view=netframework-4.6.2) oder [Argument.Set(ActivityContext, Object)](/dotnet/api/system.activities.argument.set?view=netframework-4.6.2), die sie bereitstellen. Diese erfordern die Instanz [CodeActivityContext](/dotnet/api/system.activities.codeactivitycontext), die an die `Execute`-Methode übergeben wird. Im folgenden Beispiel wird gezeigt, wie auf den Wert eines Eingabeparameters zugegriffen wird und wie der Wert eines Ausgabeparameters festgelegt wird.

```csharp
using Microsoft.Xrm.Sdk.Workflow;
using System.Activities;

namespace SampleWorkflowActivity
{
  public class IncrementByTen : CodeActivity
  {
    [RequiredArgument]
    [Input("Decimal input")]
    public InArgument<decimal> DecInput { get; set; }

    [Output("Decimal output")]
    public OutArgument<decimal> DecOutput { get; set; }

    protected override void Execute(CodeActivityContext context)
    {
      decimal input = DecInput.Get(context);
      DecOutput.Set(context, input + 10);
    }
  }
}
```

### <a name="get-contextual-information"></a>Kontextbezogene Informationen abrufen

Wenn Ihr Code kontextbezogene Informationen benötigt, können Sie darauf mithilfe der [CodeActivityContext.GetExtension\<T>-Methode](/dotnet/api/system.activities.activitycontext.getextension) mit der <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext>-Schnittstelle zugreifen. Dieses Objekt wird von der <xref:Microsoft.Xrm.Sdk.IExecutionContext>-Schnittstelle abgeleitet, welche Zugriff auf viele schreibgeschützte Eigenschaften bereitstellt, die den Kontext des Vorgangs beschreiben. Der `IWorkflowContext` stellt ähnliche kontextbezogene Informationen bereit, die für den ausführenden Workflow spezifisch sind, der Ihre Workflowassembly verwendet.

Verwenden Sie den folgenden Code in Ihrer `Execute`-Funktion, um auf `IWorkflowContext` zuzugreifen:

```csharp
protected override void Execute(CodeActivityContext context)
{
 IWorkflowContext workflowContext = context.GetExtension<IWorkflowContext>();

...
```

> [!IMPORTANT]
> Sie sollten keine Logikabhängigkeiten basierend auf Kontextinformationen einfügen. Wenn eine benutzerdefinierte Workflowaktivität in einem Workflow verwendet wird, sollten alle relevanten Eingabeparameter innerhalb des Designers festgelegt werden. Der Ausgabewert oder das Verhalten der benutzerdefinierten Aktivität sollte immer alleine durch die Eingabeparameter bestimmt werden, sodass es keine versteckten Faktoren gibt, die das Verhalten ändern. Wenn jemand die benutzerdefinierte Aktivität im Designer verwendet, sollte das Verhalten immer vorhersagbar sein.

### <a name="use-the-organization-service"></a>Verwenden Sie den Organisationsservice

Wenn Sie Datenvorgänge mithilfe des Organisationsdiensts ausführen müssen, können Sie darauf mithilfe der [CodeActivityContext.GetExtension\<T>](/dotnet/api/system.activities.activitycontext.getextension)-Methode mit der <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>-Schnittstelle zugreifen. Von dort aus können Sie die <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})>-Methode verwenden, um auf eine Instanz oder den Service-Proxy zuzugreifen, den Sie für die Durchführung von Datenvorgängen verwenden können. Im <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId> kann verwendet werden, um den zu verwendenden Benutzerkontext zu bestimmen, wenn Sie möchten, dass der Vorgang im selben Kontext wie der aufrufende Prozess ausgeführt wird.
Verwenden Sie den folgenden Code in Ihrer `Execute`-Funktion, um Zugriff auf den Organisationsdienst zu erhalten:

```csharp
protected override void Execute(CodeActivityContext context)
{
 IWorkflowContext workflowContext = context.GetExtension<IWorkflowContext>();
 IOrganizationServiceFactory serviceFactory = context.GetExtension<IOrganizationServiceFactory>();

 // Use the context service to create an instance of IOrganizationService.             
 IOrganizationService service = serviceFactory.CreateOrganizationService(workflowContext.InitiatingUserId);

...
```

## <a name="register-your-assembly"></a>Registrieren Ihrer Assembly

Sie verwenden das Plug-In-Registrierungstool (PRT), um Assemblys zu registrieren, die benutzerdefinierte Workflowaktivitäten enthalten. Dies ist dasselbe Tool, das Sie verwenden, um Plug-Ins zu registrieren. Sowohl bei Plug-Ins als auch bei benutzerdefinierten Workflowaktivitäten müssen Sie die Assembly registrieren, die sie in die Umgebung hochladen wird. Sie registrieren jedoch keine Schritte für benutzerdefinierte Workflowaktivitäten.

Für benutzerdefinierte Workflowaktivitäten müssen Sie die folgenden Eigenschaften angeben, um zu steuern, was im Workflowprozess-Designer angezeigt wird.

|Feld|Beschreibung|
|--|--|
|`Description`|Wird in der Benutzeroberfläche des Prozessdesigners nicht angezeigt, kann aber bei der Erstellung der Dokumentation von Daten aus der PluginType-Entität hilfreich sein, in der diese Informationen gespeichert werden.|
|`FriendlyName`|Anzeigename des Benutzers für das Plug-In.|
|`Name`|Der Name des dargestellten Menüs.|
|`WorkflowActivityGroupName`|Der Name des Untermenüs, das dem Hauptmenü im Common Data Service Prozess hinzugefügt wurde.|

![Beschreibende Eigenschaften festlegen](media/create-workflow-activity-set-properties.png)

> [!NOTE]
> Diese Werte werden in der nicht verwalteten Lösung nicht angezeigt, wenn Sie Ihre Workflowaktivität testen. Wenn Sie allerdings eine verwaltete Lösung exportieren, die diese Workflowaktivität enthält, werden diese Werte im Prozessdesigner angezeigt.

## <a name="debug-workflow-activities"></a>Workflowaktivitäten debuggen

Mit benutzerdefinierten Workflowaktivitäten, die für Common Data Service bereitgestellt sind, können Sie Profile erfassen, um sie für lokale Debugvorgänge erneut wiederzugeben und Sie können den Ablaufverfolgungsdienst verwenden, um Informationen in eine Entität zu schreiben. 

Das folgende Bespiel zeigt, wie mithilfe des Ablaufverfolgungsdiensts die folgende Nachricht geschrieben wird: `Add your message.`

```csharp
protected override void Execute(CodeActivityContext context)
{
//Create the tracing service
ITracingService tracingService = executionContext.GetExtension<ITracingService>();

//Use the tracing service
tracingService.Trace("{0} {1} {2}.","Add","your","message");

...
```

Weitere Informationen:
 - [Workflowaktivitäten debuggen](debug-workflow-activites.md)
 - [Ablaufverfolgung verwenden](../debug-plug-in.md#use-tracing)
 - [Ablaufverfolgungsprotokolle anzeigen](../tutorial-write-plug-in.md#view-trace-logs)

## <a name="add-to-solution"></a>Zur Lösung hinzufügen

Wenn Sie Assemblys mithilfe des Plug-In-Registrierungstools registrieren, werden sie der **Standardlösung** hinzugefügt, die nicht mit der **Common Data Service-Standardlösung** zu verwechseln ist. Da die **Standardlösung** alle nicht verwalteten Anpassungen enthält, die auf die Umgebung angewendet werden, bevor Sie Ihre benutzerdefinierte Workflowaktivität mithilfe einer Lösung verteilen können, müssen Sie sie einer nicht verwalteten Lösung hinzufügen. Sie könnten sie beispielsweise der **Common Data Service-Standardlösung** oder einer beliebigen nicht verwalteten Lösung hinzufügen, die Sie erstellt haben.

## <a name="manage-changes-to-custom-workflow-activities"></a>Änderungen an benutzerdefinierten Workflowaktivitäten verwalten

Sie müssen den Code für Ihre benutzerdefinierten Workflowaktivitäten verwalten. Da Codeänderungen Fehler verursachende Änderungen beinhalten können, müssen Sie diese Änderung verwalten. Sie verwenden verschiedene Schritte, um Ihre benutzerdefinierten Workflowassemblys zu aktualisieren oder ein Upgrade an ihnen auszuführen.

Wenn Sie eine Assembly registrieren, die benutzerdefinierte Workflowaktivitäten enthält, wird die Version der Assembly einbezogen. Diese Informationen werden mithilfe der Reflektion von der Assembly extrahiert. Sie können die Versionsnummer mithilfe der Datei `AssemblyInfo.cs` in Ihrem Visual Studio-Projekt steuern.

Sie finden einen Abschnitt unten, der so aussieht:


```
// Version information for an assembly consists of the following four values:
//
//      Major Version
//      Minor Version 
//      Build Number
//      Revision
//
// You can specify all the values or you can default the Build and Revision Numbers 
// by using the '*' as shown below:
//[assembly: AssemblyVersion("1.0.0.*")]
[assembly: AssemblyVersion("1.0.0.0")]
[assembly: AssemblyFileVersion("1.0.0.0")]
```

Diese Versionsinformationen sind wichtig, da sie es Ihnen ermöglichen, Updates auf bereitgestellte Assemblys anzuwenden oder Upgrade bei Assemblys auszuführen, wenn Sie neue Funktionen einschließen möchten.

### <a name="update-a-custom-workflow-activity-assembly"></a>Eine benutzerdefinierte Workflowaktivitäts-Assembly aktualisieren

Wenn Sie Änderungen vornehmen, um Bugs zu beheben oder Code umzugestalten, die zu keinen bedeutenden Änderungen bei öffentlichen Klassen oder Methodensignaturen führen, können Sie die Assembly aktualisieren, sodass alle Prozesse, die ausgeführt werden, automatisch mithilfe der neuen Version der Assembly starten.

#### <a name="to-update-an-assembly"></a>So wird eine Assembly aktualisiert:

1. Ändern Sie nur die **Buildnummer** und die **Revisionswerte** in Ihrem `AssemblyInfo.cs` `AssemblyVersion`-Attribut. Beispielsweise eine Änderung von `1.0.0.0` zu `1.0.10.5`.
1. Verwenden Sie das Plug-In-Registrierungstool, um die Assembly zu aktualisieren. Weitere Informationen: [Aktualisieren einer Assembly](../register-plug-in.md#update-an-assembly)

#### <a name="upgrade-a-custom-workflow-activity-assembly"></a>Ein Upgrade bei einer benutzerdefinierten Workflowaktivitäts-Assembly durchführen:

Wenn Sie Änderungen vornehmen, die signifikante Änderungen an öffentlichen Klassen oder Methodensignaturen umfassen, wie das Ändern der Parameter, würden Sie sämtliche aktuell ausgeführten Prozesse unterbrechen, die so definiert sind, dass sie die ursprünglichen Signaturen verwenden. In diesem Fall müssen Sie ein Upgrade an der Assembly ausführen. Dadurch wird eine neue benutzerdefinierte Workflowaktivität erstellt, die Optionen zur Verfügung stellt, die definieren, welche Version im Prozess-Designer anzuwenden ist. So kann jeder Prozess der diese Aktivität benützt, neu konfiguriert werden, um sich an die Änderungen anzupassen, die in der neuen Assembly enthalten sind. Nachdem alle Prozesse, die die ursprüngliche Assembly verwenden, aktualisiert sind, um die aktualisierte Assembly zu verwenden, können Sie die Registrierung der älteren Assembly aufheben.

#### <a name="to-upgrade-an-assembly"></a>So wird ein Upgrade an einer Assembly ausgeführt:

1. Stellen Sie sicher, dass die neue Assembly denselben/dieselbe `Name`, `PublicKeyToken` und `Culture`, wie die vorhandene Assembly hat.
1. Ändern Sie die Werte **Hauptversion** und/oder **Nebenversion** in Ihrem `AssemblyInfo.cs` `AssemblyVersion`-Attribut. Beispielsweise eine Änderung von `1.0.0.0` zu `2.0.0.0`.
1. Verwenden Sie das Plug-In-Registrierungstool, um die Assembly als neue Assembly zu "Registrieren". Weitere Informationen: [Eine Assembly registrieren](../register-plug-in.md#register-an-assembly)
1. Für jeden Prozess, der die benutzerdefinierte Workflowaktivität verwendet, müssen Sie den Prozess deaktivieren und die Schritte bearbeiten, die die benutzerdefinierte Workflowaktivität verwenden.

    Sie finden einen **Version**-Selektor im Prozess-Designer, mit dem Sie wählen können, welche Version der Assembly verwendet werden soll.

    ![für den Workflow festgelegte Version](media/workflow-set-version.png)

Wenn alle Prozesse konvertiert sind, um die neue Assembly zu verwenden, können Sie das Plug-In-Registrierungstool verwenden, um die Registrierung der Assembly aufzuheben, sodass sie nicht mehr verfügbar ist. Weitere Informationen: [Registrierung für Komponenten aufheben](../register-plug-in.md#unregister-components)

## <a name="performance-guidance"></a>Leistungs-Anweisungen

Leistungsüberlegungen für die Workflowerweiterungen stimmen mit denen wie für gewöhnliche Plug-Ins überein. Weitere Informationen: [Leistungsüberlegungen](../write-plug-in.md#performance-considerations)

Im Gegensatz zu gewöhnlichen Plug-Ins haben Sie bei Workflowerweiterungen nicht die Möglichkeit, Ihren Code explizit für einen bestimmten Schritt zu registrieren. Das bedeutet, dass Sie nicht festlegen, ob der Code in Ihrer Workflowerweiterung synchron oder asynchron ausgeführt wird. Besonders muss auf Code geachtet werden, der synchron ausgeführt wird, weil er sich direkt auf die Benutzererfahrung der Anwendung auswirkt.

Als wiederverwendbare Komponenten können Workflowerweiterungen zu beliebigen Workflows oder zu benutzerdefinierten Aktionen hinzugefügt werden. Der Workflow kann als *Echtzeit*-Workflow konfiguriert werden, wodurch die Anwendung synchron ausgeführt wird. Benutzerdefinierte Aktionen sind immer synchron, aber sie sind nicht Teil einer Transaktion, es sei denn, für sie ist **Rollback aktivieren** festgelegt.

> [!IMPORTANT]
> Wenn Ihre Workflowerweiterung in einem synchronen Workflow oder in einer benutzerdefinierte Aktion verwendet wird, wirkt sie die Zeit für das Ausführen des Code direkt auf die Benutzererfahrung aus. Daher sollten Workflowerweiterungen nicht mehr als zwei Sekunden zum Abschließen erfordern, wenn sie synchron verwendet werden. Wenn Ihre Erweiterung mehr Zeit benötigt, sollten Sie dies dokumentieren und die Verwendung der Erweiterung in synchronen Workflows oder benutzerdefinierten Aktionen nicht empfehlen.

Sie sollten sich auch bewusst sein, dass in einem synchronen Workflow oder einer benutzerdefinierten Aktion, die an der Transaktion teilnimmt, jeder Fehler, der von Ihrer Workflow-Erweiterung verursacht wird, dazu führt, dass die gesamte Transaktion zurückgesetzt wird, was eine sehr teure Operation ist, die sich auf die Performance auswirken kann.

Sie können den Wert in der Eigenschaft <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext>.<xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext.WorkflowMode> verwenden, um zu ermitteln, ob das Plug-In synchron ausgeführt wird.

## <a name="real-time-workflow-stages"></a>Echtzeit-Workflowphasen

Wenn eine Workflowerweiterung in einem Echtzeit-Workflow (synchron) verwendet wird, wird sie in den Ereignisausführungspipeline-Phasen aufgerufen, die in der folgenden Tabelle veranschaulicht werden. Weitere Informationen: [Ereignisausführungspipeline](../event-framework.md#event-execution-pipeline)

|Meldung  |Phase  |
|---------|---------|
|**Erstellen**|PostOperation|
|**Löschen**|PreOperation|
|**Update**|PreOperation oder <br /> PostOperation|

Sie können den Wert in der Eigenschaft <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext>.<xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext.StageName> verwenden, um die Phase zu ermitteln.

Für den Vorgang **Aktualisieren** ist die Phase mithilfe der Optionen **Vor** oder **Danach** im Workflow-Designer konfigurierbar. Weitere Informationen: [Echtzeitworkflows verwenden](/flow/configure-workflow-steps#using-real-time-workflows)

Wenn Ihre Workflowerweiterung von Daten abhängig ist, die an den Ausführungskontext übergeben werden, steuert die Phase, in der sie ausgeführt wird, ob die Daten hier verfügbar sind: <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext><xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> und <xref:Microsoft.Xrm.Sdk.Workflow.IWorkflowContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters>.

> [!NOTE]
> Wir empfehlen nicht, Logikabhängigkeiten basierend auf <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> und <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters> aufzunehmen. Workflowerweiterungen sollten von den konfigurierten [Ein- und Ausgabeparametern](#input-and-output-parameters) abhängen, sodass die Person, die die Workflowerweiterung verwendet, das erwartete Verhalten verstehen kann, ohne dass etwas vor ihr verborgen ist.

## <a name="entity-images-for-workflow-extensions"></a>Entitätsbilder für Workflowerweiterungen

Es gibt keine Möglichkeit, Entitätsbilder für Workflowerweiterungen zu konfigurieren, da Sie nur die Assembly registrieren und die Workflowaktivität im Kontext des Workflows ausgeführt wird. Für Workflowerweiterungen sind Entitätsbilder mithilfe der Schlüsselwerte `PreBusinessEntity` und `PostBusinessEntity` jeweils für vorherige und spätere Entitätsbilder verfügbar. Weitere Informationen: [Entitätsbilder](../understand-the-data-context.md#entity-images)


### <a name="see-also"></a>Siehe auch

[Bewährte Methoden und Anweisungen zu Workflowentwicklung Plug-In- und](../best-practices/business-logic/index.md)
[Lernprogramm: Erstellen einer Workflow-Erweiterung](tutorial-create-workflow-extension.md)<br />
[Beispiel: Eine benutzerdefinierte Workflowaktivität erstellen](sample-create-custom-workflow-activity.md)<br />
[Beispiel: Aktualisieren des nächsten Geburtstags mithilfe einer benutzerdefinierten Workflowaktivität](sample-update-next-birthday-using-custom-workflow-activity.md)<br />
[Beispiel: Berechnen Sie mit einer benutzerdefinierten Workflowaktivität einen Kreditscore](sample-calculate-credit-score-custom-workflow-activity.md)

---
title: Schrieben eines Plug-In (Common Data Service für Apps) | MicrosoftDocs
description: 'Erfahren Sie über die Konzepte und technischen Details, die für das Schreiben von Plug-Ins notwendig sind.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: brandonsimons
ms.author: jdaly
manager: ryjones
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="write-a-plug-in"></a>Schreiben eines Plug-Ins

Der Prozess des Schreibens, Registrierens und Debuggens eines Plugins ist:

1. **Erstellen Sie ein .NET-Framework-Klassenbibliotheksprojekt in Visual Studio**
1. **Fügen Sie das `Microsoft.CrmSdk.CoreAssemblies` NuGet-Paket dem Projekt hinzu**
1. **Implementieren Sie die <xref:Microsoft.Xrm.Sdk.IPlugin>-Schnittstelle in Klassen, die als Schritte registriert werden.**
1. **Fügen Sie Ihren Code der <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>-Methode hinzu, die für die Schnittstelle erforderlich ist**
    1. **Rufen Sie Referenzen auf Dienste ab, die Sie benötigen**
    1. **Fügen Sie Ihre Geschäftslogik hinzu**
1. **Signieren und erstellen Sie die Assembly**
1. Testen des Assemblys.
    1. Registrieren des Assemblys in einer Testumgebung
    1. Fügen Sie Ihre registrierten Assembly und Schritte einer nicht verwalteten Lösung hinzu
    1. Testen des Verhaltens der Assembly
    1. Überprüfen, ob erwartete Ablaufverfolgungsprotokolle geschrieben werden
    1. Debuggen der Assembly nach Bedarf

Inhalt in diesem Thema befasst sich mit dem Schritten **in fett** oben und unterstützt die folgenden Tutorials:

- [Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)
- [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)
- [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)

## <a name="assembly-constraints"></a>Assemblyeinschränkungen

Wenn Sie Assemblys erstellen, beachten Sie die folgenden Einschränkungen.

### <a name="optimize-assembly-development"></a>Optimieren der Assemblyentwicklung

Die Assembly sollte mehrere Plug-In-Klassen (oder Typen) beinhalten, aber sie kann nicht größer als 16 MB sein. Es wird empfohlen, Plug-Ins und Workflow-Assemblys in eine einzelne Assembly zu konsolidieren, solange die Größe unter 16 MB bleibt. Weitere Informationen: [Optimieren von Assemblyentwicklung](/dynamics365/customer-engagement/guidance/server/optimize-assembly-development)

### <a name="assemblies-must-be-signed"></a>Assemblys müssen signiert werden

Alle Assemblys müssen signiert sein, bevor sie registriert werden können. Das kann mithilfe der Signierungsregisterkarte von Visual Studio im Projekt erfolgen oder mithilfe von [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).

### <a name="do-not-depend-on-net-assemblies-that-interact-with-low-level-windows-apis"></a>Sind nicht von .NET-Assemblys abhängig, die mit Windows-APIs auf niedriger Ebene interagieren

Plug-In-Assemblys müssen die gesamte notwendige Logik innerhalb der jeweiligen DLL enthalten.  Plug-Ins können auf einige Kern-.Net-Assemblys verweisen. Allerdings werden Abhängigkeiten auf .Net-Assemblys nicht unterstützt, die mit Windows-APIs auf niedriger Ebene, wie der Grafikentwurfsschnittstelle, interagieren.

## <a name="iplugin-interface"></a>IPlugin-Schnittstelle

Ein Plug-In ist eine Klasse innerhalb einer Assembly, die mithilfe eines .NET Framework-Klassenbibliothekprojekts mithilfe von .NET Framework 4.5.2 in Visual Studio erstellt ist. Jede Klasse im Projekt, die als Schritt registriert wird, muss die Schnittstelle <xref:Microsoft.Xrm.Sdk.IPlugin> implementieren, die die <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>-Methode benötigt.

> [!IMPORTANT]
> Beim Implementieren von `IPlugin`, sollte die Klasse *statusfrei* sein. Dies liegt daran, dass die Plattform eine Klasseninstanz zwischenspeichert und sie aus Leistungsgründen erneut verwendet. Eine einfache Möglichkeit, sich dies vorzustellen, besteht darin, dass Sie keine Eigenschaften oder Methoden der Klasse hinzufügen sollten, und alles sollte in der `Execute`-Methode eingeschlossen sein. Es gibt einige Ausnahmen davon. Beispielsweise können Sie eine Eigenschaft haben, die eine Konstante darstellt, und Sie können Methoden haben, die Funktionen darstellen, die von der `Execute`-Methode aus aufgerufen werden. Es ist wichtig, dass Sie nie irgendeine Serviceinstanz oder Kontextdaten als Eigenschaft in Ihrer Klasse speichern. Diese ändern sich bei jedem Aufruf, und Sie möchten nicht, dass diese Daten zwischengespeichert und auf darauf folgende Aufrufe angewendet werden.  Weitere Informationen: [Entwickeln von IPlugin-Implementierungen als statusfrei](/dynamics365/customer-engagement/guidance/server/develop-iplugin-implementations-stateless)

Die <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>-Methode akzeptiert einen einzelnen <xref:System.IServiceProvider>-Parameter. Der `IServiceProvider` hat eine einzelne Methode: <xref:System.IServiceProvider.GetService*>. Sie werden diese Methode verwenden, um mehrere verschiedene Diensttypen abzurufen, die Sie in Ihrem Code verwenden können. Weitere Informationen: [Dienste, die Sie in Ihrem Code verwenden können](#services-you-can-use-in-your-code)

## <a name="pass-configuration-data-to-your-plug-in"></a>Konfigurationsdaten Ihrem Plug-In übergeben

Wenn Sie ein Plug-In registrieren, haben Sie die Möglichkeit, ihm Konfigurationsdaten zu übergeben. Konfigurationsdaten ermöglichen es Ihnen zu definieren, wie eine bestimmte Instanz eines registrierten Plug-In sich verhalten soll. Diese Informationen werden als Zeichenfolgendaten den Parametern im Konstruktor Ihrer Klasse übergeben. Es gibt zwei Parameter: `unsecure` und `secure`.
Verwenden Sie die ersten `unsecure`-Parameter für Daten, bei denen es Ihnen nichts ausmacht, wenn Benutzer sie sehen können. Verwenden Sie den zweiten `secure`-Parameter für vertrauliche Daten. 

Der folgende Code zeigt die drei möglichen Signaturen für eine Plug-In-Klasse mit Namen `SamplePlugin`.

```csharp
public SamplePlugin()  
public SamplePlugin(string unsecure)  
public SamplePlugin(string unsecure, string secure)
```
Die sicheren Konfigurationsdaten werden in einer separaten Entität gespeichert. Nur Systemadministratoren haben das Recht, sie zu lesen. Weitere Informationen: [Konfigurationsdaten festlegen](register-plug-in.md#set-configuration-data)

## <a name="services-you-can-use-in-your-code"></a>Dienste, die Sie in Ihrem Code verwenden können

Innerhalb Ihres Plug-In müssen Sie:
 
- Zugriff auf die Kontextinformationen darüber, was geschieht, wenn Ihr Plug-In zur Handhabung registriert werden sollte. Das wird als *Ausführungskontext* bezeichnet.
- Greifen Sie auf den Organisationswebdienst zu, sodass Sie Code schreiben können, um Daten abzufragen, mit Entitätsdatensätzen arbeiten können und mithilfe von Nachrichten Vorgänge ausführen können.
- Schreiben Sie Nachrichten an den Ablaufverfolgungsdienst, sodass Sie auswerten können, wie Ihr Code ausgeführt wird.

Im <xref:System.IServiceProvider>.<xref:System.IServiceProvider.GetService*> Methode stellt Ihnen eine Möglichkeit bereit, bei Bedarf auf diese Dienste zuzugreifen. Um eine Instanz des Dienstes abzurufen, rufen Sie die Methode `GetService` auf, indem Sie den Diensttyp übergeben.

> [!NOTE]
> Wenn Sie ein Plug-In schreiben, dass die Azure Service Bus-Integration verwendet, verwenden Sie einen Benachrichtigungsdienst, der die <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService>-Schnittstelle implementiert, aber dies wird hier nicht beschrieben. Weitere Informationen: [Azure-Integration](azure-integration.md)

## <a name="execution-context"></a>Ausführungskontext

Mithilfe des folgenden Codes können Sie eine Variable abrufen, die die <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext>-Schnittstelle implementiert:

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

### <a name="work-with-parametercollections"></a>Verwenden von ParameterCollections

All Eigenschaften des Ausführungskontexts sind schreibgeschützt. Aber die `InputParameters`, `OutputParameters` und `SharedVariables` sind <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Werte. Sie können die Werte der Elemente in diesen Sammlungen manipulieren, um das Verhalten des Vorgangs zu ändern, je nach Phase in der Ereignisausführungspipeline, für die Ihr Plug-In registriert ist.

Die <xref:Microsoft.Xrm.Sdk.ParameterCollection>-Werte sind als <xref:System.Collections.Generic.KeyValuePair%602>-Strukturen definiert. Um auf eine Eigenschaft zuzugreifen, müssen Sie den Namen der Eigenschaft wissen, die von der Nachricht zur Verfügung gestellt wird. Um beispielsweise auf die <xref:Microsoft.Xrm.Sdk.Entity>-Eigenschaft zuzugreifen, die als Teil der <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> übergeben wird, müssen Sie wissen, dass der Name dieser Eigenschaft `Target` ist. Dann können Sie auf diesen Wert folgendermaßen mithilfe von Code zugreifen:

```csharp
var entity = (Entity)context.InputParameters["Target"];
```
Verwenden Sie die Dokumentation <xref:Microsoft.Xrm.Sdk.Messages> und <xref:Microsoft.Crm.Sdk.Messages>, um die Namen der Nachrichten zu erfahren, die in den SDK-Assemblys definiert sind. Für benutzerdefinierte Aktionen finden Sie weitere Informationen unter den Namen der Parameter, die im System definiert sind.

### <a name="inputparameters"></a>InputParameters

Die `InputParameters` stellen den Wert der <xref:Microsoft.Xrm.Sdk.OrganizationRequest>.<xref:Microsoft.Xrm.Sdk.OrganizationRequest.Parameters>- Eigenschaft dar, die den von den Webdiensten eingehenden Vorgang darstellt.

Wie beschrieben unter [Nachrichten mit Organisationsdienst verwenden](org-service/use-messages.md), sind alle Vorgänge, die sich im System ereignen letztlich Instanzen der `OrganizationRequest`-Klasse, die von <xref:Microsoft.Xrm.Sdk.IOrganizationService>.<xref:Microsoft.Xrm.Sdk.IOrganizationService.Execute*> vverarbeitet wird Methode.

Wie im [Ereignisframework](event-framework.md) beschrieben, durchlaufen Vorgänge eine Reihe von Phasen, und Sie können Ihr Plug-In in Phasen registrieren, die auftreten, bevor die Daten in die Datenbank geschrieben werden. Innerhalb der **PreValidation**- und **PreOperation**-Phasen können Sie die Werte der `InputParameters` lesen und ändern, sodass Sie das erwartete Ergebnis des Datenenvorgangs steuern können.

Wenn Sie feststellen, dass die Werte in der `InputParameters`-Sammlung eine Bedingung darstellen, die Sie nicht zulassen können, können Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException> auslösen (vorzugsweise in der Phase **PreValidation**). Dadurch wird der Vorgang abgebrochen und dem Benutzer mit einem synchronsen Plug-In ein Fehler angezeigt, oder es wird der Fehler protokolliert, wenn das Plug-In asynchron ist. Weitere Informationen: [Abbrechen eines Vorgangs](#cancelling-an-operation)

### <a name="outputparameters"></a>OutputParameters

Die `OutputParameters` stellen den Wert der <xref:Microsoft.Xrm.Sdk.OrganizationResponse>.<xref:Microsoft.Xrm.Sdk.OrganizationResponse.Results>- Eigenschaft dar, die den Rückgabewert des Vorgangs darstellt. Die `OutputParameters` werden nicht vor der Datenbanktransaktion aufgefüllt. Somit sind sie erst für Plug-Ins verfügbar, die in der **PostOperation**-Phase registriert werden. Wenn Sie die Werte ändern möchten, die von dem Vorgang zurückgegeben wurden, können Sie sie in den `OutputParameters` ändern.

### <a name="shared-variables"></a>Freigegebene Variablen

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


### <a name="entity-images"></a>Entitätsbilder

Wenn Sie einen Schritt für ein Plug-In registrieren, das eine Entität vom Datenmigrations-Assistenten als einen der Parameter enthält, haben Sie die Möglichkeit anzugeben, ob eine Kopie der Entitätsdaten als *Momentaufnahme* oder Bild mit der <xref:Microsoft.Xrm.Sdk.IExecutionContext.PreEntityImages> und/oder <xref:Microsoft.Xrm.Sdk.IExecutionContext.PostEntityImages> Eigenschaft ist.

Diese Daten stellen einen Vergleichspunkt für Entitätsdaten zur Verfügung, während sie durch die Ereignispipeline durchfließt. Mithilfe dieser Bilder kann eine bessere Leistung bereitgestellt werden, anstelle Code in einen Plug-In einzubeziehen, um eine Entität abzurufen, nur um die Attributwerte zu vergleichen.

Wenn Sie ein Entitätsbild definieren, geben Sie einen Entitätsaliaswert an, die Sie verwenden können, um auf das gewünschte Bild zuzugreifen. Wenn Sie zum Beispiel ein Vorentitätsbild definieren mit dem Alias "`a`", können Sie den folgenden Code verwenden, um auf den Attributwert `name` zuzugreifen.

```csharp
var oldAccountName = (string)context.PreEntityImages["a"]["name"];
```

Weitere Informationen: [Entitätsbilder definieren](register-plug-in.md#define-entity-images)

## <a name="organization-service"></a>Organisationsdienst

Um mit Daten innerhalb eines Plug-Ins zu arbeiten, verwenden Sie den Organisationsdienst. Versuchen Sie nicht, die Web-API zu verwenden. Plug-Ins werden für die Verwendung der .NET-SDK-Assemblys optimiert.

Um Zugriff auf eine `svc`-Variable zu erhalten, die die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Schnittstelle implementiert, verwenden Sie den folgenden Code:


```csharp
// Obtain the organization service reference which you will need for  
// web service calls.  
IOrganizationServiceFactory serviceFactory =
    (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
IOrganizationService svc = serviceFactory.CreateOrganizationService(context.UserId);
```
Die Variable `context.UserId`, die mit <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>-<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> verwendet wird kommt aus dem Ausführungskontext der <xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId>-Eigenschaft. Somit erfolgt dieser Aufruf, nachdem auf den Ausführungskontext zugegriffen wurde.

Weitere Informationen:
 - [Entitätsvorgänge](org-service/entity-operations.md)
 - [Daten abfragen](org-service/entity-operations-query-data.md)
 - [Entitäten erstellen](org-service/entity-operations-create.md)
 - [Eine Entität abrufen](org-service/entity-operations-retrieve.md)
 - [Entitäten aktualisieren und löschen](org-service/entity-operations-update-delete.md)
 - [Entitäten zuordnen und ihre Zuordnung aufheben](org-service/entity-operations-associate-disassociate.md)
 - [Nachrichten verwenden](org-service/use-messages.md)
 - [Spät gebundene und früh gebundene Programmierung](org-service/early-bound-programming.md)

Sie können Typen mit früher Bindung innerhalb eines Plug-Ins verwenden. Fügen Sie einfach die Datei mit generierten Typen in Ihr Projekt ein. Aber Sie sollten beachten, dass sämtliche Entitätstypen, die von den Ausführungskontext-Eingabeparametern bereitgestellt werden, spät gebundene Typen sind. Sie müssen sie in Typen mit früher Bindung konvertieren. Beispielsweise können Sie die folgenden Schritte ausführen, wenn Sie wissen, dass der Parameter `Target` eine Kontoentität darstellt.

```csharp
Account acct = context.InputParameters["Target"].ToEntity<Account>();
``` 
Aber Sie sollten nie versuchen, den Wert mithilfe eines Typs mit früher Bindung festzulegen. Versuchen Sie dies nicht:

```csharp
context.InputParameters["Target"] = new Account() { Name = "MyAccount" }; // WRONG: Do not do this. 
```
Infolge dessen tritt eine <xref:System.Runtime.Serialization.SerializationException> auf.

## <a name="impersonation"></a>Identitätswechsel

Manchmal ist es notwendig, dass der Code in einem Plug-In im Kontext eines anderen Benutzers ausgeführt wird.

Es gibt zwei Möglichkeiten, Identitätswechsel in Plug-Ins anzuwenden: Bei der Registrierung oder der Ausführung.

### <a name="at-plug-in-registration"></a>Bei der Plug-In-Registrierung

Wenn Sie einen Plug-In-Schritt registrieren, können Sie ein Benutzerkonto angeben, das benutzt werden soll, wenn der Code ausgeführt wird, indem Sie von der Option **Im Kontext des Benutzers ausführen** auswählen. Standardmäßig ist diese auf die Nutzung von **Aufrufender Benutzer** festgelegt. Das ist das Benutzerkonto, durch das die Aktion initiiert wurde. Wenn diese Standardoption angewendet ist, wird die [SdkMessageProcessingStep.ImpersonatingUserId](reference/entities/sdkmessageprocessingstep.md#BKMK_ImpersonatingUserId) auf null oder <xref:System.Guid.Empty> festgelegt.

Weitere Informationen: [Plug-In-Schritt registrieren](register-plug-in.md#register-plug-in-step).

### <a name="during-plug-in-execution"></a>Während der Plug-In-Ausführung

Sie können die Einstellung überschrieben, die bei der Registrierung zur Laufzeit angegeben wurde, nämlich durch Festlegen vom <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>.<xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory.CreateOrganizationService(System.Nullable{System.Guid})> `userId`-Parameter.

Dies wird in der Regel festgelegt auf den <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.UserId> -Werte, wodurch das Benutzerkonto angewendet wird, das durch die Plug-In-Schrittregistrierung definiert wurde.

```csharp
(IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    IOrganizationService service = serviceFactory.CreateOrganizationService(context.UserId);
```

Wenn Sie die Schrittregistrierung überschreiben möchten, können Sie den Wert übergeben von <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.InitiatingUserId> um einen Service zu haben, bei dem das Benutzerkonto verwendet wird, durch das die Aktion initiiert wurde, die die Ausführung des Plug-Ins verursacht hat.

Sie können auch die [SystemUser.SystemUserId](reference/entities/systemuser.md#BKMK_SystemUserId) von einem gültigen Benutzerkonto bereitstellen. Dies funktioniert, solange dieser Benutzer über die erforderlichen Berechtigungen verfügt, um die Vorgänge im Plug-In auszuführen.

## <a name="use-the-tracing-service"></a>Den Ablaufverfolgungsdienst verwenden

Verwenden Sie den Ablaufverfolgungsdienst, um Nachrichten an die [PluginTraceLog-Entität](reference/entities/plugintracelog.md) zu schreiben, sodass Sie die Protokolle überprüfen können, um zu verstehen, was sich ereignet hatte, als das Plug-In ausgeführt wurde.

Um an das traceLog zu schreiben, müssen Sie eine Instanz des Ablaufverfolgungsdiensts abrufen. Der folgende Code veranschaulicht, wie das Abrufen einer Instanz des Ablaufverfolgungsdiensts möglich ist, mithilfe der <xref:System.IServiceProvider>.<xref:System.IServiceProvider.GetService*> Methode.


```csharp
// Obtain the tracing service
ITracingService tracingService =
(ITracingService)serviceProvider.GetService(typeof(ITracingService));
```

Um die Ablaufverfolgung zu schreiben, verwenden Sie die <xref:Microsoft.Xrm.Sdk.ITracingService>.<xref:Microsoft.Xrm.Sdk.ITracingService.Trace*> Methode.

```csharp
tracingService.Trace("Write {0} {1}.", "your", "message");
```

Weitere Informationen: [Verwenden der Ablaufverfolgung](debug-plug-in.md#use-tracing).



## <a name="cancelling-an-operation"></a>Abbrechen eines Vorgangs

Ihr Code kann bewirken, dass ein Vorgang abgebrochen wird, indem eine Ausnahme ausgelöst wird. Jede nicht gehandhabte Ausnahme bewirkt, dass der Vorgang abgebrochen wird. Es ist daher wichtig, dass Sie Codierungspraktiken anwenden, um Ausnahmen zu handhaben, die ausgelöst werden und entscheiden, ob dadurch der Vorgang abgebrochen werden soll oder nicht.

Wenn Ihre Geschäftslogik vorschreibt, dass der Vorgang abgebrochen werden soll, sollten Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>-Ausnahme auslösen und eine Nachricht bereitstellen, um zu erklären, warum der Vorgang abgebrochen wurde.

Wenn Sie eine <xref:Microsoft.Xrm.Sdk.InvalidPluginExecutionException>-Ausnahme innerhalb eines synchronen Plug-In auslösen, wird dem Benutzer ein Fehlerdialog mit Ihrer Nachricht angezeigt. Wenn Sie keine Meldung bereitstellen, wird dem Benutzer ein generischer Fehlerdialog angezeigt. Wenn irgendein anderer Ausnahmetyp ausgelöst wird, wird der Benutzer einen Fehlerdialog mit einer generischen Nachricht sehen, und die Ausnahmemeldung sowie Stapelüberwachung werden in die [PluginTraceLog-Entität](reference/entities/plugintracelog.md) geschrieben

Idealerweise sollten Sie nur Vorgänge mithilfe synchroner Plug-Ins abbrechen, die in der Phase **PreValidation** registriert wurden. Diese Phase erfolgt *gewöhnlich* außerhalb der Hauptdatenbanktransaktion. Das Abbrechen eines Vorgangs, bevor er die Transaktion erreicht, ist hoch erwünscht, da der abgebrochene Vorgang zurückgesetzt werden muss. Der Rollback des Vorgangs erfordert beträchtliche Ressourcen und wirkt sich auf die Systemleistung aus. Vorgänge in den Phasen **PreOperation** und **PostOperation** befinden sich immer innerhalb der Datenbanktransaktion.

Manchmal sind **PreValidation**-Phasen innerhalb einer Transaktion, wenn sie von Logik in einem anderen Vorgang initiiert sind. Wenn Sie beispielsweise einen Aufgabenentitätsdatensatz in der Phase **PreOperation** der Erstellung einer Firma erstellen, wird die Aufgabenerstellung durch die Ereignisausführungspipeline übergeben und wird innerhalb der Phase **PreValidation** erfolgen. Sie wird aber ein Bestandteil der Transaktion sein, durch den der Firmaenentitätsdatensatz erstellt wird. -Sie können feststellen, ob sich ein Vorgang innerhalb einer Transaktion befindet anhand des Werts der <xref:Microsoft.Xrm.Sdk.IExecutionContext>.<xref:Microsoft.Xrm.Sdk.IExecutionContext.IsInTransaction> -Eigenschaft verfügbar.

## <a name="performance-considerations"></a>Leistungsüberlegungen

Wenn Sie die Geschäftslogik für Ihr Plug-In hinzufügen, müssen Sie sich der Auswirkungen sehr bewusst sein, die sie auf die Gesamtleistung haben. Der Abschluss der Geschäftslogik in Plug-Ins sollte nicht mehr als 2 Sekunden dauern.

### <a name="time-and-resource-constraints"></a>Zeit- und Ressourcenbeschränkungen

Es gibt eine 2-Minuten-Zeitbegrenzung für den Abschluss von Nachrichtenvorgängen. Es gibt auch Beschränkungen hinsichtlich des Umfangs von CPU und Speicherressoucen, die von Erweiterungen verwendet werden können. Wenn die Beschränkungen überschritten werden, wird eine Ausnahme ausgelöst und der Vorgang wird abgebrochen.

Wenn das Zeitlimit überschritten wird, wird eine <xref:System.TimeoutException> ausgegeben. Wenn irgendeine benutzerdefinierte Erweiterung die Schwelle bei CPU-, Speicher- oder Handhabungsbeschränkungen überschreitet oder auf eine andere Weise nicht reagiert, beendet die Plattform den jeweiligen Prozess. An diesem Punkt wird jede beliebige aktuelle Erweiterung in diesem Prozess mit Ausnahmen fehlschlagen. Wenn jedoch die Erweiterung das nächste Mal ausgeführt wird, wird sie normal ausgeführt.

### <a name="monitor-performance"></a>Leistung überwachen

Laufzeitinformationen zu Plug-Ins und benutzerdefinierten Workflowerweiterungen werden erfasst und in der [PluginTypeStatistic-Entität](reference/entities/plugintypestatistic.md) gespeichert. Diese Datensätze werden innerhalb von 30 Minuten oder einer Stunde nach der Ausführung des benutzerdefinierten Codes aufgefüllt. Diese Entität stellt die folgenden Datenpunkte bereit:

|**Attribut**|**Beschreibung**|
|--|--|
|AverageExecuteTimeInMilliseconds|Die durchschnittliche Ausführungszeit für den Plug-In-Typ (in Millisekunden). |
|CrashContributionPercent|Anteil des Plug-In-Typs an Abstürzen (Prozentsatz). |
|CrashCount|Anzahl der Abstürze des Plug-In-Typs. |
|CrashPercent|Prozentsatz der Abstürze für den Plug-In-Typ. |
|ExecuteCount|Anzahl der Ausführungen des Plug-In-Typs. |
|FailureCount |Anzahl der Fehler beim Plug-In-Typ. |
|FailurePercent|Prozentsatz der Fehler für den Plug-In-Typ. |
|PluginTypeIdName|Eindeutiger Bezeichner des Benutzers, der die Plug-In-Typ-Statistik zuletzt geändert hat. |
|TerminateCpuContributionPercent |Der Beitrag des Plug-In-Typs an der Beendigung des Arbeitsprozesses aufgrund übermäßiger CPU-Nutzung in Prozent. |
|TerminateHandlesContributionPercent |Der Beitrag des Plug-In-Typs an der Beendigung des Arbeitsprozesses aufgrund übermäßiger Handlenutzung in Prozent. |
|TerminateMemoryContributionPercent|Der Beitrag des Plug-In-Typs an der Beendigung des Arbeitsprozesses aufgrund übermäßiger Arbeitsspeichernutzung in Prozent. |
|TerminateOtherContributionPercent|Der Beitrag des Plug-In-Typs an der Beendigung des Arbeitsprozesses aus unbekannten Gründen in Prozent. |

Diese Daten sind ebenfalls verfügbar, damit Sie sie mithilfe des [Organisationsinformationen-Plug-In-Dashboard](/dynamics365/customer-engagement/admin/use-organization-insights-solution-view-instance-metrics#plug-ins) neben vielen anderen nützlichen Berichten durchsuchen können.


## <a name="next-steps"></a>Nächste Schritte

[Registrieren eines Plug-Ins](register-plug-in.md)<br />
[Debuggen von Plug-Ins](debug-plug-in.md)

### <a name="see-also"></a>Siehe auch

[Schreiben von Plug-Ins, um Geschäftsprozesse zu erweitern](plug-ins.md)<br />
[Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)<br />
[Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)<br />
[Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)<br />

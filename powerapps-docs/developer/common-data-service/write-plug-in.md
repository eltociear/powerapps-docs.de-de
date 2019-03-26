---
title: Schrieben eines Plug-In (Common Data Service für Apps) | MicrosoftDocs
description: 'Erfahren Sie über die Konzepte und technischen Details, die für das Schreiben von Plug-Ins notwendig sind.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
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

Ein Plug-In ist eine Klasse innerhalb einer Assembly, die mithilfe eines .NET Framework-Klassenbibliothekprojekts mithilfe von .NET Framework 4.6.2 in Visual Studio erstellt ist. Jede Klasse im Projekt, die als Schritt registriert wird, muss die Schnittstelle <xref:Microsoft.Xrm.Sdk.IPlugin> implementieren, die die <xref:Microsoft.Xrm.Sdk.IPlugin.Execute*>-Methode benötigt.

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

Weitere Informationen finden Sie unter: [Tracing verwenden](debug-plug-in.md#use-tracing), [Protokollierung und Verfolgung](logging-tracing.md)

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
[Bewährte Methoden und Anweisungen zu Workflowentwicklung Plug-In- und](best-practices/business-logic/index.md)
[Ausnahmenbehandlung](handle-exceptions.md)<br />
[Die Identität eines Benutzers annehmen](impersonate-a-user.md)<br />
[Lernprogramm: Schreiben und Registrieren eines Plugins](tutorial-write-plug-in.md)<br />
[Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)<br />
[Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)<br />

---
title: 'Lernprogramm: Schreiben und Registrieren eines Plug-Ins (Common Data Service) | MicrosoftDocs'
description: 'Dieses Lernprogramm ist das erste in der Serie, in der Ihnen gezeigt wird, wie Sie mit Plug-Ins arbeiten.'
ms.custom: ''
ms.date: 02/23/2019
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
# <a name="tutorial-write-and-register-a-plug-in"></a>Lernprogramm: Schreiben und Registrieren eines Plugins

Dieses Lernprogramm ist das erste in der Serie, das Ihnen zeigt, wie Sie mit Plug-Ins arbeiten. Dieses Lernprogramm ist eine Voraussetzung für die folgenden Lernprogramme:

- [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md)
- [Lernprogramm: Aktualisieren eines Plug-Ins](tutorial-update-plug-in.md)

Eine detaillierte Erläuterung der unterstützenden Konzepte und technischen Details finden Sie unter:

- [Verwenden von Plug-Ins zur Erweiterung von Geschäftsprozessen](plug-ins.md)
- [Schreiben eines Plug-Ins](write-plug-in.md)
- [Registrieren eines Plug-Ins](register-plug-in.md)
- [Debuggen von Plug-Ins](debug-plug-in.md)

## <a name="goal"></a>Ziel

Erstellen Sie ein asynchrones Plug-In, das in der Erstellungsmeldung der Firmenentität registriert ist. Das Plug-In erstellt eine Aufgabenaktivität, die den Ersteller der Firma erinnert, eine Woche später eine Nachverfolgung durchzuführen.

> [!NOTE]
> Das Ziel kann mithilfe eines Workflows einfach erreicht werden, ohne Code zu schreiben. Wir verwenden dieses einfache Beispiel, damit wir uns auf den Vorgang der Erstellung und Bereitstellung eines Plug-Ins konzentrieren können.

## <a name="prerequisites"></a>Voraussetzungen

- Zugriff auf Administratorebene auf eine Common Data Service-Umgebung
- Eine modellgesteuerte App, die die Firmen- und Aufgabenentitäten einschließt.
    - Wenn Sie über keine modellgesteuerte App verfügen, die diese enthält, finden Sie Schritte zum [neuen Erstellen Ihrer ersten modellgesteuerten App](../../maker/model-driven-apps/build-first-model-driven-app.md) in nur wenigen Minuten.
- Visual Studio 2017
- Kenntnisse der Programmiersprache Visual C#
- Laden Sie das das Plug-in-Registrierungstool herunter.
    - Informationen zum Herunterladen des Plug-In-Registrierungstools erhalten Sie unter [Tools von NuGet herunterladen](download-tools-nuget.md). Dieses Thema enthält Anweisungen zur Verwendung eines PowerShell-Skripts, um die aktuellen Tools von NuGet herunterzuladen.

## <a name="create-a-plug-in-project"></a>Plug-In-Projekt erstellen

Sie müssen ein Plug-In in Visual Studio schreiben. Führen Sie diese Schritte aus, um ein grundlegendes Plug-In zu schreiben. Alternativ finden Sie hier die kompletten Plug-in-Lösungsdateien: [Beispiel: Erstellen Sie ein Basis-Plugin](org-service/samples/basic-followup-plugin.md).

### <a name="create-a-visual-studio-project-for-the-plug-in"></a>Ein Visual Studio-Projekt für das Plug-In erstellen

1. Öffnen Sie Visual Studio 2017 und öffnen Sie ein neues **Klassenbibliothek (.NET Framework)**-Projekt mit **.NET Framework 4.6.2**

    ![öffnen Sie eine neuen Klassenbibliothek (.NET Framework)-Projekt mit .NET Framework 4.6.2](media/tutorial-write-plug-in-create-visual-studio-project.png)

    Der Name, der für das Projekt verwendet wird, ist der Name der Assemblys. Dieses Lernprogramm verwendetet den Namen `BasicPlugin`.
1. Klicken Sie im **Lösungsexplorer** mit der rechten Maustaste in das Projekt und wählen Sie **NuGet Pakete verwalten...** aus dem Kontextmenü aus.

    ![NuGet-Package verwalten](media/tutorial-write-plug-in-manage-nuget-packages.png)

1. Wählen Sie **Durchsuchen** aus und suchen Sie nach `Microsoft.CrmSdk.CoreAssemblies` und installieren Sie die aktuelle Version.

    ![Installieren Sie das Microsoft.CrmSdk.CoreAssemblies NuGet-Paket](media/tutorial-write-plug-in-install-microsoft.crmsdk.coreassemblies.png)

1. Sie müssen **Ich stimme zu** im Dialogfeld **Lizenz-Abnahme** auswählen.
1. Klicken Sie im **Lösungsexplorer** mit der rechten Maustaste auf die Datei `Class1.cs` und wählen Sie im Kontextmenü **Umbenennen** aus.

    ![Klasse umbenennen](media/tutorial-write-plug-in-rename-class.png)

1. Benennen Sie die Datei `Class1.cs` in `FollowupPlugin.cs` um.
1. Wenn Sie dazu aufgefordert werden, erlauben Sie Visual Studio, die Klasse umzubenennen, damit der Dateiname übereinstimmt.

    ![Dialog "Umbenennung bestätigen"](media/tutorial-write-plug-in-rename-class-confirm.png)

### <a name="edit-the-class-file-to-enable-a-plug-in"></a>Die Klassendatei bearbeiten, um ein Plug-In zu aktivieren

1. Fügen Sie die folgenden `using`-Ausdrücke am Anfang der `FollowupPlugin.cs`-Datei hinzu:

    ```csharp
    using System.ServiceModel;  
    using Microsoft.Xrm.Sdk;
    ```

1. Implementieren Sie die <xref:Microsoft.Xrm.Sdk.IPlugin>-Schnittstelle, indem Sie die Klasse bearbeiten.

    > [!NOTE]
    > Wenn Sie nach dem Klassennamen nur `: IPlugin` eingeben, schlägt Visual Studio automatisch die Implementierung einer Kurzversion für die **Ausführen**-Methode vor.

    ```csharp
    public class FollowupPlugin : IPlugin
    {
        public void Execute(IServiceProvider serviceProvider)
        {
            throw new NotImplementedException();
        }
    }
    ```


1. Ersetzen Sie die Inhalte der `Execute`-Methode durch den folgenden Code:


```csharp
// Obtain the tracing service
ITracingService tracingService =
(ITracingService)serviceProvider.GetService(typeof(ITracingService));

// Obtain the execution context from the service provider.  
IPluginExecutionContext context = (IPluginExecutionContext)
    serviceProvider.GetService(typeof(IPluginExecutionContext));

// The InputParameters collection contains all the data passed in the message request.  
if (context.InputParameters.Contains("Target") &&
    context.InputParameters["Target"] is Entity)
{
    // Obtain the target entity from the input parameters.  
    Entity entity = (Entity)context.InputParameters["Target"];

    // Obtain the organization service reference which you will need for  
    // web service calls.  
    IOrganizationServiceFactory serviceFactory =
        (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
    IOrganizationService service = serviceFactory.CreateOrganizationService(context.UserId);

    try
    {
        // Plug-in business logic goes here.  
    }

    catch (FaultException<OrganizationServiceFault> ex)
    {
        throw new InvalidPluginExecutionException("An error occurred in FollowUpPlugin.", ex);
    }

    catch (Exception ex)
    {
        tracingService.Trace("FollowUpPlugin: {0}", ex.ToString());
        throw;
    }
}
```

### <a name="about-the-code"></a>Infos zum Code

- <xref:Microsoft.Xrm.Sdk.ITracingService> ermöglicht das Schreiben in das Ablaufverfolgungsprotokoll.  Sie können ein Beispiel im letzten catch-Block sehen. Weitere Informationen: [Verwenden der Ablaufverfolgung](debug-plug-in.md#use-tracing)
- <xref:Microsoft.Xrm.Sdk.IPluginExecutionContext> bietet Zugriff auf den Kontext für das Ereignis, das das Plug-In ausgeführt hat.  Mehr Informationen: [Verstehen Sie den Kontext der Ausführung](understand-the-data-context.md).
- Der Code überprüft, dass der Kontext <xref:Microsoft.Xrm.Sdk.IExecutionContext.InputParameters> die erwarteten Parameter für <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest> enthält, für das dieses Plug-In registriert ist. Wenn die <xref:Microsoft.Xrm.Sdk.Messages.CreateRequest.Target>-Eigenschaft vorhanden ist, ist <xref:Microsoft.Xrm.Sdk.Entity>, das der Anforderung übergeben wurde, verfügbar.
- Die <xref:Microsoft.Xrm.Sdk.IOrganizationServiceFactory>-Schnittstelle bietet Zugriff auf eine Servicevariable, die die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Benutzeroberfläche implementiert, die die Methoden bereitstellt, die Sie verwenden, um mit dem Service zu interagieren, um die Aufgabe zu erstellen.


## <a name="add-business-logic"></a>Geschäftslogik hinzufügen

Das Plug-In erstellt eine Aufgabenaktivität, die den Ersteller der Firma erinnert, eine Woche später eine Nachverfolgung durchzuführen.

Fügen Sie folgenden Code dem try-Block hinzu. Ersetzen Sie den Kommentar: `// Plug-in business logic goes here`. durch Folgendes:


```csharp
// Create a task activity to follow up with the account customer in 7 days. 
Entity followup = new Entity("task");

followup["subject"] = "Send e-mail to the new customer.";
followup["description"] =
    "Follow up with the customer. Check if there are any new issues that need resolution.";
followup["scheduledstart"] = DateTime.Now.AddDays(7);
followup["scheduledend"] = DateTime.Now.AddDays(7);
followup["category"] = context.PrimaryEntityName;

// Refer to the account in the task activity.
if (context.OutputParameters.Contains("id"))
{
    Guid regardingobjectid = new Guid(context.OutputParameters["id"].ToString());
    string regardingobjectidType = "account";

    followup["regardingobjectid"] =
    new EntityReference(regardingobjectidType, regardingobjectid);
}

// Create the task in Microsoft Dynamics CRM.
tracingService.Trace("FollowupPlugin: Creating the task activity.");
service.Create(followup);
```

### <a name="about-the-code"></a>Infos zum Code

- Dieser Code verwendet den Stil mit später Bindung, um eine Aufgabe zu erstellen und diese der Firma zuzuordnen, die erstellt wird. Weitere Informationen: [Erstellen von Entitäten mit dem Organisationsdienst](org-service/entity-operations-create.md).
- Klassen mit früher Bindung können verwendet werden. Dafür ist aber die Generierung der Klassen für die Entitäten und das Einschließen der Datei erforderlich, die diese Klassen für das Assembly-Projekt definiert. Dies ist größtenteils eine persönliche Vorliebe, daher wurden diese Schritte zugunsten der Kürze aus diesem Lernprogramm weg gelassen. Weitere Informationen: [Programmierung mit später und früher Bindung mithilfe des Organisationsservices](org-service/early-bound-programming.md)
- <xref:Microsoft.Xrm.Sdk.Entity.Id> der Firma, die erstellt wird, wird im Kontext <xref:Microsoft.Xrm.Sdk.IExecutionContext.OutputParameters> gefunden und als das Suchattribut `regardingobjectid` für die Aufgabe festgelegt.

## <a name="build-plug-in"></a>Plug-In erstellen

In Visual Studio drücken Sie **F6**, um die Assembly zu erstellen. Überprüfen Sie, dass die Kompilierung fehlerfrei erfolgt.

## <a name="sign-plug-in"></a>Plug-In-signieren

1. Klicken Sie im **Lösungsexplorer** mit der rechten Maustaste auf das **BasicPlugin**-Plug-In, und wählen Sie im Kontextmenü **Eigenschaften** aus.

    ![Projekteigenschaften öffnen](media/tutorial-write-plug-in-project-properties.png)

1. Wählen Sie in den Projekteigenschaften die Registerkarte **Signierung** aus, und aktivieren Sie das Kontrollkästchen **Assembly signieren**.

    ![Die Assembly signieren](media/tutorial-write-plug-in-sign-assembly.png)

1. Im Dropdown **Eine Schlüsseldatei mit starkem Namen auswählen**: wählen Sie **<Neu…>** aus. 
1. Geben Sie im Dialogfeld **Schlüssel mit starkem Namen erstellen** einen **Schlüsseldateinamen** ein, und deaktivieren Sie das Kontrollkästchen **Meine Schlüsseldatei mit einem Kennwort schützen**.
1. Klicken Sie auf **OK**, um das Dialogfeld **Schlüssel mit starkem Namen erstellen** zu schließen.
1. Überprüfen Sie in der Registerkarte **Build** der Projekteigenschaften, dass die **Konfiguration** auf **Debuggen** festgelegt ist.
1. Drücken Sie **F6**, um das Plug-In erneut zu erstellen.
1. Verwenden Sie den Windows-Explorer, um unter ` \bin\Debug\BasicPlugin.dll` nach dem erstellten Plug-In zu suchen.

> [!NOTE]
> Erstellen Sie die Assembly mit der Konfiguration **Debuggen**, weil Sie den Plug-In-Profiler verwenden, um es in einem späteren Lernprogramm zu debuggen.   Bevor Sie ein Plug-In mit Ihrer Lösung einschließen, sollten Sie es mit der Versionskonfiguration erstellen.

## <a name="register-plug-in"></a>Plug-In registrieren

Zum Registrieren eines Plug-Ins benötigen Sie das Plug-In-Registrierungstool

[!INCLUDE [cc-connect-plugin-registration-tool](includes/cc-connect-plugin-registration-tool.md)]

### <a name="register-your-assembly"></a>Registrieren Ihrer Assembly

1. Wählen Sie im Dropdown **Registrieren** die Option **Neue Assembly** aus.

    ![Neue Assembly registrieren](media/tutorial-write-plug-in-register-new-assembly.png)

1. Wählen Sie im Dialogfeld **Neue Assembly registrieren** die Auslassungspunkte (**…**) aus, und navigieren Sie zur Assembly, die Sie im vorherigen Schritt erstellt haben.

    ![Dialog "Neue Assembly registrieren"](media/tutorial-write-plug-in-register-new-assembly-dialog.png)

1. Vergewissern Sie sich für Office 365-Benutzer, dass der **Isolationsmodus** **Sandbox** und der **Speicherort** für die Assembly **Datenbank** ist.

    > [!NOTE]
    > Weitere Optionen für **Isolationsmodus** und **Speicherort** gelten für lokale Dynamics 365-Bereitstellungen. Als Standort können Sie die Datenbank des D365-Servers, den lokalen Speicher (Festplatte) des Servers oder den Cache für die globale Assembly des Servers angeben. Weitere Informationen finden Sie unter [Plug-in-Speicher](/dynamics365/customer-engagement/developer/register-deploy-plugins#plug-in-storage).

1. Klicken Sie auf **Ausgewählte Plug-ins registrieren**.
1. Sie sehen ein **Registrierte Plug-Ins** Bestätigungsdialogfeld.

    ![Bestätigungsdialogfeld für registriertes Plug-In](media/tutorial-write-plug-in-register-new-assembly-dialog-confirm.png)

1. Klicken Sie auf **OK**, um das Dialogfeld zu schließen, und schließen Sie den Dialog **Neue Assembly registrieren**. 
1. Die Assembly **(Assembly) BasicPlugin** sollte nun angezeigt werden, die Sie erweitern können, um das **(Plug-In) BasicPlugin.FollowUpPlugin**-Plug-In anzuzeigen.

    ![(Plug-In) BasicPlugin.FollowUpPlugin-Plug-In.](media/tutorial-write-plug-in-basic-followupplugin-plugin.png)


### <a name="register-a-new-step"></a>Einen neuen Schritt registrieren

1. Klicken Sie mit der rechten Maustaste auf **(Plug-In) BasicPlugin.FollowUpPlugin**, und wählen Sie **Neuen Schritt registrieren** aus.

    ![Einen neuen Schritt registrieren](media/tutorial-write-plug-in-register-new-step.png)

1. Legen Sie im Dialogfeld **Neuen Schritt registrieren** die folgenden Felder fest:

    |Einstellung|Value|
    |--|--|
    |Meldung|Erstellen|
    |Primäre Entität|account|
    |Ereignis-Pipeline-Phase der Ausführung|PostOperation|
    |Ausführungsmodus|Asynchron|

    ![Einen neuen Schritt registrieren](media/tutorial-write-plug-in-register-new-step-dialog.png)

1. Klicken Sie auf **Neuen Schritt registrieren**, um die Registrierung abzuschließen, und schließen Sie das Dialogfeld **Neuen Schritt registrieren**.
1. Sie können den registrierten Schritt jetzt sehen.

    ![Der registrierten Schritt anzeigen](media/tutorial-write-plug-in-view-registered-step.png)

> [!NOTE]
> Zu diesem Zeitpunkt sind die Assembly und die Schritte Teil des Systems **Standardlösung**. Dies ist ein guter Zeitpunkt, um sie der nicht verwalteten Lösung hinzuzufügen, die Sie verteilen werden. Diese Schritte sind in diesem Lernprogramm nicht enthalten. Weitere Informationen finden Sie unter [Hinzufügen Ihrer Assembly zu einer Lösung](register-plug-in.md#add-your-assembly-to-a-solution) und [Hinzufügen eines Schritts zu einer Lösung ](register-plug-in.md#add-step-to-solution).

## <a name="test-plug-in"></a>Plug-In testen

1. Öffnen Sie eine modellgesteuerte App und erstellen Sie eine Firmenentität.
1. Innerhalb kurzer Zeit öffnen Sie die Firma und Sie können die Erstellung der Aufgabe überprüfen.

    ![Durch Plug-In erstellter Firmenentitätsdatensatz mit verwandter Aufgabenaktivität](media/tutorial-write-plug-in-test-plugin-in-model-app.png)

### <a name="what-if-the-task-wasnt-created"></a>Was, wenn die Aufgabe nicht erstellt wurde?

Da es sich um ein asynchrones Plug-In handelt, wird der Vorgang zur Erstellung der Aufgabe nach dem Erstellen der Firma durchgeführt. Normalerweise geschieht dies sofort, aber, falls nicht, können Sie den Systemauftrag weiterhin in der Warteschlange anzeigen, wo er auf die Anwendung wartet. Diese Schrittregistrierung verwendete die **AsyncOperation löschen, wenn StatusCode = Erfolgreich**-Option, was eine bewährten Methode ist. Das bedeutet, sobald der Systemauftrag erfolgreich abgeschlossen wird, können Sie die Systemauftragsdaten nicht anzeigen, es sei denn, Sie registrieren das Plug-In mit aufgehobener Auswahl der Option **AsyncOperation löschen, wenn StatusCode = erfolgreich** erneut.

Falls jedoch ein Fehler aufgetreten ist, können Sie den Systemauftrag anzeigen, um die Fehlermeldung anzuzeigen.

## <a name="view-system-jobs"></a>Anzeigen von Systemaufträgen

Verwenden Sie die angepasste **Dynamics 365**-App, um Systemaufträge anzuzeigen.

1. In der modellgesteuerten App navigieren Sie zur 

    ![Ansicht der angepassten Dynamics 365-App](media/dynamics-365-custom-app.png)

1. In der angepassten**Dynamics 365**-App navigieren Sie zu **Einstellungen** > **System** > **Systemaufträge**.

    ![navigieren zu Systemaufträgen](media/navigate-system-jobs.png)

1. Wenn Sie Systemaufträge anzeigen, können Sie nach **Entität** filtern. Wählen Sie **Firma** aus.

    ![foo](media/system-jobs-filter-entity-account.png)

1. Wenn der Auftrag fehlgeschlagen ist, sollten ein Datensatz mit dem Namen **BasicPlugin.FollowupPlugin: Erstellen einer Firma** angezeigt werden

    ![Fehlgeschlagener Systemauftrag](media/failed-system-job.png)

1. Wenn Sie den Systemauftrag öffnen, können Sie den Bereich **Details** erweitern, um Informationen, die in die Ablaufverfolgung geschrieben wurden, und Details zum Fehler anzuzeigen.

    ![Systemauftragsdetails](media/system-job-failed-plug-in.png)

### <a name="query-system-jobs"></a>Systemaufträge abfragen

Sie können die folgende Web API-Abfrage verwenden, um fehlerhafte Systemaufträge für asynchrone Plug-Ins zurückzugeben

```
GET <your org uri>/api/data/v9.0/asyncoperations?$filter=operationtype eq 1 and statuscode eq 31&$select=name,message
```
Mehr Informationen: [Datenabfrage über die Web API](webapi/query-data-web-api.md).


Oder Sie verwenden das folgende FetchXml:

```xml
<fetch top='50' >
  <entity name='asyncoperation' >
    <attribute name='message' />
    <attribute name='name' />
    <filter type='and' >
      <condition attribute='operationtype' operator='eq' value='1' />
      <condition attribute='statuscode' operator='eq' value='31' />
    </filter>
  </entity>
</fetch>
```
Weitere Informationen: [Verwendung von FetchXML mit FetchExpression](org-service/entity-operations-query-data.md)


## <a name="view-trace-logs"></a>Ablaufverfolgungsprotokolle anzeigen

Der Beispielcode schrieb eine Nachricht an das Ablaufverfolgungsprotokoll. Im folgenden Schritte beschrieben, wie die Protokolle angezeigt werden.

Standardmäßig sind Ablaufverfolgungsprotokolle von Plug-Ins nicht aktiviert. 

> [!TIP]
> WENN Sie es vorziehen, diese Einstellungen im Code zu ändern: Diese Einstellung befindet sich im [Organisations-Entitätsattribut PluginTraceLogSetting](reference/entities/organization.md#BKMK_PluginTraceLogSetting).
> 
> Die gültigen Werte sind:
> 
> |Value|Beschriftung|
> |--|--|
> |0|Deaktiviert|
> |1|Ausnahme|
> |2|Alle|

Verwenden Sie die folgenden Schritte, um sie in einer modellgesteuerten App zu aktivieren.

1. Öffnen Sie die angepasste Dynamics 365-App.

    ![Öffnen der angepassten Dynamics 365-App](media/tutorial-write-plug-in-open-dynamics365-custom-app.png)

1. Navigieren Sie zu **Einstellungen** > **System** > **Administration**.

    ![navigieren zur Administration](media/tutorial-write-plug-in-navigate-administration.png)

1. Wählen Sie unter **Administration** die Option **Systemeinstellungen** aus.
1. Im Dialog **Systemeinstellungen** in der Registerkarte "Anpassung" legen Sie **Protokollierung im Plug-In-Ablaufverfolgungsprotokoll aktivieren** auf **Alle** fest.

    ![Registerkarte "Systemeinstellungsanpassung"](media/tutorial-write-plug-in-system-settings-customization-tab.png)

    > [!NOTE]
    > Sie sollten die Protokollierung deaktivieren, nachdem Sie das Testen Ihres Plug-In beendet haben, oder es mindestens auf **Ausnahme** anstelle von **Alle** festlegen.

1. Klicken Sie auf **OK**, um das Dialogfeld **Systemeinstellungen** zu schließen.
1. Wiederholen Sie die Schritte zum Testen Ihres Plug-Ins, indem Sie eine neue Firma erstellen.
1. In der angepassten **Dynamics 365**-App navigieren Sie zu **Einstellungen** > **Anpassung** > **Plug-In-Ablaufverfolgungsprotokoll**.
1. Sie sollten feststellen, dass ein neuer Plug-In-Ablaufverfolgungsprotokolldatensatz erstellt wurde.

    ![Plug-In-Ablaufverfolgungsprotokolldatensatz](media/tutorial-write-plug-in-plug-in-trace-log.png)

1. Wenn Sie den Datensatz öffnen, erwarten Sie möglicherweise, dass die Informationen enthalten sind, die Sie im Ablaufprotokoll festgelegt haben. Dies ist nicht der Fall. Es wird nur überprüft, dass die Ablaufverfolgung erfolgt ist.
1. Um die Details anzuzeigen, ist es einfacher, diese Daten mithilfe der Web API in Ihrem Browser abzufragen. Nutzen Sie dazu die folgende Abfrage mit <xref href="Microsoft.Dynamics.CRM.plugintracelog?text=plugintracelog EntityType" /> mithilfe der Eigenschaft `typename`, um die Ergebnisse in der Eigenschaft `messageblock` anhand des Namens der Plug-In-Klasse zu filtern.

    `GET <your org uri>/api/data/v9.0/plugintracelogs?$select=messageblock&$filter=typename eq 'BasicPlugin.FollowUpPlugin'`

1. Bei der Web API-Abfrage können Sie die folgende Rückgabe erwarten:

    ```json
    {
        "@odata.context": "<your org uri>/api/data/v9.0/$metadata#plugintracelogs(messageblock)",
        "value": [{
            "messageblock": "FollowupPlugin: Creating the task activity.",
            "plugintracelogid": "f0c221d1-7f84-4f89-acdb-bbf8f7ce9f6c"
        }]
    }
    ```

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm haben Sie ein einfaches Plug-In erstellt und es registriert. Schließen Sie [Lernprogramm: Debuggen eines Plug-Ins](tutorial-debug-plug-in.md) ab, um zu erfahren, wie Sie dieses Plug-In debuggen.
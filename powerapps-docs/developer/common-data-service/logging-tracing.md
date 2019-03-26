---
title: Protokollierung und Rückverfolgung (Common Data Service for Apps) | Microsoft Docs
description: 'Verwenden Sie das Trace-Protokoll, um Informationen zur Ausführung von Plug-Ins zu speichern, um das Plug-In-Debugging zu unterstützen.'
ms.custom: ''
ms.date: 1/28/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: pehecke
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# Protokollierung und Ablaufverfolgung

 Eine alternative Methode, Probleme bei einem Plug-In oder einer benutzerdefinierten Workflowaktion (benutzerdefinierter Code) zu beheben, verglichen mit Debugging in [!INCLUDE[pn_Visual_Studio](../../includes/pn-visual-studio.md)], ist das Verwenden der Ablaufverfolgung. Die Ablaufverfolgung unterstützt Entwickler durch die Aufzeichnung von benutzerdefinierten Informationen zur Laufzeit als Hilfe bei der Ursachendiagnose für Codefehler. Die Ablaufverfolgung ist besonders hilfreich bei der Problembehebung von registriertem benutzerdefiniertem Code von [!INCLUDE[pn_CRM_Online](../../includes/pn-crm-online.md)], da dies die einzige unterstützte Problembehebungsmethode für dieses Szenario ist. Ablaufverfolgung wird für Sandkasten- (mit teilweiser Vertrauenswürdigkeit) und registrierten benutzerdefinierten Code mit voller Vertrauenswürdigkeit und beim synchronen oder asynchronen Ausführen unterstützt. Ablaufverfolgung wird nicht unterstützt für benutzerdefinierten Code, der in [!INCLUDE[pn_microsoft_dynamics_crm_for_outlook](../../includes/pn-microsoft-dynamics-crm-for-outlook.md)] oder einem anderen Mobil-Client ausgeführt wird.  
  
 Die Aufzeichnung von Ablaufverfolgungsinformationen zur Laufzeit für [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)]-Apps wird von einem Dienst namens <xref:Microsoft.Xrm.Sdk.ITracingService> bereitgestellt. Die Informationen, die für diesen Dienst durch benutzerdefinierten Code bereitgestellt werden, können an drei verschiedenen Orten erfasst werden, wie hier identifiziert.  

> [!NOTE]
> Nachverfolgungsrotokollierung mithilfe von `ITracingService` Schnittstellen geht nur, wenn das Plug-In im Sandkastenumgebung-Modus registriert ist.

- ****Ablaufverfolgungsprotokoll****  
  
     Ablaufverfolgungsprotokoll-Datensätze vom Typ **PluginTraceLog** können in der Webanwendung gefunden werden. Navigieren Sie zu **Einstellungen** und wählen die Kachel **Plug-in Trace Log**. Die Kachel ist nur sichtbar, wenn Sie über Zugriff auf die Ablaufverfolgungsprotokoll-Entitätsdatensätze in Ihrer zugewiesenen Sicherheitsrolle verfügen. Das Schreiben dieser Datensätze wird über die Ablaufverfolgungseinstellungen gesteuert, die im nächsten Abschnitt beschrieben werden.
  
    > [!NOTE]
    > Die Ablaufverfolgungsprotokollierung erfordert Organisationsspeicherplatz, insbesondere wenn viele Ablaufverfolgungen und Ausnahmen generiert werden. Sie sollten die Ablaufverfolgungsprotokollierung nur für das Debugging und die Problembehandlung aktivieren, und deaktivieren, wenn die Überprüfung abgeschlossen ist.  
  
- ****Fehlerdialogfeld****  
  
     Ein synchrones registriertes Plug-In oder eine benutzerdefinierte Workflowaktion, die eine Ausnahme an die Plattform zurückgibt, führt zu einem Fehlerdialogfeld in der Webanwendung, die dem angemeldeten Benutzer angezeigt wird. Der Benutzer kann die Schaltfläche **Protokolldatei herunterladen** im Dialogfeld auswählen, um das Protokoll mit der Ausnahme und der Ablaufverfolgungsausgabe anzuzeigen.  
  
- ****Systemauftrag****  
  
     Bei asynchronen registrierten Plug-Ins oder benutzerdefinierten Workflowaktionen, die eine Ausnahme zurückgeben, werden die Ablaufverfolgungsinformationen im Bereich **Details** des **Systemauftrag**-Formulars in der Webanwendung angezeigt.  
  
<a name="bkmk_trace-settings"></a>   
## Ablaufverfolgungsprotokollierung aktivieren  
 Um die Ablaufverfolgungsprotokollierung in einer Organisation zu aktivieren, die diese Funktion unterstützt, navigieren Sie in der Webanwendung zu **Einstellungen** > **Verwaltung** > **Systemeinstellungen**. Auf der Registerkarte **Anpassung** suchen Sie das Dropdownmenü namens **Protokollierung in Plug-in-Ablaufverfolgungsprotokoll aktivieren** und wählen Sie eine der verfügbaren Optionen aus.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|Deaktiviert|Das Schreiben in das Ablaufverfolgungsprotokoll ist deaktiviert. Kein **PluginTraceLog** Datensatz wird erstellt. Allerdings kann benutzerdefinierter Code weiter die <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])>-Methode aufrufen, auch wenn noch kein Protokoll geschrieben wurde.|  
|Ausnahmen|Ablaufverfolgungsinformationen werden in das Protokoll geschrieben, wenn eine Ausnahme wieder an die Plattform von benutzerdefiniertem Code zurückgegeben wird.|  
|Alle|Ablaufverfolgungsinformationen werden bei Fertigstellung von Code in das Protokoll geschrieben, oder wenn eine Ausnahme wieder an die Plattform von benutzerdefiniertem Code zurückgegeben wird.|  
  
 Wenn die Ablaufverfolgungsprotokollierungs-Einstellung auf **Ausnahme** gesetzt ist und benutzerdefinierter Code eine Ausnahme wieder zur Plattform zurückgibt, wird ein Ablaufverfolgungsprotokolldatensatz erstellt und Ablaufverfolgungsinformationen werden zudem an einen anderen Ort geschrieben. Bei benutzerdefiniertem Code, der synchron ausgeführt wird, werden die Informationen in einem Fehlerdialogfeld dem Benutzer angezeigt; andernfalls, für asynchronen Code, werden die Informationen in den verknüpften Systemauftrag geschrieben.  
  
 Standardmäßig weisen die Rollen "Systemadministrator" und "Systemanpasser" die erforderlichen Berechtigungen auf, um die Ablaufverfolgungsprotokollierungs-Einstellung zu ändern, die in einem <xref:Microsoft.Xrm.Sdk.Deployment.TraceSettings>-Entitätsdatensatz gespeichert wird. Ablaufverfolgungseinstellungen haben einen Organisationsbereich.  
  
## Schreiben in den Ablaufverfolgungsdienst  
 Bevor Sie in den Ablaufverfolgungsdienst schreiben, müssen Sie erst das Ablaufverfolgungsdienstobjekt aus dem übergebenen Ausführungskontext extrahieren. Danach fügen Sie ggf. einfach <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])>-Aufrufe benutzerdefiniertem Code hinzu, wobei alle relevanten Diagnoseinformationen in diesem Methodenaufruf übergeben werden.  

 Laden Sie das Beispiel herunter: [Arbeiten mit Plug-Ins](https://code.msdn.microsoft.com/Sample-Create-a-basic-plug-64d86ade).
  
 ```csharp
//Extract the tracing service for use in debugging sandboxed plug-ins.
 ITracingService tracingService =
     (ITracingService)serviceProvider.GetService(typeof(ITracingService));

 // Obtain the execution context from the service provider.
 IPluginExecutionContext context = (IPluginExecutionContext)
     serviceProvider.GetService(typeof(IPluginExecutionContext));

 // For this sample, execute the plug-in code only while the client is online. 
 tracingService.Trace("AdvancedPlugin: Verifying the client is not offline.");
 if (context.IsExecutingOffline || context.IsOfflinePlayback)
     return;

 // The InputParameters collection contains all the data passed 
 // in the message request.
 if (context.InputParameters.Contains("Target") &&
     context.InputParameters["Target"] is Entity)
 {
     // Obtain the target entity from the Input Parameters.
     tracingService.Trace
         ("AdvancedPlugin: Getting the target entity from Input Parameters.");
     Entity entity = (Entity)context.InputParameters["Target"];

     // Obtain the image entity from the Pre Entity Images.
     tracingService.Trace
         ("AdvancedPlugin: Getting image entity from PreEntityImages.");
     Entity image = (Entity)context.PreEntityImages["Target"];
```

  
 Entwickeln Sie anschließend das Plug-In oder die benutzerdefinierte Workflowaktion und stellen Sie diese(s) bereit. Während der Ausführung von benutzerdefiniertem Code wird die Information, die in den -Methodenaufrufen **Ablaufverfolgung** bereitgestellt wird, in einen Ablaufverfolgungsprotokoll-Entitätsdatensatz von <xref:Microsoft.Xrm.Sdk.ITracingService> geschrieben, wenn dies von Ihrer Organisation unterstützt wird und aktiviert ist, und kann auch dem Benutzer in einem Web-Dialog oder Systemauftrag bereitgestellt werden, wie im vorherigen Abschnitt beschrieben. Die Ablaufverfolgungsinformationen, die in das Ablaufverfolgungsprotokoll geschrieben werden, werden in den Ablaufverfolgungseinstellungen konfiguriert. Weitere Informationen finden Sie unter [Trace-Logging aktivieren](#bkmk_trace-settings).  
  
> [!NOTE]
> Wenn benutzerdefinierter Code in einer Datenbanktransaktion ausgeführt wird und eine Ausnahme auftritt, die ein Transaktionsrollback verursacht, werden alle Entitätsdatenänderungen durch Code rückgängig gemacht. Die **PluginTraceLog**-Datensätze bleiben jedoch bis zum Fertigstellen des Rollbacks vorhanden.  
  
## Zusätzliche Informationen über den Tracing-Dienst

 Die<xref:Microsoft.Xrm.Sdk.ITracingService> verarbeitet stapelweise die Informationen, die dafür über die **Ablaufverfolgungs** -Methode bereitgestellt werden. Die Informationen werden in einen neuen **PluginTraceLog**-Datensatz geschrieben, wenn benutzerdefinierter Code erfolgreich zum Abschluss ausgeführt oder eine Ausnahme ausgelöst wurde.  
  
 PluginTraceLog-Datensätze haben eine begrenzte Gültigkeitsdauer. Ein Massenlöschungs-Hintergrundauftrag wird einmal täglich ausgeführt, um Datensätze zu löschen, die älter als 24 Stunden seit der Erstellung sind. Dieser Auftrag kann bei Bedarf deaktiviert werden. 

## Community-Tools

 ### Plug-in Trace-Viewer

**Plug-In-Ablaufverfolgungsanzeige** ist ein Tool, das die XrmToolbox-Community für [!INCLUDE[pn_dynamics_crm](../../includes/pn-dynamics-crm.md)]-Apps entwickelte. Weitere Informationen finden Sie im Thema [Entwicklertools](developer-tools.md) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von [!include[pn_microsoft_dynamics](../../includes/pn-microsoft-dynamics.md)]-Apps. Es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).  

### Siehe auch

[[Plug-Ins](plug-ins.md)](plug-ins.md)  
[[Debuggen Sie ein Plug-In](debug-plug-in.md#use-tracing)](debug-plug-in.md#use-tracing)  
[[Ablaufverfolgungsprotokolle anzeigen](tutorial-write-plug-in.md#view-trace-logs)](tutorial-write-plug-in.md#view-trace-logs)  
[[Den Ablaufverfolgungsdienst verwenden](write-plug-in.md#use-the-tracing-service)](write-plug-in.md#use-the-tracing-service)  
[[PluginTraceLog-Entität](reference/entities/plugintracelog.md)](reference/entities/plugintracelog.md)
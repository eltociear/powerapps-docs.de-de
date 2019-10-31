---
title: Protokollierung und Verfolgung (Common Data Service) | Microsoft Docs
description: 'Verwenden Sie das Trace-Protokoll, um Informationen zur Ausführung von Plug-Ins zu speichern, um das Plug-In-Debugging zu unterstützen.'
ms.custom: ''
ms.date: 09/19/2019
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
# <a name="tracing-and-logging"></a>Protokollierung und Ablaufverfolgung

Verwenden Sie eine Verfolgung, um Fehler bei einem Plug-In oder einer benutzerdefinierten Workflowaktivität (benutzerdefiniertem Code) zu beheben. Die Ablaufverfolgung unterstützt Entwickler durch die Aufzeichnung von Informationen zur Laufzeit als Hilfe bei der Ursachendiagnose für Codefehler. Die Ablaufverfolgung wird für synchrone oder synchrone Ausführung unterstützt.
  
Die Aufzeichnung von Ablaufverfolgungsinformationen zur Laufzeit für Common Data Service wird von einem Dienst namens <xref:Microsoft.Xrm.Sdk.ITracingService> bereitgestellt. Die Informationen, die für diesen Dienst durch benutzerdefinierten Code bereitgestellt werden, können an drei verschiedenen Orten erfasst werden, wie hier identifiziert.  

- **Ablaufverfolgungsprotokoll**  
  
    Ablaufverfolgungsprotokolldatensätze werden für die [PluginTraceLog-Entität](reference/entities/plugintracelog.md) erstellt. Das Schreiben dieser Datensätze wird über die Ablaufverfolgungseinstellungen gesteuert, die in [Ablaufverfolgungsprotokollierung aktivieren](#enable-trace-logging) beschrieben werden.

    Diese Daten können in modellgesteuerten Anwendungen gefunden werden, indem Sie zu **Einstellungen** navigieren und die Kachel **Plug-In-Ablaufverfolgungsprotokoll** auswählen. Die Kachel ist nur sichtbar, wenn Sie über Zugriff auf die Ablaufverfolgungsprotokoll-Entitätsdatensätze in Ihrer zugewiesenen Sicherheitsrolle verfügen.

    Sie finden es möglicherweise einfacher, diese Daten mit der Web-API in Ihrem Browser unter Anwendung des Beispiels abzurufen, das unter [Ablaufverfolgung verwenden](debug-plug-in.md#use-tracing) dargestellt wird, oder indem Sie das [Plug-in Trace-Viewer](#plug-in-trace-viewer)-Community-Tool verwenden.

    > [!IMPORTANT]
    > Die Ablaufverfolgungsprotokollierung erfordert Organisationsspeicherplatz, insbesondere wenn viele Ablaufverfolgungen und Ausnahmen generiert werden. Sie sollten die Ablaufverfolgungsprotokollierung nur für das Debugging und die Problembehandlung aktivieren, und deaktivieren, wenn die Überprüfung abgeschlossen ist.  
  
- **Fehlerdialogfeld**  
  
     Ein synchrones registriertes Plug-In oder eine benutzerdefinierte Workflowaktivität, die eine Ausnahme von der Plattform zurückgibt, führt zu einem Fehlerdialogfeld in der Webanwendung, die dem angemeldeten Benutzer angezeigt wird. Der Benutzer kann die Schaltfläche **Protokolldatei herunterladen** im Dialogfeld auswählen, um das Protokoll mit der Ausnahme und der Ablaufverfolgungsausgabe anzuzeigen.  
  
- **Systemauftrag**  
  
     Bei asynchronen registrierten Plug-Ins oder benutzerdefinierten Workflowaktionen, die eine Ausnahme zurückgeben, werden die Ablaufverfolgungsinformationen im Bereich **Details** des **Systemauftrag**-Formulars in der Webanwendung angezeigt.  
  
<a name="bkmk_trace-settings"></a>

## <a name="enable-trace-logging"></a>Ablaufverfolgungsprotokollierung aktivieren

Ob Ablaufverfolgungsprotokolle geschrieben werden, hängt vom Wert der [Organisations](/powerapps/developer/common-data-service/reference/entities/organization)-Entität und dem [PluginTraceLogSetting](/powerapps/developer/common-data-service/reference/entities/organization#BKMK_PluginTraceLogSetting)-Attributwert ab.

Um die Ablaufverfolgungsprotokollierung zu aktivieren, können Sie diesen Wert programmatisch aktualisieren oder in der Webanwendung zu **Einstellungen** > **Verwaltung** > **Systemeinstellungen** navigieren. Auf der Registerkarte **Anpassung** suchen Sie das Dropdownmenü namens **Protokollierung in Plug-in-Ablaufverfolgungsprotokoll aktivieren** und wählen Sie eine der verfügbaren Optionen aus.  
  
|Value|Option|Beschreibung|  
|------------|-----------------|-----------------|  
|0|Deaktiviert|Das Schreiben in das Ablaufverfolgungsprotokoll ist deaktiviert. Kein **PluginTraceLog** Datensatz wird erstellt. Allerdings kann benutzerdefinierter Code weiter die <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])>-Methode aufrufen, auch wenn noch kein Protokoll geschrieben wurde.|  
|1|Ausnahmen|Ablaufverfolgungsinformationen werden in das Protokoll geschrieben, wenn eine Ausnahme wieder an die Plattform von benutzerdefiniertem Code zurückgegeben wird.|  
|2|Alle|Ablaufverfolgungsinformationen werden bei Fertigstellung von Code in das Protokoll geschrieben, oder wenn eine Ausnahme wieder an die Plattform von benutzerdefiniertem Code zurückgegeben wird.|  
  
Wenn die Ablaufverfolgungsprotokollierungs-Einstellung auf **Ausnahme** gesetzt ist und benutzerdefinierter Code eine Ausnahme wieder zur Plattform zurückgibt, wird ein Ablaufverfolgungsprotokolldatensatz erstellt und Ablaufverfolgungsinformationen werden zudem an einen anderen Ort geschrieben. Bei benutzerdefiniertem Code, der synchron ausgeführt wird, werden die Informationen in einem Fehlerdialogfeld dem Benutzer angezeigt; andernfalls, für asynchronen Code, werden die Informationen in den verknüpften Systemauftrag geschrieben.  

## <a name="write-to-the-tracing-service"></a>Schreiben in den Ablaufverfolgungsdienst

Bevor Sie in den Ablaufverfolgungsdienst schreiben, müssen Sie erst das Ablaufverfolgungsdienstobjekt aus dem übergebenen Ausführungskontext extrahieren. Danach fügen Sie ggf. einfach <xref:Microsoft.Xrm.Sdk.ITracingService.Trace(System.String,System.Object[])>-Aufrufe benutzerdefiniertem Code hinzu, wobei alle relevanten Diagnoseinformationen in diesem Methodenaufruf übergeben werden.  

  
 ```csharp
//Extract the tracing service for use in debugging plug-ins.
 ITracingService tracingService =
     (ITracingService)serviceProvider.GetService(typeof(ITracingService));

 // Use the tracing service 
 tracingService.Trace("Write your message here.");
 
```

Entwickeln Sie anschließend das Plug-In oder die benutzerdefinierte Workflowaktion und stellen Sie diese(s) bereit. Während der Ausführung von benutzerdefiniertem Code wird die Information, die in den -Methodenaufrufen **Ablaufverfolgung** bereitgestellt wird, in einen Ablaufverfolgungsprotokoll-Entitätsdatensatz von <xref:Microsoft.Xrm.Sdk.ITracingService> geschrieben, wenn dies von Ihrer Organisation unterstützt wird und aktiviert ist, und kann auch dem Benutzer in einem Web-Dialog oder Systemauftrag bereitgestellt werden, wie im vorherigen Abschnitt beschrieben. Die Ablaufverfolgungsinformationen, die in das Ablaufverfolgungsprotokoll geschrieben werden, werden in den Ablaufverfolgungseinstellungen konfiguriert. Weitere Informationen finden Sie unter [Trace-Logging aktivieren](#bkmk_trace-settings).  
  
> [!NOTE]
> Wenn benutzerdefinierter Code in einer Datenbanktransaktion ausgeführt wird und eine Ausnahme auftritt, die ein Transaktionsrollback verursacht, werden alle Entitätsdatenänderungen durch Code rückgängig gemacht. Die [PluginTraceLog](reference/entities/plugintracelog.md)-Datensätze bleiben jedoch bis zum Fertigstellen des Rollbacks vorhanden.  
  
## <a name="additional-information-about-the-tracing-service"></a>Zusätzliche Informationen über den Tracing-Dienst

Die<xref:Microsoft.Xrm.Sdk.ITracingService> verarbeitet stapelweise die Informationen, die dafür über die **Ablaufverfolgungs** -Methode bereitgestellt werden. Die Informationen werden in einen neuen [PluginTraceLog](reference/entities/plugintracelog.md)-Datensatz geschrieben, wenn benutzerdefinierter Code erfolgreich zum Abschluss ausgeführt oder eine Ausnahme ausgelöst wurde.  

Jeder Trace-Aufruf wird als neue Zeile im Attribut [PluginTraceLog](reference/entities/plugintracelog.md) [MessageBlock](reference/entities/plugintracelog.md#BKMK_MessageBlock) protokolliert. Es kann nur Text mit einer Größe von 10 KB erstellt werden. Ältere Trace-Zeilen werden entfernt, um diesen Grenzwert einzuhalten, sodass nur die neuesten Zeilen gespeichert werden.
  
[PluginTraceLog](reference/entities/plugintracelog.md)-Datensätze haben eine begrenzte Gültigkeitsdauer. Ein Massenlöschungs-Hintergrundauftrag wird einmal täglich ausgeführt, um Datensätze zu löschen, die älter als 24 Stunden seit der Erstellung sind. 

> [!CAUTION]
> Während dieser Auftrag deaktiviert oder die Häufigkeit, mit dem er auftritt, angepasst werden kann, wird häufig festgestellt, dass ein fehlendes Zurücksetzen auf die ursprüngliche Einstellung der Grund für spätere Leistungsprobleme ist.

## <a name="community-tools"></a>Community-Tools

 ### <a name="plug-in-trace-viewer"></a>Plug-in Trace-Viewer

**Plug-In-Ablaufverfolgungsanzeige** ist ein Tool, das die XrmToolbox-Community entwickelte. Bitte beachten Sie das Thema [Community-Tools für Common Data Service](community-tools.md) für Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Microsoft und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com).  

### <a name="see-also"></a>Siehe auch

[Plug-Ins](plug-ins.md)  
[Debuggen Sie ein Plug-In](debug-plug-in.md#use-tracing)  
[Ablaufverfolgungsprotokolle anzeigen](tutorial-write-plug-in.md#view-trace-logs)  
[Den Ablaufverfolgungsdienst verwenden](write-plug-in.md#use-the-tracing-service)  
[PluginTraceLog-Entität](reference/entities/plugintracelog.md)
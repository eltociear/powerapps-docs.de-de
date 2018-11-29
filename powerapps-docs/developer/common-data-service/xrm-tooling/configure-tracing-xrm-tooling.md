---
title: Konfigurieren Sie das Tracing für XRM-Tools (Common Data Service for Apps) | Microsoft Docs
description: 'Erfahren Sie, wie Sie die Ablaufverfolgung für Komponenten wie Vorgangsanrufe, Warnungen und andere bedeutende Ereignisse in XRM-Tooling zu konfigurieren.'
ms.custom: ''
ms.date: 10/31/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
ms.assetid: d7586a5a-40da-427e-bbeb-4f8a371a8dcf
caps.latest.revision: 8
author: MattB-msft
ms.author: kvivek
manager: kvivek
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-tracing-for-xrm-tooling"></a>Konfigurieren der Ablaufverfolgung für XRM-Tooling

Sie können die Ablaufverfolgung für die Datensatzdaten aktivieren, die mit Prozess-Meilensteinen über alle Komponenten des XRM-Toolings hinweg verknüpft sind, wie Vorgangsaufrufe, Warnungen, Ausnahmen und andere wichtige Ereignisse. Diese Informationen können für die Behandlung von Betriebs- und Leistungsproblemen in Ihren Wndows-Client-Anwendungen verwendet werden. Die Ablaufverfolgung im XRM-Tooling setzt auf [System.Diagnostics.Tracing](/dotnet/api/system.diagnostics.tracing) auf. Zum Aktivieren der Ablaufverfolgung für eine Assembly oder Komponente wie Microsoft.Xrm.Tooling.Connector, müssen Sie die folgenden drei Punkte für jede Komponente in Ihrem Code oder in der Konfigurationsdatei der Anwendung (*\<AppName>*.exe.config) definieren:  
  
- eine Ablaufverfolgungsquelle  
- einen Ablaufverfolgungslistener  
- eine andere Ablaufverfolgungsebene als **Aus** Dies sind die andere Werte, die Sie angeben können: **Fehler**, **Warnung**, **Informationen** und **ausführlich**.  
  
 Dies ist die Konfiguration für die Aktivierung der Ablaufverfolgung für eine Komponente im XRM-Tooling. Die folgende Konfiguration aktiviert die Ablaufverfolgung beispielsweise nur für die Microsoft.Xrm.Tooling.CrmConnectControl-Komponente:  
  
```xml  
</configuration>  
  <system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
      <source name="DynamicsCrm.CrmConnectControl"  
        switchName="DynamicsCrm.CrmConnectControl"  
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <!--   
            Possible values for switches: Off, Error, Warning, Info, Verbose  
                Verbose:    includes Error, Warning, Info, Trace levels  
                Info:       includes Error, Warning, Info levels  
                Warning:    includes Error, Warning levels  
                Error:      includes Error level  
        -->  
      <add name="DynamicsCrm.CrmConnectControl" value="Verbose"/>  
    </switches>  
    <sharedListeners>  
      <add name="fileListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="XRMLoginControl.log"/>  
      <add name="eventLogListener" type="System.Diagnostics.EventLogTraceListener" initializeData="XRMLogin"/>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
Wenn Sie die Ablaufverfolgung für alle Komponenten im XRM-Tooling aktivieren möchten, können Sie das auch tun. Dies ist die Konfiguration für eine kombinierte Ablaufverfolgung von allen drei Komponenten des XRM-Toolings:  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
      <source name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient"  
              switchName="Microsoft.Xrm.Tooling.Connector.CrmServiceClient"  
              switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
  
      <source name="Microsoft.Xrm.Tooling.CrmConnectControl"  
              switchName="Microsoft.Xrm.Tooling.CrmConnectControl"  
              switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
  
      <source name="Microsoft.Xrm.Tooling.WebResourceUtility"  
        switchName="Microsoft.Xrm.Tooling.WebResourceUtility"  
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console" type="System.Diagnostics.DefaultTraceListener" />  
          <remove name="Default"/>  
          <add name ="fileListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <!--   
            Possible values for switches: Off, Error, Warning, Info, Verbose  
                Verbose:    includes Error, Warning, Info, Trace levels  
                Info:       includes Error, Warning, Info levels  
                Warning:    includes Error, Warning levels  
                Error:      includes Error level  
        -->  
      <add name="Microsoft.Xrm.Tooling.Connector.CrmServiceClient" value="Verbose" />  
      <add name="Microsoft.Xrm.Tooling.CrmConnectControl" value="Verbose"/>  
      <add name="Microsoft.Xrm.Tooling.WebResourceUtility" value="Verbose" />  
  
    </switches>  
    <sharedListeners>  
      <add name="fileListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="XRMToolingLogs.log"/>        
      <add name="eventLogListener" type="System.Diagnostics.EventLogTraceListener" initializeData="XRMTooling" />  
    </sharedListeners>  
  
  </system.diagnostics>  
</configuration>  
```  
  
### <a name="see-also"></a>Siehe auch

[Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](build-windows-client-applications-xrm-tools.md)

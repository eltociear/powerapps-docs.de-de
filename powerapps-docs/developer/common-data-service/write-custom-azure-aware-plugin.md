---
title: Schreiben eines benutzerdefinierten Azure-Plug-Ins (Common Data Service) | Microsoft Docs
description: Das folgende Beispiel zeigt, wie Plug-In-Code hinzugefügt werden kann, um den Azure-Dienstanbieter abzurufen und die Veröffentlichung des Ausführungskontexts auf dem Servicebus durch Aufrufen von IExecutionContext) zu initiieren.
keywords: ''
ms.date: 10/31/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 93d0442e-5fc9-c43c-c8c1-a433687f3d0a
author: JimDaly
ms.author: jdaly
manager: ryjones
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: ec78fd214741b6bd2e6377d20fdd6fc238d9af88
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748331"
---
# <a name="write-a-custom-azure-aware-plug-in"></a>Schreiben eines benutzerdefinierten Azure-Plug-Ins

<!-- https://docs.microsoft.com/dynamics365/customer-engagement/developer/write-custom-azure-aware-plugin -->

Das Schreiben eines Plug-Ins, das mit Azure funktioniert ähnelt dem Schreiben eines beliebigen anderen Dynamics 365 Common Data Service-Plug-Ins. Allerdings zusätzlich zum Aufrufen aller gewünschten Webdienstmethoden muss das Plug-In Code enthalten, um das Veröffentlichen des Ausführungskontexts im Azure Service Bus einzuleiten.  
  
<a name="bkmk_design"></a>

## <a name="plug-in-design-considerations"></a>Plug-In-Entwurfsüberlegungen  
Für ein Plug-In, das synchron ausgeführt wird, sollte der Entwurf so aussehen, dass das Plug-In eine Nachricht an Azure sendet, um Informationen von einer Listener-Anwendung oder einem anderen externen Dienst abzurufen. Die Verwendung eines bidirektionalen oder REST-Vertrags auf dem Azure Service Bus-Endpunkt ermöglicht die Rückgabe einer Datenzeichenfolge an das Plug-In.  
  
Es wird nicht empfohlen, dass ein synchrones Plug-In den Azure Service Bus verwendet, um Daten mit einem externen Dienst zu aktualisieren. Probleme können auftreten, wenn der externe Dienst nicht verfügbar ist oder wenn viele Daten aktualisiert werden müssen. Synchrone Plug-Ins sollten schnell ausgeführt werden und nicht alle angemeldeten Benutzer einer Organisation aufhalten, während ein langatmiger Vorgang ausgeführt wird. Wenn zudem ein Rollback des aktuellen Kernvorgangs, der das Plug-In aufgerufen hat, auftritt, werden alle vorgenommenen Datenänderungen rückgängig gemacht. Dies könnte dazu führen, dass Dynamics 365 und ein externer Dienst in einem unsynchronisierten Status bleiben.  
  
Beachten Sie, dass es für synchrone registrierte Plug-Ins möglich ist, den Ausführungskontext im Azure Service Bus bereitzustellen.  
  
<a name="bkmk_writing"></a>
  
## <a name="write-the-plug-in-code"></a>Schreiben des Plug-In-Codes 
 
Im folgenden Beispiel wurde Plug-In-Code hinzugefügt, um den Azure-Dienstanbieter abzurufen und die Bereitstellung des Ausführungskontexts auf dem Servicebus durch Aufrufen von <xref:Microsoft.Xrm.Sdk.IServiceEndpointNotificationService.Execute(Microsoft.Xrm.Sdk.EntityReference,Microsoft.Xrm.Sdk.IExecutionContext)> zu initiieren. Ablaufverfolgungscode wurde hinzugefügt, um das Debuggen von Plug-Ins zu erleichtern, da das Plug-In im Sandkasten ausgeführt werden muss.  

> [!NOTE]
> Die `serviceEndpointId`, die an den Konstruktor in diesem Code übergeben wurde, ist diejenige, die Sie vom Erstellen eines Dienstendpunkts erhalten, wie beschrieben in [Exemplarische Vorgehensweise: Konfigurieren von Azure (SAS) für die Integration mit Common Data Service](walkthrough-configure-azure-sas-integration.md)
>
> Sie können verfügbare Dienstendpunkte für Ihre Umgebung mit einer `GET`-Anforderung an die Web-API abfragen. Verwenden Sie dazu Ihren Browser mit einer Abfrage wie der Folgenden: *`[organization Uri]`*`/api/data/v9.0/serviceendpoints?$select=name,description,serviceendpointid`
  
```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Runtime.Serialization;

using System.ServiceModel;
using System.ServiceModel.Channels;
using System.ServiceModel.Description;

using Microsoft.Xrm.Sdk;

namespace Microsoft.Crm.Sdk.Samples
{
    /// <summary>
    /// A custom plug-in that can post the execution context of the current message to the Windows
    /// Azure Service Bus. The plug-in also demonstrates tracing which assist with
    /// debugging for plug-ins that are registered in the sandbox.
    /// </summary>
    /// <remarks>This sample requires that a service endpoint be created first, and its ID passed
    /// to the plug-in constructor through the unsecure configuration parameter when the plug-in
    /// step is registered.</remarks>
    public sealed class SandboxPlugin : IPlugin
    {
        private Guid serviceEndpointId; 

        /// <summary>
        /// Constructor.
        /// </summary>
        public SandboxPlugin(string config)
        {
            if (String.IsNullOrEmpty(config) || !Guid.TryParse(config, out serviceEndpointId))
            {
                throw new InvalidPluginExecutionException("Service endpoint ID should be passed as config.");
            }
        }

        public void Execute(IServiceProvider serviceProvider)
        {
            // Retrieve the execution context.
            IPluginExecutionContext context = (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));

            // Extract the tracing service.
            ITracingService tracingService = (ITracingService)serviceProvider.GetService(typeof(ITracingService));
            if (tracingService == null)
                throw new InvalidPluginExecutionException("Failed to retrieve the tracing service.");

            IServiceEndpointNotificationService cloudService = (IServiceEndpointNotificationService)serviceProvider.GetService(typeof(IServiceEndpointNotificationService));
            if (cloudService == null)
                throw new InvalidPluginExecutionException("Failed to retrieve the service bus service.");

            try
            {
                tracingService.Trace("Posting the execution context.");
                string response = cloudService.Execute(new EntityReference("serviceendpoint", serviceEndpointId), context);
                if (!String.IsNullOrEmpty(response))
                {
                    tracingService.Trace("Response = {0}", response);
                }
                tracingService.Trace("Done.");
            }
            catch (Exception e)
            {
                tracingService.Trace("Exception: {0}", e.ToString());
                throw;
            }
        }
    }
}
```  
  
In Ihrem Plug-In-Code können Sie die schreibbaren Daten im Kontext aktualisieren, bevor Sie die Veröffentlichung initiieren. Sie können beispielsweise ein Schlüssel-/Wertpaar im Kontext den freigegebenen Variablen hinzufügen. 
  
<a name="bkmk_registration"></a>

## <a name="plug-in-registration"></a>Plug-In-Registrierung

Es gibt einige Beschränkungen, wenn Sie ein benutzerdefiniertes Azure-kompatibles Plug-In registrieren. Das Plug-In muss für die Ausführung im Sandkasten registriert werden. Darum ist das Plug-In auf den Aufruf von <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Methoden, von Azure-Lösungsmethoden oder den Zugriff auf ein Netzwerk mithilfe eines Webclient beschränkt. Kein anderer externer Zugriff, wie der Zugriff auf ein lokales Dateisystem, ist zulässig.  
  
Für ein Plug-In, das für die Ausführung im asynchronen Modus registriert ist, bedeutet das auch, dass die Reihenfolge der Plug-In-Ausführung verglichen mit anderen asynchronen Plug-Ins nicht garantiert ist. Darüber hinaus werden asynchrone Plug-Ins immer nach dem Dynamics 365-Kernvorgang ausgeführt.  
  
<a name="bkmk_failure"></a>
 
## <a name="handle-a-failed-service-bus-post"></a>Verarbeiten einer fehgeschlagenen Servicebusnachricht

Das erwartete Verhalten einer fehlgeschlagenen Servicebusnachricht ist davon abhängig, ob das Plug-In für asynchrone oder synchrone Ausführung registriert wurde. Für asynchrone Plug-Ins wiederholt der Systemauftrag, der den Ausführungskontext tatsächlich an den Servicebus sendet, den Sendevorgang. Für ein synchrones registriertes Plug-In wird eine Ausnahme zurückgegeben. Weitere Informationen: [Verwaltung und Meldung von Laufzeitfehlern](azure-integration.md)  
  
> [!IMPORTANT]
>  Nur für asynchrone registrierte Plug-Ins, wenn der asynchrone Auftrag, der an Azure Service Bus bereitstellt, nach einem Bereitstellungsfehler wiederholt wird, wird die gesamte Plug-In-Logik erneut ausgeführt. Darum fügen Sie keine andere Logik zum benutzerdefinierten Azure-kompatiblen Plug-In hinzu. Sie ändern nur den Kontext und führen eine Bereitstellung an den Servicebus aus.  
  
Für ein Plug-In, das für die asynchrone Ausführung registriert ist, umfasst <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext>, das im Textteil der Nachricht enthalten ist, die über den Servicebus gesendet wird, die Eigenschaften <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.OperationId> und <xref:Microsoft.Xrm.Sdk.RemoteExecutionContext.OperationCreatedOn> ein. Diese Eigenschaften enthalten dieselben Daten wie die Attribute `AsyncOperationId` und `CreatedOn` des verknüpften Systemauftrag-Datensatzes (`AsyncOperation`). Diese zusätzlichen Eigenschaften unterstützen die Sequenzierung und die Duplikaterkennung, wenn das Bereitstellen an den Azure Service Bus wiederholt werden muss.  
  
### <a name="see-also"></a>Siehe auch

[Azure-Erweiterungen für Dynamics 365](azure-integration.md)<br />
[Senden von Dynamics 365-Daten über den Microsoft Azure Service Bus](work-data-azure-solution.md)<br />
[Schreiben eines Plug-Ins](write-plug-in.md)<br />
[Ereignisausführungspipeline](event-framework.md)<br />
[Registrieren und Bereitstellen von Plug-Ins](register-plug-in.md)

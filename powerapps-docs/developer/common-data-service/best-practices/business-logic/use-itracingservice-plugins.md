---
title: ITracingService in Plug-Ins verwenden | MicrosoftDocs
description: Das Debuggen und/oder die Fehlerbehebung bei Plug-in-Problemen oder -Verhalten ist kompliziert, ohne eine umfangreiche und aufschlussreiche Protokollierung oder Nachverfolgung.
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d6849e0038dab80a8275b247e8bfd4239a4ec1ec
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748241"
---
# <a name="use-itracingservice-in-plug-ins"></a>ITracingService in Plug-Ins verwenden

**Kategorie**: Wartbarkeit, Supportfähigkeit

**Wirkungspotential**: Mittel

<a name='symptoms'></a>

## <a name="symptoms"></a>Symptome

Das Debuggen und/oder die Fehlerbehebung bei Plug-in-Problemen oder -Verhalten ist kompliziert, ohne eine umfangreiche und aufschlussreiche Protokollierung oder Nachverfolgung.

<a name='guidance'></a>

## <a name="guidance"></a>Anleitung

Die <xref:Microsoft.Xrm.Sdk.ITracingService>-Schnittstelle unterstützt Entwickler durch die Aufzeichnung von benutzerdefinierten Informationen zur Laufzeit als Hilfe bei der Diagnose der Ursache von Codefehlern oder unerwartetem Verhalten in Plugins. Bevor Sie in den Tracing-Service schreiben, müssen Sie zunächst das Tracing-Service-Objekt aus dem übergebenen Ausführungskontext extrahieren. Anschließend fügen Sie einfach [Trace](/dotnet/api/microsoft.xrm.sdk.itracingservice.trace)-Aufrufe zu Ihrem benutzerdefinierten Code hinzu, wobei Sie gegebenenfalls alle relevanten Diagnoseinformationen in diesem Methodenaufruf übergeben.

> [!NOTE]
> Die Ablaufprotokollierung mit der Schnittstelle `ITracingService` funktioniert nur, wenn das Plug-in im Sandbox-Modus registriert ist und Sie die Ablaufprotokollierung aktivieren müssen, um Laufzeitdaten zu erhalten. Weitere Informationen finden Sie unter: [Protokollierung und Verfolgung](/dynamics365/customer-engagement/developer/debug-plugin#logging-and-tracing)

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
    tracingService.Trace("AdvancedPlugin: Getting the target entity from Input Parameters.");
    Entity entity = (Entity)context.InputParameters["Target"];

    // Obtain the image entity from the Pre Entity Images.
    tracingService.Trace("AdvancedPlugin: Getting image entity from PreEntityImages.");
    Entity image = (Entity)context.PreEntityImages["Target"];
}
```

<a name='additional'></a>

## <a name="additional-information"></a>Weitere Informationen

Die Ablaufverfolgung ist besonders hilfreich bei der Problembehebung von registriertem benutzerdefiniertem Code, da dies die einzige unterstützte Problembehebungsmethode für dieses Szenario ist. Das Tracing wird für `sandboxed` (partial trust) und full trust registrierten benutzerdefinierten Code sowie während der synchronen oder asynchronen Ausführung unterstützt. Ablaufverfolgung wird nicht unterstützt für benutzerdefinierten Code, der in Microsoft Dynamics 365 for Outlook oder einem anderen Mobil-Client ausgeführt wird.

<a name='seealso'></a>

### <a name="see-also"></a>Siehe auch

[Schreiben eines Plug-Ins](../../write-plug-in.md)  
[Protokollierung und Ablaufverfolgung](../../logging-tracing.md)
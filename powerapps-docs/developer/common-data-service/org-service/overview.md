---
title: Verwenden der Common Data Service-Organisationsservices (Common Data Service) | Microsoft Docs
description: 'Lesen Sie, wie Sie mithilfe des Common Data Service-Organisationsservice mit Daten und Metadaten arbeiten können.'
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

# <a name="use-the-common-data-service-organization-service"></a>Nutzen des Common Data Service-Organisationsservice

Der Organisationsservice ist eine von zwei Webdiensten, die Sie zum Arbeiten mit Daten und Metadaten in Common Data Service verwenden können. Der andere ist die [Web-API](../webapi/overview.md).

Der Organisationsservice wird für die Verwendung mit dem .NET Framework und den SDK-Assemblys im NuGet-Paket [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/) optimiert, um die Klassen für die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Benutzeroberfläche bereitzustellen, die zum Arbeiten mit Daten und Metadaten unter Verwendung dieses Service erforderlich sind. 

Einige Erweiterungsfunktionen, wie z. B. Plug-Ins und Workflowerweiterungen, sind von dem .NET Framework und den Klassen abhängig, die in diesen Assemblys definiert sind. Deshalb ist der Organisationsservice die einzige Option, wenn diese Methoden zum Erweitern von Common Data Service verwendet werden.

## <a name="organization-service-assemblies"></a>Organisationsserviceassemblys

Es ist wichtig zu wissen, dass der Organisationsservice die Plattform definiert. Der Organisationsservice definiert die unterstützten Vorgänge als Nachrichten. Jede Nachricht hat einen Namen. Diese Meldungen entsprechen den Ereignissen, die vom Ereignisframework ausgegeben werden. Weitere Informationen: [Ereignisframework](../event-framework.md)

Die .NET-Assemblys für den Organisationsservice verwenden derzeit einen SOAP-Endpunkt. Die Assemblys wurden entworfen, um die zugrunde liegenden Plattformdienste basierend auf der <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Benutzeroberfläche genau nachzubilden. Sie sind allerdings keine identischen Komponenten und sollten nicht miteinander verwechselt werden. 

Der SOAP-Endpunkt für den Organisationsservice wurde im Jahre 2011 eingeführt, und wir haben in einer Ankündigung mitgeteilt, dass er veraltet ist. Dies bedeutet, dass er weiterhin funktioniert und unterstützt wird, bis wir ihn entfernen. Wir haben auch angekündigt, dass wir die .NET-SDK-Assemblys aktualisieren werden, sodass sie weiterhin funktionieren werden, nachdem der SOAP-Endpunkt entfernt wird. Dies bedeutet, dass aktualisierte SDK-Assemblys verfügbar sein werden, bevor der SOAP-Endpunkt entfernt wird, und Entwickler müssen ihren Code so aktualisieren, dass er diese neuen Assemblys irgendwann später verwendet.

## <a name="using-the-organization-service-without-assemblies"></a>Verwenden des Organisationsservice ohne Assemblys

Es ist möglich für Entwickler, den SOAP-Endpunkt des Organisationsservice ohne .NET-SDK-Assemblys zu verwenden, z. B. durch Erstellen eines Webdienst-Proxys mittels der WSDL, die durch den Service verfügbar gemacht wird, aber die Web-API ist aufgrund ihrer RESTful-Eigenschaft eine bessere Alternative.

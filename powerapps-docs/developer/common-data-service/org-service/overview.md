---
title: Verwenden des Common Data Service Organization Service (Common Data Service) | Microsoft Docs
description: Lesen Sie, wie Sie mit dem Common Data Service Organization Service mit Daten und Metadaten arbeiten können.
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
ms.openlocfilehash: 2d32c212a3b6c8f95f3de078d6849356ef3853c7
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2748534"
---
# <a name="use-the-common-data-service-organization-service"></a>Verwenden Sie den Common Data Service Organization Service.

Der Organization-Service ist einer von zwei Webservices, mit denen Sie mit Daten und Metadaten in Common Data Service arbeiten können. Der andere ist die [Web-API](../webapi/overview.md).

Der Organisationsservice ist für die Verwendung mit dem.NET Framework optimiert und die SDK-Assemblies im Paket [Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/) NuGet stellen die Klassen für die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Schnittstelle zur Verfügung, die für die Arbeit mit Daten und Metadaten mit diesem Service erforderlich sind. 

Einige Erweiterungsfunktionen, wie Plugins und Workflow-Erweiterungen, hängen vom .NET Framework und den in diesen Assemblies definierten Klassen ab, so dass der Organization Service die einzige Option ist, wenn Sie diese Methoden zur Erweiterung von Common Data Service verwenden.

## <a name="organization-service-assemblies"></a>Organisationsserviceassemblys

Es ist wichtig zu wissen, dass der Organisationsservice die Plattform definiert. Der Organisationsservice definiert die unterstützten Vorgänge als Nachrichten. Jede Nachricht hat einen Namen. Diese Meldungen entsprechen den Ereignissen, die vom Ereignisframework ausgegeben werden. Weitere Informationen: [Ereignisframework](../event-framework.md)

Die .NET-Assemblys für den Organisationsservice verwenden derzeit einen SOAP-Endpunkt. Die Assemblys wurden entworfen, um die zugrunde liegenden Plattformdienste basierend auf der <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Benutzeroberfläche genau nachzubilden. Sie sind allerdings keine identischen Komponenten und sollten nicht miteinander verwechselt werden. 

Der SOAP-Endpunkt für den Organisationsservice wurde im Jahre 2011 eingeführt, und wir haben in einer Ankündigung mitgeteilt, dass er veraltet ist. Dies bedeutet, dass er weiterhin funktioniert und unterstützt wird, bis wir ihn entfernen. Wir haben auch angekündigt, dass wir die .NET-SDK-Assemblys aktualisieren werden, sodass sie weiterhin funktionieren werden, nachdem der SOAP-Endpunkt entfernt wird. Dies bedeutet, dass aktualisierte SDK-Assemblys verfügbar sein werden, bevor der SOAP-Endpunkt entfernt wird, und Entwickler müssen ihren Code so aktualisieren, dass er diese neuen Assemblys irgendwann später verwendet.

## <a name="using-the-organization-service-without-assemblies"></a>Verwenden des Organisationsservice ohne Assemblys

Es ist möglich für Entwickler, den SOAP-Endpunkt des Organisationsservice ohne .NET-SDK-Assemblys zu verwenden, z. B. durch Erstellen eines Webdienst-Proxys mittels der WSDL, die durch den Service verfügbar gemacht wird, aber die Web-API ist aufgrund ihrer RESTful-Eigenschaft eine bessere Alternative.

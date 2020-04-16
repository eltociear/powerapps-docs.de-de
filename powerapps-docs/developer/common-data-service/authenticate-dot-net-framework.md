---
title: Authentifizierung mit .NET Framework-Anwendungen (Common Data Service) | Microsoft-Dokumentation
description: Authentifizierung von .NET Framework-Anwendungen mit Common Data Service
ms.custom: ''
ms.date: 01/25/2019
ms.reviewer: pehecke
ms.service: powerapps
ms.topic: article
author: paulliew
ms.author: jdaly
manager: ryjones
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3cb5256130773472af60fbfbc3b6f062f24db1a5
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3156450"
---
# <a name="authentication-with-net-framework-applications"></a>Authentifizierung mit .NET Framework-Anwendungen

Wenn Sie das.NET Framework verwenden, können Sie Klassen innerhalb des [Xrm.Tooling](/dotnet/api/?view=dynamics-xrmtooling-ce-9)- Namespace verwenden, um sich zu authentifizieren und eine Verbindung zum Organization Service und zur Web API herzustellen.

Mit `Xrm.Tooling`-Klassen können Sie die SDK-Assemblys über die <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Schnittstellenmethoden verwenden. Dies ist der gleiche Programmierstil, der auch von Plug-Ins und Workflow-Aktivitäten verwendet wird, was ihn zu einer Vorgehensweise macht, die Sie überall für.NET Framework-Anwendungen verwenden können.

Verwenden Sie bei den `Xrm.Tooling`-Klassen die <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> Klasse.

> [!NOTE]
> Sie finden möglicherweise älteren Code oder Beispiele mit den grundlegenden <xref:Microsoft.Xrm.Sdk.Client.OrganizationServiceProxy> oder <xref:Microsoft.Xrm.Sdk.WebServiceClient.OrganizationWebProxyClient> Klassen. Diese werden weiterhin unterstützt und sind nicht veraltet, aber wir empfehlen Ihnen, <xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient> für neue.NET Framework Client-Anwendungen zu verwenden.

Die `Xrm.Tooling`-Klassen bieten viele Vorteile, darunter:
- Sie können Verbindungsinformationen über eine Verbindungszeichenfolge definieren.
- Unterstützt sowohl OAuth als auch Office 365 anspruchsbasierte Authentifizierung.
- Thread-Sicherheit für Aktionen, die in einer Multithread-Umgebung ausgeführt werden. 
- Eine allgemeine Windows Presentation Foundation (WPF)-Anmeldungssteuerelement für eine einheitliche Anmeldeumgebung in Ihren Windows-Clientanwendungen.
- Unterstützt die sichere Speicherung der Anmeldeinformationen und die Wiederverwendung der gespeicherten Anmeldeinformationen zur automatischen Anmeldung nach der ersten Anmeldung.
- Integrierte Diagnosenachverfolgung und Leistungsberichte der durchgeführten Aktionen, die Sie entsprechend der Anforderungen Ihres Unternehmens konfigurieren können.
- Support für X.509-Zertifikatsauthentifizierung.

Die `Xrm.Tooling`-Klassen sind für die Verwendung der <xref:Microsoft.Xrm.Sdk.IOrganizationService>-Schnittstellenmethoden optimiert. 

Wenn Sie die Web-API verwenden möchten, können Sie die <xref:Microsoft.Xrm.Tooling.Connector>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient>.<xref:Microsoft.Xrm.Tooling.Connector.CrmServiceClient.ExecuteCrmWebRequest*> verwenden. Methode, um Anfragen über die Web-API mit allen anderen Vorteilen der `Xrm.Tooling`-Klassen zu erstellen, solange Sie OAuth verwenden.

Weitere Informationen: [Erstellen von Windows-Client-Anwendungen mithilfe der XRM-Tools](xrm-tooling/build-windows-client-applications-xrm-tools.md)


## <a name="net-framework-versions"></a>.NET Framework Versionen

Verwenden Sie 4.6.2 .NET Framework oder höher, wenn Client-Anwendungen erstellen. Nur Anwendungen, die Transport Level Security (TLS) 1.2 oder eine bessere Sicherheit verwenden, können eine Verbindung herstellen. TLS 1.2 ist nicht das Standardprotokoll, das von .NET Framework 4.5.2 verwendet wird, aber es ist in .NET Framework 4.6.2.

> [!NOTE]
> **Bekanntes Problem bei Visual Studio 2015**
> 
> Wenn Sie Ihr Projekt/Lösung in VS 2015 im Debug-Modus ausführen, können Sie möglicherweise keine Verbindung herstellen. Dies geschieht unabhängig davon, ob Sie ein Zielframework von 4.6.2 oder höher verwenden. Dies kann auftreten, weil der Visual Studio-Hostingprozess gegen .NET 4.5 kompiliert ist, was bedeutet, dass er standardmäßig TLS 1.2 nicht unterstützt. Sie können den Visual Studio-Hostingprozess als Umgehung deaktivieren. 
>
> Klicken Sie mit der rechten Maustaste auf den Namen Ihres Projekts in Visual Studio und dann auf **Eigenschaften**. Auf der Registerkarte **Debuggen** können Sie die Option **Visual Studio-Hostingprozess aktivieren** deaktivieren. 
>
> Dies wirkt sich nur auf das Debugging-Umgebung in VS 2015 aus. Es hat keinen Einfluss auf die erstellten Binärdateien bzw. ausführbaren Datei. Das gleiche Problem tritt nicht in Visual Studio 2017 auf.

## <a name="net-framework-applications-without-sdk-assemblies"></a>.NET Framework-Anwendungen ohne SDK-Assemblys

Wenn Sie es vorziehen, keine Abhängigkeit zu SDK-Assemblies zu haben, können Sie auch die unter [OAuth mit Common Data Service verwenden](authenticate-oauth.md) beschriebenen Muster für Anwendungen verwenden, ohne von SDK-Assemblies abhängig zu sein. Ohne die SDK-Assemblys können Sie nur die OData Restful Webdienste (Web API und OData Global Discovery Service) verwenden. Die [Beispiele für Web-API-Datenvorgänge (C#)](webapi/web-api-samples-csharp.md) veranschaulichen diese Vorgehensweise.

### <a name="see-also"></a>Siehe auch

[Authentifizierung mit Common Data Service-Webdiensten](authentication.md)<br />
[OAuth mit Common Data Service verwenden](authenticate-oauth.md)


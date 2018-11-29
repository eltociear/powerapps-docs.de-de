---
title: Visual Studio und .NET Framework (Common Data Service für Apps) | Microsoft Docs
description: Erfahren Sie mehr über die Entwicklungstools und Anforderungen für verwalteten Code.
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
# <a name="visual-studio-and-the-net-framework"></a>Visual Studio und .NET Framework

Die .NET SDK-Assemblys für Common Data Service für Apps sind auf der Grundlage von .NET Framework 4.5.2 erstellt. 

Sie können mit Visual Studio Ihre Anwendungen für verwalteten Code mithilfe von .NET Framework 4.5.2 oder höher erstellen. 

> [!IMPORTANT]
> Sie sollten alle benutzerdefinierten Client-Anwendungen mit Microsoft .NET Framework 4.6.2. oder höher erstellen.
> Nur Anwendungen, die Transport Level Security (TLS) 1.2 oder eine bessere Sicherheit verwenden, dürfen eine Verbindung mit CDS für Apps herstellen. TLS 1.2 ist nicht das Standardprotokoll, das von .NET Framework 4.5.2 verwendet wird, aber es ist in .NET Framework 4.6.2.
> 
> Weitere Informationen: [Blogbeitrag: Kommende Updates zu Dynamics 365 Customer Engagement-Verbindungssicherheit](https://blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/)
> 
> [!TIP]
> Wenn Sie .NET Framework 4.6.2 auf dem Entwicklungscomputer installieren, müssen Sie unbedingt das Entwicklerpaket installieren, und nicht nur die Laufzeit. Dadurch kann das 4.6.2-Framework im Dialogfeld **Neues Projekt** von Visual Studio und im Zielframework-Dropdownmenü der Projekteigenschaften ausgewählt werden.  

Sie können eine Visual Studio Community-Edition zu Entwicklungszwecken verwenden. 

[comment]: <> (However, use of extensions isn’t supported in the Express edition so you won’t be able to install useful extensions in that version of Visual Studio)

Weitere Information: [Unterstützung für .NET Framework-Versionen](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET)

Eine vollständige Auflistung unterstützter und nicht unterstützter Entwicklungen finden Sie unter [Unterstützte Erweiterungen für Dynamics 365](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET).

## <a name="see-also"></a>Siehe auch

 [Entwickler-Tools](/dynamics365/customer-engagement/developer/developer-tools)
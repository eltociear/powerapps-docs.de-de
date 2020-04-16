---
title: Visual Studio und .NET Framework (Common Data Service) | Microsoft Docs
description: Erfahren Sie mehr über die Entwicklungstools und Anforderungen für verwalteten Code.
ms.custom: ''
ms.date: 07/03/2019
ms.reviewer: pehecke
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
ms.openlocfilehash: aa37008b56ba88afd0286582d896c8cea5bb1c11
ms.sourcegitcommit: f4cf849070628cf7eeaed6b4d4f08c20dcd02e58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "3155418"
---
# <a name="visual-studio-and-the-net-framework"></a>Visual Studio und .NET Framework

Die .NET SDK-Assemblies für Common Data Service basieren auf dem.NET Framework 4.6.2. 

Sie können mit Visual Studio Ihre Anwendungen für verwalteten Code mithilfe von .NET Framework 4.6.2 oder höher erstellen. 

Plug-Ins und benutzerdefinierte Workflow-Assemblys sollten .NET Framework 4.6.2 verwenden. Während die Assemblys, die spätere Versionen verwenden, im Allgemeinen funktionieren. Wenn sie eine Funktion verwenden, die nach 4.6.2 eingeführt wurde, tritt ein Fehler auf.

> [!IMPORTANT]
> Sie sollten alle benutzerdefinierten Client-Anwendungen mit Microsoft .NET Framework 4.6.2 oder höher erstellen.
> Nur Anwendungen, die die Sicherheit auf Transportebene (TLS) 1.2 oder höher verwenden, dürfen mit Common Data Service verbunden werden. TLS 1.2 ist nicht das Standardprotokoll, das von .NET Framework 4.5.2 verwendet wird, aber es ist in .NET Framework 4.6.2. 
> 
> Mehr Informationen: <https://<blogs.msdn.microsoft.com/crm/2017/09/28/updates-coming-to-dynamics-365-customer-engagement-connection-security/>
> 
> [!TIP]
> Wenn Sie .NET Framework 4.6.2 auf dem Entwicklungscomputer installieren, müssen Sie unbedingt das Entwicklerpaket installieren, und nicht nur die Laufzeit. Dadurch kann das 4.6.2-Framework im Dialogfeld **Neues Projekt** von Visual Studio und im Zielframework-Dropdownmenü der Projekteigenschaften ausgewählt werden.  

Sie können eine Visual Studio Community-Edition zu Entwicklungszwecken verwenden. Die Verwendung von Erweiterungen wird in der Express-Edition aber nicht unterstützt, sodass Sie keine nützlichen Erweiterungen in der Version von Visual Studio installieren können.

Weitere Information: [Unterstützung für .NET Framework-Versionen](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET)

Eine vollständige Auflistung unterstützter und nicht unterstützter Entwicklungen finden Sie unter [Unterstützte Erweiterungen für Dynamics 365](/dynamics365/customer-engagement/developer/supported-extensions#SupportNET).

## <a name="see-also"></a>Siehe auch

 [Entwickler-Tools](/dynamics365/customer-engagement/developer/developer-tools)

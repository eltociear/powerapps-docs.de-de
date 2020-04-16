---
title: Passen Sie Befehle und Menüband an (modellgesteuerte Apps) | Microsoft Docs
description: Befehle werden in Common Data Service in unterschiedlicher Weise abhängig von der Entität und dem Client angezeigt. An den meisten Stellen in der Webanwendung wird eine Befehlsleiste anstelle eines Menübands angezeigt. Dynamics 365 für Tablets verwendet auch Daten, die als Menübänder definiert sind, um zu steuern, welche Befehle auf einer für Toucheingabe optimierten Befehlsleiste verfügbar sind.
keywords: ''
ms.date: 03/27/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 926364b0-ede6-00e9-39d4-5aae5e00be0b
author: Nkrb
ms.author: nabuthuk
manager: shilpas
ms.reviewer: ''
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bf61faabb150e45f80227ed8c776795f2e319d82
ms.sourcegitcommit: be9b8c0f5c7c7e9992e93fa0d03e961b4ac7e3ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "3172569"
---
# <a name="customize-commands-and-the-ribbon"></a>Passen Sie Befehle und das Menüband an

Befehle werden in Common Data Service in unterschiedlicher Weise abhängig von der Entität und dem Client angezeigt. An den meisten Stellen in der Webanwendung wird eine *Befehlsleiste* anstelle eines Menübands angezeigt. Dynamics 365 for Tablets verwendet auch Daten, die als Menübänder definiert sind, um zu steuern, welche Befehle auf einer für Toucheingabe optimierten Befehlsleiste verfügbar sind.  
  
 Die Befehlsleiste bietet verbesserte Leistung. Das Menüband wird weiterhin in der Webanwendung für bestimmte Entitätsformulare angezeigt und für Listenansichten in Dynamics 365 for Outlook verwendet.  
  
 Sowohl die Befehlsleiste wie auch das Menüband verwenden die gleichen XML-Daten, um zu definieren, welche Befehle angezeigt werden, wann sie aktiviert werden und welche Aktionen dadurch ausgeführt werden.  
  
 Die Themen in diesem Abschnitt bieten Ihnen eine Einführung in die wichtigsten Konzepte, deren Verständnis bei der Anpassung der Befehlsleiste oder des Menübands vorausgesetzt wird, sowie in häufige Aufgaben, die Sie dabei ausführen werden.  
  
> [!NOTE]
>  Da das zugrunde liegende XML-Schema für die Anzeige von Befehlen als Menübänder konzipiert wurde, wird der Begriff *Menüband* weiterhin in der Dokumentation verwendet werden.  
  
## <a name="troubleshoot-ribbon-issues"></a>Beheben von Menübandproblemen

Wenn ein Problem mit einer Menüband-Befehlsleistenschaltfläche auftritt, verwenden Sie diese Anleitung zur Fehlerbehebung, um das Problem zu finden und zu beheben: <https://support.microsoft.com/help/4552163>


## <a name="community-tool"></a>Community-Tool
Das SDK beschreibt den Vorgang zum Bearbeiten des Menübands durch direkte Bearbeitung der Datei customization.xml. Sie können auch ein Community-Tool verwenden, [Ribbon Workbench](https://www.develop1.net/public/rwb/ribbonworkbench.aspx), um Menübänder mithilfe der Benutzeroberfläche visuell zu bearbeiten. 

> [!NOTE]
> Microsoft bietet keine Hilfe oder Support für Community-Tools. Um Support oder Hilfe für die Verwendung der Software zu erhalten, setzen Sie sich mit dem Programmherausgeber in Verbindung.  
  
  
## <a name="see-also"></a>Siehe auch  

 [Menüband-Core-Schema](ribbon-core-schema.md)  
 [Menübandtypenschema](ribbon-types-schema.md)  
 [Menüband-WSS-Schema](ribbon-wss-schema.md)<br/> 
 [Beispiel: Exportieren von Menübanddefinitionen](sample-export-ribbon-definitions.md)<br/> 
 [Anwenden von Geschäftslogik mit Client-Skripting in modellgesteuerten Apps](client-scripting.md)

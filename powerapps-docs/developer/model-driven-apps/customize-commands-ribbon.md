---
title: Passen Sie Befehle und Menüband an (modellgesteuerte Apps) | Microsoft Docs
description: Befehle werden in Common Data Service in unterschiedlicher Weise abhängig von der Entität und dem Client angezeigt. An den meisten Stellen in der Web-Anwendung sehen Sie eine Befehlsleiste anstelle eines Menübands. Dynamics 365 für Tablets verwendet auch Daten, die als Menübänder definiert sind, um zu steuern, welche Befehle auf einer für Toucheingabe optimierten Befehlsleiste verfügbar sind.
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
ms.openlocfilehash: 27b041e7a62b76bab7e920deac9a8933accf4fca
ms.sourcegitcommit: 4a88daac42180283314f6bedee3d6810fd5a6c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "3275946"
---
# <a name="customize-commands-and-the-ribbon"></a>Passen Sie Befehle und das Menüband an

Befehle werden in Common Data Service in unterschiedlicher Weise abhängig von der Entität und dem Client angezeigt. An den meisten Stellen in der Web-Anwendung sehen Sie statt eines Menübands eine *Befehlsleiste*. 

Dynamics 365 for Tablets verwendet auch Daten, die als Menübänder definiert sind, um zu steuern, welche Befehle auf einer für Toucheingabe optimierten Befehlsleiste verfügbar sind.  
  
Die Befehlsleiste bietet verbesserte Leistung. Das Menüband wird weiterhin in der Webanwendung für bestimmte Entitätsformulare angezeigt und für Listenansichten in Dynamics 365 for Outlook verwendet.  
  
Sowohl die Befehlsleiste wie auch das Menüband verwenden die gleichen XML-Daten, um zu definieren, welche Befehle angezeigt werden, wann sie aktiviert werden und welche Aktionen dadurch ausgeführt werden.  
  
Die Artikel in diesem Abschnitt führen Sie in Schlüsselkonzepte ein, die Sie verstehen müssen, sowie in allgemeine Aufgaben, die Sie ausführen, wenn Sie die Befehlsleiste oder das Menüband anpassen.  
  
> [!NOTE]
>  Da das zugrunde liegende XML-Schema für die Anzeige von Befehlen als Menübänder konzipiert wurde, wird der Begriff *Menüband* weiterhin in der Dokumentation verwendet werden.  
  
## <a name="troubleshoot-ribbon-issues"></a>Beheben von Menübandproblemen

Wenn bei Ihnen ein Problem mit einer Schaltfläche in der Menüband-Befehlsleiste auftritt, verwenden Sie diesen [Fehlerbehebungsleitfaden](https://support.microsoft.com/help/4552163), um das Problem zu finden und zu lösen.


## <a name="community-tool"></a>Community-Tool
Das SDK beschreibt den Vorgang zum Bearbeiten des Menübands durch direkte Bearbeitung der Datei customization.xml. Sie können auch ein Community-Tool verwenden, [Ribbon Workbench](https://www.develop1.net/public/rwb/ribbonworkbench.aspx), um Menübänder mithilfe der Benutzeroberfläche visuell zu bearbeiten. 

> [!NOTE]
> Microsoft bietet keine Hilfe oder Support für Community-Tools. Um Support oder Hilfe für die Verwendung der Software zu erhalten, setzen Sie sich mit dem Programmherausgeber in Verbindung.  
  
  
## <a name="see-also"></a>Siehe auch  

 [Menüband-Core-Schema](ribbon-core-schema.md)  
 [Menübandtypenschema](ribbon-types-schema.md)  
 [Menüband-WSS-Schema](ribbon-wss-schema.md)<br/> 
 [Beispiel: Exportieren von Menübanddefinitionen](sample-export-ribbon-definitions.md)<br/> 
 [Anwenden von Geschäftslogik mit Client-Skripting in modellgestützten Apps](client-scripting.md)

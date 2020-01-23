---
title: Lösungen aktualisieren| MicrosoftDocs
description: Erfahren Sie, wie eine Lösung aktualisiert wird in Power Apps
ms.custom: ''
ms.date: 09/30/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 534c4d986cec688723e6d3351135bca2692d020f
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914337"
---
# <a name="update-solutions"></a>Lösungen aktualisieren  

Manchmal möchten Sie eine Aktualisierung zu einer vorhandenen verwalteten Lösung installieren. Die Vorgehensweise entspricht dem Installieren einer neuen verwalteten Lösung, mit Ausnahme einiger unterschiedlicher Optionen. Wenn Sie eine Lösung aktualisieren, die Sie von jemand anderem erhalten haben, sollten Sie den Lösungsherausgeber danach fragen, welche Optionen Sie auswählen sollten.  
  
1.  Wählen Sie im linken Navigationsbereich die Option **Lösungen** aus.
  
2.  Wählen Sie in der Lösungsliste die Option **Import** aus.  
  
3.  Navigieren Sie im Dialogfeld **Lösung importieren** , wählen Sie Schritt **Lösungspaket auswählen** und **wählen die Datei**, gehen Sie zur komprimierten Datei (ZIP- oder CAB-Datei), die die Lösung enthält, die Sie updaten möchten.

4.  Wählen Sie **Weiter**.  
  
5.  Zeigen Sie die Informationen zur Lösung an und klicken Sie auf **Weiter**. Diese Seite zeigt einen gelben Balken mit der Meldung **Das Lösungspaket enthält ein Update für eine bereits installierte Lösung** an.  
  
6.  Sie haben die folgenden Optionen:  
  
    - **Anpassungen warten (empfohlen)**  
  
         Mit der Auswahl dieser Option werden alle unverwalteten Anpassungen gewartet, die auf Komponenten ausgeführt wurden. Allerdings werden nicht alle Updates in dieser Lösung angewendet.  
  
    - **Anpassungen überschreiben**  
  
         Diese Option überschreibt nicht verwaltete Anpassungen, die zuvor für Komponenten in dieser Lösung vorgenommen wurden. Alle in dieser Lösung enthaltenen Aktualisierungen werden wirksam.  
  
     Wählen Sie die entsprechende Option, und wählen Sie dann **Weiter**.  
  
7.  Möglicherweise müssen Sie einige Momente beim Lösungsimport warten. Anzeigen der Ergebnisse und wählen Sie dann **Schließen** aus.  
  
 Falls Sie Änderungen importiert haben, die veröffentlicht werden müssen, müssen Sie Anpassungen veröffentlichen, bevor diese verfügbar sind. 
  
 Lösungsherausgeber können Sie auffordern, Ihre vorhandenen nicht verwalteten Anpassungen zu exportieren, ihre verwaltete Lösung mit der Option zum Überschreiben von Anpassungen zu aktualisieren, und dann Ihre nicht verwalteten Anpassungen erneut zu importieren. Dadurch wird sichergestellt, dass die erwarteten Änderungen vorgenommen und Ihre Anpassungen beibehalten werden.  
  
<a name="BKMK_ExportSolutions"></a>   

### <a name="see-also"></a>Siehe auch
[Exportieren von Lösungen](export-solutions.md) <br />
[Lösungen und Patches verteilen](use-segmented-solutions-patches-simplify-updates.md) <br />
[Lösung importieren](import-update-export-solutions.md)
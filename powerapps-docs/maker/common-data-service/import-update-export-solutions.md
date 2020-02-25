---
title: Lösungen importieren | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Lösung in Power Apps importiert wird
ms.custom: ''
ms.date: 01/30/2020
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
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 504e66801c122810da12810d9b19e5069136f7d6
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017619"
---
# <a name="import-solutions"></a>Lösung importieren 

 Sie können Lösungen mithilfe der unten angegebenen Schritte manuell importieren. Importieren Sie nur Lösungen, die von einer vertrauenswürdigen Quelle stammen. Anpassungen können Code enthalten, durch den Daten an externe Quellen gesendet werden.   
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an und wählen Sie **Lösungen** in der linken Navigation.  
  
2.  Wählen Sie in der Befehlsleiste **Importieren**.  

    > [!div class="mx-imgBorder"]  
    > ![Importieren einer Lösung](media/solution-import.png "Importieren einer Lösung") 
  
3.  Auf der Seite **Lösungspaket auswählen** wählen Sie komprimierte Datei (.ZIP oder .CAB) **suchen**, die die Lösung enthält, die Sie importieren möchten. 
  
4.  Wählen Sie **Weiter**.  
  
5.  Informationen darüber, wie die Lösung angezeigt wird. Klicken Sie auf **Importieren**.  
  
6. Möglicherweise müssen Sie einige Momente beim Lösungsimport warten. Anzeigen der Ergebnisse und wählen Sie dann **Schließen** aus.  
  
 Falls Sie Änderungen importiert haben, die veröffentlicht werden müssen, müssen Sie Anpassungen veröffentlichen, bevor diese verfügbar sind. 
  
 Wenn der Import nicht erfolgreich ist, sehen Sie einen Bericht mit allen Fehlern oder Warnhinweisen, die erfasst wurden. Wählen Sie **Protokolldatei herunterladen**, um Informationen zu den Gründen für das Fehlschlagen des Imports zu geben. Die häufigste Ursache für das Fehlschlagen eines Lösungsimports besteht darin, dass die Lösung einige erforderliche Lösungskomponenten nicht vollständig enthielt..  
  
 Wenn Sie die Protokolldatei herunterladen, sehen Sie eine XML-Datei, die Sie mit Office Excel öffnen können, um ihre Inhalte anzuzeigen.  
  
> [!NOTE]
>  Sie können einen aktiven Weiterleitungsregelsatz nicht bearbeiten. Wenn Sie eine Lösung, die einen aktiven Weiterleitungsregelsatz umfasst, in eine Organisation importieren, in der in der Regel mit derselben ID vorhanden ist, schlägt der Lösungsimport fehl. Weitere Informationen: [Regeln erstellen, um Anfragen automatisch weiterzuleiten](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

### <a name="see-also"></a>Siehe auch
[Lösungen aktualisieren](update-solutions.md) <br />
[Exportieren von Lösungen](export-solutions.md)


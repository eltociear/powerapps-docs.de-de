---
title: Lösungen importieren | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Lösung in Power Apps importiert wird
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
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0eb65eb9ac1240769ba0cc885cb9c2e30a8f83f9
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909458"
---
# <a name="import-solutions"></a>Lösung importieren 

 Sie können Lösungen mithilfe der unten angegebenen Schritte manuell importieren. Importieren Sie nur Lösungen, die von einer vertrauenswürdigen Quelle stammen. Anpassungen können Code enthalten, durch den Daten an externe Quellen gesendet werden.   
  
1.  Wählen Sie im linken Navigationsbereich die Option **Lösungen** aus.  
  
2.  Wählen Sie in der Lösungsliste die Option **Import** aus.  

    > [!div class="mx-imgBorder"]  
    > ![Importieren einer Lösung](media/solution-import.png "Importieren einer Lösung") 
  
3.  Navigieren Sie im Dialogfeld **Lösung importieren** , wählen Sie Schritt **Lösungspaket auswählen** und **wählen die Datei**, gehen Sie zur komprimierten Datei (ZIP- oder CAB-Datei), die die Lösung enthält, die Sie importieren möchten. 
  
4.  Wählen Sie **Weiter**.  
  
5.  Informationen über eine vorgeschlagene Lösung anzeigen. Klicken Sie auf **Importieren**.  
  
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


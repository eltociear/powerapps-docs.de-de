---
title: Exportieren von Daten nach Excel Online in einer modellgesteuerten App | Microsoft Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 6cb8fe650db464f41c63af87c3fcb34bb2203cf2
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544777"
---
# <a name="export-your-data-to-excel-online"></a>Exportieren von Daten nach Excel Online 

Sie können schnell eine Ad-hoc-Analyse Ihrer Daten in Ihrer App durchführen, indem Sie die Daten aus der App nach Excel Online exportieren.
  
Wenn Sie Änderungen an den Daten in Excel Online vornehmen, können Sie die aktualisierten Informationen in der App speichern. Denken Sie daran, das vorhandene Format der Excel-Zellen beizubehalten, um Probleme beim Importieren zu vermeiden. Alle Informationen, die der Tabelle hinzugefügt werden, z. B. Grafiken, Diagramme oder Farben, werden nicht gespeichert.  
  
## <a name="prerequisites"></a>Voraussetzungen  
  
- Dieses Feature erfordert, dass Sie über ein Office 365-Abonnement oder ein Abonnement für einen Onlinedienst wie SharePoint Online oder Exchange Online verfügen.
  
- Sie benötigen ein Microsoft-Konto.    
  
## <a name="open-app-data-in-excel-online"></a>Öffnen von App-Daten in Excel Online  

Die Option zum Öffnen von Daten in Excel Online ist nicht für alle Datensatztypen verfügbar. Wenn die Option nicht angezeigt wird, ist sie für diesen Datensatz nicht verfügbar.  
  
> [!NOTE]
> Aktualisierte Daten in einer App werden nicht sofort in Excel Online angezeigt, wenn dieselbe Ansicht in den letzten zwei Minuten in Excel Online geöffnet wurde. Nach diesem Zeitraum sollten alle aktualisierten Daten in Excel Online angezeigt werden.
  
Wenn Sie eine Liste der Datensätze in einer App öffnen möchten, wählen Sie in der Befehlsleiste das Menü **Nach Excel exportieren** und dann **In Excel Online öffnen** aus. 

> [!div class="mx-imgBorder"] 
> ![Nach Excel Online exportieren](media/exportexcelonline.png "Nach Excel Online exportieren")  

  
## <a name="save-your-data-and-import-it-back-to-the-app"></a>Speichern Sie Ihre Daten, und importieren Sie sie zurück in die App.  
  
1. Nachdem Sie die Änderungen vorgenommen haben, wählen Sie **Speichern** aus.  
  
   > [!NOTE]
   > - Die Daten für *Ad-hoc-Analysen* mit Excel Online werden temporär gespeichert. Ergänzungen, wie z B. Diagramme, Berechnungen und Spalten, werden nicht aus der Ad-hoc-Analyse in Excel Online in der App gespeichert.  
   > 
   > - Der Dateiimport schlägt möglicherweise fehl, wenn Sie viele Änderungen vornehmen. Wenn Sie viele Änderungen an den Daten vornehmen und diese zurück in die App importieren müssen, empfiehlt es sich, stattdessen das Arbeitsblatt in Excel zu exportieren.  
   > 
   > - Es ist in Excel Online nicht möglich, den Vorgang „**Datei** > **Speichern unter**“ durchzuführen. Wenn Sie dies tun, erhalten Sie eine Fehlermeldung, dass **die Arbeitsmappe nicht gespeichert werden kann**.   
2. Wählen Sie im Dialogfeld **Daten für Import übermittelt** die Option **Schließen** aus.  
  

  

 

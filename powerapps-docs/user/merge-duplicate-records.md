---
title: Doppelte Datensätze zusammenführen | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/25/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5a14662d25a7c2dda79f2399b863b959f9f70cc5
ms.sourcegitcommit: 79ac9decef3d5aab40fbf3bc95f8f4ba03f9b3df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2019
ms.locfileid: "72959322"
---
# <a name="merge-duplicate-records"></a>Zusammenführen doppelter Datensätze 

Doppelte Datensätze können in Ihre Daten importiert werden, wenn Sie oder andere Daten manuell eingeben oder Datenmassen importieren. Mit Common Data Service können Sie mögliche Duplikate adressieren, indem Sie eine Duplikaterkennung für Konten und Kontakte bereitstellen. Ihr Administrator kann auch doppelte Erkennungsregeln für andere Situationen einrichten.  
  
Angenommen, Sie geben einen Kontaktdaten Satz, Jim Glynn, und eine Mobiltelefonnummer ein.  Die Regel für die doppelte Erkennung ermittelt, dass Sie bereits über einen ähnlichen Datensatz verfügen, und zeigt dieses Dialogfeld an.  
  
 > [!div class="mx-imgBorder"] 
 > ![Doppelter Kontaktdaten Satz wurde ermittelt.](media/duplicates-detected.png "Doppelter Kontaktdaten Satz wurde ermittelt.")  
  
 Sie sind nicht sicher, ob es sich um einen neuen Datensatz handelt (einer, der den gleichen Namen wie ein vorhandener Kontakt hat) oder ein Duplikat. Wählen Sie daher **ignorieren und speichern**aus.  
  
 Navigieren Sie als nächstes zur Liste **alle Kontakte** , und sehen Sie, dass Sie nun über zwei Datensätze mit demselben Namen verfügen. Nachdem Sie die Datensätze überprüft haben, stellen Sie fest, dass Sie Duplikate sind, die zusammengeführt werden müssen.  
 
 > [!div class="mx-imgBorder"] 
 > ![Doppelter Kontaktdaten Satz wurde ermittelt.](media/duplicates-detected_1.png "Doppelter Kontaktdaten Satz wurde ermittelt.")  
 
Common Data Service umfasst doppelte Erkennungsregeln für Konten und Kontakte. Diese Regeln werden automatisch aktiviert. Sie müssen also nichts tun, um die Duplikaterkennung für diese Daten Satz Typen einzurichten.  
  
> [!NOTE]
>  Wenn Sie auf Ihrem System verfügbar sind, können Sie zusätzlich zu Kontakten und Konten auch nach Duplikaten anderer Daten Satz Typen suchen. Wenden Sie sich an den Systemadministrator. [Suchen Sie nach Ihrem Administrator oder Supportmitarbeiter](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>Zusammenführen doppelter Datensätze  
  
1. Wählen Sie die doppelten Datensätze aus, und klicken Sie auf zusammen **führen**.  
  
   > [!div class="mx-imgBorder"] 
   > ![Doppelter Kontaktdaten Satz wurde ermittelt.](media/duplicates-detected_2.png "Doppelter Kontaktdaten Satz wurde ermittelt.")  
  
2. Wählen Sie im Dialogfeld **Datensätze zusammenführen** den Master Daten Satz (der, den Sie behalten möchten) aus, und wählen Sie dann alle Felder im neuen Datensatz aus, die Sie mit dem Master Daten Satz zusammenführen möchten. Die Daten in diesen Feldern können die vorhandenen Daten im Master Daten Satz überschreiben. Wählen Sie **OK** aus.  
  
     
   > [!div class="mx-imgBorder"] 
   > ![Dialog Feld zum Zusammenführen von Datensätzen](media/merge-records-dialog.png "Dialog Feld zum Zusammenführen von Datensätzen")  
  
> [!NOTE]
>  Es gibt einige Situationen, in denen Duplikate gefunden werden können:  
> 
> - Wenn ein Datensatz erstellt oder aktualisiert wird.  
>   - Wenn Sie Dynamics 365 für Outlook verwenden und Sie von offline zu Online wechseln.  
>   - Beim Importieren von Daten mithilfe des Datenimport-Assistenten.  
> 
>   Duplikate werden beim Zusammenführen von Datensätzen, Speichern einer Aktivität als abgeschlossen oder Ändern des Status eines Datensatzes (z. b. Aktivieren oder erneutes Aktivieren eines Datensatzes) nicht erkannt.  

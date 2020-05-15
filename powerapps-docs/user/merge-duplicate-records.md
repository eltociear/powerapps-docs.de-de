---
title: Zusammenführen doppelter Datensätze | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c0811645429c9f1e7570ceeaf316a5217e440ae4
ms.sourcegitcommit: bee698ca0d11524377b67813a65e1a022d08c05e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "3302631"
---
# <a name="merge-duplicate-records"></a>Zusammenführen doppelter Datensätze 

Wenn Sie oder andere Personen Daten manuell eingeben oder im Massenvorgang importieren, kann es zu doppelten Datensätzen kommen. Common Data Service unterstützt Sie beim Erkennen potenzieller Duplikate mithilfe von Duplikaterkennung für aktive Datensätze wie Firmen und Kontakte. Wenn Sie einen Datensatz zusammenführen, werden auch alle zugehörigen oder untergeordneten Datensätze zusammengeführt. Der Administrator kann auch Duplikaterkennungsregeln für andere Situationen einrichten.  
  
So können Sie beispielsweise einen Kontaktdatensatz, Cosimo Meller, zusammen mit einer Mobiltelefonnummer eingeben.  Die Regel zur Duplikaterkennung ermittelt, ob Sie bereits über einen ähnlichen Datensatz verfügen, und zeigt das folgende Dialogfeld an:  
  
 > [!div class="mx-imgBorder"] 
 > ![Doppelter Kontaktdatensatz erkannt](media/duplicates-detected.png "Doppelter Kontaktdatensatz erkannt")  
  
 Da Sie nicht genau wissen, ob es sich um einen neuen Datensatz (der zufällig den gleichen Namen hat wie ein vorhandener Kontakt ) oder um ein Duplikat handelt, wählen Sie **Ignorieren und speichern** aus.  
  
 Wechseln Sie als Nächstes zur Liste **Alle Kontakte**. Dort sehen Sie, dass Sie nun über zwei Datensätze mit demselben Namen verfügen. Nachdem Sie die Datensätze überprüft haben, stellen Sie fest, dass es sich um Duplikate handelt, die zusammengeführt werden müssen.  
 
 > [!div class="mx-imgBorder"] 
 > ![Doppelter Kontaktdatensatz erkannt](media/duplicates-detected_1.png "Doppelter Kontaktdatensatz erkannt")  
 
Common Data Service enthält Duplikaterkennungsregeln für Firmen und Kontakte. Diese Regeln werden automatisch aktiviert. Sie müssen also keine weiteren Schritte ausführen, um die Duplikaterkennung für diese Datensatztypen einzurichten.  
  
> [!NOTE]
>  Wenn dies für Ihr System verfügbar ist, können Sie auch prüfen, ob neben Kontakt- und Kontoduplikaten auch Duplikate anderer Datensatztypen vorhanden sind. Wenden Sie sich hierfür an den Systemadministrator. [Suchen Sie nach Ihrem Administrator oder Supportmitarbeiter](find-admin.md).  
  
## <a name="merge-duplicate-records"></a>Zusammenführen doppelter Datensätze  
  
1. Wählen Sie die doppelten Datensätze und wählen dann **Zusammenführen** aus.  
  
   > [!div class="mx-imgBorder"] 
   > ![Doppelter Kontaktdatensatz erkannt](media/duplicates-detected_2.png "Doppelter Kontaktdatensatz erkannt")  
  
2. Im Dialogfeld **Datensätze zusammenführen** wählen Sie den Masterdatensatz (der, den Sie behalten möchten) aus, und wählen Sie dann alle Felder des neuen Datensatzes aus, die im Masterdatensatz zusammengeführt werden sollen. Die Daten in diesen Feldern überschreiben unter Umständen die vorhandenen Daten im Masterdatensatz. Wählen Sie **OK** aus.  
  
     
   > [!div class="mx-imgBorder"] 
   > ![Dialogfeld zum Zusammenführen von Datensätzen](media/merge-records-dialog.png "Dialogfeld zum Zusammenführen von Datensätzen")  
  
> [!NOTE]
>  Duplikate können in verschiedenen Situationen auftreten:  
> 
> - Beim Erstellen oder Aktualisieren eines Datensatzes.  
>   - Wenn Sie Dynamics 365 for Outlook verwenden und vom Offline- in den Onlinemodus wechseln.  
>   - Wenn Sie Daten mit dem Datenimport-Assistenten importieren  
> 
>   Duplikate werden nicht erkannt, wenn Sie Datensätze zusammenführen, eine Aktivität als abgeschlossen speichern oder den Status eines Datensatzes ändern und ihn beispielsweise aktivieren oder reaktivieren.  

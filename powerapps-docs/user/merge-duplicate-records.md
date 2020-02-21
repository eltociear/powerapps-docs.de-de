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
ms.locfileid: "73609883"
---
# <a name="merge-duplicate-records"></a>Zusammenführen doppelter Datensätze 

Wenn Sie oder andere Personen Daten manuell eingeben oder im Massenvorgang importieren, kann es zu doppelten Datensätzen kommen. Mit Common Data Service können Sie eventuelle Duplikate vermeiden, indem Sie eine Duplikaterkennung für aktive Datensätze wie Konten und Kontakte bereitstellen. Wenn Sie einen Datensatz zusammenführen, werden auch alle zugehörigen oder untergeordneten Datensätze zusammengeführt. Ihr Administrator kann Regeln zur Duplikaterkennung auch für andere Situationen einrichten.  
  
Angenommen, Sie geben den Kontaktdatensatz Jim Glynn und eine Mobiltelefonnummer ein.  Die Regel zur Duplikaterkennung ermittelt, ob Sie bereits über einen ähnlichen Datensatz verfügen, und zeigt das folgende Dialogfeld an:  
  
 > [!div class="mx-imgBorder"] 
 > ![Doppelter Kontaktdatensatz erkannt](media/duplicates-detected.png "Doppelter Kontaktdatensatz erkannt")  
  
 Da Sie nicht genau wissen, ob es sich um einen neuen Datensatz (der zufällig den gleichen Namen hat wie ein vorhandener Kontakt ) oder um ein Duplikat handelt, wählen Sie **Ignorieren und speichern** aus.  
  
 Wechseln Sie als Nächstes zur Liste **Alle Kontakte**. Dort sehen Sie, dass Sie nun über zwei Datensätze mit demselben Namen verfügen. Nachdem Sie die Datensätze überprüft haben, stellen Sie fest, dass es sich um Duplikate handelt, die zusammengeführt werden müssen.  
 
 > [!div class="mx-imgBorder"] 
 > ![Doppelter Kontaktdatensatz erkannt](media/duplicates-detected_1.png "Doppelter Kontaktdatensatz erkannt")  
 
Common Data Service umfasst Regeln zur Duplikaterkennung für Konten und Kontakte. Diese Regeln werden automatisch aktiviert. Sie müssen also keine weiteren Schritte ausführen, um die Duplikaterkennung für diese Datensatztypen einzurichten.  
  
> [!NOTE]
>  Wenn dies für Ihr System verfügbar ist, können Sie auch prüfen, ob neben Kontakt- und Kontoduplikaten auch Duplikate anderer Datensatztypen vorhanden sind. Wenden Sie sich hierfür an den Systemadministrator. [Suchen Sie nach Ihrem Administrator oder Supportmitarbeiter](find-admin.md).  
  
## <a name="merge-duplicate-records"></a>Zusammenführen doppelter Datensätze  
  
1. Wählen Sie die doppelten Datensätze und wählen dann **Zusammenführen** aus.  
  
   > [!div class="mx-imgBorder"] 
   > ![Doppelter Kontaktdatensatz erkannt](media/duplicates-detected_2.png "Doppelter Kontaktdatensatz erkannt")  
  
2. Wählen Sie im Dialogfeld **Datensätze zusammenführen** den Masterdatensatz aus, den Sie beibehalten möchten, und wählen Sie anschließend alle Felder im neuen Datensatz aus, die Sie im Masterdatensatz zusammenführen möchten. Die Daten in diesen Feldern überschreiben unter Umständen die vorhandenen Daten im Masterdatensatz. Wählen Sie **OK** aus.  
  
     
   > [!div class="mx-imgBorder"] 
   > ![Dialogfeld zum Zusammenführen von Datensätzen](media/merge-records-dialog.png "Dialogfeld zum Zusammenführen von Datensätzen")  
  
> [!NOTE]
>  Duplikate können in verschiedenen Situationen auftreten:  
> 
> - Wenn ein Datensatz erstellt oder aktualisiert wird  
>   - Wenn Sie Dynamics 365 für Outlook verwenden und von offline zu online wechseln  
>   - Wenn Sie Daten mit dem Datenimport-Assistenten importieren  
> 
>   Duplikate werden nicht erkannt, wenn Sie Datensätze zusammenführen, eine Aktivität als abgeschlossen speichern oder den Status eines Datensatzes ändern und ihn beispielsweise aktivieren oder reaktivieren.  

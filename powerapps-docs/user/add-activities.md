---
title: Hinzufügen einer Termin-, E-Mail-, Telefonanruf-, Notiz- oder Aufgabenaktivität zur Zeitachse in einer modellgesteuerten App | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/26/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 308e36938c673a5f6ba83be02591a7199af20432
ms.sourcegitcommit: 4db9c763455d141a7e1dd569a50c86bd9e50ebf0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "56444430"
---
# <a name="add-an-appointment-email-phone-call-note-or-task-activity-to-the-timeline"></a>Hinzufügen einer Termin-, E-Mail-, Telefonanruf-, Notiz- oder Aufgabenaktivität zur Zeitachse 

Fügen Sie **Aktivitäten** der Pinnwand **Zeitachse** hinzu, um den Überblick über Ihre gesamte Kommunikation mit einem Kunden oder Kontakt zu behalten. Sie können z.B. Notizen erstellen, Beiträge und eine Aufgabe hinzufügen, E-Mails senden, Details zu Telefonaten hinzufügen oder Termine ausmachen. Das System versieht jede Aktivität automatisch mit einem Zeitstempel und zeigt an, wer sie angelegt hat. Sie und andere Mitglieder Ihres Teams können durch die Aktivitäten scrollen, um den Verlauf der Zusammenarbeit mit einem Kunden einzusehen. 

- Aktivitäten, die Sie innerhalb eines Datensatzes hinzufügen, werden auf der Pinnwand **Zeitachse** des Datensatzes angezeigt. 
- Wenn das Feld **Bezug** einer Aktivität festgelegt ist, wird die Aktivität in dem Datensatz angezeigt, dem sie zugeordnet ist. 
- Sie können auch im Filterbereich die Aktivitäten nach Datensatztyp und Datum filtern. 
- Wenn eine neue Aktivität erstellt wird, erhalten Sie auf der Pinnwand **Zeitachse** eine Benachrichtigung des Typs **Was Sie verpasst haben**.

  > [!div class="mx-imgBorder"]
  > ![Zeitachsenansicht von Aktivitäten in PowerApps](media/TimelineViewOfActivity.png "Zeitachsenansicht von Aktivitäten in PowerApps")  
 
## <a name="add-an-activity-from-the-nav-bar"></a>Hinzufügen einer Aktivität über die Navigationsleiste
 
Der schnellste Weg, eine Aktivität hinzuzufügen, ist das Verwenden der Verknüpfung auf der Navigationsleiste, die einem Datensatz zugeordnet wird. Sie können beispielsweise eine Telefonanrufaktivität erstellen und diese dann über das Feld **Bezug** einem Kontakt im System zuordnen.

1. Klicken Sie auf der Navigationsleiste auf das **Pluszeichen** ![Schaltfläche „Datensatz erstellen“](media/create-record-button.png "Schaltfläche „Datensatz erstellen“"), und wählen Sie dann **Aktivitäten** aus. 

   > [!div class="mx-imgBorder"]
   > ![Verknüpfung zum Hinzufügen einer Aktivität in PowerApps](media/QuickCreate.png "Verknüpfung zum Hinzufügen einer Aktivität in PowerApps")  
 
2. Wählen Sie den Typ der Aktivität, die Sie hinzufügen möchten.

3. Geben Sie die erforderlichen Informationen ein. Verwenden Sie das Feld **Bezug**, um die Aktivität einem Datensatz zuzuordnen.

4. Klicken Sie abschließend auf **Speichern**.

 
## <a name="add-a-phone-call"></a>Hinzufügen eines Telefonanrufs  
  
1. Öffnen Sie den Datensatz, dem die Aktivität hinzugefügt werden soll. Öffnen Sie z.B. einen Kontaktdatensatz.
  
2. Klicken Sie auf der Pinnwand **Zeitachse** auf **Pluszeichen** > **Telefonanruf**. 


   > [!div class="mx-imgBorder"]
   > ![Hinzufügen einer Telefonaktivität in PowerApps](media/addphonecall.png "Hinzufügen einer Telefonaktivität in PowerApps")
  
3. Geben Sie den **Betreff** des Anrufs ein.

     Geben Sie im Bereich **Notizen** eine Zusammenfassung des Gesprächs mit dem Kunden ein. 
  
     Das Feld **Anrufen** wird automatisch mit dem Datensatz aufgefüllt, dem Sie die Telefonanrufaktivität hinzugefügt haben. Sie können bei Bedarf einen anderen Datensatz auswählen.  
  
4. Die Richtung ist standardmäßig auf **Ausgehend** festgelegt. Sie können sie in **Eingehend** ändern, indem Sie **Ausgehend** auswählen. 
  
5. Wenn Sie mit dem Ausfüllen des Formulars fertig sind, klicken Sie auf **Speichern**, um die Aktivität zu speichern.  
  
## <a name="add-a-task"></a>Hinzufügen einer Aufgabe  
  
1. Öffnen Sie den Datensatz, dem die Aktivität hinzugefügt werden soll. Öffnen Sie z.B. einen Kontaktdatensatz.
  
2. Klicken Sie auf der Pinnwand **Zeitachse** auf **Pluszeichen** > **Aufgabe**.
  
3. Das Feld **Besitzer** ist standardmäßig auf den aktuellen Benutzer festgelegt. Wenn Sie die Aufgabe neu zuweisen möchten, klicken Sie auf das Nachschlagesymbol, und wählen Sie dann einen anderen Benutzer oder ein anderes Team aus.  
  
4. Wenn Sie mit dem Ausfüllen des Formulars fertig sind, klicken Sie auf **Speichern**, um die Aktivität zu speichern. 
  
## <a name="add-an-email"></a>Hinzufügen einer E-Mail-Adresse  

Um eine E-Mail-Aktivität zu einem Datensatz hinzuzufügen, müssen Sie zuerst den Datensatz speichern, dem Sie die Aktivität hinzufügen.  
  
1. Öffnen Sie den Datensatz, dem die Aktivität hinzugefügt werden soll. Öffnen Sie z.B. einen Kontaktdatensatz.
  
2. Klicken Sie auf der Pinnwand **Zeitachse** auf **Pluszeichen** > **E-Mail**. 

3. Füllen Sie den Betreff der E-Mail aus, und nutzen Sie den dafür vorgesehenen Bereich, um die E-Mail zu schreiben.
  
4. Um eine Anlage an die E-Mail anzufügen, speichern Sie die E-Mail. Klicken Sie dann im Abschnitt **Anlagen** auf **+**, um eine Anlage hinzuzufügen.  
  
5. Um eine Vorlage für den E-Mail-Text zu verwenden, klicken Sie auf der Befehlsleiste auf **Vorlage einfügen**, und wählen Sie dann die Vorlage aus.   
  
6. Wenn Sie mit dem Ausfüllen des Formulars fertig sind, klicken Sie auf **Senden**. 
  
## <a name="add-an-appointment"></a>Hinzufügen eines Termins  

Um eine Terminaktivität zu einem Datensatz hinzuzufügen, müssen Sie zuerst den Datensatz speichern, dem Sie die Aktivität hinzufügen.  
  
1. Öffnen Sie den Datensatz, dem die Aktivität hinzugefügt werden soll. Öffnen Sie z.B. einen Kontaktdatensatz.
  
2. Klicken Sie auf der Pinnwand **Zeitachse** auf **Pluszeichen** > **Termin**.  
  
3. Verwenden Sie die QuickInfos, um die erforderlichen Informationen einzugeben.
  
4. Wenn Sie mit dem Ausfüllen des Formulars fertig sind, klicken Sie auf **Speichern**, um den Termin zu speichern.

## <a name="add-notes"></a>Hinzufügen von Notizen

Sie können im Aktivitätsbereich auch ganz einfach Notizen hinzufügen.
  
1. Öffnen Sie den Datensatz, dem die Aktivität hinzugefügt werden soll. Öffnen Sie z.B. einen Kontaktdatensatz.
  
2. Beginnen Sie auf der Pinnwand **Zeitachse** mit der Eingabe Ihrer Notizen. Klicken Sie auf **Anlage hinzufügen**, um der Notiz Anlagen hinzuzufügen.

3. Wenn Sie mit dem Ausfüllen des Formulars fertig sind, klicken Sie auf **Notiz hinzufügen**, um die Notiz zu speichern.

   > [!div class="mx-imgBorder"]
   > ![Hinzufügen einer Notiz](media/addnote.png "Hinzufügen einer Notiz")

Nachdem die Notiz hinzugefügt wurde, können Sie sie löschen oder bearbeiten. Sie können eine Notiz hinzufügen, indem Sie im oberen Abschnitt der Pinnwand **Zeitachse** auf das **Pluszeichen** klicken.


> [!div class="mx-imgBorder"]
> ![Aktualisieren einer Notiz](media/addnote2.png "Aktualisieren einer Notiz")

## <a name="add-a-post"></a>Hinzufügen eines Beitrags 

1. Öffnen Sie den Datensatz, dem ein Beitrag hinzugefügt werden soll. Öffnen Sie z.B. einen Kontaktdatensatz.

2. Klicken Sie auf der Pinnwand **Zeitachse** auf **Pluszeichen** > **Beitrag**. 

3. Geben Sie Ihren Beitrag in das Textfeld ein. 

4. Wenn Sie mit dem Ausfüllen des Formulars fertig sind, klicken Sie auf **Hinzufügen**, um den Beitrag zu speichern.

> [!div class="mx-imgBorder"]
> ![Aktualisieren eines Beitrags](media/post.png "Aktualisieren eines Beitrags")
  
  Nachdem Sie den Beitrag gespeichert haben, wird er am oberen Rand der Pinnwand „Zeitachse“ angezeigt.
  
## <a name="refresh-the-timeline"></a>Aktualisieren der Zeitachse 

Sie können die Pinnwand „Zeitachse“ aktualisieren, damit die neuesten Informationen angezeigt werden.

Klicken Sie auf der Pinnwand **Zeitachse** auf die ![Schaltfläche „Mehr“ ](media/MoreButton.png "Schaltfläche „Mehr“") und dann auf **Zeitachse aktualisieren**.

> [!div class="mx-imgBorder"]
> ![Aktualisieren der Zeitachse](media/refresh.png "Aktualisieren der Zeitachse")


## <a name="use-the-filter-pane"></a>Verwenden des Filterbereichs

Sie können Aktivitäten, Notizen oder Beiträge auf der Pinnwand „Zeitachse“ mithilfe des Filterbereichs schnell nach Datensatz- oder Aktivitätstyp und Datum filtern.

1. Klicken Sie auf der Pinnwand **Zeitachse** auf die ![Schaltfläche „Mehr“ ](media/MoreButton.png "Schaltfläche „Mehr“") und dann auf **Filterbereich öffnen**.

> [!div class="mx-imgBorder"]
> ![Filterbereich auf der Zeitachse](media/filterpane.png "Filterbereich auf der Zeitachse")

2. Klicken Sie nach dem Anzeigen der gefilterten Informationen auf das Trichtersymbol **Alle Filter löschen**, um den Filter zu löschen. Dadurch wird der Filter zurückgesetzt, sodass alle Informationen auf der Pinnwand „Zeitachse“ angezeigt werden.

> [!div class="mx-imgBorder"]
> ![Zurücksetzen des Filters](media/resetfilter.png "Zurücksetzen des Filters")

## <a name="manage-activities"></a>Verwalten von Aktivitäten
Sie können Aktivitäten direkt auf der Zeitachse verwalten, z.B. eine Aktivität einer anderen Person zuordnen, eine Aktivität löschen oder schließen, eine Aktivität zu einer Warteschlange hinzufügen, einen zugehörigen Datensatz öffnen oder Notizen und Beiträge bearbeiten.


> [!div class="mx-imgBorder"]
> ![Manage Activities.png](media/ManageActivities.png "ManageActivities.png")




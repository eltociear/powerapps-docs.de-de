---
title: Deaktivieren des automatischen Speicherns in einer modellgesteuerten App mit PowerApps | MicrosoftDocs
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: 2e7f75dd-7a3f-4716-b995-b626929c0501
caps.latest.revision: 14
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="disable-auto-save-in-a-model-driven-app"></a>Deaktivieren des automatischen Speicherns in einer modellgesteuerten App

Die automatische Speicherung hilft App-Benutzern, sich auf ihre Arbeit zu konzentrieren, ohne dass sie sich um die Speicherung von Daten in dem Formular kümmern müssen. Die meisten Benutzer schätzen es sehr, nicht bei jeder Aktualisierung eines Datensatzes ausdrücklich die Daten speichern zu müssen, manche Organisationen haben jedoch Anpassungen, die genau dies verlangen. Für solche Organisationen stehen Optionen zur Verfügung, um die automatische Speicherung zu verwalten.  
  
<a name="BKMK_HowAutoSaveWorks"></a>   

## <a name="how-auto-save-works"></a>Wie die automatische Speicherung funktioniert  
 Standardmäßig ist für alle Hauptformulare für [aktualisierte Entitäten und klassische Entitäten](create-design-forms.md#updated-versus-classic-entities) die automatische Speicherung aktiviert. Nachdem ein Datensatz erstellt (zum ersten Mal gespeichert) wurde, werden alle Änderungen an einem Formular automatisch dreißig Sekunden nach der Änderung gespeichert. Wenn keine Änderungen im Formular vorgenommen werden, wird die automatische Speichern nicht durchgeführt, solange das Formular geöffnet ist. Nachdem eine Änderung vorgenommen wurde, beginnt der 30-Sekunden-Zeitraum vor der nächsten automatischen Speicherung erneut. Das Feld, das gerade bearbeitet wird, ist von der automatischen Speicherung ausgeschlossen. Wenn ein anderer Benutzer den gleichen Datensatz aktualisiert hat, während Sie ihn bearbeiten, werden diese Änderungen abgerufen und bei der automatischen Speicherung in dem Formular angezeigt.  
  
 Wenn die automatische Speicherung aktiviert ist, wird die Speichern-Schaltfläche nur für die erste Speicherung des Datensatzes angezeigt. Nachdem der Datensatz erstellt wurde, wird die Speichern-Schaltfläche auf der Befehlsleiste nicht angezeigt, Sie sehen jedoch eine ![Schaltfläche "Automatisches Speichern"](media/auto-save-icon.png "Schaltfläche \"Automatisches Speichern\"")-Schaltfläche in der rechten unteren Ecke, die anzeigt, ob ungesicherte Änderungen vorhanden sind. Dieses Steuerelement wird auch angezeigt, wenn die automatische Speicherung deaktiviert ist.  
  
 Sie können diese Schaltfläche auswählen, um den Datensatz zu speichern und gleichzeitig Daten im Formular zu aktualisieren. Ob die automatische Speicherung aktiviert ist oder nicht: Wenn Sie von einem Datensatz wegnavigieren oder ein separates Fenster mit einem Datensatz schließen, wird der Datensatz gespeichert. Die Schaltfläche **Speichern und schließen**, die in Formularen für nicht gespeicherte Entitäten angezeigt wird, wird nicht benötigt.  
  
<a name="BKMK_AutoSave"></a>   
## <a name="should-you-disable-auto-save"></a>Sollten Sie die automatische Speicherung deaktivieren?  
 Wenn Sie Workflows, Plug-Ins oder Formularskripts haben, die ausgeführt werden, wenn ein Datensatz gespeichert wird, werden diese bei jeder automatischen Speicherung ausgeführt. Dieses kann u. U. zu unerwünschtem Verhalten führen, wenn diese Erweiterungen nicht zur Arbeit mit der automatischen Speicherung ausgelegt wurden. Unabhängig davon, ob die automatische Speicherung aktiviert ist, sollten Plugins, Workflows und Formularskripte so entworfen werden, dass sie nach bestimmten Änderungen suchen und nicht unterschiedslos bei einem bestimmten Ereignis ausgelöst werden.  
  
 Wenn Sie für eine Entität die Überwachung konfiguriert haben, wird jede Speicherung wie eine separate Aktualisierung behandelt. Wenn jemand auf einem Formular mit nicht gespeicherten Änderungen länger als dreißig Sekunden verweilt, sehen Sie nur dann einen zusätzlichen Eintrag, wenn dieser Benutzer nach der automatischen Speicherung weitere Daten hinzufügt. Wenn Sie Berichte haben, die von der Überwachung von Daten abhängen und jede Speicherung als individuelle Manipulation eines Datensatzes behandeln, sehen Sie möglicherweise eine Zunahme der Zahl der Manipulationen. Wenn Sie dieses Konzept verwenden, sollten Sie bedenken, dass, ob mit oder ohne automatische Speicherung, individuelles Benutzerverhalten dies zu einer unzuverlässigen Metrik macht.  
  
<a name="BKMK_DisableAutoSaveOrg"></a>   
## <a name="disable-auto-save-for-the-organization"></a>Deaktivierung der automatischen Speicherung für die Organisation  
 Wenn Sie zu dem Schluss kommen, dass die automatische Speicherung zu Problemen mit von ihnen verwendeten Erweiterungen führt, können Sie sie für Ihre Organisation deaktivieren. Es gibt keine Einstellung, um die automatische Speicherung für einzelne Entitäten oder Formulare zu deaktivieren.  
  
1. Gehen Sie zu **[Einstellungen](advanced-navigation.md#settings)** > **Verwaltung**.  
  
2.  Wählen Sie **Systemeinstellungen** aus.  
  
3.  Wählen Sie für die Option **Automatisches Speichern für alle Formulare aktivieren** **Nein**.  
  
<a name="BKMK_DisalbleAutoSaveForm"></a>   
## <a name="disable-auto-save-for-a-form"></a>Deaktivieren der automatischen Speicherung für ein Formular  
 Wenn Sie die automatische Speicherung für bestimmte Entitätsformulare deaktivieren möchten, können Sie dem `OnSave`-Ereignis in einer Entität Code hinzufügen.  
  
> [!NOTE]
>  Die automatische Speicherung wird für das Formular deaktiviert, die Daten werden aber weiterhin gespeichert, wenn Sie die ![Schaltfläche „Automatisches Speichern“](media/auto-save-icon.png "Schaltfläche „Automatisches Speichern“") rechts unten auswählen. Wenn Sie versuchen, von einem Formular wegzunavigieren oder ein Formular zu schließen, in dem Daten geändert wurden, werden Sie aufgefordert, die Änderungen zu speichern, bevor Sie dies tun können.  
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  
  
3.  Öffnen Sie das Formular, das Sie bearbeiten möchten.  
  
4.  Erstellen Sie eine JavaScript-Webressource, und fügen Sie sie dem Formular hinzu:  
  
    1.  Wählen Sie im Formulareditor in der Gruppe **Formular** den Eintrag **Formulareigenschaften** aus.  
  
    2.  Wählen Sie auf der Registerkarte **Ereignisse** unter **Formularbibliotheken** die Option **Hinzufügen** aus.  
  
    3.  Wählen Sie im Dialogfeld **Datensatz nachschlagen** die Option **Neu** aus.  
  
    4.  Geben Sie im Webressourcenformular die folgenden Informationen ein:  
  
        |||  
        |-|-|  
        |**Name**|preventAutoSave|  
        |**Anzeigename**|Verhindern der automatischen Speicherung|  
        |**Typ**|Skript (JScript)|  
  
    5.  Wählen Sie neben dem Feld **Typ** die Option **Text-Editor** aus.  
  
    6.  Geben Sie im Feld **Quelle** den folgenden Code ein:  
  
        ```javascript  
        function preventAutoSave(econtext) {  
            var eventArgs = econtext.getEventArgs();  
            if (eventArgs.getSaveMode() == 70 || eventArgs.getSaveMode() == 2) {  
                eventArgs.preventDefault();  
            }  
        }  
  
        ```  
  
    7.  Wählen Sie **OK** aus, um den Text-Editor zu schließen.  
  
    8.  Wählen Sie **Speichern** aus, um die Webressource zu speichern und das Webressourcefenster dann zu schließen.  
  
    9. Die Webressource, die Sie erstellt haben, ist jetzt im Dialogfeld **Datensatz suchen** ausgewählt. Wählen Sie **Hinzufügen** aus, um das Dialogfeld zu schließen.  
  
5.  Konfigurieren des OnSave-Ereignisses:  
  
    1.  Setzen Sie im Fenster **Formulareigenschaften** im Abschnitt **Ereignishandler** das **Ereignis** auf **OnSave**.  
  
    2.  Wählen Sie **Hinzufügen** aus.  
  
    3.  Setzen Sie im Fenster **Handlereigenschaften** **Bibliothek** auf die Webressource, die Sie im vorherigen Schritt hinzugefügt haben.  
  
    4.  Geben Sie "`preventAutoSave`" in das Feld **Funktion** ein. Dabei die Groß-/Kleinschreibung beachten. Geben Sie keine Anführungszeichen ein.  
  
    5.  Stellen Sie sicher, dass **Aktiviert** markiert ist.  
  
    6.  Markieren Sie **Ausführungskontext als ersten Parameter übergeben**.  
  
        > [!IMPORTANT]
        >  Andernfalls funktioniert das Skript nicht.  
  
         Das Dialogfeld **Handlereigenschaften** sollte so aussehen. Das Anpassungspräfix "new_ " kann je nach dem für den Standardherausgeber für Ihre Organisation eingerichteten Anpassungspräfix abweichen.  
  
 ![OnSave-Ereignishandler zur Verhinderung der automatischen Speicherung in Dynamics 365](media/prevent-auto-save-script.png "OnSave-Ereignishandler zur Verhinderung der automatischen Speicherung in Dynamics 365")  
  
    7.  Wählen Sie auf **OK** aus, um den Dialog **Handlereigenschaften** zu schließen.  
  
    8.  Wenn noch weitere Ereignishandler für das Ereignis `OnSave` vorhanden sind, verwenden Sie die grünen Pfeile, um diesen nach oben zu verschieben.  
  
6. Wählen Sie **OK** aus, um das Dialogfeld **Formulareigenschaften** zu schließen.  
  
7. Klicken Sie auf **Speichern und schließen**, um das Formular zu schließen.  
  
8. Wählen Sie im Projektmappen-Explorer die Option **Alle Anpassungen veröffentlichen** aus.  
  
 Nachdem Sie dieses Skript auf das `OnSave`-Ereignis angewendet haben, erscheint dann, wenn Benutzer mit diesem Formular einen Datensatz bearbeiten, in der unteren rechten Ecke des Formulars die Meldung **nicht gespeicherte Änderungen**, genau so, als ob die automatische Speicherung nicht aktiviert wäre. Diese Meldung verschwindet jedoch erst, wenn Benutzer auf die ![Schaltfläche "Automatisches Speichern"](media/auto-save-icon.png "Schaltfläche \"Automatisches Speichern\"") daneben klicken.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen und Gestalten von Formularen](create-design-forms.md)      

 

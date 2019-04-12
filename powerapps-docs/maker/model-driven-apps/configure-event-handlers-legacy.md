---
title: Konfigurieren von Ereignishandlern für Modell-angetriebene Hauptformulare in PowerApps | MicrosoftDocs
description: Grundlegendes zum Konfigurieren von Ereignishandlern in Dynamics 365 for Customer Engagement
Keywords: Hauptformular; Ereignishandler konfigurieren; Dynamics 365
author: Mattp123
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: powerapps
ms.topic: article
ms.assetid: dc0ebb3f-0c00-413a-968f-9cfd107055c0
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-model-driven-app-form-event-handlers"></a>Konfigurieren Sie Modell-angetriebene App-Formularereignishandler

 Formularereignishandler für PowerApps-Formulare können für die folgenden Bereiche in einem Formular konfiguriert werden:  
  
|Element|Ereignis|Beschreibung|  
|-------------|-----------|-----------------|  
|Formular|`OnLoad`|Tritt auf, wenn das Formular geladen wird.|  
||`OnSave`|Tritt auf, wenn Daten gespeichert werden.|  
|Registerkarte|`TabStateChange`|Tritt, wenn auf die Registerkarte erweitert oder reduziert wird.|  
|Feld|`OnChange`|Tritt auf, wenn Daten im Feld geändert werden und das Steuerelement den Fokus verliert.|  
|IFRAME|`OnReadyStateComplete`|Tritt auf, wenn der Inhalt eines IFRAMEs geladen wird.|  
  
 Ein Ereignishandler besteht aus einem Verweis auf eine JavaScript-Webressource und eine Funktion, die innerhalb dieser Webressource definiert ist und ausgeführt wird, wenn das Ereignis auftritt. Jedes Element kann bis zu 50 verschiedene konfigurierte Ereignishandler haben.  
  
> [!IMPORTANT]
>  Die inkorrekte Konfiguration eines Ereignishandlers kann zu Skriptfehlern führen, durch die das Formular inkorrekt geladen wird oder funktioniert. Wenn Sie nicht über der Entwickler des Skripts sind, stellen Sie sicher, dass Sie genau verstehen, welche Konfigurationsoptionen das Skript verlangt.  
>   
>  Konfigurieren Sie keinen Skriptereignishandler mithilfe einer Bibliothek, die aus einer Quelle stammt, der Sie nicht vollständig vertrauen. Skripts können verwendet werden, um beliebige Aktionen auszuführen, die ein Benutzer ausführen könnte, und schlecht geschriebene Skripts können die Leistung eines Formulars erheblich beeinträchtigen.  
>   
>  Testen Sie jeden konfigurierten Ereignishandler auf seine korrekte Funktionsweise.  
  
### <a name="to-configure-an-event-handler"></a>Konfigurieren von Ereignishandlern 
  
1.  Wählen Sie im Formular-Editor das Element mit dem Ereignis aus, für das Sie den Handler konfigurieren möchten.  
  
2.  Wählen Sie auf der [Registerkarte „Start”](form-editor-user-interface-legacy.md#home-tab) in der Gruppe **Bearbeiten** die Option **Eigenschaften ändern** aus, oder doppelklicken Sie einfach auf das Element.  
  
3.  Wählen Sie im Elementeigenschaftendialogfeld die Registerkarte **Ereignisse**  
  
4.  Erweitern Sie den Bereich **Formularbibliotheken**. Wenn die Bibliothek, die die Funktion, die Sie als Ereignishandler einrichten wollen, enthält, noch nicht aufgeführt ist, fügen Sie sie hinzu.  
  
5.  So fügen Sie eine Formularbibliothek zu einem Ereignishandler hinzu:  
    1.  Wählen Sie im Abschnitt **Formularbibliotheken** der **Ereignisliste** die Option **Hinzufügen** aus.  
  
    2.  Suchen Sie die JavaScript-Webressource in der Liste verfügbarer Webressourcen. Wählen Sie diese aus, und wählen Sie dann Auswählen **Hinzufügen** aus.  
  
         Wenn die benötigte JavaScript-Webressource nicht vorhanden ist, wählen auf **Neu** aus, um ein neues Webressourcenformular zu öffnen und eine Ressource zu erstellen.  
  
    3.  So erstellen Sie eine JavaScript-Webressource:  
        1.  Stellen Sie im Webressourceformular die folgenden Eigenschaften ein:  
  
            |Eigenschaft|Wert|  
            |--------------|-----------|  
            |Name|**Erforderlich** Geben Sie den Namen der Webressource ein.|  
            |Anzeigename|**Erforderlich** Geben Sie den in der Liste der Webressourcen anzuzeigenden Namen ein.|  
            |Beschreibung|(Optional). Geben Sie eine Beschreibung der Webressource ein.|  
            |Typ|**Erforderlich** Wählen Sie **Skript (JScript)** aus.|  
            |Sprache|(Optional). Wählen Sie eine der Sprachen aus, die für Ihre Organisation verfügbar sind.|  
  
        2.  Wenn Sie ein Skript erhalten haben, wird nachdrücklich empfohlen, die Schaltfläche **Durchsuchen** zu verwenden, um die Datei zu suchen und sie hochzuladen.  
  
             Alternativ können Sie die Schaltfläche **Text-Editor** auswählen und den Inhalt des Skripts in den Dialog **Inhalt bearbeiten** eingeben oder einfügen.  
  
            > [!NOTE]
            >  Da dieser einfache Text-Editor keine Funktionen enthält, um die Korrektheit des Skripts zu prüfen, sollten Sie immer eine separate Anwendung wie Visual Studio verwenden, um die Skripts zu bearbeiten und sie dann hochladen.  
  
        3.  Wählen Sie **Speichern** aus, und schließen Sie den Webressourcendialog.  
  
        4.  Die Webressource, die Sie erstellt haben, ist jetzt im Dialogfeld **Datensatz suchen** ausgewählt. Wählen Sie **Hinzufügen** aus, um den Dialog zu schließen.  
6.  Wählen Sie im Abschnitt **Ereignishandler** das Ereignis, für das Sie einen Ereignishandlern einrichten möchten.  
  
7.  Wählen Sie **Hinzufügen** aus, um den Dialog **Handlereigenschaften** zu öffnen.  
  
8. Wählen Sie auf der Registerkarte **Details** die entsprechende Bibliothek, und geben Sie den Namen der Funktion ein, die für das Ereignis ausgeführt werden soll.  
  
9. Der Ereignishandler ist standardmäßig aktiviert. Deaktivieren Sie das Kontrollkästchen **Aktiviert**, wenn Sie dieses Ereignis nicht aktivieren möchten.  
  
     Einige Funktionen erfordern einen Ausführungskontext, um an die Funktion übergeben werden zu können. Wählen Sie **Ausführungskontext als ersten Parameter übergeben** aus, wenn dies erforderlich ist.  
  
     Einige Funktionen akzeptieren eine Reihe von Parametern zur Steuerung des Verhaltens einer Funktion. Wenn diese erforderlich sind, geben Sie diese in der **Durch Kommata getrennten Liste mit Parametern, die an die Funktion weitergegeben werden.** ein.  
  
10. Fügen Sie auf der Registerkarte **Abhängigkeiten** alle Felder, von denen das Skript abhängt, im Bereich **Abhängige Felder** hinzu.  
  
11. Wählen Sie auf **OK** aus, um den Dialog **Handlereigenschaften** zu schließen.  
  
12. Wenn der Ereignishandler eingegeben ist, können Sie die Reihenfolge, in der die Funktion ausgeführt wird im Verhältnis zu anderen Funktionen mit den grünen Pfeilen ändern.  
  
13. Wählen Sie **OK** aus, um den Dialog Elementeigenschaften zu schließen.  
  
14. Wählen Sie **Speichern** aus, um Ihre Änderungen zu speichern. Wählen Sie **Veröffentlichen** aus, um das Formular zu veröffentlichen.  
  
> [!NOTE]
>  Während Sie mit der Benutzeroberfläche (UI) die Reihenfolge ändern können, in der die Skripts geladen werden, indem die grünen Auf- und Abwärts-Pfeile verwendet werden, werden die Skripts tatsächlich nicht sequenziell geladen.   

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)

---
title: Konfigurieren von Ereignishandlers für modellgesteuerte App-Hauptformularen mit PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ereignishandler in Dynamics 365 für Customer Engagement konfigurieren.
Keywords: Main form; Configure event handlers; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: dc0ebb3f-0c00-413a-968f-9cfd107055c0
ms.openlocfilehash: e05e9d840a2b3ad7d8d5c74e8e3b670504f739b0
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39686738"
---
# <a name="configure-model-driven-app-form-event-handlers"></a>Konfigurieren von Ereignishandler für modellgesteuerte App-Formulare

 Formular-Ereignishandler für PowerApps-Formulare können für die folgenden Bereiche in einem Formular konfiguriert werden:  
  
|Element|Veranstaltung|Beschreibung|  
|-------------|-----------|-----------------|  
|Formular|`OnLoad`|Tritt auf, wenn das Formular geladen wird.|  
||`OnSave`|Tritt auf, wenn Daten gespeichert werden.|  
|Registerkarte|`TabStateChange`|Tritt auf, wenn die Registerkarte erweitert oder reduziert ist.|  
|Feld|`OnChange`|Tritt auf, wenn Daten im Feld geändert werden und das Steuerelement den Fokus verliert.|  
|IFRAME|`OnReadyStateComplete`|Tritt auf, wenn der Inhalt von einem IFRAME geladen wird.|  
  
 Ein Ereignishandler besteht aus einem Verweis auf eine JavaScript-Webressource und einer in dieser Webressource definierten Funktion, die ausgeführt wird, wenn das Ereignis eintritt. Für jedes Element können bis zu 50 separate Ereignishandler konfiguriert werden.  
  
> [!IMPORTANT]
>  Die falsche Konfiguration eines Ereignishandlers kann zu Skriptfehlern führen, wodurch das Formular nicht richtig geladen wird oder nicht richtig funktioniert. Wenn Sie nicht der Entwickler des Skripts sind, stellen Sie sicher, dass Sie genau verstehen, welche Konfigurationsoptionen das Skript benötigt.  
>   
>  Konfigurieren Sie einen Skripereignishandler nicht mit einer Bibliothek, die nicht aus einer vertrauenswürdigen Quelle stammt. Skripte können verwendet werden, um jede Aktion auszuführen, die ein Benutzer ausführen könnte, und ein schlecht geschriebenes Skript kann die Leistung eines Formulars erheblich beeinträchtigen.  
>   
>  Nachdem Sie einen Ereignishandler konfiguriert haben, testen Sie ihn immer, um sicherzustellen, dass er korrekt funktioniert.  
  
### <a name="to-configure-an-event-handler"></a>So konfigurieren Sie einen Ereignishandler 
  
1.  Wählen Sie im Formulareditor das Element mit dem Ereignis aus, für das Sie einen Handler konfigurieren möchten.  
  
2.  Wählen Sie auf der Registerkarte [Home](form-editor-user-interface-legacy.md#home-tab) in der Gruppe **Bearbeiten** die Option **Eigenschaften ändern**, oder doppelklicken Sie einfach auf das Element.  
  
3.  Wählen Sie im Dialogfeld „Elementeigenschaften“ die Registerkarte **Ereignisse**.  
  
4.  Erweitern Sie den Bereich **Formularbibliotheken**. Wenn die Bibliothek, die die Funktion enthält, die Sie als Ereignishandler festlegen möchten, nicht bereits aufgelistet ist, fügen Sie die Bibliothek hinzu.  
  
5.  So fügen Sie eine Formularbibliothek zu einem Ereignishandler hinzu:  
    1.  Wählen Sie im Abschnitt **Formularbibliotheken** der **Ereignisliste** **Hinzufügen** aus.  
  
    2.  Suchen Sie die JavaScript-Webressource in der Liste der verfügbaren Webressourcen. Wählen Sie sie aus und anschließend **Hinzufügen**.  
  
         Wenn die von Ihnen benötigte JavaScript-Webressource nicht vorhanden ist, wählen Sie **Neu**, um ein neues Webressourcenformular zu öffnen und zu erstellen.  
  
    3.  So erstellen Sie eine JavaScript-Webressource:  
        1.  Legen Sie im Webressourcenformular die folgenden Eigenschaften fest:  
  
            |Eigenschaft|Wert|  
            |--------------|-----------|  
            |Name|**Erforderlich**. Geben Sie den Namen der Webressource ein.|  
            |Anzeigename|**Erforderlich**. Geben Sie den Namen ein, der in der Liste der Webressourcen angezeigt werden soll.|  
            |Beschreibung|Optional. Geben Sie eine Beschreibung für die Webressource ein.|  
            |Typ|**Erforderlich**. Wählen Sie **Skript (JScript)** aus.|  
            |Sprache|Optional. Wählen Sie eine für Ihre Organisation verfügbare Sprache.|  
  
        2.  Wenn Ihnen ein Skript zur Verfügung gestellt wurde, empfehlen wir Ihnen dringend, die Schaltfläche **Durchsuchen** zu verwenden, um die Datei zu finden und hochzuladen.  
  
             Alternativ können Sie auch die Schaltfläche **Texteditor** auswählen und den Inhalt des Skripts in das Dialogfenster **Inhalt bearbeiten** einfügen oder eingeben.  
  
            > [!NOTE]
            >  Da dieser einfache Texteditor keine Funktionen zur Überprüfung der Korrektheit des Skripts bietet, sollten Sie im Allgemeinen immer versuchen, eine separate Anwendung wie Visual Studio zu verwenden, um Skripte zu bearbeiten und dann hochzuladen.  
  
        3.  Wählen Sie **speichern**, und schließen Sie das Dialogfeld „Webressource“.  
  
        4.  Die Webressource, die Sie erstellt haben, ist jetzt im Dialogfeld **Datensatz suchen** ausgewählt. Wählen Sie **Hinzufügen**, um das Dialogfeld zu schließen.  
6.  Wählen Sie im Abschnitt **Ereignishandler** das Ereignis aus, für das Sie einen Ereignishandler festlegen möchten.  
  
7.  Wählen Sie **Hinzufügen**, um das Dialogfeld **Handlereigenschaften** zu öffnen.  
  
8. Wählen Sie auf der Registerkarte **Details** die entsprechende Bibliothek und geben Sie den Namen der Funktion ein, die für das Ereignis ausgeführt werden soll.  
  
9. Der Ereignishandler ist standardmäßig aktiviert. Deaktivieren Sie das Kontrollkästchen **Aktiviert**, wenn Sie dieses Ereignis nicht aktivieren möchten.  
  
     Einige Funktionen erfordern die Übergabe eines Ausführungskontexts an die Funktion. Wählen Sie **Ausführungskontext als ersten Parameter übergeben**, wenn dies erforderlich ist.  
  
     Einige Funktionen können einen Satz von Parametern akzeptieren, um das Verhalten einer Funktion zu steuern. Wenn diese erforderlich sind, tragen Sie sie in die durch **Komma getrennte Liste der Parameter ein, die an die Funktion übergeben werden**.  
  
10. Fügen Sie auf der Registerkarte **Abhängigkeiten** alle Felder, von denen das Skript abhängt, in den Bereich **Abhängige Felder** ein.  
  
11. Wählen Sie **OK**, um das Dialogfeld **Handlereigenschaften** zu schließen.  
  
12. Wenn der Ereignishandler aufgerufen wird, können Sie die Reihenfolge, in der die Funktion im Vergleich zu allen anderen Funktionen ausgeführt wird, anpassen, indem Sie sie mit den grünen Pfeilen nach oben oder unten verschieben.  
  
13. Wählen Sie **OK**, um das Dialogfeld „Elementeigenschaften“ zu schließen.  
  
14. Wählen Sie **Speichern** aus, um Ihre Änderungen zu speichern. Wählen Sie **Veröffentlichen**, um das Formular zu veröffentlichen.  
  
> [!NOTE]
>  Während die Benutzeroberfläche (UI) es Ihnen ermöglicht, die Reihenfolge, in der die Skripte geladen werden, mit den grünen Pfeilen nach oben und unten anzupassen, werden die Skripte eigentlich nicht sequentiell geladen.   

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)

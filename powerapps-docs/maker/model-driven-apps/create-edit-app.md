---
title: Erstellen oder Bearbeiten einer modellgesteuerten App mithilfe des App-Designers in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie Apps mithilfe des App-Designer erstellt oder bearbeitet werden'
keywords: ''
ms.date: 10/15/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 2a44229e-44f0-4c4e-ba21-a476210d0a12
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 19
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-create-a-model-driven-app-by-using-the-app-designer"></a>Anleitung: Erstellen oder Bearbeiten einer modellgesteuerten App mithilfe des App-Designers

In diesem Artikel lernen Sie die Grundlagen, wie Sie eine Modell-angetriebene App erstellen und bearbeiten, indem Sie den Kachel-basierten Anwendungs-Designer verwenden.

## <a name="prerequisites"></a>Voraussetzungen
Überprüfen Sie die folgenden Voraussetzungen, bevor Sie mit dem Erstellen der App beginnen:
- PowerApps Umgebung Weitere Informationen: [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment)
- Systemadministrator oder Systemanpasser-Sicherheitsrollen Weitere Informationen: [Über vordefinierte Sicherheitsrollen](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app#about-predefined-security-roles).
 
<a name="createApp"></a>   
## <a name="create-an-app"></a>App erstellen  

1.  Klicken Sie auf [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **Start**-Seite die Option **Ohne Vorlage erstellen** für eine modellgesteuerte App aus.  

    ![Modellgesteuertes Erstellen ohne Vorlage](media/start-from-blank-model-driven.png)

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2. Wählen Sie **Diese App erstellen** aus.

3. Geben Sie die folgenden Details auf der Seite **Neue App erstellen** ein: 

    - **Name**: Geben Sie einen Namen für die App ein.  
  
    - **Eindeutiger Name**: Der eindeutige Name wird automatisch anhand des App-Namens aufgefüllt, den Sie angeben. Ihm wird ein Herausgeberpräfix vorangestellt. Sie können den Teil des eindeutigen Namens ändern, der bearbeitet werden kann. Der eindeutige Name darf nur Buchstaben und Zahlen enthalten.  
  
        > [!NOTE]
        >  Ein Herausgeberpräfix ist der Text, der allen Entitäten oder Feldern hinzugefügt wird, die für eine Lösung mit diesem Herausgeber erstellt wurden.   
  
    - **Beschreibung**: Geben Sie eine kurze Beschreibung der App ein.  
  
    - **Symbol**: Standardmäßig ist das Miniaturansichtskontrollkästchen **Standard-App verwenden** aktiviert. Wenn Sie eine andere Webressource als ein Symbol für die App auswählen, deaktivieren Sie das Kontrollkästchen, und wählen Sie anschließend ein Symbol aus der Dropdownliste. Dieses Symbol wird auf der Vorschaukachel der App angezeigt.  
  
    - Wählen Sie den Clienttyp aus, für den die App verwendet wird.  
  
        - **Einheitliche Oberfläche**: Dies ist der neuere dynamische Webbrowser-Client, der für PCs und mobile Geräte eine ähnliche Oberfläche besitzt.  

        - **Internet**: Dies ist der klassische Dynamics 365 Customer Engagement Webbrowser-Client.  
    
    - **Suffix der App-URL**: Die App-URL wird automatisch anhand des App-Namens aufgefüllt, den Sie angeben. Es wird eine Vorschau der vollständigen URL angezeigt. Die App-URL muss eindeutig sein.  
  
         Zum Beispiel: https://\<org>.crm#.dynamics.com/Apps/\<App URL>

         Für lokal: http://\<server>/\<org name>/Apps/\<App URL> 
  
      > [!NOTE]
      >  Wenn Sie das Feld **Suffix der App-URL** löschen und die App speichern, wird die App-URL automatisch mit der App-ID generiert.  
  
    - **Vorhandene Lösung zum Erstellen der App verwenden**: Wählen Sie diese Option aus, um die App aus einer Liste von installierten Lösungen zu erstellen. Falls Sie diese Option auswählen, wechselt **Fertig** in der Kopfzeile zu **Weiter**. Wenn Sie **Weiter** auswählen, wird die Seite **App mit vorhandener Lösung erstellen** angezeigt. Wählen Sie in der Dropdownliste **Lösung auswählen** eine Lösung aus, aus der Sie die App erstellen möchten. Wenn eine Siteübersicht für die ausgewählten Lösung verfügbar ist, wird die Dropdownliste **Siteübersicht auswählen** verfügbar. Wählen Sie die Siteübersicht und dann **Fertig** aus.

      > [!NOTE]
      > Wenn Sie **Standardlösung** auswählen, wenn Sie eine Siteübersicht hinzufügen, werden die Komponenten, die dieser Siteübersicht zugeordnet sind, der App automatisch hinzugefügt.  

      ![Seite "Vorhandene Lösung zum Erstellen der App verwenden"](media/use-existing-solution-to-create-the-app.png "Vorhandene Lösung zum Erstellen der App verwenden") 

    - **Wählen Sie eine Startseite für die App aus**: Diese Option gestattet Ihnen, eine der Webressourcen auszuwählen, die in Ihrer Organisation zur Verfügung stehen. Die Willkommensseiten, die Sie erstellen, können hilfreiche Informationen für Benutzern enthalten (z.B. Links zu Videos, Upgradeanweisungen oder Informationen zu ersten Schritten). Die Willkommensseite wird angezeigt, wenn eine App geöffnet wird. Benutzer können **Diesen Willkommensbildschirm nächstes Mal nicht anzeigen** auf der Begrüßungsseite auswählen, um die Seite zu deaktivieren, damit sie bei der nächsten Ausführung der App nicht erscheint. Weitere Informationen dazu, wie Sie eine Webressource erstellen, wie beispielsweise eine HTML-Datei, die Sie als Begrüßungsdatei verwenden können, finden Sie unter [Erstellen und Bearbeiten von Webressourcen zum Erweitern der Webanwendung](create-edit-web-resources.md).  
      
    Um die App-Eigenschaften später zu bearbeiten, navigieren Sie zur Registerkarte **Eigenschaften** im App-Designer. Weitere Informationen: [App-Eigenschaften verwalteten](manage-app-properties.md)  
  
     > [!NOTE]
     >  Sie können den eindeutigen Namen und die App-URL-Endung auf der Registerkarte **Eigenschaften** nicht ändern.  
  
4. Klicken Sie auf **Fertig**. Falls Sie **Eine vorhandene Lösung zum Erstellen der App verwenden** gewählt haben, klicken Sie auf **Weiter**, um eine der in die Organisation importierten verfügbaren Lösungen auszuwählen.  
  
    Eine neue App wird erstellt und im Entwurfsstatus angezeigt. Die App-Designer-Canvas der neuen App wird angezeigt. Von dort können Sie die Komponenten, wie Entitäten, Ansichten, und Dashboards hinzufügen, um die App nützlich zu machen. Weitere Informationen: [Hinzufügen oder Bearbeiten von App-Komponenten](add-edit-app-components.md)  
   
<a name="editApp"></a>   
## <a name="edit-an-app"></a>App bearbeiten  
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

> [!IMPORTANT]
> "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2. Klicken Sie im linken Navigationsbereich die Option **Apps**, wählen eine modellgesteuerte App aus und klicken Sie dann auf der Symbolleiste die Option **Bearbeiten** an.   

3. Im App Designer fügen Sie Komponenten hinzu oder bearbeiten Sie diese wie erforderlich. Weitere Informationen: [Hinzufügen oder Bearbeiten von App-Komponenten](add-edit-app-components.md)  
 
  
### <a name="next-steps"></a>Nächste Schritte  
 [Hinzufügen oder Bearbeiten von App-Komponenten](add-edit-app-components.md)   



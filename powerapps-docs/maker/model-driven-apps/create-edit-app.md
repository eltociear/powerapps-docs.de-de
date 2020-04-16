---
title: Erstellen oder Bearbeiten einer modellgesteuerten App mithilfe des App-Designers in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Apps mithilfe des App-Designer erstellt oder bearbeitet werden
keywords: ''
ms.date: 03/05/2020
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 2a44229e-44f0-4c4e-ba21-a476210d0a12
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 19
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d5909d704863dbf88673ac35e3b36b59143d9f5f
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136563"
---
# <a name="create-a-model-driven-app-by-using-the-app-designer"></a>Erstellen oder Bearbeiten einer modellgesteuerten App mithilfe des App-Designers

In diesem Artikel lernen Sie die Grundlagen, wie Sie eine Modell-angetriebene App erstellen und bearbeiten, indem Sie den Kachel-basierten Anwendungs-Designer verwenden.

## <a name="prerequisites"></a>Voraussetzungen
Überprüfen Sie die folgenden Voraussetzungen, bevor Sie mit dem Erstellen der App beginnen:
- Eine Power Apps-Umgebung. Weitere Informationen: [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment)
- Systemadministrator oder Systemanpasser-Sicherheitsrollen Weitere Informationen: [Über vordefinierte Sicherheitsrollen](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app#about-predefined-security-roles).
 
<a name="createApp"></a>   
## <a name="create-an-app"></a>App erstellen  

1.  Wählen Sie auf der [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) **Homepage** die Option **Modellgesteuerte App ohne Vorlage** für eine modellgesteuerte App.  

2.  Wählen Sie **Erstellen** aus.

3.  Geben Sie die folgenden Details auf der Seite **Neue App erstellen** ein: 

    - **Name**: Geben Sie einen Namen für die App ein.  
  
    - **Eindeutiger Name**: Der eindeutige Name wird automatisch anhand des App-Namens aufgefüllt, den Sie angeben. Ihm wird ein Herausgeberpräfix vorangestellt. Sie können den Teil des eindeutigen Namens ändern, der bearbeitet werden kann. Der eindeutige Name darf nur Buchstaben und Zahlen enthalten.  
  
        > [!NOTE]
        >  Ein Herausgeberpräfix ist der Text, der allen Entitäten oder Feldern hinzugefügt wird, die für eine Lösung mit diesem Herausgeber erstellt wurden.   
  
    - **Beschreibung**: Geben Sie eine kurze Beschreibung der App ein.  
  
    - **Symbol**: Standardmäßig ist das Miniaturansichtskontrollkästchen **Standard-App verwenden** aktiviert. Wenn Sie eine andere Webressource als ein Symbol für die App auswählen, deaktivieren Sie das Kontrollkästchen, und wählen Sie anschließend ein Symbol aus der Dropdownliste. Dieses Symbol wird auf der Vorschaukachel der App angezeigt.  
  
    - **Vorhandene Lösung zum Erstellen der App verwenden**: Wählen Sie diese Option aus, um die App aus einer Liste von installierten Lösungen zu erstellen. Falls Sie diese Option auswählen, wechselt **Fertig** in der Kopfzeile zu **Weiter**. Wenn Sie **Weiter** auswählen, wird die Seite **App mit vorhandener Lösung erstellen** angezeigt. Wählen Sie in der Dropdownliste **Lösung auswählen** eine Lösung aus, aus der Sie die App erstellen möchten. Wenn eine Siteübersicht für die ausgewählten Lösung verfügbar ist, wird die Dropdownliste **Siteübersicht auswählen** verfügbar. Wählen Sie die Siteübersicht und dann **Fertig** aus.

      > [!NOTE]
      > Wenn Sie **Standardlösung** auswählen, wenn Sie eine Siteübersicht hinzufügen, werden die Komponenten, die dieser Siteübersicht zugeordnet sind, der App automatisch hinzugefügt.  

      > [!div class="mx-imgBorder"] 
      > ![Vorhandene Lösung zum Erstellen der App-Seite verwenden](media/use-existing-solution-to-create-the-app.png "Eine vorhandene Lösung zum Erstellen der App verwenden") 

    - **Wählen Sie eine Startseite für die App aus**: Diese Option gestattet Ihnen, eine der Webressourcen auszuwählen, die in Ihrer Organisation zur Verfügung stehen. Die Willkommensseiten, die Sie erstellen, können hilfreiche Informationen für Benutzern enthalten (z.B. Links zu Videos, Upgradeanweisungen oder Informationen zu ersten Schritten). Die Willkommensseite wird angezeigt, wenn eine App geöffnet wird. Benutzer können auf der Begrüßungsseite die Option **Diesen Willkommensbildschirm nächstes Mal nicht anzeigen** auswählen, um die Seite zu deaktivieren, damit sie bei der nächsten Ausführung der App nicht angezeigt wird. Beachten Sie, dass die Option **Diesen Willkommensbildschirm nächstes Mal nicht anzeigen** eine Einstellung auf Benutzerebene ist und nicht von Administratoren oder App-Entwicklern gesteuert werden kann. Weitere Informationen dazu, wie Sie eine Webressource erstellen, wie beispielsweise eine HTML-Datei, die Sie als Begrüßungsdatei verwenden können, finden Sie unter [Erstellen und Bearbeiten von Webressourcen zum Erweitern der Webanwendung](create-edit-web-resources.md).  
      
    Um die App-Eigenschaften später zu bearbeiten, navigieren Sie zur Registerkarte **Eigenschaften** im App-Designer. Weitere Informationen: [App-Eigenschaften verwalteten](manage-app-properties.md)  
  
     > [!NOTE]
     >  Sie können den eindeutigen Namen und die App-URL-Endung auf der Registerkarte **Eigenschaften** nicht ändern.  
  
4. Klicken Sie auf **Fertig** oder,&mdash;falls Sie **Bestehende Lösung zum Erstellen der App verwenden**&mdash;gewählt haben, klicken Sie auf **Weiter**, um eine Auswahl aus den verfügbaren Lösungen zu treffen, die in das Unternehmen importiert wurden.  
  
    Eine neue App wird erstellt und im Entwurfsstatus angezeigt. Die App-Designer-Canvas der neuen App wird angezeigt. Von dort können Sie die Komponenten, wie Entitäten, Ansichten, und Dashboards hinzufügen, um die App nützlich zu machen. Weitere Informationen: [Hinzufügen oder Bearbeiten von App-Komponenten](add-edit-app-components.md)  
   
<a name="editApp"></a>   
## <a name="edit-an-app"></a>App bearbeiten  
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2. Klicken Sie im linken Navigationsbereich die Option **Apps**, wählen eine modellgesteuerte App aus und klicken Sie dann auf der Symbolleiste die Option **Bearbeiten** an.   

3. Im App Designer fügen Sie Komponenten hinzu oder bearbeiten Sie diese wie erforderlich. Weitere Informationen: [Hinzufügen oder Bearbeiten von App-Komponenten](add-edit-app-components.md)  
 
  
### <a name="next-steps"></a>Nächste Schritte  
 [App-Komponenten hinzufügen oder bearbeiten](add-edit-app-components.md)   



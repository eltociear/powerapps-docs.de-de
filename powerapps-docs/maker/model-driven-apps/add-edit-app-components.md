---
title: 'Tutorial: Hinzufügen oder Bearbeiten von Komponenten einer modellgesteuerten App mit PowerApps | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie mit dem App-Designer von PowerApps Komponenten hinzufügen oder bearbeiten.
keywords: ''
ms.date: 03/30/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 17
topic-status: Drafting
ms.openlocfilehash: 87fec3bff3ad21a5c0474b67f001cca5c902d609
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39688033"
---
# <a name="tutorial-add-or-edit-model-driven-app-components-in-the-powerapps-app-designer"></a>Tutorial: Hinzufügen oder Bearbeiten von Komponenten einer modellgesteuerten App mit dem PowerApps-App-Designer

In diesem Tutorial erfahren Sie, wie Sie Komponenten einer modellgesteuerten App hinzufügen und daraus entfernen können. 

Eine modellgesteuerte App besteht aus verschiedenen Komponenten. Sie können einer App zwei Arten von Komponenten hinzufügen: Artefakte und Entitätsressourcen. Im Rahmen des App-Designers gehören Entitäten, Dashboard und Geschäftsprozessfluss zu den Artefakten einer App. Entitätsressourcen bestehen aus Formularen, Ansichten, Diagrammen und Dashboards.  
  
Der App-Designer verweist auf vorhandene Metadaten in der Standardlösung. Sie können damit Komponenten wie Formulare, Ansichten, Diagramme und Dashboards erstellen.  
  
## <a name="app-designer-layout"></a>App-Designer-Layout  
 Der App-Designer besteht aus zwei Hauptbereichen. Auf der linken Seite befindet sich die Canvas, in der Sie die App-Komponenten hinzufügen.  
  
![App-Designer-Canvas](../model-driven-apps/media/app-designer-canvas-pane.png)

 Auf der rechten Seite befinden sich Registerkarten, mit denen Sie Komponenten auswählen und Komponenteneigenschaften festlegen können.  
  
 ![App-Designer-Komponenten](../model-driven-apps/media/app-designer-canvas-components-tab.png "App-Designer-Komponenten")  
  
 Auf der Canvas werden die Bereiche für Siteübersicht, Geschäftsprozessfluss, Dashboards und Entitäten angezeigt. Wenn Sie ein Dashboard oder einen Geschäftsprozessfluss auswählen oder eine Siteübersicht konfigurieren, fügt der App-Designer der Canvas automatisch die Entitäten hinzu, die in diesen Komponenten verwendet werden. Nachdem die Entitäten hinzugefügt wurden, müssen Sie nur noch jede Entität auswählen und die erforderlichen Entitätsressourcen wie Formulare, Ansichten und Diagramme hinzufügen.
 
 Sie können auch **Canvas durchsuchen** verwenden, um nach Komponenten auf der Canvas zu suchen. Wenn Sie **Canvas durchsuchen** auswählen, wird im rechten Bereich rechts neben den Registerkarten eine neue Suchregisterkarte geöffnet.   
  
 ![Option „Canvas durchsuchen“](media/app-designer-search-tab.png "Option „Canvas durchsuchen“")

## <a name="open-an-app"></a>Öffnen einer App
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/) an. 

2. Wählen Sie **Modellgesteuert** > **Apps** und dann eine vorhandene App oder **App erstellen** aus. Weitere Informationen zum Erstellen einer App finden Sie unter [Erstellen oder Bearbeiten einer modellgesteuerten App mit dem App-Designer](create-edit-app.md#create-an-app).

## <a name="add-an-artifact-entity-dashboard-or-business-process-flow"></a>Hinzufügen eines Artefakts (Entität, Dashboard oder Geschäftsprozessfluss)  
 Wenn Sie einer App ein Dashboard oder einen Geschäftsprozessfluss hinzufügen, werden die in diesem Rahmen verwendeten Entitäten automatisch der App hinzugefügt. Wenn Sie eine Entität hinzufügen, werden die Kacheln für ihre Ressourcen automatisch hinzugefügt. Artefakte lassen sich der Designer-Canvas auf zwei Wegen hinzufügen: über die Befehlsleiste und die Schaltfläche **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Schaltfläche „Hinzufügen“ im Designer") sowie über die Kacheln auf der Registerkarte **Komponenten**.  
  
 Die folgenden Schritte zeigen, wie Sie der App ein Dashboard hinzufügen. Gehen Sie genau so vor, um einen Geschäftsprozessfluss oder eine Entität hinzuzufügen.  
  
1.  Wählen Sie auf der App-Designer-Canvas die Kachel **Dashboards** aus.  
  
     Auf der Canvas des App-Designers werden im rechten Bereich Ihre Dashboards angezeigt, die in der Standardlösung verfügbar sind.  
  
    > [!TIP]
    >  Alternativ können Sie folgendermaßen vorgehen:  
    >   
    > - Wählen Sie **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Schaltfläche „Hinzufügen“ im Designer") und dann **Dashboards** aus.  
    > - Wählen Sie auf der Registerkarte **Komponenten** unter **Artefakte** **Dashboards** aus.  
  
2.  Geben Sie in das Feld **Suchen** einige Schlüsselwörter für den gesuchten Dashboardnamen ein.  
  
     Die Dashboardliste wird so gefiltert, dass die Ergebnisse angezeigt werden, die Ihren Schlüsselwörtern entsprechen.  
  
3.  Wenn Sie möchten, dass Ihre Benutzer nur ausgewählte Dashboards verwenden, aktivieren Sie das Kontrollkästchen für die Dashboards, die Sie hinzufügen möchten. Die folgenden Dashboardtypen stehen zur Auswahl:
    - **Klassische Dashboards** werden sowohl in der Web-App als auch in der App mit der einheitlichen Oberfläche angezeigt.
    - **Interaktive Dashboards** werden nur in der App mit der einheitlichen Oberfläche angezeigt. Wenn Sie für den Clienttyp der App „Web-App“ ausgewählt haben, wird die Option **Interaktive Dashboards** nicht angezeigt.

     Diese Dashboards werden der Kachel **Dashboard** auf der App-Designer-Canvas hinzugefügt. Die Kachel **Dashboard** gibt auch die Anzahl von Dashboards an, die Sie der App hinzugefügt haben. Wenn Sie kein Dashboard auswählen, wird **Alle** anstelle der Dashboardanzahl angezeigt, und Benutzern stehen bei Verwendung der App alle Dashboards zur Verfügung.  
  
     Alle Entitäten, die das Dashboard verwendet, werden auch dem Bereich **Entitätsansicht** hinzugefügt. Wenn Sie beispielsweise das Dashboard „Leiter Kundendienst“ hinzufügen, werden dem Bereich „Entitätsansicht“ die Entitäten „Fall“, „Berechtigung“ und „Warteschlangenelement“ hinzugefügt. Für jede Entität werden auch die Kacheln für ihre Ressourcen hinzugefügt. Mit diesen Kacheln lassen sich Formulare, Ansichten und Diagramme hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen oder Bearbeiten von App-Komponenten im PowerApps-App-Designer](add-edit-app-components.md#bkmk_AddEntityAssets).   
  
    ![Hinzufügen von Entitäten zur App-Designer-Canvas](../model-driven-apps/media/add-entity-app-designer-canvas.png "Hinzufügen einer Entität zur App-Designer-Canvas")  
  
4.  Wenn das gewünschte Dashboard in der Standardlösung nicht vorhanden ist, erstellen Sie ein neues, indem Sie auf der Registerkarte **Komponenten** rechts neben der Canvas **Neu erstellen** auswählen.  
  
     ![Link „Neu erstellen“ auf der Registerkarte „Komponenten“ im App-Designer](../model-driven-apps/media/app-designer-components-tab-create-new.png "Link „Neu erstellen“ auf der Registerkarte „Komponenten“ im App-Designer")  
  
     Daraufhin wird der Dashboard-Designer geöffnet. Weitere Informationen finden Sie unter [Erstellen und Bearbeiten von Dashboards](create-edit-dashboards.md).  
  
    > [!NOTE]
    > - Wenn Sie einen Geschäftsprozessfluss oder eine Entität hinzufügen, öffnet die Option **Neu erstellen** den entsprechenden Designer. Weitere Informationen zum Erstellen von Geschäftsprozessflüssen und Entitäten finden Sie unter [Erstellen eines Geschäftsprozessflusses](/flow/create-business-process-flow) bzw. [Erstellen einer benutzerdefinierten Entität](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-create-entity).  
      
  
5.  Wenn Sie die Artefakte hinzugefügt haben, wählen Sie in der Befehlsleiste **Speichern** aus.  
  
<a name="bkmk_AddEntityAssets"></a>   
## <a name="add-entity-assets-forms-views-charts-or-dashboards"></a>Hinzufügen von Entitätsressourcen (Formulare, Ansichten, Diagramme oder Dashboards)  
 Wenn die Artefakte hinzugefügt wurden, können Sie damit beginnen, der App Entitätsressourcen wie Formulare, Ansichten, Diagramme und Dashboards hinzuzufügen.
Wenn Sie außerdem den Client für die einheitliche Oberfläche verwenden, können Sie der App auch Dashboardressourcen hinzufügen.  
  
 Dieser Abschnitt beschreibt die Schritte zum Hinzufügen eines Formulars zur App. Gehen Sie genauso vor, um der App eine Ansicht oder ein Diagramm hinzuzufügen.  
  
1.  Wählen Sie auf der App-Designer-Canvas die Kachel **Formulare** für die Entität aus, der Sie ein Formular hinzufügen möchten.  
  
     Auf der Canvas des App-Designers wird die gesamte Zeile für die Entität ausgewählt. Auf der rechten Seite werden alle vorhandenen Formulare für die ausgewählte Entität angezeigt.  
  
    > [!NOTE]
    >  Alternativ können Sie folgendermaßen vorgehen:  
    >   
    > - Wählen Sie **Hinzufügen** ![Schaltfläche „Hinzufügen“ im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Schaltfläche „Hinzufügen“ im Designer") und dann **Formulare** aus.  
    > - Wählen Sie auf der Registerkarte **Komponenten** unter **Entitätsressourcen** **Formulare** aus.  
  
    > [!TIP]
    >  Für alle Entitäten, die für die App ausgewählt sind, erscheint auf der Registerkarte **Komponenten** in der Liste **Entitäten auswählen** die Schaltfläche **Weitere Optionen** (**...**). Um alle Ressourcen für die ausgewählte Entität hinzuzufügen, wählen Sie **Weitere Optionen** (**...**) und dann **Alle Ressourcen hinzufügen** aus.  
  
2.  Wenn Ihre App-Benutzer nur ausgewählte Formulare verwenden sollen, aktivieren Sie die Kontrollkästchen für die Formulare, die Sie hinzufügen möchten. Die Formulare definieren, wie Benutzer Daten in der App angezeigt bekommen und mit ihnen interagieren. 
 
     Die Kachel „Formular“ der ausgewählten Entität zeigt die Anzahl von hinzugefügten Formularen an.  
  
     ![Kachel „Formular“ für die Entität „Fall“](../model-driven-apps/media/add-forms-entity.png "Kachel „Formular“ für die Entität „Fall“")  
  
     Wenn Sie beispielsweise kein Formular für eine Entität auswählen, werden den Endbenutzern beim Verwenden der App alle Formulare für diese Entität angezeigt. Dieses Verhalten ähnelt dem von Ansichten und Diagrammen, wenn keine Ansicht bzw. kein Diagramm ausgewählt ist. So können Sie Apps schnell erstellen, wenn Sie mit allen verfügbaren Komponenten arbeiten müssen, weil Sie nicht jede Komponente beim App-Design auswählen müssen.  

     Wenn keine Dashboards oder Geschäftsprozessflüsse ausgewählt sind, stehen den Benutzern beim Verwenden der App alle Dashboards und Geschäftsprozessflüsse zur Verfügung.
  
    > [!NOTE]
    > Damit die App ausgeführt werden kann, muss jede Entität, die Sie hinzufügen, mindestens ein aktives Formular haben. Wenn Sie mehrere Formulare ausgewählt haben, wird das erste aktive Formular verwendet, das in der Standardlösung angezeigt wird, wenn Benutzer die App ausführen.  
  
3.  Wenn Sie ein neues Formular hinzufügen möchten, das nicht in der Liste verfügbar ist, wählen Sie **Neu erstellen** aus.  
  
     Wählen Sie in der Dropdownliste die Art des Formulars aus, das Sie erstellen möchten.  
  
    > [!NOTE]
    >  Die Dropdownliste ist nur verfügbar, wenn Sie Formulare hinzufügen. Sie kann nicht für Ansichten und Diagramme verwendet werden.  
  
     Daraufhin wird der Formulardesigner geöffnet. Weitere Informationen finden Sie unter [Erstellen und Gestalten von Formularen](create-design-forms.md).  
  
     Wenn Sie eine Ansicht oder ein Diagramm hinzufügen, öffnet die Option **Neu erstellen** den entsprechenden Designer. Weitere Informationen finden Sie unter [Grundlegendes zu Ansichten](create-edit-views.md) und [Erstellen oder Bearbeiten eines Systemdiagramms](create-edit-system-chart.md).  
  
    > [!NOTE]
    >  Wenn Sie eine Ansicht hinzufügen, können Sie nur auf öffentliche Ansichten verweisen, die im Projektmappen-Explorer unter dem Knoten **Ansichten** aufgeführt sind.  
  
4. Wählen Sie den Dropdownpfeil ![Dropdownsymbol](../model-driven-apps/media/drop-down-icon.png "Dropdownpfeil") aus, um die Kachel zu erweitern und eine Liste der hinzugefügten Formulare anzuzeigen.  
  
     ![Erweiterte Kachel „Formular“ im App-Designer](../model-driven-apps/media/app-designer-expanded-form-tile.png "Erweiterte Kachel „Formular“ im App-Designer")  
  
5.  Wiederholen Sie diese Schritte, um der App Entitätsansichten und Diagramme hinzuzufügen.  
  
6.  Wählen Sie **Speichern**.  
  
## <a name="edit-or-remove-artifacts"></a>Bearbeiten oder Entfernen von Artefakten  
  
- Um ein Dashboard oder einen Geschäftsprozessfluss zu bearbeiten, wählen Sie den Dropdownpfeil ![Dropdownsymbol](../model-driven-apps/media/drop-down-icon.png "Dropdownpfeil") aus, um die Kachel zu erweitern, und wählen Sie dann die Schaltfläche ![Siteübersichts-Designer öffnen](../model-driven-apps/media/dynamics365-open-designer.PNG "Schaltfläche „Siteübersichts-Designer öffnen“") aus, die dem Dashboard bzw. Geschäftsprozessfluss entspricht, den Sie bearbeiten möchten.  
  
     Daraufhin wird der Designer für das ausgewählte Artefakt geöffnet.  
  
- Um ein Dashboard oder einen Geschäftsprozessfluss zu entfernen, wählen Sie den Dropdownpfeil ![Dropdownsymbol](../model-driven-apps/media/drop-down-icon.png "Dropdownpfeil") aus, um die Kachel zu erweitern, und wählen Sie dann das Dashboard bzw. den Geschäftsprozessfluss aus, den Sie entfernen möchten. Wählen Sie in der Befehlsleiste **Entfernen** aus.  

    Alternativ können Sie ein Dashboard oder einen Geschäftsprozessfluss entfernen, indem Sie das entsprechende Kontrollkästchen auf der Registerkarte **Komponenten** deaktivieren.
  
- Um eine Entität zu bearbeiten oder zu entfernen, wählen Sie die Entitätskachel und dann in der Befehlsleiste **Bearbeiten** bzw. **Entfernen** aus. Wenn Sie eine Entität bearbeiten, öffnet sich der Projektmappen-Explorer, in dem Sie Änderungen an der Entität vornehmen können.  
  
     Alternativ können Sie eine Komponente entfernen, indem Sie das Dashboard, den Geschäftsprozessfluss oder die Entitätskachel auswählen. Deaktivieren Sie auf der Registerkarte **Komponenten** die Kontrollkästchen für die Artefakte, die Sie aus dem Designer entfernen möchten.  
  
    > [!NOTE]
    >  Wenn Sie Änderungen an einer Entität vornehmen &mdash; z.B. den Anzeigename oder die Beschreibung der Entität ändern &mdash; werden diese erst nach ihrer Veröffentlichung im Projektmappen-Explorer im App-Designer angezeigt.  
  
## <a name="edit-or-remove-entity-assets"></a>Bearbeiten oder Entfernen von Entitätsressourcen  

### <a name="edit-entity-assets"></a>Bearbeiten von Entitätsressourcen
  
1. Wählen Sie den Dropdownpfeil ![Dropdownsymbol](../model-driven-apps/media/drop-down-icon.png "Dropdownpfeil") aus, um die Kachel für Formulare, Ansichten, Diagramme oder Dashboards zu erweitern.  
  
2. Wählen Sie das Formular, die Ansicht, das Diagramm oder das Dashboard aus, das Sie bearbeiten möchten.  
  
3. Wählen Sie in der Befehlsleiste **Bearbeiten** aus.

   oder

   Wählen Sie die Schaltfläche ![Siteübersichts-Designer öffnen](../model-driven-apps/media/dynamics365-open-designer.PNG "Schaltfläche „Siteübersichts-Designer öffnen“") aus, die dem Formular, der Ansicht, dem Diagramm oder dem Dashboard entspricht.  

### <a name="remove-entity-assets"></a>Entfernen von Entitätsressourcen  

1. Wählen Sie den Dropdownpfeil ![Dropdownsymbol](../model-driven-apps/media/drop-down-icon.png "Dropdownpfeil") aus, um die Kachel für Formulare, Ansichten, Diagramme oder Dashboards zu erweitern.  
  
2. Wählen Sie das Formular, die Ansicht, das Diagramm oder das Dashboard aus, das Sie bearbeiten möchten.

3. Wählen Sie in der Befehlsleiste **Entfernen** aus. 

Alternativ können Sie die Kachel „Formulare“, „Ansichten“, „Diagramme“ oder „Dashboards“ auswählen, und dann auf der Registerkarte **Komponenten** die Kontrollkästchen für die Ressourcen deaktivieren, die Sie aus dem Designer entfernen möchten.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen einer Siteübersicht für eine App](create-site-map-app.md) </br>  
 [Überprüfen und Veröffentlichen einer App](validate-app.md)

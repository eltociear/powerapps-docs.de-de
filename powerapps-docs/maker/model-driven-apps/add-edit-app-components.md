---
title: 'Hilfe, um Bearbeitungsmodus-getriebene App-Komponenten mit PowerApps hinzuzufügen oder zu bearbeiten | MicrosoftDocs'
description: Mithilfe des PowerApps-App-Designers Komponenten hinzufügen und bearbeiten
keywords: ''
ms.date: 03/30/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 17
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-add-or-edit-model-driven-app-components-in-the-powerapps-app-designer"></a>Hilfe, um Bearbeitungsmodus-getriebene App-Komponenten mit PowerApps hinzuzufügen oder zu bearbeiten

In diesem Lernprogramm wird erläutert, wie Sie Komponenten hinzufügen und Komponenten aus einer Modell-angetriebenen App löschen. 

Eine modell-getriebene App besteht aus verschiedenen Komponenten. Es gibt zwei Typen von Komponenten, die Sie einer App hinzufügen können: Artefakte und Entitätsressourcen. Im App-Designer sind Entitäten, Dashboards und Geschäftsprozessflüsse Artefakte einer App. Entitätsressourcen bestehen aus Formularen, Ansichten, Diagrammen und Dashboards.  
  
Der App-Designer bezieht sich auf vorhandene Metadaten in der Standardlösung. Sie können ihn verwenden, um Komponenten wie Formulare, Ansichten und Diagramme und Dashboards zu erstellen.  
  
## <a name="app-designer-layout"></a>App-Designer Darstellung  
 Der Anwendungs-Designer hat zwei Hauptbereiche. Auf der linken Seite sind die Canvas, in denen Sie App-Komponenten hinzufügen.  
  
![Anwendungs-Designer-Canvas](../model-driven-apps/media/app-designer-canvas-pane.png)

 Auf der rechten Seite sind Registerkarten, die Sie verwenden, um Komponenten auszuwählen und Komponenteneigenschaften festzulegen.  
 
 > [!div class="mx-imgBorder"]
 > ![App-Designer-Komponenten](../model-driven-apps/media/app-designer-canvas-components-tab.png "App-Designer-Komponenten")  
  
 Auf der Canvas finden Sie Bereiche für Siteübersicht, Geschäftsprozessfluss, Dashboard und Entitäten. Wenn Sie ein Dashboard oder einen Geschäftsprozessfluss auswählen oder eine Siteübersicht konfigurieren, wird der App-Designer automatisch die Entitäten hinzufügen, die in diesen Komponenten vom Canvas verwendet werden. Nachdem Sie die Entitäten bereitgestellt haben, müssen Sie nur noch jede Entität auswählen und die erforderlichen Entitätsanlagen wie die Formulare, die Ansichten und die Diagramme hinzufügen.
 
 Sie können auch **Canvas durchsuchen** verwenden, um nach Komponenten auf dem Canvas zu suchen. Wenn Sie **Canvas durchsuchen** auswählen, wird eine neue Suchregisterkarte rechts neben den Registerkarten im ganz rechten Bereich angezeigt.   
 
 > [!div class="mx-imgBorder"]
 > ![Option "Canvas durchsuchen"](media/app-designer-search-tab.png "Canvas durchsuchen")

## <a name="open-an-app"></a>Eine App öffnen
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/) an. 

2. Wählen Sie **Modell-angetrieben** > aus und dann **Anwendungen** und wählen Sie eine vorhandene App aus oder wählen Sie **App erstellen** aus. Weitere Informationen darüber, wie Sie eine App erstellen, finden Sie unter [Erstellen oder Bearbeiten einer Modell-angetriebene App, mithilfe von App-Designer](create-edit-app.md#create-an-app).

## <a name="add-an-artifact-entity-dashboard-or-business-process-flow"></a>Hinzufügen eines Artefakt (Entität, Dashboard oder Geschäftsprozessfluss)  
 Wenn Sie ein Dashboard oder einen Geschäftsprozessfluss zu einer App hinzufügen, werden die verwendeten Entitäten automatisch der App hinzugefügt. Wenn eine Entität hinzugefügt wird, werden die Kacheln für die Anlagen automatisch hinzugefügt. Es gibt zwei Arten, wie Sie Artefakte dem Designer-Canvas hinzufügen können: Mithilfe der Schaltfläche **Hinzufügen** ![Hinzufügen-Schaltfläche im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Hinzufügen-Schaltfläche im Designer") auf der Befehlsleiste oder mithilfe der Kacheln auf der Registerkarte **Komponenten**.  
  
 In diesem Abschnitt werden die Schritte zum Hinzufügen eines Dashboards zu der App erläutert. Verwenden Sie dieselben Schritte, um einen Geschäftsprozessfluss oder eine Entität hinzuzufügen.  
  
1.  Wählen Sie auf der App-Design-Canvas die Kachel **Dashboards**.  
  
     Auf der App-Designer-Canvas werden im ganz rechten Bereich die Dashboards angezeigt, die in der Standardlösung verfügbar sind.  
  
    > [!TIP]
    >  Alternativ können Sie eine der folgenden Möglichkeiten nutzen:  
    >   
    > - Klicken Sie auf die Schaltfläche **Hinzufügen**![Hinzufügen-Schaltfläche im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Hinzufügen-Schaltfläche im Designer") und wählen Sie **Dashboards**.  
    > - Wählen Sie auf der Registerkarte **Komponenten** unter **Artefakte** **Dashboards**.  
  
2.  Im Feld **Suchen** geben Sie einige Suchbegriffen für den Dashboardnamen ein, den Sie suchen.  
  
     Die Dashboardliste wird gefiltert, damit nur Ergebnisse angezeigt werden, die mit dem gesuchten Schlüsselwort übereinstimmen.  
  
3.  Wenn Sie möchten, dass Ihre App-Benutzer nur ausgewählte Dashboards verwenden können, aktivieren Sie das Kontrollkästchen für das Dashboard aus, das Sie hinzufügen möchten. Sie können die folgenden Arten von Dashboards auswählen:
    - **Klassische Dashboards** werden in der Web-App und in der App mit einheitlicher Oberfläche angezeigt.
    - **Interaktive Dashboards** werden nur in der App mit einheitlicher Oberfläche angezeigt. Wenn Sie als Clienttyp für die App die Web-App ausgewählt haben, wird die Option **Interaktive Dashboards** nicht angezeigt.

     Diese Dashboards werden der Kachel **Dashboard** auf der App-Designer-Canvas hinzugefügt. Die Kachel **Dashboard** zeigt auch die Anzahl der Dashboards an, die Sie der App hinzugefügt haben. Wenn Sie kein Dashboard auswählen, wird anstelle der Dashboard-Anzahl **Alle** angezeigt, und alle Dashboards sind für Benutzer verfügbar, wenn diese die App verwenden.  
  
     Alle Entitäten, in denen das Dashboard verwendet wird, werden auch zum Bereich **Entitätsansicht** hinzugefügt. Wenn Sie das Kundenservicemanagerdashboard hinzufügen, werden die Fall-, Anspruchs- und Warteschlangenelemententitäten zum Entitätsansichtbereich hinzugefügt. Für jede Entität werden auch die Kacheln für die Ressourcen hinzugefügt. Sie können diese Kacheln verwenden, um die Formulare, Ansichten und Diagramme hinzufügen. Weitere Informationen: [Hinzufügen oder Bearbeiten von App-Komponenten im PowerApps App-Designer](add-edit-app-components.md#bkmk_AddEntityAssets)   
  
    ![Der App-Designer-Canvas eine Entität hinzufügen](../model-driven-apps/media/add-entity-app-designer-canvas.png "Der App-Designer-Canvas eine Entität hinzufügen")  
  
4.  Wenn das gewünschte Dashboard nicht in der Standardlösung vorhanden ist, erstellen Sie ein Dashboard, indem Sie auf **Neu erstellen** auf der Registerkarte **Komponenten** rechts neben der Canvas klicken.  
  
     > [!div class="mx-imgBorder"]
     > ![Einen neuen Link auf der Registerkarte "Komponenten" des App-Designers erstellen](../model-driven-apps/media/app-designer-components-tab-create-new.png "Einen neuen Link auf der Registerkarte \"Komponenten\" des App-Designers erstellen")  
  
     Der Dashboard-Designer wird geöffnet. Weitere Informationen: [Erstellen und Bearbeiten von Dashboards](create-edit-dashboards.md)  
  
    > [!NOTE]
    > - Wenn Sie einen Geschäftsprozessfluss oder eine Entität hinzufügen, wird die Option **Neu erstellen** im entsprechenden Designer geöffnet. Weitere Informationen zur Erstellung von Geschäftsprozessflüssen finden Sie unter [Einen neuen Geschäftsprozessfluss erstellen](/flow/create-business-process-flow) und [Eine neue benutzerdefinierte Entität erstellen](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-create-entity).  
      
  
5.  Wenn Sie mit dem Hinzufügen von Artefakten fertig sind, wählen Sie **Speichern**.  
  
<a name="bkmk_AddEntityAssets"></a>   
## <a name="add-entity-assets-forms-views-charts-or-dashboards"></a>Hinzufügen von Entitätsressourcen (Formulare, Ansichten, Diagramme oder Dashboards)  
 Mit den Artefakten an der richtigen Stelle können Sie nun mit dem Hinzufügen von Entitätsanlagen wie Formulare, Ansichten, Diagramme und Dashboards zur App beginnen.
Wenn Sie außerdem den Client mit einheitlicher Oberfläche verwenden, können Sie Entitätsdashboardanlagen zur App hinzufügen.  
  
 In diesem Abschnitt werden die Schritte zum Hinzufügen eines Formulars zu der App erläutert. Verwenden Sie dieselben Schritte, um eine Ansicht oder ein Diagramm einer App hinzuzufügen.  
  
1.  Wählen Sie auf dem App-Designer-Canvas die Kachel **Formulare** für die Entität, die Sie in einem Formular hinzufügen möchten.  
  
     Auf der App Designer-Canvas ist die gesamte Zeile für die Entität aktiviert. Auf der rechten Seite sehen Sie alle vorhandenen Formulare für die ausgewählte Entität.  
  
    > [!NOTE]
    >  Alternativ können Sie eine der folgenden Möglichkeiten nutzen:  
    >   
    > - Klicken Sie auf die Schaltfläche **Hinzufügen**![Hinzufügen-Schaltfläche im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Hinzufügen-Schaltfläche im Designer") und wählen Sie **Formulare**.  
    > - Wählen Sie auf der Registerkarte **Komponenten** unter **Entitätsressourcen** **Formulare**.  
  
    > [!TIP]
    >  Für alle für die App ausgewählten Entitäten wird die Schaltfläche **Weitere Optionen** (**...**) in der Liste **Entitäten auswählen** der Registerkarte **Komponenten** angezeigt. Um alle Ressourcen für die ausgewählte Entität hinzuzufügen, wählen Sie **Weitere Optionen** (**...**) und dann **Alle Ressourcen hinzufügen**.  
  
2.  Wenn Sie möchten, dass Ihre App-Benutzer nur ausgewählte Formulare verwenden können, aktivieren Sie das Kontrollkästchen für die Formulare aus, das Sie hinzufügen möchten. Die Formulare definieren, wie Benutzer mit den Daten in der App interagieren. 
 
     Die Formularkachel der ausgewählten Entität zeigt die Anzahl der hinzugefügten Formulare.  
  
     ![Formularkacheln für die Anfrageentität](../model-driven-apps/media/add-forms-entity.png "Formularkacheln für die Anfrageentität")  
  
     Wenn Sie beispielsweise kein Formular für eine Entität auswählen, werden alle Formulare für diese Entität für Endbenutzer angezeigt, während Sie die App verwenden. Dieses Verhalten ist für Ansichten und Diagramme ähnlich, wenn kein Ansicht oder kein Diagramm ausgewählt wird. Dies erleichtert es Benutzern, Apps schnell zu erstellen, wenn sie mit allen verfügbaren Komponenten arbeiten müssen. Es ist nicht notwendig, jede Komponente während dem App-Design auszuwählen.  

     Wenn keine Dashboards oder Geschäftsprozessflüsse ausgewählt werden, werden alle Dashboards und Geschäftsprozessflüsse für Benutzer verfügbar gemacht, während Sie die App verwenden.
  
    > [!NOTE]
    > Um die App auszuführen muss jede hinzugefügte Entität mindestens ein aktives Formular aufweisen. Falls Sie mehrere Formulare ausgewählt haben, wird das erste aktive Formular im Formularauftrag der Standardlösung verwendet, wenn Benutzer die App ausführen.  
  
3.  Wenn Sie ein neues Formular hinzufügen möchten, das nicht in der Liste angezeigt wird, wählen Sie **Neu erstellen**.  
  
     Wählen Sie in der Dropdownliste den Formulartyp aus, den Sie erstellen möchten.  
  
    > [!NOTE]
    >  Die Dropdownliste ist nur verfügbar, wenn Sie Formulare hinzufügen. Es ist nicht für Ansichten und Diagramme verfügbar.  
  
     Der Formular-Designer wird geöffnet. Weitere Informationen: [Erstellen und Entwerfen von Formularen](create-design-forms.md)  
  
     Wenn Sie eine Ansicht oder ein Diagramm hinzufügen, öffnet die Option **Neu erstellen** den entsprechenden Designer. Weitere Informationen: [Ansichten verstehen](create-edit-views.md) und [Erstellen oder Bearbeiten eines Systemdiagramms](create-edit-system-chart.md)  
  
    > [!NOTE]
    >  Wenn Sie eine Ansicht hinzufügen, können Sie nur auf öffentliche Ansichten verweisen, die mit dem **Ansichten**-Knoten im Projektmappen-Explorer aufgelistet sind.  
  
4. Wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel zu erweitern und eine Liste der Formulare anzuzeigen, die hinzugefügt wurden.  
  
     ![Erweiterte Formularkachel im App-Designer](../model-driven-apps/media/app-designer-expanded-form-tile.png "Erweiterte Formularkachel im App-Designer")  
  
5.  Wiederholen Sie diese Schritte, um Entitätsansichten und Diagramme der App hinzuzufügen.  
  
6.  Wählen Sie **Speichern** aus.  
  
## <a name="edit-or-remove-artifacts"></a>Bearbeiten oder entfernen Sie Artefakte  
  
- Um ein Dashboard oder einen Geschäftsfluss zu bearbeiten, wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel zu erweitern, und wählen Sie dann die Schaltfläche ![Schaltfläche "Den Siteübersichtdesigner öffnen"](../model-driven-apps/media/dynamics365-open-designer.PNG "Schaltfläche \"Den Siteübersichtdesigner öffnen\"") gemäß dem Dashboard oder dem Prozessfluss, den Sie bearbeiten möchten.  
  
     Der Designer für das ausgewählte Artefakt wird geöffnet.  
  
- Wenn Sie ein Dashboard oder einen Geschäftsprozessfluss entfernen möchten, wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel zu erweitern. Wählen Sie dann das Dashboard oder den Geschäftsprozessfluss, das oder den Sie entfernen möchten. Wählen Sie auf der Befehlsleiste **Entfernen** aus.  

    Eine weitere Methode, ein Dashboard oder einen Geschäftsprozessfluss zu entfernen, ist, die entsprechenden Kontrollkästchen auf der Registerkarte **Komponenten** zu deaktivieren.
  
- Zum Bearbeiten oder Entfernen einer Entität wählen Sie die Entitätskachel und dann auf der Befehlsleiste **Bearbeiten** oder **Entfernen**. Wenn Sie eine Entität bearbeiten, öffnet der Lösungsexplorer, wo Sie Änderungen an der Entität vornehmen können.  
  
     Alternativ wählen Sie das Dashboard oder den Geschäftsprozessfluss oder die Entitätskachel aus, um eine Komponente zu entfernen. Deaktivieren Sie auf der Registerkarte **Komponenten** die Kontrollkästchen für die Artefakte, die Sie aus dem Designer entfernen möchten.  
  
    > [!NOTE]
    >  Wenn Sie Änderungen an einer Entität vornehmen (beispielsweise das Ändern des Anzeigenamens der Entität oder der Beschreibung), werden die Änderungen nicht im App-Designer angezeigt, es sei denn, die Änderungen werden im Projektmappen-Explorer veröffentlicht.  
  
## <a name="edit-or-remove-entity-assets"></a>Bearbeiten oder entfernen von Entitätsanlagen  

### <a name="edit-entity-assets"></a>Entitätsressourcen bearbeiten
  
1. Wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel für Formulare, Ansichten, Diagramme oder Dashboards zu erweitern.  
  
2. Wählen Sie das Formular, die Ansicht, das Diagramm oder das Dashboard, das Sie bearbeiten möchten.  
  
3. Klicken Sie auf der Befehlsleiste auf **Bearbeiten**.

   oder

   Wählen Sie die Schaltfläche des Siteübersichtsdesigners ![Schaltfläche "Siteübersichts-Designer öffnen"](../model-driven-apps/media/dynamics365-open-designer.PNG "Schaltfläche \"Siteübersichts-Designer öffnen\"") gemäß dem Formular, der Ansicht, dem Diagramm oder dem Dashboard.  

### <a name="remove-entity-assets"></a>Entfernen von Entitätsanlagen  

1. Wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel für Formulare, Ansichten, Diagramme oder Dashboards zu erweitern.  
  
2. Wählen Sie das Formular, die Ansicht, das Diagramm oder das Dashboard, das Sie bearbeiten möchten.

3. Wählen Sie auf der Befehlsleiste **Entfernen** aus. 

Alternativ können Sie die Kachel für Formulare, Ansichten, Diagrammen oder Dashboards auswählen und dann auf der Registerkarte **Komponenten** die Kontrollkästchen für die Ressourcen deaktivieren, die Sie aus dem Designer entfernen möchten.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen einer App-Siteübersicht](create-site-map-app.md) </br>  
 [Überprüfen und Veröffentlichen Sie eine App](validate-app.md)

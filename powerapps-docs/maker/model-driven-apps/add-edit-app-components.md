---
title: Tutorial, um modellgesteuerte App-Komponenten mit PowerApps | Microsoft-Dokumentation hinzuzufügen oder zu bearbeiten
description: Mithilfe des PowerApps-App-Designers Komponenten hinzufügen oder bearbeiten
keywords: ''
ms.date: 10/15/2018
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c9cbb77b0b312b4376aed8b5f9d106e2c2826ea4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752192"
---
# <a name="tutorial-add-or-edit-model-driven-app-components-in-the-powerapps-app-designer"></a>Tutorial: Modellgesteuerte Apps in PowerApps-App-Designer hinzufügen oder bearbeiten

In diesem Lernprogramm wird erläutert, wie Sie Komponenten hinzufügen und Komponenten aus einer Modell-angetriebenen App löschen. 

Eine modell-getriebene App besteht aus verschiedenen Komponenten. Es gibt zwei Typen von Komponenten, die Sie einer App hinzufügen können: Artefakte und Entitätsressourcen. Im App-Designer sind Entitäten, Dashboards und Geschäftsprozessflüsse Artefakte einer App. Entitätsressourcen bestehen aus Formularen, Ansichten, Diagrammen und Dashboards.  
  
Der App-Designer bezieht sich auf vorhandene Metadaten in der Standardlösung. Sie können ihn verwenden, um Komponenten wie Formulare, Ansichten und Diagramme und Dashboards zu erstellen.  
  
## <a name="app-designer-layout"></a>App-Designer Darstellung  
 Der Anwendungs-Designer hat zwei Hauptbereiche. Auf der linken Seite sind die Canvas, in denen Sie App-Komponenten hinzufügen.  
  
![Anwendungs-Designer-Canvas](../model-driven-apps/media/app-designer-canvas-pane.png)

 Auf der rechten Seite sind Registerkarten, die Sie verwenden, um Komponenten auszuwählen und Komponenteneigenschaften festzulegen.  
 
 > [!div class="mx-imgBorder"]
 > ![App-Designer-Komponenten](../model-driven-apps/media/app-designer-canvas-components-tab.png "App-Designer-Komponenten")  
  
 Auf der Canvas finden Sie Bereiche für Siteübersicht, Geschäftsprozessfluss, Dashboard und Entitäten. Wenn Sie ein Dashboard oder einen Geschäftsprozessfluss auswählen oder eine Siteübersicht konfigurieren, wird der App-Designer automatisch die Entitäten hinzufügen, die in diesen Komponenten von Canvas verwendet werden. Nachdem Sie die Entitäten bereitgestellt haben, müssen Sie nur noch jede Entität auswählen und die erforderlichen Entitätsanlagen wie die Formulare, die Ansichten und die Diagramme hinzufügen.
 
 Sie können auch **Canvas durchsuchen** verwenden, um nach Komponenten auf dem Canvas zu suchen. Wenn Sie **Canvas durchsuchen** auswählen, wird eine neue Suchregisterkarte rechts neben den Registerkarten im ganz rechten Bereich angezeigt.   
 
 > [!div class="mx-imgBorder"]
 > ![Canvas-Suchoption](media/app-designer-search-tab.png "Canvas-Suche")

## <a name="open-an-app"></a>Eine App öffnen
1. Melden Sie sich bei [PowerApps](https://make.powerapps.com/) an. 

2. Wählen Sie eine vorhandene modellgetriebene Anwendung aus oder wählen Sie **Ohne Vorlage erstellen**. Weitere Informationen darüber, wie Sie eine App erstellen, finden Sie unter [Erstellen oder Bearbeiten einer Modell-angetriebene App, mithilfe von App-Designer](create-edit-app.md#create-an-app).

## <a name="add-an-artifact-entity-dashboard-or-business-process-flow"></a>Hinzufügen eines Artefakt (Entität, Dashboard oder Geschäftsprozessfluss)  
 Wenn Sie ein Dashboard oder einen Geschäftsprozessfluss zu einer App hinzufügen, werden die verwendeten Entitäten automatisch der App hinzugefügt. Wenn eine Entität hinzugefügt wird, werden die Kacheln für die Anlagen automatisch hinzugefügt. Es gibt zwei Arten, wie Sie Artefakte dem Designer-Canvas hinzufügen können: Mithilfe der Schaltfläche **Hinzufügen** ![Hinzufügen-Schaltfläche im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Schaltfläche im Designer hinzufügen") auf der Befehlsleiste oder mithilfe der Kacheln auf der Registerkarte **Komponenten**.  
  
 In diesem Abschnitt werden die Schritte zum Hinzufügen eines Dashboards zu der App erläutert. Verwenden Sie dieselben Schritte, um einen Geschäftsprozessfluss oder eine Entität hinzuzufügen.  
  
1.  Wählen Sie auf der App-Design-Canvas die Kachel **Dashboards**.  
  
     Auf der App-Designer-Canvas werden im ganz rechten Bereich die Dashboards angezeigt, die in der Standardlösung verfügbar sind.  
  
    > [!TIP]
    >  Alternativ können Sie eine der folgenden Möglichkeiten nutzen:  
    >   
    > - Wählen Sie **Hinzufügen** ![Schaltfläche Hinzufügen im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Schaltfläche im Designer hinzufügen"), und dann **Dashboards**.  
    > - Wählen Sie auf der Registerkarte **Komponenten** unter **Artefakte** **Dashboards**.  
  
2.  Im Feld **Suchen** geben Sie einige Suchbegriffen für den Dashboardnamen ein, den Sie suchen.  
  
     Die Dashboardliste wird gefiltert, damit nur Ergebnisse angezeigt werden, die mit dem gesuchten Schlüsselwort übereinstimmen.  
  
3.  Wenn Sie möchten, dass Ihre App-Benutzer nur ausgewählte Dashboards verwenden können, aktivieren Sie das Kontrollkästchen für das Dashboard aus, das Sie hinzufügen möchten. Sie können die folgenden Arten von Dashboards auswählen:
    - **Klassische Dashboards** werden in der Web-App und in der App mit einheitlicher Oberfläche angezeigt.
    - **Interaktive Dashboards** werden nur in der App mit einheitlicher Oberfläche angezeigt. Wenn Sie als Clienttyp für die App die Web-App ausgewählt haben, wird die Option **Interaktive Dashboards** nicht angezeigt.

     Diese Dashboards werden der Kachel **Dashboard** auf der App-Designer-Canvas hinzugefügt. Die Kachel **Dashboard** zeigt auch die Anzahl der Dashboards an, die Sie der App hinzugefügt haben. Wenn Sie kein Dashboard auswählen, wird anstelle der Dashboard-Anzahl **Alle** angezeigt, und alle Dashboards sind für Benutzer verfügbar, wenn diese die App verwenden.  
  
     Alle Entitäten, in denen das Dashboard verwendet wird, werden auch zum Bereich **Entitätsansicht** hinzugefügt. Wenn Sie das Kundenservicemanagerdashboard hinzufügen, werden die Fall-, Anspruchs- und Warteschlangenelemententitäten zum Entitätsansichtbereich hinzugefügt. Für jede Entität werden auch die Kacheln für die Ressourcen hinzugefügt. Sie können diese Kacheln verwenden, um die Formulare, Ansichten und Diagramme hinzufügen. Weitere Informationen:[Hinzufügen oder Bearbeiten von App-Komponenten im PowerApps-App-Designer](add-edit-app-components.md#bkmk_AddEntityAssets)   
  
    ![Hinzufügen der Entität zur App Designer-Canvas](../model-driven-apps/media/add-entity-app-designer-canvas.png "Hinzufügen einer Entität zur App Designer-Canvas")  
  
4.  Wenn das gewünschte Dashboard nicht in der Standardlösung vorhanden ist, erstellen Sie ein Dashboard, indem Sie auf **Neu erstellen** auf der Registerkarte **Komponenten** rechts neben der Canvas klicken.  
  
     > [!div class="mx-imgBorder"]
     > ![Erstellen eines neuen Links auf der Registerkarte Komponenten des App-Designers](../model-driven-apps/media/app-designer-components-tab-create-new.png "Erstellen eines neuen Links auf der Registerkarte Komponenten des App-Designers")  
  
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
    > - Wählen Sie **Hinzufügen** ![Schaltfläche Hinzufügen im Designer](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "Schaltfläche im Designer hinzufügen"), und dann **Formulare**.  
    > - Wählen Sie auf der Registerkarte **Komponenten** unter **Entitätsressourcen** **Formulare**.  
  
    > [!TIP]
    >  Für alle für die App ausgewählten Entitäten wird die Schaltfläche **Weitere Optionen** (**...**) in der Liste **Entitäten auswählen** der Registerkarte **Komponenten** angezeigt. Um alle Ressourcen für die ausgewählte Entität hinzuzufügen, wählen Sie **Weitere Optionen** (**...**) und dann **Alle Ressourcen hinzufügen**.  
  
2.  Wenn Sie möchten, dass Ihre App-Benutzer nur ausgewählte Formulare verwenden können, aktivieren Sie das Kontrollkästchen für die Formulare aus, das Sie hinzufügen möchten. Die Formulare definieren, wie Benutzer mit den Daten in der App interagieren. 
 
     Die Formularkachel der ausgewählten Entität zeigt die Anzahl der hinzugefügten Formulare.  
  
     ![Formularkachel für Anfrageentität](../model-driven-apps/media/add-forms-entity.png "Formularkachel für Anfrageentität")  
  
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
  
     ![Formularkachel im App-Designer erweitert](../model-driven-apps/media/app-designer-expanded-form-tile.png "Formularkachel im App-Designer erweitert")  
  
5.  Wiederholen Sie diese Schritte, um Entitätsansichten und Diagramme der App hinzuzufügen.  
  
6.  Wählen Sie **Speichern** aus.  
  
## <a name="edit-or-remove-artifacts"></a>Bearbeiten oder entfernen Sie Artefakte  
  
- Um ein Dashboard oder einen Geschäftsprozessfluss zu bearbeiten, wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel zu erweitern. Wählen Sie dann die Schaltfläche Siteübersichtsdesigner ![Siteübersichtdesigner öffnen](../model-driven-apps/media/dynamics365-open-designer.PNG "Schaltfläche "Siteübersichts-Designer öffnen""), die dem Dashboard oder dem Geschäftsprozessfluss, den Sie bearbeiten möchten, entspricht.  
  
     Der Designer für das ausgewählte Artefakt wird geöffnet.  
  
- Wenn Sie ein Dashboard oder einen Geschäftsprozessfluss entfernen möchten, wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel zu erweitern. Wählen Sie dann das Dashboard oder den Geschäftsprozessfluss, das oder den Sie entfernen möchten. Wählen Sie auf der Befehlsleiste **Entfernen** aus.  

    Eine weitere Methode, ein Dashboard oder einen Geschäftsprozessfluss zu entfernen, ist, die entsprechenden Kontrollkästchen auf der Registerkarte **Komponenten** zu deaktivieren.
  
- Zum Bearbeiten oder Entfernen einer Entität wählen Sie die Entitätskachel und dann auf der Befehlsleiste **Bearbeiten** oder **Entfernen**. Wenn Sie eine Entität bearbeiten, öffnet der Lösungsexplorer, wo Sie Änderungen an der Entität vornehmen können.  
  
     Alternativ wählen Sie das Dashboard oder den Geschäftsprozessfluss oder die Entitätskachel aus, um eine Komponente zu entfernen. Deaktivieren Sie auf der Registerkarte **Komponenten** die Kontrollkästchen für die Artefakte, die Sie aus dem Designer entfernen möchten.  
  
    > [!NOTE]
    >  Wenn Sie Änderungen an einer Entität&mdash;vornehmen (beispielsweise das Ändern des Anzeigenamens der Entität oder der Beschreibung),&mdash;werden die Änderungen nicht im App-Designer angezeigt, es sei denn, die Änderungen werden im Projektmappen-Explorer veröffentlicht.  
  
## <a name="edit-or-remove-entity-assets"></a>Bearbeiten oder entfernen von Entitätsanlagen  

### <a name="edit-entity-assets"></a>Entitätsressourcen bearbeiten
  
1. Wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel für Formulare, Ansichten, Diagramme oder Dashboards zu erweitern.  
  
2. Wählen Sie das Formular, die Ansicht, das Diagramm oder das Dashboard, das Sie bearbeiten möchten.  
  
3. Klicken Sie auf der Befehlsleiste auf **Bearbeiten**.

   oder

   Wählen Sie die Schaltfläche Siteübersichtsdesigner ![Siteübersichtsdesigner öffnen](../model-driven-apps/media/dynamics365-open-designer.PNG "Schaltfläche "Siteübersichts-Designer öffnen""), die dem Formular, der Ansicht, dem Diagramm oder dem Dashboard entspricht.  

### <a name="remove-entity-assets"></a>Entfernen von Entitätsanlagen  

1. Wählen Sie den Pfeil nach unten ![Dropdown-Symbol](../model-driven-apps/media/drop-down-icon.png "Pfeil nach unten"), um die Kachel für Formulare, Ansichten, Diagramme oder Dashboards zu erweitern.  
  
2. Wählen Sie das Formular, die Ansicht, das Diagramm oder das Dashboard, das Sie bearbeiten möchten.

3. Wählen Sie auf der Befehlsleiste **Entfernen** aus. 

Alternativ können Sie die Kachel für Formulare, Ansichten, Diagrammen oder Dashboards auswählen und dann auf der Registerkarte **Komponenten** die Kontrollkästchen für die Ressourcen deaktivieren, die Sie aus dem Designer entfernen möchten.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [App-Siteübersicht erstellen](create-site-map-app.md) </br>  
 [App überprüfen und veröffentlichen](validate-app.md)

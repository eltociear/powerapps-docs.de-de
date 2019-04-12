---
title: Modell-angetriebene Appformularnavigation für zugehörige Entitäten in PowerApps hinzufügen | MicrosoftDocs
description: Mehr zu Formularnavigation für verknüpfte Entitäten hinzufügen
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
  - PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-model-driven-app-form-navigation-for-related-entities"></a>Modell-angetriebene Appformularnavigation für zugehörige Entitäten in PowerApps hinzufügen

In diesem Thema nutzen Sie das Formular Navigationsbereich, das verwendet wird, um verknüpfte Entitäten hinzufügen. Wenn ein App-Benutzer in einem Datensatz auf einen dieser Links klickt, wird die zugeordnete Ansicht für die Entität angezeigt.   
  
1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

  
    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 
  
3.  Öffnen Sie in der Liste der Formulare das Formular des Typs **Primär**, um es zu bearbeiten.  
  
4.  Wenn Sie einer verknüpften Entität einen Link hinzufügen möchten, wählen Sie auf der Registerkarte **Start** in der Gruppe **Auswählen** die Option **Navigation**.  
  
     Der Bereich **Beziehungs-Explorer** wird auf der rechten Seite des Formular-Editors geöffnet.  
  
5.  Wählen Sie im Bereich **Beziehungs-Explorer** in der Liste **Filter** eine der folgenden Optionen aus:  
  
    - **Verfügbare Beziehungen**. Listet alle Entitäten auf, die mit der Entität verknüpft werden können, der das Formular zugeordnet ist.  
  
    - **n:1-Beziehungen**. Listet Entitäten auf, die als 1:n-Beziehung mit der Entität verknüpft werden können, der das Formular zugeordnet ist.  
  
    - **N:N-Beziehungen**. Listet Entitäten auf, die als N:N-Beziehung mit der Entität verknüpft werden können, der das Formular zugeordnet ist.  
  
    > [!NOTE]
    >  Wenn im Bereich **Beziehungs-Editor** keine zugehörigen Entitäten angezeigt werden, können Sie von diesem Formular aus keine Verknüpfung zu einer verbundenen Entität herstellen.  
  
6.  Wählen Sie die verbundene Entität aus, zu der Sie eine Verknüpfung herstellen wollen, ziehen Sie sie in den Navigationsbereich, und legen Sie sie dort ab, wo sie angezeigt werden soll.  
  
    > [!TIP]
    >  Sie können auch eine neue Beziehung erstellen, indem Sie im Bereich **Beziehungs-Explorer** die Schaltfläche **Neue 1:n-Beziehung** oder **Neue N:N-Beziehung** wählen.   
  
7. Zum Bearbeiten der Eigenschaften des Links für diese oder für eine andere verknüpfte Entität im Navigationsbereich, markieren Sie den Link, und wählen Sie dann auf der Registerkarte **Start** die Option **Eigenschaften ändern**.  
  
8. Geben Sie im Dialogfeld **Beziehungseigenschaften** auf der Registerkarte **Anzeige** eine neue Anzeigebeschriftung ein.  
  
9. Wählen Sie auf der Registerkarte **Name** die Option **Bearbeiten**, um Details anzuzeigen oder zu bearbeiten, die dem Beziehungsdatensatz zugeordnet sind.  
  
10. Wählen Sie **OK**.  
  
11. Prüfen Sie in einer Vorschau die Darstellung des Hauptformulars und die Funktionsweise der Ereignisse:  
  
    1.  Wählen Sie auf der Registerkarte **Homepage** die Option **Vorschau** aus, und wählen Sie dann **Formular erstellen**, **Formular aktualisieren** oder **Schreibgeschütztes Formular** aus.  
  
    2.  Wählen Sie zum Schließen des Formulars **Vorschau** im Menü **Datei** die Option **Schließen** aus.  
  
12. Wenn Sie die Bearbeitung des Formulars abgeschlossen haben, wählen Sie zum Schließen des Formulars **Speichern und schließen**.  
  
13. Sind die Anpassungen vollständig, können sie veröffentlicht werden:  
  
    -   Wenn Sie Anpassungen für ausschließlich die Komponente veröffentlichen möchten, die Sie gerade bearbeiten, wählen Sie in der Navigationsleiste die Entität aus, an der Sie gearbeitet haben, und wählen Sie dann **Veröffentlichen** aus.  
  
    -   Um Anpassungen für alle nicht veröffentlichten Komponenten gleichzeitig zu veröffentlichen, wählen Sie in der Navigationsleiste **Entitäten** und dann auf der Befehlsleiste **Alle Anpassungen veröffentlichen** aus.  
  
> [!NOTE]
> Das Installieren einer Lösung oder Veröffentlichen von Anpassungen kann den normalen Systembetrieb stören. Wir empfehlen, dass Sie einen Lösungsimport planen, wenn er Benutzer am wenigsten stört.
  
## <a name="next-steps"></a>Nächste Schritte  
 [Erstellen und Bearbeiten von Entitäts-Beziehungen für Common Data Service](../common-data-service/create-edit-entity-relationships.md)

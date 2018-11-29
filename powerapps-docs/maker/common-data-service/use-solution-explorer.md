---
title: Verwenden von Lösungen in PowerApps | MicrosoftDocs
description: 'Hier erfahren Sie, wie Sie die Lösung nutzen, um Apps zu erstellen oder anzupassen'
ms.custom: ''
ms.date: 10/29/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-solutions-in-powerapps"></a>Verwenden von Lösungen in PowerApps

 In PowerApps können Sie eine Liste mit Lösungen anzeigen, indem Sie in der linken Navigation die Option **Lösungen** wählen. Sie können dann eine Lösung wählen, um alle ihrer Komponenten anzuzeigen. 
 
> [!NOTE]
>  Die Lösungserfahrung ist nur online und für Umgebungen ab Version 9.1.0.267 und höher verfügbar. Um Ihre Version zu prüfen, gehen Sie zu [PowerApps-Administratorcenter](https://admin.powerapps.com/) > Umgebungen > wählen Sie Ihre Umgebung > Registerkarte „Details”. Bei Instanzen mit einer früheren Version wird durch die Auswahl einer Lösung eine Instanz in der klassischen Umgebung geöffnet. 

> [!div class="mx-imgBorder"]  
> ![Demolösung mit allen Komponenten](media/solution-all-items-list.PNG "Demolösung mit allen Komponenten")  
  
 
 Sie können alle Komponenten einer Lösung durchsuchen, indem Sie durch die Elemente scrollen. Wenn mehr als 100 Elemente in der Liste vorhanden sind, können Sie die Option **Die nächsten 100 Elemente laden** wählen, um mehr anzuzeigen. 
 
> [!div class="mx-imgBorder"]  
> ![Laden weiterer Komponenten](media/load-more.PNG "Laden weiterer Komponenten")  

 ## <a name="search-and-filter-in-a-solution"></a>Suchen und Filtern in einer Lösung
 
 Sie können anhand des Namens nach einer bestimmten Komponente suchen. 
 
> [!div class="mx-imgBorder"]  
> ![Suchkomponente](media/solution-search-box.PNG "Suchkomponente")  
 
 Oder filtern Sie die Elemente in der Liste anhand des Komponententyps.
  
> [!div class="mx-imgBorder"]  
> ![Filterkomponente anhand des Typs](media/solution-filter.PNG "Filterkomponente anhand des Typs")  
 
 ## <a name="contextual-commands"></a>Kontextbefehle
 
 Bei der Auswahl der einzelnen Komponenten ändern sich die in der Befehlsleiste zur Verfügung stehenden Aktionen je nach dem Typ der ausgewählten Komponente sowie danach, ob es sich um die Standardlösung oder um eine verwaltete Lösung handelt. 
 
> [!div class="mx-imgBorder"]  
> ![Komponentenspezifische Befehle](media/component-commands.PNG "Komponentenspezifische Befehle")  
 
 Wenn Sie keine Komponente wählen, werden in der Befehlsleiste die Aktionen angezeigt, die auf die Lösung angewendet werden. 
 
> [!div class="mx-imgBorder"]  
> ![Lösungsspezifische Befehle](media/solution-commands.PNG "Lösungsspezifische Befehle")  
 
 ## <a name="create-components-in-a-solution"></a>Erstellen von Komponenten in einer Lösung
 Bei Lösungen, die nicht verwaltet oder standardmäßig sind, können Sie den Befehl **Neu** verwenden, um unterschiedliche Typen von Komponenten zu erstellen. So erhalten Sie eine neue Erfahrung während des Erstellprozesses, je nach Typ der ausgewählten Komponente. Nachdem Sie die Komponente erstellt haben, wird sie zur Lösung hinzugefügt. 
 
> [!div class="mx-imgBorder"]  
> ![Erstellen einer neuen Komponente in einer Lösung](media/solution-new-component.PNG "Erstellen einer neuen Komponente in einer Lösung")  
 
 ## <a name="add-an-existing-component-to-a-solution"></a>Hinzufügen einer vorhandenen Komponente zu einer Lösung
 
 Bei nicht verwalteten Lösungen, die nicht die Standardlösung sind, können Sie den Befehl **Vorh. hinzufügen** verwenden, um die Komponenten einzufügen, die sich nicht bereits in der Lösung befinden.  
 
> [!div class="mx-imgBorder"]  
> ![Vorhandene Komponente einer Lösung hinzufügen](media/solution-add-existing-component.PNG "Vorhandene Komponente einer Lösung hinzufügen")  
  
 Bei verwalteten Lösungen sind keine Befehle verfügbar, und Sie sehen die unten angezeigte Message. Sie müssen die Komponente in der Lösung namens **Standardlösung** suchen und versuchen, sie dort zu bearbeiten, oder sie einer anderen von Ihnen erstellten nicht verwalteten Lösung hinzuzufügen. Möglicherweise kann die Komponente nicht angepasst werden. Weitere Informationen: [Verwaltete Eigenschaften](solutions-overview.md#managed-properties)

> [!div class="mx-imgBorder"]  
> ![Verwaltete Lösung](media/managed-solution.PNG "Verwaltete Lösung")  

 Viele der Anpassungen, die Sie ausführen möchten, werden Entitäten einbeziehen. Sie können den Filter **Entität** verwenden, um eine Liste aller Entitäten in der aktuellen Lösung anzuzeigen, die in irgendeiner Weise angepasst werden können. Sobald Sie Detailinformationen zu einer Entität anzeigen, können Sie die Komponenten sehen, die Teil der Entität sind, wie im folgenden Screenshot mit der Firmenentität gezeigt: 
 
> [!NOTE]
>  Wenn Sie derzeit eine bereits vorhandene Entität einer Lösung hinzufügen, fügt das System automatisch alle Komponenten der Lösung hinzu, die Teil der Entität sind. Wenn dies nicht Ihre bevorzugte Möglichkeit ist, verwenden Sie den Befehl **In klassischen Modus wechseln**, um zur klassischen Erfahrung zu wechseln, und fügen Sie nur die Komponenten hinzu, die Sie möchten. <!-- We will soon improve this experience from PowerApps and allow you to select only the specific component(s) under entity that you want to add into a solution. -->
  
> [!div class="mx-imgBorder"]  
> ![Demolösung, die eine erweiterte Firmenentität anzeigt](media/solution-entity-account.PNG "Demolösung, die eine erweiterte Firmenentität anzeigt")  

## <a name="classic-solution-explorer"></a>Klassischer Projektmappen-Explorer

In PowerApps können Sie den klassischen Projektmappen-Explorer anzeigen, indem Sie im linken Navigationsbereich **Lösungen** und dann **In klassischen Modus wechseln** in der Befehlsleiste wählen. Der klassische Projektmappen-Explorer ist derjenige, der zuvor über den Bereich **Einstellungen > Erweiterte Anpassungen** in PowerApps verfügbar war. Falls Sie Dynamics 365 for Customer Engagement-Benutzer sind, verwenden Sie den klassischen Projektmappen-Explorer für die Arbeit mit Lösungen.  

## <a name="known-limitations"></a>Bekannte Einschränkungen

- Durch das Löschen oder Entfernen einer verwalteten Lösung wird nicht die Canvas-App aus PowerApps gelöscht.
- Benutzerdefinierte Konnektoren sind nicht in einer Lösung verfügbar.
- Canvas-Apps müssen nach dem Import einer Lösung geöffnet sein, um die Verbindungen zu aktualisieren.
- Nach dem Hinzufügen einer vorhandenen SDK-Assembly wird diese nicht in der Lösung angezeigt. 
- Wenn Canvas-Apps in einer verwalteten Lösung gepackt sind, können Sie auch in der neuen Umgebung noch von den Administratoren bearbeitet werden.
- Abhängigkeiten sind für Canvas-Apps nicht verfügbar
- Durch das Löschen einer verwalteten Lösung wird kein Rollback auf eine andere Version der Canvas-App ausgeführt 
-   Der Zugriff auf Canvas-Apps (CRUD und Sicherheit) wird vollständig in PowerApps und nicht in der Common Data Service-Datenbank verwaltet
-   CDS-APIs zum Aufrufen von Canvas-Apps werden blockiert und geben nichts mehr zurück 
-   In einer Lösung erstellte Canvas-Apps können als Miteigentümer einer AAD-Sicherheitsgruppe nicht geteilt werden
-   Canvas-Apps werden nicht im klassischen Projektmappen-Explorer angezeigt 
-   Vorhandene Canvas-Apps sind nicht lösungsfähig 

 Ausführliche Informationen zum Anpassen einzelner Lösungskomponenten finden Sie in den folgenden Themen:  
  
-   Informationen zu Entitäten, Entitätsbeziehungen, Feldern und Nachrichtenanpassungen finden Sie unter [Metadaten](create-edit-metadata.md).  
  
-   Für Entitätsformulare vgl. [Formulare](../model-driven-apps/create-design-forms.md).  
  
-   Für Prozesse vgl. [Prozesse](../model-driven-apps/guide-staff-through-common-tasks-processes.md).  
  
-   Für Geschäftsregeln siehe [Geschäftsregeln](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).  

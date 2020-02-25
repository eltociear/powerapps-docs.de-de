---
title: Lösungen in Power Apps verwenden | MicrosoftDocs
description: Hier erfahren Sie, wie Sie die Lösung nutzen, um Apps zu erstellen oder anzupassen
ms.custom: ''
ms.date: 10/28/2019
ms.reviewer: tapanm
ms.service: powerapps
ms.topic: article
author: caburk
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: caburk
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c926e0fb48791879ea88c19212b30c79731cb3be
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "3004862"
---
# <a name="use-solutions-in-power-apps"></a>Lösungen in Power Apps verwenden

 Innerhalb von Power Apps können Sie eine Liste von Lösungen einsehen, indem Sie **Lösungen** in der linken Navigation auswählen. Sie können dann eine Lösung wählen, um alle ihrer Komponenten anzuzeigen. 
 
> [!div class="mx-imgBorder"]  
> ![Demolösung mit allen Komponenten](media/solution-all-items-list.PNG "Demolösung mit allen Komponenten")  
 
> [!NOTE]
>  Die Lösungserfahrung ist nur online und für Umgebungen ab Version 9.1.0.267 und höher verfügbar. Um Ihre Version zu überprüfen, gehen Sie bitte zu ...[Power Apps Admin-Center](https://admin.powerapps.com/)> **Umgebungen** > wählen Sie Ihre Umgebung > **Details** Registerkarte. Für Umgebungen mit früheren Versionen öffnet die Auswahl einer Lösung diese im klassischen Sinne.  
 
 Sie können alle Komponenten einer Lösung durchsuchen, indem Sie durch die Elemente scrollen. Wenn mehr als 100 Elemente in der Liste vorhanden sind, können Sie die Option **Die nächsten 100 Elemente laden** wählen, um mehr anzuzeigen. 
 
> [!div class="mx-imgBorder"]  
> ![Laden weiterer Komponenten](media/load-more.PNG "Laden weiterer Komponenten")  

 ## <a name="search-and-filter-in-a-solution"></a>Suchen und Filtern in einer Lösung
 
 Sie können anhand des Namens nach einer bestimmten Komponente suchen. 
 
> [!div class="mx-imgBorder"]  
> ![Suche nach Komponenten](media/solution-search-box.png "Suche nach Komponenten")  
 
 Oder filtern Sie die Elemente in der Liste anhand des Komponententyps.
  
> [!div class="mx-imgBorder"]  
> ![Komponente nach Typ filtern](media/solution-filter.PNG "Komponente nach Typ filtern")  
 
 ## <a name="contextual-commands"></a>Kontextbefehle
 
 Bei der Auswahl der einzelnen Komponenten ändern sich die in der Befehlsleiste zur Verfügung stehenden Aktionen je nach dem Typ der ausgewählten Komponente sowie danach, ob es sich um die Standardlösung oder um eine verwaltete Lösung handelt. 
 
> [!div class="mx-imgBorder"]  
> ![Komponentenspezifische Befehle](media/component-commands.png "Komponentenspezifische Befehle")  
 
 Wenn Sie keine Komponente wählen, werden in der Befehlsleiste die Aktionen angezeigt, die auf die Lösung angewendet werden. 
 
> [!div class="mx-imgBorder"]  
> ![Lösungsspezifische Befehle](media/solution-commands.PNG "Lösungsspezifische Befehle")  
 
 ## <a name="create-components-in-a-solution"></a>Erstellen von Komponenten in einer Lösung
 Bei Lösungen, die nicht verwaltet oder standardmäßig sind, können Sie den Befehl **Neu** verwenden, um unterschiedliche Typen von Komponenten zu erstellen. So erhalten Sie eine neue Erfahrung während des Erstellprozesses, je nach Typ der ausgewählten Komponente. Nachdem Sie die Komponente erstellt haben, wird sie zur Lösung hinzugefügt. 
 
> [!div class="mx-imgBorder"]  
> ![Neue Komponente in einer Lösung erstellen](media/solution-new-component.PNG "Neue Komponente in einer Lösung erstellen")  
 
 ## <a name="add-an-existing-component-to-a-solution"></a>Hinzufügen einer vorhandenen Komponente zu einer Lösung
 
 Bei nicht verwalteten Lösungen, die nicht die Standardlösung sind, können Sie den Befehl **Vorh. hinzufügen** verwenden, um die Komponenten einzufügen, die sich nicht bereits in der Lösung befinden.  
 
> [!div class="mx-imgBorder"]  
> ![Hinzufügen einer vorhandenen Komponente zu einer Lösung](media/solution-add-existing-component.PNG "Hinzufügen einer vorhandenen Komponente zu einer Lösung")  
  
 Bei verwalteten Lösungen sind nur bestimmte Befehle verfügbar, und Sie sehen die unten angezeigte Message. Sie müssen es zu einer anderen nicht verwalteten Lösung hinzufügen, die Sie erstellt haben, um die Komponente anzupassen. Möglicherweise kann die Komponente nicht angepasst werden. Weitere Informationen: [Verwaltete Eigenschaften](solutions-overview.md#managed-properties)

> [!div class="mx-imgBorder"]  
> ![Verwaltete Lösung](media/managed-solution.PNG "Verwaltete Lösung")  

 Viele der Anpassungen, die Sie ausführen möchten, werden Entitäten einbeziehen. Sie können den Filter **Entität** verwenden, um eine Liste aller Entitäten in der aktuellen Lösung anzuzeigen, die in irgendeiner Weise angepasst werden können. Sobald Sie Detailinformationen zu einer Entität anzeigen, können Sie die Komponenten sehen, die Teil der Entität sind, wie im folgenden Screenshot mit der Firmenentität gezeigt: 
   
> [!div class="mx-imgBorder"]  
> ![Demolösung, die eine erweiterte Firmenentität anzeigt](media/solution-entity-account.png "Demolösung, die eine erweiterte Firmenentität anzeigt")  

## <a name="classic-solution-explorer"></a>Klassischer Projektmappen-Explorer

In Power Apps können Sie den klassischen Lösungsexplorer anzeigen, indem Sie im linken Navigationsbereich **Lösungen** auswählen und dann **Zum Klassiker wechseln** in der Befehlsleiste wählen. Der klassische Lösungsexplorer ist derjenige, der zuvor über den Bereich **Einstellungen > Erweiterte Anpassungen** in Power Apps verfügbar war. 

## <a name="known-limitations"></a>Bekannte Einschränkungen

Die folgenden Beschränkungen gelten für die Verwendung von Canvas-Apps, Flows und benutzerdefinierten Connectors in Lösungen. 

- Von der Schaltfläche Canvas-App ausgelöste Flows sind in Lösungen nicht untertstützt. Erstellen Sie die App und den Flow außerhalb einer Lösung und exportieren Sie die .msapp-Datei, um Canvas-Apps mit einem eingebetteten, durch Schaltflächen ausgelösten Flow zu migrieren. 
- Wenn eine Canvas-App in eine verwalteten Lösung gepackt wurde, kann sie in der Zielumgebung nicht bearbeitet und erneut veröffentlicht werden. Verwenden Sie nicht verwaltete Lösungen, wenn die Apps in der Zielumgebung Bearbeitung erfordern. 
- Verbindungen erfordern die Authentifizierung und Zustimmung, was eine interaktive Benutzersitzung erfordert, und können daher nicht über Lösungen übermittelt werden. Nachdem Sie die Lösung importiert haben, geben Sie die App wieder, um die Verbindungen zu authentifizieren. Sie können die Verbindungen auch vor dem Import der Lösung in der Zielumgebung anlegen. 
-   Canvas-Apps, die als Miteigentümer für eine Azure Active Directory (AAD)-Sicherheitsgruppe freigegeben wurden, können nicht zu Lösungen hinzugefügt werden. Heben Sie die Freigabe der App auf, bevor Sie sie zu einer Lösung hinzufügen.
-   Canvas-Apps werden nicht im klassischen Projektmappen-Explorer angezeigt. Verwenden Sie die moderne Erfahrung.
-   Der Zugriff auf Canvas-Apps (CRUD und Sicherheit) wird vollständig in Power Apps und nicht in der Common Data Service-Datenbank verwaltet.
- Datenbankvorgänge wie Sicherung, Wiederherstellung und Kopieren werden für Canvas-Apps und -Flows nicht unterstützt. Diese Vorgänge können Canvas-Apps und -Flows beschädigten.
- Durch das Löschen einer verwalteten Lösung wird kein Rollback auf eine andere Version der Canvas-App ausgeführt. Stattdessen werden alle Versionen der App gelöscht.
- Wenn eine Lösung importiert wird, die einen Flow enthält, werden die erforderlichen Verbindungen nicht automatisch erstellt oder zugeordnet. Der Flow muss bearbeitet werden, um feste Verbindungen sicherzustellen.
  - Wenn Sie verwaltete Lösungen verwenden, wird eine aktive Anpassung in der nicht verwalteten Ebene erstellt. Daher werden die nachfolgenden Lösungsupdates für den Flow nicht berücksichtigt. 
- Aus Lösungen erstellte Flows werden in der Liste „Team Flows“ nicht angezeigt. Der Zugriff muss über eine Lösung erfolgen. 
- Über eine Schaltfläche ausgelöste Flows sind in Lösungen nicht verfügbar.
- Aus Microsoft 365-Anwendungen wie Excel ausgelöste Flows sind in Lösungen nicht verfügbar.
- Flows, die mit SharePoint verbunden sind, sind in Lösungen nicht verfügbar.
- Flows in Lösungen unterstützen keine delegierte Authentifizierung. Beispielsweise wird der Zugriff auf einen Flow nicht automatisch anhand des Zugriffs auf die SharePoint-Liste erteilt, aus der der Flow erstellt wurde.
- Die außerhalb von Lösungen erstellten benutzerdefinierten Connectors können derzeit nicht zu Lösungen hinzugefügt werden.


 Ausführliche Informationen zum Anpassen einzelner Lösungskomponenten finden Sie in den folgenden Themen:  
  
-   Informationen zu Entitäten, Entitätsbeziehungen, Feldern und Nachrichtenanpassungen finden Sie unter [Metadaten](create-edit-metadata.md).  
  
-   Für Entitätsformulare vgl. [Formulare](../model-driven-apps/create-design-forms.md).  
  
-   Für Prozesse vgl. [Prozesse](../model-driven-apps/guide-staff-through-common-tasks-processes.md).  
  
-   Für Geschäftsregeln siehe [Geschäftsregeln](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).  

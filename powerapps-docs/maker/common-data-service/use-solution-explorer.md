---
title: Lösungs-Explorer in PowerApps nutzen | MicrosoftDocs
description: 'Hier erfahren Sie, wie Sie Lösungsexplorer nutzen, um Apps zu erstellen oder anzupassen'
ms.custom: ''
ms.date: 06/18/2018
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
# <a name="use-the-solution-explorer"></a>Verwenden des Lösungsexplorers

 Innerhalb des Lösungsexplorers können Sie durch eine Hierarchie von Knoten mithilfe des Navigationsbereichs links, wie im folgenden Screenshot gezeigt, navigieren:  
  
 ![Standardlösung mit reduzierten Entitäten](media/crm-itpro-cust-defaultsolutionentitiescollapsed.PNG "Standardlösung mit reduzierten Entitäten")  
  
> [!NOTE]
>  Verwenden Sie die Maus und die Tastatur, wenn Sie mit Anpassungstools im Lösungs-Explorer arbeiten. Dieser Bereich der Anwendung ist nicht für Touch optimiert.  
  
 Wenn Sie die einzelnen Knoten auswählen, sehen Sie eine Liste der Lösungskomponenten. Die Aktionen, die in der Befehlsleiste zur Verfügung stehen, ändern sich je nach dem Kontext des ausgewählten Knotens sowie danach, ob es sich um die Standardlösung oder um eine verwaltete Lösung handelt. Bei nicht verwalteten Lösungen, die nicht die Standardlösung sind, können Sie den Befehl **Vorhandenes Element hinzufügen** verwenden, um die Lösungskomponenten einzufügen, die sich nicht bereits in der Lösung befinden.  
  
Bei verwalteten Lösungen sind keine Befehle verfügbar, und Sie sehen die Meldung:  

> [!NOTE]
> Sie können die Komponenten in einer verwalteten Lösung nicht direkt bearbeiten. Wenn die verwalteten Eigenschaften für Lösungskomponenten so festgelegt sind, dass Anpassungen erlaubt sind, können Sie diese mit einem PowerApps Design-Tool oder von einer anderen nicht verwalteten Lösung aus bearbeiten.    
  
 Sie müssen die Lösungskomponente in der Standardlösung suchen und versuchen, sie dort zu bearbeiten, oder sie einer anderen von Ihnen erstellten nicht verwalteten Lösung hinzuzufügen. Möglicherweise kann die Lösungskomponente nicht angepasst werden. Weitere Informationen: [Verwaltete Eigenschaften](solutions-overview.md#managed-properties)
  
 Viele der Anpassungen, die Sie ausführen möchten, werden Entitäten einbeziehen. Sie können den Knoten **Entitäten** erweitern, um eine Liste aller Entitäten im System anzuzeigen, die in irgendeiner Weise angepasst werden können. Sie können jede Entität weiter erweitern, um die Lösungskomponenten anzuzeigen, die Teil der Entität sind, wie im folgenden Screenshot mit der Firmenentität gezeigt:  
  
 ![Standardlösung, die eine erweiterte Firmenentität anzeigt](media/crm-itpro-cust-defaultsolution.PNG "Standardlösung, die eine erweiterte Firmenentität anzeigt")  
  
 Ausführliche Informationen zum Anpassen einzelner Lösungskomponenten im Lösungsexplorer finden Sie in den folgenden Themen:  
  
-   Informationen zu Entitäten, Entitätsbeziehungen, Feldern und Nachrichtenanpassungen finden Sie unter [Metadaten](create-edit-metadata.md).  
  
-   Für Entitätsformulare vgl. [Formulare](../model-driven-apps/create-design-forms.md).  
  
-   Für Prozesse vgl. [Prozesse](../model-driven-apps/guide-staff-through-common-tasks-processes.md).  
  
-   Für Geschäftsregeln siehe [Geschäftsregeln](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md).  

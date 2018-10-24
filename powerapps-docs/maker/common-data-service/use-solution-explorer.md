---
title: Verwenden des Projektmappen-Explorers in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit dem Projektmappen-Explorer Apps erstellen und anpassen.
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
ms.openlocfilehash: 6abbe701a6207e68ac367fbe80495a7d04a6e682
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683561"
---
# <a name="use-the-solution-explorer"></a>Verwenden des Projektmappen-Explorers

 Sie können im Projektmappen-Explorer über den Navigationsbereich auf der linken Seite durch eine Knotenhierarchie navigieren:  
  
 ![Standardlösung mit ausgeblendeten Entitäten](media/crm-itpro-cust-defaultsolutionentitiescollapsed.PNG "Standardlösung mit ausgeblendeten Entitäten")  
  
> [!NOTE]
>  Verwenden Sie Maus und Tastatur, wenn Sie im Projektmappen-Explorer mit Anpassungstools arbeiten. Dieser Teil der Anwendung ist nicht für die Toucheingabe optimiert.  
  
 Wenn Sie die einzelnen Knoten auswählen, wird eine Liste der Lösungskomponenten angezeigt. Die in der Befehlsleiste verfügbaren Aktionen hängen davon ab, welchen Knoten Sie auswählen, und ob es sich um die Standard- oder eine verwaltete Lösung handelt. Bei nicht verwalteten Lösungen, die nicht die Standardlösung sind, können Sie den Befehl **Vorhandenes Element hinzufügen** verwenden, um Lösungskomponenten zu integrieren, die sich nicht bereits in der Lösung befinden.  
  
Bei verwalteten Lösungen sind keine Befehle verfügbar und wird diese Meldung angezeigt:  

> [!NOTE]
> Die Komponenten können nicht direkt in einer verwalteten Lösung bearbeitet werden. Wenn die verwalteten Eigenschaften für Lösungskomponenten für das Zulassen von Anpassungen festgelegt werden, können sie mit einem PowerApps-Designtool oder über eine andere nicht verwaltete Lösung bearbeitet werden.    
  
 Sie müssen die Lösungskomponente in der Standardlösung finden und sie dort bearbeiten oder sie einer anderen nicht verwalteten Lösung hinzufügen, die Sie erstellt haben. Die Lösungskomponente ist möglicherweise nicht anpassbar. Weitere Informationen finden Sie unter [Verwaltete Eigenschaften](solutions-overview.md#managed-properties).
  
 Viele Anpassungen, die Sie vornehmen möchten, beziehen sich auf Entitäten. Sie können den Knoten **Entitäten** erweitern, um eine Liste aller Entitäten im System anzuzeigen, die angepasst werden können. Sie können jede Entität weiter erweitern, um die Lösungskomponenten anzuzeigen, die Teil der Entität sind. Dieser Screenshot veranschaulicht das anhand der Entität „Konto“:  
  
 ![Standardlösung mit erweiterter Entität „Konto“](media/crm-itpro-cust-defaultsolution.PNG "Standardlösung mit erweiterter Entität „Konto“")  
  
 Weitere Informationen zum Anpassen der einzelnen Lösungskomponenten im Projektmappen-Explorer finden Sie in den folgenden Themen:  
  
-   Anpassungen an Entitäten, Entitätsbeziehungen, Feldern und Meldungen: [Metadaten](create-edit-metadata.md)  
  
-   Anpassungen an Entitätsformularen: [Formulare](../model-driven-apps/create-design-forms.md)  
  
-   Anpassungen an Prozessen: [Prozesse](../model-driven-apps/guide-staff-through-common-tasks-processes.md)  
  
-   Anpassungen an Geschäftsregeln: [Geschäftsregeln](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)  

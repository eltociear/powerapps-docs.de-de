---
title: Erstellen einer persönlichen Ansicht mithilfe erweiterter Rasterfilter | Microsoft-Dokumentation
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 04/02/2020
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0a27f7104b85b8ae45146ea7a3626cd1b0e2157c
ms.sourcegitcommit: 3e6c499a65ada8a9f28022a02f64030b0c069a17
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80661326"
---
# <a name="edit-or-create-personal-views-using-advanced-grid-filters"></a>Erstellen oder Bearbeiten persönlicher Ansichten mithilfe erweiterter Rasterfilter 

Mit den erweiterten Filteroptionen können Sie eine persönliche Ansicht erstellen, um die Datensätze einzusehen, die Ihnen wichtig sind. Mithilfe der erweiterten Filteroptionen können Sie eine Vielzahl von Ansichten von einfach bis komplex erstellen. Außerdem können Sie den Filtern gruppierte und geschachtelte Bedingungen hinzufügen.


> [!NOTE]
> Die erweiterte Filteroption ist nur in Versionen in englischer Sprache verfügbar.

Wenn Sie eine persönliche Ansicht erstellen und speichern, wird sie in Ihrer Liste der persönlichen Ansichten unter **Meine Ansichten** angezeigt.

> [!div class="mx-imgBorder"]
> ![Persönliche Ansichten](media/my_peronsal_view.png "Persönliche Ansichten")


## <a name="see-the-current-view-definition"></a>Anzeigen der aktuellen Ansichtsdefinition

Um zu prüfen, welche Filter auf die aktuelle Ansicht angewendet wurden, wählen Sie eine Ansicht und dann **Filter** ![Filtersymbol](media/commandbar_filter_icon.png "Filtersymbol") aus. Der Ausdrucks-Generator wird geöffnet und die Standardansichtsdefinition angezeigt.

> [!div class="mx-imgBorder"] 
> ![Aktuelle Ansichtsdefinition](media/current_view_def.gif "Diese Abbildung zeigt, wie die Filter für die Ansicht angezeigt werden.")

## <a name="add-conditions-to-filters"></a>Hinzufügen von Bedingungen zu Filtern

1. Um die aktuelle Ansicht zu bearbeiten und weitere Filter hinzuzufügen, wählen Sie eine Ansicht und dann **Filter** ![Filtersymbol](media/commandbar_filter_icon.png "Filtersymbol") aus.
2. Verwenden Sie auf dem Bildschirm **Erweiterte Filter** den Ausdrucks-Generator, um Bedingungen zu Filtern hinzuzufügen. Weitere Informationen zum Hinzufügen von Bedingungen finden Sie unter [Hinzufügen von Bedingungen zu einem Filter](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-conditions-to-a-filter).
3. Wenn Sie fertig sind, wählen Sie **Übernehmen** aus. 

   > [!div class="mx-imgBorder"] 
   > ![Hinzufügen von Filtern](media/add_filters.gif "Diese Abbildung zeigt, wie Filter mit dem Ausdrucks-Generator hinzugefügt werden können.")

### <a name="add-grouped-or-nested-conditions"></a>Hinzufügen gruppierter oder geschachtelter Bedingungen

Um Ihre Daten eingehender zu untersuchen, können Sie den Filtern gruppierte oder geschachtelte Bedingungen hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen einer Gruppenbedingung zu einem Filter](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-a-group-condition-to-a-filter).

   > [!div class="mx-imgBorder"] 
   > ![Hinzufügen einer gruppierten oder geschachtelten Bedingung](media/group_condition.gif "Diese Abbildung zeigt, wie einem Filter eine gruppierte oder geschachtelte Bedingung hinzugefügt wird.")

### <a name="clear-filters"></a>Löschen von Filtern

Um angewendete Filter zu löschen und die Ansicht wieder auf die Ursprungsdefinition zurückzusetzen, wählen Sie **Filter löschen** ![Symbol „Filter löschen“](media/clear_filter_icon.png "Symbol „Filter löschen“") aus.

### <a name="save-your-personal-view"></a>Speichern Ihrer persönlichen Ansicht

Ein Sternchen neben einem Ansichtsnamen gibt an, dass die Ansicht nicht gespeichert wurde. 

   > [!div class="mx-imgBorder"] 
   > ![Nicht gespeicherte Ansicht](media/unsaved_view.png "Nicht gespeicherte Ansicht")

1. Um eine persönliche Ansicht zu speichern, wählen Sie auf der Befehlsleiste **Mehr** ![Symbol „Mehr](media/commandbar_more_icon.png "Symbol „Mehr“") aus. 
2. Wählen Sie **Ansicht erstellen** > **Filter als neue Ansicht speichern** aus.
3. Geben Sie im Dialogfeld **Als neue Ansicht speichern** einen Namen und eine Beschreibung für die Ansicht ein, und wählen Sie dann **Speichern** aus.
4. Die Ansicht wird in Ihrer Liste der persönlichen Ansichten unter **Meine Ansichten** angezeigt.

   > [!div class="mx-imgBorder"] 
   > ![Speichern einer persönlichen Ansicht](media/save_personal_view.gif "Diese Abbildung zeigt, wie Sie eine persönliche Ansicht speichern können.")


   

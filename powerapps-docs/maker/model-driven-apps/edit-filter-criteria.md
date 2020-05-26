---
title: Bearbeiten der Filterkriterien und Ändern der Sortierreihenfolge in modellgesteuerten App-Ansichten mit Power Apps | Microsoft-Dokumentation
description: Informationen zum Bearbeiten der Filterkriterien und Ändern der Sortierreihenfolge in Ansichten
ms.custom: ''
ms.date: 03/26/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: fecf23c9-05e6-4397-9a5d-37210bcc2816
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fd5541059b743115a56614671b72e5e00deabfd2
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285562"
---
# <a name="edit-filter-criteria-and-change-sort-order-in-model-driven-app-views"></a>Bearbeiten der Filterkriterien und Ändern der Sortierreihenfolge in modellgesteuerten App-Ansichten

<a name="BKMK_EditFilterCriteria"></a>   

Zusammen mit den Spalten, die in einer Ansicht angezeigt werden, sind die Filterkriterien, die auf eine Ansicht angewendet werden, ein wichtiger Faktor beim Wert, den eine Ansicht bietet. Sie können Filterkriterien hinzufügen oder bearbeiten und die Sortierfolge für die Spalten, die Sie in eine Ansicht aufnehmen, ändern. Wenn für eine Ansicht keine Sortierfolge festgelegt wurde, wird die Ansicht standardmäßig nach dem Primärfeld in der Ansicht in aufsteigender Reihenfolge (A bis Z) sortiert.

## <a name="change-the-sort-order-of-a-view"></a>Ändern der Sortierreihenfolge einer Ansicht

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten**, wählen Sie **Entitäten** und dann die gewünschte Entität aus und wählen Sie die dann die Registerkarte **Ansichten** aus.

3.  Wählen Sie eine Ansicht aus, um sie im Ansichts-Designer zu öffnen.

    > [!div class="mx-imgBorder"] 
    > ![Filter bearbeiten](media/view-column-menu.png "Filter bearbeiten")

4.  Wählen Sie einen Feldnamen im Spaltenkopf und wählen Sie dann aus dem Spaltenmenü **Sortieren A bis Z** oder **Sortieren Z bis A**. Die Sortierreihenfolge wird im Spaltenkopf mit einem Pfeil nach oben oder einem Pfeil nach unten angezeigt.

Sie können auch die Sortierreihenfolge ändern, indem Sie das Ansichtseigenschaften-Panel verwenden. 

1.  Wenn für die Ansicht keine Sortierfolge festgelegt wurde, wählen Sie **Sortieren nach** und wählen Sie dann die primäre Sortierung nach Spalte.

2.  Wenn Sie die Ansicht nach zusätzlichen Spalten sortieren möchten, wählen Sie **Dann sortieren nach** und wählen Sie dann eine zusätzliche Sortierung nach Spalte für die Ansicht.

    Möglicherweise möchten Sie nach mehr als einer Spalte sortieren, wenn Sie Daten haben, die Sie nach demselben Wert in einer Spalte gruppieren möchten, und dann eine andere Spalte innerhalb dieser Gruppe von gleichen Werten sortieren.

3.  Um einen Sortierausdruck zu entfernen, wählen Sie **Sortierausdruck entfernen** (die Schaltfläche **X**).

## <a name="add-or-edit-filter"></a>Filter hinzufügen oder bearbeiten

1.  Wählen Sie eine Spalte, und wählen Sie im Spaltenmenü **Filtern nach**.

    > [!div class="mx-imgBorder"] 
    > ![Filter bearbeiten](media/edit-filter-criteria.png "Filter bearbeiten")

2.  Wählen Sie den Bedingungsoperator, den Sie verwenden möchten.

3.  Geben Sie den Vergleichswert für die Bedingung ein oder wählen Sie ihn aus.

4.  Wählen Sie **Übernehmen** aus.

    Die Filterausdrücke für eine Ansicht werden im Ansichtseigenschaften-Panel angezeigt.
    
5.  Um einen Filterausdruck zu bearbeiten, wählen Sie den Filterauswahlausdruck aus der Eigenschaftenleiste Ansicht.

6.  Um einen Filterausdruck zu entfernen, wählen Sie die Schaltfläche **X**. 

Sie können auch den Ausdrucksbildner im Ansichtsdesigner verwenden, um Filter für beliebige Felder der Entität in der aktuellen Ansicht oder beliebige Felder in einer verknüpften Entität hinzuzufügen oder zu bearbeiten. Weitere Informationen: [Erstellen oder bearbeiten Sie Filter in modellbasierten App-Ansichten](create-edit-view-filters.md)

## <a name="use-solution-explorer-to-edit-filter-criteria-and-change-sort-order"></a>Verwenden Sie den Lösungsexplorer, um Filterkriterien zu bearbeiten und die Sortierreihenfolge zu ändern

Sortierreihenfolge für eine Ansicht ändern.

1.  Öffnen Sie [Lösungsexplorer](advanced-navigation.md#solution-explorer), erweitern Sie **Entitäten**, wählen Sie die gewünschte Entität, wählen Sie **Ansichten** und öffnen Sie dann die gewünschte Ansicht.

2.  Im Ansicht-Designer wählen Sie **Sortieren konfigurieren** aus.  

    > [!div class="mx-imgBorder"] 
    > ![Konfigurieren der Sortierung](media/configure-sorting.png "Konfigurieren der Sortierung")
  
3.  Wählen Sie im Dialogfeld **Sortierreihenfolge konfigurieren** in der Liste **Sortieren nach** die Spalte aus, die Sie sortieren möchten. Wählen Sie **Aufsteigende Reihenfolge** oder **Absteigende Reihenfolge** aus.  
  
4.  Wählen Sie **OK**, um die Sortierreihenfolge zu speichern.  

Ändern Sie die Filterkriterien für eine Ansicht.

1.  Wenn Sie die Ansicht im Ansichtsdesigner erstellen oder bearbeiten, wählen Sie im Bereich **Allgemeine Aufgaben** die Option **Filterkriterien bearbeiten**.  
  
2.  Das Dialogfeld zeigt eine Benutzeroberfläche ähnlich wie **Erweiterte Suche** Sie können **AND** und **OR** Klauseln verwenden, um Kriterien zu spezifizieren und zu gruppieren, indem Sie die Filterklausel auswählen und dann **Gruppieren AND** oder **Gruppieren OR** wählen.  

3.  Wählen Sie **OK**, um die Filterkriterien zu speichern.  
  
Weitere Information zum Erstellenvon Filterklauseln finden Sie unter [Erstellen, Bearbeiten oder Speichern einer erweiterten Suche](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search).   
 
## <a name="next-steps"></a>Nächste Schritte
[Ansichten verstehen](create-edit-views.md)

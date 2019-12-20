---
title: Erstellen oder bearbeiten einer modellgesteuerten App-Ansicht in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Ansicht erstellt oder bearbeitet wird
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 68d295e6c5426296cf4fb77e794b7c6edbf37021
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875572"
---
# <a name="create-or-edit-a-model-driven-app-view"></a>Erstellen oder bearbeiten einer Modell-angetriebene App-Ansicht

<a name="BKMK_CreatingAndEditingViews"></a>   

 In diesem Thema erstellen Sie eine neue benutzerdefinierten öffentliche Ansicht. Sie bearbeiten auch eine vorhandene Ansicht.  
  
### <a name="create-a-new-view"></a>Eine neue Ansicht erstellen  
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

    

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die **Konto**-Entität aus und wählen Sie die Registerkarte **Ansicht**. 

3.  Wählen Sie **Ansicht hinzufügen** in der Symbolleiste.  

4.  Im Dialogfeld **Eigenschaften anzeigen** können Sie auf **Name**, **Firmen mit 25 oder mehr Mitarbeiter**, optional **Beschreibung** für die Ansicht angeben und dann **OK** auswählen.

    > [!div class="mx-imgBorder"] 
    > ![Eigenschaften anzeigen](media/view-properties.png)
  
5.  Im rechten Bereich unter Allgemeine Aufgaben wählen Sie **Spalten hinzufügen** und wählen Sie im Dialogfeld **Spalten hinzufügen** die Option **Anzahl der Mitarbeiter** und anschließend **OK** aus.  

    > [!div class="mx-imgBorder"] 
    > ![Anzahl der Mitarbeiter-Spalten](media/column-no-employees.png)
  
6. Im rechten Bereich unter allgemeine Aufgaben wählen Sie die Option **Filterkriterien bearbeiten** aus, wählen Sie in den bearbeitbaren Filterkriterien-Dialogfeld die **Anzahl der Mitarbeiter**, wählen Sie **Ist größer oder gleich** und geben dann **25** ein.  

    > [!div class="mx-imgBorder"] 
    > ![Filterkriterien bearbeiten](media/edit-filter-criteria.png)

7.  Aktivieren Sie **OK**, um das Dialogfeld **Filterkriterien bearbeiten** zu schließen und **Speichern und schließen** im Ansichtseditor aus.  
  
8.  Beachten Sie, dass Ihre Ansicht nun von der Registerkarte **Ansichten** auf der Website Power Apps verfügbar ist und einer App hinzugefügt werden kann.
  
### <a name="edit-a-view"></a>Eine Ansicht bearbeiten  
  
1.  Wählen Sie in der **Ansichten**-Registerkarte auf der Website Power Apps die Ansicht **Anzahl der Mitarbeiter** aus.
  
2.  Ändern Sie im Feld **Name** einen Namen für die Ansicht auf **Anzahl der Mitarbeiter mit 25 oder mehr Mitarbeiter in Arizona** und wählen Sie dann **OK** aus.  

3.  Im rechten Bereich unter Allgemeine Aufgaben wählen Sie **Spalten hinzufügen** und wählen Sie im Dialogfeld **Spalten hinzufügen** die Option **Adresse 1: Stadt** und anschließend **OK** aus.  

4. Im rechten Bereich der allgemeine Aufgaben wählen Sie **Filterkriterien bearbeiten**Im Dialogfeld bearbeitbare Filterkriterien und fügen eine zweite Filter-Klausel hinzu. Wählen Sie **Adresse 2: Bundesland/Kanton** aus und wählen Sie **Gleich** und geben dann **Arizona** ein. 

    > [!div class="mx-imgBorder"] 
    > ![Adresse 2: Bundesland/Kanton](media/column-address-2-state.png)

5. Aktivieren Sie **OK**, um das Dialogfeld **Filterkriterien bearbeiten** zu schließen und **Speichern und schließen** im Ansichtseditor aus.  
  

## <a name="create-a-new-view-from-an-existing-view"></a>Erstellen einer neuen Ansicht aus einer vorhandenen Ansicht  
 Folgen Sie der Vorgehensweise, um eine Ansicht zu erstellen, aber anstatt **Speichern und schließen** auszuwählen, wählen Sie **Speichern unter** aus, und geben Sie einen neuen **Name** und eine **Beschreibung** für die Ansicht ein.  
 
### <a name="next-steps"></a>Nächste Schritte
[Aktivieren und Konfigurieren von Spalten](choose-and-configure-columns.md)  
  
[Filterkriterien bearbeiten](edit-filter-criteria.md)  
  
[Konfigurieren der Sortierung](configure-sorting.md)  

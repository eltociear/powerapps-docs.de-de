---
title: Erstellen oder bearbeiten eines Systemdiagramms für modellgesteuerte Apps in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie ein Diagramm erstellt oder bearbeitet wird
ms.custom: ''
ms.date: 03/30/2020
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
ms.assetid: e02d58f7-6b1c-4a51-b801-a4d9f24729c5
caps.latest.revision: 29
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 426bfaf0ab53e1d896f7e0b098e089c8596ad907
ms.sourcegitcommit: 3c6c5594b73abd5ff438d50f3b579d56cef7241c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "3285606"
---
# <a name="create-a-model-driven-app-system-chart"></a>Erstellen eines Systemdiagramms für modellgesteuerte Apps

In diesem Thema erfahren Sie, wie Sie ein Systemdiagramm erstellen. Systemdiagramme sind Diagramme im Besitz der Organisation. Dadurch stehen sie allen Benutzern mit Lesezugriff auf die Daten, mit denen die App ausgeführt werden. Systemdiagramme können nicht bestimmten App-Benutzern zugewiesen oder mit ihnen geteilt werden.  
  
1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2. Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Diagramme**.  
  
3.  Wählen Sie **Diagramm hinzufügen** in der Symbolleiste.  
  
4.  Geben Sie den Typ des Diagramms und die Anzeige der Daten im Diagramm an.  
  
    -   Geben Sie dem Diagrammnamen ein, beispielsweise *Anzahl der Mitarbeiter nach Firma*.  
  
    -   Wählen Sie im Dropdown-Menü **Feld auswählen** aus. 
        - Wählen Sie im Achsendropdown **Feld auswählen** **Serie** ein Feld wie **Anzahl der Mitarbeiter** aus.  
        - Wählen Sie im Achsendropdown **Feld auswählen** **Kategorie** ein Feld wie **Firmenname** aus.
  
    -   Fügen Sie eine Beschreibung hinzu, um den Zweck des Diagramms zu identifizieren, z. B. *In einem Säulendiagramm wird die Anzahl der Mitarbeiter mit Suchkriterien nach Firmenname angezeigt*. 

    > [!div class="mx-imgBorder"] 
    > ![Beispieldiagramm](media/sample-chart.png)
  
5.  Klicken Sie auf **Speichern und schließen**.  

## <a name="known-issues"></a>Bekannte Probleme  
Im Diagrammdesigner einen Auftrag für bestimmte berechnete Felder hinzuzufügen wird nicht unterstützt und wird einen Fehler verursachen.  Die berechneten Felder, die das verursachen, verwenden andere berechnete Felder, ein Feld einer verknüpften Entität oder ein lokales Feld in der Entität.

## <a name="next-steps"></a>Nächste Schritte  
[Dashboards erstellen oder bearbeiten](create-edit-dashboards.md)

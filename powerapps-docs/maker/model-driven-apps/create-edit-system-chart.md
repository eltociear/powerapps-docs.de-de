---
title: Erstellen oder bearbeiten eines Systemdiagramms für modellgesteuerte Apps in PowerApps | MicrosoftDocs
description: 'Erfahren Sie, wie ein Diagramm erstellt oder bearbeitet wird'
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: crm-online
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
---
# <a name="create-a-model-driven-app-system-chart"></a>Erstellen eines Systemdiagramms für modellgesteuerte Apps

In diesem Thema erfahren Sie, wie Sie ein Systemdiagramm erstellen. Systemdiagramme sind Diagramme im Besitz der Organisation. Dadurch stehen sie allen Benutzern mit Lesezugriff auf die Daten, mit denen die App ausgeführt werden. Systemdiagramme können nicht zugewiesen oder für bestimmte App-Benutzer freigegeben werden.  
  
1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).     
  
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

## <a name="next-steps"></a>Nächste Schritte  
[Erstellen oder Bearbeiten eines Dashboards](create-edit-dashboards.md)

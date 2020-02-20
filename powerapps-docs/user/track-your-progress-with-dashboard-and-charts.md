---
title: Verfolgen des Fortschritts mit Dashboards und Diagrammen in modellgesteuerten Apps | Microsoft-Dokumentation
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/4/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 70c6f97c2617c9d6084c3aa8a0861793a0c059d5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74726169"
---
# <a name="track-your-progress-with-dashboards-and-charts"></a>Verfolgen des Fortschritts mit Dashboards und Diagrammen

Dashboards enthalten erfasste App-Daten und bieten Einblicke, um KPI (Key Performance Indicator) und andere wichtige Daten in leicht lesbaren interaktiven Diagrammen und Diagrammen anzuzeigen. Dashboards sind für alle Datensatztypen verfügbar.

> [!div class="mx-imgBorder"]
> ![Dashboard](media/Dashboard.png "Dashboard") 

-  Wenn Sie ein anderes Dashboardlayout anzeigen möchten, wählen Sie den Pfeil nach unten neben dem Namen des Dashboards aus, und wählen Sie dann das gewünschte Layout aus.
-  Zum Auswählen eines Standarddashboards zeigen Sie das gewünschte Dashboard an, und wählen Sie dann am oberen Rand des Bildschirms **Als Standard festlegen** aus.

   > [!div class="mx-imgBorder"]
   > ![Dashboard hinzufügen oder ändern](media/add_dashboard.png "Hinzufügen oder Ändern eines Dashboards") 

## <a name="create-a-new-dashboard"></a>Erstellen eines neuen Dashboards

1. Wählen Sie zum Erstellen eines neuen Dashboards **Dynamics 365-Dashboard erstellen** aus. 

   > [!div class="mx-imgBorder"]
   > ![Neues Dashboard hinzufügen](media/new_dashboard.png "Hinzufügen eines neues Dashboards")
   
2. Wählen Sie ein Dashboardlayout aus, und wählen Sie **Erstellen** aus.  

   > [!div class="mx-imgBorder"]
   > ![Erstellen eines Dashboards](media/create_dashboard.png "Erstellen eines Dashboards")
 
3. Geben Sie einen Namen für das Dashboard ein. 
4. Fügen Sie den gewünschten Inhalt für die einzelnen Bereiche des Dashboards hinzu. Wir fügen z. B. ein Diagramm hinzu. 

   > [!div class="mx-imgBorder"]
   > ![Diagramm hinzufügen](media/add_chart.png "Hinzufügen eines Diagramms")
 
 5. Wählen Sie den **Datensatztyp** für das Diagramm aus.
 6. Wählen Sie eine **Ansicht** aus, in der die Daten im Diagramm angezeigt werden.
 7. Wählen Sie das Diagramm aus, und wählen Sie dann **Hinzufügen** aus.
 8. Fügen Sie dem Dashboard weitere Komponenten hinzu, und wählen Sie dann **Speichern** aus, wenn der Vorgang abgeschlossen ist. 
 
Das Dashboard, das Sie erstellt haben, wird im Dropdownmenü der verfügbaren Dashboards angezeigt.

## <a name="use-charts"></a>Verwenden von Diagrammen 

Diagramme bieten Ihnen einen schnellen Überblick über die Nachverfolgung ihrer Ziele. Sie sind interaktiv. Wenn Sie auf einen Bereich im Diagramm klicken oder tippen, erhalten Sie weitere Informationen.

-   Zeigen Sie mit der Maus auf das Diagramm, um eine QuickInfo zu diesem Bereich des Diagramms anzuzeigen.
-   Klicken Sie auf den Bereich eines Diagramms, um eine Rasteransicht mit weiteren Details zu den Daten im Diagramm anzuzeigen.
-   Wenn Sie ein Diagramm erweitern möchten, wählen Sie die Schaltfläche **Diagramm erweitern** ![Ansicht „Diagramm erweitern“](media/expandviewbutton.png "Erweitern der Diagrammansicht") aus.
-   Wählen Sie ![Weitere Befehle](media/MoreButton.png "Weitere Befehle") aus, und führen Sie dann eine Aktion aus, um Datensätze im Diagramm anzuzeigen oder das Diagramm zu aktualisieren: **Aktualisieren** oder **Datensätze anzeigen**
     
     > [!div class="mx-imgBorder"]
     > ![Anzeigen von Diagrammen in Power Apps](media/ViewOfCharts.png "Anzeigen von Diagrammen in Power Apps")  
       

**Ändern der Diagrammansicht**
 
Wenn Sie die Diagrammansicht ändern, wird eine andere Aufschlüsselung der Daten angezeigt, z. B. Verkaufschancen, die sich innerhalb eines bestimmten Zeitraums ergeben. Sie können eine Diagrammansicht ändern, indem Sie die Ansichtsauswahl auf der Rasterseite auswählen.

Wählen Sie z. B. „Alle Verkaufschancen“ aus, und wählen Sie dann eine andere Ansicht aus. Das Diagramm und das Raster werden daraufhin aktualisiert.

> [!div class="mx-imgBorder"]
> ![Ändern einer Diagrammansicht in Power Apps](media/ChangeChartView.png "Ändern einer Diagrammansicht in Power Apps")

## <a name="known-issues"></a>Bekannte Probleme  
Im Diagramm-Designer wird das Hinzufügen eines Auftrags für bestimmte berechnete Felder nicht unterstützt und führt zu einem Fehler.  Die berechneten Felder, die zu diesem Fehler führen, verwenden ein anderes berechnetes Feld, ein verknüpftes Entitätsfeld oder ein lokales Feld in der Entität.




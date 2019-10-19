---
title: Verfolgen Sie Ihren Fortschritt mit Dashboards und Diagrammen in Modell gesteuerten apps | MicrosoftDocs
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
ms.openlocfilehash: e9d046c49a2a91aaf5c65094d446ae09f41572f9
ms.sourcegitcommit: 4c35aedde46380d5438687ae6f61a3b0cc7e7e2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2019
ms.locfileid: "71969088"
---
# <a name="track-your-progress-with-dashboards-and-charts"></a>Verfolgen des Fortschritts mit Dashboards und Diagrammen

Dashboards nehmen eine Sammlung von App-Daten auf und bieten Einblicke, um KPI (Key Performance Indicator) und andere wichtige Daten in leicht lesbaren interaktiven Diagrammen und Diagrammen anzuzeigen. Dashboards sind für alle Daten Satz Typen verfügbar.

> [!div class="mx-imgBorder"]
> ![Dashboard](media/Dashboard.png "Dashboard") 

-  Wenn Sie ein anderes Dashboardlayout anzeigen möchten, wählen Sie den Pfeil nach unten neben dem Namen des Dashboards aus, und wählen Sie dann das gewünschte Layout aus.
-  Zum Auswählen eines Standard Dashboards zeigen Sie das gewünschte Dashboard an, und wählen Sie dann oben auf dem Bildschirm **als Standard festlegen** aus.

   > [!div class="mx-imgBorder"]
   > Dashboard(media/add_dashboard.png "Hinzufügen") oder ändern Dashboard ![Hinzufügen oder]ändern 

## <a name="create-a-new-dashboard"></a>Erstellen eines neuen Dashboards

1. Klicken Sie zum Erstellen eines neuen Dashboards auf **Dynamics 365-Dashboard erstellen**. 

   > [!div class="mx-imgBorder"]
   > ![Hinzufügen eines neuen Dashboards](media/new_dashboard.png "Hinzufügen eines neuen Dashboards")
   
2. Wählen Sie ein Dashboard-Layout und dann **Erstellen**aus.  

   > [!div class="mx-imgBorder"]
   > ![Erstellen eines Dashboards](media/create_dashboard.png "Erstellen eines Dashboards")
 
3. Geben Sie einen Namen für das Dashboard ein. 
4. Fügen Sie den gewünschten Inhalt für die einzelnen Bereiche des Dashboards hinzu. Fügen wir beispielsweise ein Diagramm hinzu. 

   > [!div class="mx-imgBorder"]
   > ![Hinzufügen eines Diagramms](media/add_chart.png "Hinzufügen eines Diagramms")
 
 5. Wählen Sie den **Daten Recordtyp** für das Diagramm aus.
 6. Wählen Sie eine **Ansicht** aus, die von den Daten im Diagramm angezeigt wird.
 7. Wählen Sie das Diagramm und dann **Hinzufügen**aus.
 8. Fügen Sie dem Dashboard weiterhin Komponenten hinzu, und klicken Sie anschließend auf **Speichern**. 
 
Das Dashboard, das Sie erstellt haben, wird im Dropdown Menü der verfügbaren Dashboards angezeigt.

## <a name="use-charts"></a>Verwenden von Diagrammen 

Diagramme bieten Ihnen einen schnellen Überblick über die Nachverfolgung ihrer Ziele. Sie sind auch interaktiv, sodass Sie auf einen Bereich eines Diagramms klicken oder tippen können, um weitere Informationen zu erhalten.

-   Zeigen Sie mit der Maus auf das Diagramm, um eine QuickInfo mit schnellen Informationen zu diesem Bereich des Diagramms anzuzeigen.
-   Klicken Sie auf den Bereich eines Diagramms, um eine Rasteransicht mit weiteren Details zu den Daten im Diagramm anzuzeigen.
-   Um ein Diagramm zu erweitern, wählen **Sie die Schaltfläche Diagramm erweitern**Diagramm![Ansicht]erweitern Diagramm(media/expandviewbutton.png "Ansicht") erweitern aus.
-   Um Datensätze im Diagramm anzuzeigen oder das Diagramm zu aktualisieren, klicken Sie auf ![Weitere Befehle](media/MoreButton.png "Weitere Befehle") , und wählen Sie dann eine Aktion aus: **Aktualisieren** oder **Datensätze anzeigen**.
     
     > [!div class="mx-imgBorder"]
     > ![Ansicht der Diagramme in der powerapps]-(media/ViewOfCharts.png "Ansicht der Diagramme in powerapps")  
       

**Ändern der Diagramm Ansicht**
 
Wenn Sie die Diagramm Ansicht ändern, wird eine andere Aufschlüsselung der Daten angezeigt, z. b. Verkaufschancen, die innerhalb eines bestimmten Zeitraums geöffnet wurden. Sie können eine Diagramm Ansicht ändern, indem Sie die Ansichts Auswahl auf der Raster Seite auswählen.

Wählen Sie z. b. "alle Verkaufschancen" aus, und wählen Sie dann eine andere Ansicht aus, und das Diagramm und das Raster werden aktualisiert.

> [!div class="mx-imgBorder"]
> ![Ändern einer Diagramm Ansicht in powerapps](media/ChangeChartView.png "Ändern einer Diagramm Ansicht in powerapps")

## <a name="known-issues"></a>Bekannte Probleme  
Im Diagramm-Designer wird das Hinzufügen von Order by für bestimmte berechnete Felder nicht unterstützt und führt zu einem Fehler.  Die berechneten Felder, die dies bewirken, verwenden ein anderes berechnetes Feld, ein verknüpftes Entitäts Feld oder ein lokales Feld in der Entität.




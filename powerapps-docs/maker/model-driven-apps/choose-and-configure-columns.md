---
title: Spalten in Ansichten in Modell-angetriebenen App-Ansichten in PowerApps wählen und konfigurieren | MicrosoftDocs
description: 'Erfahren Sie, wie Sie Ansichten für Ihre App auswählen und konfigurieren'
keywords: ''
ms.date: 11/27/2018
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 31bfcf18-58c3-491c-91b5-f9b0f5424852
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 25
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="choose-and-configure-columns-in-model-driven-app-views"></a>Spalten in Ansichten in modellgestützten App-Ansichten wählen und konfigurieren

<a name="BKMK_ChooseAndConfigureColumns"></a>   

 Zusammen mit Filterkriterien sind die Spalten, die in einer PowerApps-Ansicht angezeigt werden, sehr wichtig für den Wert der ausgewählten Ansicht. In diesem Thema erstellen oder bearbeiten Sie Ansichten, indem Sie die folgenden Aufgaben ausführen:  

-   [Ansicht-Editor öffnen](choose-and-configure-columns.md#open-the-view-editor)  
   
-   [Hinzufügen von Spalten](choose-and-configure-columns.md#BKMK_AddColumns)  
  
-   [Entfernen von Spalten](choose-and-configure-columns.md#BKMK_RemoveColumns)  
  
-   [Ändern der Spaltenbreite](choose-and-configure-columns.md#BKMK_ChangeColumnWidth)  
  
-   [Verschieben einer Spalte](choose-and-configure-columns.md#BKMK_MoveAColumns)  
    
  > [!IMPORTANT]
  > Die neueste Version des Ansicht-Designers befindet sich derzeit in der Vorschau. Einige Funktionen wie das Aktivieren oder Deaktivieren der Präsenz für eine Spalte und das Hinzufügen einer Suchspalte werden noch nicht unterstützt. Um diese Aufgaben zu erfüllen, [öffnen Sie die Ansicht im klassischen Ansicht-Designer](/dynamics365/customer-engagement/customize/create-and-edit-views#open-the-classic-view-designer).
  >  -   [Präsenz für diese Spalte aktivieren oder deaktivieren](/dynamics365/customer-engagement/customize/choose-and-configure-columns#BKMK_EnableOrDisablePresence)  
  >
  >  -   [Suchspalten hinzufügen](/dynamics365/customer-engagement/customize/choose-and-configure-columns#BKMK_AddFindColumns) 



### <a name="open-the-view-editor"></a>Ansicht-Editor öffnen

1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Anzeigen**. 

    > [!div class="mx-imgBorder"] 
    > ![Ansichten](media/available-views.png)

3. Wählen Sie eine vorhandene Ansicht aus, um diese oder auf der Symbolleiste auf **Ansicht hinzufügen** zu öffnen. 

<a name="BKMK_AddColumns"></a>   
### <a name="add-columns"></a>Hinzufügen von Spalten  
 Sie können Spalten aus der aktuellen Entität oder der aus verknüpften Entitäten einschließen, bei denen eine 1:n-Entitätsbeziehung mit der aktuellen Entität besteht.  
  
 Beispielsweise, möchten Sie möglicherweise den Besitzer einer Entität im besitz eines Benutzers in einer Spalte anzeigen. Sie können auswählen, dass das Feld **Besitzer** der aktuellen Entität den Namen des Besitzers anzeigt. Dieser erscheint als Link, um den **Benutzer**-Datensatz für den Mitarbeiter zu öffnen, der der Besitzer ist.  
  
 Wenn Sie die Telefonnummer für den Datensatzbesitzer anzeigen möchten, müssen Sie **Besitzer (Benutzer)** in der Dropdownliste **Datensatztyp** das Feld **Telefon 1** auswählen.  
  
#### <a name="add-columns-to-views"></a>Hinzufügen von Spalten zu einer Ansicht  
  
1.  Beim Erstellen und Bearbeiten von Ansichten, sollten Sie sicherstellen, dass der Bereich **Felder** geöffnet wird. Wenn nicht, wählen Sie **Felder hinzufügen** auf der Symbolleiste aus. 

    > [!div class="mx-imgBorder"] 
    > ![Editor und Spalten anzeigen](media/fields-drawer-view-designer.png)

2.  Wählen Sie die Felder aus, die Sie dem Ansicht-Designer hinzufügen möchten. Dadurch wird das Feld als Spalte auf der rechten Seite der Ansicht hinzugefügt.

3.  Wählen Sie die Registerkarte **Verknüpft** aus, um verknüpfte Entitäten und die entsprechenden Felder anzuzeigen.
  
 Wenn Sie Spalten hinzufügen, erhöhen Sie die Breite der Ansicht. Wenn die Breite der Ansicht den Platz überschreitet, um sie auf der Seite anzuzeigen, erlauben horizontale Bildlaufleisten den Benutzern das Scrollen, um die ausgeblendeten Spalten anzuzeigen.  
  
> [!TIP]
>  Wenn die Ansicht daten für ein bestimmtes Feld filteren, damit nur Datensätze mit einem bestimmten Wert angezeigt werden, enthalten Sie diese Spalte nicht in der Ansicht. Wenn Sie z. B. nur aktive Datensätze anzeigen, schließen sie die Statusspalte nicht in die Ansicht ein. Benennen Sie die Ansicht, um anzugeben, dass alle Datensätze, die in der Ansicht angezeigt werden, aktiv sind.  
  
> [!NOTE]
>  Wenn Sie Spalten für Suchansichten für aktualisierte Entitäten hinzufügen, werden nur die ersten zehn drei Spalten angezeigt.  
  
<a name="BKMK_RemoveColumns"></a>   
### <a name="remove-columns"></a>Entfernen von Spalten  
  
1.  Wählen Sie die Kopfzeile der Spalte aus, die entfernt werden soll.  
  
2.  Wählen Sie in der Dropdownliste die Option **Entfernen** aus.  
  
<a name="BKMK_ChangeColumnWidth"></a>   
### <a name="change-column-width"></a>Ändern der Spaltenbreite  
  
1.  Zeigen Sie mit der Maus auf den Bereich zwischen den Spalten in der Ansicht.  
  
2.  Eine Linie erscheint und der Cursor wird zu einem doppelseitigen Pfeil.  
  
3.  Ziehen Sie die Spalte auf die entsprechende Breite.  
  
<a name="BKMK_MoveAColumns"></a>   
### <a name="move-a-column"></a>Verschieben einer Spalte  
  
Klicken und ziehen Sie die Spaltenkopfzeile zur richtigen Position.
  
> [!TIP]
>   Sie können auch die Kopfzeile der Spalte auswählen, die Sie verschieben möchten und aus dem Dropdown-Menü **Nach rechts** oder **Nach links**auswählen.  


  
## <a name="next-steps"></a>Nächste Schritte
[Ansichten erstellen oder bearbeiten](create-edit-views.md)

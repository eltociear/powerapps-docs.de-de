---
title: Spalten in Ansichten in Modell-angetriebenen App-Ansichten in PowerApps wählen und konfigurieren | MicrosoftDocs
description: 'Erfahren Sie, wie Sie Ansichten für Ihre App auswählen und konfigurieren'
keywords: ''
ms.date: 06/11/2018
ms.service: crm-online
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

# <a name="tutorial-choose-and-configure-columns-in-model-driven-app-views"></a>Anleitung: Spalten in Ansichten in Modell-angetriebenen App-Ansichten in PowerApps wählen und konfigurieren

<a name="BKMK_ChooseAndConfigureColumns"></a>   

 Zusammen mit Filterkriterien sind die Spalten, die in einer PowerApps-Ansicht angezeigt werden, sehr wichtig für den Wert der ausgewählten Ansicht. In diesem Lernprogramm Erstellen oder Bearbeiten Sie Ansichten, indem Sie die folgenden Aufgaben ausführen:  

-   [Ansicht-Editor öffnen](choose-and-configure-columns.md#open-the-view-editor)  
   
-   [Hinzufügen von Spalten](choose-and-configure-columns.md#BKMK_AddColumns)  
  
-   [Entfernen von Spalten](choose-and-configure-columns.md#BKMK_RemoveColumns)  
  
-   [Ändern der Spaltenbreite](choose-and-configure-columns.md#BKMK_ChangeColumnWidth)  
  
-   [Verschieben einer Spalte](choose-and-configure-columns.md#BKMK_MoveAColumns)  
  
-   [Präsenz für diese Spalte aktivieren oder deaktivieren](choose-and-configure-columns.md#BKMK_EnableOrDisablePresence)  
  
-   [Suchspalten hinzufügen](choose-and-configure-columns.md#BKMK_AddFindColumns)  

### <a name="open-the-view-editor"></a>Ansicht-Editor öffnen

1.  Melden Sie sich bei [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Anzeigen**. 

    > [!div class="mx-imgBorder"] 
    > ![Ansichten](media/available-views.png)

3. Wählen Sie eine vorhandene Ansicht aus, um diese oder auf der Symbolleiste auf **Ansicht hinzufügen** zu öffnen. 

<a name="BKMK_AddColumns"></a>   
### <a name="add-columns"></a>Hinzufügen von Spalten  
 Sie können Spalten aus der aktuellen Entität oder der aus verknüpften Entitäten einschließen, bei denen eine 1:n-Entitätsbeziehung mit der aktuellen Entität besteht.  
  
 Beispielsweise, möchten Sie möglicherweise den Besitzer einer Entität im besitz eines Benutzers in einer Spalte anzeigen. Sie können auswählen, dass das Feld **Besitzer** der aktuellen Entität den Namen des Besitzers anzeigt. Dieser erscheint als Link, um den **Benutzer**-Datensatz für den Mitarbeiter zu öffnen, der der Besitzer ist. In diesem Fall haben Sie auch die Möglichkeit, die [Präsenz für eine Spalte zu aktivieren oder deaktivieren](choose-and-configure-columns.md#BKMK_EnableOrDisablePresence).  
  
 Wenn Sie die Telefonnummer für den Datensatzbesitzer anzeigen möchten, müssen Sie **Besitzer (Benutzer)** in der Dropdownliste **Datensatztyp** das Feld **Telefon 1** auswählen.  
  
#### <a name="add-columns-to-views"></a>Hinzufügen von Spalten zu einer Ansicht  
  
1.  Beim Erstellen und Bearbeiten von Ansichten, aktivieren Sie  **Spalten hinzufügen** 

    > [!div class="mx-imgBorder"] 
    > ![Editor und Spalten anzeigen](media/view-editor.png)

    Das Dialogfeld **Spalten hinzufügen** wird angezeigt.

    > [!div class="mx-imgBorder"] 
    > ![Hinzufügen von Spalten](media/add-columns.png)
  
2.  Wählen Sie **Datensatztyp** aus, wenn Sie Felder aus verknüpften Entitäten einfügen möchten.  
  
3.  Sie können auch mehrere Felder aus verknüpften Entitäten auswählen.  
  
4.  Wenn Sie die Felder, die Sie verwenden möchten, ausgewählt haben, wählen Sie **OK** aus, um das Dialogfeld **Spalten hinzufügen** zu schließen.  
  
 Wenn Sie Spalten hinzufügen, erhöhen Sie die Breite der Ansicht. Wenn die Breite der Ansicht den Platz überschreitet, um sie auf der Seite anzuzeigen, erlauben horizontale Bildlaufleisten den Benutzern das Scrollen, um die ausgeblendeten Spalten anzuzeigen.  
  
> [!TIP]
>  Wenn die Ansicht daten für ein bestimmtes Feld filteren, damit nur Datensätze mit einem bestimmten Wert angezeigt werden, enthalten Sie diese Spalte nicht in der Ansicht. Wenn Sie z. B. nur aktive Datensätze anzeigen, schließen sie die Statusspalte nicht in die Ansicht ein. Benennen Sie die Ansicht, um anzugeben, dass alle Datensätze, die in der Ansicht angezeigt werden, aktiv sind.  
  
> [!NOTE]
>  Wenn Sie Spalten für Suchansichten für aktualisierte Entitäten hinzufügen, werden nur die ersten zehn drei Spalten angezeigt.  
  
<a name="BKMK_RemoveColumns"></a>   
### <a name="remove-columns"></a>Entfernen von Spalten  
  
1.  Beim Erstellen und Bearbeiten von Ansichten wählen Sie die Spalte, die Sie entfernen möchten.  
  
2.  Im Bereich **Allgemeine Aufgaben** wählen Sie **Entfernen** aus.  
  
3.  Wählen Sie in der Bestätigungsmeldung **OK** aus.  
  
<a name="BKMK_ChangeColumnWidth"></a>   
### <a name="change-column-width"></a>Ändern der Spaltenbreite  
  
1.  Beim Erstellen und Bearbeiten von Ansichten wählen Sie die Spalte, die Sie ändern möchten.  
  
2.  Wählen Sie im Bereich **Allgemeine Aufgaben** die Option **Eigenschaften ändern** aus.  
  
3.  Wählen Sie im Dialogfeld **Spalteneigenschaften ändern** eine Option aus, um die Spaltenbreite festzulegen, und wählen Sie dann **OK** aus.  
  
<a name="BKMK_MoveAColumns"></a>   
### <a name="move-a-column"></a>Verschieben einer Spalte  
  
1.  Beim Erstellen und Bearbeiten von Ansichten wählen Sie die Spalte, die Sie verschieben möchten.  
  
2.  Verschieben Sie die Spalte im Bereich **Allgemeine Aufgaben** mithilfe der Pfeile nach links oder rechts.  
  
<a name="BKMK_EnableOrDisablePresence"></a>   
### <a name="enable-or-disable-presence-for-a-column"></a>Präsenz für diese Spalte aktivieren oder deaktivieren  
 Wenn die folgenden Bedingungen zutreffen, können Personen ein Skype for Business-Onlinestatussteuerelement in Listen sehen, das anzeigt, ob die Person verfügbar ist und Mitarbeitern ermöglichen, mit ihnen über Instant Messaging zu interagieren:  
  
-   Benutzer nutzen Edge oder Internet Explorer.  
  
-   Für ist Skype for Business installiert.  
  
-   Benutzer haben Microsoft ActiveX im Internet Explorer aktiviert.  
  
-   Ihre Organisation hat Präsenz für das System in den Systemeinstellungen aktiviert.  
  
 Das Präsenz-Steuerelement und die Einstellung, um es zu aktivieren, ist nur für Spalten verfügbar, die primäre Felder für E-Mail-fähige Entitäten anzeigen (Benutzer, Kontakte, Leads, Verkaufschancen oder benutzerdefinierte Entitäten).  
  
#### <a name="enable-or-disable-skype-for-business-presence-for-a-column"></a>Skype for Business-Präsenz für diese Spalte aktivieren oder deaktivieren  
  
1.  Beim Erstellen und Bearbeiten von Ansichten wählen Sie die Spalte, die Sie ändern möchten.  
  
2.  Wählen Sie im Bereich **Allgemeine Aufgaben** die Option **Eigenschaften ändern** aus.  
  
3.  Aktivieren oder deaktivieren Sie im Dialogfeld **Spalteneigenschaften ändern** die Option **Präsenz für diese Spalte aktivieren**, und wählen Sie dann **OK** aus.  
  
<a name="BKMK_AddFindColumns"></a>   
### <a name="add-find-columns"></a>Suchspalten hinzufügen  
 Suchspalten sind die Spalten, die von der anwendung durchsucht werden, wen Mitarbeiter das textfeld **Nach Datensätzen suchen** verwenden, das für Listen angezeigt wird, oder wenn die Fähigkeit besteht, nach Datensätzen für eine Entität in der Anwendung zu suchen, wenn Mitarbeiter z. B. nach eine,m Datensatz für ein Suchfeld suchen.  
  
1.  Öffnen Sie eine Ansicht für die **Schnellsuche**. Informationen zum die Schnellsuche finden Sie unter [Typen von Ansichten](create-edit-views.md#types-of-views).  
  
2.  Wählen Sie **Suchspalten hinzufügen** aus, um das Dialogfeld zu öffnen.  
  
3.  Wählen Sie die Felder aus, die die Daten enthalten, die Sie suchen möchten.  
  
4.  Wählen Sie **OK** aus, um das Dialogfeld **Suchspalten hinzufügen** zu schließen.  

## <a name="community-tools"></a>Community-Tools

**Ansichts-Layout-Replikator** und **Ansicht-Designer** sind die Tools, die von der XrmToolbox-Community bereitgestellt werden und für Dynamics 365 Customer Engagement entwickelt wurden. Weitere Informationen finden Sie im Thema [Entwicklertools](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools) für von der Community entwickelte Tools.

> [!NOTE]
> Die Communitytools sind kein Produkt von Microsoft Dynamics und es wird kein Support für die Communitytools angeboten. Wenn Sie Fragen zu dem Tool haben, setzen Sie sich bitte mit dem Herausgeber in Verbindung. Weitere Informationen: [XrmToolBox](https://www.xrmtoolbox.com). 

## <a name="next-steps"></a>Nächste Schritte
[Erstellen oder Bearbeiten von Ansichten](create-edit-views.md)

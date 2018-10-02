---
title: Feld einem modellgesteuertes App-Formular in PowerApps hinzufügen | MicrosoftDocs
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
  - PowerApps
author: Mattp123
ms.assetid: 29499887-6e7b-44a1-86a7-eaad33f3075d
caps.latest.revision: 30
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-a-field-to-a-model-driven-app-form"></a>So fügen Sie ein Feld zu einem modellgesteuerten App-Formular hinzu: 

Wenn ein PowerApps-Formular für eine Standard-Entität nicht den Anforderungen Ihres Unternehmens entspricht, können Sie das Formular anpassen, indem Sie vorhandene Felder ändern oder durch neue Felder hinzufügen. Es ist zwar einfacher, die vorhandenen Felder in einem Formular zu bearbeiten, manchmal ist es jedoch besser, ein Feld hinzuzufügen, um auf ein bestimmtes Unternehmensszenario einzugehen.

In diesem Thema fügen Sie ein Feld einem Formular hinzu.   
  
1.  Wählen Sie auf der Seite [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) die Option **Modellgesteuert** (unterer linker Teil des Navigationsbereichs).  

    ![Modellgesteuerter Entwurfsmodus](../model-driven-apps/media/model-driven-switch.png)

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment). 

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3.  Öffnen Sie in der Liste der Formulare das Formular des Typs **Primär**, um es zu bearbeiten.  
  
4.  Klicken Sie im Formular auf den Abschnitt, dem Sie ein Feld hinzufügen möchten, und doppelklicken Sie dann im Bereich **Feld-Explorer** auf das Feld, das Sie dem Formular hinzufügen möchten.  
  
    > [!TIP]
    >  Wenn Sie ein Optionssatzfeld im Formular hinzufügen, kann die Dropdownliste, die die Optionssatzwerte enthält, nur zwei Werte anzeigen. Benutzer müssen einen Bildlauf durchführen, um mehrere Werte in der Liste anzuzeigen. Wenn mehr als zwei Werte angezeigt werden sollen, ohne dass Benutzer einen Bildlauf durchführen müssen, fügen Sie mindestens ein **Abstandhalter**-Steuerelement unterhalb des Optionssatzfelds auf dem Formular hinzu. Jedes **Abstandhalter**-Steuerelement stellt ein Abstandhalter für einen Optionssatzwert bereit. Wenn Sie z. B. vier Werte in der Dropdownliste anzeigen möchten, ohne einen Bildlauf durchzuführen, fügen Sie zwei **Abstandhalter**-Steuerelemente unterhalb des Optionssatzfelds auf dem Formular hinzu.  
  
5.  Prüfen Sie in einer Vorschau die Darstellung des Formulars und die Funktionsweise der Ereignisse:  
  
    1.  Klicken Sie auf der Registerkarte **Homepage** auf **Vorschau**, und wählen Sie dann **Formular erstellen**, **Formular aktualisieren** oder **Schreibgeschütztes Formular** aus.  
  
    2.  Klicken Sie zum Schließen des Vorschauformulars auf **Schließen**.  
  
    3.  Wenn Sie Anpassungen für das Formular, das Sie bearbeiten, veröffentlichen möchten, wählen Sie bei geöffnetem Formular die Option **Veröffentlichen** aus.  
  
6.  Wenn Sie die Bearbeitung des Formulars abgeschlossen haben, klicken Sie auf **Speichern und schließen**.  
  
7. Wenn Sie Anpassungen für alle nicht veröffentlichten Komponenten gleichzeitig veröffentlichen möchten, klicken Sie auf **Datei** und auf **Alle Anpassungen veröffentlichen**.  
  
> [!NOTE]
>  Das Veröffentlichen von Anpassungen kann sich auf den normalen Systembetrieb auswirken. Wir empfehlen, dass Sie Veröffentlichungen zu einem Zeitpunkt durchführen, wenn dies die Benutzer am wenigsten stört.  
  
## <a name="next-steps"></a>Nächste Schritte  
 
 [Erstellen und Gestalten von Formularen](create-design-forms.md)

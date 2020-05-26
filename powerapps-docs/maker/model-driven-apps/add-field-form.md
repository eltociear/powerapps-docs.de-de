---
title: Feld einem modellgesteuerten App-Formular hinzufügen in Power Apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/04/2020
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
ms.assetid: 29499887-6e7b-44a1-86a7-eaad33f3075d
caps.latest.revision: 30
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: dcf292660c89e55ec83739c4dba662ff4cf7bff4
ms.sourcegitcommit: 52b7f59e271437e86ffff226fb6c1982bf7f08b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "3332474"
---
# <a name="add-a-field-to-a-model-driven-app-form"></a>So fügen Sie ein Feld zu einem modellgesteuerten App-Formular hinzu: 

Wenn ein Power Apps-Formular für eine Standard-Entität nicht den Anforderungen Ihres Unternehmens entspricht, können Sie das Formular anpassen, indem Sie vorhandene Felder ändern oder neue Felder hinzufügen. Es ist zwar einfacher, die vorhandenen Felder in einem Formular zu bearbeiten, manchmal ist es jedoch besser, ein Feld hinzuzufügen, um auf ein bestimmtes Unternehmensszenario einzugehen.

In diesem Thema fügen Sie ein Feld einem Formular hinzu.   
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3.  Öffnen Sie in der Liste der Formulare das Formular des Typs **Primär**, um es zu bearbeiten.  
  
4.  Klicken Sie im Formular auf den Abschnitt, dem Sie ein Feld hinzufügen möchten, und klicken Sie dann im Bereich **Felder** auf das Feld, das Sie dem Formular hinzufügen möchten.  
  
    > [!TIP]
    >  Wenn Sie ein Optionssatzfeld im Formular hinzufügen, kann die Dropdownliste, die die Optionssatzwerte enthält, nur zwei Werte anzeigen. Benutzer müssen einen Bildlauf durchführen, um mehrere Werte in der Liste anzuzeigen. Wenn mehr als zwei Werte angezeigt werden sollen, ohne dass Benutzer einen Bildlauf durchführen müssen, fügen Sie mindestens ein **Abstandhalter**-Steuerelement unterhalb des Optionssatzfelds auf dem Formular hinzu. Jedes **Abstandhalter**-Steuerelement stellt ein Abstandhalter für einen Optionssatzwert bereit. Wenn Sie z. B. vier Werte in der Dropdownliste anzeigen möchten, ohne einen Bildlauf durchzuführen, fügen Sie zwei **Abstandhalter**-Steuerelemente unterhalb des Optionssatzfelds auf dem Formular hinzu.  
  
5.  Wenn Sie Anpassungen für das Formular, das Sie bearbeiten, veröffentlichen möchten, wählen Sie bei geöffnetem Formular die Option **Veröffentlichen** aus. 
  
6.  Wenn Sie die Bearbeitung des Formulars abgeschlossen haben, klicken Sie auf **Speichern und schließen**.  
  
> [!IMPORTANT]
>  Wenn Sie in der einheitlichen Benutzeroberfläche Sicherheit auf Feldebene einstellen, empfehlen wir nicht, dass Sie für ein erforderliches Feld unter Verwendung von Sicherheitsregeln auf Feldebene schreibgeschützt festlegen.  Wenn der Datensatz erstellt wird, ignoriert die Speicher-Pipeline die schreibgeschützte Einstellung für das erforderliche Feld und speichert den Datensatz. Wir empfehlen, dass Sie die Entität mit rollenbasierter Sicherheit auf schreibgeschützt setzen. Dadurch wird sichergestellt, dass es beim Erstellen oder Speichern eines Datensatzes keine Konflikte gibt.
  
  
> [!NOTE]
>  Das Veröffentlichen von Anpassungen kann sich auf den normalen Systembetrieb auswirken. Wir empfehlen, dass Sie Veröffentlichungen zu einem Zeitpunkt durchführen, wenn dies die Benutzer am wenigsten stört.

  
## <a name="next-steps"></a>Nächste Schritte  
 
 [Formulare erstellen und gestalten](create-design-forms.md)

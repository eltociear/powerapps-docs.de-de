---
title: Erstellen oder Bearbeiten von modellgesteuerter Schnellansichtsformulare-App in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Schnellansichtsformular erstellen oder bearbeiten
ms.custom: ''
ms.date: 03/13/2020
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
ms.assetid: 9b101734-cc11-4d05-bd45-eb611eae9931
caps.latest.revision: 14
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1e94b836fc7718f3aa259b677edc58419c98af06
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3167100"
---
# <a name="create-a-model-driven-app-quick-view-form-to-view-information-about-a-related-entity"></a>Erstellen und Bearbeiten eines Schnellansichtsformulars für modellgesteuerten Apps, um Informationen über eine verknüpfte Entität anzuzeigen

In diesem Thema erfahren Sie, wie Sie in ein Schnellansichtsformular erstellen und wie Sie ein Schnellansicht-Steuerelement ein Hauptformular hinzufügen. 

Ein Schnellansichtsformular kann einem anderen Formular als Steuerelement zur schnellen Anzeige hinzugefügt werden. Es bietet eine Vorlage für die Anzeige von Informationen zu verknüpften Entitätsdatensätzen innerhalb eines Formulars für einen anderen Entitätsdatensatz. Das bedeutet, dass Ihre App-Benutzer nicht zu einem anderen Datensatz wechseln müssen, um die Informationen anzuzeigen, die sie für ihre Arbeit benötigen.  
  
 Steuerelemente für die Schnellansicht sind mit einem Suchfeld verknüpft, das in einem Formular enthalten ist. Wenn der Suchfeldwert nicht festgelegt wurde, ist das Steuerelement für die Schnellansicht nicht sichtbar. Die Daten in den Schnellansicht-Steuerelementen sind nicht bearbeitbar, und Schnellansichtsformulare unterstützen keine Formularskripts.  
  
 Da Schnellansichtsformulare mithilfe eines Schnellansicht-Steuerelements in einem Formular angezeigt werden, enthalten sie keinen Kopf-, Fuß- oder Navigationsbereich. Schnellansichtsformularen können keine Sicherheitsrollen zugewiesen werden, und sie können nicht aktiviert oder deaktiviert werden.  
  
<a name="BKMK_CreateQFV"></a>   
## <a name="create-a-quick-view-form"></a>Erstellen eines Schnellansichtsformulars  
 Sie können Schnellansichtsformulare mithilfe des Formular-Editors erstellen, ähnlich wie auch andere Formulare erstellt werden. Schnellansichtsformulare sind schreibgeschützt. Verwenden Sie diese, um Formulare zu erstellen, um die nur zum Lesen bstimmt sind.  
  
1. Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2. Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 
  
3. Wählen Sie in der Symbolleiste **Formular hinzufügen** > **Schnellansichtsformular** aus.  
  
5. Geben Sie im Bereich **Formular** einen **Anzeigenamen** und eine **Beschreibung** ein, um dieses Schnellansichtsformular von beliebigen anderen zu unterscheiden.  
  
6. Ziehen Sie im Formulardesigner beliebige Felder aus dem **Felder-Explorer** in den Abschnitt im Formular.

    > [!IMPORTANT]
    > Erforderliche Felder können nicht aus einem Formular entfernt werden. Wenn Sie dem Formular ein erforderliches Feld hinzufügen und es entfernen möchten, müssen Sie das Formular löschen und anschließend neu erstellen. Wenn Sie die Eigenschaft „Erforderlich“ für ein Feld festlegen, kann ein Datensatz nicht ohne Daten in diesem Feld gespeichert werden.

7. Wählen Sie **Speichern** aus, um das Formular zu speichern.  

8. Wählen Sie **Veröffentlichen**, damit das neue Formular in der Anwendung angezeigt wird. <!-- Which app? What does Publish do?-->
  
<a name="BKMK_EditQVF"></a>   
## <a name="edit-a-quick-view-form"></a>Bearbeiten eines Schnellansichtsformulars  
 Schnellansichtsformulare besitzen ein vereinfachtes Layout, da sie zur Anzeige innerhalb eines Formularabschnitts konzipiert sind. Nur eine Einspaltenregisterkarte ist verfügbar. Sie können nur weitere Einspaltenabschnitte, Felder, Unterraster und Abstandhalter hinzufügen.   
  
  > [!IMPORTANT]
  > Erforderlich Felder können nicht gelöscht werden. Wenn Sie dem Formular ein erforderliches Feld hinzufügen, können Sie es nicht löschen. Wenn Sie das Feld nicht im Formular haben möchten, müssen Sie das Formular löschen und anschließend neu erstellen.
  
 Wenn Sie ein Schnellansichtsformular bearbeiten, müssen Sie Ihre Änderungen veröffentlichen, bevor sie in der Anwendung sichtbar sind.  
  
<a name="BKMK_AddQVF"></a>   
## <a name="add-a-quick-view-control-to-a-main-form"></a>Hinzufügen eines Schnellansicht-Steuerelement zu einem Hauptformular  
 Schnellansichtsformulare können nur einem Hauptformular hinzugefügt werden, das ein Suchfeld enthält, das auf die Entität des Schnellansichtsformulars verweist.  
  
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3. Wählen Sie ein Formular mit **Typ** **Haupt** aus.

4. Wählen Sie im Bereich Komponenten des Formulardesigners die Option **Schnellansicht** aus.  
  
5.  Wählen Sie im Dialogfeld **Schnellansichtsformulare auswählen** das Feld **Suche** und dann den Wert für das Suchfeld aus. Weitere Informationen: [Eigenschaften zum Steuerelement für die Schnellansicht](quick-view-control-properties-legacy.md)  

    > [!div class="mx-imgBorder"] 
    > ![Hinzufügen von Schnellansicht-Steuerelement](media/add-quick-view-control.png "Hinzufügen von Schnellansicht-Steuerelement zu Hauptformular")

6.  Wählen Sie **Fertig** aus, um das Dialogfeld **Schnellansichtsformulare auswählen** zu schließen. Das Schnellansichtsformular wird im Formular angezeigt.

7.  Wählen Sie **Speichern** aus, um das Formular zu speichern.  

## <a name="next-steps"></a>Nächste Schritte   
 [Erstellen und Gesalten von Formularen](create-design-forms.md)   
 [Schnellerstellungsformulare erstellen oder bearbeiten](create-edit-quick-create-forms.md)

---
title: Erstellen oder Bearbeiten von modellgesteuerter Schnellansichtsformulare-App in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Schnellansichtsformular erstellen oder bearbeiten
ms.custom: ''
ms.date: 05/23/2018
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
ms.openlocfilehash: 0384b233ddd9df0f88019df6064f5a99ef8af0bd
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759114"
---
# <a name="create-a-model-driven-app-quick-view-form-to-view-information-about-a-related-entity"></a>Erstellen und Bearbeiten eines Schnellansichtsformulars für modellgesteuerten Apps, um Informationen über eine verknüpfte Entität anzuzeigen

In diesem Thema erfahren Sie, wie Sie in ein Schnellansichtsformular erstellen und wie Sie ein Schnellansicht-Steuerelement ein Hauptformular hinzufügen. 

Ein Schnellansichtsformular kann einem anderen Formular als Steuerelement zur schnellen Anzeige hinzugefügt werden. Es bietet eine Vorlage für die Anzeige von Informationen zu verknüpften Entitätsdatensätzen innerhalb eines Formulars für einen anderen Entitätsdatensatz. Das bedeutet, dass Ihre App-Benutzer nicht zu einem anderen Datensatz wechseln müssen, um die Informationen anzuzeigen, die sie für ihre Arbeit benötigen.  
  
 Steuerelemente für die Schnellansicht sind mit einem Suchfeld verknüpft, das in einem Formular enthalten ist. Wenn der Suchfeldwert nicht festgelegt wurde, ist das Steuerelement für die Schnellansicht nicht sichtbar. Die Daten in den Schnellansicht-Steuerelementen sind nicht bearbeitbar, und Schnellansichtsformulare unterstützen keine Formularskripts.  
  
 Da Schnellansichtsformulare mithilfe eines Schnellansicht-Steuerelements in einem Formular angezeigt werden, enthalten sie keinen Kopf-, Fuß- oder Navigationsbereich. Schnellansichtsformularen können keine Sicherheitsrollen zugewiesen werden, und sie können nicht aktiviert oder deaktiviert werden.  
  
<a name="BKMK_CreateQFV"></a>   
## <a name="create-a-quick-view-form"></a>Erstellen eines Schnellansichtsformulars  
 Sie können Schnellansichtsformulare mithilfe des Formular-Editors erstellen, ähnlich wie auch andere Formulare erstellt werden. Schnellansichtsformulare sind schreibgeschützt. Verwenden Sie diese, um Formulare zu erstellen, um die nur zum Lesen bstimmt sind.  
  
1. Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  


    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).     
  
2. Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 
  
3. Wählen Sie in der Symbolleiste **Formular hinzufügen** > **Schnellansichtsformular** aus.  
  
4. Wählen Sie in der Formular-Editor-Symbolliste **Formulareigenschaften** aus.  
  
5. Geben Sie im Dialogfeld **Formulareigenschaften** einen **Formularnamen** und eine **Beschreibung** ein, um dieses Schnellansichtsformular von beliebigen anderen zu unterscheiden. Wählen Sie **OK** aus, um das Dialogfeld **Formulareigenschaften** zu schließen.  
  
6. Ziehen Sie im Formulardesigner beliebige Felder aus dem **Feld-Explorer** im Abschnitt im Formular. 
  
    > [!IMPORTANT]
    >  Wenn Sie ein Feld hinzufügen und auf **Feldanforderung** > **Eingabe erforderlich** klicken und dann speichern, ist es nicht möglich, das Feld zu löschen.  
  
7. Zum Speichern des Formulars und Schließen des Formular-Editor wählen Sie **Speichern und schließen** aus.  

8. Wählen Sie **Veröffentlichen**, damit das neue Formular in der Anwendung angezeigt wird.
  
<a name="BKMK_EditQVF"></a>   
## <a name="edit-a-quick-view-form"></a>Bearbeiten eines Schnellansichtsformulars  
 Schnellansichtsformulare besitzen ein vereinfachtes Layout, da sie zur Anzeige innerhalb eines Formularabschnitts konzipiert sind. Nur eine Einspaltenregisterkarte ist verfügbar. Sie können nur weitere Einspaltenabschnitte, Felder, Unterraster und Abstandhalter hinzufügen.   
  
> [!NOTE]
>  Sie können ein Feld nicht löschen, für das **Eingabe erforderlich** ist. Sie erhalten diese Nachricht, wenn Sie versuchen, das Feld zu löschen: "Das Feld, das Sie gerade zu entfernen versuchen, wird vom System oder Unternehmen benötigt." Wenn Sie das Feld nicht im Formular haben möchten, müssen Sie das gesamte Formular löschen und es dann neu erstellen.  
  
 Wenn Sie ein Schnellansichtsformular bearbeiten, müssen Sie Ihre Änderungen veröffentlichen, bevor sie in der Anwendung sichtbar sind.  
  
<a name="BKMK_AddQVF"></a>   
## <a name="add-a-quick-view-control-to-a-main-form"></a>Hinzufügen eines Schnellansicht-Steuerelement zu einem Hauptformular  
 Schnellansichtsformulare können nur einem Hauptformular hinzugefügt werden, das ein Suchfeld enthält, das auf die Entität des Schnellansichtsformulars verweist.  
  
1.  Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

    > [!IMPORTANT]
    > "Wenn der **Modell-angetrieben** Entwurfsmodus nicht verfügbar ist, müssen Sie ggf eine [Umgebung erstellen](https://docs.microsoft.com/powerapps/administrator/create-environment).     
  
2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3. Wählen Sie ein Formular mit **Typ** **Haupt** aus.

4. Wählen Sie im Formular-Designer auf die Registerkarte **Einfügen** und anschließend auf der Symbolleiste **Schnellansichtsformular** aus.  
  
5.  Im Dialogfeld **Eigenschaften zum Steuerelement für die Schnellansicht** legen Sie die Eigenschaften für das Steuerelement der Schnellansicht auf **Name**, **Bezeichnung** und **Schnellansichtsformular** fest. Weitere Informationen: [Eigenschaften zum Steuerelement für die Schnellansicht](quick-view-control-properties-legacy.md)  
  
6.  Wählen oder tippen Sie auf **OK**, um das Dialogfeld **Eigenschaften des Schnellansicht-Steuerelements** zu schließen.  
  
7.  Wählen Sie die Registerkarte **Startseite** und dann **Veröffentlichen** aus, um das Steuerelement für die Schnellansicht im Formular angezeigt werden.  
  
## <a name="next-steps"></a>Nächste Schritte   
 [Erstellen und Gesalten von Formularen](create-design-forms.md)   
 [Erstellen oder Bearbeiten von Schnellerstellungsformularen](create-edit-quick-create-forms.md)

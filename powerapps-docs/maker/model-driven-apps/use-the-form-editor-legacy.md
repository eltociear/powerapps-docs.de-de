---
title: Ändern der Navigation innerhalb eines modellgesteuerten App-Formulars in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Navigation in einem Formular ändern
ms.custom: ''
ms.date: 06/06/2018
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
ms.assetid: 4c379202-9f0e-4003-a49c-efff53e7f79f
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 92d76b056c21ebe583679bc51b73b04dcf812e69
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867585"
---
# <a name="change-navigation-within-a-model-driven-app-form"></a>Ändern der Navigation innerhalb eines modellgesteuerten Appformulars

 Die Navigation innerhalb des Formulars ermöglicht die Anzeige einer Liste verknüpfter Datensätze. Jede Entitätsbeziehung verfügt über Eigenschaften, die steuern, ob sie angezeigt werden soll. Weitere Informationen: [Navigationsbereichselement für die primäre Entität](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)  
  
 Alle Entitätsbeziehungen, die so konfiguriert werden, dass sie angezeigt werden, können im Formular-Editor überschrieben werden. Sie können auch Navigationslinks einschließen, um Webressourcen oder andere Websites per Formularnavigation anzuzeigen.  
  
 Genaue Anweisungen finden Sie unter [Erstellen und Bearbeiten von Entitätsbeziehungen für Common Data Service](../common-data-service/create-edit-entity-relationships.md)  
  
 Zur Aktivierung der Bearbeitung der Navigation müssen Sie zuerst den Befehl **Navigation** in der Gruppe **Auswählen** auf der Registerkarte **Start** des Formular-Designers auswählen.  
 
> [!div class="mx-imgBorder"] 
> ![Navigationsbefehl](media/navigation-command.png)
 
 Im rechten Bereich des **Beziehungs-Explorer** können Sie nach 1:n- oder n:n-Beziehungen filtern oder alle verfügbaren Beziehungen anzeigen Das Kontrollkästchen **Nur nicht verwendete Beziehungen anzeigen** ist aktiviert und ausgewählt. Sie können daher nur jeweils eine Beziehung gleichzeitig hinzufügen.  
 
 > [!div class="mx-imgBorder"] 
 > ![Beziehungs-Explorer](media/relationship-explorer.png)

 Um eine Beziehung aus dem **Beziehungs-Explorer** hinzuzufügen, doppelklicken Sie auf die Beziehung, und sie wird dann unter der aktuell ausgewählten Beziehung im Navigationsbereich hinzugefügt. Doppelklicken Sie auf eine Beziehung im Navigationsbereich und Sie können die Bezeichnung auf **Anzeigen** festlegen. Auf der Registerkarte **Name** können Sie Informationen zur Beziehung finden. Verwenden Sie die Schaltfläche **Bearbeiten**, um die Definition der Entität zu öffnen.  
  
 Es stehen fünf Gruppen im Navigationsbereich zur Verfügung. Sie können sie ziehen, um sie neu zu positionieren, und doppelklicken, um die Bezeichnung ändern, Sie können sie jedoch nicht entfernen. Diese Gruppen werden nur angezeigt, wenn sie Inhalte haben. Wenn Sie nicht wollen, dass eine Gruppe angezeigt wird, fügen Sie ihr einfach nichts hinzu.  
  
 Verwenden Sie die Schaltfläche **Navigationslink** in der Gruppe **Steuerelement** der Registerkarte **Einfügen**, um einen Link oder eine Webressource oder eine externe URL hinzuzufügen.  
 
 ![Navigationslink](media/navigation-link.png)
 
<a name="BKMK_NavigationLinkProperties"></a>   
### <a name="navigation-link-properties"></a>Navigationslinkeigenschaften  
 Navigationslinks haben die folgenden Eigenschaften:  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Name|**Erforderlich**: Als Beschriftung anzuzeigender Text.|  
|Symbol|Verwenden Sie eine Webressource mit 32 x 32 Pixeln. Verwenden Sie am besten ein PNG-Bild mit einem transparenten Hintergrund.|  
|Webressource|Geben Sie eine Webressource an, die im Formular im Hauptbereich anzuzeigen ist.|  
|Externe URL|Geben Sie die URL einer Seite an, die im Formular im Hauptbereich anzuzeigen ist.|  

<a name="BKMK_PrivacyNotices"></a>   

## <a name="privacy-notices"></a>Datenschutzhinweise  
 [!INCLUDE[cc_privacy_crm_website_preview_control](../../includes/cc-privacy-crm-website-preview-control.md)]    
  
 [!INCLUDE[cc_privacy_multimedia_control](../../includes/cc-privacy-multimedia-control.md)]  

## <a name="next-steps"></a>Nächste Schritte

[Übersicht zur Formular-Editor-Benutzeroberfläche](form-editor-user-interface-legacy.md)

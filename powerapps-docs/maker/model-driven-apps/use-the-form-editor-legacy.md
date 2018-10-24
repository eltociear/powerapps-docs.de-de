---
title: Ändern der Navigation in einem Formular einer modellgesteuerten App in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie die Navigation innerhalb eines Formulars geändert werden kann.
ms.custom: ''
ms.date: 06/06/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 5a8156875f669854a4ba4649e50a23e340f3ceff
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39681962"
---
# <a name="change-navigation-within-a-model-driven-app-form"></a>Ändern der Navigation innerhalb eines Formulars einer modellgesteuerten App

 Die Navigation in einem Formular ermöglicht App-Benutzern das Anzeigen von Listen der verknüpften Datensätze. Jede Entitätsbeziehung weist Eigenschaften auf, um zu steuern, ob diese angezeigt werden soll. Weitere Informationen finden Sie unter [Erstellen und Bearbeiten von Entitätsbeziehungen](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity).  
  
 Entitätsbeziehungen, die für die Anzeige konfiguriert sind, können innerhalb des Formular-Editors überschrieben werden. Sie können außerdem die Navigationslinks einschließen, um Webressourcen oder andere Websites über die Formularnavigation anzuzeigen.  
  
 Eine ausführliche Anleitung finden Sie unter [Überblick über Entitätsbeziehungen](../common-data-service/create-edit-entity-relationships.md).  
  
 Um die Bearbeitung der Navigation zu ermöglichen, müssen Sie zuerst auf der Registerkarte **Start** im Formular-Designer **Navigation** aus der Gruppe **Auswählen** auswählen.  
 
 ![Navigationsbefehl](media/navigation-command.png)
 
 Im rechten Bereich im **Beziehungs-Explorer** können Sie nach 1:n- oder m:n-Beziehungen filtern oder alle verfügbaren Beziehungen anzeigen. Das Kontrollkästchen **Nur unbenutzte Beziehungen anzeigen** wird deaktiviert und aktiviert. Daher können Sie jede Beziehung nur einmal hinzufügen.  
  
 ![Beziehungs-Explorer](media/relationship-explorer.png)

 Um eine Beziehung über den **Beziehungs-Explorer** hinzuzufügen, doppelklicken Sie einfach auf die Beziehung. Daraufhin wird sie unterhalb der momentan ausgewählte Beziehung im Navigationsbereich hinzugefügt. Doppelklicken Sie auf eine Beziehung im Navigationsbereich. Sie können dann die Beschriftung auf der Registerkarte **Anzeige** ändern. Auf der Registerkarte **Name** finden Sie Informationen über die Beziehung. Verwenden Sie die Schaltfläche **Bearbeiten**, um die Definition der Entität zu öffnen.  
  
 Es gibt fünf Gruppen im Navigationsbereich. Sie können ihre Position per Drag & Drop ändern und darauf doppelklicken, um die Beschriftung zu ändern, sie kann jedoch nicht entfernt werden. Diese Gruppen werden nur angezeigt, wenn sie etwas enthalten. Wenn eine Gruppe also nicht angezeigt werden soll, fügen Sie ihr nichts hinzu.  
  
 Klicken Sie auf die Schaltfläche **Navigationslink** in der Gruppe **Steuerelement** der Registerkarte **Einfügen**, um einen Link zu einer Webressource oder die externe URL hinzuzufügen.  
 
 ![Navigationslink](media/navigation-link.png)
 
<a name="BKMK_NavigationLinkProperties"></a>   
### <a name="navigation-link-properties"></a>Eigenschaften von Navigationslinks  
 Navigationslinks weisen die folgenden Eigenschaften auf:  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Name|**Erforderlich**: Text, der als Beschriftung angezeigt werden soll.|  
|Symbol|Verwenden Sie eine Webressource mit 32 x 32 Pixel. Es wird empfohlen, ein PNG-Bild mit transparentem Hintergrund zu verwenden.|  
|Webressource|Geben Sie eine Webressource an, die im Hauptbereich des Formulars angezeigt werden soll.|  
|Externe URL|Geben Sie die URL einer Seite an, die im Hauptbereich des Formulars angezeigt werden soll.|  

<a name="BKMK_PrivacyNotices"></a>   

## <a name="privacy-notices"></a>Datenschutzhinweise  
 [!INCLUDE[cc_privacy_crm_website_preview_control](../../includes/cc-privacy-crm-website-preview-control.md)]    
  
 [!INCLUDE[cc_privacy_multimedia_control](../../includes/cc-privacy-multimedia-control.md)]  

## <a name="next-steps"></a>Nächste Schritte

[Überblick über die Benutzeroberfläche des Formular-Editors](form-editor-user-interface-legacy.md)
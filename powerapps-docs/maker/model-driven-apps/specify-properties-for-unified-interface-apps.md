---
title: Angeben von Eigenschaften für modellgesteuerte Apps mit einheitlicher Benutzeroberfläche in PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das Rastersteuerelement in Ihrer App konfigurieren.
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 3ecea4a7-0d18-4ccd-9609-3a62179e9e1b
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 0
topic-status: Drafting
ms.openlocfilehash: 007ac566e317ee99bd85ab0675e5a53839800bb4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683513"
---
# <a name="specify-properties-for-model-driven-unified-interface-apps"></a>Angeben von Eigenschaften für modellgesteuerte Apps mit einheitlicher Benutzeroberfläche

Das Framework für einheitliche Oberflächen nutzt Prinzipien des reaktionsfähigen Designs, um eine optimale Anzeige und Interaktion für jede Bildschirmgröße und -ausrichtung zu ermöglichen. Bei modellgesteuerten Apps, die das Framework für einheitliche Oberflächen verwenden, ist das Steuerelement zur Anzeige des Rasters reaktionsfähig. Wenn ein Container verkleinert wird – z.B. auf Smartphones und in Viewports –, wird das Raster in eine Liste umgewandelt. 

Das Steuerelement für schreibgeschützte Raster gibt an, wie ein Raster in unterschiedlichen Bildschirmgrößen dynamisch umbrochen wird. Wenn Sie als App-Ersteller mit einer App mit einheitlicher Benutzeroberfläche arbeiten, können Sie das Steuerelement für schreibgeschützte Raster und dessen Eigenschaften für benutzerdefinierte Raster und Listen konfigurieren.
- **Card Form**-Eigenschaft: Verwenden Sie ein Kartenformular für Listen anstelle der standardmäßigen Listenvorlage. Kartenformulare bieten mehr Informationen für Listenelemente als die standardmäßige Listenvorlage.
- **Reflow Behavior**-Eigenschaft: Verwenden Sie diesen Parameter, um festzulegen, ob ein Raster in eine Liste dynamisch umbrochen werden soll oder nicht.

## <a name="allow-grid-to-reflow-into-list"></a>Zulassen des dynamischen Umbruchs eines Rasters in eine Liste

Durch Hinzufügen des Steuerelements für schreibgeschützte Raster zu Ihren Steuerelementen können Sie die folgenden Funktionen konfigurieren: 
- Lassen Sie zu, dass ein Raster auf kleinen Displays z.B. von Mobilgeräten dynamisch in eine Liste umbrochen wird.
- Geben Sie den Renderingmodus als „nur Raster“ oder „nur Liste“ an.  

1. Öffnen Sie den [Projektmappen-Explorer](advanced-navigation.md#solution-explorer).
2. Erweitern Sie im Navigationsbereich die Option **Entitäten**, wählen Sie die gewünschte Entität aus (z.B. **Konto** oder **Kontakt**), und klicken Sie dann auf der Registerkarte **Steuerelemente** auf **Steuerelement hinzufügen**.

    ![Öffnen von „Steuerelement hinzufügen“](media/UnifiedInterface_ReadOnlyGrid_AddControl.png "Öffnen von „Steuerelement hinzufügen“")

3. Wählen Sie **Read Only Grid** aus der Liste der Steuerelemente aus, und klicken Sie dann auf **Hinzufügen**.

    Das Steuerelement wird der Liste der verfügbaren Steuerelemente hinzugefügt.
   
    ![Auswählen eines Steuerelements](media/UnifiedInterface_ReadOnlyGrid_SelectControl.png "Auswählen eines Steuerelements")
    
4. Wählen Sie die Geräte aus (**Web**, **Smartphone** oder **Tablet**), für die Sie das Raster als schreibgeschützt festlegen möchten.

    ![Auswählen des Gerätetyps](media/UnifiedInterface_ReadOnlyGrid_SelectDevice.png "Auswählen von Geräten")

5. Konfigurieren Sie die **Card Form**-Eigenschaft.

    Sie können die Card Form-Eigenschaft verwenden, um Listenelemente anstelle der Standardlistenvorlage anzuzeigen. Kartenformulare bieten mehr Informationen für Listenelemente als die standardmäßige Listenvorlage.    

    a. Klicken Sie neben **Card Form** auf das Stiftsymbol.

    ![Bearbeiten des Kartenformulars](media/UnifiedInterface_ReadOnlyGrid_CardForm.png "Bearbeiten des Kartenformulars")

    b.  Wählen Sie die Typen **Entity** und **Card Form**.

    ![Eigenschaften des Kartenformulars](media/UnifiedInterface_ReadOnlyGrid_CardFormProperties.png "Eigenschaften des Kartenformulars")

    c. Klicken Sie auf **OK**.
6. Konfigurieren Sie die Eigenschaft **Reflow Behavior**. 
    
    a. Klicken Sie neben **Reflow Behavior** auf das Stiftsymbol.

    ![Bearbeiten des dynamischen Umbruchs](media/UnifiedInterface_ReadOnlyGrid_EditReflow.png "Bearbeiten des dynamischen Umbruchs")

    b. Wählen Sie in der Dropdownliste **An statische Optionen binden** den Umbruchtyp für das Raster aus.
    |Umbruchtyp|Beschreibung|
    |--------------|--------------------|
    |**Dynamischer Umbruch**|Ermöglicht es, das Raster im Listenmodus zu rendern, wenn auf dem Display nicht genügend Platz vorhanden ist.|
    |**Nur Raster**|Verhindert, dass das Raster im Listenmodus gerendert wird, auch wenn auf dem Display nicht genügend Platz vorhanden ist.|
    |**Nur Liste**|Es wird immer eine Liste angezeigt, auch wenn genügend Platz zur Anzeige als Raster vorhanden ist.|
    
     ![Eigenschaften des dynamischen Umbruchs](media/UnifiedInterface_ReadOnlyGrid_ReflowProperties.png "Eigenschaften des dynamischen Umbruchs")

    c. Klicken Sie auf **OK**.


7.  Speichern und veröffentlichen Sie die Änderungen. 


## <a name="conditional-image"></a>Bedingte Grafik
Sie können in einer Liste ein benutzerdefiniertes Symbol anstelle eines Werts anzeigen und mithilfe von JavaScript die Logik einrichten, die zur Auswahl der Option basierend auf den Werten einer Spalte verwendet wird. Weitere Informationen zu bedingten Grafiken finden Sie unter [Anzeigen von benutzerdefinierten Symbolen anstelle von Werten in Listenansichten](../common-data-service/display-custom-icons-instead.md).

## <a name="next-steps"></a>Nächste Schritte
[Erstellen oder Bearbeiten einer Ansicht](create-edit-views.md)
---
title: Festlegen von Eigenschaften für modellgesteuerte Einheitliche Oberfläche-Apps in Power Apps | Microsoft-Dokumentation
description: Erfahren Sie, wie das Rastersteuerelement für Ihre App konfiguriert wird
keywords: ''
ms.date: 06/03/2019
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 25e6125476ae3e5ceac47b0ef6b45f67ccfc1d3f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867893"
---
# <a name="specify-properties-for-model-driven-unified-interface-apps"></a>Festlegen von Eigenschaften für modellgesteuerte Einheitliche Oberfläche-Apps

Das „Einheitliche Oberfläche”-Framework verwendet dynamische Webdesignprinzipien, um bei jeder Bildschirmgröße oder -ausrichtung die bestmögliche Ansicht und Interaktion zu bieten. Mit modellgesteuerten Apps, die das Einheitliche Oberlfäche-Framework verwenden, ist das Raster-(Ansichts-)-Steuerelement dynamisch. Wenn die Größe des Containers abnimmt – beispielsweise bei Smartphones und kleineren Viewports – wird das Raster in eine Liste umgewandelt. 

Das schreibgeschützte Rastersteuerelement gibt an, wie ein Raster an verschiedene Bildschirmgrößen angepasst wird. Wenn Sie als App-Hersteller mit einer „Einheitliche Oberfläche”-App arbeiten, können Sie das schreibgeschützte Rastersteuerelement und dessen Eigenschaften für benutzerdefinierte Raster und Listen anpassen.
- **Kartenformular**-Eigenschaft: Verwenden Sie ein Kartenformular für Listen anstelle der Standardlistenvorlage. Kartenformulare stellen mehr Informationen zu Listenelementen bereit als die Standardlistenvorlage.
- **Dynamisches Umbruchsverhalten**-Eigenschaften: Geben Sie mit diesem Parameter an, ob ein Raster in eine Liste umgewandelt wird.

## <a name="allow-grid-to-reflow-into-list"></a>Raster in Liste umbrechen lassen

Durch Hinzufügen des schreibgeschützten Rastersteuerelements zu Ihrer Steuerelementliste können Sie die folgenden Funktionen konfigurieren: 
- Lassen Sie das Umbrechen eines Rasters in eine Liste bei kleinen Displays (z. B. Mobilgeräte) zu.
- Legen Sie den Rendermodus als "nur Raster" oder "nur Liste" fest.  

1. Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).
2. Erweitern Sie **Entitäten** im Navigationsbereich, wählen Sie die entsprechende Entität (beispielsweise **Firma** oder **Kontakt**) aus, und wählen Sie dann auf der Registerkarte **Steuerelemente** die Option **Steuerelement hinzufügen** aus.

    ![„Steuerelement hinzufügen“ öffnen](media/UnifiedInterface_ReadOnlyGrid_AddControl.png "„Steuerelement hinzufügen“ öffnen")

3. Wählen Sie in der Liste der Steuerlemente **Schreibgeschütztes Raster** aus, und wählen Sie dann **Hinzufügen** aus.

    Das Steuerelement wird der Liste verfügbarer Steuerelemente hinzugefügt.
   
    ![Steuerelement auswählen](media/UnifiedInterface_ReadOnlyGrid_SelectControl.png "Steuerelement auswählen")
    
4. Wählen Sie die Geräte aus (**Web**, **Telefon** oder **Tablet**), für die Sie ein schreibgeschütztes Raster möchten.

    ![Gerätetyp auswählen](media/UnifiedInterface_ReadOnlyGrid_SelectDevice.png "Geräte auswählen")

5. Konfigurieren Sie die **Kartenformular**-Eigenschaft.

    Sie können anstelle der Standardlistenvorlage die Kartenformular-Eigenschaft nutzen, um Listenelemente anzuzeigen. Kartenformulare stellen mehr Informationen zu Listenelementen bereit als die Standardlistenvorlage.    

    a. Wählen Sie das Stiftssymbol neben **Kartenformular** aus.

    ![Kartenformular bearbeiten](media/UnifiedInterface_ReadOnlyGrid_CardForm.png "Kartenformular bearbeiten")

    b.  Wählen Sie die Typen **Entität** und **Kartenformular** aus.

    ![Kartenformulareigenschaften](media/UnifiedInterface_ReadOnlyGrid_CardFormProperties.png "Kartenformulareigenschaften")

    c. Wählen Sie **OK**.
6. Konfigurieren Sie die **Dynamisches Umbruchsverhalten**-Eigenschaft. 
    
    a. Wählen Sie das Stiftssymbol neben **Dynamisches Umbruchsverhalten** aus.

    ![Dynamisches Umbruchsverhalten bearbeiten](media/UnifiedInterface_ReadOnlyGrid_EditReflow.png "Dynamisches Umbruchsverhalten bearbeiten")

    b. Wählen Sie den Rasterflusstyp aus dem Dropdwon **An statische Optionen binden** aus. 

    |Flusstyp|Beschreibung|
    |--------------|--------------------|
    |**Dynamischer Umbruch**|Ermöglicht dem Raster in einen Listenmodus gerendert zu werden, wenn nicht genügend Anzeigeplatz vorhanden ist.|
    |**Nur Raster**|Schränkt das Umbrechen des Rasterns in eine Liste auch dann ein, wenn nicht genügend Anzeigeplatz vorhanden ist.|
    |**Nur Liste**|Wird nur als Liste angezeigt, auch wenn ausreichend Platz zur Anzeige als Raster vorhanden ist.|
    
     ![Dynamisches Umbruchsverhalten – Eigenschaften](media/UnifiedInterface_ReadOnlyGrid_ReflowProperties.png "Dynamisches Umbruchsverhalten – Eigenschaften")

    c. Wählen Sie **OK**.


7.  Speichern und veröffentlichen Sie die Änderungen. 


## <a name="conditional-image"></a>Bedingtes Bild
Sie können ein benutzerdefiniertes Symbol anstelle eines Werts in der Liste anzeigen und die Logik zum Auswählen dieser basierend auf den Werten einer Spalte mit JavaScript erstellen. Weitere Informationen zu bedingten Bildern finden Sie unter [Benutzerdefinierte Symbole anstelle von Werten in Listenansichten anzeigen](../common-data-service/display-custom-icons-instead.md).

## <a name="next-steps"></a>Nächste Schritte
[Ansicht erstellen oder bearbeiten](create-edit-views.md)

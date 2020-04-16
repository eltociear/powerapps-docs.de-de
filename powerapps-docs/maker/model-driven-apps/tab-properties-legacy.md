---
title: Registerkarten-Eigenschaften für Formulare in modellgesteuerten Apps in Power Apps | Microsoft-Dokumentation
description: Grundlegendes zur Registerkarteneigenschaften für Hauptformulare
Keywords: Registerkarteneigenschaften; Dynamics 365; Hauptformulare
author: matp
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: Mattp123
manager: kvivek
ms.date: 03/17/2020
ms.service: powerapps
ms.topic: article
ms.assetid: e0790865-c5a4-4e86-bce2-584af2b8ed93
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 613352e9ec86101b776fce5b0bf18d64b175f363
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166528"
---
# <a name="tab-properties-for-model-driven-app-forms-overview"></a>Registerkarten-Eigenschaften für Hauptformulare in modellgesteuerten Apps im Überblick

 Im Textkörper der Formularregisterkarten steht eine horizontale Trennung zur Verfügung. Registerkarten haben eine Beschriftung, die angezeigt werden kann. Wenn die Beschriftung angezeigt wird, können Registerkarten erweitert oder reduziert werden, um ihre Inhalte ein- oder auszublenden, indem Sie die Beschriftung auswählen.  
  
 Registerkarten enthalten bis zu drei Spalten, und die Breite der Spalten kann auf einen Prozentsatz der Gesamtbreite festgelegt werden. Wenn Sie eine neue Registerkarte erstellen, wird die Spalte mit Abschnitt vorab ausgefüllt.  

Sie können auf **Registerkarten-Eigenschaften** über die Power Apps-Website zugreifen. 
1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3.  Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**. Wählen Sie dann eine der Registerkarten im Formular aus, um die Registerkarteneigenschaften anzuzeigen.

|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Registerkartenbeschriftung**|**Erforderlich**: Die lokalisierbare Beschriftung für die Registerkarte, die für Benutzer sichtbar ist.|  
|**Name**|**Erforderlich**: Der eindeutige Name für die Registerkarte, der verwendet wird, wenn auf sie in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten.|  
|**Registerkarte standardmäßig erweitern**|Der Status der Registerkarte kann durch Formularskripts oder durch Klicken auf die Beschriftung zwischen erweitert und reduziert gewechselt werden. Wählen Sie den Standardstatus für die Registerkarte.|  
|**Registerkarte ausblenden**|Die Anzeige der Registerkarte ist optional und kann durch Skripts gesteuert werden. Wählen Sie, ob die Registerkarte angezeigt werden soll. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md)|  
|**Auf Telefon ausblenden**|Wählen Sie, ob Sie möchten, dass die Registerkarte auf dem Smartphone verfügbar ist. Um eine verkürzte Version dieses Formulars auf Smartphone-Bildschirmen anzuzeigen, können Sie die Registerkarte ausblenden.|  
|**Formatierung**|Registerkarten können bis zu drei Spalten haben. Verwenden Sie diese Optionen, um die Anzahl der Spalten festzulegen, sowie, welchen Prozentsatz der gesamten Breite sie ausfüllen sollen.|  

  > [!div class="mx-imgBorder"] 
  > ![Registerkarteneigenschaften](media/newform-tab-properties.png "Eigenschaften der Registerkarte")

## <a name="tab-properties-for-model-driven-app-main-forms-classic"></a>Registerkarteneigenschaften für Hauptformulare in modellgesteuerten Apps: Klassisch

Dies sind die Eigenschaften, die konfiguriert werden können, wenn eine Registerkarte in einem Formular mithilfe des klassischen Formulardesigners verwendet wird. Die folgende Tabelle zeigt Eigenschaften, die Sie für Registerkarten im Formular festlegen können:
  
|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Anzeigen**|**Name**|**Erforderlich**: Der eindeutige Name für die Registerkarte, der verwendet wird, wenn auf sie in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten.|  
||**Bezeichnung**|**Erforderlich**: Die lokalisierbare Beschriftung für die Registerkarte, die für Benutzer sichtbar ist.|  
||**Beschriftung dieser Registerkarte auf dem Formular anzeigen**|Wenn die Beschriftung angezeigt wird, können Benutzer darauf klicken, um die Registerkarte zu erweitern oder zu reduzieren. Wählen Sie, ob Beschriftung angezeigt werden soll.|  
||**Registerkarte standardmäßig erweitern**|Der Status der Registerkarte kann durch Formularskripts oder durch Klicken auf die Beschriftung zwischen erweitert und reduziert gewechselt werden. Wählen Sie den Standardstatus für die Registerkarte.|  
||**Standardmäßig sichtbar**|Die Anzeige der Registerkarte ist optional und kann durch Skripts gesteuert werden. Wählen Sie, ob die Registerkarte angezeigt werden soll. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md)|  
||**Verfügbarkeit**|Wählen Sie, ob Sie möchten, dass die Registerkarte auf dem Smartphone verfügbar ist.|  
|**Formatierung**|**Layout**|Registerkarten können bis zu drei Spalten haben. Verwenden Sie diese Optionen, um die Anzahl der Spalten festzulegen, sowie, welchen Prozentsatz der gesamten Breite sie ausfüllen sollen.|  
|**Ereignisse**|**Formularbibliotheken**|Geben Sie JavaScript-Webressourcen an, die in der Registerkarte `TabStateChange`-Ereignishandler verwendet werden sollen.<br /><br />|  
||**Ereignishandler**|Konfigurieren Sie die Funktionen aus den Bibliotheken, die für das Ereignis `TabStateChange`-Registerkarte aufgerufen werden sollen. Weitere Informationen: [Konfigurieren Sie Ereignishandler](configure-event-handlers-legacy.md)|  

  > [!div class="mx-imgBorder"] 
  > ![Registerkarteneigenschaften Klassisch](media/tab-properties.png "Registerkarteneigenschaften in Klassisch")

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)

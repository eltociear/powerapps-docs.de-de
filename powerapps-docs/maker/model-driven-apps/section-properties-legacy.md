---
title: Abschnittseigenschaften für Hauptformulare in modellgesteuerten Apps in Power Apps | Microsoft-Dokumentation
description: Grundlegendes zu Abschnittseigenschaften für ein Hauptformular
Keywords: Hauptformular; Abschnittseigenschaften; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 03/23/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 2d3af6e9-e8a4-4129-b708-383b2740c015
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 25d2edd58bf146f9537af87a0b7564b4ce421395
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166572"
---
# <a name="model-driven-app-form-section-properties"></a>Abschnittseigenschaften von Formularen in modellgesteuerten Apps.

 Ein Abschnitt in einem Formular nimmt den in einer Registerkartenspalte verfügbaren Raum ein. Abschnitte enthalten eine Beschriftung, die angezeigt werden kann, sowie eine Zeile, die unter der Beschriftung angezeigt werden kann.  
  
 Abschnitte können bis zu 4 Spalten enthalten und enthalten Optionen für die Anzeigen von Bezeichnungen für Felder im Abschnitt.  
  
 Kopf- und Fußzeilen entsprechen Abschnitten, können jedoch nicht entfernt werden. Wenn Sie nichts enthalten, werden sie nicht angezeigt.

## <a name="section-properties-in-form-designer"></a>Abschnittseigenschaften in Formulardesigner

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3.  Öffnen Sie in der Liste der Formulare ein Formular des Typs **Haupt**. Um ein Formular in einer anderen Registerkarte zu öffnen, wählen Sie **Weitere Befehle** ![Schaltfläche „Weitere Befehle“](media/more-commands.gif "Schaltfläche „Weitere Befehle“ für Formulare") und dann **Formular bearbeiten** > **Formular in neuer Registerkarte bearbeiten** aus.

4.  Wählen Sie einen der Abschnitte aus, um die Abschnittseigenschaften anzuzeigen.

    > [!div class="mx-imgBorder"]
    > ![Abschnittseigenschaften](media/new-section-properties.png "Abschnittseigenschaften in Formulardesigner")

|Eigenschaft|Beschreibung|  
|---------|--------------|  
|**Abschnittsbeschriftung**|**Erforderlich**: Die lokalisierbare Beschriftung für den Abschnitt, die für Benutzer sichtbar ist.|  
|**Name**|**Erforderlich**: Der eindeutige Name für den Abschnitt, der verwendet wird, wenn auf ihn in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten.|  
|**Beschriftung ausblenden**|Abschnitte werden oft ohne Beschriftungen verwendet, um die Formatierung der Felder darin zu steuern.|
|**Auswahl sperren**|Dies verhindert, dass der Abschnitt und sein Inhalt versehentlich entfernt werden.<br /><br /> Das Entfernen eines Abschnitts entfernt nicht nur diesen selbst, sondern auch alle darin befindlichen Felder.<br /><br /> Wer diesen Abschnitt entfernen möchte, müsste vorher diese Einstellung ändern.|  
|**Abschnitt auswählen**|Die Anzeige des Abschnitts ist optional und kann durch Skripts gesteuert werden. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md)|  
|**Auf Telefon ausblenden**|Wählen Sie, ob Sie möchten, dass die Registerkarte auf dem Smartphone verfügbar ist.|  
|**Formatierung**|Geben Sie maximal vier Spalten für den Abschnitt an.|  

## <a name="section-properties-in-classic-form-designer"></a>Abschnittseigenschaften in klassischem Formulardesigner

Sie können auf **Abschnittseigenschaften** im Projektmappen-Explorer aus der Power Apps-Site zugreifen.

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3.  Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**. 

4.  Wählen Sie **In klassischen Modus wechseln** aus, um das Formular im klassischen Formulardesigner zu bearbeiten.

5.  Doppelklicken Sie in einem der Abschnitte, um die Abschnittseigenschaften anzuzeigen. 

    > [!div class="mx-imgBorder"]
    > ![Abschnittseigenschaften](media/section-properties.png "Abschnittseigenschaften in Projektmappen-Explorer")
  
|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Anzeige**|**Name**|**Erforderlich**: Der eindeutige Name für den Abschnitt, der verwendet wird, wenn auf ihn in Skripts verwiesen wird. Der Name kann nur alphanumerische Zeichen und Unterstrichzeichen enthalten.|  
||**Bezeichnung**|**Erforderlich**: Die lokalisierbare Beschriftung für den Abschnitt, die für Benutzer sichtbar ist.|  
||**Beschriftung dieses Abschnitts auf dem Formular anzeigen**|Abschnitte werden oft ohne Beschriftungen verwendet, um die Formatierung der Felder darin zu steuern.|  
||**Zeile am oberen Rand des Abschnitts anzeigen**|Eine Zeile oben in einem Abschnitt kann Sie bei der Unterteilung des Formularlayouts unterstützen.|  
||**Breite der Feldbeschriftung**|**Erforderlich**: Legen Sie einen Wert zwischen 50 und 250 fest, um den für Feldbeschriftungen verfügbaren Raum zu begrenzen.<br /><br /> Kopfzeilen- und Fußzeilenelemente haben auch diese Eigenschaft.|  
||**Sichtbarkeit**|Die Anzeige des Abschnitts ist optional und kann durch Skripts gesteuert werden. Weitere Informationen: [Sichtbarkeitsoptionen](visibility-options-legacy.md)|  
||**Verfügbarkeit**|Wählen Sie, ob Sie möchten, dass die Registerkarte auf dem Smartphone verfügbar ist.|  
||**Abschnitt auf dem Formular sperren**|Dies verhindert, dass der Abschnitt und sein Inhalt versehentlich entfernt werden.<br /><br /> Das Entfernen eines Abschnitts entfernt nicht nur diesen selbst, sondern auch alle darin befindlichen Felder.<br /><br /> Wer diesen Abschnitt entfernen möchte, müsste vorher diese Einstellung ändern.|  
|**Formatierung**<br /><br /> Kopfzeilen- und Fußzeilenkomponenten haben auch diese Eigenschaft.|**Layout**|Geben Sie maximal vier Spalten für den Abschnitt an.|  
||**Ausrichtung der Feldbeschriftung**|Beschriftungen für Felder innerhalb des Abschnitts können links, rechts oder zentriert ausgerichtet werden.|  
||**Position der Feldbeschriftung**|Beschriftungen für Felder innerhalb des Abschnitts können an der Seite oder oberhalb von Feldern positioniert werden.|  


Ein neuer Abschnitttyp namens **Bereichs-Verweise** kann ebenfalls hinzugefügt werden. Ein Verweisbereich ist ein Einspaltenabschnitt. Sie können Unterraster, Schnellansichtssteuerelemente oder ein Steuerelement für Wissensdatenbanksuchen im Bereich Verweis hinzufügen. Jedes Steuerelement, das Sie im Bereich ""Verweise" hinzugefügt haben, wird als vertikale Registerkarte innerhalb des Bereichs zur Laufzeit angezeigt. Sie können verschiedene Steuerelemente innerhalb des Bereichs Verweis per Drag & Drop bewegen. Die Standardregisterkarte zur Laufzeit ist das erste Steuerelement, das zum Bereich „Verweise“ hinzugefügt wurde. Die anderen Registerkarten werden in der Reihenfolge angezeigt, in der sie im Formular-Editor hinzugefügt wurden. Um eine Registerkarte zu löschen, drücken Sie die Taste ENTF.  
  
Wenn Sie einen Bereich Verweise einfügen, wird er standardmäßig als letzter Abschnitt auf der Registerkarte hinzugefügt. Sie können nur einen Bereich Verweise pro Formular hinzufügen.  
  
> [!IMPORTANT]
>  Standardmäßig ist der Bereich "Verweise" in den diesen Standardformularen gesperrt: Anfragen, Firma und Kontakt. Um ihn zu entfernen oder zu ändern, entsperren Sie ihn. 

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)

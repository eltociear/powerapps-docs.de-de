---
title: Abschnittseigenschaften für Hauptformulare in modellgesteuerten Apps in PowerApps | Microsoft-Dokumentation
description: Grundlegendes zu Abschnittseigenschaften für ein Hauptformular
Keywords: Hauptformular; Abschnittseigenschaften; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/06/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 2d3af6e9-e8a4-4129-b708-383b2740c015
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 45764a992215c697361f77da656182bdbb0e7783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755001"
---
# <a name="model-driven-app-form-section-properties"></a>Abschnittseigenschaften von Formularen in modellgesteuerten Apps.

 Ein Abschnitt in einem Formular nimmt den in einer Registerkartenspalte verfügbaren Raum ein. Abschnitte enthalten eine Beschriftung, die angezeigt werden kann, sowie eine Zeile, die unter der Beschriftung angezeigt werden kann.  
  
 Abschnitte können bis zu 4 Spalten enthalten und enthalten Optionen für die Anzeigen von Bezeichnungen für Felder im Abschnitt.  
  
 Kopf- und Fußzeilen entsprechen Abschnitten, können jedoch nicht entfernt werden. Wenn Sie nichts enthalten, werden sie nicht angezeigt. 

Sie können auf **Abschnittseigenschaften** über die PowerApps-Website zugreifen. 
1. Melden Sie sich bei [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3.  Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**. Doppelklicken Sie dann innerhalb eines der Abschnitte, um die Abschnittseigenschaften zu sehen. 

    ![Abschnittseigenschaften](media/section-properties.png)
  
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
  
Wenn Sie einen Bereich Verweise einfügen, enthält er standardmäßig da ein letzter Abschnitt der Registerkarte hinzugefügt. Sie können nur einen Bereich Verweise pro Formular hinzufügen.  
  
> [!IMPORTANT]
>  Standardmäßig ist der Bereich "Verweise" in den diesen Standardformularen gesperrt: Anfragen, Firma und Kontakt. Um ihn zu entfernen oder zu ändern, entsperren Sie ihn. 

## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)

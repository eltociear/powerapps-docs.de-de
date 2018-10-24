---
title: Einrichten des Notizensteuerelements in modellgesteuerten Apps zum Zugreifen auf Informationen zu Beiträgen in PowerApps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/06/2018
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
ms.assetid: f10cdf1c-3540-439c-a171-27a10e72da45
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 014f0c2516813b7cbcaa8e44a188455b07056c71
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39689186"
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>Einrichten des Notizensteuerelements in modellgesteuerten Apps zum Zugreifen auf Informationen zu Beiträgen

 In PowerApps-Formularen für bestimmte Systementitäten, die [aktualisierte Formulare](main-form-presentations.md#updated-forms) verwenden, bietet das Notizensteuerelement die Möglichkeit, auf Informationen zu **Beiträgen**, **Aktivitäten** und **Notizen** zuzugreifen. Für benutzerdefinierte Entitäten, für die Sie Notizen und Aktivitäten aktiviert haben, sehen Sie nur **Notizen** und **Aktivitäten**. Um **Beiträge** einzuschließen, müssen Sie sie für die benutzerdefinierte Entität aktivieren.  
  
## <a name="enable-posts-for-a-custom-entity"></a>Aktivieren von Beiträgen für eine benutzerdefinierte Entität  
  
1.  Gehen Sie zu **[Einstellungen](advanced-navigation.md#settings)** > **Konfiguration von Aktivitätsfeeds**. 
  
2.  Öffnen Sie den Eintrag für Ihre benutzerdefinierte Entität.  
  
3.  Überprüfen Sie, ob **Pinnwände für diese Art von Datensatzformular aktivieren** ausgewählt ist, und speichern Sie den Datensatz.  
  
4.  Wählen Sie in der Befehlsleiste **Aktivieren** aus.  
  
5.  Wenn Sie Pinnwände aktivieren möchten, müssen Sie die Entität veröffentlichen.  
  
 Standardmäßig befindet sich das Notizensteuerelement für Systementitäten in einem Social Media-Bereich in der Mitte einer dreispaltigen Registerkarte oben im Formular. Es kann nur einmal in einem Formular angezeigt werden. Sie können das Notizensteuerelement verschieben oder entfernen. Um es wieder hinzuzufügen, verwenden Sie auf der Registerkarte **Einfügen** in der Gruppe **Steuerung** die Schaltfläche **Notizen**.  
  
 Die folgende Tabelle beschreibt die Eigenschaften des Notizensteuerelements.  
  
|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Anzeige**|**Bezeichnung**|**Erforderlich**: Obwohl die Bezeichnung nicht standardmäßig angezeigt wird, muss sie angegeben werden.|  
||**Bezeichnung im Formular anzeigen**|Sie können auswählen, dass die Bezeichnung angezeigt wird.|  
||**Feld im Formular sperren**|Diese Eigenschaft verhindert, dass Notizen versehentlich aus dem Formular entfernt werden.|  
||**Standardregisterkarte**|Wählen Sie aus, welche Registerkarte standardmäßig angezeigt wird. Die Optionen sind:<br /><br /> - **Aktivitäten**<br />- **Beiträge**<br />- **Notizen**|  
|**Formatierung**|**Wählen Sie die Anzahl der Spalten, die vom Steuerelement belegt werden**|Wenn der Abschnitt mit dem Notizensteuerelement mehrere Spalten enthält, können Sie die Anzahl von zu belegenden Feldern bis zu der Anzahl von im Abschnitt enthaltenen Spalten festlegen.|  
||**Anzahl von Zeilen**|Bestimmen Sie die Höhe des Notizensteuerelements, indem Sie die Anzahl von Zeilen auswählen, die das Steuerelement einnimmt.|  
||**Automatisch erweitern, um verfügbaren Bereich auszufüllen**|Anstatt die Höhe durch eine Zahl von Zeilen anzugeben, können Sie zulassen, dass die Höhe des Notizensteuerelements den verfügbaren Raum einnimmt.|  
  
## <a name="next-steps"></a>Nächste Schritte
[Öffnen des Formular-Editors](open-form-editor.md)

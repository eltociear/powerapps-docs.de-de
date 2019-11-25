---
title: Einrichten des Hinweis-Steuerelements in modellgesteuerten Apps für den Zugriff auf Informationen über Beiträge in PowerApps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/06/2018
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
ms.assetid: f10cdf1c-3540-439c-a171-27a10e72da45
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bb60588e34e66fc1a0222d18e90d50af672bcc69
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711693"
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>Einrichten des Hinweis-Steuerelements in modellgesteuerten Apps für den Zugriff auf Informationen über Beiträge

 In PowerApps-Formularen für bestimmte Systemeinheiten, die die [Updated forms](main-form-presentations.md#updated-forms) verwenden, bietet das Notes-Control die Möglichkeit, auf Informationen über **Posts**, **Aktivitäten** und **Notes** zuzugreifen. Bei benutzerdefinierten Entitäten, bei denen Sie Notizen und Aktivitäten aktiviert haben, sehen Sie nur **Notizen** und **Aktivitäten**. Um **Beiträge** einzuschließen, müssen Sie sie für die benutzerdefinierte Entität aktivieren.  
  
## <a name="enable-posts-for-a-custom-entity"></a>Nachrichten für eine benutzerdefinierte Entität aktivieren  
  
1.  Öffnen Sie **[Einstellungen](advanced-navigation.md#settings)** > **Konfiguration von Aktivitätsfeeds**. 
  
2.  Öffnen Sie den Datensatz für die benutzerdefinierte Entität.  
  
3.  Stellen Sie sicher, dass **Pinnwände für diese Art von Datensatzformular aktivieren** ausgewählt ist, und speichern Sie den Datensatz.  
  
4.  In der Befehlsleiste wählen Sie **Aktivieren** aus.  
  
5.  Wenn Sie Fall Pinnwände aktivieren müssen, müssen Sie die Entität veröffentlichen.  
  
 Für Systementitäten ist das Notizensteuerelement standardmäßig in einem "Sozialen" Bereich in der Mitte der dreispaltigen Registerkarte am oberen Rand des Formulars positioniert. Es kann nur einmal in einem Formular angezeigt werden. Sie können das Notizensteuerelement verschieben oder entfernen. Um es wieder hinzuzufügen, verwenden Sie die Schaltfläche **Notizen** in der Gruppe **Steuerung** der Registerkarte **Einfügen**.  
  
 Die folgende Tabelle beschreibt die Eigenschaften des Notizensteuerelements.  
  
|Registerkarte|Eigenschaft|Beschreibung|  
|---------|--------------|-----------------|  
|**Anzeige**|**Bezeichnung**|**Erforderlich**: Obwohl die Beschriftung nicht standardmäßig angezeigt wird, ist eine Beschriftung erforderlich.|  
||**Beschriftung im Formular anzeigen**|Sie können wählen, die Beschriftung anzuzeigen.|  
||**Feld im Formular sperren**|Auf diese Weise wird verhindert, dass die Notizen versehentlich aus dem Formular entfernt werden.|  
||**Standardregisterkarte**|Wählen Sie aus, welche Registerkarte standardmäßig angezeigt werden soll. Die Optionen sind:<br /><br /> - **Aktivitäten**<br />- **Nachrichten**<br />- **Notizen**|  
|**Formatierung**|**Wählen Sie die Anzahl der Spalten, die vom Steuerelement belegt werden**|Wenn der Abschnitt, der das Notizensteuerelement enthält, mehr als eine Spalte enthält, können Sie festlegen, dass das Feld die Anzahl von Spalten belegt, die der Abschnitt enthält.|  
||**Anzahl der Zeilen**|Sie können die Höhe des Notizensteuerelements steuern, indem Sie eine Zahl von Zeilen auswählen.|  
||**Automatisch erweitern, um verfügbaren Bereich auszufüllen**|Anstatt die Höhe durch eine Zahl von Zeilen anzugeben, können Sie zulassen, dass die Höhe des Notizensteuerelements den verfügbaren Raum einnimmt.|  
  
## <a name="next-steps"></a>Nächste Schritte
[Öffnen des Formulareditors](open-form-editor.md)

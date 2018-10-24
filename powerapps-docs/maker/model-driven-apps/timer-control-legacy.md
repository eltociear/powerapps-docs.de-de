---
title: Zeitgeber-Steuerelement einer modellgesteuerten App in PowerApps | Microsoft-Dokumentation
description: In diesem Artikel wird erläutert, wie Sie das Zeitgeber-Steuerelement verwenden können.
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
ms.assetid: b2b64771-083b-42f9-a3d5-2218f9d8a713
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 7df13482e7773abc3e6762f80bd9f6b99c7ba9e6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683066"
---
# <a name="model-driven-app-timer-control-overview"></a>Übersicht über das Zeitgeber-Steuerelement einer modellgesteuerten App

 Verwenden Sie ein Zeitgeber-Steuerelement bei Formularen, bei denen Datensätze einen bestimmten zeitbasierten Meilenstein erfüllen müssen. Ein Zeitgeber-Steuerelement zeigt Benutzern, wie viel Zeit zum Ausführen einer Aktion bei der Auflösung eines aktiven Datensatzes verfügbar ist oder wie viel Zeit seit der Ausführung der Aktion verstrichen ist. Zeitgeber-Steuerelemente müssen mindestens für die Anzeige einer erfolgreichen oder fehlerhaften Ausführung der Aktion konfiguriert werden. Darüber hinaus können sie so konfiguriert werden, dass Warnungen angezeigt werden, wenn die Bedingungen Fehler aufweisen.  
  
 Einem Formular für eine beliebige Entität kann ein Zeitgeber-Steuerelement hinzugefügt werden, aber sie werden am häufigsten für die Fallentität verwendet, insbesondere, wenn diese mit Feldern verknüpft wird, die Vereinbarungen zum Servicelevel nachverfolgen. Sie können mehrere Zeitgeber-Steuerelemente im Text eines Formulars hinzufügen. Sie können sie nicht der Kopf- oder Fußzeile hinzufügen.  
  
 Die Eigenschaften von **Datenquelle** für das Zeitgeber-Steuerelement verwenden Felder für die Entität.  
  
-   Das **Feld "Fehlerzeit"** verwendet ein Feld für Datum/Uhrzeit, um die Zeit festzulegen.  
  
-   Die drei Bedingungsfelder verwenden eines der folgenden Felder für die Entität: **Optionssatz**, **Zwei Optionen**, **Status**, oder **Statusgrund**.  

Um ein Zeitgeber-Steuerelement zu erstellen, wählen Sie im Formular-Designer die Registerkarte **Einfügen** und dann auf der Symbolleiste **Zeitgeber** aus. 

  ![Einfügen des Zeitgeber-Steuerelements](media/insert-timer-control.png)

Geben Sie auf der Eigenschaftenseite „Zeitgeber-Steuerelement“ die gewünschten Eigenschaften ein, oder wählen Sie sie aus. Klicken Sie anschließend auf **OK**. 

  
<a name="BKMK_TimerControlProperties"></a>   

## <a name="timer-control-properties"></a>Eigenschaften des Zeitgeber-Steuerelements  
 In der folgenden Tabelle werden die Eigenschaften eines Zeitgeber-Steuerelements beschrieben.  
  
|Gruppe|Name|Beschreibung|  
|-----------|----------|-----------------|  
|Name|Name|**Erforderlich**. Ein eindeutiger Name für das Steuerelement.|  
||Bezeichnung|**Erforderlich**. Die Beschriftung, die für das Zeitgeber-Steuerelement angezeigt werden soll.|  
|Datenquelle|Feld „Zeitfehler“|**Erforderlich**. Wählen Sie eines der Felder für Datum/Uhrzeit für die Entität aus, um darzustellen, wann ein Meilenstein erfolgreich abgeschlossen werden sollte.|  
||Erfolgsbedingung|**Erforderlich**. Wählen Sie ein Feld für die Entität aus, das den Erfolg des Meilensteins auswertet, und wählen Sie dann aus, welche Option auf eine erfolgreiche Ausführung hinweist.|  
||Warnungsbedingung|Wählen Sie ein Feld für die Entität aus, um auszuwerten, ob der Erfolg des Meilensteins gefährdet ist, sodass eine Warnung angezeigt werden sollte. Wählen Sie dann aus, welche Option angibt, dass eine Warnung angezeigt werden sollte.|  
||Abbruchbedingung|Wählen Sie ein Feld für die Entität aus, um auszuwerten, ob das Erreichen des Meilensteins abgebrochen werden muss, und wählen Sie dann die Option aus, die angibt, dass der Meilenstein abgebrochen wird.|  

## <a name="next-steps"></a>Nächste Schritte

[Überblick über die Benutzeroberfläche des Formular-Editors](form-editor-user-interface-legacy.md)
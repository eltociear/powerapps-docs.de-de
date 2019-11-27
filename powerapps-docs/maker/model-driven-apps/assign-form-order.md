---
title: Modellgesteuerte App Formular-Aufträgen zuweisen PowerApps | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das Standardformular in Ihrer App zuweisen
ms.custom: ''
ms.date: 03/07/2019
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
ms.assetid: 914c5694-9c80-4424-be89-9f63256b4811
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 90190dc9021d3852d123dd63e678c7924e164838
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700869"
---
# <a name="assign-model-driven-app-form-order"></a>Modell-angetriebenen App-Formularauftrag zuweisen

 Wenn Sie mehrere Haupt-, Schnellerfassungs- , Schnellansichts- oder Kartenformulare für eine Entität haben, können Sie ihnen eine Reihenfolge zuweisen. Die Formularreihenfolge legt fest, welche der verfügbaren Formulare standardmäßig angezeigt werden. Die verfügbaren Hauptformulare können weiter durch die Zuweisung von Sicherheitsrollen zum Formular gesteuert werden. Weitere Informationen finden Sie unter [Steuern des Zugriffs auf Formulare](control-access-forms.md)  
  
 Sie können keine Sicherheitsrollen zu Schnellerfassungs-, Schnellansichts- oder Kartenformularen zuweisen. Das einzige Formular, das von allen Benutzern benutzt wird, ist das erste in der Formularreihenfolge.  
  
## <a name="to-assign-a-form-order"></a>Zuweisen einer Formularreihenfolge  
  
1.  [Lösungsexplorer](advanced-navigation.md#solution-explorer) öffnen, um die gewünschte Entität zu erweitern und dann **Formular** auswählen.  
  
2.  Wählen Sie auf der Formularlistensymbolleiste die Option **Formularreihenfolge**.  

     > [!div class="mx-imgBorder"] 
     > ![Formularauftrags-Symbolleistenbefehl](media/form-order.png)
  
3.  Wählen Sie **Hauptformularsatz**, **Formularsatz für Schnellerfassung**, **Schnellansichtsformular** oder **Kartenformularsatz**, je nach Art der Formulare, die Sie verwenden möchten. Weitere Informationen: [Feldtypen](types-forms.md). 
  
4.  Das Dialogfeld **Formularreihenfolge** ist eine einfache Liste, in der Sie ein ausgewähltes Formular auf- oder abwärts verschieben können.  
  
5.  Wenn Sie damit fertig sind, klicken Sie auf **OK**, um das Dialogfeld zu schließen.  

## <a name="next-steps"></a>Nächste Schritte

[Navigation innerhalb eines Formulars ändern](use-the-form-editor-legacy.md)

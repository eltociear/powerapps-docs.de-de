---
title: Zuweisen einer Reihenfolge für Formulare einer modellgesteuerten App in PowerApps | Microsoft-Dokumentation
description: Informationen zum Zuweisen des Standardformulars in einer App
ms.custom: ''
ms.date: 06/22/2018
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
ms.assetid: 914c5694-9c80-4424-be89-9f63256b4811
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 22ed9c144c90c5393b6d9e76692172f0dd067225
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39685185"
---
# <a name="assign-model-driven-app-form-order"></a>Zuweisen einer Reihenfolge für Formulare einer modellgesteuerten App

 Wenn für eine Entität mehrere Hauptformulare, Schnellerfassungsformulare oder mobile Formulare vorhanden sind, können Sie eine Formularreihenfolge zuweisen. Mit der Formularreihenfolge wird festgelegt, welches der verfügbaren Formulare standardmäßig angezeigt wird. Der Zugriff auf die verfügbaren Hauptformulare oder die verfügbaren mobilen Formulare kann durch Zuweisen von Sicherheitsrollen genauer festgelegt werden. Weitere Informationen hierzu finden Sie unter [Steuern des Zugriffs auf Formulare](control-access-forms.md).  
  
 Schnellerfassungsformularen können keine Sicherheitsrollen zugewiesen werden. Somit ist das Formular ganz vorn in der Formularreihenfolge das einzige Formular, das von allen verwendet wird.  
  
## <a name="to-assign-a-form-order"></a>Zuweisen einer Formularreihenfolge  
  
1.  Öffnen Sie den [Projektmappen-Explorer](advanced-navigation.md#solution-explorer), erweitern Sie die gewünschte Entität, und wählen Sie **Formulare** aus.  
  
2.  Wählen Sie in der Symbolleiste der Formularliste die Option **Formularreihenfolge** aus.  

    ![Befehl für die Formularreihenfolge in der Symbolleiste](media/form-order.png)
  
3.  Wählen Sie **Hauptformularsatz**, **Formularsatz für Schnellerfassung**, **Schnellansichtsformularsatz** oder **Mobiler Formularsatz** aus, je nachdem, welche Art von Formularen Sie verwenden möchten. Weitere Informationen: [Type of forms (Formulartypen)](types-forms.md). 
  
4.  Beim Dialogfeld **Formularreihenfolge** handelt es sich um eine einfache Liste, in der Sie ein ausgewähltes Formular nach oben oder unten verschieben können.  
  
5.  Nachdem Sie die gewünschte Reihenfolge festgelegt haben, klicken Sie auf **OK**, um das Dialogfeld zu schließen.  

## <a name="next-steps"></a>Nächste Schritte

[Change navigation within a form (Ändern der Navigation in einem Formular)](use-the-form-editor-legacy.md)
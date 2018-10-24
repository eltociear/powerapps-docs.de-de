---
title: Öffnen des Formular-Editors einer modellgesteuerten App in PowerApps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 8478a07a-c697-4784-874b-36958eb4f95d
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: e0fe15df88fccbaee3c13a344416a434e1f92923
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39683050"
---
# <a name="open-the-model-driven-app-form-editor"></a>Öffnen des Formular-Editors einer modellgesteuerten App 
Im Formular-Editor können Sie Formulare entwerfen, indem Sie Komponenten wie Abschnitte, Registerkarten, Felder und Steuerelemente in der Canvas des Formular-Editors ablegen. In diesem Thema lernen Sie die verschiedenen Möglichkeiten kennen, um auf den Formular-Editor zuzugreifen.
 
Wenn Sie bei der Bearbeitung des Formulars neue Lösungskomponenten (z.B. Webressourcen) erstellen, enthalten die Namen der Komponenten das Anpassungspräfix des Lösungsherausgebers für die Standardlösung. Zudem werden diese Komponenten nur in die Standardlösung eingeschlossen. Wenn Sie neue Lösungskomponenten in eine bestimmte nicht verwaltete Lösung einbeziehen möchten, sollten Sie den Formular-Editor über diese nicht verwaltete Lösung öffnen.  

## <a name="access-the-form-editor-from-the-powerapps-site"></a>Zugriff auf den Formular-Editor über die PowerApps-Website

1. Melden Sie sich bei [PowerApps](https://web.powerapps.com/) an. 

2. Klicken Sie auf **Modellgesteuert** > **Daten** > **Entitäten** und dann auf die gewünschte Entität, z.B. die Firmenentität. 

3. Wählen Sie die Registerkarte **Formulare** aus, und öffnen Sie das gewünschte Formular, z.B. das Hauptformular **Firma**.

## <a name="access-the-form-editor-from-solution-explorer"></a>Zugriff auf den Formular-Editor über den Lösungs-Explorer
  
1.  Öffnen Sie den [Lösungs-Explorer](advanced-navigation.md#solution-explorer).
  
2.  Erweitern Sie unter **Komponenten** die Option **Entitäten** und dann die gewünschte Entität, und klicken Sie dann auf **Formulare**.  
  
3.  Klicken Sie in der Liste der Formulare auf das Formular, das Sie bearbeiten möchten.  
  

## <a name="access-the-form-editor-through-the-command-bar-within-a-model-driven-app"></a>Zugriff auf den Formular-Editor über die Befehlszeile in einer modellgesteuerten App 
  
1.  Öffnen Sie einen Datensatz.  
  
2.  Wenn es mehrere Hauptformulare für die Entität gibt, stellen Sie sicher, dass es sich bei dem Formular um das Formular handelt, das Sie bearbeiten möchten. Falls dies nicht der Fall sein sollte, verwenden Sie die Formularauswahl, um das Formular auszuwählen, das Sie bearbeiten möchten.  
  
3.  Klicken Sie auf die Schaltfläche **Weitere Befehle** ![Schaltfläche „Weitere Befehle“ in der Terminaktivität](media/more-commands.gif "Schaltfläche „Weitere Befehle“ in der Terminaktivität").  
  
4.  Wählen Sie den **Formular-Editor** aus.  

## <a name="access-the-form-editor-from-within-dynamics-365-customer-engagement"></a>Zugriff auf den Formular-Editor über Dynamics 365 Customer Engagement
  
 Abhängig von der Entität können Sie über die Befehlsleiste oder das Menüband auf den Formular-Editor in Dynamics 365 Customer Engagement zugreifen. Bei beiden Methoden wird das Formular im Kontext der Standardlösung geöffnet. 

## <a name="access-the-form-editor-for-an-unmanaged-solution"></a>Zugriff auf den Formular-Editor für eine nicht verwaltete Lösung  
  
1.  Öffnen Sie [Lösungen](advanced-navigation.md#solutions).  
  
2.  Doppelklicken Sie auf die nicht verwaltete Lösung, mit der Sie arbeiten möchten.  
  
3.  Suchen Sie die Entität mit dem Formular, das Sie bearbeiten möchten. Wenn die Entität nicht vorhanden ist, müssen Sie sie hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen einer Entität zu einer nicht verwalteten Lösung](#add-an-entity-to-an-unmanaged-solution). 
  
### <a name="add-an-entity-to-an-unmanaged-solution"></a>Hinzufügen einer Entität zu einer nicht verwalteten Lösung  
  
1.  Wählen Sie den Knoten **Entitäten** aus, und klicken Sie auf der Symbolleiste über der Liste auf **Vorhandene hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Lösungskomponenten auswählen** mit auf **Entität** festgelegter Auswahl **Komponententyp** die Entität aus, die Sie hinzufügen möchten, und klicken Sie auf **OK**.  
  
3.  Wenn das Dialogfeld **Fehlende erforderliche Komponenten** angezeigt wird und Sie nicht beabsichtigen, diese nicht verwaltete Lösung in eine andere Umgebung zu exportieren, können Sie auf **Nein, erforderliche Komponenten nicht einschließen** klicken. Wenn Sie festlegen, fehlende erforderliche Komponenten an dieser Stelle nicht einzuschließen, können Sie sie später hinzufügen. Sie erhalten erneut eine Benachrichtigung, wenn Sie diese Lösung zu einem späteren Zeitpunkt exportieren.  
  
5.  Erweitern Sie im Lösungs-Explorer die Entität mit dem Formular, das Sie bearbeiten möchten, und klicken Sie auf **Formulare**.  
  
6.  Doppelklicken Sie in der Liste der Formulare auf das Formular, das Sie bearbeiten möchten.  

## <a name="next-steps"></a>Nächste Schritte

[Erstellen und Entwerfen von Formularen](create-design-forms.md)

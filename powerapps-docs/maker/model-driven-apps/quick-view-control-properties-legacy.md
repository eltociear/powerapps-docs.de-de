---
title: Schnellansichts-Steuerelementeigenschaften für Hauptformulare in modellgesteuerten Apps in Power Apps | Microsoft-Dokumentation
description: Grundlegendes zu Schnellansichts-Steuerlementeigenschaften für Hauptformulare
Keywords: Eigenschaften des Steuerelements für die Schnellansicht; Dynamics 365; Hauptformulare
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 05/04/2020
ms.service: powerapps
ms.topic: article
ms.assetid: 68f68d5b-6c71-4b95-bb46-d48c59d9008e
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a76269092be62d2e8bb99138fb35b521cebb1f9c
ms.sourcegitcommit: 52b7f59e271437e86ffff226fb6c1982bf7f08b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "3332428"
---
# <a name="model-driven-app-quick-view-control-properties"></a>Eigenschaften des Schnellansichtssteuerelements in modellgesteuerten Apps

Ein Steuerelement für die Schnellansicht auf einem modellgesteuerten App-Formular zeigt Daten aus einem Datensatz an, der bei einer Suche im Formular ausgewählt wurde. Die im Steuerelement angezeigten Daten werden anhand eines Schnellansichtsformulars definiert. Die Daten, die angezeigt werden, können nicht bearbeitet werden; wenn jedoch das primäre Feld im Schnellansichtsformular Feld enthalten ist, wird es zu einem Link, mit dem der verknüpfte Datensatz geöffnet werden kann. Weitere Informationen: [Erstellen und Bearbeiten von Schnellansichtsformularen](create-edit-quick-view-forms.md)  

> [!div class="mx-imgBorder"] 
> ![Kontaktschnellansichtsformular im Firmenformular](media/quick-view-form-contact.png "Kontakt Schnellansichtsformular auf dem Kontoformular")  

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**.  

3.  Wählen Sie ein Formular mit **Typ** **Haupt** aus.

4.  Wählen Sie im Formulardesigner **Komponente hinzufügen**.

5.  Wählen Sie im linken Navigationsbereich **Schnellansicht**.

6.  Wählen Sie im Dialogfeld **Schnellansichtsformulare wählen** ein Feld **Nachschlagen**, das im Formular enthalten ist, und wählen Sie dann ein Schnellansichtsformular für die verknüpften Entitäten. Die angezeigten verwandten Entitäten hängen von dem von Ihnen gewählten Feld **Nachschlagen** ab.  

    > [!div class="mx-imgBorder"] 
    > ![Hinzufügen von Schnellansicht-Steuerelement](media/select-quick-view-form.png "Hinzufügen von Schnellansicht-Steuerelement zu Hauptformular")

7.  Wählen Sie **Fertig** aus, um das Dialogfeld **Schnellansichtsformulare auswählen** zu schließen. Das Schnellansichtsformular wird auf dem Formular angezeigt, und die Eigenschaften der Schnellansicht erscheinen im Eigenschaftenbereich.

|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Beschriftung**|**Erforderlich**: Eine für das Schnellansichtsformular anzuzeigende Beschriftung.|  
|**Name**|**Erforderlich**: Der eindeutige Name für das Schnellansichtsformular, der verwendet wird, wenn auf es in Skripts verwiesen wird.|  
|**Beschriftung ausblenden**|Zeigt die Beschriftung im Formular an.| 
|**Schnellansichtsformulare**|Listet die Schnellansichtsformulare auf, die Sie für die verknüpften Entitäten ausgewählt haben. 
|**Formulare auswählen**|Wählen oder ändern Sie die ausgewählten Schnellansichtsformulare für die verbundenen Entitäten. Die angezeigten verwandten Entitäten hängen von dem von Ihnen gewählten Feld **Nachschlagen** ab.|  
|**Komponenten**|Zu konfigurierende Eigenschaften für die Komponente. Eine Schnellansichtssteuerelementkomponente hat keine zu konfigurierenden Eigenschaften und wird standardmäßig angezeigt, ob jemand einen Webbrowser, Dynamics 365 für Telefone oder Dynamics 365 für Tablets verwendet.

## <a name="quick-view-control-properties-in-classic-form-designer"></a>Schnellansicht der Steuereigenschaften im klassischen Formulardesigner

1.  Melden Sie sich bei [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) an.  

2.  Erweitern Sie **Daten** und wählen **Entitäten**, wählen Sie die Entität aus und wählen Sie die Registerkarte **Formulare**. 

3.  Öffnen Sie in der Liste der Formulare das Formular des Typs **Haupt**.

4.  Wählen Sie im Befehlsmenü **Wechsel zu klassisch**.

5.  Wählen Sie dann auf der Registerkarte **Einfügen** das **Schnellansichtsformular**, um die Eigenschaften des Steuerelements für die Schnellansicht anzuzeigen.

    > [!div class="mx-imgBorder"] 
    > ![Steuerelement für die Schnellansicht](media/quick-view-control.png)
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Name**|**Erforderlich**: Der eindeutige Name für das Schnellansichtsformular, der verwendet wird, wenn auf es in Skripts verwiesen wird.|  
|**Bezeichnung**|**Erforderlich**: Eine für das Schnellansichtsformular anzuzeigende Beschriftung.|  
|**Beschriftung im Formular anzeigen**|Zeigt die Beschriftung im Formular an.|  
|**Suchfeld**|Wählen Sie eines der Suchfelder, die im Formular enthalten sind.|  
|**Verknüpfte Entität**|Dieser Wert hängt vom **Nachschlagefeld** ab, das Sie auswählen. Dies ist normalerweise die primäre Entität für die 1: N-Entitätsbeziehung für die Suche.<br /><br /> Wenn die Suche eine Entität **Potenz. Kunde** umfasst, die entweder eine Firma oder einen Kontakt annehmen kann, können Sie im Feld **Schnellansichtsformular** ein Schnellansichtsformular für Firma und Kontakt auswählen, indem Sie diesen Wert ändern und dann ein anderes Schnellansichtsformular auswählen.|  
|**Schnellansichtsformular**|Wenn die **Verknüpfte Entität** ein Schnellansichtsformular hat, können Sie dies hier auswählen. Wählen Sie andernfalls **Neu** aus, um eines zu erstellen.<br /><br /> Wählen Sie **Bearbeiten** aus, um das ausgewählte Schnellansichtsformular zu ändern.|  
|**Zusätzliche Eigenschaften**|Sie können den Standardrenderingstil angeben, indem Sie das Kontrollkästchen aktivieren.|

>[!NOTE] 
> Wenn Sie ein mehrzeiliges Textfeld zu einem Schnellansichtsformular hinzufügen, hat das Formular eine Höhe von eins, unabhängig davon, wie die Feldsteuerungshöhe eingestellt ist. Dadurch wird die korrekte Wiedergabe des Formulars bei gleichzeitiger Beibehaltung der Dichte gewährleistet. Beachten Sie, dass mehrzeilige Textfelder in anderen Formulartypen, wie z.B. Hauptformularen, anders funktionieren, da das Formular automatisch entsprechend der Textmenge erweitert wird. 


## <a name="next-steps"></a>Nächste Schritte

[Verwenden des Hauptformulars und seiner Komponenten](use-main-form-and-components.md)
 
